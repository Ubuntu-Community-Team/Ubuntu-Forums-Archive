---
title: "error installing ubuntu on ibook G4"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by gabric098 on 2008-07-29
Hello everyone,
I downloaded iso image of ppc version of Hardy Heron from here:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
I burned it onto a dvd, I restarted my mac pressing C key. Installation started and asked me to choose from different boot types, i choosed "live". After few seconds i red on my monitor this 2 lines:

PCI cannot allocate resource region 0 of device 0001.10.18.0
PCI cannot allocate resource region 0 of device 0001.10.19.0

then the monitor became black and nothing happened (I waited for about 5 minutes).

Any suggestion?

My mac configuration:
ibook G4 12 inch 800Mhz
640MB ram
30Gb HD

Thanks a lot!
Gab

---

### Post by stream303 on 2008-07-29
You'll probaby need to pass some kernel options to it at boot time.  See:

[http://ubuntuforums.org/showthread.php?t=872191](http://ubuntuforums.org/showthread.php?t=872191)

Hit -tab- at the second stage yaboot boot: prompt and see what the options are.  Most likely video=ofonly and/or nosplash will get you further.

---

### Post by mkvnmtr on 2008-07-29
Just last night I finally got Ubuntu 8.04.1 installed on my IBook G4. Don't wait to hit tab. When it first starts to tell you that it is about to load the kernel hit tab. You will see  options in several rows repeated several times. I had luck with one on the left that said something like ofonly nosplash powerpc. tybe this in like it says. At the bottom you will see the prompt and where you are typing. When you are finished typing hit enter. If the first on does not work restart come to the same place to hit tab and try another. I had the same problem as you and once you get to the black screen there is nothing you can do but start over. I must of tried 10 times before I found when to hit tab. Good luck

---

### Post by gabric098 on 2008-07-30
Thanks a lot,
as you suggested me I finally found out the right option:
live-nosplash-powerpc video=ofonly

Now installation is going on, I'll tell you much more later!

Thanks again.
Gab

---

