---
title: "How do i install programs?"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by completelinuxnoob on 2006-01-15
hi i can get programs via windows but how do you install in linux?

---

### Post by Derek Djons on 2006-01-15
You can use System -> Administration -> 'Synaptic Package Manager'. You can simply search for applications and mark them to be installed.

---

### Post by patrick295767 on 2006-01-15
```
sudo apt-get -f install program_name
```
  
example:
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

  Have a look to the wiki [https://wiki.ubuntu.com/UserDocumentation#head-53abb59509da14eef4bfa451d74af2c8f7eaa02b]("https://wiki.ubuntu.com/UserDocumentation#head-53abb59509da14eef4bfa451d74af2c8f7eaa02b")
---------
Progress thread:
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8](http://www.ubuntuforums.org/showthread.php?t=64557&page=8)

---

### Post by jasmuz on 2006-01-15
for a full detailed list of programs you can install, there is an "Add appliations" program in the menu or in the System menu-->Administration-->Synaptic package manager, wich has all the software available to you.

This also can be done via a terminal,
To do a search is; sudo apt-cache search name 
And to install it; sudo apt-get install program

---

### Post by sinisterfuzzy on 2006-08-29
i tried to find that Synaptic thing the graphical installer, but it's not on my list, i went to Edit Menus, it was checked to be under Administration but would not show up, i moved it to the top, i checked it and only like 3 other things, but no matter what i did, it would not show up in the menu, how else can i run this program?

---

### Post by justin whitaker on 2006-08-29
> **completelinuxnoob said:**
> hi i can get programs via windows but how do you install in linux?

Check this site out:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Depending on what files you want to install, follow the instructions, and you will be fine.

---

### Post by sinisterfuzzy on 2006-08-29
alright i followed those instruction, and i can't get past Password:  while the thing is blinking i enter the password and press enter and it brings me back to my name:~$

[IMG]http://i23.photobucket.com/albums/b378/sinisterfuzzy/Screenshot.png[/IMG]

---

### Post by geo_bio on 2006-08-29
Are you talking about the popup rectangle and everything else becomes darker?

You're supposed to type in your password you use to log in (IF YOU'RE ADMIN). If you're not an admin.... sorry.
If you typed in the password.... maybe it's wrong or you dont have the ability to do that.

It doesn't need some secret password or anything.

---

### Post by justin whitaker on 2006-08-29
> **sinisterfuzzy said:**
> alright i followed those instruction, and i can't get past Password:  while the thing is blinking i enter the password and press enter and it brings me back to my name:~$

[IMG]http://i23.photobucket.com/albums/b378/sinisterfuzzy/Screenshot.png[/IMG]

Run sudo passwrd (or is that passwd-I never can remember!), to change the Root password, then try it again.

---

### Post by sinisterfuzzy on 2006-08-29
alright, i figured out how to install and I installed amaroK.  now, when i try to play an .mp3 it does this:
[IMG]http://i23.photobucket.com/albums/b378/sinisterfuzzy/mp3.png[/IMG]

---

### Post by 3rdalbum on 2006-08-29
Go into the Software Properties administration panel, and enable all the repositories.

Now go into Synaptic and hit Control-R. This will reload the package information with the new repositories.

Once that's done, do a search for "gstreamer". Install:

```

gstreamer0.10-plugins
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-alsa

```

And that should get your MP3s playing.

---

### Post by miky on 2006-11-01
forgive me if i am wrong (or if i am writing what you do not need).
there is a soft which can help you with some basic things. it is called easy ubuntu [URL="http://easyubuntu.freecontrib.org/"]http://easyubuntu.freecontrib.org/[ /URL] and it can install some thongs for you...(VGA drivers, some codecs..)

---

### Post by easyease on 2007-09-28
You can also install software by installing ".deb" packages, theres a great site here...
[http://www.getdeb.net/](http://www.getdeb.net/)
you just download the packages you want then double click on the icon where  its saved to,  then it will pop up a window called gdeb installer which will do the job for you.

---

### Post by Human2.0 on 2007-11-15
If I'm installing a third party program that's not in Synaptic, and it's a tar.bz2 rather than a .deb, do I need a compiler (as in, something that's not included in Gutsy Gibbon)? Where can i find a decent walk-through if i have to use terminal?

---

