---
title: "gedit not working in kubuntu?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-02-18
hi
i just moved from ubuntu to kubuntu
in terminak gedit not working
i get

evan@evan-laptop:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
evan@evan-laptop:~$

Please Help
Thanks

---

### Post by Maestro23 on 2007-02-18
You need to install it. It is Gnome's text editor.

apt-get install gedit

---

### Post by evkefalas on 2007-02-18
thanks for the reply
tried it and get

evan@evan-laptop:~$ apt-get install gedit
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
evan@evan-laptop:~$

---

### Post by Shay Stephens on 2007-02-18
Why not use kate instead of gedit?

---

### Post by Maestro23 on 2007-02-18
My bad,

sudo apt-get install gedit.

You should know that by now...:) 

Might have to enable some extra repositories if you still don't find it.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by arochester on 2007-02-18
The command should be: sudo apt-get install gedit

As the above reply says - when the command says "gedit" you can edit it to say "kate".

---

### Post by evkefalas on 2007-02-18
i am trying to mount my ntfs partition
following this page:

How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access 
Warning: The software you will use is still in Beta. You should not enable it on production machines 
Read #General Notes 
Enable universe. Read #How to apt-get the easy way (Synaptic) 
sudo apt-get install ntfs-3g

Read #How to list partition tables 
Create the local mount folder and edit the fstab file to mount the disks to this folder. 
e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
 Local mount folder: /media/windows 
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

Append the following line at the end of file. 
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0

 You can adjust your locale. Execute 'locale -a' in a terminal to know which one are supported by your system. 
Save the edited file. 
If you reboot now, the disk will be writable to every users. If you want the changes to take effect immediately without rebooting, execute the following command, ignoring the errors about "/" and others not being unmounted. 
sudo umount -a && sudo mount -a

Further troubleshooting is listed at this comprehensive howto thread.


So how can i use kate instaed of gedit in this line above:
gksudo gedit /etc/fstab

thanx a lot for yr help
:)

---

### Post by evkefalas on 2007-02-18
Thanx alot
everything worked fine guys
many thans
:)

---

### Post by mcduck on 2007-02-19
> **evkefalas said:**
> 
So how can i use kate instaed of gedit in this line above:
gksudo gedit /etc/fstab
'kdesu kate /etc/fstab' should work in KDE :)

---

### Post by Metallinut on 2007-03-01
> **mcduck said:**
> 'kdesu kate /etc/fstab' should work in KDE :)

I also just recently switched to kubuntu.  I actually wound up wiping out my old partitions, and starting over, installing straight from the Kubuntu live CD (6.10).

I get some weird output when I use:
```
kdesu kate
``` from a konsole

Kate still winds up opening, but in the konsole there's a whole bunch of jibber jabber about missing displays and such.

I also have a weird symptom where if I go to change my keyboard layout in Regional & Language settings of System Settings.  I'd like to change my layout (as I did once in Gnome) to make my Window key work like Super.  I know I can do a modmap to get it working, but I should be able to just select my keyboard from the dropdown list.  But the dropdown list is empty!  And this is a FRESH install off the Kubuntu live CD!!!  What's up with that?

---

### Post by khedron on 2007-03-01
> **Metallinut said:**
>  I should be able to just select my keyboard from the dropdown list.  But the dropdown list is empty!


I had what you have. Is your /usr/share/X11/xkb folder empty? Try
```

sudo cp -a /etc/X11/xkb /usr/share/X11/xkb

```Edit: BTW, that weird console output from Kate is normal. I get it with basically every application I run from the command line. I think it's something to do with debugging.

---

### Post by igknighted on 2007-03-01
Yeah, if you don't want to see all that debugging output I think you can turn it off in the control panel somewhere.

---

### Post by Metallinut on 2007-03-01
> **khedron said:**
> I had what you have. Is your /usr/share/X11/xkb folder empty? Try
```

sudo cp -a /etc/X11/xkb /usr/share/X11/xkb

```Edit: BTW, that weird console output from Kate is normal. I get it with basically every application I run from the command line. I think it's something to do with debugging.

Rock on!  That's it!  Thanks!  Isn't it strange that that wouldn't be there upon initial install though?

---

