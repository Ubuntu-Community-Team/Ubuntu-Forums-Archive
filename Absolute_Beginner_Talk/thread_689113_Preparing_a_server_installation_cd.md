---
title: "Preparing a server installation cd"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by bheki on 2008-02-06
I have been using linux for jus over a year now and I have finally convinced other users at home to switch over from winxp to ubuntu they agreed. However I am looking at building a server and I have downloaded the 7.10 and open to 6.06 LTS if thats the better choice.

My problem is that I can not understand the upacking and preparing an installation part. Is there a tutorial out there (i couldnt find anything) to assist me in this? Or if someone can please give me a step by step.

It took 13 weeks to get the desktop cd deliverd from UK to South Africa so I am not realy prepared to wait for that long to get a ready to install server cd.

Please Help!

---

### Post by hyper_ch on 2008-02-06
Well, did you download a .iso cd-image?

---

### Post by bwtranch on 2008-02-06
Very funny post! I like your attitude. I would not want to wait either. Tell us what you are having problems with and we will try to help. Best Regards.

---

### Post by bheki on 2008-02-06
Yes I downloaded ubuntu-7.10-server-amd64.iso and tried preparing it to for installation and wrote it to a cd but I failed dismally to get it going. 

So ya I need a clear instructions as to what file to move where and so on before the cd is ready to be a bootable cd.

thanks

---

### Post by bwtranch on 2008-02-06
OK, first off, it needs to be a bootable CD, that is, it needs to be an image, not just files copied over. I think you probably have that, if it's a iso 9660 you've got that covered. 

The next thing is to have your machine boot the thing. This differs among machines, but it is when your machine boots, there is a screen that says BIOS, usually you have to hit a F function key and you get options. Find the one that says Boot From a CD. Then you should be OK. On one machine I have it's F10 on another it's F12. But, it's always that first splash sceen you see when the computer boots. You may have to go through it a couple of times. If you miss it, press Cntl + Opt + Alt and Delete key to force a re-start. (It's the four finger discount)

---

### Post by bheki on 2008-02-06
:confused::confused:> **bwtranch said:**
> OK, first off, it needs to be a bootable CD, that is, it needs to be an image, not just files copied over. I think you probably have that, if it's a iso 9660 you've got that covered. 

The next thing is to have your machine boot the thing. This differs among machines, but it is when your machine boots, there is a screen that says BIOS, usually you have to hit a F function key and you get options. Find the one that says Boot From a CD. Then you should be OK. On one machine I have it's F10 on another it's F12. But, it's always that first splash sceen you see when the computer boots. You may have to go through it a couple of times. If you miss it, press Cntl + Opt + Alt and Delete key to force a re-start. (It's the four finger discount)

So after downloading it and **Before** burning it as a bootable CD (using programs such as Nero or Alcohol, on winxp) what files should I have on a "ready to burn" image?

Excuse my ignorance, but I have been realy stuck on this!:confused:

Thanx again

---

### Post by bwtranch on 2008-02-06
I'm not too sure on those Windows programs. I haven't used them in so long, but you should have an option for burning an iso IMAGE. That is what you want. Maybe somebody else can chime in about the Windows programs. I just use Linux. K3b is my preferred app for burning. I used to use Nero and it should do the job.

---

### Post by bheki on 2008-02-06
I will try when I get back home and let you know of the results.

Appreciated!

---

### Post by SteveHillier on 2008-02-06
> **bheki said:**
> :confused::confused:

So after downloading it and **Before** burning it as a bootable CD (using programs such as Nero or Alcohol, on winxp) what files should I have on a "ready to burn" image?

Excuse my ignorance, but I have been realy stuck on this!:confused:

Thanx again

Nero will work but you probably need to use a non oem version.  The copy I have which came with a CD drive has an option to 'Burn an image to CD' that is the option to use and then you simply select the iso file you want to burn to disk.
As a thought, do not try to burn at maximum speed.  If your disk says it will burn as 48x try 24x.  It takes a little longer but is less prone to corruptions during the burn process.
Caom back is you need more.

---

### Post by hyper_ch on 2008-02-06
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by bheki on 2008-02-25
It worked, it worked, it worked! now I will be starting configurations and hope to enjoy the power of ubuntu!

thank you all for your help

---

### Post by andrewPCT on 2008-02-25
I guess it is too late for this, but when I was using Windows, I found this free program very handy for burning ISO images to CDs: [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

