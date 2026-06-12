---
title: "CRC errors"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by nerdoneirik on 2007-08-28
Ok, so i know this may be outof the relm of ubuntu help BUT I figure i'll try because I am hopelessly lost. I used to have a duel boot with windows and ubuntu. Unfortunetly I was not the one that set up my computer so I have no idea how it was done and with what configurations. One day I was in windows and decided to shut down my computer. I went about my business and realized after about an hour, it was still in the process of shutting down. So I did something stupid - I just manually shut it off. The next day when I went to turn it on in windows, it wouldn't boot. Thinking it was just windows being trixsy I tried booting in to Ubuntu, that was a huge no go. 

I admit I kinda began to panic.

It said I had a crc error. I tried to google on ANOTHER computer how to fix crc errors but it seems like they usually occur when trying to transfer data from a cd... I wasn't transfering ANYTHING when I shut down. So I just figured I'd reinstall Ubuntu and just use that from now on (thanks to a stroke of paranoia I had just bought an external hard drive and filled it with my precious things so theres no data I really need to recover).

On my work pc I downloaded ubuntu and burned a disc. I got home and put it in my lovely cd drive and tried to install. The dreaded crc error popped up again for that. 

Any text I find online to fix a crc error requires that i run something once i've already booted into the computer. i can't even load an OS without it halting and saying CRC error.  What do I do? It there something wrong with my hardware? I'm an extreme noob so if any one could get back to me with simplfied instructions I would be extremly grateful. Even if you just tell me "Your hard drive bit the big one", I know nothing so anything would help!

---

### Post by zero-9376 on 2007-08-28
i think you need to be a little more specific, what is the exact error message.

is your bios set to boot from cd?

---

### Post by nerdoneirik on 2007-08-28
It really only says "System Halted CRC Error"

My bios are set to boot from cd and it will get to the welcome screen of the cd which has the main menu. If i try and install ubuntu, check the cd for errors or ANY of the options on the cd, it goes to a completely black screen that says:  "System Halted CRC Error"

When I try and go in to Ubunto or windows that is already installed on the computer it just says "System Halted CRC Error" and nothing else.

---

### Post by ryanawall on 2007-08-28
Try running DBan:
 [http://dban.sourceforge.net/]("http://dban.sourceforge.net/")
 
after that try to install Ubuntu again, hopefully after DBan you won't get that error anymore.

---

### Post by nerdoneirik on 2007-08-29
Ok, so I tried to run DBan. I tried every command they gave (autonuke, dod, dodshort etc, and even the trouble shooting ones) and i got the same error message:

boot autonuke
loading kernel.bzi...........
loading initrd.gz
Ready.
Uncompressing Linux with LZMA...
LZMA: Decoding failed. System halted

Then I tried re-starting without any disc in to see if it would some how start booting in to the ubutu on my hard drive and to get the exact error message. This is the EXACT error message that comes up when ever i try and boot in to ubuntu (hopefully I'm not giving out any vital information, like I said I'm a noob.... so if I am hopefully nothing bad will happen...)

booting 'Ubuntu, kernal 2.6.15-23-386'
root (hd0,1)
 Filesysem type is ext2f's partition type 0x83
kernal /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
     [Linux-bzImage, setup=0x1c00, size=0157774d]
initrd /boot/intrd.img-2.6.15-23-386
     [Linux-initrd @ 0x1f94000,0x6as406 bytes]
savedefault
boot
Uncompressing Linux...


crc error

--System halted

That is the EXACT error message. It's no clue what any of it means I can take a wild guess... maybe it doesn't recognize my hard drive?  I have no idea. Any help would be awesome. If nothing makes sense please pm me or reply to me and say exactly what they need and i can try and figure it out. I'm sorry, I'm a super noob and really confused. :confused:

---

### Post by nerdoneirik on 2007-08-29
Would the best solution be to just buy a new hard drive and try that? OR a motherboard? Or a whole new computer? If it helps, I have a shuttle not a pc... does this problem right a bell with anyone else?

---

### Post by Ben Margolis on 2007-08-29
Hi,

I'm having the same issues. I found [http://forums.debian.net/viewtopic.php?t=16848&highlight=crc+error](http://forums.debian.net/viewtopic.php?t=16848&highlight=crc+error) , which suggests....


memtest,
save bios settings
flash bios...

in that order. i'm currently trying memtest. Memtest86+ came on the linux rescue CD that used to try dban (giving the same error you got).

Good luck! I'm in my schools computer lab hoping something good will happen.

---

### Post by Ben Margolis on 2007-08-29
Okay, so I ran memtest86 for about 15 minutes before it died inexplicably.

But then I tried running dban, and it got past the LZMA and started formatting. Hopefully it'll keep going. It says it will take about 2 hours..... I'm not sure I like that, I'm not sure I have much of a choice.

I have a compaq presario v5304US and was trying to get a dualboot going with Win XP. All day I've been trying to run the install and keep getting errors indicating my CDs were bad (could not find xxxx file on install CD). The CD was in a hot car (not directly in sun) for a couple days. I thought that was it, but then Ubuntu would no longer install over it. I really hope this will allow me to dualboot.

I hope this helps.


Updates: about 20 minutes into DBAN (autonuke), I get a syncing error. I try again, and get a kernel error, attempting to kill init, or something along those lines. Then I try again and get bad sectors. Then, the Linux Rescue CD actually boots! I'm not sure what this means, other than dumb trying and trying again actually seems to be working.

---

### Post by nerdoneirik on 2007-09-05
Okeydoke, well none of that worked. I still got crc errors after running the memory test. I talked to a friend and he believes that it's my hard drive. So I'm going to go ahead and buy a new one. If that does work then I suppose it's my motherboard (?). If anyone else has any ideas, I'm open and desperate. If it's not the hard drive... le grrr. I have a shuttle so I have no idea if i can even replace the motherboard....

I will be installing ubuntu when i get my new hard drive (if it works...) and so I shall prolly return once I try that. Last time i tried, there were issues with my moniter, but hopefully that's all worked out. Hrmm or it may have been my graphics card. 

Yeah. I'm a noob x 3.

But thank you Mr. Ben Margolis for trying!

---

### Post by Ben Margolis on 2007-09-05
ACTUALLY, I should have updated. I kept getting hopeful. Then I gave up and sent my laptop in under my 1 year warranty. I just got a confirmation they recieved it today. In 7-9 days I should get it back.


I think it's the hard drive too. Those things are generally cheap now a days, which is good. Good luck!

---

### Post by r_bazghaleh on 2008-01-16
Please chech whether your cdrom compatible with your motherboard or not?

---

