---
title: "cannot install with Nvidia 6200 card please help"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by dacium on 2007-11-09
When I run the install disc (even in safe graphics mode) I get to see the desktop for a second, then my monitor looses all signal. If I press cntrl alt f1 I can access the console all right.

My video card is XFX 6200 AGP. Can someone please help me set this thing up from the command line!

---

### Post by Doggles on 2007-11-09
Hi Dacium - I've got a 6200A - didn't have this problem with Gutsy install, but I was using the Ubuntu Studio installer, which is a text-based, non-graphical installer. I guess that after the installer had set up my graphics OK, when I rebooted to hard drive it just worked - lucky me...

Anyway, sounds like xorg might not be configured properly, if you can get into terminal, you could try this:

sudo dpkg-reconfigure xserver-xorg

Not sure what will happen with the "sudo" thing yet of course cos you haven't set up an acccount or root password yet but it's worth a try.

Here's a thought - how about proceeding with the install using the "alternate CD" - get your base system installed using the text installer (not sure if you're familiar with that, but it's not too scary to be honest, even if you're new to it), then if you still don't have GUI, then use the above from terminal to reconfigure xorg. If you're lucky and this works to give you a usable desktop, then I'd recommend Envy to install the NVidia restricted drivers - this worked well for my 6200.

Best of luck mate - let me know how you get on, I'll keep my eye on this thread and will try my best to assist further if needed

Cheers

---

### Post by so7777777os on 2007-11-09
> **Doggles said:**
> Hi Dacium - I've got a 6200A - didn't have this problem with Gutsy install, but I was using the Ubuntu Studio installer, which is a text-based, non-graphical installer. I guess that after the installer had set up my graphics OK, when I rebooted to hard drive it just worked - lucky me...

Anyway, sounds like xorg might not be configured properly, if you can get into terminal, you could try this:

sudo dpkg-reconfigure xserver-xorg

Not sure what will happen with the "sudo" thing yet of course cos you haven't set up an acccount or root password yet but it's worth a try.

Here's a thought - how about proceeding with the install using the "alternate CD" - get your base system installed using the text installer (not sure if you're familiar with that, but it's not too scary to be honest, even if you're new to it), then if you still don't have GUI, then use the above from terminal to reconfigure xorg. If you're lucky and this works to give you a usable desktop, then I'd recommend Envy to install the NVidia restricted drivers - this worked well for my 6200.

Best of luck mate - let me know how you get on, I'll keep my eye on this thread and will try my best to assist further if needed

Cheers

Hope to be useful........

---

### Post by dacium on 2007-11-09
Hi,
I already found out about that command. That lests me at least get a visible desktop. However nothing to do with video card or video settings in the gui works. for example system->screen resolution doesn't do anything. I can pick lots of resolutions but they have no effect.

I am not convinced I even have a driver installed... where do i go to install nvidia driver??

---

### Post by Doggles on 2007-11-09
Envy lives here:

[http://albertomilone.com/](http://albertomilone.com/) - good because it checks your system out and installs the right driver for you. Requires a restart though, so only useful for an installed system, not a live CD!

...or you can enable restricted drivers in the restricted drivers manager menu - I think that lives in the "System" menu somewhere.

I think you might have more joy with a hard-drive install rather than the live CD in this case because it gives you more opportunity to fix this. Would thoroughly understand if you don't want to commit to that yet of course...

---

### Post by dacium on 2007-11-09
No i want to commit because i want to run myth tv on this box.
I am installing now. It is stuck at "Configuring apt" Scanning the mirror... 82%, got to there fairly quickly now just sits there for a long time, no CDROM or HDD activity... I thought I saw some link activity, what is going on? How long does this take?

---

### Post by Doggles on 2007-11-09
That's probably a network step so might depend on how fast your network is? - If I remember correctly, Gutsy took about half an hour to finish installing on my system.

---

### Post by newlinux on 2007-11-09
You may have a bad install disc as well (or a bad part of the disc). DId you burn it yourself? I have found ubuntu install discs to be pretty sensitive. Make sure you burned it at a very slow speed, and make sure your .iso passes the md5sum test.

---

