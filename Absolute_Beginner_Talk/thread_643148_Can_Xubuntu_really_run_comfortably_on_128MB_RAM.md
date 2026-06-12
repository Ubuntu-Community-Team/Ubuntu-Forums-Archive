---
title: "Can Xubuntu really run comfortably on 128MB RAM?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-17
I am running Xubuntu on my laptop with 512MB RAM and I'm only running FIrefox and the system monitor right now and it says I'm using something like 130MB RAM. The Xubuntu website says that it CAN run on 64MB, but will run "comfortably" with 128. Can I assume that when I put Xubuntu on my Dell Pentium3, 1Ghz, 128MB RAM it will send sleeping processes to the swap to run it comfortably?

---

### Post by edsmaffs on 2007-12-17
My friend's set up Xubuntu and it runs fine on his 128MB RAM system, so yes I think so.

---

### Post by DarKnyht on 2007-12-17
I was running Xubuntu on my laptop with only 192MB RAM, and some of that was tied into the integrated graphics card.  It used the swap for some work, but I rarely noticed a slowdown.  The few times it did it was because I had OpenOffice installed on it.

I think you should be fine as long as you don't attempt something like OpenOffice on it.

---

### Post by patoruzu on 2007-12-17
Yes, it will swap idle processes. In fact the default swappiness of Ubuntu is quite high and is sometimes recomended to lower the value to reduce the swapping process.
And the word comfortably depends on the use you are going to give the computer. If you are only going to use firefox and a few other programs at a time then it's going to run comfortably. But if you are planning to run 15 windows of Firefox, play music, chat with your favorite IM client, and be using some Office Suite all at once, then you are going to suffer xD

---

### Post by brunetteredhead on 2007-12-17
I would think you would be fine.  You have to keep in mind that firefox can actually be a rather memory intensive browser and that is why it would seem like you would normally have problems.  The best thing you can do is give it a whirl, and if you do notice slowdowns try and find alternative, less memory intensive programs to use rather than the ones that are installed by default.  Also, setting up a reasonably sized swap partition on the hard drive would be helpful.

---

### Post by Pogeymanz on 2007-12-17
That's weird. I have Windows 98SE on it now and I use OpenOffice. It takes a few seconds to open up, but it doesn't hurt too bad. Is Xubuntu significantly more resource-heavy than Windows98?

---

### Post by patoruzu on 2007-12-17
I don't think so. By default ubuntu tries to dump as much as it can to the swap just to keep RAM memory free. This keeps the processor kinda busy. You should try editing the swappiness option in /etc/sysctl.conf

sudo gedit /etc/sysctl.conf

and add or edit the line so that it says
vm.swappiness = 10

you could try other numbers instead of 10, I think that the default value of swappiness is 80.

Also run 
sudo sysctl -w vm.swappiness=10
that way you don't need to restart the system for the changes to take effect.

Other thing you should consider is prelinking the applications.

take a look here [http://ubuntuforums.org/showthread.php?t=1971]("http://ubuntuforums.org/showthread.php?t=1971")

Openoffice enjoys eating your memory. Those steps really helped to tune the system to run that kind of applications.

---

### Post by Pogeymanz on 2007-12-17
Thanks.

So, high swappiness means the system stores things in swap sooner than it would with a lower number?

What are the pros and cons of high/low swapiness?

---

### Post by uxe1 on 2007-12-17
and does any one know the default *swappiness*  of xubuntu over ubuntu or kubuntu?

---

### Post by BeardlessForeigner on 2007-12-27
I too am curious about Xubuntu on low-mid memory machines. It sounds like it should run fine on a computer with 128+ MB RAM. However, when I recently installed it on an eMachine w/ 512 MB someone had given up on and found that after logging in ~200 MB are already being used. Only about 50 MB come from processes listed in system monitor. I'm wondering if the integrated graphics are somehow hogging massive amounts of ram, but I don't know how I can check/fix it.

---

### Post by tgalati4 on 2007-12-27
I tried Xubuntu on an old Dell Inspiron 7500 (PIII, 500 MHz) with 128 MB RAM.  It ran but it was pokey.  Added a 128 MB stick and it's much snappier.  Memory is cheap these days.  Try to max out what you can and you will happy.

Machines of that era can normally take 256 MB per slot.  If you have two slots (most laptops do, you can probably get 512 MB).

---

### Post by yaknowwat on 2007-12-28
I wouldn't suggest 128 MB with Xubuntu I would suggest something like fluxbuntu.

I tested it on an old HP same specs as the person above just about and it was pretty slow for what itwas going to be used for, youtube videos where like a slide show if thats a good enough example.

Xubuntu on boot takes a total of around 130 MB though has swappable parts ot make it slightly better for older machines, but I'd suggest Xubuntu for something like 256MB RAM and a 1Ghz processor personally..

Im testing fluxbuntu under 96MB RAM in a VMware and it runs very snappily though there are a few things that need to be setup for it though such as the current release doesn't have ' *.deb ' associated to install by default little things like that. Youtube runs alright though im not sure if the youtube running nicely has to do with my graphics card but i will admit it did have a bit of a lag.

edit* i put fluxbuntu at 42 MB o RAM or so and the video performance was similar to 96 MB so but, i did notice lagg spikes in it. SO It seems like fluxbuntu might be ok for 128MB RAM.  You may want to choose Xubuntu (or just another distro made for old comps) for usability sake though.

---

### Post by Pogeymanz on 2007-12-29
Well, this is an old Dell PC with PIII 1Ghz and 192MB RAM. I thought it was 128, but it appears that it's actually 192. I'll look into fluxbuntu anyway, that's probably a better idea.

---

### Post by zipperback on 2007-12-29
> **tgalati4 said:**
> I tried Xubuntu on an old Dell Inspiron 7500 (PIII, 500 MHz) with 128 MB RAM.  It ran but it was pokey.  Added a 128 MB stick and it's much snappier.  Memory is cheap these days.  Try to max out what you can and you will happy.

Machines of that era can normally take 256 MB per slot.  If you have two slots (most laptops do, you can probably get 512 MB).

You might want to check out fluxbuntu 
It has pretty low system requirements.

Or you can also checkout DSL which has a very low system requirement too.

zipperback
:popcorn:

---

### Post by vector99 on 2008-02-02
I use in my old laptop Toshiba Satellite 1620 CDS, with 96MB ram and hard drive 4.3Gb! If I don't run many programs simultaneously runs OK!

---

