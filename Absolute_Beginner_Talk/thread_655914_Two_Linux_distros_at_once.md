---
title: "Two Linux distros at once?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Psyco_Chipmunk on 2008-01-01
Hey, I was just wondering, is there a way to two linux distros on my computer at once?  I really like ubuntu but want to have openSUSE at the same time.  If theres a way, please tell me! Thanks!  :guitar:

---

### Post by Psyco_Chipmunk on 2008-01-02
bump
:confused:

---

### Post by Xavieran on 2008-01-02
I think if you just repartitioned and made another partition for your other linux distro you could do that ...Just make sure you don't wipe your existing one!

GRUB should configure automatically with that...

---

### Post by bump_ on 2008-01-02
> Hey, I was just wondering, is there a way to two linux distros on my computer at once? I really like ubuntu but want to have openSUSE at the same time. If theres a way, please tell me! Thanks!

Can't you just dual-boot between the operating systems?

---

### Post by Shazaam on 2008-01-02
Yes you can. You can either dual-boot or virtualize (VMware, VirtualBox, etc).
When you dual/multi boot you can either use just one hard drive or as many as you like. When you virtualize you run a "guest" operating system at the SAME time as your "host" os. Lots of links and how-to's on the forums so search to your hearts content :)

---

### Post by EXCiD3 on 2008-01-02
You can either dual boot or run one in a Virtual Machine...[http://www.virtualbox.org](http://www.virtualbox.org) :D

---

### Post by jken146 on 2008-01-02
Yeah, of course you can do that.  Just free up some space for a partition for Suse and install it there.  It's probably not a good idea to have a shared /home though, as the hidden config files will probably clash with each other.  What I do is have a shared storage partition.

---

### Post by kestrel1 on 2008-01-02
You should be able to. I used to have two versions of Linux installed, but to be honest this was a awhile ago & I forgot exactly what I did. I have a feeling that I just had to manually configure Lilo to point to the other linux version. You should be able to do the same with Grub. I think I copied the configuration file for Lilo & copied the line that pointed to the other linux version.

---

### Post by Psyco_Chipmunk on 2008-01-02
so how do i make another partition?  Is there a progrm i can use to do that? how much space should i use?

---

### Post by kestrel1 on 2008-01-02
going by the above posts, I am well out of date. Didn't realise that grub would auto configure now. Cool.

---

### Post by kestrel1 on 2008-01-02
Try Gparted.

---

### Post by thelatinist on 2008-01-02
Like everyone else said, just install it in a separate partition.  And for goodness' sake don't bump a 10-minute old thread.  It makes you look like an impatient 5 year old.

---

### Post by Psyco_Chipmunk on 2008-01-02
to tell u the truth, the reason i'm doing this is because I love ubuntu and dont want to get rid of it but it has caused me to many problems.  I have had to reinstall ubuntu about 4 times so far and am going to have to do it again i think.  The main problem now is that i messed up my sound.  I just want a really really stable os...

---

### Post by kestrel1 on 2008-01-02
If you play about if you don't know what you are doing you will end up with an unstable OS.
Ubuntu is very stable, unless you mess with it in the wrong way.

---

### Post by bump_ on 2008-01-02
> The main problem now is that i messed up my sound

I noticed in your sig you use an HD audio COntroller. I have a similar sound controller and, when sound did not work out of the box, Variation B on this website worked like a charm:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by Psyco_Chipmunk on 2008-01-02
> **kestrel1 said:**
> If you play about if you don't know what you are doing you will end up with an unstable OS.
Ubuntu is very stable, unless you mess with it in the wrong way.


well, i admit i do mess a lot of things up, but some things seem to mess up on there own.  VLC just stoped working for no reason, wont even do anything if i click the icon or run it from the terminal or anything...
:(

---

### Post by kestrel1 on 2008-01-02
I am afraid that is the way of things with computers. I must admit to have messed up a few times in Linux & even more in Windows. I have learnt by my mistakes though. Been using computers for the past 24 years, but still learning new tricks. Even more now that I have got Ubuntu installed. Used Linux before, but I am really getting in to it this time.

---

### Post by Greevous on 2008-01-09
I installed BackTrack after I already had Ubuntu on my computer, but now apparently lilo takes control before grub has a chance, and it boots straight into Backtrack.

Their wiki says to add an entry for backtrack in the grub menu, but that doesn't help because the grub never comes up. 

How can I get lilo to recognize my Ubuntu distribution, or better yet- get back to using grub?

---

### Post by kestrel1 on 2008-01-10
Reconfigure lilo to boot into Ubuntu.

---

### Post by Paqman on 2008-01-10
> **jken146 said:**
> It's probably not a good idea to have a shared /home though, as the hidden config files will probably clash with each other.  

If you use different user names on each distro that won't be a problem. Each user's config files will be held in their own directory.

---

