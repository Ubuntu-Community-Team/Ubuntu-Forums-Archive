---
title: "Mounting an NTFS partition in &quot;Hoary Hedgehog&quot;"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Irdin on 2007-05-05
Hi there.
I have WinXp (2002 with SP2) installed on an NTFS partition. I am able to boot it but there seems to be no way to get it to run as it puts out a quite strange error page. I SUPPOSE it's the hdd (physical).
On the same hdd, I have a working but old version of ubuntu: 5.04
I installed it some long time ago to try it out and now it happens to be probably the only chance to regain access to the files stored on the Windows partition, that I need.
Being a beginner in using linux I started reading the online documentation and searching some forums. I learned that in order to mount a NTFS partition I would need a working driver . What the NTFS-3G project does sounds fantastic but I can't figure out if it would run on my old ubuntu version. Unfortunately I am not able to install a newer version of ubuntu at this time for some complicated reasons and I cannot access the internet while in ubuntu because of much, much more complicated reasons (no linux driver for directly connected crappy isdn device).

Please, if you know a way to mount an NTFS partition with ubuntu 5.04, help me.

Thank you for reading.

Irdin

(As a reference: I basically used [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G))

---

### Post by cotcot on 2007-05-05
Have you tried with this line in your /etc/fstab ? > /dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0  where hda1 is the ntfs partition you want to mount.
I am not sure that ntfs-3g is the hoary 5.04 repos because ntfs-3G is much more recent than hoary.

A question that many people will have reading your post is why you do not install a more recent version of ubuntu. If you install Feisty you will have ntfs partitions mounted out of the box.

---

### Post by aysiu on 2007-05-05
I don't believe Hoary is supported with security updates any more. You should upgrade to a new version... or install a newer version.

---

### Post by Irdin on 2007-05-05
Actually, putting that line in /etc/fstab (plus the gksudo command and so on) was the first thing I tried.
I understand that it is not reasonable using Hoary Hedgehog any longer. It will take some days getting Feisty. I just thought there might be a way mounting the windows partition under Hoary, which would have saved me the time as I need to get those files asap.

Thank you for your replies.

Irdin

---

### Post by aysiu on 2007-05-05
The line in /etc/fstab should work.

Let's try mounting it manually. Can you post the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Just copy and paste those into the terminal and then copy and paste back here the output.

---

### Post by Irdin on 2007-05-07
(As I certainly cannot gain internet access under linux I have to type the outputs off the other screen. System language is German, I'll try to translate the terms)

Before trying something:
The man page for fstab says (in the chapter about the third field: vfstype) that the supported systems can be found in /proc/filesystems and there is NO entry for hpfs or ntfs. As a result, using that type in fstab and mounting returns: unknown systemtype "ntfs".

Thank you for your help. Here are the Outputs:

Output of "sudo fdisk -l":

```
Device		boot.	Start	End	Blocks		Id	System
/dev/hda1	*	1	1275	10241406	7	HPFS/NTFS
/dev/hda5	*	1276	2431	9285538+	83	Linux
```


Output of "df -h":

```
File System	Size		Used	Free	Used%	Mount Point
/dev/hda5	8,8G		1,4G	7,0G    17%	/
tmpfs		94M		0	94M	0%	/dev/shm
/dev		8,8G		1,4G	7,0G	17%	/.dev
none		5,0G		2,8M	2,3M	55%	/dev
```


Output of "cat /etc/fstab":

```
<file system>	<mount point>	<type>		<otions>			<dump>	<pass>
proc		/proc		proc		defaults			0	0
/dev/hda5	/		ext3		defaults,errors=remount-ro	0	1
/dev/hdc	/media/cdrom0	udf,iso9660	ro,user,noauto			0	0
/dev/fd0	/media/floppy0	auto		rw,user,noauto			0	0
```


Thank you,

Irdin

---

### Post by aysiu on 2007-05-07
Try pasting these commands into the terminal. If you get any errors, post them back here:```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
cd /media/windows
ls
```

---

### Post by Irdin on 2007-05-08
Wow. It worked.
Thank you all for your help!

Just if someone has got the time and for me to learn something out of this: Why does it work? Where is the difference in mounting with fstab?
Could somebody explain that to me?


I just ordered a feisty live-cd. I'll switch to linux-only now.

---

### Post by aysiu on 2007-05-08
Well, now that we know it can be mounted manually successfully, go ahead and add it to your /etc/fstab: ```
sudo nano -B /etc/fstab
``` Add in this line at the end of the file: ```
/dev/hda1/media/windows ntfs nls=utf8,umask=0222 0 0
``` Then save (Control-X, Y, Enter), and it should be mounted every time you boot.

---

