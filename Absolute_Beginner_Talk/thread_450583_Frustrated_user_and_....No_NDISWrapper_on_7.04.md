---
title: "Frustrated user and ....No NDISWrapper on 7.04?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by humason on 2007-05-21
Can't help but continuing to be frustrated with the complexity of a Linux install...

I order the Ubuntu CD from Ubuntu, 5 computers later, one amazingly installs...the 4 others just sit with black screen for hours...no messages as to why, just nothing...

The 2GHz machine that it actually gets installed on has no wireless support...need to install Ndiswrapper...Fine, follow all of the directions(on the web)...Figure out that Ndiswrapper is not automatically installed, nothing to check in the Synaptic Package Manager, doesn't show up on the CLI. The CD has no Ndiswrapper to install as a package....and the solution is...download it from the internet and then then install it...This would be fine but it is a network card driver, can't get the internet access to the computer to install it....I just can't believe that so much energy is put into a "slick" OS when one of the most key components is totally overlooked....

So many people want to get away from Windows...but situations like this, time and time again, to say the least is discouraging to technically minded people but make it inevitably impossible to the non-technically minded person....I was really hoping that Ubuntu bridged this hurdle...

---

### Post by Cypher on 2007-05-21
Linux has come a very long way from it's very humble beginnings and Ubuntu is taking it much farther than any other distro has. But as you've found out there are still a few gaps to be filled. I'm certain that Gutsy Gibbon and future releases will plug those up and make it even easier to get Ubuntu up and running even for the most non-technical person.

However, even if you manage to get Linux up and running, there is a level of technical know-how that is needed to manage a Linux machine. Ignoring all the marketing you might have read, Linux is not trying to convert Windows/GUI/point-and-click people to Linux. Linux is out there doing it's own thing offering an alternative that you've got to want to use.

Now, Linux might be a lot of things to many people, but it certainly isn't the OS for everyone. There are, frankly, those who are much better off with Windows..

Having said all that..as you have access to Internet on one of your machines, download the ndiswrapper package onto a USB flash drive and take it to the machine with Ubuntu.

The other machines you have, how far do they get in the install? Are you using the Live CD? Feisty Fawn? What are the specs of those machines?

---

### Post by humason on 2007-05-21
Hello Cypher, I appreciate your response and I certainly don't want to sound like I am bitching or unappreciative of Ubuntu's efforts and obvious headway.

Also, I do understand that *NIX is not Windows (thankfully) and have about 10-years of IT working experience with BSD, Cisco, programming, etc. I guess what happens is that I see so much potential for people to really catch on to the power and beauty of *NIX (and specifically Ubuntu) that when something silly like a key piece of software that is no where to be found on a CD that ships worldwide for something that is such a vital component such as a standard/generic network driver, I become baffled.

As far as my situation goes. I do not have a USB memory stick (and is not stated as something that is needed to install Ubuntu under the Main install docs pages). I'll download Ndiswrapper to floppy.

The version that I am running is 7.04 LiveCD. The computers that I tried to install it on: 800Mhz Dell Inspiron, 800Mhz Dell Dimension, 500Mhz AMD with with Unix compatible Peripheries and BSD installed. All of these computers get to the boot menu, click to install, CD spins up and just sits spinning with a black screen, a cursor a cursor at the top left corner and a whole lot of nothing else indefinitely. I am used to seeing messages logged to the screen via the bootup/install process, but with Ubuntu everything is hidden? Is there a way around this?

Thanks for your time,
Scott Humason.

---

### Post by icechen1 on 2007-05-21
> **humason said:**
> I am used to seeing messages logged to the screen via the bootup/install process, but with Ubuntu everything is hidden? Is there a way around this?

Thanks for your time,
Scott Humason.

I think during the live cd menu,press F6(i think?) and remove splash and quiet line in it.

---

### Post by Cypher on 2007-05-21
> **icechen1 said:**
> I think during the live cd menu,press F6(i think?) and remove splash and quiet line in it.
In addition to doing this, judging by the speed of the machines, do you have more than 256MB ram on each of those machines? The LiveCD desktop needs at least that much if not more to perform. You might consider XUbuntu if memory is tight and/or the Alternate Installer which uses text-mode..

---

### Post by Cypher on 2007-05-21
> **humason said:**
> Hello Cypher, I appreciate your response and I certainly don't want to sound like I am bitching or unappreciative of Ubuntu's efforts and obvious headway.

Also, I do understand that *NIX is not Windows (thankfully) and have about 10-years of IT working experience with BSD, Cisco, programming, etc. I guess what happens is that I see so much potential for people to really catch on to the power and beauty of *NIX (and specifically Ubuntu) that when something silly like a key piece of software that is no where to be found on a CD that ships worldwide for something that is such a vital component such as a standard/generic network driver, I become baffled.

As far as my situation goes. I do not have a USB memory stick (and is not stated as something that is needed to install Ubuntu under the Main install docs pages). I'll download Ndiswrapper to floppy.

The version that I am running is 7.04 LiveCD. The computers that I tried to install it on: 800Mhz Dell Inspiron, 800Mhz Dell Dimension, 500Mhz AMD with with Unix compatible Peripheries and BSD installed. All of these computers get to the boot menu, click to install, CD spins up and just sits spinning with a black screen, a cursor a cursor at the top left corner and a whole lot of nothing else indefinitely. I am used to seeing messages logged to the screen via the bootup/install process, but with Ubuntu everything is hidden? Is there a way around this?

Thanks for your time,
Scott Humason.

Scott,

I understand that you weren't griping and as someone who's familiar with Unix in general it is good get your perspective with where Ubuntu needs to be. Also, I think wireless networking has become a very prevalent thing recently and I'd be absolutely shocked if there wasn't better support for it in Gutsy Gibbon.

---

### Post by humason on 2007-05-21
I did check the system requirements and caught that 256 Mb is a minimum. All of my systems have 384Mb except the laptop...So this brings up the question, is Xbuntu a subset of the LiveCD? I don't see it on the CD so I presume that it has to be downloaded separately? Also does Xbuntu have the same driver support as what comes on the LiveCD?

PS. trying fd and fdutils but also installed? A directory search reveals that they exist. When I go to run fd -> fdclone install line comes up and says that Universe mode needs to be enabled. Any ideas?? Note that I am trying to use a DOS formated floppy and is not mounting...

Thanks for everyones input and support,

---

