---
title: "nvidia driver confusion"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by pjrettin on 2007-04-22
When using edgy, I always got the best video performance using nvidia's proprietary drivers (installed by using Envy). 

I had some issues during the upgrade with the installation of the drivers part, but managed to fix it and now I THINK I'm using the restricted drivers (nvidia in xorg not 'nv').  The Restricted Drivers Manager shows I'm using the accel nvidia drivers.  How do I find out exactly what drivers I'm using?

Check out this screenshot in synaptic -> [http://www3.nb.sympatico.ca/pjrpjr/Screenshot.png](http://www3.nb.sympatico.ca/pjrpjr/Screenshot.png)

I want to use the new envy to install the proprietary drivers again for Feisty, so should I clean up some of these driver installations shown in syanptic first?

---

### Post by SOULRiDER on 2007-04-22
To know if youre using it, just open your xorg config and see what youre using. Another way to check is if the nvidia logo appears when xorg loads up (it might have been turned off though so it may not appear). One thing that i noticed is that (at least on my computer) if you drag a big rectangle in your desktop it will be smooth if hte nvidia drivers are running, but if the default ones are being used, it will lag.

---

### Post by pjrettin on 2007-04-22
I mean, how can I tell what driver in the synaptic list I'm actually using... xorg just tells me nv or nvidia...

My real question is, should I remove / cleanup those packages before I use Envy to install the proprietary drivers?  Or.. are one of those drivers in the synaptic list actually the latest nvidia proprietary drivers?

I seem to be running into graphic issues like I did before using Envy in Edgy so that makes me think I'm not actually using the nvidia proprietary drivers.

---

### Post by pjrettin on 2007-04-22
No one else?

---

### Post by SOULRiDER on 2007-04-22
If youre using the nvidia driver i dont see the point of reinstalling using envy. If youre using the nv driver, i dont see why use envy to install when you can just add "idia" to xorg and it will be working.

---

### Post by pjrettin on 2007-04-22
So, are you saying that the 'restricted' drivers in the synaptic screenshot are the actual nvidia proprietary drivers I'd get if I downloaded them from nvidia?

I need an explanation of what all these different nvidia drivers are I guess...

---

### Post by SOULRiDER on 2007-04-22
Yeah, basicallt, theres 2 drivers, the open source ones 'nv', and the ones provided by nvidia, aka propietary aka restricted, 'nvidia'.
You have the propietary/restricted ones installed, all you need to do now is enable them in xorg (if not done already)

---

### Post by pjrettin on 2007-04-23
Yeah, but... what VERSION of the nvidia proprietary driver is in the repositories?  I doubt it's the same one that Envy downloads from nvidia...

---

### Post by pjrettin on 2007-04-23
Okay, if I open up nvidia-settings it says I'm using driver version 1.0-9631.

I've seen reference to nvidia-manager  but I don't have that... so I'm wondering now if I should clean up my drivers somehow (maybe nvidia-settings is left over from the Envy official nvidia installation before my upgrade to feisty?)

What I want to end up with is to using the 97XX version of the drivers in nvidia-glx-new.  I guess I should mention that I have a 7800GS card.

---

### Post by doriard on 2007-04-23
I've got a similar problem with the nvidia driver 9755.  I tried to follow the install instructions from the nvidia website but I get an error message saying it can't find libc.  So I tried to install libc6-dev per messages in this forum and now I get the error message:

The following packages have unresolvable dependencies...
Depends: libc6 (=2.3.5-1ubuntu12.5.10.1) but 2.5-0ubuntu14 is to be installed

How can I get the libc6-dev library installed?

Should I try the beta version of envy, or do I need to get these libraries installed first?  I haven't tried envy before.

---

### Post by univremonster on 2007-07-17
I had this same problem but for a different function.  The way that I got the version of libc6 needed was a bit of a cheat really, but it worked - just do the online upgrade to Fiesty Fawn and you're good to go

---

