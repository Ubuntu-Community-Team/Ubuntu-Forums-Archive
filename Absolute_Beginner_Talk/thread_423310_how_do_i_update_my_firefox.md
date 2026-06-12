---
title: "how do i update my firefox"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by tonywho on 2007-04-25
i curently use ubuntu version 6.06 and i am happy with this version and i do not wish to change it, but i do want to update my version of firefox to 2.1 . i tried checking in the package manager but i couldnt find an update for firefox. if anyone could tell me how to update firefox  it would be greatly appreciated ty :)

---

### Post by st33med on 2007-04-25
2.1 is not out yet. 2.0.0.3 is the current version. So, don't sweat it just yet.:guitar:

---

### Post by 007Bond on 2007-04-25
Well if you don't have firefox 2 you need to get that but if you do just input this into console

sudo apt-get update

and then you should have alll the updates available.

---

### Post by Delkster on 2007-04-25
> **tonywho said:**
> i curently use ubuntu version 6.06 and i am happy with this version and i do not wish to change it, but i do want to update my version of firefox to 2.1 . i tried checking in the package manager but i couldnt find an update for firefox.
Firefox 2.0 hasn't been packaged for Ubuntu 6.06, at least not yet. Generally the stable releases of Ubuntu don't get entirely new versions of software (for example 1.5 -> 2.0), only bug fixes and security updates to the original version. If you want Firefox 2.0, you'll need to either install it manually (from the Mozilla website, bypassing the package manager) or upgrade to a newer version of Ubuntu.

Also, for entirely new versions of applications for stable Ubuntu releases there's the [backports](https://help.ubuntu.com/community/UbuntuBackports) repository/channel. New versions of some applications are placed there. However, they aren't installed automatically -- you have to enable the backports yourself. Firefox 2.0 hasn't been backported to 6.06, though, so it's of no help in this particular case.

Firefox may get updated to 2.0 (or something later) in Ubuntu 6.06 at some point in case that's needed to fix security issues but otherwise it'll probably stay at the old version.

I hope this makes some kind of sense. My head isn't at its best right now.

---

### Post by louieb on 2007-04-25
The psychocats link in my signature has a how to install Firefox 2. in Dapper.
as well as a lot of other good Ubuntu stuff.

---

### Post by Drewski on 2007-04-25
Check out my thread, where I asked the same question.

[http://ubuntuforums.org/showthread.php?t=420811](http://ubuntuforums.org/showthread.php?t=420811)

---

### Post by alienexplorers on 2007-04-25
I found the easiest way to get Firefox 2.0.0.3 is to download it from Mozilla and unpack it in your home folder.  This allows you to receive automated updates for the program and it does not interfere with Ubuntu at all.  Nice thing is if you don't want it any longer you can just delete the folder and desktop shortcut.

---

