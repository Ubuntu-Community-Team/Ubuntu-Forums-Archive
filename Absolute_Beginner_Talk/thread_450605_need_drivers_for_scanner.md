---
title: "need drivers for scanner"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-05-21
picked up a scanner(canon canoscan parallel fb330p) but cant find drivers for it, any idea where i can??

---

### Post by Kobalt on 2007-05-21
When you plug it in and launch Apps. > Images > XSane, what happens ?

---

### Post by scrooge_74 on 2007-05-21
> **99bluefoxx said:**
> picked up a scanner(canon canoscan parallel 300dpi) but cant find drivers for it, any idea where i can??

Look for your scanner here, but as far as I know Canon scanners have poor support under windows, and if it is a parallel port type is going to be even harder

[http://www.sane-project.org/](http://www.sane-project.org/)

---

### Post by 99bluefoxx on 2007-05-21
it tells me that theres no device ready

---

### Post by 99bluefoxx on 2007-05-21
ok found it there but how do i use that?
the link i clicked for my scanner took me to this page[ http://www.sane-project.org/man/sane-canon.5.html]("http://www.sane-project.org/man/sane-canon.5.html")
what do i do with that?

Edit: i figured it out
XP

---

### Post by 99bluefoxx on 2007-05-21
ok i got the stuff but now i need to install somthing called "libieee1284-0.2.10.tar.bz2"
i didnt find any step by step for it though, help please?

---

### Post by cotcot on 2007-05-21
Install with synaptic ('sudo synaptic' will give you a list; if you have the same repositories as I have you will find it in the list).

---

### Post by az_s_za on 2007-07-12
I have problems with the same printer and have been down the same road as you, blue fox, but am a little further along, so here is some advice, before I ask for some more help myself:

Before you try installing the new libieee and driver, try this:
1.  Ist you need your system to detect the printer.  So open a terminal and type:
> cd /etc/sane.d, then
> gksudo gedit dll.conf
now go down and comment (add a '#') everything except 'net' and 'canon_pp'. (you will need to un-comment 'canon_pp')
Save and exit.

2.  Parallel port printers need to be run as root.  So first try running xsane as root:
> gksudo xsane

How does that work for you?

By the way, you can change your system to allow any user to run your PP printer... see  [_this post_]("http://ubuntuforums.org/showthread.php?t=91879&highlight=CanoScan+N640P") for more info.

Now FYI, and hopefully someone else can hlep me/us further, I have done the above, and my printer is finally detected by sane, however, when I try to do anything (calibrate or preview), it starts OK (i.e. the scanner starts moving), but xsane and the scanner freeze after a few seconds.

So, now I wanted to try and install the packages from the sane-project as you described earlier.
Now, for the benefit of cotcot, these packages are NOT available in synaptic.  Also, the sane-project says this printer should work well with these drivers.  Links to their downloads can be found [_here_]("http://canon-fb330p.sourceforge.net/")
Now, I am a real newbie at compiling stuff, and this is where I come unstuck.  I get an "Error 1" when I try to "make" the libieee1294 package.  The terminal output from the "make" command is attached.  **If anyone can help me compiling this, I'd be VERY appreciative!**

I feel that if bluefox can get his scanner going with the instructions I have posted, then mine must be a problem with my (now very old) scanner.  However, if he has the same problem I do, then we will need to get these new drivers installed.

---

### Post by 99bluefoxx on 2007-07-15
well i'de of loved to try that out but now my computer went and killed itself(power supply too weak, destroyed hdd, then second mb) i cant do much, the only reason i can reply to this is cause im on vacation in kitimaat visiting relatives and borrowing a computer from them, which is running win xp, and they asked me to try to get rid of the viruses on it and i checked my email on the side^^;
oh well, couple more months and i can buy parts for a new one im gonna build, from scratch...

---

### Post by Rohen on 2007-07-17
I have a CanonScan Lide 25.  The comp detects it, but when I scan anything it just shows me a black image? :confused:

I'm guessing there's something wrong with the scanner.  I mean if it's read, then the problem lie in the Scanner, am I right? :(

Thanks. :o

---

### Post by qazphilby on 2007-11-26
Hi all,

This thread has been extremly uawfull however i m still having some troubles install my scanner (CanoScan N640P).  I have followed the instruction on how to installt he driver and all seems to be working well until i do a ../scan -C i get the following > 
Finding IEEE1284 ports...
    parport0 (0x378): <raw><cpt><nbl><byt><ecp><swe><irq><dma>... OK (ecp).

Detecting scanner:
 ID:    "CANON   IX-06115G       1.00"
 Model: N640P   (600x600dpi,  5104x7016 pixels)
Calibrating 5104x6 pixels calibration image (38280 bytes each scan).
Step 1/3: Calibrating black level...
  * Black scan number 1/3.


I have also tried running zsane from root terminal and it just hung.

any suggestions would be fantastic.

thanks

---

### Post by 99bluefoxx on 2007-11-26
i gave up on my scanner ages ago, infact, i tore it apart and the glass bed is going to become the window in the side of my computer
moral: almost no electronics from value village work>buy it from the flea market[i got a gig of ram for 5$!]
good luck though

---

### Post by qazphilby on 2007-11-26
Thanks 99bluefoxx

I have actually progressed a bit further.  now when i run xsane from the graphice menu, it actually detects the scanner fine, however if i try to scan it get stuck about 1/5 of the way and doesnt respond.

If i click callibrate it hangs. 

And if i run ./scan -C from the terminal it still hangs

---

