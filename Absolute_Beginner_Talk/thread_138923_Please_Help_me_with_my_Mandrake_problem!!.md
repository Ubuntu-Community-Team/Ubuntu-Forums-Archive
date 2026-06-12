---
title: "Please Help me with my Mandrake problem!!"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by dearanna on 2006-03-02
Hey everyone,

I have Mandrake Linux on my 2nd desktop computer, and Ubuntu on my main computer. Well, I have a problem with my Mandrake system that I was hoping people could help me with.

Okay, well I accidently knocked my power cord in Mandrake and turned off my computer. When I went to reboot it, instead of going into the GUI, it went into the kernal. I can't even figure out how to run the GUI from the kernal.

As of now, I think I have two options:
1.) Figure out how to start GUI from within Kernal
2.) Erase drive and start fresh!!

Please help, as I wish for option 2 to be a last resort. Please help me!!!!:cry:

---

### Post by xhie on 2006-03-02
"kernal" == "terminal" ?

if so, I have no idea how to start anything in mandrake but on an ubuntu box its 

sudo /etc/init.d/gdm start

or startx



Yeah thats probably no help, so I dunno.

---

### Post by dickohead on 2006-03-02
[http://mandrakeusers.org](http://mandrakeusers.org) / [http://mandrivausers.org](http://mandrivausers.org)

But it sounds like you may have fried some of the data on the hard drive and it needs you to fsck it all better? I did that last night, my usplash screen wasn't working so I kept rebooting, only to realise that 2.6.14 doesn't support vga=771... silly me!

You will more than likely be in recovery mode, you will need to tell us what messages you receive before the command line comes up ready for input - also are you using resiserfs or ext3?

---

### Post by dearanna on 2006-03-03
Okay, I'm using Ext3 format for my Mandrake, yes!!

Before the screen comes up, the only warning message I get is this:

"Linux Module has been moved to Ax03"

Then it says that the system was shut down uncleanly and you can press F to force a system check. I tried doing this, but it never works.

Whe I get to the Kernal (Terminal) it asks for Local host login and password.

I tried loging in using my main account, I also tried loging in using my Root. I got in, but I'm no expert on the Kernal. BTW, if anyone knows of any tutorials on how to use the Terminal and all of it's commands, that would be useful!!

Thanks!!

---

### Post by Swab on 2006-03-03
[QUOTE=dearanna] BTW, if anyone knows of any tutorials on how to use the Terminal and all of it's commands, that would be useful!!
Thanks!![/QUOTE]

[This tutorial ]("http://www.linux.org/lessons/beginner/toc.html")helped me out a lot.. it's a bit dated but still does a great job getting you up to speed with using the terminal.

---

### Post by AndyCooll on 2006-03-03
I'm assuming that it drops you into the command line when booting up instead of getting a gui.

In which case it is likely that you will need to log on as yourself, then change to root (ie. type su followed by the root password that you initially set on installation).
Then type:
```
fsck
```

It'll do a file system check and offer to repair. Accept these offers. When it's finished type:
```
startx
```

Hopefully that'll bring the gui back up.

---

### Post by dearanna on 2006-03-03
I'll try that when I get home, thanks a lot!!!

---

