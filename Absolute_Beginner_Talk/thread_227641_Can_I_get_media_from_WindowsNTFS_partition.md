---
title: "Can I get media from WindowsNTFS partition?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-08-02
I'm dual booting Windows XP and Ubuntu 6.06 and all of my media (Video, and Audio) is on my Windows partition (which is NTFS): Can I access my vids and audio through Ubuntu? -I think I've installed all the necesary codecs via Automatix...but is it safe to access media stored on an NTFS partition through Ubuntu? And if so how would you suggest I import (and save) all this media to Ubuntu (ie: where/how should I create a folder* for storage in Ubuntu?]
-I hope I've made my questions clear enough -I'm very new to Linux.
Thanks for your time. 

*I don't even know enough to know if there *are* folders in Ubuntu -or what there equivalent might be in in the Linux world.

---

### Post by Dr. Nick on 2006-08-02
may try here
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

its very much possible to do

---

### Post by fiver22 on 2006-08-02
Thanks very much for the link -I'll definately try to grok my way through it.
I *am* very new to Linux and find the information a bit daunting -might there be a more simplistic explanation to my original question? -I'm not trying to be difficult and I *really* do appreciate your link (and will try to suss it out).
Thanks for taking the time to reply, Dr. Nick.

> **Dr. Nick said:**
> may try here
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

its very much possible to do

---

### Post by orb9220 on 2006-08-02
Ok first can you see your xp partition the one with the files.

If you can then yes all you do is browse or drag and drop the file into the music or video player of you choice. I had my music and video's on ntfs partition and could play them fine.

The only drawback is that you cannot rename,delete or edit them in any way.

If you want to do those write functions you will have to convert the ntfs to fat32 which is what I did so xp and linux could read and write to the partition.

If you want to go to all linux then you will have to move them to a linux partition or dvd's or another hardrive then reformat the ntfs to ext3 partition and move them back to there.

Hope this helped.

---

### Post by fiver22 on 2006-08-02
> **orb9220 said:**
> Ok first can you see your xp partition the one with the files. 

--Yes: I can see the files through Ubuntu.

> **orb9220 said:**
>  If you want to do those write functions you will have to convert the ntfs to fat32 which is what I did so xp and linux could read and write to the partition. 

--Is there a way to convert my NTFS to fat32? -if so: How?
--If I can convert my NTFS to fat32: how should I get ALL my music/videos over to my Linux partition? -I can select all the media but where do I copy it to in Linux -do I have to create a new directory (how do I do that?) or folder on the linux partition?

I'm sure that I can get my Linux media player to open ANY file from  WHICHEVER partition: but how do I get ALL of my media over to Linux?
 
> **orb9220 said:**
> Hope this helped.

-It has helped
Thanks, again, for your time.
Sorry to be a pain -I'll get it eventually.

---

### Post by orb9220 on 2006-08-02
Yes you can convert ntfs to fat32. I did it with windows program called partition magic on xp side. It is not a freeware program tho. you can search for xp programs that will do it. For linux I do not know if there are any linux programs that will convert ntfs to fat32. Maybe someone with more knowledge can clue you in.

Well if you have the room just go to your home folder and right click create folder and name it whatever you want. If space is not limited then you should be able to multi-select whatever folders on the ntfs that you want and right click copy. Then go to the new folder in your home directory and right click paste this will copy your ntfs files to there.

If you get a you do not have permissions dialog, then open a terminal and type:  gksudo nautilus
enter your password when asked. Now you should have permission to write  to home folder. and try again.

If You have the space then just copy everything over to whatever folders you create in your home directory. Then you can just go back and use a program like gpart to delete the ntfs and create a ext3 partition then  you can move everything back or just use the new partition to store new stuff.

If anybody here can think of other way or if I am leaving stuff out  please help out.

Thanks

---

### Post by cantormath on 2006-08-02
[http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)

---

### Post by benner on 2006-08-02
i got as far as this:

Now add your NTFS drive to your fstab file, so it will be loaded on boot up :
sudo gedit /etc/fstab
/dev/(your partition like hda1 or sda1) /media/(mount point) ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

my partition is hda1 and my mount point is a folder i called 'windowsC' (is that right?)

i'm just copying and pasting (with the obvious changes) and got this: 

"ben@ben-laptop:~$ sudo gedit /etc/fstab /dev/hda1 /media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
sudo: gedit: command not found"

i don't have an fstab file in etc  i am running kubuntu.  is it different?

what did i do wrong?

-benner

---

### Post by orb9220 on 2006-08-02
Try gksudo gedit /etc/fstab   I think the gksudo is for gui apps like gedit.

When it opens then insert
media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
into the fstab file. and save logoff then back on

---

### Post by orb9220 on 2006-08-02
media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

should be 

/media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

Sorry about that

---

### Post by benner on 2006-08-02
thanks for the quick reply.  

"ben@ben-laptop:~$ gksudo gedit /etc/fstab
bash: gksudo: command not found"

???

-benner

---

### Post by benner on 2006-08-02
thanks for the quick reply.  here's what happened...

ben@ben-laptop:~$ gksudo gedit /etc/fstab
bash: gksudo: command not found

???

-benner

---

### Post by orb9220 on 2006-08-02
That's wierd I just copy and paste  gksudo gedit /etc/fstab into the term window it asked for my password and then opened the fstab file in gedit.

You are running default gnome ubuntu?

---

### Post by orb9220 on 2006-08-02
Try

sudo nano /etc/fstab

That is the terminal based editor

---

### Post by benner on 2006-08-02
running kubuntu.  i just located fstab.  i must've mistyped something in the terminal, i guess.  i just right clicked on fstab, opened as root and put your lines in using the kubuntu text editor (Kate) and it seemed to work.  i will try to move on to the next step in the instructions on lunapark6.  wish me luck. thanks, again.

---

### Post by benner on 2006-08-02
I was able to get through all of the instructions.  (gedit is gnome, kate is kubuntu, figured that out) but the drives aren't mounted.  here's the error:

Could not mount device.
The reported error was:
[mntent]: warning: no final newline at the end of /etc/fstab
mount: according to mtab, /dev/fuse is already mounted on /media/windowsC
mount failed

here's the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hda5 /media/windowsE ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

is there something mising?

-benner

---

### Post by givré on 2006-08-02
The instruction on lunapark are just a copy of the ubuntu howto : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) which has been really improve since that time.
And people should stop to point to that blog but start to point to the ubuntu's howto. This is really important because now everything is in a repo, which will allow an automatic upgrade when the stable release will be out.

---

### Post by Dr. Nick on 2006-08-02
can you see your files on the windows partition? If so then your fstab is already configured. If that is the case then just open up konqueror and right click and thier should be a new folder option. from that point it is not much different to copy the files then it would be in windows

I wouldnt try anyhing with the fat32 convert at the moment, just get your files copied over, Changing it to fat32 wouldnt really make it easier. If you get any permission problems you can use 

sudo konqueror

then try it.

---

### Post by pomegranate on 2006-08-02
Dr Nick, that link fixed my problem! 
I'm a complete Ubuntu noob having just moved from XP a few days ago, and was desperately trying to access my saved files (gigs of mp3s, personal files, years of photos etc), on a **FAT32 external HD**. I worked through and experimented with the advice on that page, and it's working, fantastic!
Now to get on with getting mp3 playback working... :(

---

