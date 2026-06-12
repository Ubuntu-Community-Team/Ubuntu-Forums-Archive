---
title: "Powermac G5 xubuntu 6.06 to 6.10 upgrade issues"
date: 2007-04-23
forum: Apple PPC Users
---

### Post by Kepesk on 2007-04-23
Hi!  I'm having a few issues with my first install of Xubuntu on a PowerPC platform (Powermac G5 dual 1.8).

The thing installed and ran fine from the Dapper alternate install CD; the issue presents itself when I try to upgrade from there to 6.10.  I can't seem to get it to work.

I first tried with the upgrade manager.  It got stuck with an error message, complaining that it failed to estimate the install, whatever that means.

Second, I tried the command line 'apt-get dist-upgrade' to update it.  It looked like it would take a while to complete, so I left it overnight.

When I woke up this morning, and tried to get out of the screensaver, it wouldn't accept my username and password.  So I rebooted, and noticed when it was starting up, several of the parameters had the red fail line.  However, it appeared to boot up okay anyway, until I logged in.  It accepted the username and password, but it didn't give me anything after that but the desktop color and the file manager icon.  No menus, no bar at the bottom.  I had to wipe and reinstall 6.06 to get anything else.  Now I'm worried about trying to upgrade again.  Does anyone have any advice?

Thanks in advance!

---

### Post by Auria on 2007-04-23
Updating from Dapper to Edgy via distupgrade seems to cause problems for a lot of people. If you want Edgy (but why would you, since Feisty was just released? ;) ) i would recommend doing a clean install, i had little problems with it

---

### Post by Kepesk on 2007-04-23
Is a feisty PowerPC image out?  I was under the impression that they stopped PowerPC support.

---

### Post by Auria on 2007-04-23
PPC is no more a concern for the main team, however a team of volunteers continues to maintain it.

See this thread [http://ubuntuforums.org/showthread.php?t=413447](http://ubuntuforums.org/showthread.php?t=413447)

---

### Post by stmiller on 2007-04-23
Yes there is a feisty ppc disc. Just look at a few threads on this very forum to find the link. You may have to install with the alternate CD in text mode, if the live cd doesn't work. 

I use Feisty on my powermac G5 dual 2ghz. So you have support from me, FWIW. :)

The pre-feisty ubuntu releases did not ever work on G5 machines. The kernels ubuntu released did not load the thermal modules correctly, and the ubuntu devs did not care to fix it. (And they told me so!)

So you must use feisty, or if using an older version of ubuntu you must compile your own kernel with thermal support.

---

### Post by Kepesk on 2007-04-24
Well, that's Ubuntu, but no Xubuntu?  I can't find a working link for Xubuntu Feisty PowerPC, not even for beta.  Can I assume that it just can't be found?

Thanks guys, for all the advice.

---

### Post by stmiller on 2007-04-24
Yeah, no xubuntu ppc disc. You'll have to install with that Feisty image, then apt-get install xubuntu-desktop

---

