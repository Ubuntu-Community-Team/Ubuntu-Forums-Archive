---
title: "Ubuntu Software Questions"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-09-21
Can anyone tell me about these pieces of Windows software, and what the linux replacement would be, or if maybe there is a Linux version out there?


Norton Ghost:
Made for Linux?  What can I image my Linux HDD with?

Nero:
Seems like maybe they make a Linux version, not sure.

VNC:
I installed the VNC server and client from the Synaptic Pkg Mgr on Ubuntu, and it says that it is installed, but I can't find it in the Applications menu anyehere.

I'll probably think of some more later.

---

### Post by kidders on 2006-09-21
Hi there,

Unlike silly Windows, you don't need any special software to take a disk image. As for CD/DVD burning, I use cdrecord. It has some nice graphical front-ends, such as K3B.

Did you install the VNC server or client? You may need to log out & in to update your applications menu, maybe.

---

### Post by Kurdt on 2006-09-21
Norton Ghost:
I think you can do it with linux tools, but maybe someone with better knowledge could tell.

Nero:
Yes there is,  i prefer Brasero (aka bonfire)

VNC:
Server: You have to activate it from System - Remote Desktop
Client: You have it under Apps - Internet - Terminal Server Client - Choose VNC from the drop down menu.

I hope this helps

---

### Post by kc5hwb on 2006-09-21
> **kidders said:**
> Hi there,

Unlike silly Windows, you don't need any special software to take a disk image. As for CD/DVD burning, I use cdrecord. It has some nice graphical front-ends, such as K3B.

Did you install the VNC server or client? You may need to log out & in to update your applications menu, maybe.

OK, what do I use to make an Image, then?

I installed both server and client.

---

### Post by kc5hwb on 2006-09-21
> **Kurdt said:**
> 
Server: You have to activate it from System - Remote Desktop
Client: You have it under Apps - Internet - Terminal Server Client - Choose VNC from the drop down menu.

I hope this helps

Ok, I have done both of those things.  What port does VNC run on?  I need to forward it from my router?

---

### Post by kidders on 2006-09-21
There are many ways of creating disk images, but the one I tend to use is a plain disk dump, which lets you throw a byte-for-byte copy of an entire physical device into a file. Type "man dd" for more (perhaps too much!) info.

---

### Post by Kurdt on 2006-09-21
> **kc5hwb said:**
> Ok, I have done both of those things.  What port does VNC run on?  I need to forward it from my router?

5900, if you want to reach it from the outside i think yes.

---

### Post by kc5hwb on 2006-09-21
> **kidders said:**
> There are many ways of creating disk images, but the one I tend to use is a plain disk dump, which lets you throw a byte-for-byte copy of an entire physical device into a file. Type "man dd" for more (perhaps too much!) info.

I read some of this and it doesn't look like what I want.  Will it create a bootable CD to reinstall a pre-loaded image?

---

### Post by tagra123 on 2006-09-21
partimage  makes good partion backups. Its quick and does not backup blank areas of the filesystem.

Its not very hard to use either. I did read the instructions twice before using it. For it to work best run it from a live cd because the filesystem you are backing up cannot be mounted

Google for partimage --  all kind of good stuff.

I backup to a NFS network drive so when using the Live CD

I have to 

apt-get install nfs 
spt-get install samba ( if you are backing up to a windows share)
apt-get install partimage

Next, you mount to the network share or another partition (a backup partition)

mkdir /mnt/backups
mount -t nfs 192.168.1.XXX/compbackups /mnt/backups

and then

partimage

If you use systemrescue cd partimage is already there. I made my own Dapper Rescue CD with these goodies pre-installed.

---

### Post by kidders on 2006-09-21
No ... there would be no need for one.

It's my understanding that Norton Ghost exists because Microsoft refuses to acknowledge that most Windows users spend their lives resinstalling the thing, and build support into Windows for doing so easily.

With Linux on the other hand, all you'd need is to insert any boot disk/disc from virtually any distro, and a single "dd" command would let you completely rewrite a filesystem, or an entire disk.

**Edit:**

> partimage makes good partion backups.
Yep :-) Same deal, different tool.

---

### Post by ewl1217 on 2006-09-21
"Nero:
Seems like maybe they make a Linux version, not sure."

There is Nero for Linux, but you may want to check out free programs like K3B first.


"VNC:
I installed the VNC server and client from the Synaptic Pkg Mgr on Ubuntu, and it says that it is installed, but I can't find it in the Applications menu anyehere."

It's probably just a text-based program. Check with Synaptic to see which files were installed. The program itself should be located in "/bin", "/usr/bin", or something similar. Try running that from the terminal.

---

### Post by kc5hwb on 2006-09-21
> **kidders said:**
> No ... there would be no need for one.

It's my understanding that Norton Ghost exists because Microsoft refuses to acknowledge that most Windows users spend their lives resinstalling the thing, and build support into Windows for doing so easily.

With Linux on the other hand, all you'd need is to insert any boot disk/disc from virtually any distro, and a single "dd" command would let you completely rewrite a filesystem, or an entire disk.


So boot to a command line and then run "dd"?  Does this create an image, or copy and existing image to a new install?  Or both?

---

### Post by CatKiller on 2006-09-22
> **kc5hwb said:**
> So boot to a command line and then run "dd"?  Does this create an image, or copy and existing image to a new install?  Or both?

dd makes a bit-by-bit copy and puts it somewhere else. What it's copying and where it puts it is entirely up to you.

---

