---
title: "cannot execute binary file"
date: 2006-08-25
forum: Apple PPC Users
---

### Post by naomi on 2006-08-25
Hi,

I'm having Ubuntu 5.10 installed on my desktop machine and it works  fantastic. Furthermore I have an ibook G4 and I think of installing Ubuntu on it, because Mac OS X has it's limitations. However, before getting rid of Mac OS X I tried the Ubuntu Live CD. Apart from some firmware error messages during the boot process it looked fine. I then tried to execute a binary (which I put on my USB stick) and I get the error messages: "cannot execute binary file". The binary worked fine on Ubuntu 5.10. So here comes my question: doesn't it work, because of some incompatibility (PPC processor architecture?) or just because it is the live CD?
I really need this little program to run on my machine and unfortunately I only have the binary but not the source code.

Naomi

---

### Post by kadymae on 2006-08-25
Is your desktop also an Apple machine with a PPC processor?

---

### Post by APU on 2006-08-25
Well you did not tell us which architecture your desktop machine is. If it is a x86 (Intel or AMD basically) the identical binary will not run on a PPC as you were already guessing.

The only way you have to run a x86 binary on a PPC Computer is through Emulation (QEMU would be a way). But this is very slow of course. It could do if its only a little programm but if you want to use it a lot...

What does it do? Maybe there is an alternative software available where you can even get the source code?

APU

---

### Post by naomi on 2006-08-25
Thanks for your replies! Sorry, forgot to mention the desktop's architecture, which is x86. Haven't heard of QEMO yet, but I will give it a try. The program is a very simple molecular viewer for xyz files developed by our sysadmin (ages ago). I'm working in condensed matter physics research, i.e. I look at crystal structures, but not at fancy proteins, etc. Apart from rasmol most viewers nowadays focus on bio stuff and are not really suitable...

---

### Post by APU on 2006-08-26
The emulator is called QEMU, not QEMO. I also remembered another one which is called Bochs.

You can give both a try but the downside is that you will have to emulate a complete x86 System to be able to run the x86 binary. You will really have to try it to find out if this works for you.

APU

---

### Post by naomi on 2006-08-26
Yeah, sorry about the typo. I wrote the reply in the middle of the night (I live in the UK). I tried QEMU today. It wasn't too success though. I just ran the DSL live CD because I somehow couldn't install it on the hard disk (i.e. Q's image file).
Surprisingly my network connection (Airport wireless on ibook G4, yep, the one which makes all the trouble) worked out of the box. However I didn't know how to mount my usb-stick to load any files. I then did an scp to get the binary of the tiny program. I could download it, but unfortunately I get an error when executing it - some library object file isn't found... Well, I think I will give up soon... :-(

Naomi

---

### Post by xurios on 2006-08-26
Rasmol has a mac os port (classic), and also a fink port (uses X windows under OS X, make sure you start it from an xterm under some form of X11 and not Apple's terminal.app). If you don't know about fink, you should [check it out](http://fink.sourceforge.net/). Also, if you use fink, [fink commander](http://finkcommander.sourceforge.net/) is a nice front end for it. I can't seem to load a file with the stupid macos classic version of rasmol. Maybe because the path separators are different? Also, in the classic version, the graphical file browser in rasmol doesn't recognize any of the valid file types and has no 'show all' option. Bunk. Stick with the fink port if you want rasmol on your mac.

---

### Post by naomi on 2006-08-27
Yes, thanks, I know. I have both fink and darwinports installed on my ibook. But rasmol isn't simplistic enough. I need a very simple balls and sticks viewer which allows me _easily_ to zoom in/out, get (multi) atom information on bondlengths, angles, random distances, delete atom(s), layers, etc. and change atom types. I already thought a couple of time of programming it myself platform independently using Java, but unfortunately my Java programming skills are almost non existent...
Anyway, thanks for your help. I guess it's a matter of fact, that I just can't doo everthing on my ibook...

Naomi

---

### Post by naomi on 2006-08-30
ok, well, the actual problem hasn't been solved, but if anyone using a mac is looking for a platform independent molecular viewer, then try Jmol! this is an awesome programme written in Java, and it works on both, my Ubuntu machine and my ibook.

naomi

---

### Post by blue_chili on 2006-09-15
Ignore this !

---

