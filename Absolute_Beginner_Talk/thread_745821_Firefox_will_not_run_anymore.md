---
title: "Firefox will not run anymore"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by xenocution on 2008-04-04
I've been running 7.10 on my desktop for about a week now, when out of the blue Firefox 2.0.0.13 decides not to run anymore. Epiphany will not run either, but Opera works fine.

Running Firefox in terminal gives me:
> Floating point exception (core dumped)

Any help fixing this would be very appreciated.   :)

---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
Tried reinstalling? 

```
 sudo apt-get reinstall firefox 
```

---

### Post by xenocution on 2008-04-04
I've uninstalled with Synaptic and reinstalled that way. But no change.

The comand:
> sudo apt-get reinstall firefox
doesn't seem to work. I only get:
> Invalid operation reinstall

---

### Post by JoshuaRL on 2008-04-04
Okay, try this:
```

sudo apt-get remove firefox
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox

```

---

### Post by xenocution on 2008-04-04
JoshuaRL:

Just ran the four commands you suggested and then rebooted. Unfortunately, Firefox still won't run.
I get the "starting Firefox Web Browser" tab at the bottom of my desktop, but it just stops.

---

### Post by HereInOz on 2008-04-04
This is a bit of a long shot, but uninstall firefox like you did above, and then go into your home directory and delete the .mozilla directory.  It is a hidden directory, so you will need to Ctrl-H in Nautilus to show it.

Once you have uninstalled, and then removed that directory, try a re-install after that, and you may have some luck.

---

### Post by Crafty Kisses on 2008-04-04
> **xenocution said:**
> I've been running 7.10 on my desktop for about a week now, when out of the blue Firefox 2.0.0.13 decides not to run anymore. Epiphany will not run either, but Opera works fine.

Running Firefox in terminal gives me:


Any help fixing this would be very appreciated.   :)

Can you we also get some system specs?

---

### Post by joshrobinson on 2008-04-04
> **HereInOz said:**
> This is a bit of a long shot, but uninstall firefox like you did above, and then go into your home directory and delete the .mozilla directory.  It is a hidden directory, so you will need to Ctrl-H in Nautilus to show it.

Once you have uninstalled, and then removed that directory, try a re-install after that, and you may have some luck.

that outa do it, theres a file in there called prefs.jfs or prefs.js
thats the file that usually mucks things up

---

### Post by xenocution on 2008-04-05
ok, just did: sudo apt-get remove firefox, deleted the the .mozilla directory, and reinstalled.
but no go :(

my system specs are:
> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1097.957
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips        : 2198.72
clflush size    : 32

and
> MemTotal: 645492 kB

---

### Post by joshrobinson on 2008-04-05
you must have a plugin problem or something (add on, extension, plugin etc)
try

```
firefox -safe-mode
```
this should disable your plugins


then boot firefox normally and see what happens

---

### Post by xenocution on 2008-04-05
ran:
> firefox -safe-mode

and got:
> Floating point exception (core dumped)

is there a way delete everything Firefox? complete removal in Synaptic didn't seem that complete. 

btw, thanks for all the comments so far!  :guitar:

---

### Post by xenocution on 2008-04-05
YEA! firefox lives again! :guitar::guitar::guitar::lolflag:

did some searching on google and remembered I'd installed some fonts just before the problem started.

I deleted the fonts and then ran:

> sudo fc-cache -fv

which I found in another thread.

Firefox will start now, but now to find out which font was the problem. :confused:

Thanks again for everyone's help. The folks on this forum are so patient and helpfull with all the new people, it's kept me from running back to the Windows devil I know.:)

---

### Post by linuxbeatswin on 2008-04-05
> **xenocution said:**
> 

Thanks again for everyone's help. The folks on this forum are so patient and helpfull with all the new people, it's kept me from running back to the Windows devil I know.:)

Thanks to you for posting this thread, bud. I followed the whole darn thing and fixed the firefox problem on my wife's computer. Glad that I could benefit from the help that someone else was getting.

And, thanks again to all those who help us Ubuntu "noobs".

---

### Post by ToySouljah on 2008-04-14
> **xenocution said:**
> YEA! firefox lives again! :guitar::guitar::guitar::lolflag:

did some searching on google and remembered I'd installed some fonts just before the problem started.

I deleted the fonts and then ran:



which I found in another thread.

Firefox will start now, but now to find out which font was the problem. :confused:

Thanks again for everyone's help. The folks on this forum are so patient and helpfull with all the new people, it's kept me from running back to the Windows devil I know.:)

Oh great...lol...I have a feeling I'm having the same prob as you with the fonts messing up my firefox (had to load Vista to get back on here).  I was installing some fonts last night and then FF stopped working and I am getting the exact same error.  I use a lot of different fonts for photos, lightscribe labels, etc. and thought they would be ok.  I did however notice that I think it was .afm (I think they were Adobe Fonts) that every time I'd select them they would just disappear and I'm not sure where they went.  There were some other files in the type1 folder with the same extension so I figured I'd throw them in that folder.  Going to try to see if I can get it running now  :)

---

### Post by ToySouljah on 2008-04-14
Yup, that was the problem...I'm now posting back in Ubuntu...whew...lol.  I get nervous going online in Vista since I don't really have anything installed on it as far as AV software since I use Ubuntu about 99.9% of the time and boot into Windows for exporting my Handicam files since I have yet to find a program to make it as easy as it is in Windows (yeah even Vista...lol)

---

