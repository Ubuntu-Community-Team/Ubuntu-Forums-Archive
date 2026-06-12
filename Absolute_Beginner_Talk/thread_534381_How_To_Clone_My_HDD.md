---
title: "How To Clone My HDD?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-25
I had the recent misfortune of having to reinstall my OS due to me changing hardware.

Would I would like to know is there a 'cloning' applicaton similar to Norton Ghost that could do the job and allow me to burn to DVDR and be able to BOOT from the disc.

I have seen mentioned in earlier threads G4L (Ghost 4 Linux?) but members have said it did not meet their requirements. As it transfers the image to a FTP server instead of locally.

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

[img]http://i11.tinypic.com/4pxn8k4.jpg[/img]


OR would be possible to use a DOS based version of Norton Ghost v8.x which is floppy based?

Any advice/suggestions would be welcome as I don't think I could bear having to reinstall again.

Thanks

---

### Post by hysteresis on 2007-08-25
clonezilla will clone your disk:
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)
It runs off a bootable cd.  It's kind of a pain to use, but it works.

---

### Post by chrome307 on 2007-08-25
Thanks for that, but just looking at the webpage, doesn't it just clone to another HDD not to removable media eg CDR or DVDR.

---

### Post by mikex on 2007-08-25
> **chrome307 said:**
> Thanks for that, but just looking at the webpage, doesn't it just clone to another HDD not to removable media eg CDR or DVDR.

This is what I use, it works like magic.

[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

---

### Post by chrome307 on 2007-08-25
Can you explain how you get it to work ... Acronis True Image as it's $50, so I want to be sure beforehand.

Is it a Windows based application, therefore I need to install it on a Windows based PC and then SLAVE my Ubuntu HDD?

Or is it a bootable CD that I can just use on any PC?

---

### Post by mikex on 2007-08-25
It's both a windows app, and a linux app. The CD you create with it once installed onto windoze is actually a version of linux when you boot up off the CD. It can create images of windows, linux, and dual boot. I work for a major Corp. and we use it there. Trust me, it will save your a$$. I use it several times a day after playing with this Ubuntu so I can get back to something that works if I muck it up. It's great to know you can destroy your linux setup and just boot up off the CD and get back what you had. I create the images on a USB HD.

---

### Post by Benoone on 2007-08-25
> **mikex said:**
> This is what I use, it works like magic.

[http://www.acronis.com/homecomputing/products/trueimage/](http://www.acronis.com/homecomputing/products/trueimage/)

I have used Acronis for Windows for years but now I have moved up to a tri-boot (w2k, xp and ubuntu) and it clones my (500gb sata) sda to (500gb sata) sdb.

But, in the process, mucks up the boot superblock of the sdb primary partition3 that GRUB normally lives in and  my sdb ubuntu will not boot from the clone :(

It's almost like Acronis/Ghost do not know what to do when GRUB is in a primary bootsector so they just start to write zeros to fill in the space?

Maybe I should put GRUB in /boot but that still does not solve the Acronis/Ghost bug?  Maybe I'm just missing something? 

The sdb clone MBR is intact and both Micro$oft partitions boot the same as the original. 

I confirmed that both Acronis and Ghost11 produce the identical results as I have gone in and viewed the bootsector and it is indeed, mostly a a bunch of zeros and... GRUB is gone.  Correct me if I am wrong but I understand that they are file type copiers and not bit/block copiers.  

I used Trinty Rescue kit (TRK) to run the (bit copiers) dd and ddrescue and dd does a good job but I can't get the speed up to anything reasonable.  Once... I copied 500gb in 2h 30m but can't seem to duplicate that feat anymore?  If anyone has any hints I'd appreciate them as all my hair is now white.

Thanks for reading and any suggestions you may have.

Benoone

@Chrome

Acronis installs in Windows and then lets you make a bootable linux CD that does all kinds of backups/clones.  Nice as it sees the network and USB drives.  

You can search puzo for "hiren" - It's there.  And, it's a small world :)

Benoone

---

### Post by chrome307 on 2007-08-25
So back to square 1 again :confused:

**[COLOR="blue"]ROFL ..... it's a small world and it appears it's getting smaller!![/COLOR]**

---

### Post by asmoore82 on 2007-08-25
> **chrome307 said:**
> I had the recent misfortune of having to reinstall my OS due to me changing hardware.

If the hardware changes sufficiently enough to where you need to re-install,
Why would a Clone of that exact same setup work?

and even better question, what exactly did you do that caused you to re-install??

---

### Post by chrome307 on 2007-08-25
Just to clarify I exchanged my gfx card for a different one manually editing the xorg config file and changing it to VESA  etc

Installed new card and rebooted .... initially got the splash screen but then it rebooted itself again and this time I was presented with the CLI ...... I could not remember the command to reconfigure the card hence the reinstall.

Hope that explains the situation?

Lastly I wish to keep the hardware 'as is' therefore there would be no further additions etc - so the next time if I have any human/PC errors I can use the 'Restore CD/DVD' to reinstall the OS and the core applications I'm using.

---

### Post by asmoore82 on 2007-08-25
> **chrome307 said:**
> Just to clarify I exchanged my gfx card for a different one manually editing the xorg config file and changing it to VESA  etc

Installed new card and rebooted .... initially got the splash screen but then it rebooted itself again and this time I was presented with the CLI ...... I could not remember the command to reconfigure the card hence the reinstall.

Hope that explains the situation?

Lastly I wish to keep the hardware 'as is' therefore there would be no further additions etc - so the next time if I have any human/PC errors I can use the 'Restore CD/DVD' to reinstall the OS and the core applications I'm using.

^^^! you re-installed an entire OS instead of looking up/learning how to change 1 word in 1 text file??

in that situation, just use the LiveCD you installed from and you get a full
Graphical OS to look up the solution to the problem.

Also, it would seem to me to be more trouble than it's worth to restore the
system 100% from a CD/DVD because of file ownership and permissions.

---

### Post by chrome307 on 2007-08-25
Yep that's right I took all that time to reinstall instead of writing down the commands for reference.

I thought this section was for 'Absolute Beginners' ??  ..... or am I failing to even understand this ??

Members have different degrees of IT knowledge - it seems that my lack of this with this OS has left you incredulous ....... it's a scandal I know.

---

### Post by WebSiteGuru on 2007-08-27
Dont feel bad chrome307, I actually did the similar thing (after it took me a whole month of hard work configured everything to the way I wanted) and went into edit my xorg (because of GL Desktop setting ordeal) and screwed everything up. I, also, went back to square 1 and had to re-installed the OS.

That is why I am also looking for something to backup my OS state just incase I ran into this type of problem again.

@ asmoore82 - FYI! Not all of us newbies know all the code and how to edit xorg configuration (we are just following instruction on the forums that we found). And we are a beginner here trying to learn how to use Ubuntu. (Dont tell me you never been in a beginner stage and screwed your system up, we all been there [some more than other].) It is a learning process, and we all have to go through it.  ;) Hope you understand what I mean. :popcorn::guitar:

---

### Post by chrome307 on 2007-08-27
***@ WebsiteGuru***

Thank you for supportive comments.

I still am none the wiser however I would recommend that you install 

APTonCD

```


http://aptoncd.sourceforge.net/


```

This application ( via Add & Remove ) once installed allows you 'backup' your existing downloads that you have carried out via APT. You can burn this to a CDR or DVDR depending on the size.

This is useful, so if you have to reinstall at anytime, you just load the core files and then use the APTonCD to reinstall the packages.  It could also be used to install software on other PC's if required I guess.

Anyway goodluck and if you ever come across ..... please let us all know !! :)


[IMG]http://i17.tinypic.com/5xgmjic.jpg[/IMG]

---

### Post by WebSiteGuru on 2007-08-27
You are welcome! :D

Cool feature :KS, especially for backing up installed Applications (packages). I'll keep this option on the back burner, just incase I need it. :D

I'll still look around for Linux version that will works thou. I rather have the whole state for the OS backup with the setting I had predefined. ;)

---

### Post by Roaster on 2007-08-27
^^^! you re-installed an entire OS instead of looking up/learning how to change 1 word in 1 text file??

Is this not the "Absolute Beginners " forum? Try not to be so condescending in your answers. I for one have done the exact same thing! Hopefully I'll learn from my mistakes and I won't have to ask the likes of you. Best regards:)

---

