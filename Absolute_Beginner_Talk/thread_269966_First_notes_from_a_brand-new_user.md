---
title: "First notes from a brand-new user"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by VoodooDali on 2006-10-02
Hello all:

I finally got Ubuntu working after several days, and I have to say...  this is not encouraging. I cannot use it. :-? 

First, I think that *much* more coulda/shoulda been said about the incompatibility of the NTFS file system with Linux. I spent two days trying to troubleshoot a blank screen during the LiveCD install, before sniffing that one out. ](*,)  Eventually I got to a desktop. Nicely and smartly arranged, and visually stunning. But...

1. Everything happens so slow as to be virtually indistinguishable from a system freeze. Every last click takes 10-20 seconds to register, and every application takes multiple minutes to open.

2. Got a message during boot:

[FONT="Fixedsys"][17179841.492000] hw_random: RNG not detected[/FONT]

This sounds like a reference to the Random Number Generator.

3. Got another message after reaching the desktop:

[FONT="Fixedsys"]Internal error: Failed to initialize HAL![/FONT]

Not a clue what this is - if it's in any way related to performance, I definitely wanna fix it pronto. :-? 

4. Cannot connect to the Internet at all. It seems to recognize my wireless port at eth1. It's active. It found my access point and filled in the ESSID for me; I just added the WEP key. But then, nothing.

There are lots of other issues, such as getting my screen resolution fixed. But honestly, these are peanuts to the system performance and my Internet connection. Without these, it just isn't worth it to continue. :( 

My setup:

Alienware Sentia series laptop
. Pentium M processor, 2.0 GHz
. 2.0 GB memory
. Intel "Extreme Graphics" (whatta misnomer!), using Intel 82852/82855 GM/GME chipset
. Widescreen display, 1280x800 resolution, 60 Hz, 32-bit color
. Intel Pro/Wireless 2200BG (internal)
. Dual-booted with WinXP Pro SP2

If I've omitted anything important, please just let me know and I'll gladly dig up the info. Thanks in advance for any tips you can offer.

---

### Post by Marsolin on 2006-10-02
I don't see anything strange with your hardware, but the HAL is the interface between the hardware and the rest of the software, so that's probably why everything is so slow. You could try disabling devices in BIOS to get to a barebones system and see if performance of the LiveCD is any better. If it is then you could reenable the devices one at a time to discover the incompatibile.

I haven't run into this problem myself so I don't have any more concrete ideas. Hopefully someone else will have experience with it.

---

### Post by VoodooDali on 2006-10-02
Eep :shock: disabling devices in BIOS sounds iffy as all heck.

Would this be equivalent to starting Ubuntu in Safe Mode? 'Cause that I think I could manage without a panic attack. :-k 

Thanks

---

### Post by podunk on 2006-10-02
Maybe write ailenware and ask them what flavor of Linux they recommend? Ask them if they have any drivers handy? :-)

---

### Post by firebirdworks on 2006-10-02
Humm...It sounds like your system is good enought to run linux.  That "equilivent" to a safe mode sounds good, but if you thought it was slow before...

---

### Post by K.Mandla on 2006-10-02
> **VoodooDali said:**
> First, I think that *much* more coulda/shoulda been said about the incompatibility of the NTFS file system with Linux. 
True, it should probably be mentioned early on that NTFS doesn't play well with Linux, but as of late it has become more commonplace. No doubt you've seen [this]("http://www.ubuntuforums.org/showthread.php?t=217009"). I can't vouch for it because I gave up on Windows some time ago, but it looks promising.

> **VoodooDali said:**
> I spent two days trying to troubleshoot a blank screen during the LiveCD install
Interesting. Was that during the installation off the live CD? I've gotten the black-screen-plus-small-white-box when installing from the alternate/install CD to Intel 82855 machines, but I didn't know it could happen with the live CD too.

> **VoodooDali said:**
> 1. Everything happens so slow as to be virtually indistinguishable from a system freeze. Every last click takes 10-20 seconds to register, and every application takes multiple minutes to open.
That's a real problem. With your hardware, it should be very snappy. 

> **VoodooDali said:**
> 2. Got a message during boot:

[FONT="Fixedsys"][17179841.492000] hw_random: RNG not detected[/FONT]

This sounds like a reference to the Random Number Generator.

I think most people get that message if they have Intel chipsets in their machines, regardless of whether they're using onboard graphics or not. Either way, it seems safe enough to disregard (I get it on four machines or so, and it's never proven problematic.) You might learn more about it [here]("http://home.comcast.net/~andrex/hardware-RNG/index.html").

> **VoodooDali said:**
> 3. Got another message after reaching the desktop:

[FONT="Fixedsys"]Internal error: Failed to initialize HAL![/FONT]

Not a clue what this is - if it's in any way related to performance, I definitely wanna fix it pronto. :-? 

Definitely. As someone mentioned, HAL acts as a liaison between the guts of your machine and the software that's running on it. You're probably right if you suspect it has some bearing on the poor performance.
> **VoodooDali said:**
> 4. Cannot connect to the Internet at all. It seems to recognize my wireless port at eth1. It's active. It found my access point and filled in the ESSID for me; I just added the WEP key. But then, nothing.
That's unusual, because I also had a 2200BG in an XPS M170 about a year ago, and Ubuntu (then version 5.10) seized it immediately and had it up and running before the installer was ever finished.

You've probably gotten lots of suggestions, but if I could give any advice, I'd make sure the settings in your /etc/network/interfaces file were correct, that iwconfig and ifconfig both show your hardware there, and finally to make sure that the key you gave it was correct. If you have other posts going on that topic, could you give a link? I'd like to read more about it, since mine was what drew me to Ubuntu in the first place.

> **VoodooDali said:**
> There are lots of other issues, such as getting my screen resolution fixed. 
I'm assuming you've already tried editing the xorg.conf file to add the resolution you want. Aside from that, make sure it shows the i810 (or another, if there's a more appropriate one) driver in use, and not that darned vesa one.

Again, if you have other posts on these subjects, could you link to them? We'll try and convince you to stick with us, but there are probably too many things wrong here to tackle them in one thread. :D

---

### Post by The Geoff on 2006-10-02
This may sound really stupid, but I've been through a lot of stupid mistakes getting my system (which I now love :) ) up and running...

You have actually installed on to the hard drive haven't you?  If it's still running from the CD then everything will be *really* slow and you'll have trouble changing any root settings, ie getting wirelesss adapters to work.

---

### Post by VoodooDali on 2006-10-03
First off, thanks to everyone for their interest in helping the noobs along. That goes a long way with me, and it does credit to the U community.

After a lot of good advice, I think this is the order in which I'll attack these problems:

[LIST=1]
[*]Troubleshoot the wireless - I can even monitor my signal strength at this point, so I suspect we're 99% there. Once that's done we'll be able to tackle the rest much more expediently.

[*]Remove the hw_random process.

[*]Bone up on this HAL thing and what's making it choke. Others' past experience seems to suggest a flaky DVD/CD-RW device, but mine seems to be detected correctly.

[*]Re-evaluate performance at this time.
[/LIST]

So thanks - we're nowhere near done with this thread, and I'll do my best to post reference links when/wherever I find solutions.

--Voo

---

### Post by VoodooDali on 2006-10-03
> **podunk said:**
> Maybe write ailenware and ask them what flavor of Linux they recommend? Ask them if they have any drivers handy? :-)

I would, but I've been led to understand that the Alienware hacks don't speak any language other than Windows. Having dealt with them myself, I strongly suspect they're just call-center inmates, reading from a computer-aided troubleshooting script. :roll:

---

### Post by VoodooDali on 2006-10-03
> **K.Mandla said:**
>  (...)I gave up on Windows some time ago (...)
I admit I find that *very* encouraging.

> Interesting. Was that during the installation off the live CD?
Actually it was happening during all attempts to boot from the LiveCD. Couldn't even get to the point of installing.

> HAL acts as a liaison between the guts of your machine and the software that's running on it.
Hm. Sounds like debugging that puppy is gonna be Job #1, once I get my Internet connection re-established.

> You've probably gotten lots of suggestions, but if I could give any advice, I'd make sure the settings in your /etc/network/interfaces file were correct, that iwconfig and ifconfig both show your hardware there, and finally to make sure that the key you gave it was correct.
I'll give that a shot, today. As I mentioned elsewhere, it's even at the point where I can use a docklet to monitor my signal strength.

> I'm assuming you've already tried editing the xorg.conf file to add the resolution you want.
Since my screen is at least functional, that's further down the priority list. ;) 

> Again, if you have other posts on these subjects, could you link to them?
Will do, and thanks! :biggrin:

---

### Post by Gary42 on 2006-10-03
Hi...

I'm really sorry if I'm way off but I just tried the Live CD and had a similar problem with my ethernet cable connection (by the way, did you try a cable?)...

After a little bit of trial an error (I'm a complete novice) I found an icon at the top right that allowed my to set "eth1" as my internet connection instead of "loc" (or something similar).

Again, sorry if this is no help...

---

### Post by VoodooDali on 2006-10-04
Well now:

Greetings from my first online session with U...  :mrgreen:  Which, of course, means that I've repaired my wireless connection.

The problem turned out to be with the entry of my WEP key. I should have left the original format (Hexadecimal) alone. However, I didn't think this was correct, so I selected ASCII instead.

So, Note to Self: just because a string of numbers doesn't include any characters A/a through F/f, doesn't mean it isn't in Hex. :rolleyes: 

There is still *so* much work to do, but at least now the work may begin in earnest. :cool: 

Thanks to all for your help.  --Voo

---

