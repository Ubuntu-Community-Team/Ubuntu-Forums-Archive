---
title: "Oops with windows xp...please help me"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-25
Ok, I was watcing youtube videos after listening to my friend talk about how cool Ubuntu is and I thought i'd like to try it out. I followed the Dual boot write up as best as I could (Found on UBuntu) and I chose the "First" option when I installed and partitioned. I downloaded Ubuntu, burned, installed, it works, been playing around with it, think its neat, just need to gain some knowledge before I go diving into it. Well...did i dive in to deep or what? How do i get to windows XP again!? I hope i didn't get rid of it or something. I read something about being able to choose what i boot...when I turn my PC on all i get is bios menu options (like always) and then it goes straight to Ubuntu. So really...how bad did i **** up? luckily i saved my school files and stuff. Built this pc about 3 weeks ago, so not much on it luckily. Please help a windows use that has never installed linux until tonight. 

-Justin

---

### Post by thisiam on 2008-02-25
good thing you backed up, quick fix is format and reinstall and try again.
i'm actually dual booting my other computer right now. install xp but didn't install any programs in case i mess up and have to reinstall windows.
not sure but i would try booting up with a live cd and see if you can delete all partitions except the NTFS where you would have windows

---

### Post by HoLLyw00dGT on 2008-02-25
By live cd do you mean the windows install live CD? I already had xp installed and then installed ubuntu.

---

### Post by mevets on 2008-02-25
Judging from screenshots I see on the web, I think you resized your windows partition and used the free space for ubuntu. That is the case then it should have installed grub for you. If you are not seeing a screen that says 'Loading GRUB' after your bios, then you might be booting from the cd still. You take the cd out, change you bios to boot to hd first?

---

### Post by thisiam on 2008-02-25
> **HoLLyw00dGT said:**
> By live cd do you mean the windows install live CD? I already had xp installed and then installed Ubuntu.

i would use the Ubuntu cd that you use to install, gparted should show you all the partitions.
system->administrator->gparted

---

### Post by HoLLyw00dGT on 2008-02-25
Took the cd out right after the install like it said to do. Unfortunately for some godforsaken reason...when i try to go into my bios my tv says "No Signal" Which i dont have an extra monitor atm to try it on. **Using a Westinghouse 32" HDTV as monitor** I used [HTML]http://www.psychocats.net/ubuntu/installing[/HTML] and followed that. On this part of the installation [http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png) i used like 60gig

-Justin

---

### Post by thisiam on 2008-02-25
> **HoLLyw00dGT said:**
> Took the cd out right after the install like it said to do. Unfortunately for some godforsaken reason...when i try to go into my bios my tv says "No Signal" Which i dont have an extra monitor atm to try it on. **Using a Westinghouse 32" HDTV as monitor** I used [HTML]http://www.psychocats.net/ubuntu/installing[/HTML] and followed that. On this part of the installation [http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png) i used like 60gig

-Justin

is guided the option you selected?
i selected manual and created 2 partitions from the left over space after i installed windows.
gave my ext3 partition 30gb and swap partition 1024 MB.
just finished and i am able to boot into both windows and Ubuntu.
also mount ext as root "/"

---

### Post by HoLLyw00dGT on 2008-02-25
This is what i'm getting:

NTFS - 70 gig

ext3 - 218 gig

extended - 6 gig

linux swap - 6 gig

unallocated - 1.31 Mib

ext2 - 3 gig

unallocated 127 Mib

---

### Post by thisiam on 2008-02-25
> **HoLLyw00dGT said:**
> This is what i'm getting:

NTFS - 70 gig

ext3 - 218 gig

extended - 6 gig

linux swap - 6 gig

unallocated - 1.31 Mib

ext2 - 3 gig

unallocated 127 Mib

ext3 is ok but 6gb swap is a lot, bring that down a bit.The rest i don't know why  you would have created them for.
i would delete them all except the NTFS one and see if your windows still works then try the dual boot again with just ext3 and swap file.

---

### Post by HoLLyw00dGT on 2008-02-25
IDK how to delete all of them except my NTFS. I know some of it was partitioned for my backup when i installed xp but idk which one. Plus when i DO delete it how do i get back 2 windows? Just does it auto?

---

### Post by thisiam on 2008-02-25
if you know how to delete the NTFS partition you should be able to delete the rest. remember GPARTED
at this point you got nothing to lose so what i would do is delete the ext2,ext3 and swap file. 
you know if you gotten to a point where you don't know what to do its always best to start over and not make the same mistakes again. you said you built this computer right ?
well how about you boot up with the windows cd and delete everything and you said you backed up right.
start over and try again, best way to learn.
goodnight.

---

### Post by HoLLyw00dGT on 2008-02-25
Well, deleted partitions, windows cd just prompts me to install it again. Says grub root error or something upon startup. Went into my bios (hooked up a shitty crt monitor cuz my HDTV wont work in bios) and did the xpress recovery. So when I get home from class I am gonna try installing Ubuntu again but i guess i need a better write up or something. I followed the directions and just never had the option upon startup to choose between xp and ubuntu. Thats all i want is 2 OS lol

-Justin Thx again btw for your quick responses at 2am =P

***EDIT***

Wow...I think I might have done it right in the first place...just saw a SS of Grub boot menu. I never saw that before and i'm pretty sure its because my TV said "No Signal" at the top...i waited and then it booted Ubuntu after the 10 seconds or whatever. If that is the case, which very well may be, i'm pissed as hell lol. IDK wtf 2 do though about my TV

---

### Post by mevets on 2008-02-25
haha, maybe you are being presented with the screen. in that case try hitting down 4 times then enter after your TV goes out. This will select windows, but it may not givin you had so many partitions.

If then menu is to hard to navigate in the dark you should edit /boot/grub/menu.lst s that there are only 2 choices, ubuntu and windows. This will make it much easier to select the menu entries cause you have less to get lost in.

---

### Post by HoLLyw00dGT on 2008-02-26
Well i'm on my crt and i can see it now. like 4 or 5 selections...ubuntu works...when i hit xp pro all it does is

Starting...


then nothing and it doesn't open.

---

