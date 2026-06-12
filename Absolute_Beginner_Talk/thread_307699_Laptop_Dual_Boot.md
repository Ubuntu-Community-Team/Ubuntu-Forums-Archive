---
title: "Laptop Dual Boot"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2006-11-27
Hi, Linux newbie here,

I got a Compaq Presario 700 laptop with WinXP from my uncle as a hand-me-down. Inevitably, Windoze crashed, and now it won't even boot.  ](*,) 

I know it still works, because I ran the Ubuntu LiveCD on it just fine. I still want to retain XP, but I want to load Ubuntu on it to make it functional again. I was told that to dual-boot one on one harddrive, I would need to defragment it before I partition it. The problem is, I can't defrag the hardrive because XP won't boot and I don't have the recovery disk.

So, is there some way to defrag and partition it without using WinXP? 

I'm willing to learn and I'm not afraid of a command prompt.

Thank you!

---

### Post by foxmulder881 on 2006-11-27
Just because the Live CD works it doesn't mean the XP partition is still working. Live CD means it runs straight from the CD with no interaction with the HD whatsoever. You are more than likely going to require a Windows install disc for a repair/reinstall. Sorry for the bad news!

---

### Post by Rod Steel on 2006-11-27
You should get a hold of a bootable Utility CD and boot the laptop with that, then reformat the hard drive as Fat 32 reinstall XP, then install Ubuntu using the install disk. One other thing, hopefully you still have the XP serial # somewhere, cause you're gonna need it.

---

### Post by Paul133 on 2006-11-27
Well, I think you'll have some trouble dual-booting if one of your OS's (Windows) won't boot! As for partitioning, that can be done during the installation. As for defragging, I wouldn't worry about it. If you want to keep Windows on and you think it may boot, then insert the Ubuntu LiveCD, click Install and go through the installation. If you don't know how to install Ubuntu, you can search the forums, but all you really need to know is here, at one of the best Ubuntu websites (Just click on "Install Desktop CD Ubuntu") 
 
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) (this is the same site in my sig under "Great Ubuntu Help Site")

And, it might not be worth it to keep Windows, particurarly if you have to reinstall Windows. As others have said, the fact the LiveCD works means your computer hardware is working, not Windows. From what you've said, Windows seems dead. And, it's great you want to learn the command line! Not too many people like bothering with the command line these days. It's fast and fun, and though it's not necesary, it's a nice skill that can come in handy while using Ubuntu. Check out my "Guide to the Terminal and Shell Scripting" in my sig for common commands and such.

---

### Post by jakenn-linux on 2006-11-27
I think your problem is getting XP back up and running.](*,)   You can use gpart (it's on the liveCD install) to set up the partitions, and set up everything you need for the Ubuntu install.  I was told that it was best to load Windows first and then add Linux.  Linux (Ubuntu) will add a boot loader (grub) so that you would be able to choose between Ubuntu and WindowsXP.  But since XP won't boot up, you can probably install Linux but selecting XP from the boot menu won't work.  So my advice (I'm somewhere a bit above newbie) is to get someone to help get XP back and then it'll be a breeze adding Ubuntu. I'm dual booting a laptop and desktop.

John

P.S.  You might check with someone you know that has XP and see if they made a boot disk that could let you defrag from the A: prompt.  Get XP running if you must and then you'll be fine.

---

### Post by foxmulder881 on 2006-11-27
> **jakenn-linux said:**
> its was best to load Windows first and then add Linux.  Linux (Ubuntu) will add a boot loader (grub) so that you would be able to choose between Ubuntu and WindowsXP.

That's great advice and exactly the way it should be done. It's a breeze, thanks to Ubuntu.

---

### Post by foxmulder881 on 2006-11-27
> **Rod Steel said:**
> reformat the hard drive as Fat 32 reinstall XP

Why would you recommend FAT32 over NTFS. I recommend NTFS. FAT32 is old and crusty and why people still insist on using it is beyond me!

---

### Post by The Iron Curtain on 2006-11-27
[QUOTE=foxmulder881]Just because the Live CD works it doesn't mean the XP partition is still working. Live CD means it runs straight from the CD with no interaction with the HD whatsoever. You are more than likely going to require a Windows install disc for a repair/reinstall. Sorry for the bad news![/QUOTE]

Oi! Is there anyway to check if the Harddrive works? 

Well, I don't know how soon I can fix XP. I was hoping to set up the bootloader and Ubuntu so I could use the laptop and fix XP later. Since XP is already installed, there shouldn't be a problem...right?:confused: 

Thank you all for your quick reponses!

---

### Post by foxmulder881 on 2006-11-27
You could try. But when you do eventually get around to fixing XP it will more than likely overwrite GRUB with Windows' own MBR. (Master Boot Record)

---

### Post by The Iron Curtain on 2006-11-27
> **foxmulder881 said:**
> You could try. But when you do eventually get around to fixing XP it will more than likely overwrite GRUB with Windows' own MBR. (Master Boot Record)

I see...Then I would have to reinstall just GRUB or Ubuntu and GRUB?

---

### Post by ngch on 2006-11-27
For your case, i recommend u try to repair (or better yet, just reformat and reinstall) your windows xp installation before installing ubuntu.

This is because if you choose to reinstall windows xp after installing ubuntu, winxp will rewrite the master boot record on the hard drive, and you can't boot ubuntu anymore. After that, you will have to 1. reinstall ubuntu or 2. reinstall the boot loader.

Usually, I'll just back up my data and start all over again. :p

---

### Post by Drifter on 2006-11-27
The reason you use Fat 32 is so ubuntu can see the windows drive, if you don't want to be able to read the windows drive out of ubuntu then use NTFS

---

### Post by foxmulder881 on 2006-11-27
Even by using FAT32, Ubuntu can still be a little fussy with reading a Windows partition. I would still recommend keeping them completely seperate and you will have no dramas.

---

### Post by gn2 on 2006-11-27
The good news is if you have a valid Windows XP product key (usually found on a green sticker) you can borrow a Windows XP install CD from a friend and re-install using your own product key.

So long as they are both the same version, eg Home, Pro or Media Centre.

---

### Post by The Iron Curtain on 2006-11-27
> **gn2 said:**
> The good news is if you have a valid Windows XP product key (usually found on a green sticker) you can borrow a Windows XP install CD from a friend and re-install using your own product key.

So long as they are both the same version, eg Home, Pro or Media Centre.

See, that's the problem....I got the laptop as a hand-me-down, so it didn't come with a product key or disk. I can borrow a WinXP disk, but I don't have the key. :(

I don't have any files on the machine as I just got it, so that's a relief :) .

It seems like for this, I might as well reformat the HDD and stick straight Ubuntu. I was really keeping WinXP because it can run games, but I checked out Cedega and it looks like I can play some of the games I have.

---

### Post by foxmulder881 on 2006-11-27
If you have access to XP disc, simply use the view install key program to view the current installed cd key. It's a tiny little .exe file you just run and it'll give you the installed cd key. Google for it.

---

### Post by gn2 on 2006-11-27
You might be able to get it running using Recovery mode on the XP Cd. If you can get XP running on the laptop, this should find you the product key: [http://www.magicaljellybean.com/keyfinder.shtml](http://www.magicaljellybean.com/keyfinder.shtml)

A good XP help site is [www.theeldergeek.com](www.theeldergeek.com)

---

### Post by lankieboy on 2006-11-27
I did a dual boot - XP and ubuntu on my Acer travel mate 2440. I love it so far. Sound is little bit of buggy and sometimes it does not detect my usb tv card. Once I reboot it after connecting it works fine. Maybe something it wrong with my tv card. Power management is great as well. So this is free right? What is the catch? Anyways, keep it up. Hope it doesn't have spyware like most of the free programs does. 8)

---

### Post by The Iron Curtain on 2006-11-27
well, I'm on my laptop using Knoppix. I was able to read the windows part of the harddrive (/media/hda1), but I can't write to it. So, I guess teh HDD works. 

I couldn't get the XP CD to fix XP, so I might as well reformat. Does the Ubuntu liveCD do that?

---

### Post by foxmulder881 on 2006-11-28
When you install Ubuntu, it will give you this option.

---

### Post by The Iron Curtain on 2006-11-28
Well, I took the plunge and now my laptop runs Ubuntu only.

Thanks all for your help and support! I'll likely be on these forums for sometime getting the hang of things. :D

---

### Post by foxmulder881 on 2006-11-29
Glad I could help.

---

