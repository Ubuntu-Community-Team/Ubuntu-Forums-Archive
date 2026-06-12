---
title: "[SOLVED] Can't believe it"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ilikecoffee on 2007-11-15
Little help needed. maybe a lot.

I'm having trouble with installing Ubuntu. Seems like a great system. My friend said to check it out because it's something I could get into, however, I'm having nothing but problems.

Kinda lengthy, so bear with me and feel free to ask if I'm unclear about anything...

I put together a system using:
Pentium4 3.0 Ghz
Don't know Motherboard (let's assume generic, it has built in Video, Audio, Ethernet, 4 USB, 3 PCI and an open AGP slot)
512MB RAM
160 GB HD

Seems pretty standard, but I couldn't install 7.1. I found 7.04 off CNET/Downloads, but couldn't install that either (both attempts left the "loading bar" stalled at about 80%)

So, I tried 6.0 - BINGO! Hey, Ubuntu looks great, but I had to connect to the internet to get updates. Connecting via the ethernet card is physically difficult (Comp is in garage). It seems 6.0 doesn't come with what I need for my Airlink 101 wireless card. After wasting two weeks trying all sorts of remedies, my friend suggested a fresh/good download of 7.1 and a proper burn of the CD.

Now I have 5 copies of 7.1, 2 copies of 7.04, a copy of Kubuntu, a copy of the 7.1 Alt CD and a copy of the 6.0 Alt CD.

None of these install.

So, I tried it on my main computer. This other computer has:

AMD 4600 X2
ABIT motherboard
2 GB RAM
320 HD
BFG Video 256MB
blah, blah, blah

Tried the 64 version of 6.1, the 64 version of 7.1 and the 64 7.1 Alt CD.

nuthin.

Is this a joke? What is happening that I can't install Ubuntu on anything?

I've downloaded from 3 different machines, Used different sources, I've done the MD5 checksum, I've downloaded and burned from Infra-recorder, also tried Deep-Burner. I've looked through installation guides and checked the forums (seems like Ubuntu issues are like noses, everybody's is unique). I've done CD checks, memory tests, OEM installs...

The only thing I can load is 6.0 and when I try to upgrade anything some error pops up referring to "lib6, dev, blah, blah, you suck and/or are stupid go back to windows, noob" ) My floor is covered in Ubuntu copies and the hair that I've been pulling out. 

In all seriousness, I need some advice. I'm at my wits end.

Thanks in advance for following this and any help you can offer.

---

### Post by Paul820 on 2007-11-15
At what speed are you burning the disks? A speed of 4x or less will greatly reduce any errors that you are getting.

---

### Post by Dr Small on 2007-11-15
I always burn at 1x or less. May take a little longer, but I have never gotten any errors ;)

---

### Post by Duck2006 on 2007-11-15
Are they burnt on a cd-r or cd-w/r or dvd-r or dvd+r or dvd w/r?

---

### Post by ilikecoffee on 2007-11-15
Well after reading the install guide several times I thought 4x would be good.
I chose 4x and even 2x and lastly 1x. When it was burning, however, each time it changed the actual burn speed to around 16x. Once it changed to 8x on my machine here at work.
All the CD's checked out fine on md5 check and CD check. Is there some significant code that would be missed on every version so that it would look normal using "live CD", but each CD would hang on the same spot on installation?

---

### Post by rustybronco on 2007-11-15
one suggestion, remove the wireless card and try the install again.

---

### Post by ilikecoffee on 2007-11-15
> **Duck2006 said:**
> Are they burnt on a cd-r or cd-w/r or dvd-r or dvd+r or dvd w/r?

Burnt using cd-r. The computer I'm installing it onto doesn't have a DVD player

---

### Post by Paul820 on 2007-11-15
The 7.10 version sometimes get stuck when it is trying to configure apt if you have no internet connection at that time, you can skip it and carry on with the install.

---

### Post by ilikecoffee on 2007-11-15
> **rustybronco said:**
> one suggestion, remove the wireless card and try the install again.

Worth a shot. Why would that affect an install? I thought 7.1 was supposed to have more features including wireless card support.

---

### Post by rustybronco on 2007-11-15
> **ilikecoffee said:**
> Worth a shot. Why would that affect an install? I thought 7.1 was supposed to have more features including wireless card support.

> The 7.10 version sometimes get stuck when it is trying to configure apt if you have no internet connection at that time, you can skip it and carry on with the install.  it stops at trying to get the updates because of no internet connection.
 not all cards are supported, we'll help you on that also, if you need it.
I assume the live cd worked fine? you could try out the wireless settings (essid, password, ect. ), then click install.

---

### Post by ilikecoffee on 2007-11-15
Yeah, the Live CD was great! Made me want to install it. I think the whole "hard" internet connection may be the hic-up. I'll try connecting using the Ethernet connected to the router.

Is that it? Could it by anything else? I just don't want to re-post unless I've tried everything.

---

### Post by rustybronco on 2007-11-15
I checked your other posts and your chipset is a rtl-8185
so this post may help with your wireless issues. [http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

---

### Post by rustybronco on 2007-11-15
> **ilikecoffee said:**
> Yeah, the Live CD was great! Made me want to install it. I think the whole "hard" internet connection may be the hic-up. I'll try connecting using the Ethernet connected to the router.

Is that it? Could it by anything else?  I doubt it.

---

### Post by ilikecoffee on 2007-11-15
Just remembered another quirky thing.

At the moment it hangs, i.e. 80%, the floppy disk light comes on. I tried to fool the computer by turning off the floppy in BIOS, changing boot settings, but it still hangs. Changed the floppy disk settings back, put in blank floppy (yes I still had one), still hangs.

Don't know if it's related to Ubuntu having to be hard-wired to the internet with all wireless devices un-installed.

Why would the light come on and just hang?

---

### Post by rustybronco on 2007-11-15
> **ilikecoffee said:**
> Just remembered another quirky thing.

At the moment it hangs, i.e. 80%, the floppy disk light comes on. I tried to fool the computer by turning off the floppy in BIOS, changing boot settings, but it still hangs. Changed the floppy disk settings back, put in blank floppy (yes I still had one), still hangs.

Don't know if it's related to Ubuntu having to be hard-wired to the internet with all wireless devices un-installed.

Why would the light come on and just hang? I saw a post about hangs on floppy IIRC. or it could be a cableing/bad floppy drive problem, double check that cd-rom/ floppy drive/ jumper set up, then if necessary disconnect the floppy drive and see what's up.

---

### Post by roaldz on 2007-11-15
You could try to install Ubuntu with Wubi, this could give you a better sight on what you need to do for a real installation. Wubi uses an alternate install cd iso, which it downloads and uses without having to burn it to a CDRW. It installs ubuntu in a file, which you can choose to boot from in the windows boot loader. I must warn you that it could be MUCH slower in disk read/write performance, but I think it´s not meant for ¨real¨ use. Remember, you´ll have to install windows first ](*,)

[http://wubi-installer.org/](http://wubi-installer.org/)

@the floppy thing:

I´ve had that problem before, and wubi did work on the machine. What also worked is putting a hard drive with ubuntu installed in that computer. Now it run´s like a charm:)

Greetz,

Roald

---

### Post by steve.horsley on 2007-11-15
There are some boot options you can try like nopci, nolapic (or something like that) which may help - they turn off some power management which may be having problems. Press F1 at the boot menu to see the options.

---

### Post by ilikecoffee on 2007-11-17
just a follow up.
I connected using the Ethernet interface (LAN line). Installed fine.
I took out the wireless card and installed from live CD desktop. I'm writing from the machine. 
Next step is to get the wireless card working.
Thanks for everyone's help!

---

