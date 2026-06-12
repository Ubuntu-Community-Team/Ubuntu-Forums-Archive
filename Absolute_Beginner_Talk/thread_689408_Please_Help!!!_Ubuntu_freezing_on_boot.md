---
title: "Please Help!!! Ubuntu freezing on boot"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by bagguley on 2008-02-06
Ive just got a second hand desktop from a friend. It had Vista on, which I naturally got rid of. At the time the only disk I had available was 6.10 Live disk. Booted, installed with duel boot (before discovering vista duel boot problems). Ubuntu worked brilliantly! Vista didnt (not a problem - wasnt interested anyway).

I then downloaded the 7.10 alternative disk (I was just curious- I had never used an alternative disk) and installed. Again worked fine untill I started downloading updates. Updates downloaded eventually (avoid virgin media) and the install started. Halfway through everything froze - I couldnt even reboot X.

Next step was to hard crash and reboot. It froze with a black screen during boot. So next plan was to use the rescue option on the alternative disk. Froze again.

What I now think I need to do (please correct me if im wrong) is do a low level format of the hard drive and reinstall with a live disk (slowly downloading).

The problem being is that I dont know what to use. Can anyone help me at all? Please!!!!!

---

### Post by jken146 on 2008-02-06
As this is a first time install of Ubuntu on that machine (you have nothing to lose), I would:

1.  Run the integrity check on the 7.10 install CD you have.

2.  If it passes, install again from scratch, making sure that the hard disk gets formatted in the process (the installer will do this for you).

3.  Download your updates again from a reliable mirror.

---

### Post by bagguley on 2008-02-06
Now its frozen on live cd boot. Any ideas?

---

### Post by jken146 on 2008-02-06
What's wrong with a the live CD boot?  Did you verify the md5sum of the ISO you downloaded?  Did you burn the CD slowly?  Did you run the CD integrity check?

---

### Post by Michl on 2008-02-06
I've just been suffering through this doing a fresh install of gutsy.  One thing to
keep in mind is that sometimes the install from a live cd takes a very long time.
It will hang at 15% for more than an hour and then continue.  However,  it
has also frozen on me -- I waited for 8 hours before I gave up.  Twice.  Nothing
wrong with the CD.  One hypothesis I have is that it had a hard time with the
/home partition.

What is weird is that when it freezes, I force power off, reboot, and the old grub
and everything else is there.  So it freezes early just trying to read.  So
I am guessing (blindly) that it is better not to do the manual partition and
let the installer do it.

Someone suggested that enable a network connection before installing
even if you are installing from a live cd.

---

### Post by bagguley on 2008-02-06
Its not just one live cd that wont boot, ive tried three.

---

### Post by bagguley on 2008-02-06
Ive just ried the alternative disk again. It seems to be freezing on Detecting network hardware

---

### Post by jken146 on 2008-02-06
At what stage of the Live CD process does it fail?  Do you see the black screen with the Ubuntu logo and the boot options?

---

### Post by bagguley on 2008-02-06
Cool, how do you enable a network connection?

---

### Post by bagguley on 2008-02-06
Yep, I get the boot options up and then select either boot/install or boot in safe mode. I then get the logo and the bar that winds from side to side for a while. After that the line starts filling up from the left hand side. It will get to three bars full and then stop.

---

### Post by jken146 on 2008-02-06
You plug in a network cable or connect to your wireless router.  I'm not sure you need this in any case, and I'm certain that with a working CD you can install Ubuntu with just the CD.

---

### Post by bagguley on 2008-02-06
Yeah, it can (Ive done it before) Ive now fried a fed core disk. Thats not working either!

---

### Post by jken146 on 2008-02-06
Can you post some specs please?  In particular, what is your graphics card and how much RAM have you got?

---

### Post by bagguley on 2008-02-06
So, Ive managed to get vista reinstalled (to my disgust) but still the same problem.

Specs as follows:

Intel Pentium 4 CPU 3.40GHz
1 GB ram
Radion X600 series

Help....please!!!!

---

### Post by lespaul_rentals on 2008-02-06
Burn your disks slowly, 8x tops.  Try using Ubuntu 7.04, as 7.10 was buggy for me.

---

### Post by bagguley on 2008-02-06
Yeah, Ive tried 6.10 but still the same!

---

### Post by bagguley on 2008-02-06
Cheers everyone, gonna give wubi a go. Will report back.

---

### Post by bagguley on 2008-02-06
OK, I used Unetbootin in the end. Again no luck. 

Stuck at 25.122486] Prism54:pci_set_mwi(pdev) succeeded

Anyone, please..............dont leave with the horrible vista monster!

---

### Post by bagguley on 2008-02-06
Anyone???

---

### Post by borris.morris on 2008-02-06
Well, sounds like you're getting kernel panics to me. try taking out the hard drive and booting from the live cd.

---

### Post by bagguley on 2008-02-07
Cheers Borris.

Ive not yet had chance to try this out due to thirteen hour day at work, but am planning to try this tomorrow afternoon.

My only question is, if this works what would my next move be? Should I consider a low level format or do I need a new HD?

---

### Post by pieisgood4589 on 2008-02-07
Low-level format. Never give up on the HD! :lolflag:

Mine's over 39 years old. It was handed down from my dad- it's only 20gb, but works like a charm!:popcorn:

---

### Post by bagguley on 2008-02-07
I dont suppose you can suggest software to perform a low level format?

---

### Post by borris.morris on 2008-02-07
fdisk from the win 98 startup disk?

---

### Post by bagguley on 2008-02-10
Ive tried everything I can think of now. The only luck I had was to low level format my hard drive - The live disk then booted up (great........) then froze on reboot. Tried low level format and alternative disk - wouldnt install (froze at the same point). Then tried windows install followed by low level format followed by alternative install. Wouldnt work - froze at the same point. Final attempt was open SUSe, installed but froze (something todo with ACPI).

So in short my desktop is defying the gods and doing the unheard - running windows but refusing to linux....... The world is upside-down!

---

