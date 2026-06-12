---
title: "Ubuntu Freezes 30 seconds after boot"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by MasterRoshi on 2007-09-08
Hey, im semi new to Ubuntu; so please tone the technical stuff down a little =).

Alright, heres my problem: 

I have installed Ubuntu i386 on my Desktop PC three times now. the first time it froze at 88% on install. the second time i booted from the i386 CD, and it froze before it would start. this forced me to install from the alternate boot CD, which went 100% more smooth. It installed correctly, but then it had the same error as my other CD: it froze about 30 seconds in. 

I decided "hmm...must be a bad boot CD seeing as ive had linux on here before; but had to erase my hard drive". 

So i fired up the laptop and downloaded/burnt another i386 boot CD. This time there were no crashes, no freezes, but it STILL froze after startup. 

I HAVE tried failsafe gnome. using this i updated the entire system...for the first time it worked. when i logged into the updated 2.16 kernel, it locked up after 30 seconds again. 

any suggestions as what i should do? i know that ubuntu shouldnt freeze much, if at all, because it isnt like windows or mac. =/

here are my Specs:
2 250 gig WD hard drives
1 Linksys WMP54G (shouldnt matter...im hardwired)
1 NVIDIA GeForce 6600GT
1 SoundMAX Audio Card
1 52x CD/DVD RW drive
1 AMD Athlon 64 X2 Dual Core Processor (4400+)
2 Gigs (4 Sticks) of RAM
 and an ABIT AN8 ULTRA Motherboard

my ubuntu partition is on 55 Gigs of hard disk space; including swap. 

please help im really stuck and love ubuntu!

---

### Post by GMachine_24 on 2007-09-08
Hi:

There is a known issue . . . where Ubuntu freezes after logging in . . . and then takes 2 minutes or more until it continues with the start up....

... is this what happens? or does it just freeze forever?

I have this problem but only on my laptop. I'm using 6.XX LTNS.

It's a pain but your comp will eventually boot if this is the problem.

--gm

---

### Post by MasterRoshi on 2007-09-08
actually im not sure...i'll check it out. 2 minutes u said?

i dont have that much patience but i will test it lol.

is there any way to fix the issue? 

i mean i had Ubuntu 7.04 on there before, but since i wiped my disk its been a pain. ..and i wish i knew why. it worked amazingly before...

i'll let you know in 5 mins if it worked

---

### Post by Crafty Kisses on 2007-09-08
> **MasterRoshi said:**
> actually im not sure...i'll check it out. 2 minutes u said?

i dont have that much patience but i will test it lol.

is there any way to fix the issue? 

i mean i had Ubuntu 7.04 on there before, but since i wiped my disk its been a pain. ..and i wish i knew why. it worked amazingly before...

i'll let you know in 5 mins if it worked

You can try booting in verbose mode, and see where it actually freezes, like what part it freezes at.

---

### Post by MasterRoshi on 2007-09-08
alright its an unusual freeze. the mouse still works, but the keyboard and screen (maybe its X?) freezes. which is odd. usually a freeze means completely frozen. 

how do i activate verbose mode? if you let me know, i'll post the error or whatever. i mean...ubuntu/GNOME loads up: it just doesnt last long...

and i waited over 5 minutes for the un-freeze to occur and it didnt.

---

### Post by Dr Small on 2007-09-08
> **Codename said:**
> You can try booting in verbose mode, and see where it actually freezes, like what part it freezes at.
Is it CTRL + ALT + F8, which will output the info at bootup?
I would try that.. I forget which vt it is, but it is one of them. I am pretty sure it is F8 or F2.

Dr Small

---

### Post by MasterRoshi on 2007-09-08
> **Dr Small said:**
> Is it CTRL + ALT + F8, which will output the info at bootup?
I would try that.. I forget which vt it is, but it is one of them. I am pretty sure it is F8 or F2.


i did as you suggested, pressing CTRL + ALT + F8 several times during boot. this brought up the following:

*Running local boot scripts (/etcrc.local)
[    39.992000] BUG: soft lockup detected on CPU#0Q!
[    47.348000] rt61MlmeEnque: full, msg dropped and may corrupt MLME
[    67.620000] rt61MlmeEnque: full, msg dropped and may corrupt MLME
[    87.892000] rt61MlmeEnque: full, msg dropped and may corrupt MLME

etc. it goes on with that kind of script up to 268.956000

any idea? i dont have one lol

---

### Post by alienexplorers on 2007-09-08
Are you able to drop into terminal mode once the computer freezes:
> ctrl-alt-f1
If so bring up an editor such as nano and look what is inside the script at /etc/rc.local ....

---

### Post by GMachine_24 on 2007-09-08
You might want to check out this thread as there are a few suggestions about booting without the GUI so you can see the terminal output and some files you can check for possible error output info....

[http://ubuntuforums.org/showthread.php?t=490222](http://ubuntuforums.org/showthread.php?t=490222)

--gm

---

### Post by MasterRoshi on 2007-09-09
[QUOTE=please login and type

sudo /etc/init.d/gdm restart

and post the errors of this (if any).

I was only astonished because it is really rare to have to install printer drivers by hand. Tell me what printer do you have and I can help you with the installation (mostly...).

So:
-what are the errors when you restart gdm? [/QUOTE]
 this was from the post above about following the link.

well, i did that step by trying something different. i went into recovery mode for the kernel, and typed that in as root. my computer has been on for about a minute now; still not frozen. it DID however pop up with these errors:

Internal Error - failed to initialize HAL!

CPU frequency scaling unsupported - You will not be able to modify the frequence of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.


it seems to be working ok in this mode; except i dont have my frequency monitor but thats ok. problem is, i know it works... so wtf.

thats not the big issue, but whatever. im afraid to restart my desktop lol.

---

### Post by MasterRoshi on 2007-09-09
i rebooted, and its frozen again. great.

it worked when i did it in recovery mode...

---

### Post by Horomancer on 2007-09-09
I have the same problem roughly. I'm brand new to Ubuntu but have heard good things. I made a live CD from windows and double checked it with that MD5sum prog.
Everthing check out and the boot to the CD went without a hitch, but once it got into the desktop for installation everthing went to ****. After 4 tries, with the installer freezing at different points (total freeze, no mouse, no key combos, nothing but to power down my comp and try again) I got a full 100% install with the computer freezing on the 'Do you want to restart?' message.
I restarted and the comp said it couldn't boot from anything and to insert a bootdisk and hit any key.

---

### Post by MasterRoshi on 2007-09-09
ok i did restart, and im stuck again. it worked fine in the terminal mode kinda deal. or w/e its called.

i feel like a total n00b right now lol

---

### Post by MasterRoshi on 2007-09-09
thats it. im tired of this.


i went into XP and deleted my ubuntu partition. im going to try a fresh install...again. i just did one, but it froze on "copying files; 33%

the weird thing: it allows me to open and close applications, but freezes the keyboard...

and then, i disconnect the keyboard, and it freezes completely. possibly a keyboard error? although idk why THAT would be...because its a new keyboard. i have it converted to PS/2..its USB.


perhaps it keeps screwing me over because of a keyboard error? idk... =/

---

### Post by MasterRoshi on 2007-09-14
i was looking through the files, and appearently it was an unsupported keyboard. which is weird seeing as it worked fine before. so i bought a new one and problem solved. thanks for all the help!

---

