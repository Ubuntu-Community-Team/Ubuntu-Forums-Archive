---
title: "firewall question firestarter\gaurddog"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-17
I like the look of firestarter, how do I make it start with ubuntu automatically? how do I run it minimized with no window?  

Is gaurddog better? I like firestarter due to its gui

---

### Post by eolson on 2008-01-17
In the default mode it runs in the background.

I'm kind of bad at explaining things.  This is probably a lot more clear.

[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

Being as how it's a frontend for iptables,  I don't think there is anything better.  At least not readilly available

---

### Post by meindian523 on 2008-01-17
Firestarter is just a graphical frontend for the real firewall iptables which is built-in with the kernel.Just click on it's icon in the System Task bar,looks like a blue circle with a "play" button,and it will run minimized.

---

### Post by KezzerDrix on 2008-01-17
but how do you get it to start with ubuntu, right now I have to go into the applications and click on it, to bring up the blue play button.  Isn't there a start menu, or a config file to manipulate?

---

### Post by eolson on 2008-01-17
Once you've started it,  it's started for good.   You can even uninstall it.  The IP tables have been set.

---

### Post by bodhi.zazen on 2008-01-17
Firestarter is NOT you firewall, it is a configuration tool only. Ditto for Guarddog.

Your firewall is iptables.

Once you have configured iptables you should close firestarter and / or Guarddog. You iptables settings remain active, even if you reboot.

You should not run them automatically at log in or as a way of monitoring your network traffic as they run as root and are a security risk.

See this link : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

