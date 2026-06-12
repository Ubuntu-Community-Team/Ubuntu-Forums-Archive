---
title: "freeze after login"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by KingTiger on 2006-01-05
Hello
i installed ubuntu 5.10 and when I boot up and try to login it just shows a brown screen and sometimes says Ubuntu than it just sits there please help 

my computer info
intel celeron
vidio card: nvidea Rivia 128
ram: 256mb ram
if you need any more info just ask

KingTiger

---

### Post by KingTiger on 2006-01-05
update it some times logs in after like 10 minutes
should it take that long?

KingTiger

---

### Post by patrick295767 on 2006-01-05
[QUOTE=KingTiger]Hello
i installed ubuntu 5.10 and when I boot up and try to login it just shows a brown screen and sometimes says Ubuntu than it just sits there please help 

my computer info
intel celeron
vidio card: nvidea Rivia 128
ram: 256mb ram
if you need any more info just ask

KingTiger[/QUOTE]
  
Brown screen is rather strange ... 
  
Isnt it grey and white color with the cross (mouse) ?
  
try maybe server installation, 
with your breezy sources.list there: "/root/sources.list"
then 
apply this script:
```
#!/bin/bash
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" "/etc/apt/sources.list"
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
echo "#!/bin/bash" > "/etc/init.d/patrickrcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/patrickrcs70.sh"
chmod +x /etc/init.d/patrickrcs70.sh

cd /etc/init.d/
ln -s patrickrcs70.sh /etc/rc2.d/S70patrickrcs70.sh
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
  
  
u can then : 
type :
if u'd like gnome :
apt-get -f install gnome
if u'd like kde :
apt-get -f install kde
  
Greetz'
  
Pat'

---

### Post by estel on 2006-01-05
Yer? :s

Why should it be grey. X appears to be running, allowing them to log in; but it takes 10 minutes timeout half way through logging in.

---

### Post by KingTiger on 2006-01-05
today I tryed it agian and it worked but it toke 20 minutes to login

KingTiger

---

### Post by KingTiger on 2006-01-05
Update:
after the desktop comes up it wont open things like the admin network thing and other admin options (it says opening xyz program and asks my password but than nothing happens) and the programs that do open take forever to open or do any thing (like i'll open firefox and then in 5 minutes it might open)

KingTiger

---

### Post by KingTiger on 2006-01-05
is there any thing i can do to get it to run faster (with windows xp it runs just fine)

KingTiger

---

### Post by patrick295767 on 2006-01-05
[QUOTE=estel]Yer? :s

Why should it be grey. X appears to be running, allowing them to log in; but it takes 10 minutes timeout half way through logging in.[/QUOTE]
  
Thks, passed the second reply about brown color freeze stuffs ...
That not the grey screen that may come from xlib... prob.
   
Was your linux working fine just after the first ubuntu installation ?
or somethg went wrong after using the linux box ?

I wish this prob is solved ...
some user crontab maybe ? (I dont think so)
  
or try maybe from the console, as root after ```
sudo su
```:
```
adduser user_beta2
```
then login with user_beta2
(you hidden .file  are maybe not correct anymore)
  
  
Greetings, 

Pat'

---

### Post by KingTiger on 2006-01-05
ok that works thanks

---

### Post by KingTiger on 2006-01-05
I have a new problem I cant open anything in the system/administration menu
sometimes it will ask me the password but wont open anything (other then say opening xyz program for a minute)

KingTiger

---

