---
title: "[SOLVED] Cannot boot linux (live cd)"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Jim01 on 2008-01-02
Hi,

I've just got ubuntu 7.10 on a live cd.

I dont wont to install it just yet I just want to play with it.... but I cant boot it....

I've checked the cd itself by testing it and its fine according to linux.

Anyway I press the start/instal linux and it came up with some message saying something or other not found but I couldnt read it because it flashed on and then off and was replaced with the ubuntu loading screen.

After sitting on that screen with the bar going from left to right and back for about 1:30min it goes to a black screen and then it says:

ATA.01: revalidation failed (errno=-5)
ATA1: SRST faild (errno=-16)

and so on and after a while it in the end says:

Run-init: /sbin/init: I/O error
Kernal Panic - not syncing: attempted to kill init!

and thats it apart from abit of other lines which I didnt copy and paste as there was a bunch of them and I couldnt be bothered writing them down..... let me know if to solve this if you need the rest of the writing.

Help most appreciated.

---

### Post by xeth_delta on 2008-01-02
Just a short question, did you also check the integrity of the iso image before burning the cd?
[https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24]("https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24")

Welcome to the Ubuntu forums!

---

### Post by Jim01 on 2008-01-02
> **xeth_delta said:**
> Just a short question, did you also check the integrity of the iso image before burning the cd?
[https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24]("https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24")

Welcome to the Ubuntu forums!

well I did the option second time round when this thing came up and it tested the integrity and it was ok BUT..

I got this cd from the australian apc magazine (december 2007 issue so its 7.10) and it gave me the options of downloading the iso but there was also a md5 thingo on the cd which by looking at the link I think I was supposed to download and burn that too... is that supposed to be the case?

---

### Post by Jim01 on 2008-01-02
well reading the link you sent more thouroughly the md5 is supposed to check the integrity of the iso thingo... I have the iso on the computer so I'll check it under windows while keeping an eye out for replys.... I'll let you guys know how it goes.

---

### Post by nwadams on 2008-01-02
so the cd had ubuntu on it already?...I dont' think you'd need to download any iso
what kind of computer are u using?

but the easiest solution might be to start from scratch and re-download ubuntu from the main website, burn it to a blank and try to boot to it

---

### Post by Jim01 on 2008-01-02
umm I'm using a computer with a pentium 4, Asus p5s800-vm-uayz mother board (uses agp graphics card)... umm lg dvd burner... umm ide seagate hd I think... anyway I did the check of the md5 sums and it says they are different.  that must be where my problem lies right?

---

### Post by nwadams on 2008-01-02
i'm not entirely familiar with md5 sums but i'd say so...the easiest solution might be to re-download the iso from the ubuntu main website
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and then burn it to a blank

---

### Post by Jim01 on 2008-01-02
> **nwadams said:**
> so the cd had ubuntu on it already?...I dont' think you'd need to download any iso

sorry I meant download meaning I downloaded it from the apc mag cd as instructed from the cd and onto the computer.

---

### Post by nwadams on 2008-01-02
ya, I would suggest re-downloading the iso of the ubuntu website, that will ensure the iso is not corrupt

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by xeth_delta on 2008-01-02
Jim01, remember to burn the new CD at a low speed, 4x at the most.

---

### Post by Jim01 on 2008-01-02
> **xeth_delta said:**
> Jim01, remember to burn the new CD at a low speed, 4x at the most.
umm yeah that might be a real good idea too... I burnt it at 32x lol... will get downloading tonight.

---

### Post by nwadams on 2008-01-02
well good luck,  let us know if you have further problems. I normally burn mine at 48x wihtout any problems(i'm testing fate, yes I know), so it's really luck of the draw. 

glad to have you witn us Jim

---

### Post by Jim01 on 2008-01-02
no worrys It might take awhile adjusting to linux from windows I was going to get windows for the computer I'm building but when recomended ubuntu from a source of xbox live (more than happy to let you guys know who he is... just pm me) who has used linux for over 10 years and said have a go at it so I am lol.... sounds pretty good from what I heard from him... he said its been more stable than windows lol... but anyway I should give feedback once I download ubuntu again and get it running and let you guys know...

Thanks for all the help ;)... very good replys within 10 minutes is very very very impressive... never known a forum with replys like yours ;) and within 10 minutes!

again thanks!

---

### Post by ugm6hr on 2008-01-02
> **Jim01 said:**
> sorry I meant download meaning I downloaded it from the apc mag cd as instructed from the cd and onto the computer.

This doesn't make sense.  You downloaded it from a CD onto your computer?  If it came with a magazine, you can probably just put it straight into your CD drive and reboot your computer.  It is unusual for magazine CD/DVD's to have .iso files on them (but I don't know about APC).

But if you've already downloaded it direct from Ubuntu - that will definitely work:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by xeth_delta on 2008-01-02
> **ugm6hr said:**
> This doesn't make sense.  You downloaded it from a CD onto your computer?  If it came with a magazine, you can probably just put it straight into your CD drive and reboot your computer.  It is unusual for magazine CD/DVD's to have .iso files on them (but I don't know about APC).

But if you've already downloaded it direct from Ubuntu - that will definitely work:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I actually think he downloaded it from a 3rd party site.

---

### Post by Jim01 on 2008-01-02
> **ugm6hr said:**
> This doesn't make sense.  You downloaded it from a CD onto your computer?  If it came with a magazine, you can probably just put it straight into your CD drive and reboot your computer.  It is unusual for magazine CD/DVD's to have .iso files on them (but I don't know about APC).

But if you've already downloaded it direct from Ubuntu - that will definitely work:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

first off apc is an australian computer magazine that comes with a bunch of software and it happens to follow linux and it had the latest ubuntu on it which is 7.10 bundled with the cd.... I downloaded the .iso from the as instructed.. yes it does have a .iso plus a md5sum to check it with... NOT DIRECT FROM THE UBUNTU WEBSITE... just to clear that bit up for the moment.  then burnt it with nero at x32... wont do that again at that speed.  Then put the newly burnt cd  in the dvd drive and shut down the computer with the cd in it... then rebooted... and selected the start/install ubuntu bit and that is where I had my problems... and then as instructed by you guys I checked the md5sum with the one give with the cd and they where different.

SO... currently I am downloading ubuntu this time direct from the website as that is probably more uptodate and the md5sum thingos should match and work hopefully...

Again I'll let you guys know how this go's.

---

### Post by nwadams on 2008-01-02
i wouldn't worry about the md5 sums with the download from the ubuntu main site, just burn it slow and boot to it

---

### Post by Jim01 on 2008-01-02
> **xeth_delta said:**
> I actually think he downloaded it from a 3rd party site.

Yes I would say apc is a 3rd party thingo and but it doesnt have the software on their website.. It has it all on cd. I only bought the mag so I could see what their opinion was on certain stuff as I am currently building my own computer.  And it happened to have the latest ubuntu on the cd that came with it.

---

### Post by Jim01 on 2008-01-02
> **nwadams said:**
> i wouldn't worry about the md5 sums with the download from the ubuntu main site, just burn it slow and boot to it

No worrys ;)

---

### Post by Jim01 on 2008-01-02
Well here are the results after downloading off the website:

Dowloaded it, burnt it at 4x with nero, Shut the computer down with the cd in it, rebooted, and pressed the start/install linux option.  This time it worked... took abit of time to load while it was on cd but who cares?  It did however stop sending feed to the screen and I was thinking... ok.... but I just happened to move the mouse and the screen all of asudden turned on and there was ubuntu.  I'm replying right now using ubuntu.. also I see that there is not much abit of a screen diference.  its about 10 mm (ruler size) on the right hand corner screen that is black... the other side looks ok though...

anyway while I've got it working I'll play around with it.... if I need anymore help I'll just start another thread and I'll change the topic to solved.

Thanks for all your support yet again guys ;)

---

