---
title: "Save Current Session &amp; Groundhog Day"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by mybootorg on 2006-05-17
Ever see that Bill Murray movie, Groundhog Day", where he gets caught in a time loop - living the same day over and over and over?

Well, one evening I decided to check the box for "Save Current Setup" when I logged out of Ubuntu Breezy and now I'm stuck in a similar loop.

To be specific, every time I log onto my machine now, the same applications pop up that I was using that one evening when I checked the box and shutdown.  The same Firefox browser comes up pointing to the same page, the same music comes up in AmaroK, etc.  It was funny at first. But after a week of it, it's becoming less so.

Two questions: what did I do that caused this?

And how do I make it stop?

Thanks,

Craig

---

### Post by halfvolle melk on 2006-05-17
That's a cool movie :mrgreen: 

I will assume you use Gnome under Breezy. Before you log-out/shut down, you can close all the stuff you don't want at start-up and again select "save current setup". 

And I just testd this: in your home dir (mine anyway) there's a directory called .gnome2. The dot in front makes it hidden, so in your file browser select "show hidden files". In that dir you'll find the file "session". If you delete it, your next session will be a clean one.

Both options should work.

---

### Post by louis_nichols on 2006-05-17
It might be because you cannot write to the file that saves the session, for some reason. Try this command first of all

sudo chown <your username> ~/.gnome2/session && chmod 700 ~/.gnome2/session

Then log out and back in and should be fine.

---

### Post by mybootorg on 2006-05-17
Thanks for your guys advice.  Indeed, it was a permissions problem in .gnome.  I'd love to know why permissions seem to get changed randomly.  I'm not doing it.  I can only assume that application installs are the culprit.

Again, many thanks.

---

### Post by louis_nichols on 2006-05-17
Permissions change when you open GUI apps with sudo. For such apps, when open from terminal, it is best to use gksudo instead of sudo. Keep sudo only for cli commands.

---

