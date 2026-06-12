---
title: "I feel like such a n00b (gParted)"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by randomco on 2007-05-09
Yeah, so I was running the Ubuntu 7.04 live CD on my Windows XP laptop, and used gparted to resize the partition containing all my documents and desktop files. It failed. And all the documents are turned into nice little 1024kb files :(

Anything I can do to restore anything?
I don't care about the desktop as it was about 6gigs of downloaded files, just installers etc.
But My Documents! all my documents! 

It wasnt a good thing to have just after a hard drive failure and corruption in my old PC.

Thanks in advance, but I'm not too hopeful :( and please don't throw too many LOLs my way, thats what friends are for...
Mike

---

### Post by miggols99 on 2007-05-09
Did you defragment your windows partition? You should always do that before you resize a windows partition. I don't know if you can do anything, but next time, backup backup backup!

---

### Post by ghostboy on 2007-05-09
Ok, I had that problem happen but I was using openSUSE.  Here is what I did to get my documents back.  I downloaded a LiveCD of Knoppix 5.1.  

~Throw that LiveCD into your CDROM.  
~When you boots screen comes up, hit F2, or F12, or whatever you need to, to get into the BIOS settings. 
 ~Find your boot options.
~Change your boot options to reflect that your CDROM boots first.
~Save those settings.
~Reboot.

This reboot, if done correctly will force your system to boot from the HD.  Since your going to be using a LiveCD it wont affect your system.  Knoppix does take some time to load, so just be patient.  When Knoppix has loaded you will have the ability to access those files you need.  I want to say that it will recognize your HD as /media/hd1.  Find your "My Documents" folder, and move them onto a removable media, like a jump drive.  Then shut down, and perform a "Repair" or "Fresh" installation of your OS.  

I hope this helps.

---

### Post by randomco on 2007-05-09
Why I didn't backup (not an excuse tho):
 I have an acer laptop and there are two supplied backup tools. One needs to make a full copy of the HD back onto the same HD before saving onto CD or DVD, kinda a bugga if you have more than 50 of 100 gigs full :P. The other tool - NTI Backup Now! 4 is so buggy that clicking the file menu crashes the program.

All in all its only school work - not important. and websites :( - the hours i have spent on web design is insane so im more than slightly annoyed at losing those. Other stuff is just general word docs and Flash/GIMP projects.

Thanks for replying anyways
Mike

EDIT: Just read that last post, I was wondering that, because although I could see Desktop had gone from ubuntu, I could still see all my Docs files. Ill try it but its kinda 50 odd gigs :(
Ill get back to you in an hour or so. 

Thanks again

---

### Post by ghostboy on 2007-05-09
What kind of Acer do you have?  I experienced this issue on my Acer Aspire 5050.  50 gigs is a lot of stuff.  I hope you have a friend with an external HD.:biggrin:

---

### Post by randomco on 2007-05-09
It's an Acer Aspire 5102WLMi, so its similar to yours. Booting back into linux didnt work, and short of the 40 dollars for diskinternals ntfs recovery, im now running ZAR 8.1 - anyone heard of it. Hopefully i can at least get some data back. The diskinternals was recovering some mildly corrupted image files but you need to pay to save the files :(. I may end up paying for it. ZAR is at 33% of I-don't-quite-know-what, but it seems to have found some file fragments etc.

BTW - anyone need a website? - I need cash :P - Just kidding, but not really :S.

Thanks again,

Mike

---

### Post by hyper_ch on 2007-05-09
do you have another network pc with 50gb free of diskspace?

---

### Post by randomco on 2007-05-09
There may be some misunderstanding here, gParted was trying to move everything around to resize the partition and turned it all into 1024kb "files". Unless there would be another method of recovery requiring a 50gig HD other than copying files over network?

Nothing (almost) has been deleted because windows still shows up as the drive having just 2gig free space (after the resize). So im just hoping ZAR can make something of the garbled files.

Mike

---

### Post by hyper_ch on 2007-05-09
I would suggest first to make an image of that partition as it is now before messing around with it... that's why I asked

---

### Post by randomco on 2007-05-09
hmm good idea - is that what Norton ghost is for because I might just have a copy lying around.

TBH at the end of the day if I lost all the files it wouldnt matter too much ecept for one web project I was working on, the basics of which are online anyway. 

Thanks
Mike

UPDATE: ZAR has correctly identified the partition as FAT32 after 40 mins of scanning (XP could have and did tell me that already but there you go) seems to be fixing some stuff so ill get back to you all again soon)

---

### Post by hyper_ch on 2007-05-09
yes, ghost can make an image... that will be a 1:1 copy of the partition... I just think it's better to have a backup of its current state than no backup at all...

well, then it seems good that ZAR seems to help :)

If you need some advice on making backups later, let me know.

---

### Post by ghostboy on 2007-05-09
I love ZAR.  I actually use it to recover deleted images off of SD cards in cameras.  [http://www.z-a-recovery.com/]("http://www.z-a-recovery.com/")  I hope that works for you.  What was wrong with Knoppix?  Did it not work?  Or were you not able to get the files you needed?

---

### Post by randomco on 2007-05-13
Hi all, sorry I haven't responded in a few days, I was away from home.

I decided to splash out a tenner for Zero Assumption Recovery (ZAR) about an hour ago, for some reason there is a 75% discount on weekends :S!. Anyway, ZAR is currently copying file 25000ish of 75000ish of the stuff I chose to restore to an external drive which I managed to borrow for a few days. It comes to about 25GB so I'll probably shove it all onto DVD afterwards - which could take a while. Seems to be working although the program recognised that some files (about 15%) were corrupt. I also need to scan the 12GB of 'empty' space left over from the gParted incident for any files I might need.

Wish me luck, and thanks to everyone who helped, losing all your data is scary!

Mike

BTW: Knoppix was not what I needed, due to the nature of the problem, and also I didn't bother with Norton Ghost - mainly because the data wasn't critical and I didn't have a disc to put the image on, because I needed the external drive I had for the restore itself.

---

