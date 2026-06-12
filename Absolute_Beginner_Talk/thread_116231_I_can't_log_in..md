---
title: "I can't log in."
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-12
Hey, I am having troubles logging into Ubuntu.

When I enter my user name and pass word, the little jingle music thing comes up; then the little loading bar thing with all the icons on it, then the screen goes black, and takes me back to the log in screen.

I've a dual boot Breezy/WinXP; But I've never had this problem before.

Any ideas?

Thanks

---

### Post by matthewv on 2006-01-12
Sounds like a problem loading GNOME... What, I don't know...

---

### Post by Jimmey on 2006-01-12
Right, well, I'm not too bothered about a re-install, if that's what's necessary, but....
How, using the "Failsafe terminal", do I get to the contents of a CD, erase them, and put a newly created ter.gz backup archive on there?

I tried apt-get install ubuntu-desktop, that didn't work.

Thanks

---

### Post by Thirsteh on 2006-01-12
Hmm, try this:

When at the login screen, hit CTRL+ALT+F2, then login there. Now type 'sudo killall gdm', followed by 'startx' (NOT sudo) now when it crashes, hit CTRL+ALT+F2 again and see what error message you received, if you got any.

---

