---
title: "Firefox loading pages slowly"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-03-01
Ubuntu 6.10 - Firefox is running wicked slow.  It takes half a minute to get to a page.  In the bottom left of the window it will say "Looking up www.whateverdomain.com" for 20 to 30 seconds before loading up the page.  Is this normal?

---

### Post by Quillz on 2007-03-01
It doesn't sound normal to me, but it also doesn't necessarily sound like a Firefox issue. The problem could be on your end. Is there a lot of traffic on your network right now? But it could also be a problem on the server end.

Finally, consider the Fasterfox extension or Swiftfox.

---

### Post by Thrasonic on 2007-03-01
I don't have this problem when I'm running XP and IE, just when I'm running Ubuntu and Firefox.  I've never used Firefox before, either, so I don't know what's normal with this browser.

---

### Post by philip360 on 2007-03-01
Hi Thrasonic, I had same problem. I can't find original post for solution, but from my notes:

Open firefix and in address bar type in:

about:config

press enter and a screen comes up  of config settings. Double click these ones to set to TRUE

network.dns.disable IPv6
network.http.pipelining
network.http.proxy pipelining
network. http.pipelining.max requests        ****set this one to 8 or 10******
plugin.expose_full_path

I have done several fresh installs and have done this every time and it worked
Philip

---

### Post by Thrasonic on 2007-03-01
Whoa yeah!  That did the trick.  Thanks a ton!  Sweet.

Hey, while I have your attention I have another question.  I've noticed that when I use my middle mouse button to scroll down a page or even when I click and drag the scroll bar up and down it's horribly slow.  How is that fixed?

---

### Post by igknighted on 2007-03-01
> **Thrasonic said:**
> Whoa yeah!  That did the trick.  Thanks a ton!  Sweet.

Hey, while I have your attention I have another question.  I've noticed that when I use my middle mouse button to scroll down a page or even when I click and drag the scroll bar up and down it's horribly slow.  How is that fixed?

Sounds like graphics driver issues.  What type of graphics card do you have?  And have you attempted to install the proper drivers yet?

---

### Post by Thrasonic on 2007-03-01
I have an ATI Radeon x1600 Pro, and no, I haven't tried installing any other drivers for it.  I don't know how.  With Windows, no problem.  With Linux, I don't even know where to begin.  I don't even know how to look and see what driver Linux is using right now...

---

### Post by igknighted on 2007-03-01
> **Thrasonic said:**
> I have an ATI Radeon x1600 Pro, and no, I haven't tried installing any other drivers for it.  I don't know how.  With Windows, no problem.  With Linux, I don't even know where to begin.  I don't even know how to look and see what driver Linux is using right now...

Ok, with this card the default drivers (an open-source attempt to reverse engineer the ati cards) are no good... the card is too new.  Open a terminal and type the following commands:
```
sudo aptitude update
sudo aptitude install xorg-driver-fglrx
sudo aticonfig --initial
```
Then reboot your system (an X restart might do the trick, but I'd reboot to be safe) and type "fglrxinfo" in a terminal.  Post the results here, but as long as there's no reference to "mesa" you should be OK.

---

### Post by Thrasonic on 2007-03-01
Thanks.  Things looked to be going great and than I ran the third command you outlined - sudo aticonfig -initial - and I got this:

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

What to do?

---

### Post by igknighted on 2007-03-01
Type this command in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
Then find a section that starts with Section "Device".  Under that there should be a line Driver "ati".  Change "ati" to "fglrx", then save and close the file.  Thats pretty much what aticonfig would have done.  From here you can reboot.

---

### Post by Thrasonic on 2007-03-01
Interestingly enough that file is completely blank...

---

### Post by igknighted on 2007-03-01
did you change my capitalization at all?  if you used x11 instead of X11 it would be blank, because those are different.  If you did do it right, something very serious is wrong.  You need to run sudo dpkg-reconfigure xserver-xorg and answer its questions as best you can (choose fglrx when it asks you for driver) and then go ahead and try a restart once its done.

---

### Post by Thrasonic on 2007-03-01
Okay, I changed the case of X to x.  I didn't even notice that.  Sorry.  I went in and found what you were referring to, but instead of driver being ati it was vesa.  I've changed it, will reboot, and am going to bed.  I'll pick this up again tomorrow if it doesn't work.  Thanks for your help.

---

### Post by Thrasonic on 2007-03-01
Bingo, that did it.  You guys are geniuses, I swear!  Thanks a ton.

---

### Post by igknighted on 2007-03-01
Glad to hear that... For what it's worth, I found out why the aticonfig command didn't work.  The --initial flag needs 2 '-'s, as in linux one '-' means a single letter (or a series of letters, read individually not as a word), while '--' means read until the next space as one word.  So you used 'aticonfig -initial' but you needed 'aticonfig --initial'.

---

### Post by mconway0003 on 2007-03-01
> **Thrasonic said:**
> I don't have this problem when I'm running XP and IE, just when I'm running Ubuntu and Firefox.  I've never used Firefox before, either, so I don't know what's normal with this browser.

It sounds to me like you prefer this "XP" from microgates, over Ubuntu and the whole open source community!

Gentlemen!?

---

### Post by igknighted on 2007-03-01
> **mconway0003 said:**
> It sounds to me like you prefer this "XP" from microgates, over Ubuntu and the whole open source community!

Gentlemen!?

Chill man, he was pointing out that the issue was with Ubuntu and/or firefox, as other browsers/OS's didn't have this issue.  It was valuable info at the time.

---

### Post by mconway0003 on 2007-03-01
> **philip360 said:**
> Hi Thrasonic, I had same problem. I can't find original post for solution, but from my notes:

Open firefix and in address bar type in:

about:config

press enter and a screen comes up  of config settings. Double click these ones to set to TRUE

network.dns.disable IPv6
network.http.pipelining
network.http.proxy pipelining
network. http.pipelining.max requests        ****set this one to 8 or 10******
plugin.expose_full_path

I have done several fresh installs and have done this every time and it worked
Philip

Hey man, that helped me a lot thanks. But what exactly do all of those changes do?

---

### Post by philip360 on 2007-03-02
Since I posted it I'll reply...
I don't remember what the particular explanation was. As I mentioned I could not find the original post and I just kept notes of the changes. I think I originally searched forum for "slow firefox"

---

### Post by mcduck on 2007-03-02
> **mconway0003 said:**
> Hey man, that helped me a lot thanks. But what exactly do all of those changes do?

The first one disables IPv6 protocol, some networks and routers don't support it yet. This was probably the one that solved the problem.

Others tell Firefox to open more connections when opening a web page so that FF can load many things at the same time.

I'm not sure about the last one, never seen that one before.

---

