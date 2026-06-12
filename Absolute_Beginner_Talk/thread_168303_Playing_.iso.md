---
title: "Playing .iso"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by topic58 on 2006-04-30
Hi all, is there any way I can play an .iso in VLC or some other player? I got an .iso from a DVD-movie. (copied a DVD-movie to my harddrive using right-click and copy disc to .iso)

---

### Post by encompass on 2006-04-30
ok... an ISO is the direct copy of the image itself... you may be able to mount the device with 
> sudo losetup /dev/loop0 FILENAME.iso
sudo mkdir ISO_DRIVE
sudo mount /dev/loop0 ISO_DRIVE

The using vlc, somehow, look at that DIR you made, ISO_DRIVE and the information of the dvd will be there...
A MUCH better way is to rip the dvd to a simpler format like AVI or MPEG.  But that is another story.
Hope this helps.

---

### Post by topic58 on 2006-04-30
Okay, I got it working by doing this: I mounted my existing iso under media. Using that iso to rip the .iso in Acidrip.

sudo mount /home/myname/myname/DVD/file.iso /media/iso/ -t iso9660 -o loop

Just to open whose files in VLC. :-D 

Hey thanks you got me on to the right track here!

---

### Post by encompass on 2006-04-30
I would try just click on one of the files... and do you have to use vls?  mplayer and other can do it.  I would get the dvd and rip it to the drive.  That would be your best bet.  As it is a movie and all... you should have the original unless you are using an illegal copy.:-D

---

### Post by topic58 on 2006-04-30
No worries, it's a recording from television. :)  We don't want any illegal stuff here, do we? [-(

---

### Post by majstor on 2006-04-30
You can use this scripts  if you need to play/mount  isos often:

[http://www.ubuntuforums.org/showthread.php?t=87369](http://www.ubuntuforums.org/showthread.php?t=87369)

---

### Post by clarkth on 2006-04-30
I would think that VLC could play the iso directly (open file).  I haven't tried this in Ubuntu or Linux, but it works that way in Windows XP.

---

### Post by howbag on 2006-05-04
It can. Or atleast a little :P
I just opened my mounted DVD.img (similar to iso) **folder** in another application --> VLC, found out it freaked out, so I opened it in totem. Worked like a charm.

if that didn't make sense:
mount the img, iso or whatever in a folder, open the folder in your desired videoplayer, or try a new player if it didn't work.

---

