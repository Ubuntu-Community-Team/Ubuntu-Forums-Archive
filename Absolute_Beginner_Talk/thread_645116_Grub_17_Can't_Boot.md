---
title: "Grub 17 Can't Boot"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by liberum on 2007-12-19
laptop with 7.04, and 2.6.20-16 kernel

i just installed updates (which included new kernel/headers and all that stuff) on a laptop which was running FINE.

of course the kernel update required a reboot and viola:

after grub starts I get Error 17 cannot mount selected partition...

WTF?  how did the update do that?  I have not changed anything (including grub) that would have done this

Any suggestions?
Thanks

---

### Post by overdrank on 2007-12-19
> **liberum said:**
> laptop with 7.04, and 2.6.20-16 kernel

i just installed updates (which included new kernel/headers and all that stuff) on a laptop which was running FINE.

of course the kernel update required a reboot and viola:

after grub starts I get Error 17 cannot mount selected partition...

WTF?  how did the update do that?  I have not changed anything (including grub) that would have done this

Any suggestions?
Thanks

Hi and welcome, you can try and reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope this helps and good luck!

---

### Post by PurdueEngr on 2007-12-19
Liberum -

I had exactly the same problem you did, but I managed to fix it without reinstalling grub.
I started that process up to the point of finding the correct partition (mine returned hd(0,0).
From there I quit grub and edited my /boot/grub/menu.lst file.  I found all of the Ubuntu entries were configured for hd(0,1).  So a quick edit and a reboot = back in business.

I'd be curious to know why this happened though...

HTH

Best Regards, John

---

### Post by liberum on 2007-12-19
Thanks Purdue... engineer here too

i havent looked at menu.list yet but just sort of annoyed that this happened.

the kernel update shouldnt have fubar'd by grub

I have been using ubuntu for almost a year and have never had a problem like this before (well one that wasnt my own fault)

thanks again
ill see if it works

---

### Post by eolson on 2007-12-19
Must just be certain laptops.  Worked fine on my old  Walmart specail e machines (W4605).

---

### Post by liberum on 2007-12-19
Good to go!
menu.lst was pointing to hd0,2
when in reality my linux partition is the second part (i.e.hd0,1) and xp is the first part (i.e.hd0,0)
!! back in business

Good point, not sure if its a laptop thing BUT this only happened on my toshiba satellite laptop, not on my dell or hp desktops which are both running feisty.

It didnt happen on my server at work (6.06) or my vmware appliance (7.10)

BUT! i still have my wife and my kids laptops (old ones running 6.10) so who knows what will happen with those two.

---

### Post by stevieb on 2007-12-19
happened to me too on a lenovo 3000 c100 laptop, but edited menu.lst and all is well, except it blew away my puppy linux!

---

### Post by liberum on 2007-12-20
Yeah

I now realize that, despite being back up and running, my sound no longer works.

I had trouble with wlan/video/sound inititially with this laptop, so i will re make-install the drivers for sound and see what's up

---

### Post by Hasen_A on 2007-12-20
Hey you guys. I seem to be having the same problem whenever I let SPM update my system. This happens when being prompted for a restart after certain updates. Always after a distribution update. The (hd0,0) entries in the menu.lst are changed.

Is there any way to set up the program so that this won't happen again in the future? It really bugs me :(!

Thanks

---

### Post by psusi on 2007-12-20
Have you had to change menu.lst before?  When you change the root, you need to be sure you also change the #groot= line to match, because it is that value which is used to rebuild the menu entries when you update your kernel.

---

### Post by dstew on 2007-12-20
You can edit the **#groot** line in /boot/grub/menu.lst to point to the root directory you want to use. When a new kernel is installed, the script **update-grub** is run in order to put the new kernel line into menu.lst. At this time the default grub root will be determined by the #groot entry. So, ordinary updates don't change menu.lst, only kernel updates. So, change the #groot to the root you want, then issue the command update-grub and you should be good to go.

---

### Post by Hasen_A on 2007-12-20
I will will give that a try. groot=(hd0,1) if "grub> find /boot/grub/menu.lst" returns (hd0,1) right?

---

### Post by dstew on 2007-12-20
Yes, I think that is right.

---

### Post by liberum on 2007-12-20
I just had to do that myself.  Thanks to some good advice from rsambuca I modified that line in my menu.lst.

I still had the groot set at hd0,2 from the original linux install when I had vista on my laptop.  But after deleting the two vista partitions my linux partition changed to hd0,1.  Which I had changed in the OS entries so I could boot from grub.

But I wasnt aware of the groot item until now.  Should be good next time my kernel updates.

Thanks to the great people on these forums!

---

### Post by benrboone on 2007-12-24
This same thing happen to me, However I am not using a laptop.  In order to fix it, I Just push e to edit grub change the harddrive from one to zero.  This allowed it to boot correctly so then I edited /boot/grub/menu.1st to reflect the change I made above.  In the past I have updated the kernel and never had this problem.  I did notice that this last time the entry for the previous kernel was gone.  In the past the previous kernel has still been listed although I,m not sure if it was valid (never tried to boot)

---

