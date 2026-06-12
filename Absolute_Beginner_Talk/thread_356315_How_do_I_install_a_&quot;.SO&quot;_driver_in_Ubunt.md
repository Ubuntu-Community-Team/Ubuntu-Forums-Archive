---
title: "How do I install a &quot;.SO&quot; driver in Ubuntu?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-02-08
810_drv.so  is the file.  It is a vide driver patch.  

See 
[http://www.ubuntuforums.org/showthread.php?p=2121912#post2121912](http://www.ubuntuforums.org/showthread.php?p=2121912#post2121912)
for more information.

THANKS!

---

### Post by emarkay on 2007-02-08
Using Windows again is driving me crazy!  HELP!  Anyone have an answer?

---

### Post by benuski on 2007-02-08
Where exactly did this error appear?  What were you doing when it appeared?

---

### Post by dannyboy79 on 2007-02-08
that driver is for xfree86, ubuntu doesn't use that x server. Ubuntu uses Xorg. sorry, you'll have to look for another solution. if you already tried this link, [http://xorg.freedesktop.org/archive/X11R6.8.0/doc/i810.4.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/i810.4.html)
than I don't know what else to tell you except I can tell you for sure that trying a xfree86 driver within xorg isn't going to work. that's similar to trying an ati driver on an nvidia graphics card. I just have to be honest, onboard video is rarely meant for direct rendering and 3d intensive stuff.

---

### Post by emarkay on 2007-02-08
> **benuski said:**
> Where exactly did this error appear?  What were you doing when it appeared?

About 5 seconds after booting to the GUI - not enough time to even "look around".  I then get the text window with the error message for about 10 seconds. then it goes back to the login screen...

---

### Post by emarkay on 2007-02-08
> **dannyboy79 said:**
> that driver is for xfree86, ubuntu doesn't use that x server. Ubuntu uses Xorg. sorry, you'll have to look for another solution. if you already tried this link, [http://xorg.freedesktop.org/archive/X11R6.8.0/doc/i810.4.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/i810.4.html)
than I don't know what else to tell you except I can tell you for sure that trying a xfree86 driver within xorg isn't going to work. that's similar to trying an ati driver on an nvidia graphics card. I just have to be honest, onboard video is rarely meant for direct rendering and 3d intensive stuff.

Thanks for the heads-up.  3D stuff? Hell no, I just want my 2D Ubuntu!  
This error happened when I got a new Samsung 940n  flat screen LCD monitor, AFTER, I set it up in  Windows$. 

I think it's a coincidence, um, isn't it?

MRK

PS: As for that driver, I already have thatone loaded - and it was fine till yesterday! How can I tell if I have the latest "X" driver?

---

### Post by emarkay on 2007-02-08
I am 'going out on a limb" here, but shall I download the latest Xorg? 

[http://wiki.x.org/wiki/X11R71Release](http://wiki.x.org/wiki/X11R71Release)
[http://xorg.freedesktop.org/releases/](http://xorg.freedesktop.org/releases/)

Um, how do I set it up in Ubuntu?

---

### Post by dannyboy79 on 2007-02-08
no, you don't need the latest xorg. have you tried to reconfigure your xorg. the command is 
sudo dpkg-reconfigure xserver-xorg from the command line. so boot into the recovery mode and then do this command.

OH, I just saw what you put as far as when the error is occuring. the only reason I have ever seen my ubuntu install go from logging in right back to the login screen was because my / and or /home partitons were full. so, boot up using a live cd or boot to the recovery mode and delete some stuff. you could try to do sudo aptitude autoclean or sudo aptitude clean. which per the man pages, do this:
 clean  Removes  all previously downloaded .deb files from the package cache directory
              (usually /var/cache/apt/archives).

       autoclean
              Removes any cached packages which can no longer be downloaded. This allows you
              to  prevent  a  cache from growing out of control over time without completely
              emptying it.


good luck.

---

### Post by emarkay on 2007-02-08
I have "gigs" of space, so it's not that.  I will reconfig my xorg file and see.

D'ya'thunk' it has anything to do with my new monitor?

---

### Post by dannyboy79 on 2007-02-08
well it could be your monitor, have you tried hooking up a different one. does the monitor have a resolution that your vid card doesn't support?? I bet if you reconfigure your xorg it will work again

---

### Post by emarkay on 2007-02-08
Xorg reconfigure worked - thanks - now need to tweak it so it works as before.

---

### Post by dannyboy79 on 2007-02-09
glad to hear it.

---

