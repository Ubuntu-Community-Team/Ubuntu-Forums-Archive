---
title: "Odd ubuntu 7.1 install problem"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by ReillyRoo on 2008-01-24
hello,

first off here is my machine:
amd athalon 64 x2 2.8ghz
2x nvidia 8600 gt graphic cards
2gb ram
160gb hard drive


i have a tried to install ubuntu 7.1 on my machine. once i get to the black screen were it has a list of functions on the left and says "ok" on the right, my screen goes blank and it stays that way for ever.

so i formated my hard drive and tried again... same problem.

so i thought it was the disk, so i tried it on my laptop... it worked perfectly on my laptop, no problem at all.

so i downloaded the 64bit edition and tried that... same problem.  so its got to be my hardware, because i wiped my hard drive clean.  what is the solution?  what part of my hard ware is causing this problem?


thank you in advance.

---

### Post by ReillyRoo on 2008-01-24
i find it hard to believe that NO ONE has come across this before. :confused:

---

### Post by jken146 on 2008-01-24
Please don't shout, and please have some patience.  We are all volunteers here.  If you're impatient for an answer you'd be well advised to search the forums and the rest of the Web.

> i have a tried to install ubuntu 7.1 on my machine. once i get to the black screen were it has a list of functions on the left and says "ok" on the right, my screen goes blank and it stays that way for ever.

Are you referring to the screen with the boot options for the live CD?  If so, this is most likely a graphics card issue --  try the safe graphics option.  Failing that try the alternate CD.

---

### Post by Paul820 on 2008-01-24
> **ReillyRoo said:**
> i find it hard to believe that NO ONE has come across this before. :confused:

It could be a graphics card issue, have you tried the alternate install disk? It uses a text based installer instead of the graphical one. Once you get the system installed with the alternate disk then you can sort out the graphics issue.

EDIT: Link [http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")

---

### Post by ReillyRoo on 2008-01-24
so i tried the safe graphics mode, and i got sound (the ubuntu start up sound) but just a black screen, which means ubuntu is working but i cant see it.:confused:

---

### Post by ReillyRoo on 2008-01-24
> **Paul820 said:**
> It could be a graphics card issue, have you tried the alternate install disk? It uses a text based installer instead of the graphical one. Once you get the system installed with the alternate disk then you can sort out the graphics issue.

EDIT: Link [http://releases.ubuntu.com/7.10/]("http://releases.ubuntu.com/7.10/")

thanks, im going to give this alternate cd a try. will update soon.

---

### Post by ReillyRoo on 2008-01-24
i used the alternate install cd... it took about an hour and finaly i got it all installed.
i pulled the cd out,
the computer rebooted... and i STILL have the same problem. i cant see anything it just goes to the black screen. 

how can i get my video card drivers on my computer if i can only see a black screen?:mad:

---

### Post by omegabane on 2008-01-25
ReillyRoo - I've had the same problem. Ubuntu boots and I even get the login screen sound, but the screen is completely black. I ran the reconfiguration tool that many have suggested around the forums, but no luck.

That said, I did find a solution that worked for me. When I get to the login screen (even though I can't see it) I hit CTRL+ALT+F1. This drops me to the command line where it presents me with a login prompt. I don't login, but rather immediately hit CTRL+ALT+F7 which returns me to the GUI login screen, which, for whatever reason, I can now see.

Granted, this is a work around and doesn't actually solve whatever is causing the problem to begin with, but at least this will let you see what's going on to make any changes you might need to make.

Hopefully this will work for you.

---

