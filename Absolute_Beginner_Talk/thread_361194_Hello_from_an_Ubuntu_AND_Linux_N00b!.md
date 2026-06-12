---
title: "Hello from an Ubuntu AND Linux N00b!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Valiante on 2007-02-14
I must say, having NEVER used Linux of any description, and having worked in IT Support for six years solely on Microsoft Windows, I feel quite child-like and excited now I've installed Ubuntu on my home PC.  It's just like the first time I used a PC!

My reason for taking the Linux route is that I want to run a web & email server from home.  A good pal of mine, a programmer who works on Linux all day long, suggested I try Ubuntu.

I must say, at first glace I like it.  There's a nice feel to the GUI, it's almost familiar (which I guess was deliberate to help us Windows-dwellers).  The first hurdle was getting my wireless card to work (a Broadcom 4318 ).  It took a few attempts but after following a couple of guides I found on this forum I managed to get it going.

I've since set up my email accounts and gaim - but where to go from here, I'm not sure.  I already have a few questions!  (e.g. Why can't I go above 1024x768 resolution?)

I'm sure I'll soon be on the other forums asking for various bits of help & advice!

So, anyway, "HELLO" from a true Ubuntu n00b!

):P

---

### Post by Spike-X on 2007-02-14
> **Valiante said:**
> I must say, having NEVER used Linux of any description, and having worked in IT Support for six years solely on Microsoft Windows, I feel quite child-like and excited now I've installed Ubuntu on my home PC.  It's just like the first time I used a PC!


Somebody on another board I go to says it's like sleeping with somebody else for the first time after getting out of a long-term relationship.

Anyway, hi! I'm also a n00b to the world of Linux. I've been using Ubuntu for 2-3 weeks now. the learning curve's been steep (still is), but it's so rewarding when you finally find a solution to a problem.

---

### Post by housam on 2007-02-14
Open your xserver-xorg 
```
sudo dpkg-reconfigure xserver-xorg
```
and press enter for every thing ( leave every thing as it is ) till you get the sitting page and select 1280x800  or what you like ( by pressing space ) and continue to go out.

---

### Post by tribaal on 2007-02-14
Nice to hear another successful conversion story! :)

I'm sure you'll find that it's possible to switch to whatever resolution you want, but you'll have to do a little hand tweaking for this (i.e. not using GUIs but going command-line).

I suggest you have a command-line look at the following file: /etc/X11/xorg.conf
In there you should find a list of possible resolutions. Just add the one you're trying to get to in there, and reboot your X server (the default shortcut is ctrl-alt-backspace).

Now your resolution should be available :)

You might want to backup xorg.conf (like with the following command: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup") before you make changes to it though, it's an important file, and if you mess it up your graphical environment will not waork anymore :(

With a backup you'll e able to revert the changes easily.

Hope this helps :)

- trib'

---

### Post by Valiante on 2007-02-14
Wow, that's great guys - what a fast response!  Glad I signed up!  I'll be trying those suggestions as soon as I get the chance.

---

### Post by megalania on 2007-02-14
That's what they're here for

---

### Post by tronica on 2007-02-14
I would suggest installing the correct driver for your video card

Nvidia:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")

Ati:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29")

---

### Post by Valiante on 2007-02-15
Hmm, now I've got some conflicting answers...  do I wanna edit this file or install drivers?

---

### Post by igknighted on 2007-02-15
> **Valiante said:**
> Hmm, now I've got some conflicting answers...  do I wanna edit this file or install drivers?

I'd install the drivers, your performance will be much better.

---

### Post by Valiante on 2007-02-15
Ok, will do.  Thanks!

---

### Post by Valiante on 2007-02-17
In the end I needed to do both to get the resolution I wanted but now I'm running at 1280x1024 - thanks guys!

---

### Post by IusedTObeSOMEONEelse on 2007-02-17
> **Valiante said:**
> I must say, having NEVER used Linux of any description, and having worked in IT Support for six years solely on Microsoft Windows, I feel quite child-like and excited now I've installed Ubuntu on my home PC.  It's just like the first time I used a PC!

My reason for taking the Linux route is that I want to run a web & email server from home.  A good pal of mine, a programmer who works on Linux all day long, suggested I try Ubuntu.

I must say, at first glace I like it.  There's a nice feel to the GUI, it's almost familiar (which I guess was deliberate to help us Windows-dwellers).  The first hurdle was getting my wireless card to work (a Broadcom 4318 ).  It took a few attempts but after following a couple of guides I found on this forum I managed to get it going.

I've since set up my email accounts and gaim - but where to go from here, I'm not sure.  I already have a few questions!  (e.g. Why can't I go above 1024x768 resolution?)

I'm sure I'll soon be on the other forums asking for various bits of help & advice!

So, anyway, "HELLO" from a true Ubuntu n00b!

):P
Hi and welcome to the community!!!  :popcorn:  Sally

---

