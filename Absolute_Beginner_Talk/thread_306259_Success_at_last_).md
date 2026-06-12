---
title: "Success at last :)"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by MoiraA on 2006-11-24
I was determined to achieve this and I just thought I'd report that I actually have done it, yay!

I'm the useless person with all the problems trying to install Ubuntu/Kubuntu in this thread:

[http://ubuntuforums.org/showthread.php?t=189966](http://ubuntuforums.org/showthread.php?t=189966)

I got a new laptop which came installed with Windows Media Centre Edition, so I gave it one last go at installing Ubuntu on my old laptop.  I'm delighted to say, that while Ubuntu didn't seem to want to install, Kubuntu (after using the irqpoll option) has successfully installed - without trying to dual boot with Windows this seems to have worked without any problem at all.

I can see my Windows network immediately from the laptop, however as I expected, doing so in the other direction, ie viewing the kubuntu install from my Windows PC is a different matter.  When I had Suse 9 installed as a dual boot on the same laptop, I remember having to install and configure Samba to get a "two way" network.  I did save the samba config file before wiping Suse - will this be any use, and basically what do I need to do to be able to view files in Windows from Kubuntu?

My first impressions of Kubuntu are very good.  I like the OS very much and I hope to be able to, in the end, maybe use Kubuntu on the new laptop as a replacement for Windows.  It seems very user friendly, but this is my one difficulty.

---

### Post by rlozano on 2006-11-24
first, congratulations! :-)

second, you don't have to install samba in kubuntu anymore since it's within the installation. viewing files from your window files from kubuntu is alot easy.

konqueror is a very flexible AIO file manager. from the address location just type: smb:/xxx.xxx.xxx.xxx and you'll be able to get into your windows machine, or from the openeing screen of konqueror just select network folders then samba shares...

and btw, make sure that your files in windows are shared. :)

have fun and goodluck! if you have any problem, just post it here. im sure that the community will be always happe to help.

---

### Post by MoiraA on 2006-11-25
I can see the windows network from kubuntu with no trouble whatsoever - it was so much easier than I remember with Suse 9!  I just wondered if it ought to be as easy to do the other way round, ie will I be able to easily see the kubuntu install from my windows machine here?  At least I don't need to worry about mounting the windows partition of a dual boot setup as that is the only OS on the laptop now.  

I'm amazed how much more user friendly kubuntu/ubuntu is than Suse was when I first tried it, or mandrake before that.  It looks a really nice interface too.  If all goes to plan, I may make one of my computers run nothing else but linux - at the moment my only regret is that it's installed on a slow machine, however it runs kubuntu so much better than it did XP!

I just can't believe it's going to be a case of just adding a network place in the usual way and browsing to the kubuntu laptop without going through all sorts of horrendous samba configuration.  I have to say I haven't actually tried the networking yet as I've been busy with setting up my new laptop as well, with windows media edition.  I'll have a try with it tomorrow, but I'm sure it won't just "work" and was wondering what I needed to do to make it.

---

### Post by MoiraA on 2006-11-26
I really don't know where to begin to see the kubuntu install from my Windows network.  I managed to do this when I had Suse installed, but I remember needing some help to configure Samba and get it working.

Can someone tell me what to add in Network Places so that I can attempt to connect to this laptop?  Do I need the samba file that I used for Suse, indeed would this be any help if I replaced the Kubuntu samba file with it?

If I just got my network working in both directions as I did have with my previous linux install I'd be quite content, I reckon I can figure anything else out given time.

PS:  I tried to drop the samba file into /etc so I could compare the two and if that was the right course of action, change the smb file there, but it wouldn't let me because I didn't have root permission?  How do I get this, I don't recall being asked for a root password during setup?  If I do need to make system changes, I'm probably not going to be able to for this reason alone.

---

