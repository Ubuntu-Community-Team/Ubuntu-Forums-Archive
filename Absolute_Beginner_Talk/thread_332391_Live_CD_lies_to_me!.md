---
title: "Live CD lies to me!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jodrre on 2007-01-06
Hello all - 

I got the book Ubuntu Hacks from Barnes and Noble.  In it was described how to let Windows control your computer, but let Ubuntu run Live and still save everything.  I did what it said to get everything ready for persistent mode (I spelled it that way, too).  It was all about labeling the USB stick casper-cow and rebooting with persistent added.When I boot the computer, I get to the normal screen.  I press F6 (it says F4 in the book) to get to the other options menu.  The book says add a space after the arguments and type persistent.  I do that, and it hangs at mounting the root filesystem.  I tried typing persistent right after the double-hyphen (so it looked like --persistent.  Not like --  persistent or -- persistent)  Still hung.  I put it after splash (or whatever last argument it was) and did a bunch of stuff.  It still hangs.  I've tried so far:

--  persistent
-- persistent
--persistent
splash persistent --
-- persistent --

Yet nothing works.  I just want to be able to run Ubuntu without reformatting my HD!  ](*,) I would reformat without a second thought, but I've got some expensive programs and I don't want to buy a new HD.  (I did read the post about letting it run on another HD, and not losing Windows.  I don't want to do it unless I have to.  Tight budget)

Somebody help me please!

---

### Post by Shatrat on 2007-01-06
You can shrink an existing partition you know.  Unless your windows partition is nearly full there is no reason why you couldn't have both on one disk without losing data, although it should be backed up regardless.  I don't know what your "expensive programs" are but if you dont have the ability to reinstall them you've already lost half the battle anyway.

---

### Post by kavon89 on 2007-01-06
A Live CD does what you want, "I just want to be able to run Ubuntu without reformatting my HD!" There isn't a need to use some Ubuntu Hacks to get it to run without touching the HD, thats what the Live CD is set up to do. Next off the Installer should have a partition resizer to keep your XP install and partition a new section for linux. Wait for a more experenced person to answer the installing part.

Also, I think your book is old... Ubuntu was probably updated with a version or two before that book even made it to the book store.

---

### Post by jodrre on 2007-01-06
I just want to be able to run in Persistent mode.  I would love to be able to walk up to a random PC, put the mem stick and CD in, and work with Ubuntu.  The reason I don't want to stick it on my HD is because that ties me down, and some places I go don't have high-speed access.  Remote Desktop is out of the question

---

### Post by kavon89 on 2007-01-06
I know that Knoppix is better at doing this persistant mode, I remember doing it but i used 500mb of my hardrive instead of a usb stick to save my persistant mode settings. Ubuntu's Live CD function is more like a 'test drive me first' then 'install me please'. Knoppix is meant to be a Live CD, but has an installer function if needed.

[http://www.knoppix.org/](http://www.knoppix.org/)

---

### Post by jodrre on 2007-01-06
idk, i've been saving up for a new HD... maybe I'll get two (or divide one in half) and put Ubuntu on it... I'm a bit upset that I can't just randomly walk up to a PC and run Ubuntu without leaving any trace.  Oh well, thanks for dealing with me...

---

