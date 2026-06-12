---
title: "Samba with XP and Qemu"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by n1tro on 2005-08-22
Hello,

Is there a really, really easy step by step guide to setting up samba so that I can have access to the files I saved using XP under Qemu?  I've read bits and pieces all over the place and it's gotten me nowhere.  A lot of the how to guides take for granted that people reading are somewhat literate with linux and stuff between the lines.  

I am a complete n00b.  I know nothing between the lines, especially in linux.  If a how guide skips an "easy" step, I'm lost :(

So what I gotten so far from reading bits and pieces of "how to" samba guides is this...

step 1. install samba <--- easy enough...done that...whats the rest?!  ](*,)

---

### Post by tonysathre on 2005-08-23
create a FAT32 partition
put in the ubuntu install cd, when it gets to the partitioning part resize one of your partitions so you can create a new one, format as a FAT32 partition because both linux and windows can read and write FAT32, give it a label like windows or something so its easily identified. after this go back to the main menu and reboot, when you boot into windows you will get a light blue screen that says a fatal error has occured or something to that effect and must run scandisk, dont worry about this you havent ruined anything, let it run scandisk, after this it should finish booting, it might say that new hardware has been detected and installed and must restart the computer before you can use the new FAT32 partition, try using it, if not reboot
thats it, you can now share files back and forth between linux and windows...to access your share open a terminal and type cd / and hit enter, then type ls and you should see a directory named whatever u labeled it

---

### Post by n1tro on 2005-08-23
So how do I make a fat32 partition?  Booting up the disc makes it go through the process of installing ubuntu again...and I'd rather not lose what I have set up so far.  Downloading QTParted or GParted doesn't seem to want to let me use some of the free space left over on my HD to make a separate partition on the fly like Partition Magic in Windows.

---

### Post by GrumpyBob on 2005-11-13
I'm not sure Tonysathre is answering your question.  If I get this right, you are using qemu to run WinXP within Linux, and you wish to access folders on the HD (either on the WinXP ntfs partition or on the Linux partition) from WinXp running within qemu on Linux.

I am in a similar position.  I have installed qemu, and Win98SE within qemu.  I think I need to use samba to share the Linux partitions with the Win98SE.  Now, I have in the past set up samba on the home network, but this succeeded more by trial and error than expertise.

I haven't so far managed to get samba set up to allow file sharing as I need it!
Any clues would be most welcome (sample smb.conf files might help!)

Robert

---

### Post by GrumpyBob on 2005-11-15
OK, I now have Win98SE running in qemu using Ubuntu 5.10 as the host OS, and able to read my Ubuntu folders from within Win98SE.

I have set up samba, and followed the directions in the qemu doumentation, except (as pointed out by someone else in a long thread about qemu) use \\10.0.2.2\foldername.

My smb.conf is nothing out of the ordinary - I can email some of it if it would help.

Robert

---

### Post by nutubu on 2005-12-09
I struggled for quite a while to able to share files both ways between the guest(Windows 2000) and host(Ubuntu Hoary) of qemu. The ideal solution is to run Samba since you can play with files directly from the applications (not the case with ftp).  I finally sorted it out.

If you decide to use a samba server started by qemu with the switch -smb, you need to:
[B]
1) Stop an already running samba by issuing:
sudo /etc/init.d/samba stop

2) Run qemu as root, i.e. starting it with sudo

Note that in this case the content of /etc/samba/smb.conf is irrelevant because qemu creates its own on the fly in the /tmp directory. I wasted a good deal of time playing with /etc/samba/smb.conf not knowing that it was irrelevant.
[/B]

If you feel comfortable with the configuration of your own samba server with the file /etc/samba/smb.conf, I suggest you go for it. You will be able to configure the server exactly like you want.

Personally, when trying to access the samba server at \\10.0.2.2, the best I could get was a message from Windows saying that the user or password was wrong even though they were the same on both the guest and the host. I finally found my problem, I had to issue the following for each user id:
 smbpasswd -a userid

I found the answer by following this incremental howto: [http://www.troubleshooters.com/linux/samba.htm](http://www.troubleshooters.com/linux/samba.htm)

Note that I am running qemu 0.7.2 compiled from source with kqemu enabled.

I hope this will help someone.

---

### Post by rickyrockrat on 2007-12-04
NOTE: my username for the sake of this discussion is 'me', but it's not my real one.
When I tried this:
qemu-system-x86_64 win2000.ovl -smb /hom/me/tmp -m 384 -localtime
It kept asking me for a password, and contrary to what others have said, (the /etc/samba/smb.conf not being used) that was not true for me.  Here is the quick & dirty:
install samba
install qemu
EDIT the /etc/samba/smb.conf file, and add this down at the bottom somewhere:
[tmp]
    comment = tmp share
    path=/tmp/qemu
    browseable = yes
    public = yes
    guest ok = yes
    writeable = yes


This will be \\10.0.2.4\tmp on the windows side.
NOW do the sudo smbpasswd -a <youruser>, where <youruser> is whatever you use to login.
type in the windows-side pwd twice.:
sudo smbpasswd -a me

Then tell smb to reload (sudo /etc/init.d/samba reload)

The start quemu: NONE of this is using root, and since you are using windows, I strongly suggest you don't use root, since a virus on the windows box could possibly mess with the host OS.
Here is an excellent ref on creating the overlay file:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

