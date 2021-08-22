<h1 align=center> Commands to install correct drivers for 
  TP-Link TL-WN722N</p>

### Install pkgs
```bash
sudo apt update
sudo apt upgrade
sudo apt install bc
sudo apt-get install build-essential
sudo apt-get install libelf-dev
sudo apt-get install linux-headers-`uname -r`
```

### Change drivers
```bash
sudo apt install dkms
sudo rmmod r8188eu.ko
git clone https://github.com/aircrack-ng/rtl8188eus
cd rtl8188eus
sudo -i
echo "blacklist r8188eu" > "/etc/modprobe.d/realtek.conf"
exit
sudo reboot
```

### After reboot
```bash
sudo apt update
cd rtl8188eus
sudo make
sudo make install
sudo modprobe 8188eu
````

### To enable Monitor mode and test packet injection:
``` bash
ip link set wlan1 down
sudo airmon-ng check kill
sudo airmon-ng start wlan1
ip link set wlan1 up
iwconfig
sudo aireplay-ng --test wlan0
```
