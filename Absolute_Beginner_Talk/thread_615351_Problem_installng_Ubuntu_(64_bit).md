---
title: "Problem installng Ubuntu (64 bit)"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by ChaosApothecary on 2007-11-17
So I finally built my new computer and had the Ubunut OS installation disk all ready to go-

The comp starts up just fine, and loads the Ubuntu menu- the mobo doesn't recognize my USB keyboard so I can't choose any options...

The countdown gets to zero and the blue bar loads- then nothing- the screen just goes black and nothing happens- I waited 5-6 minutes and nothing appeared to be loading-

I am running the Abit-IP35 Pro mobo with an intel core 2 quad Q6600 processor if that might affect anything.

Also- since my processor can handle 64 bit processes, is there a 64 bit version of Ubuntu or some option I need to change to install it as 64 bit instead of 32 bit?


Thanks for any and all help!

---

### Post by Inxsible on 2007-11-17
> **ChaosApothecary said:**
> Also- since my processor can handle 64 bit processes, is there a 64 bit version of Ubuntu or some option I need to change to install it as 64 bit instead of 32 bit?you definitely need to download the 64 bit version of the OS. apart from that you dont need to do anything else.

---

### Post by ChaosApothecary on 2007-11-17
Ah, my mistake- I had downloaded the 64 bit version already- I just doubled checked it.

Any advice on that blank screen though? Is that part of the normal installation  (and I just need to keep waiting) or does it mean that there is a problem?

The screen doesn't just turn blank, it actually goes into power safe mode- as though it isn't receiving any signal.

---

### Post by Inxsible on 2007-11-17
> **ChaosApothecary said:**
> Ah, my mistake- I had downloaded the 64 bit version already- I just doubled checked it.

Any advice on that blank screen though? Is that part of the normal installation  (and I just need to keep waiting) or does it mean that there is a problem?

The screen doesn't just turn blank, it actually goes into power safe mode- as though it isn't receiving any signal.
your graphics card might not be supported. what card do you have?

you may be able to install it using the alternate cd.

---

### Post by ChaosApothecary on 2007-11-17
evga 8800GT is the video card

---

### Post by Inxsible on 2007-11-17
Thats nvidia right ?

I have seen a bunch of threads with 8800. Try to install using the alternate Cd and see if that works out for you.

Sorry, I couldn't be of much help

---

### Post by rsambuca on 2007-11-17
Yup, you need to install via the alternate CD and then install the nvidia-glx-new drivers from there.

---

### Post by uclalinux on 2007-11-17
You can hit F6 with a keyboard that is supported (ie, a old plug in one PS/2) and remove the quite splash from the command, this will allow you to see that is loading during the boot. I have read other places that the loading bar has not been working for everyone. Also after ubuntu install your keyboard should work just fine. AND use the x64 Ubuntu install.

---

### Post by ChaosApothecary on 2007-11-17
Alternate CD? Any chance for linkage to the download? I'll check around for another keyboard- but I doubt I have one.

---

### Post by Inxsible on 2007-11-17
> **ChaosApothecary said:**
> Alternate CD? Any chance for linkage to the download? I'll check around for another keyboard- but I doubt I have one.Here's the link. Make sure you click the box where it says check here for alternate CD. I am assuming you want ubuntu and not kubuntu or xubuntu

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by ChaosApothecary on 2007-11-17
Alright- I am currently downloading the alternate version of the 64bit ubuntu OS- though I still have not been able to find a keyboard that works on startup (damn USB keyboards =p)

I notice that this alternate CD claims to be a "text-based" install- will i need a usable keyboard for me to use this?

---

### Post by Inxsible on 2007-11-17
> **ChaosApothecary said:**
> I notice that this alternate CD claims to be a "text-based" install- will i need a usable keyboard for me to use this?Most definitely !!!

---

### Post by PmDematagoda on 2007-11-17
It's very strange that the USB keyboard is not working at startup, mine does with no problems. Did the keyboard work previously?

---

### Post by derby007 on 2007-11-17
I did the 64bit alternate install last nite, and it detected my keyboard by asking me to type a few letters, ie. n,r,w, & eventually the £ symbol (after a few wierd symbols) & hense an american-english keyboard.
By the way it wouldnt boot into graphical mode, i had to do a 'cntrl-alt-F1' to get a command prompt, then login, then edit /etc/X11/xorg.conf to get into graphics mode.

---

