---
title: "application packages"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by elvindon on 2007-06-02
If i have problem with a .deb package that installs ok but does not run who do i contact to try and get the problem resolved.
Thanks in advance
don

---

### Post by H.E. Pennypacker on 2007-06-02
Can you please be more specific?  What happens after you install, and what do you mean by it not running?  

Suppose that you install Firefox, the deb file will tell you that it has been installed.  You will then locate Firefox through Applications > Internet.

You could also tell us what you have installed.  If it has been succesfully installed (you will know it has been succesfully installed when you see that it says it has been installed), you will find it in under the Applications menu.  

If you are having an application specific error, you may contact the developer.  There is no centralized developer.  If you are having a Ubuntu problem, the forums are a good place for help, but if you want to report a Ubuntu bug, you may post that bug on launchpad.net.

We will need details before we can really answer your question.

---

### Post by elvindon on 2007-06-02
I downloaded a package called " qpcr1k", a hamradio program to control a pcr1000 receiver using Synaptic manager. It installed okay and when i run it it gives the following message
don@don-desktop:~$ qpcr1k
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/dev/pcr1000: No such file or directory

i would like to contact someone to try and get the problem solved....either the developer or the person who controls the package...
Hope this helps
DON

---

### Post by H.E. Pennypacker on 2007-06-02
By providing more details, I have been able to look into things, but unfortunately, this looks like something far beyond me.  I have never even heard of amatuer radio or ghetto.org.  

I have not been able to locate the developer of qpcr1k.  I have been, however, able to find something called GRIG.  It is a "Ham Radio control (CAT) program."  In any case, you'll find it here: [http://groundstation.sourceforge.net/grig/](http://groundstation.sourceforge.net/grig/).  Also check out its homepage: [http://groundstation.sourceforge.net/](http://groundstation.sourceforge.net/).

I found it through gnome-files.org.  You may also check out getdeb.net for any alternatives there.  

Since we know you are having an application specific problem, and not ALL applications, you should create a thread with a *specific* thread title that will hopefully attract other amatuer radio people.  Whatever you do, never use a general, and vague, thread title.  This is considered a definite sin on the Internet.  Please don't do this.

I am just guessing here, but your error appears to relate to not have a device that is apparently required for using amatuer radio. You would know better than me what kind of hardware is involved in operating or taking part in amatuer radio.  Are you sure all hardware is up and running, and everything is okay?  That is where I believe failure lies.  

As your error indicates, if all hardware had been fine, there should have been something located under /dev/pcr1000.  It is possible that your Ubuntu installation has pcr1000 located somewhere else, not under /dev/.  Please do a search for PCR1000 (Places > Search).  

Some of the other errors you received are quite general, according to a Google search.  See how far you can get with a Google search by copying and pasting one line at a time.  Never copy and paste an entire error output because other people's errors will likely only match a part of your error, not all of it.

PS:  I forgot to add what may be a useful link: [http://radio.linux.org.au/?sectpat=All&ordpat=&descpat=](http://radio.linux.org.au/?sectpat=All&ordpat=&descpat=).

---

### Post by elvindon on 2007-06-02
thank you very much for the work you have done...this is my first time on here and have a lot to learn...will maybe try a different package as you suggesthanks again
Don

---

### Post by dchurch24 on 2008-07-15
Did you get grig working with your pcr1000 ever?

I have one coming (ICOM PCR1000 from ebay) and Grig looks fantastic.

---

