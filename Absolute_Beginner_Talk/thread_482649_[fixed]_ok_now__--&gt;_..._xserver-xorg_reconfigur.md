---
title: "[fixed] ok now  --&gt; ... xserver-xorg reconfigure ... acts strangely"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-06-23
[COLOR="Red"][B][ edit:  resolved.  The -p switch for priority was screwing it up.  I'm not sure why everywhere online it says to use the -p switch .  ]
[/B][/COLOR]

Hello --

I've installed various flavors of Ubuntu onto many PCs.  Tonight's install on a Dell Dimension 2400 with 845G IG chipset is confounding me.  Admittedly I am in new territory tapping into the terminal before Gnome, but I'm trying my best below.

First, I have successfully installed 6.06 on this Dell.  I can boot into it, all is good.

**At some point near the end of the loading of Ubuntu, the screen goes blank, or refreshes to black**.  So I tap CTRL + ALT + F1 to get a terminal command prompt.

It asks me for username and password.  I give it the only user/pswd I ever gave to it during install.
It gives me prompt:      mynameme@ubuntu$

So far, so good.  I know that my not seeing the xorg gnome screen is related to the xorg configuration.  So I type:
   [B]$sudo dpkg-reconfigure -phigh xserver-xorg
[/B]
From my readings this should launch me into a dialogue to choose or force video settings.  I even have enough experience with this machine's chipset -- and from using Gparted on this machine -- to know what settings I need.  

But when I type the above command, **I do not get the expected dialogue**.  Instead, the screen refreshes to black again, pauses while black, and always comes back to report:
   **postinst warning**: overwriting possibly customises file
and then it makes an automatic backup into /etc/X11/xorg.conf

Of course, yeah, I know that overwriting is exactly what I want to do. Right?

I have found that I can sudo and do things to xorg.conf below.

Please help.  A few other things I have tried:   

* I used sudo rm to delete the xorg.conf file from the appropriate directory - hoping that this would of course force a reconfiguration upon the next dpkg-reconfigure command.  That didn't work.

* I have indeed removed xorg.conf, then used a previous backup in its place, and then tried dpkg-reconfigure.  That didn't work.

* I tried the (-a) "All" switch in dpkg, but that didn't seem to be what I wanted.

* I see a --force switch for dpkg-reconfigure but I don't understand the syntax of how to enable this switch.

Thank you for any help !!!!!

---

