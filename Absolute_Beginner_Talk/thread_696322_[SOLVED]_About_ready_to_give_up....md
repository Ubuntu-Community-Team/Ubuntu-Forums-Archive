---
title: "[SOLVED] About ready to give up..."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-13
*sigh*

Well, I'm so frustrated I'm thinking about just giving up and I really don't want to.  I'm going to give it just one more chance and then I'm done.

Here's the situation:  I built a PC from some spare parts I had laying around.  No matter what distro of Ubuntu I use, I get error message after error message telling me that some package is corrupted or some file is corrupted or SOMETHING is corrupted.  Whenever I try to fix it, I get a NEW message saying something is corrupted.

I can't get ANY browsers to work on this machine.  When I launch Firefox, I get the little "thinking circle thingy" and then it just disappears and Firefox never launches.  I tried launching it from the terminal and it says it's not installed, so I tried to install it with **sudo apt-get install firefox**.  It then tells me that I'm already at the newest version, which pisses me off because it just got through telling me that the program wasn't installed.

I tried to install Opera, but there are some dependancies it needs and it flat out tells me that it's not going to install them for me.

I tried to install Iceape, but this time I got my old standby error saying something is corrupted.  It's hard to go back and forth between computers typing everything word for word.  If I could just get a browser working, I could cut and paste the error messages.

So...I'm thinking that an error here and there isn't such a big deal, but to get error after error after error probably indicates a problem with hardware someplace.  I ran memtest and the RAM checks out fine (I ran it for about an hour).  I have a brand new hard drive, but I suppose I could've got a bad one.

Is there a utility that can test my motherboard and CPU (kinda like how memtest checks your RAM)?  This is the last straw.  I'm thinking I'll buy an inexpensive MB and a P4 CPU.  If it doesn't work after that, I'm done with Ubuntu and Linux in general.  I just can't take the frustration anymore.

---

### Post by hAvAAck on 2008-02-13
I can't help you but I'd say don't give up. I had a dell I wanted to really try ubuntu on a couple years ago  but it'd never worked, so I gave up. I recently built a new box and ubuntu is great on it, it's a whole different experience that I'm enjoying
best of luck!

---

### Post by blackdragon1157 on 2008-02-13
Do you have an internet connection?  Because if you're reinstalling packages from the install CD, this screams 'bad cd'.  Otherwise, I'm stuck too. (Waits for superusers)

---

### Post by KCormier on 2008-02-13
That really sounds like a hardware problem.  You said the memory is checking out fine.  Are you running the live cd when you get these errors or is it only AFTER the install?  if it's after the install, try just using it as a live cd for a while. If the live cd works but the install doesn't, chances are it's the hard drive.  If the live cd doesn't work then it could be mobo/processor/video card or god knows what else.  Let us know first if the live cd works.

good thinking blackdragon...i didn't even think of that...   Have you ever tested the cd?  When you boot to cd, it's one of the options (includes memtest, and then all the live boots/yada yada)

---

### Post by emarkd on 2008-02-13
I guess it would be quite strange for a corrupted CD to finalize an installation, but bad burned CD's are very common.  Did you burn the disk yourself?  Did you check the md5 hash of the .iso to make sure you got a good download?  Did you burn the disk real slow to minimize burning errors?

There's a good article about these things here:  [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I know this sounds like a long shot, but with lots of "corrupt stuff" error messages, I guess I'm thinking corrupt stuff.  If nothing else, could you get a little more descriptive and complete with your error messages?  Something might ring a bell with someone...

---

### Post by Scut_Farkus on 2008-02-13
Hey all!

Thanks for the quick responses.  Part of my frustration is that I have a fever, chills, headache, my nose is stuffy, and my body aches.

To answer some of your questions:

1.)  Yes, I burned the CD myself.
2.)  I verified that the hash is correct on my download (because I had so many problems with other distros).
3.)  I verified that there were no problems with the burn (checked CD for errors)

I bought a new hard drive because I was getting the same type of errors with the old drive I was using.  I like to use DBAN to scrape the drive before an install and when DBAN was scraping the old drive I got a lot of weird stuff on the screen (not the normal DBAN progress screen)...blocks of black background and odd messages appeared over the top of DBAN's normal screen.  I'm getting this same weirdness with the new hard drive, so either the new one is bad too, or perhaps there are some interface problems with the drive talking to the other components?

I wasn't very descriptive with the error messages because there were just so many of them I didn't know where to start.  I can't seem to get ANY browsers working.   I don't want to go back and forth from one computer to another, typing in a bunch of error messages, when it might be I'm banging my head against a wall for nothing if the hardware is bad.

Good idea about the LIVE CD.  I'm getting these messages after the install (it installs just fine, by the way).

Yes, I have an internet connection.  It works.  I can get some stuff, but most things error out on me after a while.

I guess I'll just pick an error....this is one I get when I try to grab updates using the Update Manager:

An error occurred

The following details are provided:

E: /var/cache/apt/archives/lib6_2.6.1-1 ubuntu 10_i386.deb: corrupted filesystem tarfile-corrupted package archive

---

### Post by SunnyRabbiera on 2008-02-13
Hmm, did you try to use apt-get update?
sometimes it fixes issues like this.
Dont give up just yet, someone is bound to have an answer for you

---

### Post by Scut_Farkus on 2008-02-13
Thanks, bud!

Yeah, I tried apt-get update.  Got an error message.  Didn't bother to write it down because of the frustration factor.  As I said before, no point in writing it all down and transferring it here if the hardware is bad.  I'm going to mess around with the LIVE CD for a bit to see if I still get errors.

---

### Post by emarkd on 2008-02-13
Apt caches those .deb's for later use.  Maybe you got a bad download?  You can remove the cached packages by running:

```
sudo apt-get autoclean
```

Then try installing it again.  It'll have to pull it from the network again and maybe you'll have better luck this time.

---

### Post by SunnyRabbiera on 2008-02-13
well you can give another distro a shot, I personally recommend mandriva.
Also give Mint a shot, its based on ubuntu but it is more stable in my opinion.

---

### Post by Scut_Farkus on 2008-02-14
**UPDATE**

Well, I have to say that I think I ended up getting ANOTHER bad hard drive!  

Irritating, but Newegg rocks, so I'll just send it back to them.  

My Live CD experiments are working flawlessly.  

I got some really simple instructions to get the 3D Nvidia drivers working from a site called [www.pendrivelinux.com](www.pendrivelinux.com).

Here's what they said to do:
1.)  **sudo apt-get update **<--when I did this on the installed version, I got error messages.  No problem with the Live CD.
2.)  **sudo apt-get install nvidia-glx**
3.)  **sudo apt-get upgrade **<--it's still going....it error'd out on me very quickly when I did it before

Hmmm...okay...got an error this time.  Perhaps this is because these steps are not meant to be carried out on the Live CD?  (I hope, I hope, I hope)

Errors were encountered while processing:
/var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-52_i386.deb
E:  Sub-process /usr/bin/dpkg returned an error code (1)

4.)  **sudo dpkg-reconfigure xserver-xorg **<--couldn't even do this step on the installed version and I can't do it now.  It crashes when I try to configue the xserver at the point where it talks about PowerPC's and multiple video devices.  I should be able to simple hit ENTER at this point, but it stops.  

These steps worked with Dapper.  I tried it and it worked flawlessly, so perhaps these instructions are only good for Dapper and Gutsy has some other way to do it?

Anyway, despite the errors, I'm encouraged that some newer, perhaps better hardware might ease some of my Ubuntu Gutsy woes.

Thanks everybody!   :)

---

