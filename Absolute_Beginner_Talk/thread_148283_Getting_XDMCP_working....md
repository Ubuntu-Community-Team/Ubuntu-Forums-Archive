---
title: "Getting XDMCP working..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by bluewomble on 2006-03-21
I'm having a strange problem getting XDMCP working with Breezy Badger... 

I've gone into the Login manager setup thing and clicked "Enable XDMCP" to allow remote sessions... Using my Windows PC (using cygwin and something like "xwin :0 -query 192.168.2.92") I get a login prompt and I can login, however after that, it just shows me a blank desktop with not menu or taskbar...  Am I doing something obviously wrong?

Thanks in advance for any help.
Ash.

---

### Post by bluewomble on 2006-03-22
I still haven't had any joy with this... any ideas?

I can get a login screen remotely via XDMCP, but once I log in, I just get a blank desktop (with the brown Ubuntu picture), with no menu bar at the top or task bar at the bottom... any idea what I'm doing wrong?

Cheers,
Ash.

---

### Post by bluewomble on 2006-03-22
No ideas?  Anybody?  I used to have this set up quite nicely on Mandrake... over XDMCP, my XWindows session would look exactly as if I had sat down at the server machine locally... but with Ubuntu, it just doesn;t seem to have worked...
Ash.

---

### Post by patrick295767 on 2006-03-22
I do it with : 
X -query IP_address :2.0
or
with gdm login manager (in session stuffs)
  
Check that gdm is running on the server.
/etc/init.d/gdm start

Greetz

---

### Post by bluewomble on 2006-03-22
Hmmm... doing X -query 192.168.2.92 :2.0 didn't work -- it gave exactly the same problem as before (i.e. I could get a login screen but once I logged in I don;t get a menu or task bar)

Interestingly, when I used the XDMCP Chooser from another Ubuntu machine, I could sucessfully connect to the server machine (i.e. logged in, then got a menu and task bar), which would suggest I'm doing something wrong on the windows side with:

X -query 192.168.2.92 :2.0

Are there any cygwin configuration files I've forgotten to set up?

Thanks very much for your help... I think I might be getting somewhere... slowly ;-)

Any more ideas?

Cheers,
Ash

---

### Post by obiyoda on 2006-03-30
Ash,
I am trying this with windows xp and linuxtsc (linuxtsc.org) any way I have the same problem that you are having however if I disable windows firewall it seems to work fine. Trying to track down which ports windows XP firewall is blocking that it shouldn't. Don't know if this will help but it may be worth a try if you haven't tried already.

---

### Post by ptlinux on 2006-06-17
I have exactly the same problem with Linuxtsc, I turned off my windows firewall, however the problem still persists. Any advice will be greatly appreciated.

thanks in advance,

pt

---

### Post by houstonbofh on 2006-06-20
I hate "Me too" posts, but **"Me Too!"** :)  I am using Xming on Windoze, and Putty for ssh.  I can start apps.  I can run nautilus with or without desktop.  But even with desktop, it does not have any title/menu bars. I **Need** this to support several clients.  Help!

---

### Post by obiyoda on 2006-06-20
I never got xdmcp working under windows xp Pro. I did find that for what ever reason it worked fine under windows xp home edition once I disabled the firewall.  I eventually gave up on it as I could find no work around for it. You may want to check out the FreeNx project. There are a bunch of threads about it in the forums here. This post may help getting it set up [http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx]("http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx")[http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx](http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx)

---

### Post by houstonbofh on 2006-06-20
I am aware of FreeNX, but I am stubborn. :D  The config on my WinXP system will work XDMCP to several commercial Unix distributions.  And there is no difference between XPPro and XPHome.  This problem just bugs me!

---

### Post by houstonbofh on 2006-06-21
**It Works!**  Determination pays off!  It is slow, but no consistently works.  (How ever it works best when no one is logged in to the console.)  Under System -> Administration -> Login Window Prefs, press the Security tab.  Check both "Allow *** System Administrator login" and **Uncheck** "Deny TCP Connections to Xserver."  It claims it will not effect XDMCP, but it lies. :D  It is slow, and not a solution for all (Perhaps not even me) but it does work!

---

### Post by mandeep kaur on 2007-08-30
Hello,

I was able to get into xdmcp. but the problem I am facing is the greeter application appears to be crashed  is it possible to restore.

please help

Thanks

Mandeep Kaur

---

