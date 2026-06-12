---
title: "Ubuntu 12.04 on iMac G4"
date: 2012-07-11
forum: Apple Hardware Users
---

### Post by surenot on 2012-07-11
I have an old G4 iMac that I would like to run Ubuntu on, unfortunately it seems there is a problem with the graphics driver, because whenever I try to boot the live cd, the top half the screen shows nothing but white while the bottom half is nothing but black.  I thought it might be an issue with the RAM, so I installed via a text installer.  But even when I try to boot into it after it's installed, it does the same thing.  I tried booting with video=ofonly, but it doesn't help.  I know it's possible, because my friend had someone install it on his computer (same model), and it appears to run flawlessly.  I'm not sure what the problem is here.

---

### Post by 2blue on 2012-07-11
If your iMac and Ubuntu version is the exact same model as your friend's I would double check the CD if you haven't already, or even burn a new one. If you have the same downlaod you can still do a MD5 sum file check, and remember to burn at lowest speed if you burn a new CD. 

Is iMac G4 a powerpc?  Then you might have to go for lubuntu, I think main Ubuntu is not that easy to run on those. Lubuntu have an indivudual build for powerpc. [Link]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-powerpc.iso") for lubuntu ppc download.

Edit; I took a look at the iMac G4 specs, and unless it's a later one with memory upgrade, I doubt there is even a chance to install full Ubuntu. Lubuntu seems to be the best choice, it's really cleverly made, and the only really light version of the buntus.

---

### Post by Easy Limits on 2012-07-11
I could only get my iMac G4 to load Ubuntu 8.04.  Any later Ubuntus and I had all kinds of problems.

---

### Post by sdgalbo on 2012-07-12
Hi Easy Limits,
I am having the same exact problem  with my G4 imac. I would disagree with 2blue, that you cannot install 12.04 on a ppc. I am currently running 12.04 with Unity 2D on a G4 ibook. It installed flawlessly and runs perfectly-- except I cannot get a battery icon to show up. It's not fast, but it's not slow either!

My iMac has basically the same resources as the ibook - 1.2 Gb ram and a 1.2 GHz processor. I believe you are correct, that the video card is the culprit. It does the same thing for me--your symptoms exactly. I would be interested in seeing if anyone has a solution as well.

For the time being, I installed Lubuntu 12.04 and it works pretty well. I do have a few issues with the cdrom drive and playing media, but haven't had the time to work on it. I don't think the issues are insurmountable. But I'd really like to see if anyone can come up with a solution for Ubundu 12.04 though. I really like the Unity 2D interface with these old machines.

---

### Post by 2blue on 2012-07-13
,

---

### Post by 2blue on 2012-07-13
I have managed to insall lubuntu ppc 12.04 on an iBook G4. It now boots fine, connects to wired and wireless network all fine. All updates seem to have run all right too. I installed libre office and it works. Battery icon shows fine here. 

I still have issues with some video streams, and java doesn't work at all, no sound at all, but I will get to those in time.

---

### Post by phillw on 2012-07-13
Great that lubuntu 12.04 installed. We are desperately short of PPC testers, if you or any friends can spare the time / kit please do lend a hand![ Lubuntu Testing ](https://wiki.ubuntu.com/Lubuntu/Testing)is where the team lives.

From the alpha 2 release, it seems that lubuntu is the last hope for PPC's (There is a killer bug on the alternate install at the moment, but desktop seems to install okay).

Regards,

Phill.

---

