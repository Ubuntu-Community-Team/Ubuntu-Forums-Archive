---
title: "Gnome-panel properties =&gt; fails"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2006-05-04
When I right-click on the gnome-panel and click on properties, i get an error message saying that gnome-panel must be restarted [the generic ubuntu message when a gui fails].

sudo apt-get install --reinstall gnome-panel

does not fix the problem.

Anyone have any ideas.

[P.S.] - I get a glimpse of the properties dialog before the message box pops up.

---

### Post by mybootorg on 2006-05-13
This seems to be a fairly common problem - I'm seeing the same thing exactly as you descibe: new panel, right-click properties, a glimpse of the properties dialogue, and then the gnome-panel app freezes.

Some suggestions I've seen: 1) reinstall the gnome-panel package.  2) chown .gnome2 to be your regular, non-root user.

However, neither of these have worked for me.  

I'm fairly persistant though, and when I find a solution I will post it here.

---

### Post by mybootorg on 2006-05-13
There is a file named .recently-used in your home directory.  If you don't see it, CTRL-H in Nautilus to unhide it.-

I was able to rename that file and reboot and that resolved my problems.

mv /home/yourUsername/.recently-used /home/yourUsername/.recently-old

I hope this works for you.  If not, I found quite a few people speculating that it's a permissions issue with themes.  Because right after they changed from, say for example, Clearlooks to Human, the problem started.   Another person was insisting it had something to do with a wireless network monitor applet.  Your mileage may vary.

---

