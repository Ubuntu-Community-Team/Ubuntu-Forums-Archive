---
title: "First install a rocky start"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by rogue_trader on 2008-04-19
Hi everyone,

I have been using windows for ages, and XP served me quite well at work and home. Since I do not know why I should shell out the bucks for vista to get the same as before, just bigger and buggier, the new windows was no option for my me.

So I downloaded kubuntu 7.10 and installed it yesterday. Everything worked fine on my samsung r41 laptop, including the automatic install of restricted drivers for wlan access and graphics. I was really impressed. After connecting to the internet and changing the software sources in adept to get new update, I saw quite a few packages were ready for an update. I decided to update and then the trouble started.

At first, downloads worked fine, but then an error message occurred and the updating process stopped. I tried to reboot (old windows reflex I guess) but then - after selecting kubuntu I got a FILE NOT FOUND error and was stuck. Since I am a linux newbie, I figured I might have done something wrong and reinstalled everything. I could not resist the temptation to use the update function again when I was finished though. But then the update process crashed again, and after a reboot the load screen just remained black. I was stuck again.

OK I might have no clue about the inner workings of linux, but I think t is really scary that the installation of updates can crash your system so bad that you cannot access anything.

Don't worry, I experienced a lot of scary stuff with MS' products as well, so I am willing to give linux a few more tries (or to learn how not to screw up my own system in the first 5 minutes after install *g*).

Should I just download 8.04 and try again? Just install portions of the upgrade packages? Or in any particular order?

Thanks in advance.

---

### Post by meborc on 2008-04-19
hmm... you said you changed the software sources... what do you mean by that? maybe you added some non-gutsy sources (hardy maybe)... did you use the terminal or the gui to upgrade?

pls attach your /etc/apt/sources.list file 

just to check the sources are OK :D

---

### Post by warbread on 2008-04-19
Can you be more specific about the errors you encountered?  It might be telling you something that's obvious to more experienced people, but fly by unnoticed by the uninitiated.  Anything you can remember may help.  Even better, try and replicated the problem and take a screen shot of the error and upload it to us before you reboot.  

Screenshot:  Applications->Accessories->Take a Screenshot

---

### Post by rogue_trader on 2008-04-19
I used the GUI. I selected a German mirror of the internet resources and then started the installation without changing anything else (uninstalling of software or adding of additional software).

Sorry for not using the correct terms / a more exact description, but I am online with my XP right now and downloading 8.04 in the background, so I cannot have a look and check.

RT

---

### Post by rogue_trader on 2008-04-19
Warbread,

if the vague descriptions from my memory are not sufficient, I will install it again and have a screenshot.

What I remember is:

The download worked fine. About 170 of 920 (not the exact figures) were about to be updated. Download size was about 250MB. Then the exchanging and upgrading of packages started. I remember a package aking longer called lipc6 or something like that. 2 or 3 packages later the error occurred. The system continued to appear normal until the reboot. Then the crash became apparent.

RT

---

### Post by warbread on 2008-04-19
It's not critical to use the correct terminology, but without a description of the error, there's little anyone can do but throw guesses out.  Next time something bad happens on your desktop, try taking a screen shot of it and uploading it to photobucket or something so you have a reference.

---

### Post by meborc on 2008-04-19
i really can't think of anything why this would happen :( i hope it was just some server inconsistency, but i doubt it... hope you will have better luck with hardy, it will be released soon so it is the best of the best :D using it now without any major problems, few small glitches still need to be fixed

---

### Post by ugm6hr on 2008-04-19
If you are already donloading 8.04, give it a try.  It's almost ready for the official release, and it will update in a week to the real thing anyway.  I think that is reasonable if you are dual-booting.

Just a point - I gather Kubuntu 8.04 does not have LTS support (unlike Gnome Ubuntu).

Updates can sometimes cause problems with hardware (kernel updates - but you can go back to an old kernel anyway).  However, if the actual update process causes the system to crash, there is something wrong with the updater.

Whether this is a problem with Adept (the Kubuntu updater), I don't know.  Did you lose internet connection while downloading updates?

---

### Post by rogue_trader on 2008-04-19
Thanks for you help anyone,

I will try to install 8.04 - hope that works. But I will make sure I get screenshots if things go wrong! :)

RT

---

### Post by rogue_trader on 2008-04-19
Now I am back online with the 8.04 RC. Everything works fine now, including updates.

I think that my last try was not successful mainly due to my changing of options before I fully understood them.

Anyway, 8.04 runs smoothly.

Thanks again
RT

---

### Post by ugm6hr on 2008-04-19
Welcome to Ubuntu RT.

I should try 8.04 myself - but I have grown out of the urge to see what new toys the latest version brings!

---

