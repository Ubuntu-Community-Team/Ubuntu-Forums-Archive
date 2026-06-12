---
title: "PPC ibook G4 blank screen trying to get 8.04 working"
date: 2009-01-17
forum: Apple Hardware Users
---

### Post by FaiSua on 2009-01-17
Hi everyone, 

I am excited to try linux for the first time, even with all the obstacles, I am interested to see if it is worth all the hassle.

I booted with the ubuntu 8.04 alternate ppc iso file, It installed and then restarted.  After the boot finished I was left with a half black and half white screen.

So i went to this link: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and attempted to follow the directions, but here is where I am confused, I got it into rescue mode, But I am not sure how to do the rest of the process. 

I am stuck currently at a window with the header: [!!] Enter rescue mode, then in the box it says:
enter a device you wish to use as your root file system. You will be able to choose among various rescue operations to perform on this file system

Device to use as root file system: 

/dev/hda1
/dev/hda2
/dev/hda3
/dev/hda4

1,2,and 4 give error message, so I guess my root is 3. I don't remember setting that up when I installed but I guess I will go with it.

after going with hda3 I have a window that has the same heading as before with a list of rescue options:

execute a shell in /dev/hda3
execute a shell in the installer environment
reinstall yaboot boot loader
choose a different root file system
reboot the system

am I going in the right direction?

Thanks, Garrett

---

### Post by McFrostey on 2009-01-17
well you can always try and reinstall it... 
or try the "Alternate PowerPC.ISO" Version 8.10
is Ubuntu worth all this hassle well with PowerPC you have VERY limited options
no compinies or very few officially support PowerPC
PowerPC these days is all community.

---

### Post by FaiSua on 2009-01-17
thanks MF, what distro would you recommend for a 1 ghz 256 ibook g4?

---

### Post by McFrostey on 2009-01-17
256 ram?

---

### Post by McFrostey on 2009-01-17
theres many but YellowDogLinux officially supports nothing but powerpc but i used it and it sucks soo bad... if you can live with minor bugs id stick with ubuntu.

---

### Post by FaiSua on 2009-01-17
Yeah that's why im trying to figure this out. Any help?

---

### Post by McFrostey on 2009-01-17
put your installation disc back in your ibook restart and hold down "C" reinstall it again if it still happens lemme know.

---

### Post by boydrice on 2009-01-17
@FaiSua I have a 2004 G4 ibook, the Ubuntu 8.04.1 live CD worked flawlessly for installing Ubuntu.  At the boot prompt you will most likely need to type "live video=ofonly" from there you should have no problems.  This version of Ubuntu seems to work the best on my hardware with even wireless with WPA/WPA2 encryption working.  By the way since you are a PPC user I strongly recommend checking out this site: [http://www.ppclinux.info/](http://www.ppclinux.info/) there is a ton of great info and a supportive PPC-centric community.  Honestly you don't need the alternate cd.

---

### Post by FaiSua on 2009-01-17
thanks body rice, I will look into it.

McFrosty, I restarted it and it seemed to work this time, although it's prompting me to login and when I type in my username it prompts me for my password. But when I type nothing shows up for the password, Just blank. I thought maybe it was hidden so I just tried entering the password but to no avail???

---

### Post by mkvnmtr on 2009-01-17
Right nnow I am downloading the updates from an install of 8.04 on my G4 Ibook.I finally added enough software that I had some conflicts that seemed to make it over heat and freeze. I have used 8.04 since it first came out and really like it. I think your main problem is a lack of ram. Mine came with 256Mb also but I added a 1Gb stick before I started with 6.06. It is more than enough and doesn't cost much. It is very easy to put in. You should give it some thought. They say that 256Mb is not enough to install from the live disk and that after you git an install from the alt. disk it is pretty slow.

---

### Post by FaiSua on 2009-02-19
Using the (Ubuntu Desktop CD 8.04.1 PowerPC), I booted from yaboot with 

live-nosplash-powerpc

Everything worked perfect, even the wireless airport extreme packages installed automatically and worked great! Thanks for your help everybody.

Shanti

---

