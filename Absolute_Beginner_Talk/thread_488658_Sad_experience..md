---
title: "Sad experience."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by mastersync on 2007-06-30
Hello there, I've been reading stuff about Linux 3 months ago and yesterday I brave myself to install Ubuntu. 
I'm running on Windows XP and somehow I didn't like it, so I downloaded Ubuntu and burn it on a disc. Format the drive ext3.

Here's where the pain started, I boot it up and I tought everything went well. After the hardware configuration(cd-rom) page, the setup remains with blue screen, for almost 1 hour. No IDE led, CD in spinning. I tought, "Maybe its the disc." Sadly, its not the disc, I burned almost 6 copys of Ubuntu, all low speed. None worked.

The laptop I'm installing Ubuntu on is pretty old, 500Mhz, 128mb RAM and 5gb HD. It ran WinXP before I attempt to install Ubuntu. I tried the guide on low-end pc documentation, ubuntu server, command-line, none get further than that screen.

I really hope the people here can help me to experience Ubuntu.

Thank you.

---

### Post by alienexplorers on 2007-06-30
You could try the Alternate CD or xubuntu.

---

### Post by hardyn on 2007-06-30
I beleieve the mininum memory requirement for a grapical environment are 196MB of ram.

---

### Post by sailor2001 on 2007-06-30
1st......... your ram is too small for regular ubuntu installation. try alternate ubuntu or xubuntu.
2nd you have to burn disk as an iso image......and then boot into that.... the regular ubuntu disk is a "live" disk and you may be able to boot into that (slow) , but doubt it.

---

### Post by buuntuu! on 2007-06-30
welcome to ubuntu!
if you need help, please be more specific!
what we need to know to be able to help:

which cd did you download?(with 128mb a desktop-cd will run but will NOT install, you'll need the "alternate-cd")
did you check the filesum of your download? (it could be a bad download)
did you do the integritycheck of your disc?
did you do the mem-test?

cheers, buuntuu!

EDIT: you'll need xubuntu of course, even better would be a server install with a lightweight windowwmanager on top, but you can do such tweaks once you have become comfortable with *buntu

---

### Post by mastersync on 2007-06-30
I tried Xubuntu too, but same thing happen. Tried Alternate cd too.

It gives me a buffer logical partition error or something.

I know my RAM is too small, but it can handle XP ? Then I tought it could handle Ubuntu...

---

### Post by buuntuu! on 2007-06-30
a thing i just noticed: with a harddisc of 5gb how on earth did you run xp??
afaik the install alone requires no less than 7gb or am i mistaken??

btw: DID you do the steps i posted above?

---

### Post by mastersync on 2007-06-30
Oh yes I tried downloading alternate twice, burn it again and no luck, it still hangs.

Haha, surprisingly WinXP runs fairly smooth on that 5gb.

EDIT : I noticed it hangs after recognising the cd drive, could it by my cd drive ? Its an old dell laptop and it uses external Cd Drive, its not USB.

---

### Post by buzzmandt on 2007-06-30
start the alternate cd, when boot/install options comes up press F6 and at the end of the line (after the -- ) add the following code 
noapic nolapic

try that....this is what stopped me from using ubuntu for about a month on this system

---

### Post by mastersync on 2007-06-30
Nope, it didn't work...

Thanks for the replys!

---

### Post by mastersync on 2007-06-30
Sorry for the double.

Maybe Ubuntu doesn't support external CD Drive ?

---

### Post by buuntuu! on 2007-06-30
it's a good guess, i've read about external drive-problems, search for such threads!
good luck!

---

### Post by mastersync on 2007-06-30
I found out something about loadlin, it was too complex tough.

I'll try.

Thanks!

---

### Post by Hranj on 2007-06-30
sorry, what i posted was already established

---

### Post by mastersync on 2007-06-30
After reading all that loadlin articles, I still don't get how you can load xubuntu from harddrive.


I really need help...

EDIT : What if I do this. I burn the Xubuntu iso and the live-floopy as data and copy them to the hardrive. Then running the live-floopy to install Xubuntu. No ?

---

### Post by mastersync on 2007-07-01
Bump.

---

### Post by thelemech on 2007-07-01
> **buuntuu! said:**
> a thing i just noticed: with a harddisc of 5gb how on earth did you run xp??
afaik the install alone requires no less than 7gb or am i mistaken??

btw: DID you do the steps i posted above?

On a side note I've installed XP pro on a 4 GB Hd and it worked -sort of!

---

