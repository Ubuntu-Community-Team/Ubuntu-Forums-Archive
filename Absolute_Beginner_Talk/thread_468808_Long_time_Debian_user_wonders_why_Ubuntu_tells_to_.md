---
title: "Long time Debian user wonders why Ubuntu tells to restart after installing Nvidia?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by arpegiator on 2007-06-09
Okey,so I've been a long time Debian user and because I was bored last night I thought I'd
give Ubuntu a try.
Booted into the sytem or the first time and applied the available updates.
One of the updates was the kernel and the system told be to reboot wich i can understand after updating the kernel.
What i don't understand i why the system told me to reboot after installing my Nvidia driver with that proprietary drivers manager
thingy, why is Ubuntu telling me to freaking reboot while all i have to do is logout and login?
In all my time using GNU/Linux no distro ever told me to reboot after installing the Nvidia driver so why did the Ubuntu devs make the decision to incorporate something that doesn't need to be done into the system?

---

### Post by bodhi.zazen on 2007-06-09
> **arpegiator said:**
> Okey,so I've been a long time Debian user and because I was bored last night I thought I'd
give Ubuntu a try.
Booted into the sytem or the first time and applied the available updates.
One of the updates was the kernel and the system told be to reboot wich i can understand after updating the kernel.
What i don't understand i why the system told me to reboot after installing my Nvidia driver with that proprietary drivers manager
thingy, why is Ubuntu telling me to freaking reboot while all i have to do is logout and login?
In all my time using GNU/Linux no distro ever told me to reboot after installing the Nvidia driver so why did the Ubuntu devs make the decision to incorporate something that doesn't need to be done into the system?

LOL ~ Just between you and me ~ you do not need to reboot. Shhh it is a secret.

Ubuntu is geared to new users and sometimes the advice to reboot is easier (and scares off the new users less) then the advice to re-start a service.

New users prefer "reboot" to ```
sudo /etc/init.d/gdm restart
``` 

Reboot = mission accomplished

sudo /etc/init.d/gdm restart = "Where, what is a terminal, why does Ubuntu have to be so hard, what's sudo, ....."

---

### Post by Nythain on 2007-06-09
yeah, being geared towards user friendlyness, with lots of new linux users, i would think it recomends rebooting so as not to confuse someone with terminal commands or keyboard shortcuts... reboot is simple and easily understood, and doesnt involve opening up a terminal

---

### Post by arpegiator on 2007-06-09
> **bodhi.zazen said:**
> Ubuntu is geared to new users and sometimes the advice to reboot is easier (and scares off the new users less) then the advice to re-start a service.

I completely disagree!
I've set up many friends with debian who've never used GNU/Linux before and when i told them to just logout by pressing Crl>Alt>Backspace and login again after updating the system or installing the Nvidia drivers they were simply delighted by not having to reboot.
A reboot is nessecary for only two things,booting into a new kernel or changing/adding hardware and that is one of the joys of using GNU/Linux wich the Ubuntu devs should be promoting.
What they should not be promoting is the "Windows way" ;)

---

### Post by bodhi.zazen on 2007-06-09
> **arpegiator said:**
> I completely disagree!
I've set up many friends with debian who've never used GNU/Linux before and when i told them to just logout by pressing Crl>Alt>Backspace and login again after updating the system or installing the Nvidia drivers they were simply delighted by not having to reboot.
A reboot is nessecary for only two things,booting into a new kernel or changing/adding hardware and that is one of the joys of using GNU/Linux wich the Ubuntu devs should be promoting.
What they should not be promoting is the "Windows way" ;)

Ha ha ha ha, rofl

I don't disagree with you, which is to say I agree with you. But ... see Nythain's comment and you will at least understand the sentiment. This is not to say that rebooting is wrong or that restarting services is better, it is just that here at Ubuntu we attract (and to some extent cater to) users who find rebooting to be be more familiar. When they come from windows rebooting seems natural.

Over time we (I) try to teach 'em right, but they are incorrigible :twisted:  

[http://ubuntuforums.org/showthread.php?&t=404250](http://ubuntuforums.org/showthread.php?&t=404250) :rolleyes:

Since you feel so strongly might I suggest two things to you :

1. Feel free to add to the Ubuntu documentation. Comments/suggestions are always welcome and user contributions/improvements is how we grow. ;)

2. Any interest in joining the beginners team (Lord knows we need the help) ? 

[http://ubuntuforums.org/forumdisplay.php?&f=215](http://ubuntuforums.org/forumdisplay.php?&f=215)

[http://ubuntuforums.org/showthread.php?&t=375658](http://ubuntuforums.org/showthread.php?&t=375658)

Careful with that terminal though or you, like me, are going to get a reputation of being an uber-geek :lolflag:

---

### Post by calraith on 2007-06-09
The windows way, as in, "YOUR COMPUTER MAY BE INFECTED WITH SPYWARE!!! Click here to make sure."  That way?

*grin*

---

### Post by ghost_ryder35 on 2007-06-09
> **calraith said:**
> The windows way, as in, "YOUR COMPUTER MAY BE INFECTED WITH SPYWARE!!! Click here to make sure."  That way?

*grin*

:)

---

### Post by bodhi.zazen on 2007-06-09
> **calraith said:**
> The windows way, as in, "YOUR COMPUTER MAY BE INFECTED WITH SPYWARE!!! Click here to make sure."  That way?

*grin*

> **ghost_ryder35 said:**
> :)

LOL. No OS bashing. If you listen to what arpegiator is telling us you might learn something here :)

:lolflag:

arpegiator:

The directions on how-to install the nvidia drivers does not always advise to re-boot, nor would I say rebooting is "the ubuntu way", it is merely an option. It seems to work for some and it does not do any real harm.

See here : [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

See "STEP 2: Install nvidia drivers"

---

### Post by calraith on 2007-06-09
> **bodhi.zazen said:**
> LOL. No OS bashing. If you listen to what arpegiator is telling us you might learn something here :)

Learn something from a Debian user?  Hahahaha!

(kidding)

I know, I know.  If I'm not part of the solution...

OK, so anyway, the NVidia driver installs not only an Xorg driver, but also a kernel module.  After installation, the module is loaded by the installer; but a reboot also helps ensure the intended module gets reloaded, and doesn't get overridden by some non-matching module in linux-restricted-modules.  Installing the NVidia driver from the apt repos has been, in my experience, more reliable than installing the latest and greatest binary from the NVidia website.  Have a look at [http://ubuntuforums.org/showthread.php?t=459771](http://ubuntuforums.org/showthread.php?t=459771) and share my pain.

How do the threads in which I post always tend to go so off-topic?  Hmmmm...

---

