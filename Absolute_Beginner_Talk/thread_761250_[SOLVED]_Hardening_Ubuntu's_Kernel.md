---
title: "[SOLVED] Hardening Ubuntu's Kernel"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by steven0451 on 2008-04-21
I'm still fairly new to this, and I've had no problems thus far so I don't know how wise it would be to implement something like this...but can someone with more experience check this over and tell me if it's something that maybe should be done by default on Ubuntu? Or if it's just for something a little more open to the net like a server?

[http://www.ubuntu-unleashed.com/2008/04/howto-harden-ubuntu-linux-kernel-with.html](http://www.ubuntu-unleashed.com/2008/04/howto-harden-ubuntu-linux-kernel-with.html)

It's some sort of modification to a sysctl.conf file, so I'm not really sure how safe it would be (or if it's even needed). This is why I'm a little on-edge about trying it on my only functioning "production" laptop.

Any response would be appreciated. :)

---

### Post by bumanie on 2008-04-21
Have a read of[ this]("http://ubuntuforums.org/showthread.php?t=510812"). I personally think for a home machine that hardening the kernel will not be of any real advantage, servers controlling a network, it arguably could be worthwhile. But overall, linux is already fairly secure out of the box, unlike some other OSes, which have very little of the server market. Linux is used on most servers for a reason, stability and reduced vulnerability to attack.

---

### Post by skymera on 2008-04-21
Any added security is still security.

Im not a security freak.
but i do like to bragg about how Ubuntu was unable to be hacked in "Pwn 2 Own".
But more security is stil 1up on other OS's

I added the text to my sysctl it's harmless at the end of the day.

---

### Post by WorldTripping on 2008-04-21
Have a look at this:

[http://bastille-linux.sourceforge.net/]("http://bastille-linux.sourceforge.net/")

---

### Post by skymera on 2008-04-21
I'll have to look more into Bastille!

Seems good :) Good link.

---

### Post by HunterThomson on 2008-04-21
What, do you just replace the /etc/sysctl.conf file contents with the example (RedHat Linux) contents or past it at the end of the file?

---

### Post by skymera on 2008-04-21
I added it to the end, i have a modified sysctl.conf already.

---

### Post by HunterThomson on 2008-04-21
OK, cool Thanks skymera:) I too like to know that my OS is harder for no real reason. The thing with hacking a box is that no matter how hardened the OS is out of the box doesn't really madder. You hack the vulnerabilities that a OS has out of the box and they all have some. It is only the steps you take after installation that make your system hardened. And, thanks steven0451 for the link.

what about these errors I got after running sysctl -p

error: "vm.bdflush" is an unknown key (( is # Improve file system performance))
error: "vm.buffermem" is an unknown key (( is # Improve virtual memory performance))
error: "net.core.hot_list_length" is an unknown key (( is # Increase the maximum number of skb-heads to be cached))

no big deal right? Should I just delete them?

---

### Post by brian_p on 2008-04-21
> **steven0451 said:**
> I'm still fairly new to this, and I've had no problems thus far so I don't know how wise it would be to implement something like this...but can someone with more experience check this over and tell me if it's something that maybe should be done by default on Ubuntu? Or if it's just for something a little more open to the net like a server?

[http://www.ubuntu-unleashed.com/2008/04/howto-harden-ubuntu-linux-kernel-with.html](http://www.ubuntu-unleashed.com/2008/04/howto-harden-ubuntu-linux-kernel-with.html)

It's some sort of modification to a sysctl.conf file, so I'm not really sure how safe it would be (or if it's even needed). This is why I'm a little on-edge about trying it on my only functioning "production" laptop.

Any response would be appreciated. :)

If you are not offering remote services the additions will do nothing for you. If you are offering remote services the additions may or may not do anything for you.

Adding system variables blindly to /etc/sysctl.conf without knowing what effect they have appears to be the fashion. My guess is you will not miss the absence of
fs.file-max = 65000 or kernel.core_uses_pid = 1.

---

### Post by HunterThomson on 2008-04-21
Increasing the buffer sizes will stop a script kitty from using a packaged buffer overflow attack.

---

### Post by skymera on 2008-04-21
So why aren't these tweaks added in as standard?

---

### Post by brian_p on 2008-04-21
> **HunterThomson said:**
> Increasing the buffer sizes will stop a script kitty from using a packaged buffer overflow attack.

Which specific parameter(s) are you referring to?

---

### Post by brian_p on 2008-04-21
> **skymera said:**
> So why aren't these tweaks added in as standard?

Why should they be? Maybe high bandwidth servers might benefit from some of them. Would increasing the maximum number of skb-heads to be cached be of use to *you*.

---

### Post by steven0451 on 2008-04-21
Judging by the amount of replies, and confusion surrounding what to do...I think I'll gracefully back down from modifying my system (which may or may not even help in the long-term).

I'll leave this in the trusted hands of the developers of Ubuntu to decide whether or not to include it as a default configuration in later revisions of the OS. I want to say thank you for taking an interest in it and trying to help me though; to all of those who did. It's always nice to see an active, helpful community. :)

---

