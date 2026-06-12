---
title: "G4 AGP 6.10 can't find repositories"
date: 2009-05-08
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-08
I have installed Ubuntu 6.10 on an old PPC G4 Sawtooth (AGP graphics) and it works fine...but this is linux so you KNOW there's an "except" coming, and here it is: It works fine, except that the repositories are not located where the system thinks they are. I read the FAQ thread on this and still have not figured out where they are now. I have found some repos at [http://old-releases.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-powerpc/](http://old-releases.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-powerpc/) but have been unable to edit the sources.list in any way that makes this work. I guess I need some "example" type help.

I am using 6.10 because it runs on the G4 and later ones I have tried do not.

When I try to play mp3 files of course I get the error message that I need a new codec (since mp3 codecs don't come with the distro) but I am absolutely unable to add them. I get line after line like this:

[http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-powe](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-powe)
rpc/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/P](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-powerpc/P)
ackages.gz: 404 Not Found

The simple issue of playing mp3s is not as important as the overall one of the machine simply not being able to get ANYTHING in the way of an add-on.

Can someone tell me what my sources.list file should be pointing the machine to for the repositories for 6.10?

Thanks in advance.

---

### Post by cyberdork33 on 2009-05-08
6.10 is very old. the newer PPC releases are in a different place now. People have been having a lot of luck with 9.04:
[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

---

### Post by Benboom on 2009-05-08
Look, I know that 6.10 is old. I also know that the newer versions will not run on this machine and said so in my post. If you look at these threads you will see there are a ton of issues with getting Ubuntu to work on a G4 AGP so since I seem to have found one that works that's what I'm using. Where the heck have the repositories gone?

---

### Post by cyberdork33 on 2009-05-08
> **Benboom said:**
> Look, I know that 6.10 is old. I also know that the newer versions will not run on this machine and said so in my post. If you look at these threads you will see there are a ton of issues with getting Ubuntu to work on a G4 AGP so since I seem to have found one that works that's what I'm using. Where the heck have the repositories gone?
I thought you were indicating that there were no downloads for ppc and versions > 6.10... my apologies.

Edgy reached end of life about a year ago, so the repos may be closed now. You could try old-releases.ubuntu.com as the server...

---

### Post by Benboom on 2009-05-08
I did try using that server but I can't seem to get the syntax right in the sources.list file, which seems odd, as it isn't particularly strange. But all the variations I have tried have given me error messages, although if I actually GO there in a browser it shows files there.

Ubuntu 8.10 won't even load the live disk; it says there's no CD-ROM drive.

I have tried 9.04 but my monitor keeps giving me an OUT OF SCAN RANGE when I try to boot the system. The 9.04 disk did that too but went ahead and got past it to load. But the installed version just refused to do that.

Kubuntu 6.10 had real problems with the screen display, too. I haven't tried 7.x because I read so many comments about it.

That's why I'm trying to get these Ubuntu 6.10 repositories located in the computer's mind.

---

### Post by Benboom on 2009-05-08
I'm writing this via Firefox under Ubuntu 9.04...BUT

I pulled the monitor from my main Mac and attached it to the old one and it boots the 9.04 although it only shows 2 available resolutions, both pretty mediocre. The old Mac had a Sony Multiscan17sfII attached to it which is certainly capable of most resolutions the system should need for a basic display - I would probably set it to 1024 x 768 @ 75 hz if I could because the monitor supports that resolution with the old G4 just fine. But under Ubuntu the bootup just stops before it can even get to the log in with this OUT OF SCAN RANGE. Obviosly, if I could get this working I certainly wouldn't mess with 6,10 as with this version of Ubuntu I am able to access repositories and upgraded my codecs with no trouble.

So maybe I should start a new thread about OUT OF SYNC RANGE message on bootup...because I need to put this particular monitor (the one I'm using right now) back on the newer Mac, which is my Photoshop machine.

UPDATE: now it's working! I put the old monitor back in the chain and when I rebooted this time it didn't go through all the bs about the scan range. So for the moment I'm happy, though I will need to figure out how to get the monitor's resolution up to 1024x768. But that's probably doable, at least. Hard to get anywhere if all you can see is a blinking scan range error message. :-)

---

### Post by stream303 on 2009-05-09
Looks like we got the monitor working in another thread - but as kind of a followup for lurkers faced with the same frustration on ppc:

One of the reasons why the "alternate" installer is touted so much rather than the live-cd dekstop version is for precisely this reason - the default xorg H and V values may easily trigger display problems right from the start.  With the alternate, at least you can get the system installed, where you can go back in after the first reboot and fix xorg.conf manually.

Let me know what machine you have as requested in the link in the other thread - if it is running an nvidia card for graphics, I have a another tip for xorg.conf especially if you are into photoshop / Gimp etc and don't want to see rough gradients etc.

---

