---
title: "Can't even boot the liveboot"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Obbeskrutt on 2006-08-16
Ok, to start off, I'm very new to Ubuntu, and Linux to for that matter.
I boot up the disc, and go start to boot up.
When trying to load X, i get the error "Failed to start the X server (your interface...)".
I scouted the forum a bit, and found some others that had the same problem, so I ran "sudo dpkg-reconfigure xserver-xorg" and began to do the changes.

I think I'm failing at the monitor setup, since as soon as I select  any color-depht, i get the error:

"Overwriting possibly-customised configuration"

..and I get tossed back to the prompt.

When running "startx", I just get flooded with text, ending with "no monitor detected" or something.

I'm sorry if this problem have been posted countless of times before, and if so, could someone redirect me to that topic, since I couldn't find it.

Hopes that someone can help me.

Edit: I wanna add that I'm using a Viewsonic VX922 monitor.

---

### Post by Metacarpal on 2006-08-16
Hi, and welcome to Ubuntu!

I'm sorry you're having trouble getting the ball rolling.  We'll get you there.  Give us a little more detail about the computer you're trying to install on.  Do you have at least 256MB of RAM?  If you have less than 256MB of RAM, and you're trying to use the "desktop" install CD, that's probably what's giving you trouble.

The Desktop CD is a "Live CD", which means that it runs the operating system from the CD-ROM without needing to install to your hard drive.  You can then use the live session to perform the installation.  Unfortunately, the live CD can run a bit slow, and tends to hang entirely if you don't have enough memory.

If you're running on less than 256MB (or right at that), you might try downloading and installing from the "Alternate Install" CD.  It doesn't have the live desktop session (just the installer), so it tends to run better on low-memory machines.

And I might be wrong, but I don't think you can alter the x-org config file for the live session, since it is on a read-only CD...

---

### Post by Obbeskrutt on 2006-08-16
Yeah, that's what I thought.
I'm running it with 1024mb RAM and a Athlon64 3700+.

Nevermind tho, I solved the problem by running it with safe-graphic mode (or whatever it's called), witch gave me access to X, and therefore the installer.
Everything works fine now tho.
Only problem is that I have to refresh my IP everytime I reboot, witch is kinda annoying since I'm alter between Ubuntu and Windows rather often.

Thanks for the help tho Meta.

---

### Post by bodhi.zazen on 2006-08-16
Nice.

You can modify xorg.conf after booting to the live CD. You need to know the Horizontal and Vertical refresh rates for you monitor.

As far as your net work all you need to do is tweak your network configuration. Try dhcpclient from the command line.

---

