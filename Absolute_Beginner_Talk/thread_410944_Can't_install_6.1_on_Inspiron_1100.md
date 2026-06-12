---
title: "Can't install 6.1 on Inspiron 1100"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by coollibrarian on 2007-04-16
Hi

I cannot seem to get 6.10 installed on my Dell Inspiron 1100.

When I boot the disk, I get the initial menu, choose run/install, it says it's loading the kernel, it runs for a bit, and then just hangs. I never get anymore prompts, it never asks me (again) if I want to install the program - nothing. Just runs for a while and then simply stops.

I have been trying for hours. I have looked at the forums, but I haven't found anything that helps - most assume that I have the system installed, but I can't get it to install. I have read about the Inspiron 1100 having resolution issues, but I wasn't sure what to do concerning that.

Currently the system runs XP with SP2. I have not had any other problems with it. I ran virus and registry checks before I started the process. I ran the hash on my download.

I am computer literate, but not a programmer by any stretch - this is my first foray into ubuntu and linux.

Any ideas?

Thanks!

---

### Post by dstew on 2007-04-16
I recently installed 6.10 on a Dell C800, which is a lot like your Inspiron. Due to video display issues, I could not install from the live CD, no matter what boot options I tried. I finally installed using the Alternate CD (text-based install). After I finally got it installed, I was able to solve some of the display issues.

If you are sure your install disk is ok, you could also try some boot options (F6 at the initial screen, enter noapic, nolapic and many others...) but try the Alternate install CD first.

---

### Post by coollibrarian on 2007-04-16
I will try that. Is it more difficult than installing from disk? Is there just a file to download?

I want to poke my eyes out...

---

### Post by coollibrarian on 2007-04-16
I am so sorry to be do dense, but I am having a hard time locating the "Alternate" install CD. Is it called something else? Is it a separate download?

There's nothing like computer issues to make an otherwise smart person feel like a loser.

Thanks!

---

### Post by Happy_Man on 2007-04-16
[http://releases.ubuntu.com/edgy/ubuntu-6.10-server-i386.iso](http://releases.ubuntu.com/edgy/ubuntu-6.10-server-i386.iso)

That file there is what you're looking for.

---

### Post by tstockma on 2007-04-16
Hi...I'm hitting this exact same problem, but I can give you an effective "next step".

When you first get the Ubuntu "splash screen" with options about what to do, hit F6.  This brings up a text line, that is the options-line on loading the kernel. 

 Use your backspace key, delete the "--", type in "acpi=OFF".  Now use the right-arrow to get to the end of "quiet" on that same line...backspace to get rid of it...then "BOOT_DEBUG=2|3"  (that "|" is the shift-backslash on your keyboard).

You'll see a bunch of text scroll by, let it scroll.  At some point it will "hang" for a while; this is the exact command in "loading the kernel" where your problem is.  (Mine is, mounting the root file system.  I'm about to experiment just a bit more, then I'll post another request for help.)

Then post another question, asking for help on your exact problem.  Good luck!

---

### Post by coollibrarian on 2007-04-16
Thank you both for the information!

I am in the process of doing a clean install of windows on the laptop, then I will try the alternate CD. If that doesn't work, I will try the f6 steps described. If that doesn't work, I will probably just play with some FOSS programs and leave Windows on the lappy for now.

---

### Post by tstockma on 2007-04-16
Yow!  I hope you're having more luck than I am.

I have made no progress, and my "BOOT_DEBUG=2|3" no longer gets a display of the execution of the various load commands.  I am also going for the "alternative" install CD image.

The link Happy_Man posted is to the "server" version, which might or might not be something that works well for you...as best as I can determine, when people recommend the "alternative" install, it's ISO image [http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso) that gives us a command-line type way to do our initial load, with full control over parameters and viewing the command-by-command results of that load.

HTH, good luck, let us know of results!  Tom

---

### Post by tstockma on 2007-04-16
Well, I have my "final answer".

Chuck Dapper Drake.  Go to Edgy, or better yet, wait until Feisty production is released.

Much painful research leads me to conclude there's just no upside to trying to make Dapper work, even though it's officially the release with the longest support offered.

Good luck!

---

