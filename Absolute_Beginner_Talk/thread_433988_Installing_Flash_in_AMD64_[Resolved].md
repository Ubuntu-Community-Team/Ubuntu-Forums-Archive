---
title: "Installing Flash in AMD64 [Resolved]"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Lorenzo1449 on 2007-05-05
hey folks, 

I've just installed Ubuntu for the first time and am having some problems getting the basics going, took a while to get dual screen on my Radeon 1300 and am now having probs with Flash 9 running on feisty, something to do with 64bit I think but I may be wrong.

So I have 64bit firefox installed:
  Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.3) 
  Gecko/20061201 
  Firefox/2.0.0.3 (Ubuntu-feisty)

I'm running Ubuntu Feisty 7.04 on Intel 6600 dual-core.

I have followed to the letter both [http://www.psychocats.net/ubuntu/flash#aptget](http://www.psychocats.net/ubuntu/flash#aptget) (I know it's for 32 bit but I was hoping for some clues) and [http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785).

I now have the the 32bit libraries, npwrapper and alien installed:

If I run these again I get 'newest version' for all:
  sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32
  sudo apt-get install alien

Also, I get the message 'file exists' of the following 2 commands:
  sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
  sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/

Still nothing working, it appears not to have installed flash at all.:confused: ..help please!

Lorenzo

---

### Post by Lorenzo1449 on 2007-05-05
Just one more thing to add, I've just checked the npwrapper.libflashplayer.so in urs/lib/mozilla-firefox/pligins and the properties of this file say 'link (broken)' with a small white 'x' in a red box on the icon, what does this mean and is it (likely) related to the problem I am having with flash and Firefox?

Lorenzo

---

### Post by rsambuca on 2007-05-05
I followed this guide and it worked right away for me.

[[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=341727")

---

### Post by Lorenzo1449 on 2007-05-05
Cheers rsambuca, worked for too.

Lorenzo

---

