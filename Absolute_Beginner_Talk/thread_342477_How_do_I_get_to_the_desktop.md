---
title: "How do I get to the desktop?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by jonny407 on 2007-01-20
I login and all I get is "~$" what is this for? how do I get to some sort of desktop or something that uses a mouse? Oh, by the way, anybody know why my threads don't show up in bold print?

---

### Post by meng on 2007-01-20
Which version did you install?

---

### Post by jonny407 on 2007-01-20
6.06

---

### Post by meng on 2007-01-20
I meant Desktop Live, Desktop Alternate, or Server. (Server doesn't come with GUI)
And when you boot up, are there any error messages.

---

### Post by jonny407 on 2007-01-20
> **meng said:**
> I meant Desktop Live, Desktop Alternate, or Server. (Server doesn't come with GUI)
And when you boot up, are there any error messages.

I see host "SMBus not enabled" that is the only error. I used desktop alternative because the PC did not have enough ram for the live version. When I installed Ubuntu I had to choose the "install in text mode" option because when I tried the OEM install it never asked me for a username and I was unable to get past the login screen.

---

### Post by meng on 2007-01-20
What happens if you log in and type
startx

---

### Post by jonny407 on 2007-01-20
i get "command not found".

---

### Post by meng on 2007-01-20
Are you certain you didn't install the server version by mistake?
Try:
sudo aptitude install ubuntu-desktop

---

### Post by jonny407 on 2007-01-20
It installed something. Now I'm at a postfix configuration screen with a bunch of options;

no configuration
internet site
internet site with smart host
satellite system
local only

---

### Post by meng on 2007-01-20
Choose No configuration.

---

### Post by zellis on 2007-01-20
> **jonny407 said:**
> I login and all I get is "~$" what is this for? 

It's the linux command prompt, aka the bash shell. If the GUI system isn't installed, or isn't properly configured, then you end up staring at a command-line like this.

Question: did the monitor screen go dark for a bit before prompting for a login (which would mean the GUI was trying to run but eventually gave up because it couldn't), or did it just go directly to a text-based prompt (which would mean that the GUI wasn't trying to run at all)?

---

### Post by meng on 2007-01-20
If the command
sudo aptitude install ubuntu-desktop
actually installed something, then it sounds as though you accidentally installed the GUI-less server edition in the first place.

---

### Post by jonny407 on 2007-01-20
I used no configuration and everything is working fine now. Thank you=D>

---

