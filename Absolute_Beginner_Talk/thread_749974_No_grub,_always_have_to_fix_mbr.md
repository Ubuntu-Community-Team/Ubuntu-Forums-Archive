---
title: "No grub, always have to fix mbr"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by joarc on 2008-04-09
Ok, I'm a reader and I have read SO MUCH about the problem I am about to ask about but none that really seems to satisfy.  :confused: Off and on for months I've been playing with Ubuntu (I have the actual 7.10 CD vs the downloaded one).  I've installed it three times to dual boot with my XP Home & Pro and every time it's a panic.  I lose XP altogether (well it's still there, just can't boot to it).  The first install gave me grub but didn't show XP as a choice. The second time there was no grub and Ubuntu loaded up straight through.  This third time I got the grub error (I've seen it here, error 31 or something).  Each time I fixed the MBR to get my windows back (whew).  I really want to learn this OS (and more) if I could just get the damn thing to install parallel my XP that I use everyday.  I recently built a new PC that I had intended for dual boot but I have so many programs and updates etc to reinstall my "environment" takes me two whole days. I've got Acronis Disk Suite, would it be easier to set up a linux partition through it before installing Ubuntu? Thanx folks and I'm looking forward to your expertise!

---

### Post by warbread on 2008-04-09
You shouldn't need any third party apps.  Do you have an Ubuntu install now?  If so, post the contents of /boot/grub/menu.list.

---

### Post by Tatty on 2008-04-09
That is unfortunate that you have had grub errors on three consecutive installs.  However, dont panic!  Most grub problems can be solved by editing /boot/grub/menu.lst.

The best way for you to get around this is to install ubuntu again, then post on here if an error appears.  Someone will almost certinaly be able to sort you out.

You might also want to have a read through this article, explaining how grub works and how to edit the menu.lst file.  [https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29]("https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29")

---

### Post by SlappyPappy on 2008-04-09
Dude, you're so close to being in Ubuntu heaven.

Definitely do what warbread says and post your /boot/grub/menu.list

Also check out that grub article that tatty suggests as well if you like to read stuff. Heck, I'm new and I learned a bunch by reading it. 

I had a problem with grub but a quick boot into the LiveCD, a few lines of code in a terminal window and I was back up and running in a matter of seconds. Hang in there, you're very close!  :)

---

### Post by joarc on 2008-04-09
Ok you guys are definately building my confidence back up.  I'll do an install tonight on my laptop and post again.  Thanx you guys!

---

### Post by joarc on 2008-04-10
Hmmm, well I tried the install but the only option it gives me is Guided (on my slave) or ALL of my main hard drive and I don't want either.  So I tried manual but didn't have a ext3 or swap set up, so I did that under the Admin menu and went to install again. However when I chose the partition I had made it said it wasn't formatted properly.  I thought maybe cause I'm using live cd it didn't actually create the partitions but I had a look back in windows and I see there's 6gb ext3 and a 1gb swap.  I'm getting tired so I'll give it another whirl tomorrow. Thanx again!

---

### Post by buried on 2008-04-10
On my grub, it's name "menu.lst"

---

### Post by joarc on 2008-04-10
OK, got it on my master. Whew. And I see grub AND it gives me the option to reach XP. I started at noon and it is now 5 :) With that said, ho hum:

-Cannot allocate resource region 7 (and it hangs right after that on start up for a few minutes)
-There was an error starting gnome settings daemon
-Broadcom bcm4311 not compatible
-While installing updates it hangs on *Starting common unix printing system: cupsd
-And now after a cold boot it's past the sign in but hung on the blank screen with my wireless light flashing once in a while

I have to ask myself what next? and where's my patience.  I really want to learn this BUT ARRHRGGGGG. I think I found the solution to the wireless issue and the gnome settings issue, if I could just get back in! Help again?

---

### Post by spiderbatdad on 2008-04-10
Try rebooting...enter the grub menu and press 'e' to edit the menu.
Now use the arrow key to move to the line that starts with 'kernel' press 'e' again
Delete the end of that line up to and including 'ro quiet splash' or whatever you have there...maybe just 'ro'.
Add this: lapic pci=routeirq
Press 'b' to boot.

Good luck.

---

### Post by joarc on 2008-04-10
Thanx spiderbatdad.  I did as you said, I found at the end of the line the "ro quiet splash" and deleted that only (it was the only thing at the very end of the line).  When it rebooted it was very quick to get to my sign in but it still hangs on the the brown screen.

---

### Post by joarc on 2008-04-10
Ok, well just to double check I rebooted.. still slow, still hung on the brown screen. :(

---

### Post by spiderbatdad on 2008-04-10
Hmmm. not sure. I'm wondering about the integrity of the installation.
How about trying another boot parameter all together...this time try

noapic nolapic vga=792

---

### Post by joarc on 2008-04-10
No go, no difference. I noticed when I went back into edit that the "ro quiet splash" had to be deleted again...normal? The install of Ubuntu went really well (considering all the problems I usually have).  It was when I tried to let it do updates and it was just about finished until it got to the "*Starting common unix printing system: cupsd" and then it just hung there and finally after an hour or more I cold booted and have had the loading problem since. Does this help for troubleshooting?  Thanx again.

---

### Post by spiderbatdad on 2008-04-10
> **joarc said:**
> No go, no difference. I noticed when I went back into edit that the "ro quiet splash" had to be deleted again...normal? The install of Ubuntu went really well (considering all the problems I usually have).  It was when I tried to let it do updates and it was just about finished until it got to the "*Starting common unix printing system: cupsd" and then it just hung there and finally after an hour or more I cold booted and have had the loading problem since. Does this help for troubleshooting?  Thanx again.

Yes that is normal, as the boot parameters are set in /boot/grub/menu.lst.  This approach allows a one time change, and if successful can be edited into /boot/grub/menu.lst later.
Not sure what to suggest at this point.  Hardy Heron may offer out of the box support for your hardware. 
You might try the 'lapic' option again and leave out 'pci=routeirq'

---

### Post by joarc on 2008-04-10
Nope. So now what? Reinstall? I don't even know how to uninstall.

---

