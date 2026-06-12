---
title: "New poster, newb questions..."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by phlak on 2007-09-15
Hey all, this is my first post here, and I'm also incredibly inexperienced with Linux, so bear with me if I don't make any sense.

I installed Debian Etch a few days ago, without a problem. I quickly noticed when I tried to switch to different virtual consoles, there was a problem. When I switched to other VC's my monitor goes blank, and shows nothing on the screen, but indeed the monitor is still functioning. I switched over to my other monitor, same problem. Not only that, but once I switch from Gnome to a terminal, all of the terminals are blank, and I can't get back to my Gnome terminal. Hopefully, this is making sense. Now, I boot up Debian today, and get to the main Gnome login screen (it goes straight to Gnome, no terminal) after exactly 2 seconds, the screen goes blank, just as if I had switched to a terminal. Obviously, I got very frustrated with this, and decided to try a different distro, thats why I am here.

Ok, as I download the Ubunto iso, i realize I have a few questions that I should probably ask.

1. Why would Debian die on my like that? I'm running a Nvidia 8800GTX

2. Does the current version of Ubuntu, boot directly into a GUI environment?

3. How can I go from a GUI in linux, to just the command line? This one is important, because when I tried to install my GPU drivers in Debian, the installer kept telling me that I "was running an Xserver, and needed to stop to continue installation"

4. Last question. In order to satisty my GPU installer's "requirements" would switching over to a virtual console have solved that problem? Or would I have had to shutdown Gnome?


Ok, thanks in advance. And sorry if these questions are just plain dumb, I really want to discover Linux, but the learning curve is steep for me at the moment. Anyways, thanks.

---

### Post by Happy_Man on 2007-09-15
1. I have no idea why Debian would act like that, but I haven't seen a single issue like that on thse forums, so we can only hope. 

2. Yes, Ubuntu goes from GRUB to a loading bar splas screen, to a GUI login. No 'startx' command required. 

3. You can boot into recovery mode, which is installed along with regular mode in Ubuntu.

4. Yeah, you would have had to shut down X (not just GNOME). After all, it's still there, even when you can't see it.....

And another thing. You won't need to do all your shutting down X business with Ubuntu. There's a Restricted Drivers Manager that will do it all for you. All you must do is reboot when it finishes.

---

### Post by rfruth on 2007-09-15
Kinda can help you - not sure why Etch crapped out, but yes Ubuntu boots into a GUI, the command line is just a click away (terminal)

---

### Post by phlak on 2007-09-15
Thanks for the reply.

Here's another one:

How would I go about shutting down X?

---

### Post by rfruth on 2007-09-15
hmmm, shut down X - reboot, ctlr-alt-backspace (quick restart of X), ctlr-alt-f2 - fire up terminal full screen & forget X is running ?

---

### Post by Happy_Man on 2007-09-15
Press ctrl-alt-f1 and type (after logging in and all) ```
init 3
```

---

