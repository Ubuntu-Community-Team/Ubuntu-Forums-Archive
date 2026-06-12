---
title: "How to install / to download the snd_usb_audio driver ?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-16
(for usb logitech microphone)
cos not present in audacity !

tahnk you

---

### Post by Rinzwind on 2005-12-16
Are you sure?

My Breezy install installed it during 1st install.

- Doesn't **lsusb** list the device after you plugged it in?
- Oh and whenever I do plug my headset in I get a popup saying I need to go to 'sound settings' to configure it but for that to work I -did- manually edit a file. I'll have to check later today tho (no Ubuntu with me :( )

---

### Post by patrick295767 on 2005-12-16
ahhhh 
I installed my ubuntu from server:
then applied my script: 
```
#!/bin/bash
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get update
apt-get -y upgrade
apt-get -f -y install x-window-system-core
apt-get -f -y install xdm 
apt-get -f -y install openssh-server
apt-get -f -y install samba
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install proftpd
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install gnome-chess
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip

apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install nfs
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install xzgv
apt-get -f -y install nfs nfs-common
apt-get -f -y install 
apt-get -f -y install 

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash" > "/etc/init.d/bootcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/bootcs70.sh"
chmod +x /etc/init.d/bootcs70.sh

cd /etc/init.d/
ln -s bootcs70.sh /etc/rc2.d/S70bootcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 
echo "Please choose gdm "
apt-get -f -y install 
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart
echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"

```

U have any idea what I should install to make it work ??

thank y ou

---

### Post by patrick295767 on 2005-12-16
the lsusb says that my logitech microphone is there 
but not alsa
not audacity
not skype either ...

---

### Post by patrick295767 on 2006-01-07
[http://www.ubuntuforums.org/showthread.php?p=637146#post637146](http://www.ubuntuforums.org/showthread.php?p=637146#post637146)

---

