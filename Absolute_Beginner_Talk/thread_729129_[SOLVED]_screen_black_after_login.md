---
title: "[SOLVED] screen black after login"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by optimusmedia on 2008-03-19
I'm having a problem close to [[COLOR="black"]_[COLOR="Blue"]this one[/COLOR]_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=520266").  But not quite.

I  have auto login enabled.  
So I get logged in and then while the background  is black I am asked for my password (because it wants to connect to my wireless network).  I do that and I'm back to black and a mouse icon.

If I hit Ctrl-Alt-Del I get the typical log out choices visible (yet everything else remains black).  I can reboot, shutdown or even logout and log back in (and I do see the splash screen).

I installed many little things today trying to find some software that would do what I needed (I"ll spare you the details unless you think it's important). But I didn't have an issue until I rebooted.

I am running emerald and compiz - I can even rotate the cube - but it's a 4 sided black cute at this point.

In an attempt to fix i ran this: sudo dpkg-reconfigure xserver-xorg.  But that didn't fix anything.  Wait, it did change the black to "ubuntu brown" background.  Black was the old theme color. But its still not working.


Any help would be appreciated.  Thanks!

Ron

---

### Post by optimusmedia on 2008-03-19
Quick update - the screen saver works and looks normal.

---

### Post by mcdan on 2008-03-19
i had a similar problem on my computer after i install compiz.  my mouse would turn into an X tho, but it would go away after a minute.  how long have you let it sit black before rebooting or logging out?  it may just need more time to load the desktop

---

### Post by optimusmedia on 2008-03-19
RE: how long.  30 min or more.

I really think I installed something that boogered it up.  Any way to find everything I instlalled today and uninstall?

---

### Post by optimusmedia on 2008-03-19
as I try to experiment and fix this myself - i have uninstalled compiz and emerald.  Neither of which helped.

---

### Post by (((X))) on 2008-03-19
Your home directory may be messed up.
Create a user account, login with new account and see what happens.

---

### Post by optimusmedia on 2008-03-19
I fixed it.  Here's what I did.. it was a bit of a shotgun approach, so no telling what did the trick, but I'm back up and running as good as ever.

Okay since I had auto login enabled I had to Ctrl-Alt-Backspace to reboot X (correct me if that's not what is really happening -- I still got a lot of newbie in me) and bring me to a login screen.

Select the fail-safe option from the menu in the lower left hand corner then login with your admin level (in my case the only login) username and password.

That came back up and allowed me to get in and uninstall everything I added today (as best I could remember) and I completely removed compiz, emerald and other "shiny things" that I thought might be causing this. 

After that a new reboot had everything up and running.  I reinstalled my bling (compiz, emerald, etc) and all is well now.

Again, I know you can file this under "how not to write a tutorial" but I wasn't thinking about anyone buy myself at the time.   Whew, I feel better just confessing that. :)

Hopefully there is some nugget someone will find helpful.  If you know more than I do (and that bar is not high at the moment) feel free to clairify or correct anything I have written.

---

