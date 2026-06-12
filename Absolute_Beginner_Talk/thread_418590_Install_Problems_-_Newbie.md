---
title: "Install Problems - Newbie"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by DeathWarden on 2007-04-22
Ok I have tried Kubuntu, Ubuntu, and even Debian and I get the same problems.

1.  I download the iso file from the sites listed. I get the i386 version for my Dell 2350, P4 2.5ghz, 1gb ram, 80gb HD machine. 

2. I use Infrarecorder to burn the image on a cd with another computer, test it with md5sum and it comes back fine. 

3. Pop the cd into my P4 and reboot, with the boot sequence already set to where it reads that dvd rom first.

4. Ubuntu loads to a screen that has some options like 'start and install' 'check cd' 'memory test'. I hit 'start and install'

5. Ubuntu install screen hops up with a bar that slowly starts to fill. I get text at the bottom that says 'configuring x'.

6. Screen goes black except for blinking underline cursor. Then things like 'Checking restricted drivers' pop up and then it has [ok] on the other side of the screen on the same line.

7. I get a spam of text that scrolls up from the bottom with what I assume is different files it is trying to install and it goes by too quickly to even read.

8. Stops at something called error - kernel not sync

I have had this, and then another install I tried had a different error with something like 'agp get'. Please help as a friend of mine has had me try everything he knows and I want to try out Linux. The computer has windows xp home sp2 installed on it as well. Thanks

---

### Post by DeathWarden on 2007-04-22
Anyone know what to do?

---

### Post by hyper_ch on 2007-04-22
Have you done a cd check?

---

### Post by DeathWarden on 2007-04-22
Yes on each one, all come back fine. If I had another machine on which I wanted Linux I would try it there, but I only have the old P4 and this one I'm on atm which has vista and which I dont want Linux on.


 There isnt something stupid with dell bios that doesnt like anything but windows or something is there?

---

### Post by hyper_ch on 2007-04-22
Have you tried Feisty or Edgy?

---

### Post by DeathWarden on 2007-04-22
Both in fact, and they all give similar errors. Debian gives an error where it says it cant tell what my cd drives are, though I do not know if that is related to k/ubuntu installs.

---

### Post by hyper_ch on 2007-04-23
Did you also try the alternate install cd?

What video card have you got?

---

### Post by RickThorpe2006 on 2007-04-23
I haven't seen the error messages you report on my 2350, but the integrated graphics in the 2350 combined with outdated Dell BIOS seem to give the installer fits.  Try the following (some of which may be redundant but the combo worked for me -- ymmv):  Use F4 in the installer screen to change resolution from VGA to 640 x 480, use F6 (additional options) and replace option "xforcevesa" with "lowres", then begin install in safe graphics mode.   Assuming this fixes the problem on install, try editing /boot/grub/menu.lst to add "lowres" at the end of the vmlinuz line.

Again, take all of the above with a grain of salt, as I am no expert -- this worked for me, but it's the result of trial and error and may not work with your machine.

---

### Post by stalkingwolf on 2007-04-23
I have heard that there exists a beast which I hAVE NEVER ENCOUNTERED.  This beast is a M/B that
is not compatible with Linux.  You might be in the presence of such a legendary  beast.

---

### Post by thefoolisme on 2007-04-23
Well, I don't think it's a "Dell doesn't like Linux" error, because Dell is actually shipping PCs with Linux now.  

Two things:  1.  What speed did you burn the ISO at?  The recommended speed is 4x.  I managed to get away with 12x, but if you burned it at the maximum speed, then you probably have issues.  
2.  You said you ran the checksum check, but did you actually run the "Check this disk for errors" check in the boot menu options?  It checks the actual burn to verify that there are no errors.

---

### Post by Terl on 2007-04-23
I did have a Dell 2400 with similar specs to the OP's.  It did not like the Ubuntu version at the time (Breezy Badger-always said it had some issue with fonts) but I could install Debian, Fedora, Slackware and others without a problem.  Somewhere on the live cd version something isn't configuring correctly.  Try some of Rick's suggestions above.

You may want to also check the Dell site and see if there are any BIOS updates for the pc.  Their support section is easy to navigate and will be fast, especially if you enter your service tag number.

Also, what type of video card are you using?

---

### Post by pppetter on 2007-04-23
Try installing with the Alternate CD instead, since it won't boot up Ubuntu first. It's a Text based install instead.

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by SikEnCide on 2007-04-23
it porbably is becuase your burned the image too fast i made that mistake. i burned an image for my dad to try as i want them to move away from microsoft and go to ubuntu instead of vista (shivers)....  tried to boot and it freezes...  i burned it again at 8x as that is the slowest it will let me burn.. and it all works fine..

jsut a note that the "check this cd" option will report no error on the cd if its burned to fast and still sometimes it doesnt work as in my case..

if all else fails order cds from ubuntu.com for free

---

### Post by xtreme35967 on 2007-04-23
Ok plz dont get mad if you have already tried this but noone has asked this yet.  You say that you have XP on the PC. So that means that you are wanting to Dual Boot Correct?  If yes have you repartitioned the hard drive so that you have XP on one part and a FAT32 Partition for Ubuntu?  Ubuntu can not be installed on a NTFS partition. Like i said dont get mad if you know this I am just trying to check all the bases.

---

### Post by SikEnCide on 2007-04-23
> **xtreme35967 said:**
> Ok plz dont get mad if you have already tried this but noone has asked this yet.  You say that you have Vista on the PC. So that means that you are wanting to Dual Boot Correct?  If yes have you repartitioned the hard drive so that you have Vista on one part and a FAT32 Partition for Ubuntu?  Ubuntu can not be installed on a NTFS partition. Like i said dont get mad if you know this I am just trying to check all the bases.

i think  the problem is he cant even boot from the cd

---

