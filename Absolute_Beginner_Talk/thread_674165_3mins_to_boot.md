---
title: "3mins to boot ?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Chris2169 on 2008-01-21
Hi Folks,

I'm just moving over to unbuntu and have set it up to dual boot on my laptop with xp home addition.  So far I'm impressed, with reservations, but very impressed with the advice here.      Anyhow onto the possible problem.  When I select unbuntu from grub loader the screen goes black for almost exactly 3 mins then up pops the log on screen and we're good to go.  The laptop is a medion with a P1.7m, 60gig hdd, 512ram, ati radeon 9600 card and a a pro wireless 2200. That seems like an awfully long time to boot ?  I mentioned this yesterday as part of another post and someone posted this link;

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

I carried out the instructions ( I think) and the the whole thing died, refused to boot up ubuntu at all !  Resulting in a kernel panic thread last night. Anyhow thanks to forrst pixie et al who worked with me last night but it still resulted in having to reinstall so I'm nervous about having another go ! Does anyone have any other suggestions ?

Thanks in advance !!!!

Chris

---

### Post by PurposeOfReason on 2008-01-21
Press alt f1 at boot and see where it stops. Don't worry, all this does is give you a text screen so you can see what is being loaded.

---

### Post by Chris2169 on 2008-01-21
Thanks for that how interesting ! 

OK as you suggested I hit alt f1 on boot and guess what, it booted in 41secs !!!  So I tried booting agin without alt f1 and it was 3 mins.....

So I tried again and this time hit alt f1 after a minute and lo it booted in secs from then.  So whatever is causing the hang is being affected by the alt f1.  

Finally each time I hit alt f1 the following line is on the screen;

KINIT: no resume image doing normal boot

This appears to be where it sticks until either 2mins something passes or I hit alt f1 !!!!

Waiting more interesting and helpfull comments

---

### Post by PurposeOfReason on 2008-01-21
This is a known problem. To fix it (always be text) do the following:
```
sudo gedit /boot/grub/menu.lst
```
find the kernel line for Ubuntu . It will look something like
```
kernel /boot/vmlinuz26 root=/dev/sda2 quiet ro
```
Remove the quiet.

---

### Post by Chris2169 on 2008-01-21
Nope,

I get a stream of text for a couple of secs imediately the boot starts but then the screen goes black and I have to wait for the three minutes.  Unless of course I press alt f1 while I'm waiting in which case it boots instantly !!!!!!

---

### Post by spiderbatdad on 2008-01-21
i have the same problem after a fresh install due to incorrect usplash.conf settings.```
gksu gedit /etc/usplash.conf
```set x and y to match your supported screen res.

---

### Post by JoshuaRL on 2008-01-21
I second that.  If the screen goes black and it takes forever it's definitely usplash.  Fixing that is the real fix because it restores the splash screen and tells you how fast it's loading.  Just make sure you run this after updating usplash so it loads it automatically:

```

sudo update-usplash-theme usplash-theme-ubuntu

```

---

### Post by Chris2169 on 2008-01-22
Grrrrr.....I tried the 'vga' fix again yesterday.  This resulted in Kernel panic again - see another thread - and another install.  I've tried amending the usplash.conf file and followed by the update code and its done it again, kernel panic.....at least this time I have the live CD handy so I'll have another go at reversing it.  Any suggestions as to why either;

I'm having this 'hang' during boot ?

or

Why whenever I try and fix it it results in kernel panic ?

Thanks 

Chris

---

### Post by philinux on 2008-01-22
See link known bugs.

Also try installing and running startupmanager

The kernel panic can be fixed by undoing what you did or just reinstalling grub (not the whole system) from the live cd.

---

### Post by Chris2169 on 2008-01-22
Ha you must be physcic, I've just reinstalled grub. No joy kernel panic kicked in immediately......just going to try reversing the the res 'fix'

---

### Post by philinux on 2008-01-22
I'd recommend startupmanager

---

### Post by jbalazs on 2008-01-22
This is what worked for me
sudo gedit /boot/grub/menu.lst
 
find the kernel line for Ubuntu it will look like this

-f3f9-43d9-8281-8e91da84651d ro quiet nosplash

change splash to nosplash

---

### Post by Chris2169 on 2008-01-22
Thank you, thank you, thank you .......It worked, my 3 min boot now takes 37secs.  Yipee !!!!!!!:):)

---

### Post by JoshuaRL on 2008-01-23
That's the quick and dirty fix.  If you do the usplash fix, it will restore the splash page, which will then return results if you need to boot verbose.  You can do whatever works for you, but the usplash fix is the real fix of the problem.

---

### Post by Chris2169 on 2008-01-23
Hmmmmm, intersting.  Well the story so far is that every time I've tried to the use the usplash fix its resulted in a catastrophic failure, kernel panic synch failiure etc and as a result I have had to reinstall ubuntu 3 times in 3 days.  However this fix has fixed the problem without casuing any failures and allowed me to get on with evaluating ubuntu.  I'm not denying your right, I've been fiddling with Linux for 3 days now what do I know !!!! But I'm not going near the usplash file again until someone can offer me an explanation as to why everything collapses when I amend it and suggest a way of prenting it again !!!!

In the mean time a big thank you to all the people who've treid to help me over the last few days :)

---

