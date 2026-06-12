---
title: "Need HOWTO to Fix Login Window Preferences In Safemode"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-11-16
Hi,

This problem stems from another problem that can be read in full here: [http://ubuntuforums.org/showthread.php?t=190310](http://ubuntuforums.org/showthread.php?t=190310)

**Quick Summary of Original Problem:**
GDMGREETER does not load probably on Toshiba Laptops running certain ATI gfx cards - no one knows why and I have already submitted a bug to launchpad - no response yet.

There exists a temporary solution those of us who are unfortunate enough to experience this problem - edit gdm.conf for non-XDMCP logins and change gdmgreeter to gdmlogin.

This worked.

**New Problem**
A new method was proposed to get gdmgreeter to work again - I decided to jump the gun, be the guinea pig

Here's the proposal for the new fix:
> I had the same issue. This is what fixed it for me.

System/Administration/Login Window. When the "Login Window Preferences" window comes up click the "Local" tab. Change the Theme to Selected Only and Style to Themed. 

I changed my Login Window Preferences in Gnome and also changed gdmlogin to gdmgreeter.
I restarted my computer and was no abck to my original problem with gdmgreeter, the problem wasn't fixed.

Then I restarted the computer in safemode and edited gdm.conf to display gdmlogin.

Then I restarted my computer normally - same eror

Then I went back into failsafe (as root) and satrted x via the 'startx' command.

I wanted to change my login window preferences options, but when I went to system/administrator menu, there was no login preference sub menu option.

I am now stuck because I can't login into ubuntu normally....I am on my WinXP partition as I write this.

Any and all help will be greatly appreciated.

Thanks!

---

### Post by lazyrussian on 2007-11-17
*bump*

---

### Post by markharding557 on 2007-11-17
you might solve by reinstalling gdm

---

### Post by lazyrussian on 2007-11-21
Re-installing GDM didn't work. Anyway, I ended up doing something that messed up my computer - I ended up reinstalling Feisty from a fresh install and then upgrading to gutsy (this fixed everything).

---

