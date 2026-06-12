---
title: "Failed to migrate..."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by shriek on 2006-08-13
Ok, this is my 3rd attempt to migrate to ubuntu but failed. The main reason is that I can't get 3D accel to work (at least not easily) with my ATI Radeon Xpress 200M and also even following a guide I couldn't upgrade the kernel (I need the 2.6.17 because aparentely the current version cripled ppp and so I'm getting SLOWWW connections with my 3G/UMTS card-bus).

I know that this is not ubuntu's fault. If I was persistent enough (and had enough time) I should learn myself how to solve all these problems. But the thing is: I passed this learning phase already. I need something that just works with having to mess with so many subtle details.

For some people Linux is a training experience, some thing to develop our caracter. For others (like me) linux is another OS that we would like to use to replace windows. Is not that I'm not willing to learn anything about ubuntu. I just feel that it is impossible for me to get a good enough experience with my computer without having to waste a lot of energy tweaking stuff. I have a Turion64 laptop. All these hardware have at least 6 month. I thought that by now I would have good support with current distros of ubuntu (or anything else) but from what I've been searching it doesn't seem to be the case.

Maybe some of you out there with a similar box could suggest me something that would not require a whole week of tweaking. Maybe not... in that case... my only hope for migrating to *nix OS is to get a Mac or wait for a Google/Yahoo/etc supported Linux.

---

### Post by meng on 2006-08-13
My two cents:

If you wait long enough, Ubuntu will have a new enough kernel for your needs without the need for manual upgrading. (That's not a satisfactory answer, I just feel the need to state the obvious.)

Otherwise look to another distro with the newer kernel (e.g. Zenwalk 2.8 ). Unfortunately, that may require some tweaking to get everything to work (at least in my limited experience).

Myself, I'm not holding my breath waiting for Google Linux.

---

### Post by shriek on 2006-08-13
Hi, thanks for the suggestion. I went to take a look at zenwalk and it seems pretty complete. but... I even tough right now internet through UMTS is the most important thing I need in the short/medium term I really wanted to try XGL/COmpiz.... and I suppose I need GNOME (prefered) or KDE. Zen walk does not use either.

The fact is: this ATI graphic card is really anoying me because it seems that is hard to get any support compared to others (even on windows)...

---

### Post by djsroknrol on 2006-08-13
Shriek;

Why not go for stablity and investigate your options as far as the graphics goes...maybe go with the "ati" driver for a while and change your video card out...

Not having XGL/compiz is not the end of the world and a good possiblity for you in the future...

---

### Post by shriek on 2006-08-13
I know that it might feel like a futile issue to wish to have a working 3D feature what my position is: I should stick to what works (given that I've paid myself for the laptop - it is a laptop so changing the graphic card is not an option) and for now the only OS I can get to have everything working easily is in windows.

I mean, with all the maturity (it has been more than a decade that Linux have been around, and the Open Source movement is even older) Linux still does not have good enough support for troubleless experience for power-users let alone for inexperience computer users. I agree that better support have to be provided by hardware companies but the thruth is: with the high frequency of updates in OSS software it is hard for hardware companies to keep up. Also, the existence of so many standards (in spite of being open standards) in GUIs, window managers, distros etc makes universal hardware support even harder...

Well, these have been all frustration-driven mumbling... it will pass in some weeks... sorry for that :P

---

### Post by nalmeth on 2006-08-13
Hardware support is all the the kernel, and what modules are in the kernel you're using. Extra GUI's are outside that issue. 

'Tis frustrating though, I know. I feel your pain.

What specifically troubled the ATI driver installation? Were you trying to run ATI's .bin file, or trying to use the packaged ubuntu fglrx driver?

And am I correct in assuming the need for the newer kernel was solely for a wireless device?

Have you started your own threads for these problems? Going to another distro may be best after all, but you probably won't find the help as prevalent.

---

### Post by shriek on 2006-08-13
> **nalmeth said:**
> Hardware support is all the the kernel, and what modules are in the kernel you're using. Extra GUI's are outside that issue. 

'Tis frustrating though, I know. I feel your pain.

What specifically troubled the ATI driver installation? Were you trying to run ATI's .bin file, or trying to use the packaged ubuntu fglrx driver?

And am I correct in assuming the need for the newer kernel was solely for a wireless device?

Have you started your own threads for these problems? Going to another distro may be best after all, but you probably won't find the help as prevalent.

I did install ATI drivers through a guide from ATI linux wiki. I used the .run package from ATI and extracted some 3 deb package from that. after this installation I got fglrxinfo display the correct driver information and from ATI config window I expected 3D to be working but I didn't feel any performance boost in windows (the windows did have some minor glitches before I installed it).

then I tried to install xgl following another guide and it trashed my ATI driver installation! (that was after my 3rd ubuntu installation in one day) so I just surrendered. Why? because in the same day I tried to update the kernel (and yes, kernel update is only to try to get my UMTS connection working properly, not wifi) and even following the guide, without any error (at least aparentely) I could boot the OS...something related to VFS... I had the error written somewhere.

After that I posted this thread in hope of getting some enlighment with you all who are spending time reading my frustrations... (thanks for that) while I reinstalled windows because I have some project I need to accomplish this days... and I need internet.

---

### Post by nalmeth on 2006-08-13
> then I tried to install xgl following another guide and it trashed my ATI driver installation! (that was after my 3rd ubuntu installation in one day) so I just surrendered. Why? because in the same day I tried to update the kernel (and yes, kernel update is only to try to get my UMTS connection working properly, not wifi) and even following the guide, without any error (at least aparentely) I could boot the OS...something related to VFS... I had the error written somewhere.
Somewhere in here might lie the problem.. Were the restricted kernel modules installed with the kernel update? If not, it would likely bork your ATI driver setup. Unless you're sure it was XGL..

---

