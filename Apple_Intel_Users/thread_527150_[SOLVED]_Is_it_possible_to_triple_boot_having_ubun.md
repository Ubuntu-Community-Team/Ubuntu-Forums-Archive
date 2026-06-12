---
title: "[SOLVED] Is it possible to triple boot having ubuntu stuidos?"
date: 2007-08-16
forum: Apple Intel Users
---

### Post by kutos85 on 2007-08-16
Well last night I was trying to triple boot a macbook and I was following a howto. When I had the dual boot finished I continued reading through and it was asking for a live cd in order to install lilo and then edit the conf of lilo (forgot what the conf file on lilo was called or the path). I was really wanting to install ubuntu studios and remembering that you can install lilo instead of grub I tried it. I was thinking there was a way to edit the lilo conf file after the install but I wasn't 100% sure. Is there a way or can someone point me in the right direction? I have rEFIt installed and it detects the mac windows and linux partition. If I try to boot the linux partition it says it can't mount something along the lines that "boot=" but either way I figure in order to fix that I would need to edit the lilo because thats what boots after i click the linux partition in the rEFIt when the mac starts up.

---

### Post by ronocdh on 2007-08-16
Personally I don't use LILO; I never thought it was worth the trouble to set up instead of GRUB. I can say, though, that it is absolutely possible to triple boot using UbuStu. I believe the problem you are having relates entirely to LILO configuration and not at all to the fact that you're using UbuStu (you'd have the same problem with Feisty, I mean).

Sorry I can't offer more help on setting up LILO! Search the forums and maybe you can come up with what you need.

---

### Post by cyberdork33 on 2007-08-16
There are instructions on setting up lilo here:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

The error is likely due to the missing config info (The partition to mount for the kernel is not defined or something like that)

---

### Post by kutos85 on 2007-08-16
The only thing I don't get is how you are supose to triple boot if the ubuntu studios doesn't have a live cd. All the tutorials ask for the user to use a live cd.

---

### Post by cyberdork33 on 2007-08-16
> **kutos85 said:**
> The only thing I don't get is how you are supose to triple boot if the ubuntu studios doesn't have a live cd. All the tutorials ask for the user to use a live cd.
Are you talking about when you try to install a package? comment out the cdrom line in your /etc/apt/sources.list, and it will just download everything.

If that is not what you mean, can you link to the how-to you are using? that might give us idea of what you are talking about.

---

### Post by kutos85 on 2007-08-16
All I was saying is all the tutorials say insert a live cd and boot of cd. Then download lilo and configure everything. Ubuntu Studios isn't a live cd but it does have lilo as an option to install. So I did already install ubuntu studios with lilo on the linux partition but I don't know how I'm supose to edit the lilo if I can't boot into ubuntu. I get a mounting error and I'm assuming its because I need to edit lilo.

---

### Post by cyberdork33 on 2007-08-16
> **kutos85 said:**
> All I was saying is all the tutorials say insert a live cd and boot of cd. Then download lilo and configure everything. Ubuntu Studios isn't a live cd but it does have lilo as an option to install. So I did already install ubuntu studios with lilo on the linux partition but I don't know how I'm supose to edit the lilo if I can't boot into ubuntu. I get a mounting error and I'm assuming its because I need to edit lilo.

Oh, I see...
You can actually use any live CD. The point is to get a running linux system, mount your newly installed system, then you can access all the files on the system. I would recommend the normal Ubuntu Live CD just so that you have all the same tools that are likely referred to in the tutorial.

---

### Post by kutos85 on 2007-08-16
Oh ok that makes sense. I guess I was making it harder than what it was. Ok I will try that when I get home from work. Thanks a bunch!

---

### Post by kutos85 on 2007-08-18
Ok I'm still not getting this to work =/ I will try to explain everything with more detail.  I currently have a some what triple boot (Windows XP and Mac OS X work) It detects Linux but won't boot correctly.My problem is when I try to click the linux partition from  rEFit boot screen I get this message when its trying to boot up

VFS: Cannot open root device "sda3" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Ubuntu Studios is installed on sda3 with lilo on the sda3 partition. I recently downloaded ubuntu feisty fawn live cd and booted it up so I could edit the lilo.conf file. When it was booting up I got an error message 

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

(I have a MacBook Pro /w ATI Mobility Radeon X1600) I used this command to fix it which I found from [http://ubuntuforums.org/showthread.php?t=523135&highlight=x+server](http://ubuntuforums.org/showthread.php?t=523135&highlight=x+server)

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

Then it started up ubuntu. I then opened up the terminal and typed
sudo su
cat >/media/disk/etc/lilo.conf <<EOF
boot=/dev/sda3
timeout=5
default=Linux

image=/boot/vmlinuz
label= Linux
read-only
root=/dev/sda3
EOF

I then restarted and I get that error up top when I try to boot off the linux partition. I tried reading tutorials but I haven't found one that explains how to install with a nonlive cd.

---

### Post by ronocdh on 2007-08-18
You don't need a "live CD" to perform this installation. I triple boot and I never use the live CD, as I encounter the X failure, and that bothers me. I always use the alternate install CD, as that's text-based, and I can finish the installation without X nagging me. Only after the installation is complete do I have to install and briefly configure fglrx.

---

### Post by kutos85 on 2007-08-18
is my lilo.conf file correct or did I set it up wrong?

---

### Post by Jazztux on 2007-08-18
Can u post all your lilo.conf file? ;)

---

### Post by pxwpxw on 2007-08-18
And when/how did you run /sbin/lilo, which is essential after any change.

---

### Post by kutos85 on 2007-08-18
> **pxwpxw said:**
> And when/how did you run /sbin/lilo, which is essential after any change.

I just tried to boot the linux partition from rEFIt. I installed lilo through ubuntu studios. I hope that answers your question I'm still some what new to linux. Here is the lilo.conf

boot=/dev/sda3
timeout=5
default=Linux

image=/boot/vmlinuz
label= Linux
read-only
root=/dev/sda3

---

### Post by pxwpxw on 2007-08-18
There is no "initrd" entry in lilo.conf.
Can you check what is in the /boot directory  for vmlinuz and initrd* - is there an initrd as well as vmlinuz?
in other words where xxxx is wherever you have it mounted when runnig the CD rescue.
```

 ls -l /xxxx/boot

```

Edit:

Dont know if you are using this reference

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

There is some relevant lilo stuff re lilo in here, your numbers may vary from this of course

> 
 nano /etc/lilo.conf

Contents of file:

 boot=/dev/sda3
 default=Ubuntu

 map=/boot/map
 delay=20
 image=/vmlinuz initrd=/initrd.img
 root=/dev/sda3
 label=Ubuntu
 read-only

and then note that you must run lilo, and I think you can get better diagnostics using lilo -v
(try man lilo for more info, I dont have it on this box)
```

 sudo lilo -v

```

---

### Post by kutos85 on 2007-08-18
It seems no matter what I edit in the lilo.conf file I still get the same error when I try to boot up the partition.

---

### Post by cyberdork33 on 2007-08-18
> **kutos85 said:**
> It seems no matter what I edit in the lilo.conf file I still get the same error when I try to boot up the partition.
Are you positive that is the correct partition? The error says it cannot mount the file system on /dev/sda3. Can you post your partition layout?

---

### Post by kutos85 on 2007-08-19
Ok I finally got it :D I wasn't aware that you could just install grub on the linux partition and rEFIt would detect it. Now I need to figure out how to have the grub timer down to almost nothing but I'm sure I can search these forums and find that answer. One day maybe I will understand lilo alittle bit better to beable to use that instead but until then I have an alternate solution.

---

### Post by cyberdork33 on 2007-08-19
> **kutos85 said:**
> Ok I finally got it :D I wasn't aware that you could just install grub on the linux partition and rEFIt would detect it. Now I need to figure out how to have the grub timer down to almost nothing but I'm sure I can search these forums and find that answer. One day maybe I will understand lilo a little bit better to be able to use that instead but until then I have an alternate solution.

Why is grub the "alternative"? Grub is the default. I was thinking you wanted to use the other for some reason.

All the grub options are on the /boot/grub/menu.lst file. There, you can change the timer.

---

### Post by kutos85 on 2007-08-19
Well all the tutorials I read never stated that you could use grub instead of lilo so thats why I was thinking it was the alt.

---

