---
title: "The following occurs when I enter &quot;gnome-system-monitor&quot; into the Terminal."
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-06
I've recently mapped the terminal to the tilde button and am starting to memorize certain program commands so that I don't have to use the GUI all the time. I know that the command for the System Monitor is Gnome-System-Monitor, but when I enter it I get the following weird message:

I/O warning : failed to load external entity "/usr/share/gnome-about/gnome-version.xml"

** (gnome-system-monitor:9921): WARNING **: SELinux was found but is not enabled.


(gnome-system-monitor:9921): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8

However, the System Monitor does still come up with out a problem so as long as all that wacky stuff doesn't mean anything big and bad, its not that big of an issue to me as I have another tweak concerning me at the moment. I would still like to know, out of curiosity, what it all means and if it is dangerous or not. 

PS: I think I remember using this command a few days ago and I didn't get the weird message.

PPS: Yes, I am aware of the thread already pertaining to this, but I thought the title was a little off key, and thought that this thread might gather attention a little better than the other.

Here is a link to the other thread:

[http://ubuntuforums.org/showthread.php?t=631569](http://ubuntuforums.org/showthread.php?t=631569)

---

### Post by Dr Small on 2008-03-06
I am pretty sure it is not dangerous, as long as everything is working properly.
There is a way, if I recall correctly, to turn off those errors, but I forget how.

Dr Small

---

### Post by Magnentius on 2008-05-08
I received this error message from gnome-system-monitor too. So I searched for answers and I found via wikipedia this site which states that SELinux is not enabled in Ubuntu 8.04 by default. So the error message in gnome-system-monitor isn't an error message at all. To resolve the problem you'll have to install the SELinux package from synaptic or simply type at the konsole:

> sudo apt-get install selinux

I wonder why the hell selinux isn't enabled by default.

---

### Post by merlyn on 2008-07-20
Hi folks,

I've only just recently experienced a similar problem, which baffles me immensely as gnome-system-monitor worked for me the last time I logged on.

In the 'meantime' I had made no changes whatsoever, to my system.

The error message i get is this.

```
** (gnome-system-monitor:10609): WARNING **: SELinux was found but is not enabled.


(gnome-system-monitor:10609): glibmm-WARNING **: failed to wrap type of 'GHalMount'
Segmentation fault
```Anyone else come across this?

Cheers.

**Edit**: I've overcome the problem for now, though I'm not entirely satisfied with the whole deal, as I'm unsure as to the actual cause.

Quite simply, I uninstalled gnome-system-tools (completely) & reinstalled via synaptic.

---

