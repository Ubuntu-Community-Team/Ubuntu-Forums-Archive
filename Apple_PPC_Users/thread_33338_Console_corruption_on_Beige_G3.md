---
title: "Console corruption on Beige G3"
date: 2005-05-10
forum: Apple PPC Users
---

### Post by linutic on 2005-05-10
All,
This is a fairly minor issue, all things considered, but I thought I'd post on the forum about in anyway and see if this has been cured before.
 
In console mode only (not in X) I have three vertical bands running down my screen which obscure/obliterate the text they cover. I haven't had any luck passing 'VGA=' options to the kernel in an attempt to maybe 'fix' it by using a different screen mode, so I presume such things don't work the same on PPC as they do on x86.
 
Here's a snapshot of the corruption I'm talking about:
[img]http://castor.ucc.ie/medren/ubuntu/screen.jpg[/img]
 
Note that the instance most prominent in this photo actually lies over an area of the screen that would otherwise be blank.
 
Thanks in advance for any ideas or suggestions...
-js

---

### Post by Ptero-4 on 2005-05-10
[QUOTE=linutic]All,
This is a fairly minor issue, all things considered, but I thought I'd post on the forum about in anyway and see if this has been cured before.
 
In console mode only (not in X) I have three vertical bands running down my screen which obscure/obliterate the text they cover. I haven't had any luck passing 'VGA=' options to the kernel in an attempt to maybe 'fix' it by using a different screen mode, so I presume such things don't work the same on PPC as they do on x86.
 
Here's a snapshot of the corruption I'm talking about:
[img]http://castor.ucc.ie/medren/ubuntu/screen.jpg[/img]
 
Note that the instance most prominent in this photo actually lies over an area of the screen that would otherwise be blank.
 
Thanks in advance for any ideas or suggestions...
-js[/QUOTE]
 Has you checked your display to see if it's damaged.
Also try to pass the parameter's in /etc/yaboot.conf (needs root privileges).

---

### Post by linutic on 2005-05-11
I think I can safely rule out display damage as a possible culprit, since it worked perfectly on the last system I had it connected to (which was a PC) and only seems to have this problem on this Mac under this particular display mode; i.e., no problems, artefacts, &c under X or full-screen MOL.
 
The other option sounds intriguing however-- I'll try it tonight; but I wonder does yaboot.conf have any bearing on my system, since (because it's OldWorld, and because I'm too lazy to futz with Quik) I'm booting it via MacOS with BootX? Shouldn't I just be able to append kernel parameters there?
 
Nevertheless I'll give it a shot. Clearly I have a bit to learn about PPC Linux still...
 
Many thanks,
-js

---

### Post by Ptero-4 on 2005-05-11
[QUOTE=linutic]I think I can safely rule out display damage as a possible culprit, since it worked perfectly on the last system I had it connected to (which was a PC) and only seems to have this problem on this Mac under this particular display mode; i.e., no problems, artefacts, &c under X or full-screen MOL.
 
The other option sounds intriguing however-- I'll try it tonight; but I wonder does yaboot.conf have any bearing on my system, since (because it's OldWorld, and because I'm too lazy to futz with Quik) I'm booting it via MacOS with BootX? Shouldn't I just be able to append kernel parameters there?
 
Nevertheless I'll give it a shot. Clearly I have a bit to learn about PPC Linux still...
 
Many thanks,
-js[/QUOTE]
 Yes you can append them to BootX, but AFAIK BootX don't save them. So you'll probably need to append them on each boot.

---

### Post by sangling on 2005-05-23
I'm getting exactly the same problem on my beige (Old World) G3 266Mhz with Kubuntu 5.04. However, I also have the same problem with MOL in full screen mode...

Any ideas anyone?

Simon

---

### Post by linutic on 2005-05-24
I'll check how MOL functions on my box in full-screen tonight, but I don't expect there to be a great deal of difference between our systems if yours displays the same symptoms.

This page mentions using atyfb on a Beige G3 (Server), which has the same video card as our model, to change the console mode; I wonder if that might at least eliminate *my* immediate problem:
[http://web.ics.purdue.edu/~jrruble/coolstuff/007/g3server.htm]("http://web.ics.purdue.edu/%7Ejrruble/coolstuff/007/g3server.htm")

IANA developer, but I suspect it's down to the differences between how X and MOL/console addresses the display. If I say any more, tho, I'm going to come off like a complete idiot, so I'll just shut up here and save face ;)

---

### Post by Len on 2005-05-24
I get exactly the same on my 5500. You may want to compile a kernel yourself with another resolution, or put a vmode argument to the kernel in BootX or Yaboot. First option recommended because the latter will force these settings in X also.

---

### Post by sangling on 2005-05-24
I've tried the following:

```
video=atyfb:vmode:18,cmode:16
Bigger but more corruption

video=atyfb:vmode:16,cmode:16
Bigger slightly less corruption

video=atyfb:vmode:16,cmode:8
Bigger less corruption

video=atyfb: vmode:16, cmode:8
Smaller with corruption! Spaces not helping!

video=atyfb:vmode:16,cmode:1
Bigger with still corrupt
 
video=atyfb:vmode:15,cmode:8
Still corrupt
 
video=atyfb:vmode:14,cmode:8
Same...

video=atyfb:vmode:13,cmode:8
Still!

video=atyfb:mode:1024x768
Small and slightly less distortion

video=atyfb:mode:600x600-16@75
Same
```
No luck so far but I think this might be relevant... [http://ozlabs.org/ppc32-patches/patch.pl?id=368](http://ozlabs.org/ppc32-patches/patch.pl?id=368)

---

### Post by Len on 2005-05-24
Funny thing is that I didn't get it with Mandrake 10 PPC. A kernel recompile with 640x480 as resolution worked for me if I remember correctly.

The G3 uses the ATI Rage II chip as well? If so, this is an ATI rage support bug for the onboard chips.

---

### Post by sangling on 2005-05-25
[QUOTE=sangling]No luck so far but I think this might be relevant... [http://ozlabs.org/ppc32-patches/patch.pl?id=368](http://ozlabs.org/ppc32-patches/patch.pl?id=368)[/QUOTE] I've contacted Mikael but he hasn't found a solution yet. Keep looking...

---

### Post by sangling on 2005-05-25
Still not much further. I've seen reference to adding mclk. For example:
video=atyfb,vmode:14,cmode:8,mclk:63 

Where mclk is the clock speed of the chip on the graphics card. I believe this value should be 63 for a beige G3 tower.

However this doesn't appear to help!

---

### Post by linutic on 2005-05-31
In the interests of stating the blatantly obvious, I've confirmed that this *is* a 2.6 issue by building a 2.4 kernel on my Beige, which booted with no console corruption at any atyfb mode (but, on an unrelated note, a completely unusable keymap). Unfortuntely I have to let this rest for a week as I'm running off for the south of France. Has anyone had any luck digging up the Mach64 maintainer?

---

### Post by snooo on 2005-08-12
Hi ppl..

Just a bump really. Did anyone ever solve this issue pertaining to Beige G3 macs? If it is just related to the frame buffer, is there anyway to disable it? I need to use the console and it is quite annoying otherwise...

---

