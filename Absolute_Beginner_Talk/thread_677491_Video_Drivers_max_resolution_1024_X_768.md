---
title: "Video Drivers max resolution 1024 X 768"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-01-24
I have a Thinkpad A31 2652-C4U.  My Kubuntu installation defaulted to a basic ATI Radeon video card.

2 Questions
1)Does anyone know of other Linux Driver capabilities for this Thinkpad?
2)Can Windows XP driver be encapsulated somehow to run on Linux?

Bill

---

### Post by PeterJS on 2008-01-24
> **bmachia said:**
> I have a Thinkpad A31 2652-C4U.  My Kubuntu installation defaulted to a basic ATI Radeon video card.

2 Questions
1)Does anyone know of other Linux Driver capabilities for this Thinkpad?

Have you tried the Restricted Drivers Manager? System > Administration > Restricted Drivers Manager
> 
2)Can Windows XP driver be encapsulated somehow to run on Linux?

Bill

Yeah try searching for virtual box on the forums, there are some good guides to setting it up.
EDIT, you were asking about drivers, whoops. I misread that and thought you meant the whole OS

---

### Post by emarkd on 2008-01-24
Did you enable the restricted drivers for your graphics card?  Click System > Administration > Restricted Drivers Manager to make sure.

Yes, you can use NDISWrapper to wrap some Windows drivers for use in Linux, but using real Linux drivers tends to be the better option if you can.

---

### Post by bmachia on 2008-01-24
You guys nailed it!!!

My video card is not in the Restricted Driver list/screen/window.

It only list a modem, that is not used/installed and my Wireless PCMCIA card


So, now for the really dumb question;
How do I add it?
and
will option for drivers come up automatically or should I download ATI/Radeon Mobility 7500 drivers first?


Bill

---

### Post by emarkd on 2008-01-24
Well, as far as I know, you don't.  Either the restricted drivers are available or they're not.  I'm not sure, but I would think you would need the fglrx driver.  You can see if you're already using by running

```
less /etc/X11/xorg.conf | grep fglrx
```

and if it's already enabled you should get back:

Driver    "fglrx"

---

### Post by bmachia on 2008-01-24
Will it does not look like lgfrx is in xorg.conf.

grep did not return any information, so I
    sudo kwrite /etc/X11/xorg.conf 
and did not find lgfrx within the file.

Does this mean I'm out of luck?

---

### Post by emarkd on 2008-01-24
Are you misspelling fglrx in your post or did you search for the wrong thing?  Go back and see if you're using fglrx as your driver.

---

### Post by bmachia on 2008-01-24
SORRY, I mistyped it in my last post.

I went back: sudo kwrite /etc/X11/xorg.conf

^F search for fglrx, and received the following:  Search string 'fglrx' not found!

---

### Post by emarkd on 2008-01-24
not a problem.  just making sure.  honestly, i hoped you'd searched for the wrong thing and that your problem was solved :)  i'm not really sure where you should go from here, so i guess i'll point you to ubuntu's official guide for this and hope it helps:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by bmachia on 2008-01-24
Well reading the link you sent me, told me a-lot.  An lspci command returned the following information.

VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Because my VGA controller is a Radeon Mobility 7500, it is below the threshold for fglrx.  fglrx requires a model 9500 or greater, or an x prefix to the model number.

I'll keep studying over time, but I think I might be at the end of my possibilities.  I really hope not, but don't know where to go from here.

Thanks
Bill

---

### Post by Nythain on 2008-01-24
dude, your display adapter may be wicked old unsupported legacy type crap... i mean, you quite possibly are screwed minus an upgrade or new lappie...
this thread might help you get SOMETHING going
[http://ubuntuforums.org/showthread.php?t=576277](http://ubuntuforums.org/showthread.php?t=576277)
gotta love google searches... "gutsy ati legacy" :)

---

