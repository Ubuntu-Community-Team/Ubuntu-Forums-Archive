---
title: "PPC Ubuntu Studio possible?"
date: 2008-11-29
forum: Apple Hardware Users
---

### Post by casbahdk on 2008-11-29
Is it possible to upgrade a vanilla Hard Heron PPC install to Ubuntu Studio?

---

### Post by tiresia on 2008-11-29
No, there is no Ubuntu Studio for PPC, neither  for PPC64

---

### Post by mkvnmtr on 2008-11-29
I am not sure just what Ubuntu studio should have but my package manager has a ubuntu desktop and several other things to download. They all look installable. It usually says if I can't install on my machine.

---

### Post by casbahdk on 2008-11-29
> **mkvnmtr said:**
> I am not sure just what Ubuntu studio should have but my package manager has a ubuntu desktop and several other things to download. They all look installable. It usually says if I can't install on my machine.

I believe there are special repositories that need to be added for Ubuntu Studio, but I may be wrong.

---

### Post by casbahdk on 2008-11-29
How many of the following packages are available for the PPC platform? Does anyone know?

[https://wiki.ubuntu.com/UbuntuStudio/PackageList]("UbuntuStudio/PackageList")

I am particularly thinking of the ubuntustudio-audio, ubuntustudio-plugins and ubuntustudio-graphics package groups.

Cheers

---

### Post by mkvnmtr on 2008-11-29
I have no knowledge of Ubuntu studio but when I saw this thread I looked in my package manager and ran a search for ubuntu studio and found several listings. I am on ppc G4 Ibook, have medibuntu enabled and ask to view all aviable software.

---

### Post by casbahdk on 2008-11-29
I tried to install, but got the following errors:

ubuntustudio-audio:
 Depends: mixxx but it is not going to be installed
 Depends: mscore but it is not going to be installed
 Depends: qjackctl but it is not going to be installed

mixxx:
 Depends: libqt4-core but it is not going to be installed
 Depends: libqt4-gui but it is not going to be installed
 Depends: libqt4-qt3support but it is not going to be installed

mscore:
 Depends: libqt4-core but it is not going to be installed
 Depends: libqt4-gui but it is not going to be installed

qjackctl:
 Depends: libqt4-core but it is not going to be installed
 Depends: libqt4-gui but it is not going to be installed

Any idea what went wrong?

---

### Post by mkvnmtr on 2008-11-29
No idea what went wrong. Do you have medibuntu and back ports enabled? I really don't want to try installing because I have no idea what it is. The poster that said it is not for ppc has a lot more experience than me.

---

### Post by hadji457 on 2009-01-04
I installed Ubuntu 8.10 on my mini (G4). Tried to install studio right from synaptic which I have done successfully on x86 platforms many times.
 I think the problem is that most of the studio apps (esp. those that depend on jack) requires linux-rt. I don't think it's available for ppc architecture. 
 That is why I blew off the idea of ppc linux for my needs. Sorry to not have a more positive answer for you.

---

### Post by ghettonerd on 2011-01-04
I see this is an old thread but i wanted to share my experience with fellow PPC users. I am currently running Ubuntu 10.10 on my old school iBook G4 1.2ghz - 1.2ghz ram and as far as my computer goes i was able to download, instal and run the Ubuntu Audio Studio and Plug-Ins. Most of the software (the important stuff, Jack, Ardour, Hydrogen, all the soft synths, sooper looper) works fully and in real time. However, I did notice that my little iBook started to lag with 4 or more synth so im gonna experriment with MintPPC 
P.S. My Aiport Extreme setup was also a breeze in Ubuntu and since MintPPC is based on Debian it should do the trick.

---

### Post by Strangedogs on 2011-11-15
I know this thread is getting a bit long in the tooth but I'm posting anyway.

I currently have a Powermac g5 PPC G5 DP 2.3.  I have 10.5.8 running fine.  I can set a new partition and want to install Ubuntu Studio as my great love is recording and I'm dying to run Ubuntu as a new toy!  What's the BEST build of Ubuntu Studio that will run on a PPC chip?  How do I install it - will it boot from the DVD or CD?  Also will it give me a dual-boot menu to choose what OS I want to use?  Any help would be great as I'm a novice to Linux although I tried out a live CD on my Windows 7 laptop and was liking the new "drug"  ;)  HELP!

I do use Ardour and Mixbus on my Mac and actually enjoy it.  OS X RULZ but I want to experiment with Ubuntu.

---

