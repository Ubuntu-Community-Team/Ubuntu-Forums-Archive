---
title: "How to uninstall Ubuntu?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by killertofu on 2007-10-15
Here's my setup now:

Windows NTFS partition, 15gb
/ partition, 15GB
swap 2GB
/home partition, 140GB

How do I get back to a single install of Windows?

I wanted Linux to work, I drooled over the prospect of learning a new way of doing things (I am geeky like that), however, Ubuntu is a no go for me.
Gutsy gave me the white screen of death, installed feisty, and guess what? Feisty does too! ](*,)

Now, I just want my old setup back, or at least something close to it.

I have a Windows Restore disc that I burned before I partitioned my hd, installed ubuntu and ruined my life, lol.
How do I go about this? o.o

Any advice will be appreciated. It's a bummer that Ubuntu won't work for me now, but maybe someday I'll be back. (It's just too sexy to forget about for good, lol!)

---

### Post by dwhitney67 on 2007-10-15
Try a different Linux distro that ships on a DVD.  They tend to have more video an h/w drivers available on the media than Ubuntu.  Still though, very strange that Ubuntu did not set up.  Why were you attempting to use a beta-release anyhow?

If you still do not wish to use Linux, then so be it.  Use fdisk (or equivalent) to blow away all of the partitions on your HDD so that you can reinstall Windows onto a clean slate.

---

### Post by oodledoodle on 2007-10-15
sorry to hear its not working out for you! its always a struggle to get into linux when you cant even get a basic desktop to load for the first time, i had the same problem. 

can you use your ubuntu live cd at all? if so, open up a terminal and type "sudo gparted" at the prompt. 

now, be careful at this point. you will want to make sure any irreplacable data is backed up somewhere safe. 

if you can get into gparted, the ui should be fairly straightforward. you should be able to delete your linux partitions from there and expand your (ugh) windows partition to reclaim the rest of the disc. there are plenty of more in-depth faqs out there for gparted which i would reccomend reading if this is your first time resizing partitions in this manner.

i would suggest waiting until gutsy is released to the general public and try it again though. at the moment it is in development, so it probably wasnt a good time to be trying it if you're new to linux!

---

### Post by Hospadar on 2007-10-15
you just need to delete all the ubuntu/linux/swap partitions and then enlarge the ntfs partition to the whole disk.  you might need some third-party tools to do the partitioning, i'm not sure if windows itself can do it, but try right-clicking on my computer (or c:\ maybe?) and go to manage, I believe that's where the windows partitioner is.

Also, what's your hardware setup, if you can boot off a livecd, you should be able to install with maybe a little setup.

---

### Post by lopez1941 on 2007-10-16
Did you try booting with the noapic nolapic commands to the kernal.  I hope I said that right.  I have a Compaq laptop with an NVidia graphics card.  I had to tell the kernal, noapic nolapic.  It booted right up.  I was then able to install the NVidia drivers.  Don't give up yet.  It's easy to freak out but almost everything in Linux can be fixed one way or another.  Donnie.

---

### Post by killertofu on 2007-10-16
Thanks you guys. :D

I just want to go back to Windows for now, but....I will always be inclined to give Ubuntu another shot, even if it's really just an excuse to be a part of such an awesome community.

If only the rest of the world was like you.

---

### Post by bodhi.zazen on 2007-10-16
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Best of luck and come back soon

Dual boot ?

---

### Post by raydeen on 2007-10-16
Once you get your Windows back, your best bet for safely and non-destructively trying Linux again would be to use Virtualbox.


[www.virtualbox.org](www.virtualbox.org)


It will let you install a guest OS inside of Windows (or Mac, or Linux - I'm currently doing the daily update to Gutsy on my work MacBook) and use it as if it was a totally seperate machine. If you don't like, you just delete the virtual machine and start another one. You won't get the fancy graphics and such as VBox doesn't currently support any kind of 3D acceleration, but you'll get just about all the other benefits of whatever OS you're using. I currently have Gutsy and Win2K machines and just load them up whenever I need that Win or Mac fix. The only thing with VBox is that AFAIK you can't share files between the guest and your regular OS aside from copying them to a portable drive or emailing them to yourself. Little bit of a hassle but it's free so I don't complain. :)

---

