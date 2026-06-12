---
title: "Display problem..."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by AndrewS on 2007-09-08
I have 7.04 installed on a PC which had a wide screen display, and have been unable to use the 1440x900 resolution which the monitor is capable of (and which Windows XP can use).  I edited some of the configuration files for the display in 7.04, and succeeded in losing the display completely...  I'm pretty sure the system still boots OK, because I can switch to a text console (ctrl + alt + F1).

Any suggestions as to how to fix this, preferably without a re-install?  I'll be happy with pretty well any resolution (although 1440x900 would be nice).

Thanks in advance

Andrew

---

### Post by kvonb on 2007-09-08
From the console (ctrl + alt + F1), type this lot (case sensitive):

```
lspci | grep Display

```
...note the adapter type for the next part.

```
sudo dpkg-reconfigure -phigh xserver-xorg

```
It will run you through a setup thing, select your video adapter from the list, and it should also give you a list of screen resolutions, select the ones you want.

Restart the computer when done :)

---

### Post by alienexplorers on 2007-09-08
If after getting the system running again you still can not access the 1440x900 resolution you might want to try adding a modeline with the information (resolution & refresh) you want to run.  The modeline should be added into the "MONITOR" section of the xorg.conf file.  I have a listing for a modeline generator in my signature line.

---

### Post by AndrewS on 2007-09-08
Hi kvonb

I assume I can run these commands from a text console (I have no video display...)?

Thanks

Andrew

---

### Post by alienexplorers on 2007-09-08
Yes, The commands can be run out of test mode.

---

### Post by AndrewS on 2007-09-08
Hello again

I just tried the suggestions made, with the following results:

Typing [COLOR="Red"][COLOR="Black"]lspci | grep Display [/COLOR][/COLOR]didn't give me any result.  Just typing lspci gave me a long list, but I can't remember how to show this by the page (!).  Anyway, I found out that the PC has an Intel 82945G chipset.

Typing sudo dpkg-reconfigure -phigh xserver-xorg just gave me a warning that a conf file was going to be overwritten, then i was returned to the prompt.  If I left out the -phigh, I was taken through a series of questions.  I took a guess at the answers, and ended up with a black screen, with an Out of Range message.

Any other suggestions?

Thanks again

Andrew

---

