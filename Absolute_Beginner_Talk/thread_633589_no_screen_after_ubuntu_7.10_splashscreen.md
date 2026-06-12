---
title: "no screen after ubuntu 7.10 splashscreen"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by md11driver on 2007-12-06
this is the last linux chance for this laptop.  running an S3 86C270-294 Savage/ IX-MV video card.  i had one successful boot with video last night and enjoyed two wonderful hours of linux.  downloaded all updates, marveled at how well the wireless worked, etc.

today, the machine boots normally through the splash screen then blanks out the display.  i can enter my user name and password and the machine finishes booting judging from the hard drive activity.

i installed 7.04 and made it a dual-boot system because

sudo dpkg-reconfigure xserver-xorg

allows me to look at and change all the hardware settings (there's probably an easier way).  the os appears to know all the correct settings of the video card and monitor.

all my searching on google and my two earlier posts to this forum have been fruitless.  if you don't want micro$oft to make any more of my bucks please help.

i'll try anything.  i'd rather have a toasted linux computer than one running windows.

---

### Post by nonewmsgs on 2007-12-29
did you deselect any packages like ccsm?  

are you using fusion?

---

### Post by md11driver on 2007-12-29
thank you, nonewmsgs.  i did a normal alternate install of gutsy 7.10 with no additions or modifications.  by bootlegging on other posts, i have discovered how to reconfigure xserver and xorg files, but experimenting in video card drivers and monitors has been fruitless.

specs:  intel celeron@596 mhz, 255 mg ram, 4 gb partition devoted to ubuntu, S3 Inc 86C270-294 Savage/IX-MV.

i did alternate install because live cd didn't (and won't) run on my machine at current ram capacity.

i'm standing by.

---

### Post by LDRoamer on 2007-12-29
I have random times when the video fails after the splash screen both with the live CD and the installed system. I did some searching and one suggestion was to turn off the splash screen as sometimes it conflicts with the resolution that gets set when it goes to load after the splash screen. You could try that and see if it helps. I am not quite sure of the procedure to turn off the splash screen but I think it is something like adding "no splash" to grub. If you do some searches on the forum you will find the exact procedure. It may not work but it wouldn't hurt to give it a try.

---

### Post by md11driver on 2007-12-29
more information.  i followed this advice from another person's post:

"When your computer starts and you're in GRUB (you may have to hit Esc), highlight the kernel you want and press 'e'. Now add nosplash (remove splash if it's present) and, noacpi, nolapic, and noapic."

this allowed the computer to boot (judging from appropriate sounds) but still no screen.

---

### Post by clayts450 on 2007-12-29
I think it's something wonky with the S3 Savage card because I experienced this problem yedterday for the first time, not having had any problems for a whole week.

I resolved it by logging on through single user mode then running 

sudo dpkg-reconfigure xserver-xorg

at the prompt. For some bizarre reason the resolution had changed to 1980x1024 - a quick change to 1024x768 sorted it out, and it now boots fine again.

There are other suggestions - eg removing the splash screen as stated above, and also changing the video driver to 'vesa' rather than using Savage S3 - do a search on that too.

Touch wood, after resetting the resolution yesterday everything seems ticketty-boo again

---

