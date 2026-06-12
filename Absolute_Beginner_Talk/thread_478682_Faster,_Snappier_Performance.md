---
title: "Faster, Snappier Performance?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by phollos on 2007-06-19
I thought things were going great after I installed ubuntu and I was very happy with the OS... Until I decided to dual boot ubuntu and XP and realized how sluggish ubuntu seemed.

I run a 2.8ghz P4, 1.5gb ram, and an X800 card so it isn't anything too terribly old, but ubuntu, from the first startup time, to application launches, just feels well... more responsive in comparison, and it bugs me.

Anyone have any tips and tricks on speeding up the operating system? Basically all I've added is firefox, thunderbird, and amarok and I haven't set anything up to start on boot-up. It seems though that ubuntu comes with a bunch of programs I don't really need. Would removing them help speed things up? I don't understand the inner workings of Linux and if anyone has any performance and speed tweaks I'd love to hear them.
thanks!

---

### Post by Crafty Kisses on 2007-06-19
> **phollos said:**
> I thought things were going great after I installed ubuntu and I was very happy with the OS... Until I decided to dual boot ubuntu and XP and realized how sluggish ubuntu seemed.

I run a 2.8ghz P4, 1.5gb ram, and an X800 card so it isn't anything too terribly old, but ubuntu, from the first startup time, to application launches, just feels well... more responsive in comparison, and it bugs me.

Anyone have any tips and tricks on speeding up the operating system? Basically all I've added is firefox, thunderbird, and amarok and I haven't set anything up to start on boot-up. It seems though that ubuntu comes with a bunch of programs I don't really need. Would removing them help speed things up? I don't understand the inner workings of Linux and if anyone has any performance and speed tweaks I'd love to hear them.
thanks!

You can get a optimized version of FireFox called "SwiftFox" that's all that comes to mind really. :D

---

### Post by meborc on 2007-06-19
the first thing i would do is to sort out my video card drivers... ATI is known to be a problem maker... your sluggish performance might be connected to this

for tweaks, check this out - [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

---

### Post by loserboy on 2007-06-19
you can also turn off some startup services if you arent using them such as bluetooth or the HP printer thing, theres about 5 services that I end up turning off

---

### Post by oilchangeguy on 2007-06-19
> **phollos said:**
> I thought things were going great after I installed ubuntu and I was very happy with the OS... Until I decided to dual boot ubuntu and XP and realized how sluggish ubuntu seemed.

I run a 2.8ghz P4, 1.5gb ram, and an X800 card so it isn't anything too terribly old, but ubuntu, from the first startup time, to application launches, just feels well... more responsive in comparison, and it bugs me.

Anyone have any tips and tricks on speeding up the operating system? Basically all I've added is firefox, thunderbird, and amarok and I haven't set anything up to start on boot-up. It seems though that ubuntu comes with a bunch of programs I don't really need. Would removing them help speed things up? I don't understand the inner workings of Linux and if anyone has any performance and speed tweaks I'd love to hear them.
thanks!

one os has nothing to do with the other, so it's impossible for your dual boot setup to be slowing ubuntu.

---

### Post by phollos on 2007-06-19
I'm not accusing XP of slowing down ubuntu, I know they don't interact. What I'm saying is I didn't really notice how slow ubuntu was running until I was working with XP again.

I always thought that Linux would be quicker because it didn't have all that garbage that comes along with a microsoft OS running in the background. So why is XP running quicker than my Linux install?

---

### Post by hardyn on 2007-06-19
im going to bet it is 100% to do with the video drver.

try the ATI binary driver, im not sure if the 'radeon' driver will work with an x800 but its worth a try.

**whoops already suggested ;) **

---

### Post by Crafty Kisses on 2007-06-19
> **hardyn said:**
> im going to bet it is 100% to do with the video drver.

try the ATI binary driver, im not sure if the 'radeon' driver will work with an x800 but its worth a try.

**whoops already suggested ;) **

Yep. :p

---

### Post by phollos on 2007-06-19
Would a video driver really speed up boot time though? I'm running the fglrx proprietary drivers if that makes a difference. Main thing that bugs me is:

1) very slow bootup time compared to other OS's
2) apps "hang" a bit before launching like firefox (I have to wait 3-4 seconds after clicking the launch icon before firefox loads while on XP it's pretty much instant)

I guess I was just expecting such a lightweight OS (in comparison to windows) would be a leaner, faster computer. Guess I will try swiftfox as Codename suggested but I'm not sure what to do with my other apps and the boot time itself...

---

### Post by Crafty Kisses on 2007-06-19
> **phollos said:**
> Would a video driver really speed up boot time though? I'm running the fglrx proprietary drivers if that makes a difference. Main thing that bugs me is:

1) very slow bootup time compared to other OS's
2) apps "hang" a bit before launching like firefox (I have to wait 3-4 seconds after clicking the launch icon before firefox loads while on XP it's pretty much instant)

I guess I was just expecting such a lightweight OS (in comparison to windows) would be a leaner, faster computer. Guess I will try swiftfox as Codename suggested but I'm not sure what to do with my other apps and the boot time itself...

Yes, video card speeds up a whole bunch of stuff. :D

---

### Post by phollos on 2007-06-19
Is the fglrx and binary different? If so what's the difference between them?

---

### Post by sabrewolf2006 on 2007-06-19
> **loserboy said:**
> you can also turn off some startup services if you arent using them such as bluetooth or the HP printer thing, theres about 5 services that I end up turning off

Another suggestion would be to use preload.. this program basically watches your usage and puts your commonly used programs and files in ram..

You could also alter your swappiness value.. this affects how linux uses your ram.. striking a balance between cache ram usage and process usage..

ask 10 different people and you'll get 10 different answers on what this value should be..

it is altered on a per session basis by
sudo echo value > /proc/sys/vm/swappiness
to alter on a permanent basis you need to add a line like this
vm.swappiness=10
to
/etc/sysctl.conf
I currently use a value of ten (which means that my system doesn't cache that much data - the ubuntu default is 60)although 0 has been suggested as noticeably improving responsiveness

and prelinking more works a treat too.. more on that later

---

### Post by xero 1ne on 2007-06-26
Feisty doesn't need preload, it comes with something else that is better.

Older versions though, you should get preload.

---

### Post by olejorgen on 2007-06-26
> **xero 1ne said:**
> Feisty doesn't need preload, it comes with something else that is better.

And what would that be?

(Can't say I've noticed this..)

---

### Post by WakkiTabakki on 2007-08-22
Uhm... I think you've mixed thing up with **prelink**. Prelink is apparently not needed anymore: [http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197)

Cheers
/N

---

### Post by TygerTung on 2007-08-22
I have an ATI radeon graphics card, where can I get these drivers for it?

I haven't installed any drivers yet.

---

