---
title: "[SOLVED] Security &amp;amp; Safety, update packages in Ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Sceiron on 2008-01-25
Hello.

Beeing new to Linux and all i have been wondering about the security of ubuntu and the packet update manager. I have read a lot of forums that says as long as u must enter the super user password for installation of new updates ( and programs) u are in control of your own system etc etc.

But as i'm new to linux, how can i control this?

As far as i can see there is some kind of control. By using the default repositorys and not add third party repsoitorys i know i allways get thrusted package. Is this correct ?
Or do i need to read about this in the weekly neews letter and confirm that thees updates are safe?
Investegateing all updates will take weeks for me since i dont have so much insight into the OS-itself.

And if I add other repositorys, should i keep them for updating?
Are these repositorys safe?

It all comes down to, how do i keep my computer safe despite not nowing everything about the OS ?

Its not a point in updating with super user if you do not know what you are doing anyways....:confused:

Best regards
Sceiron

---

### Post by stump138 on 2008-01-25
If your user account is the one that was used when you did the installation, then all you have to do is enter your password when prompted by the update manager.  All the super user account is doing is preventing others from making changes to your machine :)

Since you aren't using 3rd pary repo's you are correct when you say that your updates will include only trusted packages.

As long as you practice smart internet browsing, and use some common sense, you'll be off to a fine start.

---

### Post by mikeyphi on 2008-01-25
Your system will be safe if you use the repositories under System/ Administration/Software Sources
The people who put out the updates are the same people who wrote the OS
Ubuntu will give you a warning if you try to install packages that are not from Ubuntu - then the choice is yours!

---

### Post by sumguy231 on 2008-01-25
With third party repositories and packages, just use the same kind of discretion you would in any other operating system - only install from places you trust.

---

### Post by bodhi.zazen on 2008-01-25
For basic security questions, you may want to start here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

For sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The old time *nix users would answer your question by pointing out that the advantage of open source is that you can inspect the code for malignant scripts. If you use open source applications , at least with the larger projects, you benefit from this indirectly. If you install a third party closed source application you may have little on no protection.

If you are paranoid, you can test applications in a virtualized environment (VMWare, Virtual Box, or chroot).

How to chroot : 	[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by Sukarn on 2008-01-25
> **bodhi.zazen said:**
> 
If you are paranoid, you can test applications in a virtualized environment (VMWare, Virtual Box, or chroot).

I love it when people talk about the paranoid mode...

I'm not being sarcastic here. My sentence made me think that it might get across as a sarcastic message so I added this info.

---

### Post by Sceiron on 2008-01-25
Marked this as solved though its not specific problem.
The post above will give me the answers.
Thanks alot.

---

