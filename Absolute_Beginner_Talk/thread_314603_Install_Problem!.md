---
title: "Install Problem!"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Terdog on 2006-12-07
OK, Installed Ubuntu fine, went great, but when system boots, goes straight to Windows XP, does not see my Ubuntu install. Even thought the partitions are there in XP.

Any Ideas? I have an old 20 GB Hard Drive I could install it on.

---

### Post by nickburns on 2006-12-07
Do you get the grub option on boot up? 

It will ask if you want to boot to windows or Ubuntu.

---

### Post by Terdog on 2006-12-07
Nope, didnt even get THAT, just boots straight to XP.

---

### Post by igknighted on 2006-12-07
Try hitting 'escape' from the time your bios POST ends until windows loads... sometimes you need to hit 'escape' to get to grub.  Alternatively, what hard drive/partition did you tell grub to install to?  Was it the MBR?

---

### Post by nickburns on 2006-12-07
Sounds like you didn't get grub installed on the Ubuntu install.  You may want to reinstall grub.

---

### Post by nickburns on 2006-12-07
To install GRUB to the MBR:

First boot the live CD

Go to a termimal ( Application >> Accessories >> Terminal )
In a terminal type:

sudo grub

You will get a grub prompt

grub>

At the GRUB prompt type:


root (hd0,1) setup (hd0) quit

Re-boot and you should be good to go....

---

### Post by phiellaep on 2006-12-08
I have exactly the same problem as Terdog.

I've tried the advice in your preceeding post nickburns, but to no avail.

I wonder why setting up Grub on hd0 is not setting it up where my MBR is? Surely my MBR is at hd0? Maybe it's not?

I'm not too linux savvy as you may have gathered. Willing to learn though.

---

### Post by phiellaep on 2006-12-08
OK I am in a lot of bother now. I would really appreciate any help from people!

As I said before, my system was just booting straight to windows.

Now I can't get Windows at all, OR linux!

I setup GRUB on hd0 AND hd1 "just in case". Evidently this was a very stupid thing to do.

Now when I boot, I get the GRUB Screen, which shows a few linux options and one windows option. When I try to load ANY of these, I get an error, for example "device not found".

The only way I am able to talk here or use my system at all is by using the Ubuntu 6.10 live cd.

PLEASE HELP.

I will take any suggsetions, even those that just wipe GRUB and linux and allow me to access windows again. I have important reports etc that I need to work on for uni!!

Philip

---

### Post by BarfBag on 2006-12-08
> **phiellaep said:**
> OK I am in a lot of bother now. I would really appreciate any help from people!

As I said before, my system was just booting straight to windows.

Now I can't get Windows at all, OR linux!

I setup GRUB on hd0 AND hd1 "just in case". Evidently this was a very stupid thing to do.

Now when I boot, I get the GRUB Screen, which shows a few linux options and one windows option. When I try to load ANY of these, I get an error, for example "device not found".

The only way I am able to talk here or use my system at all is by using the Ubuntu 6.10 live cd.

PLEASE HELP.

I will take any suggsetions, even those that just wipe GRUB and linux and allow me to access windows again. I have important reports etc that I need to work on for uni!!

Philip

I have a quick solution for you.  It's very important that you mount your Windows partition (through the live CD, of course) and back-up your data.  Messing with your partitions can be risky business.  Install GParted on your live CD (sudo apt-get install gparted) and use it to clear your Linux partitions.  Be ABSOLUTELY SURE to not clear your NTFS (or FAT32 depending on which version of Windows you use) partition!  Then, boot off of your Windows CD and do a repair install.  This should clear your MBR and preserve your data.

I don't want to get you into deeper doo-doo, so I encourage you to verify everything I just said.

---

### Post by phiellaep on 2006-12-09
Hi barfbag,

I managed to get it fixed before reading your post. I wish I had read your post first though, as my solution involved me formatting my windows/linux hdd, merging all partitions, installing windows, then formatting my backup hdd by shifting its contents over to the main hdd and formating then shifting back.

all clean now.

perhaps when i have more confidence again in the future i might try linux again :P i seem to have bad luck when it comes to MBRs though.

thanks for your help guys. i'll be around i'm sure.

---

### Post by Icepaws on 2006-12-09
i have a dell dimension 4100 with 2 hard disks a 6 gb and a 160gbit bios rev is a11. i want the root and the boot files all to be on the 6gb and everything else to be on the 160gb. But grub keeps comeing up with error 18 or(if i change the bios for the 160gb disk to boot first) invalid disk in a: insert disk in a:



also is it possible to boot from a slave drive?

---

