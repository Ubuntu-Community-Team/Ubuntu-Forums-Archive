---
title: "Oh no!!  Where's my screen display gone??"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by David F on 2007-12-15
I have just upgraded from Feisty to Gutsy.

I'm running a Sony VAIO with an Acer 1716 monitor. Under Feisty the Acer monitor functioned fine. During the upgrade the Acer functioned fine - until it came time for the final reboot, then the Acer ceased to display anything; the laptop continued to function OK.

Then I discovered the System / Administration / Screens and Graphics section. I very cleverly went in there, selected Screen 2, selected that as the default, selected Acer, selected 1715 (since 1716 wasn't on the list - unfortunately), logged off, logged back on again, and that was the end of Gutsy functioning!

Now, when I try to boot, I get a string of data on the laptop screen which, if I don't interfere with it, finishes up at:
[ 185.868000] serial8250 : too much work for irq9

Partway through loading up the screen with this data, a pop-up appears briefly advising "Failed to start the X-server...... Would you like to view the X-server to diagnose the problem".

Clicking "Yes" brings up another screen for a couple of seconds, which starts off:
etc/gdm/failsafeXserver line47 too many arguments

How do I rectify my stuff-up?

In responding, please keep in mind that I am no Linux guru. I've had years of MS but only a few months of Ubuntu. So please keep the response explicit and detailed. Thanks in advance.

---

### Post by dcstar on 2007-12-15
> **David F said:**
> I have just upgraded from Feisty to Gutsy.
.........
Partway through loading up the screen with this data, a pop-up appears briefly advising "Failed to start the X-server...... Would you like to view the X-server to diagnose the problem".

Clicking "Yes" brings up another screen for a couple of seconds, which starts off:
etc/gdm/failsafeXserver line47 too many arguments

How do I rectify my stuff-up?

In responding, please keep in mind that I am no Linux guru. I've had years of MS but only a few months of Ubuntu. So please keep the response explicit and detailed. Thanks in advance.

There are a gazillion posts on how to fix this sort of thing already in the forums, just search for "reconfigure xorg.conf" and you should be able to find something with detailed steps.

---

### Post by jken146 on 2007-12-15
You can get to a terminal with Ctrl+Alt+F1.  Then ```
sudo dpkg-reconfigure xserver-xorg
```

---

