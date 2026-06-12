---
title: "samba XP to feisty to gutsy"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by dysolve on 2007-11-14
I know there are millions of topics on samba sharing , i proberly have been reading about 100 of them over the last three days but I have problems..

XP can see the shares on both my feisty server and gutsy desktop but when I try to access them I am prompted for a username and password but no username or password works.

both ubuntu machine can access the XP drive but only through the network places, if i try to browse to them in any media player I can not find the drive.

gutsy has the same issue as XP with trying to access the shares on the feisty server..

now I know it either permissons or a username/password thing but nothing I have been reading show me anything new to what I did to setup the shares.

the main guide i used to setup samba was [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

i followed this to the word what have i missed??

regards and thanks in advance!
David..

---

### Post by renzokuken on 2007-11-14
you need to create a sambapassword for each  user

```
sudo smbpasswd -a *username*
```

then enter your desired password (same as login one on XP machines if you like)

then restart samba

```
sudo /etc/init.d/samba restart
```

---

### Post by dysolve on 2007-11-14
I already did that, i even restarted the machine after adding the users still no differance..

how do I list or see the list of samba users I have added?

---

### Post by Naipes on 2007-11-14
See this video on YouTube:

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Follow the instructions *exactly* as the dude in the video does it.   The video says it's for version 6.10, but it works for other Ubuntu versions too.

---

### Post by dysolve on 2007-11-14
that was awesome..... may have been a little monotone but he could have talked like a robot for all i care that was one of the best set of instructions i have ever followed...

thanks for the link.

xp can now access both my Ubuntu boxes and my feisty box can access my xp machine via places/network but how do i mount an XP share so i can access it from music programs and the like??

i did he following

sudo mkdir /media/mp3

sudo mount -t smbfs //xpmachinename/directory /media/mp3

but i get the following error..

mount: wrong fs type, bad option, bad superblock on //david-new/music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

what does this error mean i am doing wrong, the only thing i can think is i am trying to mount the wrong filesystem..

i added the mount to /etc/fstab and i get the same error.

tried with both ip addy and machine name same error!

---

### Post by dysolve on 2007-11-14
i have now tried cifs and i am having the same issues... windows to ubuntu is working great but ubuntu to windows and ubuntu to ubuntu are still having issues

---

### Post by dysolve on 2007-11-15
i finally got it working... it turns out it was not an security issue at all, smbfs was not installed..

I might have found a bug in gutsy but i doubt it..

synaptics install smbfs automaticlly when i install samba it's self and it was marked with a green box .. but i did apt-get install smbfs and it said it was not installed and it then proceded to install it now all works fine..

thanks for everybodys help..

the reason i think this might be a bug in gutsy is because all the tutorials tell you to use command line to install it and i did it via synaptics... so the error may not have show up before or people that have had problems then did the command line install with out testing if smbfs was properly installed!

---

