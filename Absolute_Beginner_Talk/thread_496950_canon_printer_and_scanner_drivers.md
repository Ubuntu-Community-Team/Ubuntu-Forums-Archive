---
title: "canon printer and scanner drivers"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-07-09
I'm running the latest version of ubuntu but I'm having problems finding and installing correct software for my canon pixma ip1500 and 1220 nu scanner. I have automatrix and have installed nvidea drivers and adobe without problems, but I'm stuck on the printer and scanner. TIA

---

### Post by Benbow on 2007-07-09
I would have recommended Turboprint **but** I downloaded it for my MP170 and found that whilst it prints generally ok, for photos it is absolutely hopeless. I now stick to xp for my photos and turboprint for documents. Also you have to pay for Turboprint!
I have struggled for weeks to find a canon substitute driver for Ubuntu without success, it is the only problem I have found with Ubuntu so far but sufficiently serious enough to make Linux a part tome system for me.

---

### Post by pdlethbridge on 2007-07-10
I got as far as this link, which was dead
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1500)

---

### Post by Seisen on 2007-07-10
For you canon iP1500 follow my guide here
[http://ubuntuforums.org/showthread.php?t=487890]("http://ubuntuforums.org/showthread.php?t=487890")

The scanner I will see what I can find.

---

### Post by Damanther on 2007-07-10
Have you tried any of the other pixma ip* drivers?

I had a bunch of issues trying to get my Canon S350 to work. On a whim I tried some of the other S-series drivers and it turns out the S600 worked like a champ for me.

Might be worth a shot.
Edit:
Try Seison's Howto above first.

Damanther

---

### Post by paradoc on 2007-07-10
search the forum for N1220U scanner, you'll see how to use scanbuttond here!

---

### Post by pdlethbridge on 2007-07-10
After I tried your suggestion, I got this result.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libcnbj-2.5
pdleth@pdleth-desktop:~$

---

### Post by pdlethbridge on 2007-07-10
the scanner works with xsane but still nothing for the printer

---

### Post by pdlethbridge on 2007-07-10
when I tried siesons method, the first two inputs worked but not the third, apparently there were some restricted repositories that prevented it from completing. I tried his method again this morning and I just finished the test page. 
Now the scanner and printer are working. Thanks everybody for the help.

---

### Post by pdlethbridge on 2007-07-30
the addition of automatix solved the scanner problem.

---

### Post by pdlethbridge on 2007-09-07
I've continued to have issues with the USB canon n1220u scanner. Tonight I finally got it to work by researching the bug reports ( #85488 ) Here is what I found. Give these guys the credit.

fraz  wrote on 2007-04-30:  (permalink)
Hello People,
I checked out the scan button daemon from feisty and IT WORKED.
It is really funny. The daemon could be started from the user.
Now I am able to remove the edgy kernel from my machine..

fishor wrote on 2007-04-30: (permalink)
It's a good workaround ;)
it still need be fixed in the kernel. scan button daemon don't allow suspend the device.

dompie wrote on 2007-04-30: (permalink)
It is a very big shame altogether and probably the first step to another distribution.
 
Corsaire wrote on 2007-04-30: (permalink)
to fraz
please can you tell exactly what is this "scan button daemon", I don't understand what this is about

fishor wrote on 2007-04-30: (permalink)
sudo aptitude install scanbuttond

fraz wrote on 2007-04-30: (permalink)
Some more explaination about scan button daemon:

install the software
_sudo aptitude install scanbuttond_

now start the daemon as normal user
_scanbuttond._

after this my epson scanner with snapscan backend is working fine.

But what is going on?
the daemon allways watches for the scanner and the usb did not suspend.

the real function of this software is to look for the buttons on the scanner and do something usefull lke
scanning -> printing - scanning -> email

regards
Franz
paradoc had the right answer but I totally missed it.

---

### Post by paradoc on 2007-09-07
Yes, it's [http://ubuntuforums.org/showthread.php?t=483837&highlight=n1220u](http://ubuntuforums.org/showthread.php?t=483837&highlight=n1220u)

with a few other neglected scanners thrown in too! :)

---

