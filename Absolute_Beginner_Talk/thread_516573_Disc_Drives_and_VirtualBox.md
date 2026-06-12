---
title: "Disc Drives and VirtualBox"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-03
Whiile in **VirtualBox**.... When I open any program that requires some form of DVD/CD Drive
Ubuntu states that it can't mount the DVD/CD Drive.  Any idea why I can't mount Disc Drives?
I'm using Ubuntu 7.04

Any ideas?

[img]http://img169.imageshack.us/img169/1149/02screenshotlx4.png[/img]

---

### Post by apswartz on 2007-08-03
Go to the Virtualbox settings and click on CD/DVD-ROM to open up the dialog and select how you want a cd mounted - with your actual CD/DVD-ROM Drive or an ISO image, etc. 

See attached image.

---

### Post by Orbital75 on 2007-08-03
Yep.... that's what I've been doing but it still won't mount.....
This is something interesting that I didn't notice before.
It will mount all data Discs but just not Audio CD's......
Any idea why?

So it seems that it is just limited to Audio CD's

Here is my settings.

[IMG]http://img180.imageshack.us/img180/9161/00screenshotrc2.png[/IMG]

---

### Post by apswartz on 2007-08-03
I noticed in your original screenshot that the problem is in trying to rip an audio cd. Do you have trouble mounting data cd's?

---

### Post by dca on 2007-08-03
Also, were the VB guest tools addition installed?

---

### Post by apswartz on 2007-08-03
You know, that got me to thinking. I have never tried Virtualbox for reading audio cds so I just tried it here, and no joy. I tried several audio cds and while they are recognized just find in the host OS (in my case Linux) they were not seen by the guest OS (in my case Windows XP). I'm thinking this is a Virtualbox issue.

---

### Post by dca on 2007-08-03
...okay, well, I'm out...  :)

---

### Post by apswartz on 2007-08-03
@dca, your post showed up after I made mine. Sorry. I didn't realize there was another package or program of tools to install.

@orbital75, maybe you will find more response from the Virtualbox forums...
 [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

---

### Post by apswartz on 2007-08-03
@dca, I installed the guest tools. Nice. A lot like Parallels, but I see they have  a set of tools for Linux too -- great!

But, still doesn't recognize my audio cds :eek:

---

### Post by Orbital75 on 2007-08-03
Hey guys.... sorry I've been away from the PC for awhile.

Yep, it's just when trying to read an Audio CD. 
Data CD's mount and read just fine
For some reason Audio CD's,  just won't mount.  
As you said, it will Read in the Host OS just not in the Guest.
I'm not sure why that is but it does seem to be the case.

Well, as far as the Guest tools, I do not have them installed.
I wasn't sure what they did to be honest.

I've tried the VirtualBox forums but for some reason no one seems to know anything
on the forum.  You'll ask a question and a week later there is still no reply to your
questions. I'm finding people on the Ubuntu forums much more helpful.

Heres my post on the VirtualBox Forum. I've asked several question but no one
ever replys back.

[http://forums.virtualbox.org/viewtopic.php?t=1079](http://forums.virtualbox.org/viewtopic.php?t=1079)

Here is another issue I am having:
[http://forums.virtualbox.org/viewtopic.php?t=1081](http://forums.virtualbox.org/viewtopic.php?t=1081)

---

### Post by asmoore82 on 2007-08-03
plain Audio CD's are not in mountable ISO format;
only "enhanced" audio CD hybrids are mountable

---

### Post by Orbital75 on 2007-08-03
Humm...... not sure if we are on the same page or not. 

If an Audio Disc is in my DVD/CD Drive my Optical Drive won't mount
and gives an non mountable error.

I want to mount the Optical Drive then play the CD.
For some reason when there is an Audio CD in the drive, the drive won't mount.

Not sure why.

---

### Post by asmoore82 on 2007-08-04
> **Orbital75 said:**
> Humm...... not sure if we are on the same page or not. 

If an Audio Disc is in my DVD/CD Drive my Optical Drive won't mount
and gives an non mountable error.

I want to mount the Optical Drive then play the CD.
For some reason when there is an Audio CD in the drive, the drive won't mount.

Not sure why.

Audio CD's cannont be mounted.
I know Winders does that track?.cdr thingy with them and maybe even some
Linux distro's have started showing similar GUI tricks but they are a fake.

Audio CD's never have contained CD-ROM data; that's what makes them Audio CD's
therefore they should not be mountable ...

try to play the disc with XMMS.

---

### Post by apswartz on 2007-08-04
Orbital75,
Installing the Guest tools should help with your printing issue if I understand them correctly. If you downloaded the PDF manual check on page 47 for the step by step process of installing them on an Ubuntu guest.

I'm not running linux as a guest but the really add a lot to the windows guest. I can resize the window and the mouse become active and leaves in a smooth, integrated process.

---

### Post by apswartz on 2007-08-04
asmoore82 is correct in saying that audio cds are not mountable like conventional file systems, but Orbital75 is simply reporting the error message he gets when he tries to rip an audio cd from within his virtualbox hosted guest system using grip. The application cannot read the disc and throws up that error message.

---

### Post by Orbital75 on 2007-08-04
That's correct..... I can't play or Rip Audio CD's in my Guest OS.

I installed the Guest Additions, at least I think I did.
I logged in as Root from the command line
It was strange because it wouldn't let me at 1st...... 
I had to go into users and change the Root Password
It's like the Root account wasn't activated or something.
Anyways

/media/cdrom0

then entered the command sh ./VBoxLinuxAdditions.run

the command Ran
Then it stated I needed to reboot.
I rebooted but I can't really tell if anything installed.
Should I have rebooted as Root?
I just rebooted as a normal User.

I don't see any extra features in VirtualBox
Should I?

Still can't get the printer to work..... 
As I said I am new to ubuntu but I think this is a VirtualBox issue.

---

### Post by apswartz on 2007-08-04
You might want to ask on their forums. Sorry we couldn't help more :-)

---

### Post by apswartz on 2007-08-04
Oh, if you do find a solution please come back and share it with us. Thanks.

---

### Post by Orbital75 on 2007-08-04
No problem..... I'm glad you guys helped as much as you could.

The VirtualBox Forums is a real let down to say the least.
I wish everyone there was as helpful as the Ubuntu Forum.
It's very strange no one seems to know the program very well.
When you do met someone that seems to know something, they have a
"well if i have to" attitude.

The Ubuntu Forum are something special where everyone loves
to help and share their knowledge.

---

### Post by apswartz on 2007-08-04
Yes, the Ubuntu Community is pretty special.

---

