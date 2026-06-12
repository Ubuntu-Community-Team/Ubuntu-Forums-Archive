---
title: "Mounting Windows drives."
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by appdx on 2005-12-29
Hey, This is my first post ever in these forums so I hope you can help me out. I'm new to Ubuntu and Linux so I'm a real noob. I have my system running both Ubuntu 5.10 and Windows XP pro. I know I can make linux see the windows partition and be able to browse to it. I need to edit the /etc/fstab so i put /dev/hda1    /media/windows0 ntfs <here I don't know what to put.>,unmask=0222 then after I save it I think I do sudo mount -a in terminal. If someone could help me out that would be great. Thanks!

-[app.dx]

---

### Post by Gimbo on 2005-12-29
Well, this is only my second day with Ubuntu installed, but I *think* I can help. My setup is: one NTFS partition with XP Home installed and another partition with Ubuntu 5.10.

*consults piece of paper with stuff I've messed around with so far*

You're certainly on the right track.
Open up a terminal window (Applications>Accessories>Terminal)
Type
```
sudo mkdir /media/windows
```
then hit Enter.
This makes a new folder in the /media folder, which is where mounted stuff goes (I think).
Then type
```
sudo gedit /etc/fstab
```
This opens the fstab file in gedit, which is the default text editor (ie the Notepad equivalent).
Add the following line to the file, replacing the one that starts with ```
/dev/hda1
```:
```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```
If you put tabs in rather than spaces, it should all line up neatly (I don't think this is necessary).
Save the file.
Enter
```
sudo mount -a
```
in the terminal and press Enter.

This, as far as I know, should set things up so that the Windows partition is mounted when you boot up with all users given permission to READ ONLY (I've heard that writing to NTFS partitions with Linux can cause serious data corruption).

I can't really tell the difference between what you've described and what I've done, but where you say you don't know what to put, try copying the line I've used exactly
```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```
I remember it took me a couple of tries and a bit of searching of forums etc to get it right.

Update:

For clarity, here's the contents of my /etc/fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1	/media/windows	ntfs 	umask=0222 	0 	0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Mustard on 2005-12-29
I think you will find the option is **umask**, not **unmask**.  Hopefully someone can confirm this.

---

### Post by Gimbo on 2005-12-29
[QUOTE=Mustard]I think you will find the option is **umask**, not **unmask**.  Hopefully someone can confirm this.[/QUOTE]

Yeah, that's probably the problem. I encountered a similar hitch when trying to unmount something - I used "unmount", when the command I needed was "umount".

---

### Post by appdx on 2005-12-29
I tried doing
sudo mkdir /media/windows
sudo gedit /etc/fstab (where I added /dev/hda1   /media/windows   ntfs   unmask=0222) then saved it
sudo mount -a

and i got 
 wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Mustard on 2005-12-29
The guide at help.ubuntu.com has this information on mounting a windows drive...

[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

You need to read the above information on using umask and not unmask as you have been doing, as well.

---

### Post by Gimbo on 2005-12-29
[QUOTE=appdx]I tried doing
sudo gedit /etc/fstab (where I added /dev/hda1   /media/windows   ntfs   unmask=0222)[/QUOTE]

Try putting
```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```
where you put
```
/dev/hda1   /media/windows   ntfs   unmask=0222
```
and see what happens (that's the only difference as far as I can see).

---

### Post by appdx on 2005-12-29
haha ok, it is umask not unmask. Which i just realized is in the other post there. so that worked, thanks a lot! Also, I'm trying to stream media from a server on my home network but when i try to add it to rythmbox it doesn't add it to the library, and when i plug in my ipod and use GTKpod I'm missing codecs to play these audio files...are there any packages I can get on synaptic for audio codecs?

---

### Post by Gimbo on 2005-12-29
From my limited experience, Rhythmbox seems to be based largely on something called GStreamer, and to get the right codecs you need to install some packages for GStreamer. This can probably be done in Synaptic if you know which packages you're trying to install.

I'd advise checking out [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats"), which has advice about getting various media files to play.

If you haven't done so already, you'll need to enable the "Universe" and "Multiverse" repositories (see [https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto") or do a search for "ubuntu repositories" or something similar). There's various ways to do this, but that guide's a good starting point.

---

### Post by appdx on 2005-12-29
I installed the packages gstreamer0.8-plugin and gstreamer0.8-multiverse and rythmbox works fine now...I also added nls=utf8,umask=0222 to the fstab so it shows it in american english and makes it read only :p
thanks for all the help guys!

---

### Post by TikkiRo on 2005-12-31
[COLOR="Purple"][FONT="Trebuchet MS"][SIZE="3"] I've just installed this system yesterday having played about some with a boot disk option only (Knoppix).  Haven't tried out this particular option for mounting my Win drive but wondered if like Knoppix has, is there no easier method to do so during a session i.e. without having to code and reboot?  Or does the coding make it a more permanent feature so more sensible to do it??  :) 
[/SIZE][/FONT][/COLOR]

---

### Post by appdx on 2005-12-31
well I didn't have to reboot, after editing and saving the /etc/fstab to say /dev/hda1 (this is my windows partition) /media/windows ntfs nls=utf8,umask=02220       0
(all spaces are tabs) then in terminal doing sudo mkdir /media/windows then doing sudo mount -a my windows drive appears under places (I have it so it doesn't show mounted drives on my desktop). It's really not that difficult.

---

### Post by TikkiRo on 2005-12-31
[SIZE="3"][COLOR="Purple"]  Hmm - maybe things aren't working this way for me cos I'm trying to apply a fix for a different setup or something.  Ok - I have 2 drives with XP on my #1 primary dirve and UB on a primary partition (H) of the #2 drive.  Looking in my directory think perhaps I've missed something in this.  Don't have an FStab dir in my Etc directory as yet despite having coded as given here.  Presume I need to redo all of that again?  The drive partition I'm particularly seeking to mount is F if that's any help in perhaps providing me a coding 'fix'?  Thanks for your speedy reply.:) [/COLOR][/SIZE]

---

### Post by appdx on 2005-12-31
if you get gparted from synaptic it will show you where you linux partitions are and where you windows partitions are so you can edit into the ftsab...but you say you don't have ftsab? In terminal use sudo gedit /etc/fstab

---

### Post by TikkiRo on 2005-12-31
Apologies - forgive my denseness here - Synaptic??  Website or something within Ubuntu?  Couldn't google it.

---

### Post by appdx on 2005-12-31
Synaptic Package Manager...System>Administration>Synaptic Package Manager

---

### Post by TikkiRo on 2005-12-31
[COLOR="Purple"]Tks - now stuck on trying to mount the beggars.  Getting continual error msgs following the instructions in the guide.  Could I perhaps try your patience a stretch further with this lot if you can make any sense of it??

romayne@Linux:~$ mount
/dev/hdd3 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

Now although not accurate in respect of Windows partitions, Gparted shows I have 3 NTFS partitions - I think the one I want to mount is hda3 but all 3 are showing an error stating the contents can't be read :(  Methinks I've probably screwed something up bigtime somewhere along the way with all my earlier attempts to get this done perhaps?  Any ideas?[/COLOR]

---

### Post by appdx on 2005-12-31
Did you edit the /etc/fstab like i showed you? If you did...simply save that file, go into terminal do sudo mkdir /media/windows then do sudo mount -a and it should work...that's all i did for mine

---

### Post by Omnios on 2005-12-31
You might want to read this it is an article on understanding fstab, I found it realy benifial whan I was just starting with Ubuntu

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by TikkiRo on 2005-12-31
[COLOR="Purple"]ok - think I see the problem now - my hda1 is a Fat32 partition rather than NTFS (I know, silly beggar aren't I?) - tried it anyway, and although I didn't get an error msg on it, can't see any sign of the drive - just going to do a reboot anyway now in the hope of sorting out a few other glitches.  But a LOT clearer now thanks - appreciate your patience as i said. :)[/COLOR]

Sunday - got it reasonably sorted - for one partition at least - now trying to see if I can get the others hooked on as well.  Thanks again for all your help. :)

---

