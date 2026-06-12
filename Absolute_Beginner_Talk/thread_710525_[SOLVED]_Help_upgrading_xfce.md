---
title: "[SOLVED] Help upgrading xfce"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by snkiz on 2008-02-28
I decided to give AWN another try this week when i had tried before with xfce it didn't work so well, kept stealing focus away from everything else no matter what I did. this this time however ajusting the focus policy made it workable, but not quite right. now i have to move the mouse off the window and back on that works most of the time. so I did some googling and came up with a bug report for AWN that lead me to a xfce Bug Report sucess! its been fixed in the new version. now the problem i have is the last two times I've tried to upgrade xfce I ran into dependenicy issues that i couldn't figure out I was sure I got everything on the list. so what i'd like to know is does anyone know of some good instructions for installing xfce 4.4.2 or better yet the up2date svn on ubuntu?

---

### Post by Crooksey on 2008-03-01
What composite manager are you using with xfce?

---

### Post by snkiz on 2008-03-01
not using a composite manager just xfwm4. Can´t run beryl no graphics card. this is why I want the xfce upgrade I found this [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/2c8e913f5aef88b8/453097777e84a6ad?lnk=raot]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/2c8e913f5aef88b8/453097777e84a6ad?lnk=raot") and this [http://bugzilla.xfce.org/show_bug.cgi?id=3439]("http://bugzilla.xfce.org/show_bug.cgi?id=3439")  on my cell this the first time I´ve had a chance to sit down and look at them

---

### Post by snkiz on 2008-03-01
there is a patch posted but I have no idea what to do with it.[http://launchpadlibrarian.net/10696841/xfwm4-4.4.1-dock-window-fix.patch]("http://launchpadlibrarian.net/10696841/xfwm4-4.4.1-dock-window-fix.patch")

---

### Post by snkiz on 2008-03-02
Just an update, I read in those bug reports posted above that the patch had been applied in xfwm4 for Hardy Heron witch is version 4.4.2. since I really hate compiling, (it tends to be an exercise in frustration.) I just added the Hardy repos and upgraded xfwm4, then disabled them. A little risky I know,  but it worked! I now have xfce with AWN working flawlessly and I use xfwm4 in gnome no issues so far :)

---

