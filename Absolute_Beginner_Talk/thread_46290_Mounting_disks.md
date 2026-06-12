---
title: "Mounting disks"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-04
After finally getting Ubuntu to work, I have tried to add new apps, but I cannot mount my disks!

First. I open the simple GNOME/Nautilus desktop. If I add my password and username I cannot get root privelages. The only way I can get root, is via the command lines. So all files and changes and importing I try via the desktop give me a "permission denied." I cannot even start the the Application launcher. I have worked around it a bit by assigning files to myself from the CLI. But that is such a royal PIA!!! What am I doing wrong to get permission to my system on the desktop. So far nothing in the manuals I have is working. 

My problem now is to get new programs and apps. Here is the catch. I have to download with XP, so my download sits on that disk. But I cannot mount any disk. Not via the CLI or the Desktop. The diskmounter under desktop give me the "permission denied" thingy, back to password.... Not that I think it will work in any case. I've checked and double checked and can assure you I am mounting the correct disks. In my case it is hde1 and hdf1.

I think if I can get past that problem I should be able to get my printer and scanner and sound and modem and bluetooth and whatever the heck up and running.  But I have to mount first. Please help!!!!

BTW. A friend is having the same problems with installing Ubuntu. We certainly have no joy with the installation.

---

### Post by sapo on 2005-07-04
take a look here:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

if you want to run nautilus as superuser open a terminal and type: gksudo nautilus

you have to use sudo to mount your disks and all that stuff  :-P

---

### Post by f1dave on 2005-07-04
If you would like a good idea of how something like an fstab should look for a read only ntfs partition, look here:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
... lots of other devices- usb, etc...
/dev/sda1       /media/windows  auto    ro,user,umask=666   0       0

Important things to note are the ro for read only, and the umask which allows normal users (without sudo) and applications such as amarok to read say mp3s from my windows partition.

---

### Post by GrootBrak on 2005-07-04
[QUOTE=sapo]take a look here:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

if you want to run nautilus as superuser open a terminal and type: gksudo nautilus

you have to use sudo to mount your disks and all that stuff  :-P[/QUOTE]
 Thanks tried the command, but then I get a "cannot open graphical interface" or some similiar meaning. Cannot recall the excact words now. It basically boils down to nautilus not working. When I do an "ls -a" command the only nautilus words is a .nautilus file. (Note the dot. Is that correct?) Then again why does nautilus launch by itself? I switch to another interface, usually CTRL-ALT-F4. I can change to superuser there but not back to nautilus unless I use F7. 

In the CLI I can run the command to mount a disk, but it always fails. I have already sucessfully added the directory as superuser. Maybe I'm just too bloody stupid to work with Linux!!!

---

### Post by GrootBrak on 2005-07-04
[QUOTE=f1dave]If you would like a good idea of how something like an fstab should look for a read only ntfs partition, look here:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext3    defaults        0       2
/dev/sda4       none            swap    sw              0       0
... lots of other devices- usb, etc...
/dev/sda1       /media/windows  auto    ro,user,umask=666   0       0

Important things to note are the ro for read only, and the umask which allows normal users (without sudo) and applications such as amarok to read say mp3s from my windows partition.[/QUOTE]
 Thanx. Some of the things makes sense, for instance the umask. I've tried to run the fstab, but it comes back with a "file/command not found." Sorry, I can't always recall the excat words, even though I write it down, I never take my papers to work! And believe me, I have quite a few pages full!!! On that topic, I cannot even extract tar/zip files to disk yet, because I don't have permission. I still have to learn doing it in the CLI!!!

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=GrootBrak]Thanx. Some of the things makes sense, for instance the umask. I've tried to run the fstab, but it comes back with a "file/command not found." Sorry, I can't always recall the excat words, even though I write it down, I never take my papers to work! And believe me, I have quite a few pages full!!! On that topic, I cannot even extract tar/zip files to disk yet, because I don't have permission. I still have to learn doing it in the CLI!!![/QUOTE]


Did you make the directories that the window's drives mount to?

---

### Post by topoftheworld on 2005-07-05
I have mounted my ntfs disk (I think)
but now when I try to access it (cd /media/windows) it says permission denied.
I have also tried (sudo cd /media/windows)

I am inexperienced at linux by the way. :P

---

### Post by f1dave on 2005-07-05
Please post the command you used to mount the drive, or the appropriate section in your /etc/fstab.

---

### Post by topoftheworld on 2005-07-05
thanks for the quick response,

sudo mkdir /media/windows
sudo mount /dev/hdc1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

then the second line didn't work for some reason (didn't keep terminal open ;o)

so I just entered this

sudo mount /dev/hdc1 /media/windows/ -t ntfs

now I see windows dir in media directory, but yea, permission denied

---

### Post by GrootBrak on 2005-07-05
Folks, I tried to post last night, but my server went down. Let me tell you something, there is Guides and there is GUIDES. The unofficial UBUNTU guide find on this forums had it right. 

Thanx SAPO!!! Here is the link.  [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs). 

I typed in excactly what it tells me, and my disks appeared in good order. (That after I looked at least at a dozen guides.) Just remember to make a directory first. (At least I understand that bit after creating almost one directory per guide!!) Unfortunately the above guide was no help in getting Nautilus working....

My problem was to add the disks to fstab. As i've said before, I get a "cannot open display" error when I work in the CLI. the command "gedit" give me the same result. The command "gksudo nautilus" have the same result. In the end I did a "chown" to myself, went into Nautilus desktop with ALT-F7, opened fstab, add the two lines, saved it, changed owner back to root, and now its working. Phew...

Now please, why do I get the "cannot open display" while trying to run programs from the CLI? Remember that ALT-F7 gets me back to my desktop, so it *should* work?

---

### Post by aysiu on 2005-07-05
[QUOTE=GrootBrak]I've tried to run the fstab, but it comes back with a "file/command not found."[/QUOTE] Let's slow down here. First of all, you don't run fstab. *fstab* is not a command. It is a file. The file lives in a directory called /etc.

The first person who responded gave you everything you need to know. You need to edit the fstab. What happens is when you boot up your computer, Ubuntu consults the fstab to see what to mount, where to mount it, and whether it's mounted read-only or read/write.

Follow the instructions exactly at

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

When you type *sudo gedit /etc/fstab*, the text editor will open up the fstab file for you to edit. You need to know what partition your NTFS (Windows) partition is. Is it /dev/hda1? It could be. You have to find that out. Then, you cut and paste the appropriate line into fstab with the appropriate /dev/hd#.

It sounds to me as if the command-line is a bit much for you right now. Have you considered trying Mepis? Mepis puts all partitions on the desktop automatically (whether they are mounted or not--if you click an unmounted one, it will mount and open). It also has an icon you can click to browse folders as root. Ubuntu's great if you don't mind the CLI, but I have a feeling you might have more fun with Mepis.

---

### Post by topoftheworld on 2005-07-05
not sure if that response was directed at me, but
i retried with umask=0000 and it worked. I guess umask operats sort of like chmod?

---

### Post by GrootBrak on 2005-07-05
[not sure if that response was directed at me]
Hey topoftheworld, I think it was directed at me!!! 

[First of all, you don't run fstab. fstab is not a command]
Got that, got mixed somehere, I can now see why it looks confused. the command "gedit fstab" with its path, gave me the file not found, I initially had the wrong path. (I often use caps indiscriminately, and then wonder why the file is not there!!! Some things are hard to unlearn...) With the correct path and file, the reponse by running "gedit" is "cannot open display". Please see my previous and new posts how I rectified the mounting problem.

 BTW. Never heard of Mepis. (And I think about 5000 other Linux programs!!!)

---

### Post by GrootBrak on 2005-07-05
Of the track. How do you get the neat quote brackets? Mine did not work at all as seen in my previous mail. Darn.

---

### Post by f1dave on 2005-07-05
[QUOTE=GrootBrak]Of the track. How do you get the neat quote brackets? Mine did not work at all as seen in my previous mail. Darn.[/QUOTE]

Like this you mean?
By hitting the quote button in the bottom right.

---

