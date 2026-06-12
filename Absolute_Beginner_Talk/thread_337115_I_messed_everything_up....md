---
title: "I messed everything up..."
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by cookieofdoom on 2007-01-12
Well, firstly I want to say that these forums are extremely useful even if you don't register on them. The Ubuntu distro is the best distro I've ever used (I've only used Mandrake 10, though...). I come to Linux with a fairly strong background in Windows and hardware, though my Linux lingo leaves a bit to be desired. I'm a power user (I've overclocked my CPU, and video card... and modded my soundcard...) and that can often be my undoing. Anyway, I should probably explain exactly what happened so you have the whole story. This is going to be long, but it's the best way I can think to explain it...

I have two hard-drives in my computer. Up until about two weeks ago I had only one partition on each of them. I had two working booting Windows XP hard drives, one was 80GB and the other 20. Now, I'm a gamer (otherwise I wouldn't be overclocking as much) and so I had the 20GB setup as a dedicated "America's Army" hard drive. That is to say that it had drivers, Firefox, and America's Army on it. I had disabled many system services and processes stopped so that I could use this drive during matches and have as little system lag as possible (this is an amazing alternative to getting a faster computer if you lag a lot.. but that's not what I'm here for). After setting up this drive I installed (with this 20GB drive set up as the boot drive in my BIOS) another version of XP where I put things like Office, Google Desktop, and other crap that would slow down my computer but was useful to me.

That setup worked like a dream until I got rather upset with Windows and decided that I wanted to install Linux (I do not regret this choice) as another partition on the 20GB drive. I shut down my computer, switched my BIOS boot drive to the 80GB (since I never directly booted to that drive before, it was no big deal) and started up the Live CD. I repartitioned the 20GB drive so that the Windows was 14GB and the Linux was 5GB (these figures aren't exact but I don't figure it matters). I then installed Linux and was quite impressed with the Ubuntu distro (so much easier than Mandrake!)

Keep in mind that I had simply resized the Windows XP hard drive on the 20GB drive. This made Windows on that drive not work (which wasn't to big a deal cuz I had no important files there, and could reinstall Windows pretty easily) but I could still boot to my 80GB partition from the 20GB hard drive. Let me clarify how things worked at this point to avoid confusion...

If I wanted to boot to my 80GB drive I would select the 20GB from the BIOS, Windows would come up and ask me which of the two Windows partitions I wanted to use. I'd select the top one and it would boot to XP on my 80 GB drive.
If I wanted to boot to XP on the 20GB drive (which I had made a 14GB partition in the Linux Live CD) I couldn't. I would boot to the 20GB drive (select it from the BIOS), select the bottom option and Windows would come up giving me some error message. I never bothered debugging this because it was not important to me at the time.
If I wanted to boot to Ubuntu I would select the 80GB drive from the BIOS. The Linux loader would come up giving me the usual options (Linux, Linux recovery, memtest) as well Windows XP... this brought up the Windows bootloader that would have appeared if I had selected the 20GB drive from startup.

You still with me? Okay, there's more...  I haven't actually gotten to my problem yet, sorry this is so long.

I was so happy with Ubuntu that I decided I needed more than 5GB of space dedicated to Linux. Now, I tried making the NTFS write stuff working (cuz that woulda been about all I needed) but I couldn't get it working. So I decided to **format my 14GB partition of Windows.** I then resized it to a smaller 10GB, granting me 9GB (give or take) on my Linux drive. I actually went 2 or 3 days without using Windows. I was so proud of myself.

Well, the time finally came. I had an application that I had to run that required Windows. I shut down my computer, started up, told the BIOS to boot to the 80GB. I was greeted with an error message to the effect of... "Insert valid boot medium and restart your computer". OH NO!!! What did I do!?

Well, I know what I had done (in case you're not quite clear on it) was taken away the only means I had of booting to the 80GB drive. The 80GB drive was trying to point to the Windows boot loader on the 20GB drive which didn't actually exist. I figured I could fix it.

I figured that if I installed Windows onto the empty partition on the 20GB drive it would detect the 80GB and give me the Windows boot menu at start up... It didn't. I installed XP like I said, and when I booted the computer went straight to the 10GB XP partition that I had just made. Not only that, but XP had decided to eat Linux. When I selected the 20GB drive from the BIOS I got an error message telling me that some file (a seemingly random grouping of letters from the alphabet that meant nothing to me) was missing. It told me to press control alt-delete to restart the computer. I did that twice, and would you believe it failed to find the file every time?](*,)

That made me rather unhappy because I had spent 2-3 days customizing Linux and gotten things like Compiz and Firefox extensions... okay, so not that might not be all that cool... but it took forever cuz I'm a noob. Anyway, I reinstalled Linux. I can now:

Boot to Linux (YAY!)
Boot to my 10GB XP partition (YAY AGAIN!)

But I cannot

Boot to my 80GB XP partition (BOO!!! HISSSS!!!!)

Now, I have a couple possible solutions that I could use you guys' help with. I don't know how to do one and I don't know what will happen if I try the other...

Option A: Try to get Linux to have an option to boot to the 80GB partition. I don't know how to do this, and I don't know if it will work.

Option B: (Granted this is a Linux forum, but I figures someone might be nice enough and know enough to tell me) Install Windows overtop of Windows on my 80GB drive. I'm concerned that this will delete most of my Windows data, though...

Thanks for taking the time to read my unbelievably long post. And thanks for any help you can offer.](*,) ](*,) ](*,)

---

### Post by Hendrixski on 2007-01-12
That is a long post.


So your problem is you installed Linux, and now can't boot into Windows?  Have you played with GRUB?  that's the Linux boot loader, it can manage booting between all of your partitions. If you changed something in there change it back and I'm sure everything will work, if not, make sure it lists your partitions properly.

I haven't had a problem with booting before, and I've done triple boots.  It just works so I never looked at it.

Good luck

---

### Post by Hendrixski on 2007-01-12
Oh yeah, avoid option B.  You don't wan to lose data.  Option A sounds like you want to read some documentation about GRUB.


again, hope that helps :)

---

### Post by cookieofdoom on 2007-01-12
Wow, that's fast! Thanks! Where do I find the documentation for GRUB?

<me> is a noob </me>

---

### Post by riven0 on 2007-01-12
In short, you're dual-booting two hard drive's, right? One hd is dedicated to XP, the other hd is dedicated to both XP and Linux. Well, Linux should be able to take care of all that. 

From [this thread]("http://www.ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot+two+hard+drives") it says to open grub (sudo gedit /boot/grub/menu.lst)

and add in this to the bottom:
> 
title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Make sure about your the on your XP hd number, or you'll get an error message.

---

### Post by cookieofdoom on 2007-01-12
Okay, the hard drive is showing up on my computer (mounted) as hda1.. how do I track that back to a hard-drive number like you had there?

EDIT: I have this in that file already:
> title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by riven0 on 2007-01-12
> **cookieofdoom said:**
> Okay, the hard drive is showing up on my computer (mounted) as hda1.. how do I track that back to a hard-drive number like you had there?

If I'm not mistaken, hda1 will read as hd1, so the entry should work fine. At least it worked for me half a year ago when I was till dual booting XP. 

The only thing is, you'll have to boot up to the 20GB hd with Linux on it, which will redirect you to GRUB, choose your 80GB hd and Linux will redirect you to it.

Try it out, anyway, just make sure to add the entry to the bottom of your Grub list.

---

### Post by DX 00 on 2007-01-12
Here is a link to a very good little tutorial about GRUB. It helped me a lot with a winxp/ubuntu/fedora core/suse installation. Hope it helps you too.

[http://en.opensuse.org/SDB:The_Boot_Manager_Grub](http://en.opensuse.org/SDB:The_Boot_Manager_Grub)

---

### Post by cookieofdoom on 2007-01-12
> **riven0 said:**
> If I'm not mistaken, hda1 will read as hd1, so the entry should work fine. At least it worked for me half a year ago when I was till dual booting XP. 

The only thing is, you'll have to boot up to the 20GB hd with Linux on it, which will redirect you to GRUB, choose your 80GB hd and Linux will redirect you to it.

Try it out, anyway, just make sure to add the entry to the bottom of your Grub list.

Alright... so... You suggested that I boot to Linux on the 20GB hd... I selected it from the BIOS and it took me (I forgot it would do this, but it did..) straight to the one copy of Windows (I set it up yesterday) that does work from the bootloader. So I booted to the 80GB, GRUB came up and I saw the new option I had input (that you gave me.. THANKS!) and it booted me to the same copy of Windows that I set up yesterday (and had just booted to)...

I went through the next boot and messed around with a a custom boot mode... I tried a few things and got no partition thing... When I tried...

> title Windows NT/2000/XP (loader)
map (hd0,0) (hd0,0)
map (hd0,0) (hd0,0)
rootnoverify (hd0,0)
makeactive
chainloader +1 (I THINK, not sure)

I got an error telling me that the thing in my first post could not be found. Honestly, I couldn't write it down so I said it to myself like 100 times and I can't remember it now for the life of me... it started with NT though... it told me that it couldn't find (or load... stupid me, can't remember anything) the NT (I think it had an l in it too..)  and to press ctrl+alt+delete to restart my computer. I think I deleted the Windows bootloader on that hard drive somehow... Thanks for the help again, BTW...

> **DX 00 said:**
> Here is a link to a very good little tutorial about GRUB. It helped me a lot with a winxp/ubuntu/fedora core/suse installation. Hope it helps you too.

[http://en.opensuse.org/SDB:The_Boot_Manager_Grub](http://en.opensuse.org/SDB:The_Boot_Manager_Grub)

Thanks for the link, I'm bookmarking it...

For right now I'm going to try some more seemingly random boot options...

Thanks for everything, guys.

MAJOR EDIT: I may have the problem solved... just gotta try some stuff...

---

### Post by cookieofdoom on 2007-01-12
Sorry for the double post... I wanted to make sure I didn't leave all you guys hanging... I got Windows working! I never thought I'd be so happy to say that. I followed the advice in [http://www.ubuntuforums.org/showthread.php?t=318961](http://www.ubuntuforums.org/showthread.php?t=318961) and got it working! Thank you guys for all the help, I wouldn't have been able to do it without you guys.

---

