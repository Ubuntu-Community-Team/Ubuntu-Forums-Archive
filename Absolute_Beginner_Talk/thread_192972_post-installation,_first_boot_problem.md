---
title: "post-installation, first boot problem"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-09
i am currently running an amd64 with windows already installed. i'm attempting to put ubuntu on this machine also and dual-boot. right now, i only have 5.10 and my cd burner has problems with iso images..don't ask.

i installed it and everything went fine, but whenever i get to the first boot, it locks up with a blank screen and a mouse pointer that i am able to move around. nothing loads up and i've even left it overnight in that state to see if it was just really slow.

i tried reinstalling ubuntu again after this and it doesn't help.

i appreciate your time in helping me get ubuntu on this machine.

---

### Post by Luke771 on 2006-06-09
Maybe you could try a net-install if you have a good connection to the internet. I've never done that so I can't say how it's done, but it's probably worth a try: check out that possibility on the official Ubuntu site.

---

### Post by shanepardue on 2006-06-09
well, i'm using the cd's i got from ubuntu..i've used them on different machines and they work perfectly.

---

### Post by shanepardue on 2006-06-09
does it have anything to do with me running the i386 with a 64-bit setup?

i'm kinda of clueless because i know the cd is good and i've even reinstalled the whole os. not sure what i could do from here.

---

### Post by Dragonfire on 2006-06-09
[QUOTE=shanepardue]does it have anything to do with me running the i386 with a 64-bit setup?

i'm kinda of clueless because i know the cd is good and i've even reinstalled the whole os. not sure what i could do from here.[/QUOTE]


More than likely. You should use the Unbuntu for 64bit processors. It's most likely that your cause is conflicting video drivers, or the version you put on there does not/cannot support your machine's video hardware/capabilities.

---

### Post by shanepardue on 2006-06-09
so with the amd64 ubuntu, i'm going to run into a lot of incompatibilities with software and such?

thanks for the response by the way!

---

### Post by Dragonfire on 2006-06-09
[QUOTE=shanepardue]so with the amd64 ubuntu, i'm going to run into a lot of incompatibilities with software and such?

thanks for the response by the way![/QUOTE]


Well, when using a 64 bit processor, you would normally use the 64 bit version install disks. This ensures that you have the best chance of complete compatability. You should always try to use the most appropriate disk for the system/computer you are installing on. Installing 64 bit on a standard processor(such as pentium 4, or AMD Athalon) should be avoided, as there will be driver/hardware/software conflictions.

And no problem. At LCT, we strive to help you as best we can.
(now back to scouring for those 0 reply threads...)

---

### Post by shanepardue on 2006-06-09
but i've seen many people talking about using the i386 cd with their 64-bit to be able use more programs without problems of incompatibility.

with the 64-bit ubuntu and processor, isn't there problems with flash and other plugins, codecs, etc?

---

### Post by brentoboy on 2006-06-09
im running the i386 version on my amd64. You probably have a new pci-express vidio card with a really fresh chipset.  that is what I had when I ran into the same issue a few months back.

chances are your graphics card got mis-recognized.

reboot, from the boot menu (grub) select the recovery option.  this will boot your system and dump you in a text terminal window instead of trying to boot to graphics.  it will log you in as root, and give you a command prompt.

run this:

```

nano /etc/X11/xorg.conf

```

note, the X in X11 is capitol, the rest is all lower case.  

this command will open an ugly (but functional) text editor, and it will open up your config file for X-windows (the GUI environment)  While you are in there, you are going to tell it to use the generic vidio driver instead of the optimized one it thought matched your hardware.

This file is layed out in "Sections" you are looking for the secion that defines your vidio card.  mine looks like this...
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```
yours might have...
```

	Driver		"nv"

```
instead of ati, those are the two common ones, but it could be anything really.

change the driver line (only that line) to be 
```

	Driver		"vesa"

```
that is the generic driver.

once you have that fixed up, save it and close nano (I believe ctrl+x propmts you to save and then closes.

then, reboot, which can be done by issuing this command...
```

shutdown now -r

```
the shutdown command requires a time (you can schedule a planned shutdown at a specific time, but we just want it do start now, so we said "now"  the -r means "reboot" instead of just shutting down.

then ubuntu should start.

let me know how it goes.

---

### Post by brentoboy on 2006-06-09
[QUOTE=shanepardue]
with the 64-bit ubuntu and processor, isn't there problems with flash and other plugins, codecs, etc?[/QUOTE]

yes!

the short answer is that anything that is truly free and open source can be compiled as amd64 and work great.  and, if you need a server or something, stuff compiled for the amd64 will be way, way faster if the whole OS supports it, but, sadly... some software just aint truly free.  I use the i386 version becuase my pc is a desktop and I need all the codecs and other not-truly-free stuff.

---

### Post by shanepardue on 2006-06-09
oh man! thanks sooo much for the replies! i was nervous i wouldn't get any earlier today!!

as far as that code, i will try that first chance i get (i'm at work pretending to do stuff right now)

now, i know you mentioned pci express card there and i didn't know if that meant this problem would only occur if i had one of those and the fact is, i don't have one, but i do have a slot for one that will be utilized eventually!! this code is still applicable right?

also, when this problem occurred with you, did your mouse still show and was really choppy and slow?

thanks again for all the responses!!!!

---

### Post by brentoboy on 2006-06-09
this is the same no matter whether you use  pci, isa, pci-e, or agp.  it is just a mis-recognized chip set.  instead of admitting it didnt recognize your card, it guessed.

for me, it happened in breezy but not dapper.  Im sure that it would happen in a particular release of ubuntu and may or may not be a problem in other releases becuase someone might have noticed and fixed it (or unfixed it) between any two releases.

mine used to freeze right after playing the "drums" sound that means login, but it wouldnt show much of anything on the page.

the point at which it freezes will vary depending on your gx card, as soon as the gui issues an illegal command, it will freeze.  so it will very from chipset to chipset.

good luck

---

### Post by shanepardue on 2006-06-09
YES!! this particular issue is happening with breezy also...i don't have a dapper cd yet and my burner sucks with isos so this is probably the same exact issue!!

thanks for the help!! i really appreciate it and i'll reply with the outcome once it's discovered!!!

---

### Post by brentoboy on 2006-06-09
by the way,
when I burn isos, I burn at 8x isntead of 48x,   if I dont, the end result just doesnt boot.  some CDs just arent made to be burned that fast, but pretty much every cd on the market can burn at 8x with no issues.

---

### Post by shanepardue on 2006-06-09
i've burned at 1x!! haha

[http://www.ubuntuforums.org/showthread.php?t=187379](http://www.ubuntuforums.org/showthread.php?t=187379)

---

### Post by brentoboy on 2006-06-09
two words for you:

plex writer

thank heaven for shipit
:)

---

### Post by shanepardue on 2006-06-09
is plex writer a good one?

and yes..shipit is soo awesome.

---

### Post by brentoboy on 2006-06-09
I bought my first plexwriter back when 8x was screaming, since then, I have purchased (for work or with friends) about 50 more.  I personally believe they are the best cd burner available.  and, if you dont want this year's latest craze, they arent that expensive.

I've never tried an external one though, so I cant vouch for that

---

### Post by shanepardue on 2006-06-09
i should most definitely invest in one then..i'm tired of waiting for shipit cds even though i'm very grateful. ha

---

### Post by shanepardue on 2006-06-09
i checked and it's already using the generic video driver so it's not that.

any other ideas?


p.s. the mouse is choppy and slow even before i try to log in.

---

### Post by shanepardue on 2006-06-09
let me rephrase the problem a little....

when ubuntu 5.10 i386 loads up, it get to the login screen. once there the mouse is very slow and choppy. i am able to login, but it's at that moment that the screen goes brown with a mouse pointer (that can be moved around) and stays there forever (left it like this overnight once) 

nothing else comes up.

i've already tried setting it to generic video driver in xorg.conf


i'm really anxious to get this running on my good pc!


AMD64 3400+

---

### Post by shanepardue on 2006-06-13
i'm still stuck on this. if anyone could help, that'd be great!!

---

