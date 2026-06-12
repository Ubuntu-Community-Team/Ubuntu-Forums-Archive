---
title: "[SOLVED] Bad display flickering running Hardy live CD on PowerBook G4"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by mfox on 2008-05-22
It seems that Hardy and Gutsy live CD's behave different when run on my PowerBook G4 Al.  Gutsy booted up fine and gave me a nice screen image.  But Hardy gave me a badly flickering image.  Has anyone else run into this problem?  Is there something I can do to fix it?  Will I get this problem if I actually do an install from the live CD?  Would I be better off with the alternate CD?

---

### Post by stream303 on 2008-05-23
I have a feeling you'd run into this problem no matter what, as the x server is radically different from Gutsy.

What I'd do from here is to make a copy or write down your existing Gutsy /etc/X11/xorg.conf file!!  We can use info from that to fine tune out any Hardy problems if you really desire to upgrade.

I personally always recommend using the "alternate" install image.  Back up your important data first!!

---

### Post by mfox on 2008-05-23
So if I write down what's in the xorg file, would I use the monitor-related settings as I'm installing from the Alternate CD file?  If so, where would I have the opportunity to enter the relevant information?  Or would it be better to install from the regular live installer and edit the xorg file once it's already installed?  

If I was to install Gutsy and upgrade the installation from the internet, would that likely keep my display settings?

---

### Post by sdennie on 2008-05-23
It might be useful if you described exactly what you mean by "flickering".  Is the screen turning on and off constantly or are window movements just jagged?

---

### Post by Brightbelt on 2008-05-23
Hi,
  There has been a thread on this for the intel Macs as well and I had intermittent flickering on my 24" intel iMac, ie, some boots went smooth - others would flicker non-stop. 

I can't guarantee success on this, but several have suggested that doing an Envy install of your ATI or NVidia graphics driver will solve this problem.

I went ahead and did it and so far, I've been flicker free. (that's too strange of a phrase). 

It may be worth trying...after first installing Hardy to your hard drive of course.  Here's the site for envy...
[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

I hope this helps,...Frank B.

PS I think you'd have to wait and apply this after your hard drive install of Hardy.

---

### Post by mfox on 2008-05-23
Thanks, Brightbelt.  This assumes that I can things clearly enough following the install to be able to carry out functions.  I think I can.  

vor, the screen wasn't turning on and off as far as I could tell, but it seemed to be some combination of ghosting and flickering that was not only unpleasant, but it made it difficult to read something on the screen or to some extent, to even aim the cursor.

---

### Post by mfox on 2008-05-25
Go figure!  When I started up the live CD to do the actual install, I didn't experience the bad display flickering problem again!  I did the install and didn't have the problem afterwards either! :)

Thanks anyway for your suggestions!

---

