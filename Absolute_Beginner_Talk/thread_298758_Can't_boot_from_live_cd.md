---
title: "Can't boot from live cd"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by fatnic388 on 2006-11-13
Hi. Just so you know i'm a complete linux newbie, hence only trying to run from the CD and not fully installing it just to see if I like it first. However, there's my problem.

I've selected to boot from CD in BIOS which it does. I get the splash screen with the option to run it. However, when I select to run Ubuntu it displays
```
loading /casper/vmlinuz...
loading /casper/initrd.gz.....
```After that I get nothing but a black screen wit ha blinking cursor. And that's it!!!

I'm using a 2.8Gig Pentium 4 with 512MB RAM and a 180GB hard drive.  Any suggestions?

---

### Post by podunk on 2006-11-13
How fast did you burn your CD? If you burned at the default speed you likely have a few errors. Reburn it at 4X or so.

If that doesn't';t work there is an option to run Mem test 86 on the CD's boot menu. Chose that and let it cycle a few times.

---

### Post by anaconda on 2006-11-13
Just out of curiosity..
What display card have you got?
what kind of display you got? any unusual resolution or refresh-rates?

It might be that your display card just doesn't work out-of-the-box.. maybe you could try some boot time options..

---

### Post by fatnic388 on 2006-11-13
OK. Reburnt the ISO and ran memory check a few times. Still no joy.

My display card (according to Windows device manager) is ATI Radeon Xpress 200 series. How would I go about adding boot time options?

---

### Post by Sef on 2006-11-13
> How would I go about adding boot time options?

Press F2 or F3, I believe.

---

### Post by fatnic388 on 2006-11-13
Ok. Then what? Sorry if I sould like a complete idiot but i'm new to this linux thing. I have managed to get it working on a different machine. However, I ideally wold like it onthis machine, as it has the internet connection.

---

### Post by fatnic388 on 2006-11-13
OK. Just noticed that when the CD begins to boot 'Unknown keyword in config' displays for a second then the splash screen displays. Could this be causing a problem?

---

### Post by tanman on 2006-11-13
Hi
In actually have the exact same problem. I had Dapper loaded on a Gateway with a Pent 4 and was loving it. I a bit a go I bought a Acer computer with Pent D and the Radeon express 200 video card. I gave my Gateway to my Finacee for she need a newer computer. I was never able to get the Live CD to boot on the Acer. This is the same CD I used on the Gateway. I than downloaded Edgy CD and the same thing. This CD works on a old HP and also the gateway computer. So just for a test I booted to a G parted Live CD and this will not work either. Being curious I than booted to a XP install CD and when I click install it does not find the drives and gives me a error message. Just seems like the Drives are locked or something and will not let any thing just the drives from factory. 
   Needless to say I am giving the acer to my fiancee and taking my Gateway back. I suppose a person could wipe that drive clean somehow and just get another external drive to replace that one. As of now though I am not a Acer fan and will go back to Gateway.

---

### Post by tanman on 2006-11-13
Just to add to my post the the mesaage I get is can not fing PCI and something. Sorry I am at work and can not remember the whole message. The Ubuntu splash screen shows up and then when it starts to load the bar at the bottom goes all the way to the right and then half way back to the left it freezes. I have to than have to power down my computer.

---

### Post by cr4ck3r5 on 2006-11-13
Iv got ati mobility radeon x700 and athlon 64 and the same problem... After splash screen my pc freezes. Its probably the drivers problem... but iv no idea how to deal with it
i wanna admit that everything is workin fine on suse 10.0; 10.1
dunno why ubuntu 6.10 dont wanna run
thx for any advices

---

### Post by mo79 on 2006-11-13
> **fatnic388 said:**
> Hi. Just so you know i'm a complete linux newbie, hence only trying to run from the CD and not fully installing it just to see if I like it first. However, there's my problem.

I've selected to boot from CD in BIOS which it does. I get the splash screen with the option to run it. However, when I select to run Ubuntu it displays
```
loading /casper/vmlinuz...
loading /casper/initrd.gz.....
```After that I get nothing but a black screen wit ha blinking cursor. And that's it!!!

I'm using a 2.8Gig Pentium 4 with 512MB RAM and a 180GB hard drive.  Any suggestions?

Might be your CD/DVD drive having probs reading it? I had a similar problem. Swap it with a different drive to see if it works, or brush the tray/use a CD/DVD cleaner.

---

### Post by fatnic388 on 2006-11-13
> **tanman said:**
> Just seems like the Drives are locked or something and will not let any thing just the drives from factory. 
 I'm not sure that it is the hard drive. From what I understand with the Live CD everything is loaded into the memory straight from the CD so the drive wouldn't be used at all.

I'll attempt to swap the drives and see what happens.

---

### Post by fatnic388 on 2006-11-13
Right. Well it's not the CD drive. Just tried it with the other one. Also, it's not the HDD as I have already installed it onto my other computer. I stuck in the HDD from that and tried to boot it from there. Got as for as the screen saying 'starting up...' then froze. There's something else stopping it progress, but i'll be damned if I know!!!!

---

### Post by cr4ck3r5 on 2006-11-13
Have you tried the alternate cd?

---

### Post by tanman on 2006-11-13
Well what I can not understand is why when I boot from CD nothing seems to work. Not even  XP install disk. This disk is not a upgrade disk either. It can not see the drives at all. It just gives me a error message and says that drives are either damaged or corrupted. It is not my CD drive for I put in the recover disk that came with the Acer computer and was able to reinstall from those. I did not want to do this, but I was seeing if it would install. So except for the Acer recover disks nothing else works. It has me completely baffled.

---

### Post by cr4ck3r5 on 2006-11-13
is it not booting at all? only recovery cd u can boot from?
thats weird cos iv acer laptop and i never used xp that they supplied.
in fact i cant use f.e. original ati drivers (Catalyst) cos they wont install (sic!)... but im using omega drivers instead.
Now... i tried to install on my laptop distros like gentoo debian and **ubuntu** and it seams i always have the same problem (cant configure X; pc freezes while starting X)....
only suse configures right
why?!?

---

### Post by mo79 on 2006-11-13
> **tanman said:**
> Well what I can not understand is why when I boot from CD nothing seems to work. Not even  XP install disk. This disk is not a upgrade disk either. It can not see the drives at all. It just gives me a error message and says that drives are either damaged or corrupted. It is not my CD drive for I put in the recover disk that came with the Acer computer and was able to reinstall from those. I did not want to do this, but I was seeing if it would install. So except for the Acer recover disks nothing else works. It has me completely baffled.

While you wait for a solution - you'll get there, have hope :) - you should email Acer support about this, if you haven't already.

---

