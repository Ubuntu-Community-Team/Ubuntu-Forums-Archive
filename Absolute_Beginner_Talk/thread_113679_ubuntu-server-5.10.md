---
title: "ubuntu-server-5.10"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by mohlertm on 2006-01-06
Hello,

I am new to Ubuntu.  I have installed ubuntu-server-5.10-install-i386 on my system and when I log in I get tommy@ubuntu:~$ and then a cursor.  What do I do now?  I installed it so I can have a file and print server for my house (i have a gamin pc, and two notbooks networked) for my other computers to access.  could you give me some help on what I need to do?  Thansk a lot for helping me kick the windows curse.....

Tommy

---

### Post by adwait on 2006-01-06
Well, AFAIK, the server edition doesn't come with a GUI. So whatever you want to do, has to be done from the command prompt. If you want, you can install a GUI with
```
sudo apt-get install ubuntu-desktop
```
This will install Gnome, if you can install XFCE with
```
sudo apt-get install xubuntu-desktop
```
or KDE with
```
sudo apt-get install kubuntu-desktop
```

If you dont want a GUI at all, you can make do with Command Line Interface as well.

---

### Post by patrick295767 on 2006-01-07
my script for server ubuntu installation:
=========================

It can still be improved but install my fvwm
(if you need kde, apt-get -f -y install kde)

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
apt-get -f -y install xserver-xorg

apt-get -f -y install nfs-common
apt-get -f -y install nfs-kernel-server
apt-get -f -y install portmap
apt-get -f -y install nfs
apt-get -f -y install proftpd
apt-get -f -y install autofs
apt-get -f -y install idesk
apt-get -f -y install xloadimage
apt-get -f -y install samba
apt-get -f -y install unzip
apt-get -f -y install openssh-server

apt-get -f -y install growisofs
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install 
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
apt-get -f -y install gdesklets
apt-get -f -y install idesk
apt-get -f -y install krusader
apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install digikam
apt-get -f -y install audacity
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install imagemagick
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install dvd+rw-tools
apt-get -f -y install growisofs
apt-get -f -y install openoffice.org
apt-get -f -y install inkscape
apt-get -f -y install openoffice.org-bin
apt-get -f -y install dvd+rw-format
apt-get -f -y install 
apt-get -f -y install imagemagick
apt-get -f -y install gaim

apt-get -f -y install opera
apt-get -f -y install nfs
apt-get -f -y install mozplugger
apt-get -f -y install kopete

apt-get -f -y install xlockmore
apt-get -f -y install kfmclient
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install kaffeine
apt-get -f -y install kadu
apt-get -f -y install xine
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install vpnc
apt-get -f -y install kcron
apt-get -f -y install cron
apt-get -f -y install crond gpdf kpdf gs kghostview
apt-get -f -y install xzgv mplayerplug-in

apt-get -f -y install xmltv
apt-get -f -y install audacity gcc
apt-get -f -y install digikam kmail kaddressbook mtools annoyance-filter khelpcenter kleopatra
apt-get -f -y install nfs nfs-common
apt-get -f -y install libpt-plugins-v4l kmail
apt-get -f -y install kontact kmail
apt-get -f -y install kicker
apt-get -f -y install konsole
apt-get -f -y install kmines 
apt-get -f -y install klondike
apt-get -f -y install kmahjongg
apt-get -f -y install kate


apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install 

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash" > "/etc/init.d/patrickrcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/patrickrcs70.sh"
chmod +x /etc/init.d/patrickrcs70.sh

cd /etc/init.d/
ln -s patrickrcs70.sh /etc/rc2.d/S70patrickrcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer dgen
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


cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get install mplayer-386
apt-get install mozilla-mplayer
apt-get install mplayer-fonts
apt-get install acroread 
apt-get install mozilla-acroread
apt-get install mozilla-acroread
apt-get install mplayerplug-in
wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup



apt-get -y remove numlockx
apt-get -f -y install


echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"









```

---

### Post by stabface on 2006-04-10
how could i use this over an SSH connection

---

### Post by Iowan on 2006-04-10
Dunno if your question was "How to install GUI" or "What do I need for file/print server"?  My server doesn't have a GUI either - I prefer it that way.  A P200 doesn't have a lot of "spare" horsepower for graphics.  
   For the file/print server, you'll probably want to install Samba.  There's a good how-to at: [http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")
   Check the man pages for **apt-get** or **aptitude**.  You may want to consider having your server hand out DHCP leases to the other boxes, too.

---

