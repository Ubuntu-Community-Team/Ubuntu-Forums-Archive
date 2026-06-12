---
title: "PLease help me to get my Geforce2 MX working!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by nachomania on 2008-03-20
I've just finished 9th re-installation of Ubuntu. As you may have guessed from the title, the reason for all this is my graphics chip/card/thing. So far, I've gathered that I need to install the NVIDIA Legacy driver (I, at this point, don't care i it's open), yet find this also impossible. I"ve killed my system at least twice using the driver reccomended by Ubuntu (7.04 and 7.10), and am told by NVIDIA's Legacy driver installer  that I can't run it with an X server (though, after shutting it down, X messes up, so I can't do anything at all, and can't even get to a command line). Basically, on the verge of depression, I ask if anyone could help me get support for my Geforce2 MX. I can do some basic stuff in the terminal, if it can help. I've tried other threads, which resulted in more crashes. I'm willing to crash my current system again (it's blank) to get info if needed. Please help!

*OpenSuse doesn't work; repository is missing tons of stuff.

---

### Post by |{urse on 2008-03-20
wow i just pasted this a half hour ago to someone else. ^^ go figure
Try ENVY. It detects and configures all that for you (usually)
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

BTW if all you currently have is command line

sudo nano /etc/X11/xorg.conf

search for a line that reads

Driver          "nvidia"

change it to 

Driver          "nv"

tht might help get u back to a gui.

---

### Post by nachomania on 2008-03-20
Well, it caused No-X #1 and #3, but I'll try it. Next post will be from what works

---

### Post by |{urse on 2008-03-20
> **nachomania said:**
> Well, it caused No-X #1 and #3, but I'll try it. Next post will be from what works

do you mean it caused no X (as in xorg?) #1 and #3  = ? :confused:

---

### Post by nachomania on 2008-03-20
Yes, they both resulted in no X (I couldn't use startx, wouldn't do anything). Also, the reason was I couldn't enter startx, as I got no command line.

-Update-

I've used envy to install the Legacy driver. It works just until after the Ubuntu loading bar fills. Btw, I'm running 7.04. Now, I get stuck on an NVIDIA screen, mouse frozen, and keyboard doesn't seem to work.

---

### Post by nachomania on 2008-03-20
Oh, to clarify, no Xorg. In Opensuse, it said Xorg was broken, which also gave me the same stuff.

---

