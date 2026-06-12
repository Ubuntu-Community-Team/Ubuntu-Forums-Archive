---
title: "Grub Error 17"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by wtfitsRICK on 2008-04-06
So, this might be hard to help with because it only partially involves Ubuntu.

My laptop had Vista preinstalled.  I partitioned the drive, and I had Ubuntu/Vista dual-booting.  I am a big fan of the OS, but, seeing as I have a Compaq Presario C700, the dreadful Broadcom wireless card is an issue.  Since I never got the chance to use Ubuntu properly, I decided to just merge the Ubuntu partition with my Windows so that I could have more hard drive space.  Process: delete Ubuntu partition, expand Vista partition with ex-Ubuntu partition.  Now, when booting up, I get the GRUB Error 17.  I fear that I maybe should have gone into Ubuntu and erased it or something, but I sortof jumped into it.  Could have been a bad idea.

My major question to the community is this: does anybody know a way to salvage my hard drive without using restore disks?  I'd prefer to at least be able to get back onto Vista with all of my files and everything.  However, if I had to bring it back to the Ubuntu/Vista dual-boot, that would be perfectly fine.  Just so long as my files and programs are all intact.

Thanks.

---

### Post by riven0 on 2008-04-06
Wait a second! You merge the partitions by overwriting the Ubuntu partition with Vista? Well, in that case, Ubuntu is gone. You're going to have to re-install the Windows MBR and then if you want Ubuntu, you can reinstall it.

I'll try to find the link to fix the MBR for you.


EDIT: Okay, here's a site that may help: [Un-install page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by wtfitsRICK on 2008-04-06
Alright, I was pretty sure that Ubuntu was gone, but I wasn't sure.  If you can find the link, that would be awesome.  Couple questions: how will I get the fix on my laptop (won't turn on), and and will all of my stuff still be there?

Thanks supermuch.

---

### Post by wtfitsRICK on 2008-04-06
Okay, so I've looked through this un-install page in pretty good detail, and I'm not totally sure what option I need.  Since I can't actually boot any OS, I can't download any of these .exe files and whatnot.  My computer didn't come with recover disks, so that's a problem  as well.  Any further help would be greatly appreciated.  If you need more information on the situation, let me know, and I'll do my best to give you the details.

---

### Post by riven0 on 2008-04-06
In that case, do you still have the Ubuntu cd? Hopefully, it's the livecd. That way you can boot it up and burn the Super Grub Disk from there: [Super Grub Disk]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk"). Then pop in the burnt CD, reboot to the Super Grub Disk and it should list directions on how to re-install the MBR.

---

### Post by wtfitsRICK on 2008-04-07
Well, I'm on a different computer now, but it should work if I burn Super Grub Disk and pop that in my laptop?

---

### Post by riven0 on 2008-04-07
> **wtfitsRICK said:**
> Well, I'm on a different computer now, but it should work if I burn Super Grub Disk and pop that in my laptop?

It should work. From what I remember, after it boots up you should see an option to install the Windows MBR. Just follow the directions from there and you should be fine.

---

### Post by wtfitsRICK on 2008-04-08
Okay, thanks so much.  I burned the ISO for Super Grub Disk.  Popped it in the laptop before start-up.  Dialog came up, picked Vista, and now it boots up perfectly every time.  If ever my wireless card is fully (and easily supported) by Ubuntu, I will promptly re-partition and install the latest version.  Until then, I guess I'm Ubuntu-free. :(

But, my computer works! :D

---

### Post by bumanie on 2008-04-08
Hardy heron due for release on the 24th of this month is meant to have improved wireless support. Give that a go in  a couple of weeks.

---

### Post by wtfitsRICK on 2008-04-09
> **bumanie said:**
> Hardy heron due for release on the 24th of this month is meant to have improved wireless support. Give that a go in  a couple of weeks.

Sounds good to me.  Think, since it's been a MAJOR issue, the Broadcom crapshoot will be fixed?  I hope.  I love Ubuntu from what I've experienced, so I'd like to remain a user.

---

### Post by KuruOujou on 2008-06-18
Well, not necessarily. I'm still having problems setting up broadcom chips in Hardy Heron. Maybe it will be fixed in Intrepid Ibex? Please? I'm glad I have an atheros chip...but my parent's broadcom doesn't seem to like our network.

---

