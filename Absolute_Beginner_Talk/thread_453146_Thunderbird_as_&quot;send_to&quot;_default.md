---
title: "Thunderbird as &quot;send to&quot; default"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Mel_K on 2007-05-24
I want to make Thunderbird my  "send to" default.  I have searched for an answer, but nothing  seems to work for me.
I have tried each of the the following in System>preferences>preferred applications mail reader command

 mozilla-thunderbird %s
 mozilla-thunderbird "%s"
 mozilla-thunderbird %s

Still Evolution is the default.   What else can I try? 

I have also noticed that the command in the web browser says this:
/usr/lib/firefox/firefox "%s"
Maybe this is relevant.
Any advice would be appreciated!

---

### Post by vtel57 on 2007-05-24
Try it with just "thunderbird", not "mozilla-thunderbird" (no quotes).

---

### Post by lamalex on 2007-05-24
This is a gnome bug, we're hoping it will be fixed for gutsy. File a bug report at gnome.

---

### Post by vtel57 on 2007-05-24
lamalex,

Is the directory for Thunderbird in Feisty .thunderbird, like in Dapper, or is it .mozilla-thunderbird? That would make a difference, as I suggested in the post above.

---

### Post by Inxsible on 2007-05-24
It is in .thunderbird for Feisty. I have my Thunderbird as the default Mail Reader.

---

### Post by lamalex on 2007-05-24
thunderbird 2 is .thunderbird and thunderbird 1.5 from repo is .mozilla-thunderbird, but he means right-click >> send to which goes to evolution regardless of t-bird default, it's a bug that has been brought up a number of times but never fixed.

---

### Post by vtel57 on 2007-05-24
Ah! Well, then... I'll stick to my previous suggestion for this poster's problem. I would check my own Ubuntu, however, I'm currently booted into Slackware. :)

---

### Post by vtel57 on 2007-05-24
> **Iamalex said:**
> thunderbird 2 is .thunderbird and thunderbird 1.5 from repo is .mozilla-thunderbird, but he means right-click >> send to which goes to evolution regardless of t-bird default, it's a bug that has been brought up a number of times but never fixed.

*shrugging* I'll have to take your word for it. I'm still using 6.06.1. Thanks for the reply, though. :)

---

### Post by vtel57 on 2007-05-24
Well, just for ha-has, I booted to my Ubuntu to see what was up here. My settings in the Preferred Applications window for Thunderbird are as follows:

**Mail Reader:**

Mozilla Thunderbird

**Command:**

mozilla-thunderbird %s (with no quotes)

---

### Post by Mel_K on 2007-05-24
Thanks so much for all of the above suggestions. Much appreciated.
I have tried them to no avail and will report the bug.

---

