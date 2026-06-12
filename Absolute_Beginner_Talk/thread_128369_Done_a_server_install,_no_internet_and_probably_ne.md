---
title: "Done a server install, no internet and probably need to use XFCE or other light WM"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by IainT on 2006-02-11
Made the title as descriptive as possible.

Basically I have an old laptop (433mhz celeron, 96mb RAM) which I successfully installed Ubuntu on to the other day, having figured out how to avoid a problem it seemed to be having 'apmd'. However, Gnome was too resource heavy, it was taking 51mb of RAM to sit there with an empty desktop.

I want to try XFCE or IceWM and see how that goes. Trouble is my network card is pcmcia, and the install process does not recognise it. It is a Corega FEthernet II PCC-TXD. The other way I could possibly connect to the net is directly to the modem via its USB connection - will this be possible?

Or can I download the WM's on an XP machine and burn them to cd and use them that way. If needs be I can install a basic gnome package (*sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity gdm gedit gnome-terminal* was what I got to work before) 

Thanks in advance.

---

### Post by majikstreet on 2006-02-11
I can't really help you for the network, but for the WM I think fluxbox may work... everything is going to be really slow, so for a web browser something like firefox wouldn't be a good idea, btw..  xfce is probably going to be too slow.. it was slow even on 256mb for me. gnome was slow on 256mb, too.

[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)
[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

you can also get deb's onto a cd or something.. you'd have to go to packages.ubuntu.com download ALL the dependancies for the packages and sudo dpkg -i packagename.deb  to install them.. it will be VERY tedious, unfortunately...

---

### Post by patrick295767 on 2006-02-12
After installing as server; I run this script to install everthg working:

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
apt-get -f -y install mc 
apt-get -f -y install ssh
apt-get -f -y install ftp
apt-get -f -y install openssh-server
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg
apt-get -f -y install 
apt-get -f -y install 

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
apt-get -f -y install xpdf xzgv 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip
apt-get -f -y install scrot
apt-get -f -y install gdesklets
apt-get -f -y install idesk
apt-get -f -y install krusader
apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install k3bsetup
apt-get -f -y install
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install imagemagick
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install dvd+rw-tools
apt-get -f -y install growisofs mozilla
apt-get -f -y install mozilla-firefox
apt-get -f -y install openoffice.org
apt-get -f -y install inkscape
apt-get -f -y install openoffice.org-bin
apt-get -f -y install dvd+rw-format
apt-get -f -y install 
apt-get -f -y install imagemagick mozilla-browser
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
apt-get -f -y install libqt3c102-mt
apt-get -f -y install crond gpdf kpdf gs kghostview
apt-get -f -y install xzgv mplayerplug-in

apt-get -f -y install xmltv
apt-get -f -y install audacity gcc
apt-get -f -y install digikam kmail kaddressbook mtools annoyance-filter khelpcenter kleopatra
apt-get -f -y install nfs nfs-common
apt-get -f -y install libpt-plugins-v4l kmail
apt-get -f -y install kontact kmail
apt-get -f -y install kicker
apt-get -f -y install konsole gxine
apt-get -f -y install kmines 
apt-get -f -y install camorama kbear gftp
apt-get -f -y install klondike
apt-get -f -y install kmahjongg
apt-get -f -y install kate grip
apt-get -f -y install synaptic alsamixergui
apt-get -f -y install synaptics
apt-get -f -y install wine gimp hatari 
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim
## this 3  lines for amsn 0.95
apt-get -f -y install tcl8.4 sun-j2re1.5 flashplayer-mozilla
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev
apt-get -f -y install xawtv
apt-get -f -y install gcc
apt-get -f -y install gcc-3.4
apt-get -f -y install gweather
apt-get -f -y install gdesklets
apt-get -f -y install 

# hb
apt-get -f -y install libwxgtk2.4-dev
apt-get -f -y install tcltls planner kweather knewsticker korn wine






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
apt-get -f -y install rox-filer dgen xscreensaver xlockmore gnome-screensaver
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
apt-get -f -y install azureus
apt-get -f -y install
apt-get -f -y install sun-j2sdk1.5
apt-get -f -y install
apt-get -f -y install
apt-get -f -y install azureus
apt-get -f -y install

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
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config




######################## INSTALLATION OF PACKAGE FOLDER ##################"


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

## now the cedega
mkdir /root/patrickpackages
cd /root/patrickpackages

gzip -d cedega_4.4.3-1.i386.tgz
# un-tgz
tar -xvf cedega_4.4.3-1.i386.tar
## once done
##/usr created 
##you'll have to place it in /usr

tar -jxvf cdemu-0.7.tar.bz2.tar





########################### end of patrick packages
apt-get -y remove numlockx
apt-get -f -y install

apt-cache pkgnames gnome 



echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"









```



with sources.list breezy:
```

```


Greetings

Pat'

---

### Post by kblood on 2006-02-15
In your case (but I'm also quite a newbie) I would do a server install, which installs no Desktop Environment.

Then, using Windows, or whatever you can, go crazy looking for info on how to get that PCMCIA card you have working. Probably ndiswrapper can help. All the steps you need to take should definitely be possible from the command line. Pretty much everything in Linux can be done from the command line!

Then I would install the package xubuntu-desktop.

Good luck!

---

