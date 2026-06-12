---
title: "Noob - Do I need to reinstall??"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by skipdog0420 on 2006-07-17
When I installed umbuntu I didn't create a root account... when it asked for one I put in my user account and expected to be able to add more right then... So now I cannot log in as root... is there a way to do this? a default password???

Thanks
David

p.s. I apologize if this was not the best place to post this.

---

### Post by scxtt on 2006-07-17
don't worry about root, preface any command you'd want to run as root w/ sudo ... then enter your user password ... for example - **sudo apt-get update** ... as long as your user can use sudo, this'll work like a charm - and the 1st user created when you install is considered the 'administrator' and given root privilege ...

---

### Post by skipdog0420 on 2006-07-17
Thank you I'll try...

---

### Post by meng on 2006-07-17
Check this out:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by skipdog0420 on 2006-07-17
what I'm actually trying to do is mount my windows partition and it says I need root priveleges to install... I don't know how to do this in a shell... is there any way to use sudo in the GUI

---

### Post by scxtt on 2006-07-17
if you're using Gnome, type **gksudo 'name of program you want to use as root'** and if you're using KDE, it's something like kdesu ...

---

### Post by skipdog0420 on 2006-07-17
what program do i use in order to mount my windows partition... I just need to be able to manage/play music files ... I also get an error about the name of the partition/drive 

"error: '/' must not occur in label name

error: could not execute pmount
"

but for some reason im not getting the privelige error now

---

### Post by scxtt on 2006-07-17
i just use the command line, try something like:
[indent]sudo mount -t ntfs /dev/"windows_drive" /media/"already_existing_folder"[/indent]but of course replace the "" words w/ the correct values ... this assumes your using ntfs and doesn't really take into account the writing to ntfs problems you'll encounter ... i personally avoid ntfs ...

---

### Post by skipdog0420 on 2006-07-17
Thanks to everyone who responded to my problem so quickly... I am still having a problem...  What directory names do i use in this command the windows ones or the linux... but for now i am going to get some rest... i fear i'm losing my mind after 3-4 days of staying up late to reconfigure my computer use habits, lol

thx
david

---

### Post by Frank Golden on 2006-07-17
> **scxtt said:**
> i just use the command line, try something like:
[indent]sudo mount -t ntfs /dev/"windows_drive" /media/"already_existing_folder"[/indent]but of course replace the "" words w/ the correct values ... this assumes your using ntfs and doesn't really take into account the writing to ntfs problems you'll encounter ... i personally avoid ntfs ...
You technically can't write to NTFS not by default anyway and not without difficulty and great risk. That is good as it will keep you from accidentaly messing up your Windows install. The above command will only
mount per session. To mount at boot and have an icon on desktop
you can access your NTFS partition from (read only) follow aysiu's instructions in the link that follows.

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

If you have room you could also create a Fat 32 partition
that you could automount using the above instructions.
You would have full read/write priveleges. Then you could share
between your Ubuntu and Windows install.

---

### Post by Frank Golden on 2006-07-17
> **skipdog0420 said:**
> Thanks to everyone who responded to my problem so quickly... I am still having a problem...  What directory names do i use in this command the windows ones or the linux... but for now i am going to get some rest... i fear i'm losing my mind after 3-4 days of staying up late to reconfigure my computer use habits, lol

thx
david
David when you are rested read the link I posted about mounting
drives. 

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

This should answer your questions.

---

### Post by skipdog0420 on 2006-07-17
I managed to do it finally... but no luck on getting any sleep... to much construction going on around here...  

after making /media/windows i needed to set up system>administration>disks>partitions
then change permissions from a shell I also ran the auto-mount stuff located above so that I don't have to do this often

As far as writing is concerned I don't think I will be needing to do it anytime soon... I just want to install a hard drive (linux partition not big enough) transfer my media to it >>> Then >>> finally get rid of windows... which I'd been looking for a convinient way to do ever since the death of dos-based windows (3.x)

by the way is there a linux version of dosshell (manage files from non-gui but with basic tree view)

Thanks for all of the responses... it's great that with a little help and some research you can actually fix problems with ubuntu... unlike some other os's i can think of.........

---

### Post by skipdog0420 on 2006-07-17
oops forgot something.... I also enable the root user... you may be able to fix this problem without doing that but i like it better this way anyway.

---

### Post by Frank Golden on 2006-07-18
> **skipdog0420 said:**
> I managed to do it finally... but no luck on getting any sleep... to much construction going on around here...  

after making /media/windows i needed to set up system>administration>disks>partitions
then change permissions from a shell I also ran the auto-mount stuff located above so that I don't have to do this often

As far as writing is concerned I don't think I will be needing to do it anytime soon... I just want to install a hard drive (linux partition not big enough) transfer my media to it >>> Then >>> finally get rid of windows... which I'd been looking for a convinient way to do ever since the death of dos-based windows (3.x)

by the way is there a linux version of dosshell (manage files from non-gui but with basic tree view)

Thanks for all of the responses... it's great that with a little help and some research you can actually fix problems with ubuntu... unlike some other os's i can think of.........
Glad it's working out. You got me on a linux version of dosshell.
I'm sure somebody else here can help here.

---

