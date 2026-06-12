---
title: "Dead Screen after boot from live CD on G4 Tower"
date: 2008-01-02
forum: Apple PPC Users
---

### Post by tvisher on 2008-01-02
Hi Everyone,

I've tried several times to install Ubuntu (pretty much every release starting at Breezy) on my old G4 tower and I've consistently run up against the same problem every time except when I installed the 6.10 server edition.  The problem is that when I launch from the CD, I get a normal boot choice screen (sorry if that's not standard nomenclature), and then afterwards no matter what I choose, a few messages flash across the screen and one of two things happens: if I'm booting into the GUI (so standard live CD), I get a white screen which does not go away (and I have tried appending video=ofonly onto just about every option in tho boot menu) or, if I'm booting from the alternative CD, I get a blank black screen with a non-blinking cursor in the top left hand corner that does not go away.  The longest I've allowed the machine to stay in this state is about 2 days (at one point I thought that it must just be working really slowly for some reason).

My initial thought was that the problem lay with the video out that I was using, but that's not the case.  I've now attempted to install with the video coming out of both of the video ports on the G4 and both ports exhibit the same problem.

Does this sound like something anyone else has seen?  What could the problem be?

Thanks in advance for your help!

Timmy V.

---

### Post by wavetheory on 2008-01-02
I'm trying to use the LiveCD for 7.10 on a G4 eMac, and pretty much have the same problems.  Seems like there should be an easier way...

---

### Post by tvisher on 2008-01-03
Not sure if this is legal here or not but I'm just trying to bump this back up to the top of the list.  Just to let everyone know I was able to successfully install Breezy Server Edition onto the machine.  Is there a way to upgrade from that environment through to Gutsy Desktop Edition?  Obviously it would not be the most desirable path, but at least I'd be up and running.

More desirable would be to understand why Ubuntu won't detect my screen properly.

Thanks in advance!

Timmy V.

---

### Post by DJLspider on 2008-03-21
I am having the EXACT same problem. This whole PPC thing is proving to be quite the headache. I have read all over the place what problems people are having, but I can't find this one addressed and solved anywhere.

---

### Post by stream303 on 2008-03-22
You may need to go beyond just video=ofonly.

Check out the PPC Faq, especially for some Gutsy issues:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Have you tried just

Linux-nosplash-powerpc

or a little more

linux-nosplash-powerpc video=ofonly

or even more

linux-nosplash-powerpc video=ofonly break=top

If we can find a combo that works, we can add that to the /etc/yaboot.conf file and update it so you won't have to type it at the boot prompt every time.

If busybox still comes up, we may have to add the ide-core as noted in the faq.

Looking forward to a G4 tower up!

---

