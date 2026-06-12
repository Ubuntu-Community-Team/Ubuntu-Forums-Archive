---
title: "zinf problem"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-11-05
Greetings, for some reason, today, I started having issues w/ Zinf (audio-music player).  I cannot get it to run, if I click via icon method, it would start, splash screen and then exit.  If I drop in to root terminal, I can start it, but it doesn't seem to want to find any *.ogg files.

Now, I've been using it for a week/two w/ no problems, but today all sorts of issues started up...

Now, in Terminal window, (not root), this is the error I'm getting:

tom@sonic:~$ zinf
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
tom@sonic:~$


I've removed, purged, cleaned, what I could find that refers to Zinf, and reinstalled, and yet, still same problem...

Any thoughts?

Thanks!

---

### Post by kalos on 2005-12-04
Sudden problem huh? Have you (or someone else on your ubuntu) done any updates recently? Or do you have apt-get running automatically? You could have updated a library used by zinf.

-kalos

---

