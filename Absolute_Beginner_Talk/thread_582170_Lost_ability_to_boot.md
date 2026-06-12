---
title: "Lost ability to boot"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2007-10-19
I'm pretty sure I've made a newbie mistake here, but I seem to have lost the ability to boot my other computer. She has Ubuntu (Edgy) on one hard disk, and Windows XP on the other. I recently bought a new hard drive, and to test whether or not it worked I temporarily disconnected one of the hard drives (as it turns out, the one with Ubuntu) and promptly received GRUB error 21. I knew this meant I had disconnected the Ubuntu hard drive, so then I turned the computer off, reconnected it and disconnected the Windows hard drive and used those cables to connect the new hard drive (SATA/power) but the computer would not boot. Then I figured "ah, dang" and just booted from CD. All this was just to test whether or not my hard drive worked, as it didn't come with a SATA cable, before the warranty expired.

In any event I now have the new hard drive disconnected and have all the connections as they were originally, and find myself unable to boot. Not even grub error 21, it just stops in between the BIOS screen (telling me about my master/slave drives, etc.) and when it would go to the GRUB boot menu. I know both hard drives are connected correctly, and I figure this has something to do with some mistake I must have made in all the goings on of the previous paragraph. Does any one know why this is going on?

---

### Post by spur on 2007-10-19
Is one of the drives a sata drive? I found that with a sata drive I have to boot from the cd as I can only sometimes boot properly otherwise. My mbr is on the ide drive so it doesn't really make sense.
With it not even getting to error21 I would leave the system off for a while to let things settle and ensure no residuals from your previous attempts. Then boot to the cd to see if it will boot at all.
If it doesn't double check your cables and even try out a replacement cable. Also check your drives haven't lost the jumper lead on the 'master slave select' area.
You may need to reset your bios settings as well.

---

### Post by nonpareilpearl on 2007-10-19
All (3) hard drives are SATA drives, and I was able to boot fine until I messed around trying to test if my new drive was functional. I tried booting from CD to make sure that both hard drives were detected (as the new one is disconnected until I obtain another SATA cable - I found out what I needed to know). I went into GParted and sure enough both drives were listed in their full glory - partitions, how much space is being taken up on each, and etc.

I did, however, notice that the BIOS listed both hard drives as "Master". I'm pretty sure I have (...had) the Windows hard drive set to "Slave". Could the fact that I tried to boot once with the Ubuntu hard drive disconnected forced it to switch from Slave to Master? Or would having two master drives cause this problem?

Also, I did go through the BIOS settings and aside from the master/slave problem, everything else is the way it was before (and since I'm not very creative, that means 'default').

I have that computer off for now, thanks for your advice. Any further thoughts appreciated :)

---

### Post by Arthur Archnix on 2007-10-19
Where was grub installed to? Which drive is master?

If I had to guess, I'd say you had one drive (master) with windows on it. You added second drive (slave) with ubuntu on it. You probably installed Grub to MBR of Master, but all the files it needs are on the secondary drive (slave). 

If that were the case, you'd need to make sure that you'd set your master / slave properly as before. If they're plugged in like you think they should be, and it won't boot. Try swapping them. Make the slave the master and vice versa. 

Restting the bios is also a good place to start.

---

### Post by spur on 2007-10-19
Are you sure you connected them up exactly the same? try them the other way round. In each others connector. That's just an idea but if your system is used to one being a slave and the other is hooked into its slot the system may have become confused. It seems, to me, a problem of the system recognising properly your hard drives.

---

### Post by nonpareilpearl on 2007-10-19
I'll try switching things around, but I only disconnected one hard drive at a time (thus I know that when I plugged it back in I was using the same setup). I'll also try resetting the BIOS and the Master/Slave switch...

...this may take a bit.

---

### Post by spur on 2007-10-19
You might as well try booting up with only one drive attached. If that works then attach the second. If that doesn't work, try the second first, boot then attach the first second.
Also are these native sata connections or are you using a converter?
Also sata drives are all treated as 'master' drives so your drive setting should all be master.

---

### Post by nonpareilpearl on 2007-10-19
One of the first things I did was to try booting each individually, but that hasn't worked yet.

Do you think reinstalling Linux (and thus restoring whatever defaults GRUB has) would help?

---

### Post by spur on 2007-10-19
I believe you can repair grub or at least reinstall it. I have a super grub disc I can do that with. I'll get back to you with the link.
Ok here it is [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) . You will need to burb it to a disc then insert it before you boot.

---

### Post by nonpareilpearl on 2007-10-19
For the record: When I boot with (only) the Windows hard drive I apparently still receive GRUB error 21, but when I boot with (only) the Ubuntu hard drive it stays stuck at the "you have a hard drive, DVD burner, etc." BIOS screen.

Thoughts?

Thank you all so much, by the way.

---

### Post by nonpareilpearl on 2007-10-19
Thanks for the link! Unfortunately my desktop has the CD/DVD burner. I will go to my univ. campus tomorrow morning and burn the disk there and see if that works.

Thanks again!

---

### Post by Arthur Archnix on 2007-10-19
Thoughts? Yes, I think grub is installed to the windows hard-drive, but the boot files are on the ubuntu hard-drive. With that setup you won't be able to boot. The grub live rescue cd should mend things.

---

### Post by nonpareilpearl on 2007-10-21
So far I haven't been able to accomplish anything with Super GRUB. After successfully (so it tells me) fixing the GNU/Linux boot,  I try to convince it to boot. It then pulls up the boot menu that I normally see (Ubuntu+Windows) and for all the Ubuntu options (varying kernels, etc.) I receive "Error 13: Cannot mount partition", for Windows I receive something like "Error unreadable executable".

:(

I'm about to try downloading DSL and trying to boot from a key, backing up all my files on my (now functional) hard drive, then just reinstalling whatever OS needs to be reinstalled. I am a bit confused how unplugging a hard drive could lead to such a mess?

---

### Post by nonpareilpearl on 2007-10-21
...Now I'm going to try and just install Ubuntu on an empty partition on one of my hardrives (well... empty enough) and use it to back up everything else before reinstalling the other OSes.

---

### Post by spur on 2007-10-21
Exactly, it should not have.
I would at this point back up as you say you will do then reinstall. It's a bit tricky as given your problems if you just reinstall your ubuntu it may not see your windows. I think I would go for a more sure complete reinstall. Remember that windows does not see linux so install it first. If you have an ide drive I would make a boot partition on that and use it (the drive not the boot partition) for the / partition for linux and the main windows partition and put your /home and your documents etc from windows on separate partitions on other drives. This is because grub has problems sometimes with sata drives.(it happened to me)
This set up makes it easy for grub to see all your oses and find what it needs to boot. Saves a lot if fiddling with the bios too.
Oh I forgot to say that gutsy includes read/write to ntfs so no need to create a fat partition to share files between the oses.

---

### Post by nonpareilpearl on 2007-10-21
Thanks for all the help!

Unfortunately I already have the 750 as FAT32 because I was worried about cross-compatibility between Mac, Linux, and Windows. Mac OSX I think starting supporting ntfs one or two "cats" ago, but I'm not completely sure. Also since my main computer (that's having all the boot problems) is the one with the CD burner, I can't really get Gutsy right now (no pun intended).

...it appears as though, even with the reinstall of Linux, that she still doesn't want to boot. This is insane. I can't imagine why this should be >.<  All the hard drives are on, everybody has power... no unhappy sounds... oye.

---

### Post by nonpareilpearl on 2007-10-21
Is there any way to use the LiveCD to back up data? I don't mind reformatting the whole dang drive so long as I can back up everything on it.

---

### Post by nonpareilpearl on 2007-10-21
I GOT IT TO BOOT OH MY RA THE RELIEF.

...my roommate must think I'm crazy.

---

### Post by spur on 2007-10-21
You should be able to do your back up with the live cd as it should be able to read your other drives.

---

