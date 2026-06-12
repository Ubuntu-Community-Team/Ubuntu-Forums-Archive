---
title: "Cannot open CD drawer"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by keithbchurch on 2007-01-10
Reading these forums I feel there should be a more basic level under "Absolute Beginner Talk"!

I've got an old Dell PC, Pentium 3, 128 MB RAM.  (I'm upgrading from Windows 98!) Despite a complete lack of knowledge I have installed Ubuntu, put a wireless network card in the PC and connected to the internet and can see my  Creative Zen Nano Plus MP3 player.  OK the PC and software did most of all the work, but never mind.

But I cannot reliably open the CD-drawer to put my music CDs in.  I have opened it, but it is not cooperating at the moment and nothing I try works.

I've gone into "Places", "Computer" and there is a tempting "CD-ROM Drive" Icon there. I click on it..."unable to mount volume". I've right-clicked on it and selected "open" and it has said "opening drive" (but it rarely does). I've tried "eject" (it doesn't).  I've tried pressing the button on the drive (the light comes on and it make a whirring noise).

Any advice?  

Keith

---

### Post by d3v1ant_0n3 on 2007-01-10
Hmm...If the eject button isn't working right, and 'eject' from a program is sometimes working, your drive might be on the way out?

---

### Post by OldTimeTech on 2007-01-10
"I've gone into "Places", "Computer" and there is a tempting "CD-ROM Drive" Icon there. I click on it..."unable to mount volume". "

I think you have your problem in the above quote.  Your CD may need special drivers???

---

### Post by nhandler on 2007-01-10
If you can't physically eject the cd, look for a tiny pin size hole on the drive. If there is one, use a pin or paper clip, and push it into the hole. This should cause the drive to open, and allow you to remove the disk.

---

### Post by meng on 2007-01-10
> **OldTimeTech said:**
> "I've gone into "Places", "Computer" and there is a tempting "CD-ROM Drive" Icon there. I click on it..."unable to mount volume". "
I think you have your problem in the above quote.  Your CD may need special drivers???
This just confirms that there's nothing in the drive to mount. I don't think that icon enables opening of the CD-drive door. One question for the OP: does the CD door open at other times (e.g. during boot) - wonder whether the drive itself could be faulty.

---

### Post by keithbchurch on 2007-01-10
Thanks for such prompt replies...

It'd be a big coincidence if the drive is on the way out...it worked OK under Windows 98.

The drivers issue sounds more likely. How does one get and install new drivers in Linux for a CD-ROM drive?  Indeed how can I identify what type of CD drive I have...because I might need that information.

Sorry to ask such basic questions...

Keith

---

### Post by OldTimeTech on 2007-01-10
ahhhh, because when I highlight and open dialog box on my cd-rom, it shows mount and eject.

So, if I had something in the cd-rom, it would automatically mount? 

See, learn something new everyday, thanks.

---

### Post by TooRight on 2007-01-10
Sometimes mine won't open either, usually typing ```
sudo eject
``` works, but when it doesn't I end up having to reboot my comp and popping it out then

---

### Post by meng on 2007-01-10
IIRC (and it's possible that I DON'T), clicking on the CD (or any other device) in the Places sidebar of the file browser/My Computer will auto mount that device if it is not already mounted. But it's the CD icon on the desktop that will allow you to unmount/eject the CD.

---

### Post by OldTimeTech on 2007-01-10
The drivers issue sounds more likely. How does one get and install new drivers in Linux for a CD-ROM drive?  Indeed how can I identify what type of CD drive I have...because I might need that information.


The only way I know is to open machine and pull out drive, should be written on top.....

Will look around on my machine :-D

---

### Post by OldTimeTech on 2007-01-10
> **meng said:**
> IIRC (and it's possible that I DON'T), clicking on the CD (or any other device) in the Places sidebar of the file browser/My Computer will auto mount that device if it is not already mounted. But it's the CD icon on the desktop that will allow you to unmount/eject the CD.

I've never put a cd icon on my desktop....I personally don't use my cd that much, so it's fine being under places :-D

---

### Post by meng on 2007-01-10
Well then I may just be talking rubbish! It happens when one loses one's mind ...

---

### Post by pebo on 2007-01-10
> **OldTimeTech said:**
> Indeed how can I identify what type of CD drive I have...because I might need that information.


```
dmesg | grep CD
```

should give you the info

---

### Post by OldTimeTech on 2007-01-10
Ahhhhhhhh Meng....can't be the problem......;)

---

### Post by OldTimeTech on 2007-01-10
> **pebo said:**
> ```
dmesg | grep CD
```

should give you the info

Pebo, thank you so much!

---

### Post by keithbchurch on 2007-01-10
OK.  A summary.

There is no CD in the drive.  So I understand I cannot do "mount" until there is.  So the problem is the door doesn't open for me to get a CD in.  

The door did open when I pressed the button on it as the PC powered down (Yeah!)  I didn't put a CD in it as I only had Sufjan Stevens to hand and I'd like to see it again.  The door didn't open when I pressed the button on power up.

I worked out I had an ATAPI CD-ROM drive by pressing ESC as the PC powered up.

Paperclip trick was tried already and just prompts the usual clunking noise.

As does "sudo eject" (You're pushing the boundaries of my capabilities by asking me to try this!)

Sincerely, thanks for all the replies.

Keith

---

### Post by keithbchurch on 2007-01-10
> **pebo said:**
> ```
dmesg | grep CD
```

should give you the info

It was actually me (Original Poster with misbehaving door) who asked that...

[   95.226957] hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
[   96.021367] hdc: ATAPI 40X CD-ROM drive, 128kB Cache
[   96.021396] Uniform CD-ROM driver Revision: 3.20

So is the problem that "uniform" driver?  Might a better one solve the problem?

---

### Post by tmatt95 on 2007-01-10
> **keithbchurch said:**
> 

Paperclip trick was tried already and just prompts the usual clunking noise.



There is an art to it :cool: . *You have got to feel around inside the hole with the paper clip until you meet resistance and then push. This should make the drive come out just enough for you to get your fingers around it. When I fund out about the paper clip trick, I tried it on a number of computers that I had near me and some drives were easier than others.  Good luck sorting the problem,
Regards Matt

*Be careful and do not break the drive when doing this though

---

### Post by OldTimeTech on 2007-01-10
[17179576.924000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179576.924000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179576.924000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000e400

this is what mine shows when I do the "dmesg | grep CD"

And my cd rom is definitely not a usb type.....hmmmmmmmm

---

### Post by tonyr1988 on 2007-01-10
This happened to me after I upgraded my motherboard (but had the same CD and DVD drives). I couldn't get my DVD out, either in Ubuntu or WinXP. This was pure luck, and it may not work for you, but this is exactly what was wrong with mine (eject wasn't working, it couldn't mount the CD, and it pretended that nothing was there). 

What I did was reboot, and while the BIOS was loading (even before GRUB shows up, at the *very* beginning of the boot-up), try and eject the CD. Then take the disc out, un-eject it (whatever you call it) and continue to boot into Ubuntu. I haven't had a problem since.

It could be a driver issue - I'm not sure. But for me, it seemed like it was more of a motherboard / BIOS issue (is that possible?), since it occurred when I upgraded my motherboard, and it wouldn't work under any OS I had.

Either way, good luck - and it doesn't hurt to learn the paper clip trick, especially when you need a CD out and don't want to boot your computer up! :D

---

### Post by meng on 2007-01-10
> **tonyr1988 said:**
> What I did was reboot, and while the BIOS was loading (even before GRUB shows up, at the *very* beginning of the boot-up), try and eject the CD. Then take the disc out, un-eject it (whatever you call it) and continue to boot into Ubuntu. I haven't had a problem since.
I dunno, sounds like voodoo to me! But it can't hurt!

---

### Post by TooRight on 2007-01-10
> As does "sudo eject" (You're pushing the boundaries of my capabilities by asking me to try this!)

lmaooo, too funny!!! :D

---

### Post by keithbchurch on 2007-01-10
> **meng said:**
> I dunno, sounds like voodoo to me! But it can't hurt!

I coming round to the Voodoo idea.

I've honed my paperclip skills.  The respondent who said there was an art to this is right.

I've found a few more things out as well...

I put in a music CD (obviously I borrowed my wife's copy of Cher's Greatest Hits just in case, rather than use one of mine).

I started up a music playing program which recognised the CD.  I used the "eject" command in that program.  The door opened!  I used the button to open and close the door several times.

But when I tried it again just now, it was back to "normal"

Thanks to all for the progress I have made...

Keith

---

### Post by OldTimeTech on 2007-01-10
Hey, I think we all learned something out of this.....


Wow, Cher's Greatest Hits, one of my favorites........

---

