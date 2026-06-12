---
title: "Questions about Edgy Eft accessibility"
date: 2006-10-25
forum: Assistive Technology &amp; Accessibility
---

### Post by linbetwin on 2006-10-25
I was never able to switch to Linux because the screen magnifiers (gnome-mag, kmag) are slow, buggy and CPU/RAM-intensive. Besides, enabling accessibility support causes a lot of problems to other applications.

I will probably try Edgy tomorrow, but I am just curious: does gnome-mag + orca/gnopernicus function well now? Does it render faster, does it follow keyboard focus in common applications? Do other applications crash because of it? Is it still a resource hog?

And also, are there differences in accessibility support between the i386 and the x86_64 versions of Ubuntu?

Thank you.

---

### Post by Henrik on 2006-10-25
The latest (unstable) version of gnome-mag has support for composite which should improve things greatly. That version has not yet made it into Edgy. We can probably make a backported version available though. We did apply a fix which stops a memory leak in gnome-mag so it should be less resource hungry.

You may also want to try xmcm which will&#295;ive a taste of what will appear in gnome-mag performance-wise. See: [http://xmcm.sourceforge.net/](http://xmcm.sourceforge.net/). And download an Edgy deb here:  [http://filebox.vt.edu/users/jgrieves/html/](http://filebox.vt.edu/users/jgrieves/html/) 

Have you tried running Xubuntu with Orca magnification. It is generally leaner so it may perform better. You'll need a range of gnome libraries installed for tracking to work though.

---

### Post by linbetwin on 2006-10-25
Thank you for your reply, Henrik.

I am proud to say I am the one that reported the memory leak on the GNOME Bugzilla.

I tried compiling xmcm some time ago but it didn't work. I will try the deb.

Should I try the x86_64 Edgy? Will gnome-mag perform better on that?

---

### Post by jasongrieves on 2006-10-25
might want to take a look at the old xmcm debs i made, as well as install the new gnome-mag for edgy from a previous post.  They aren't too far down the list :).  Feel free to comment on the new gnome-magnfier with composite.  I don't think its yet hooked into the at-spi layer, or at least I could not get it to do this.  It does, however, do full screen pretty well.  Runs hot though

---

### Post by RKCole on 2006-10-25
Hello, linbetwin.

I have been messing around with both Gnopernicus and Orca using the magnifier on both in Edgy beta (GNOME).  I must say that gnome-mag running with Orca for some reason performs MUCH better than it does with Gnopernicus.  I don't know why, but things run a LOT faster and more smoothly running it with Orca.

---

### Post by d3v1ant_0n3 on 2006-10-26
Depending on the spec of your computer, you might want to look into Beryl. It has a great zoom function as a plugin.

---

