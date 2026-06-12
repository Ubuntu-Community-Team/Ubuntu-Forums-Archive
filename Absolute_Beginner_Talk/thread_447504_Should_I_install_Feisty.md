---
title: "Should I install Feisty?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by krugman on 2007-05-18
Hello everybody:)

after a long break away from linux, I was considering installing Feisty on my new laptop. However, I have read that there were quite a few problems with this version; for instance, it seems that s2ram and s2disk don't always work, whereas this is a critical feature for me since I am on a laptop. Has something been done about that?
Is is this issue Feisty-specific? I mean, if I install another distro (or a previous version of Ubuntu), is it supposed to work? 
The laptop in question is an ASUS U1F (1.06 Ghz Core Duo).

Oh, and btw, I was wondering something: I would like to use some windows apps like Illustrator and some chess programs. Hence, I will certainly install Virtual Box, but if Iunderstand correctly, I won't be able to use a program which is installed in a windows partition right? I will have to install it also in the virtual HDD created with virtual box, true?

Thanks for your help!:)

---

### Post by giallofever on 2007-05-18
I am not to sure about laptop specs and their hardware as I have never installed linux on a laptop, but if you don't need anything on the drive... give Ubuntu 6.10 a try. It's pretty compatible and stable and if it doesn't support everything then you could revert back.

Not too sure on the windows apps either as I have only run standalone apps (.exe) like uTorrent on Wine.

---

### Post by Alterax on 2007-05-18
I have had excellent results with running Ubuntu Feisty on a Lenovo laptop (x86 build) and on an iBook G4 (unsupported PowerPC build).  The easiest to do, I guess, is to try and see if it works best for you.

---

### Post by mikewhatever on 2007-05-18
There are people that seem to be very unhappy with Feisty, yet others hail it as perfect. Suspend and hibernate functions are know to be problematic for a lot of users with all versions of Ubuntu, not that I have statistics though. You'd have to find out for yourself whether or not the features you need work on your laptop, but do search for your specs too.

---

### Post by Rui Pais on 2007-05-18
thats why there are liveCD ;)

you try them to see if everything works (or what it works) 
then **you** decide to install or not.

---

### Post by mikewhatever on 2007-05-18
Hm.., can you try suspend and hibernate using a live CD?

---

### Post by krugman on 2007-05-18
Thx guys for the answer! It is weird, I am supposed to get notified when there is a reply, and I didn't get anything...

well, I think one guy tried to install ubuntu on the U1F, and it seems that s2ram and s2disk do not work, hence my question about a remedy.

Since I have downloaded pclinuxos also, I might give it a try.

---

### Post by Rui Pais on 2007-05-18
> **mikewhatever said:**
> Hm.., can you try suspend and hibernate using a live CD?

well, at least suspend-to-ram should work (it depends on hardware, motherboard and ram). 

Hibernate i'm not sure what happen when it waken...  it should be going for the hd grub... maybe directing then for cdrom boot and kernel should detect a saved session (maybe check first if swap partition are detected and mounted).

---

### Post by misfitpierce on 2007-05-18
As said it does depend on hardware. I hear some have trouble with it and some don't. I myself do not, thankfully but I would say come back to linux and install feisty and see how it runs on your machine. Should run great :)

---

### Post by Sunflower1970 on 2007-05-18
I have Feisty on two desktops, and I love it. I tried it on my laptop, and although it runs beautifully, the suspend doesn't work, although it worked perfectly in Edgy. I use it quite often, so I ended up downgrading. I'm now going to wait to see if they fix it in the next version. (I sure hope so!)

---

### Post by krugman on 2007-05-18
after a bit of research, I have found this:
[http://ubuntuforums.org/showthread.php?t=194426](http://ubuntuforums.org/showthread.php?t=194426)

It seems that it solves the problem right?

---

