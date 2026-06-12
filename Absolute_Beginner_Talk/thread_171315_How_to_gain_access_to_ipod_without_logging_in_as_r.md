---
title: "How to gain access to ipod without logging in as root"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-06
I am new to linux. I am trying to play music directly from my iPod in Banshee. I am able to do this when i log in directly as root, but I want to be able to do it from my normal log in. From what I understand avoiding logging in as root is the best, I also can't run gDesklets when I'm logged in as root which is why I really want to know how to play these songs from my iPod. I have about 17 gigs of music, so you can understand why I don't want to use a quarter of my Linux partition just for music.

Thanks

---

### Post by Sandlst on 2006-05-06
If the problem lies with banshee not having enough permissions to open files from your ipod, try running it from a terminal with ```
sudo banshee
``` Hope this works, post back if it doesn't....

*EDIT* also, if the above does work, right click on Applications, select Edit Menus, click on Sound & Video in the left of the window, right click on Banshee in the right box, select Properties, and under Command, add sudo(with a space between sudo and banshee) in front.  Then, open a terminal, put in ```
sudo gedit /etc/sudoers
```Scroll to the bottom, then copy and paste this exact line into the file (replaceing USERNAME with your username)```
USERNAME ALL= NOPASSWD: /usr/sbin/banshee
``` This should allow you to run banshee from the menu as normal.

---

### Post by shutupimpoor on 2006-05-06
it didn't seem to work. I still can't get access to the iPod mount. When I click on it it says You do not have the permissions necessary to view the contents of "ipod-1". 

Also am I supposed to put sudo infront of  /usr/bin/banshee or am i supposed to do something different in menu editor?

```
 alassise@ubuntu:~$ sudo banshee

Unhandled Exception: DBus.DBusException: No reply within specified time
in [0x0003e] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:46) DBus.Bus:GetBus (BusType busType)
in [0x00001] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:23) DBus.Bus:GetSessionBus ()
in [0x00007] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/DBusIPC.cs:53) Banshee.DBusServer:.ctor ()
in [0x00016] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:135) Banshee.Core:.ctor ()
in [0x0000b] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:73) Banshee.Core:get_Instance ()
in [0x000ef] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:78) Banshee.BansheeEntry:Main (System.String[] args)

``` 
if that does anything

---

### Post by Sandlst on 2006-05-06
Unfortunatly, if the first part didn't work, adding the line to sudoers won't work either.....I wish I could test this out myself, but I never tried to read songs from my ipod, I just copied them to my harddrive, and now my ipod died :rolleyes: if you open rythembox up, and click (Music/Scan Removable Media) does that show songs?  Sudo in almost all cases should be as good as root, I'm not sure why root has access but sudo does not.....

*EDIT* also, could you try entering ```
su
```putting in your root password, then ```
banshee
```?  You might as well delete the sudoers line too, if sudo banshee doesnt work theres no point in having it in there.....

---

### Post by gr0kzer0 on 2006-05-06
Aren't you supposed to use

visudo

to edit your sudoers file?

---

### Post by Randomskk on 2006-05-06
How are you mounting the iPod?
Try checking how it's mounted - if you mount it under your own username you should be able to play from it.
Look at /etc/fstab or something maybe.

---

### Post by Omnios on 2006-05-06
You could try making a shell script. 
Open a text file
```

"cd /home/whatever_if_Needed"
gksudo banshee

```
and save it as say banshee with .sh at the end of it
Now you have a shell script which you can point your menu or desktop launcher to the shell script to launch it. Not shure but. Also this should be able to work with this ```


Code:

sudo gedit /etc/sudoers

Scroll to the bottom, then copy and paste this exact line into the file (replaceing USERNAME with your username)
Code:

USERNAME ALL= NOPASSWD: /usr/sbin/banshee

This should allow you to run banshee from the menu as normal.

```

---

### Post by Sandlst on 2006-05-06
[QUOTE=gr0kzer0]Aren't you supposed to use

visudo

to edit your sudoers file?[/QUOTE]
Yes, but gedit does work, at least in breezy so I thought it would be easier for a beginner than looking at how to work vi, is there some reason this would cause problems? And as Randomskk suggested, please post your /etc/fstab file here shutupimpoor.

---

### Post by shutupimpoor on 2006-05-07
yea i might be asking the wrong question. I can't get access to the ipod folder period, I think once I get access to that it will show up in Banshee. or maybe someone knows a way to get gdesklets to work in root? thats really the only reason i want to use my regular username, my computer isn't networked so nothing really matters

---

### Post by Sandlst on 2006-05-07
Hmmm, if thats the case, plug in your ipod, then open a terminal and put in ```
dmesg
``` you should see, at the bottom, your ipod mounted as /dev/something (I think) note what it is, then put in ```
sudo umount /dev/[COLOR="DarkOrange"]SOMETHING[/COLOR]
``` changing [COLOR="DarkOrange"]SOMETHING[/COLOR] to whatever dmesg showed you the ipod was mounted.  Then put this in:```
sudo gedit /etc/fstab
```Add a new line pasting this in:```
/dev/[COLOR="DarkOrange"]SOMETHING[/COLOR]       /media/ipod     vfat    iocharset=utf8,umask=000 0 0
```Change [COLOR="DarkOrange"]SOMETHING[/COLOR] to the right place for the ipod.  Finally do ```
sudo mount -a
```  Banshee should look for your ipod in /media/ipod.  Hope this works, post back if you have any problems

---

### Post by shutupimpoor on 2006-05-07
i've given up. i havent tried many of the new posts, but can anybody tell me how to mount the ipod? sometimes when i load it is charging instead of being mounted

---

