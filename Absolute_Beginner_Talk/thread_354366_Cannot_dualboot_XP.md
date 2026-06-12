---
title: "Cannot dualboot XP?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by dninex on 2007-02-05
Hi! I've just installed Ubuntu over the weekend, and I'm enjoying the experience...

Unfortunately, the rest of my family doesn't, due to me wiping out XP during the process of installing Ubuntu.

I was wondering if anybody could give me instructions on dual-booting XP and Ubuntu?

I don't care if I have to wipe out Ubuntu and reinstall, I don't have important data on it as of now... So, can anybody help me with this problem?

When I boot up my desktop, something called GRUB loads, and prevents me from entering XP. When I press Esc during the load, it still only allows me to load Ubuntu - just in safe settings or normally.

I went to the BIOS setup and had my CD boot as the primary drive - no difference, the GRUB loads. I forgot to mention, I have dapper, if it matters. The shipit variant.

So, please guide me through the dual-boot process... I'm not quite ready to fully commit myself to Ubuntu yet... If that reqires me only using XP, well... that will work too.

Thanks in advance. I look forward to enjoying Ubuntu.

---

### Post by shareMenaPeace on 2007-02-05
Hi, 
here is a guide

GrubHowto/ChangeDefaultOS
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

GrubHowto
[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29)

If you get stuck post a new topic with the problem.
You can use GRUB to let you choose to boot either xp or ubuntu.

---

### Post by Ryan450 on 2007-02-05
first off if you've already deleted windows and dont mind re-installing ubuntu again, then go ahead and re-install windows into its own partition, just be sure you make enough partition space for ubuntu.

Grub is the boot loader of choice for ubuntu, this is what gets you back into your linux os. The best solution I've seen thus far, especially since only one person enjoys linux is to install grub onto a floppy disk, and leave the default windows bootloader in place on the MBR.

its pretty simple to do this, go install your ubuntu system like normal under its own parition schemes. When it prompts you on where to install grub just cancel that section and continue with the rest of the setup. 

After ubuntu is installed to your hard drive you can install grub into a floppy disk via the livecd enviorment. With that setup you can just slip the floppy disk into your compy when you want to boot into your ubuntu linux, and the rest of the family can keep using windows as long as they dont put in the disk. 

Hope this helps.

---

### Post by dninex on 2007-02-05
Oh... I'm not that great in computing... I don't know how to partition anything... So, how to I partition to install XP? Let's start there. Thanks for the responses.

---

### Post by closetpirate on 2007-02-05
I know it sucks when people give you links as responses but the first time I dual booted ubuntu and XP i used this video guide. It is fun and explains just the stuff you want to know for now and gets you up and running in no time with you dual booted machine!

[http://video.google.com/videoplay?docid=-6104490811311898236&q=linux+xp+dual+boot&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=linux+xp+dual+boot&hl=en)

---

### Post by dninex on 2007-02-05
Sorry... but consider me an "absolute beginner" and please explain all of the computing vocabulary and how to do everything. Thanks.

---

### Post by dninex on 2007-02-05
Oh, excellent! A video, just what I needed, what better is there! It's a bit late in the night now, but thanks for giving me a link, I'll be sure to check it soon. Thanks a bunch!

---

### Post by shareMenaPeace on 2007-02-05
And here is the guide to the bootfloppy howto

[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29)

---

### Post by dninex on 2007-02-05
Well, I don't know what a bootfloppy is, and I just tried the first few steps of the video, but that assumes that you're installing the XP on a blank machine... I tried it, and GRUB loads. The CD doesn't load at all, even when I set it to load first. Is there a way to disable GRUB from loading at all? or more desireably, A way to completely delete Ubuntu from your system?

---

### Post by dninex on 2007-02-05
Obviously, I don't have XP installed in my system, it's gone, so any way to delete Ubuntu, when only ubuntu is installed on the system?

---

### Post by dninex on 2007-02-05
At this point, my top priority is to delete ubuntu from my system, so that I'm cleared to install XP, since GRUB gets in the way, so can anyone provide instructions on this subject? Thanks for all the support.

---

### Post by shareMenaPeace on 2007-02-05
Boot the computer and enter the BIOS.
Enable CDROM as first boot device (search the bios settings).

Than put in the xp cd and restart, this should load the xp installer.

---

### Post by dninex on 2007-02-05
That's what I did, but GRUB loads. MAybe I'll try a more direct approach... like entering system>administration>disks, entering my HD, and deleting everything from it... would this delete GRUB to produce the derised effect? I have a feeling that this may end catastrophically, but if otherwise, I'm willing to do this to delete Ubuntu, install XP, and then follow the dual boot guide with XP installed. So, anyone know if this might wipe out Ubuntu?

---

### Post by dninex on 2007-02-05
Uhh... well, if you hear from me in the next couple of hours... then it worked. If not... then you know what happened. Here I go...

---

### Post by dninex on 2007-02-05
Uhh... apparently, you can't delete files like that in Ubuntu... darn, looks like I'm stuck! No way to delete Ubuntu?

---

### Post by shareMenaPeace on 2007-02-05
You dont need to delete ubuntu xp will do this. But it depends on how your partition is setup.

To get rid of GRUB

[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

You need to put in the ubuntu LIVE CD - boot in recovery mode (maybe this can be done with the normal recovery mode aswell).

Than once you at the console log in and type.

```
fixmbr 
```
This removes grub.



Basicly i can recommend to use a partition for XP alone (you can choose this during xp install)
Best is partition to NTFS as it is faster than FAT32.

Or you can resize later the windows partition with the live cd installer (gparted).

Sorry for all this vocabulary but i guess you get the idea.

---

### Post by dninex on 2007-02-05
Thanks, but where exactly do I type in this "code"?

---

### Post by shareMenaPeace on 2007-02-05
When you boot the computer start ubuntu with recovery mode.

This will load a moment than you have a console infront (just pure text).

Enter it here.

---

### Post by closetpirate on 2007-02-16
My Suggestion is to put the XP cd in the drive and boot from it. You will need to install xp first to do a dual boot with xp and ubuntu. then follow the directions in the video it has been a while but I hope you are still interested

---

### Post by dninex on 2007-06-29
Thanks closetpirate, but I ended up buying a new PC with vista on it, and I'm using toe old system purely for Ubuntu. Turns out that my XP Pro CD was defective for some reason, so I had to run on XP home till last week. The computer I bought came preinstalled with Vista, so I've been toying around with it for a week, and then installed Ubuntu on my previous system yesterday, and at this point, I gave up dual-booting. I'll be looking for more support form everyone, Thanks.

---

