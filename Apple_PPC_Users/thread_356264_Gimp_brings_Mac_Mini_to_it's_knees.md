---
title: "Gimp brings Mac Mini to it's knees"
date: 2007-02-08
forum: Apple PPC Users
---

### Post by jsedwards on 2007-02-08
I've just installed Kubuntu 6.06.1 on a MacMini.  I have used Kubuntu on x86 for some time, but this is the first time I've tried Kubuntu on a PowerPC.

Everything seems to work pretty well, except if I try to edit a photo using the Gimp.  As soon as I try to open a file the machine grinds to a halt.  My first thought was that it was because the MacMini only has 256 Mb of RAM.  But then I remembered that my laptop only has 256 Mb of RAM and the Gimp runs fine on it, I think. I will check....  oops, I may have answered my own question, my laptop has 512 Mb of RAM.  So I guess that small amount of RAM is the problem?

I guess I could expand the memory, but after I just read another thread in this forum that PowerPC support is being discontinued I am not sure that it's worth pursuing this?  Maybe I should switch back to x86...

-Scott

---

### Post by matt_risi on 2007-02-08
I run gimp on a machine that has 256mb RAM, 866mHz processor, and it's by no means slow.. but that could also be because I'm running Xubuntu on it. It isn't PowerPC however, maybe that could be the difference?

---

### Post by garybrlow on 2007-02-08
You could try setting Kubuntu not to use a lot of system resources. Gimp should run fine even on 256MB unless your project on gimp is very big in terms of resolution and size that it needs more memory to edit and process. Kubuntu on 256MB is bare minimum, on normal usage is somewhat ok but with other things going on,  it will be quite slow and even hang. You're better off using XFCE/Xubuntu on that spec or set KDE to use minimal resources. :)


Cheers!!!

GaryBrlow :D

---

### Post by mips on 2007-02-08
> **jsedwards said:**
> 
I guess I could expand the memory, but after I just read another thread in this forum that PowerPC support is being discontinued I am not sure that it's worth pursuing this? 

RAM is cheap & Dapper has about 4yrs of support left. Either way you will still have a functional PC.

---

### Post by matt_risi on 2007-02-08
I'm still wondering why you'd remove Mac OS from the mini in the first place, it's a BSD distro in itself, and is tailored for that specific hardware.. maybe as a project or something, but if it's your main box?

---

### Post by ssam on 2007-02-08
if you are using gimp a lot you might do better running gnome or xfce as you desktop environment. that way you would not need all the kde and gtk libraries loaded at the same time.

matt_risi: using gimp in mac os x is not much fun.

---

### Post by jsedwards on 2007-02-09
I decided that the easiest solution would be just to go out and get a larger ram.  A 512 Mb stick was only $40 and that seems to have solved the problem.  The Gimp seems pretty responsive.  Not quite as fast as the amd64 machine I had been running it on, but it will do ;-)

As far as XFCE/Xubuntu goes I have been meaning to try it, but I haven't gotten around to it yet.  Wouldn't it be possible to install it on this machine alongside KDE and switch back and forth?

And as far as Mac OS X goes, I have never really been able to get into it.  I really liked the old Mac OS and I still have a Quadra that I use for recording.  But even though I think Mac OS X is pretty slick, I find it cumbersome to use.  After 20 years of programming on Unix and Linux, things are just different enough on OS X to make things difficult.  And the last time I tried to compile programs on it, there were different versions of the compilers for different versions of the OS, things weren't where I expected them to be.  I just found it to be more greif than I had time to deal with.

So I put OpenBSD on the Mini and used it as my main desktop for a couple of years and it was great.  I loved it.  But last year when I upgraded to OpenBSD 4.0 I got into some funky behavior.  The one thing I had trouble with OpenBSD on the Mini was shutting it down.  It normally wasn't a big deal because I normally never shut it down (only when the power went out).  I don't know what went wrong in 4.0 but after running X windows (or I think now it may have been KDE) and then shutting it down, it would never boot back up.  I would have to re-install the OS to get it to boot.  I fooled around with it for a couple of weeks in my spare time, but I finally gave up, because I just don't have that much time to spend fooling around.

Sorry this got so long.  Thanks for all of your advice.
  -Scott

---

### Post by mips on 2007-02-09
> **jsedwards said:**
> 
As far as XFCE/Xubuntu goes I have been meaning to try it, but I haven't gotten around to it yet.  Wouldn't it be possible to install it on this machine alongside KDE and switch back and forth?


Rather than XFCE go for something even lighter like Fluxbox+Rox-filer or look at the ready made version called Fluxbuntu.

---

### Post by maxamillion on 2007-02-09
It might be a bug in the PowerPC Gimp package because a Mac Mini with 256mb of ram shouldn't crumble because of theGimp, it should be slow but not come to a halt. (I have seen similar setups run Photoshop on OS X)

If for some reason adding ram or switching to a Desktop Environment with a smaller memory footprint does turn out to help then it could have something to do with the KDE libs, but I don't think theGimp should cripple a machine like that. (I've run theGimp on a machine with 128mb of ram before).

---

### Post by jsedwards on 2007-02-09
> **maxamillion said:**
> It might be a bug in the PowerPC Gimp package because a Mac Mini with 256mb of ram shouldn't crumble because of theGimp, it should be slow but not come to a halt. (I have seen similar setups run Photoshop on OS X)

I guess it depends upon your definition of slow :)  I tried to load a 4448 x 5040 pixels and it pretty much sat there.  After several minutes the progress bar was still maybe 5%.  And if I tried to change to the virtual desktop with a Konsole in it, it took like 30 seconds to render it.  Typing in the Konsole was painfully slow (after hitting a key, it would take several seconds for the characters to appear).  I tried to switch to a virtual desktop with Firefox running in it and it never did render, I finally gave up and switched back to the desktop with the Gimp in it.  And I would say it took almost a minute to render it.

Now with the 512 Mb RAM in the Mini, it took 20 seconds to load the same 4448 x 5040 image and another 5 seconds to bring up the window with the image in it.

> **maxamillion said:**
> If for some reason adding ram or switching to a Desktop Environment with a smaller memory footprint does turn out to help then it could have something to do with the KDE libs, but I don't think theGimp should cripple a machine like that. (I've run theGimp on a machine with 128mb of ram before).

Well it could just be how many other apps I had running.  I had 6 virtual desktops, Adept in one, Konqueror with 8 tabs open in one, Firefox with 4 or 5 tabs, Konsole with 6 tabs in one, and the Gimp in one.  If I had only the Gimp running all by itself, maybe it would have been OK?

If this Mini wasn't such a pain to open up, I might be inclined to put the 256 Mb RAM back in and run some further tests.  But it makes me a little nervous that I might break something.  If I had been thinking I would have just left the case apart for a while.

---

### Post by ssam on 2007-02-09
the only difference between the ubuntu derivatives are the default package choices. there are a set of meta-packages that make sure all the packages needed for a derivative are installed. these are names ubuntu-desktop, kubuntu-desktop etc.

you can install several of the *-desktop packages. then you can choose which desktop to use at log in (click on sessions).

if you want to install gnome without all the ubuntu default apps, i think gnome-core is the right metapackage.

if you want to install a very light window manager like openbox or fluxbox, then find their package.

---

