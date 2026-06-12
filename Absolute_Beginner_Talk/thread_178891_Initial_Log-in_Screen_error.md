---
title: "Initial Log-in Screen error"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Shenmaster on 2006-05-18
Hi, I'm totally new to Ubuntu - just burned the CD and installed on an HP Brio.

No problems, till after the install - on booting up I get a badly resolved screen that shows two images - a bit like double vision except I cant see all of it - there are 2 cursors that move together and the words Ubuntu are bad to front or partially obscured - I can't see enough to log on. 

Is this a corrupt instal or is there some way I can fix this - the screen is near un-readable.

Thanks in advance for any ideas...help!

---

### Post by user1397 on 2006-05-18
it might just be some screen-resolution problems that ubuntu isn't compatible with.  did you try the live-cd before installing it?

---

### Post by Shenmaster on 2006-05-19
Thanks for the reply.

I didn't try the live CD - however I had no errors during installation and so I hoped it may be something minor that I could fix by the following:

1. Comand line (totally new to this but willing to give it a go)
2. Re-installation (a pain but I'd do it if I had to)
3. Re-burn the CD at a lower speed than 8X (as above)
4. download another ISO (as above)

Hoping to be able to resolve

---

### Post by steve.horsley on 2006-05-19
Before reinstalling, you could try this...

Press Alt-Ctrl-F1. This should flip you to a balck and white console screen that you can work with. If not, you have problems.

Log in and enter the command:
**sudo dpkg-reconfigure xserver-xorg**
which sould ask you a lot of questions about your video card. If you can't answer, take the default offered.

I've never done this myself because Ubuntu has always just got the video right for me, but this is what I see being suggested in these forums.

---

### Post by Shenmaster on 2006-05-22
Thanks for the reply.

It seems that the default options give me a problem with a badly configured X server which stops the GUI coming up all together. I am still playing with the settings and if this doesnt recover I think I will go for the re-download/burn/install option and start again.

---

### Post by Shenmaster on 2006-05-26
Thanks Steve,

Its sorted now - managed the reconfigure the xserver - noticed in other threads that changing the vid card to VESA worked for some people so tried that then did as you mentioned going with all the default options.

Up and running - I'm really chuffed:-D 

Now to explore and get it doing some clever stuff!

---

