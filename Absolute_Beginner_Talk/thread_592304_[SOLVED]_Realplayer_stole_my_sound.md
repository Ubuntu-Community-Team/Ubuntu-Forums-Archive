---
title: "[SOLVED] Realplayer stole my sound?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by tolremeno on 2007-10-26
I know there are issues with realplayer not playing nice with other programs; I just haven't had the need to try to fix it as long as all I had to do was make sure it was the only program running.

But all of the sudden yesterday, I lost the ability to have noise come out of my speakers except through realplayer.

Any help? Please?

---

### Post by mali2297 on 2007-10-26
> **tolremeno said:**
> I know there are issues with realplayer not playing nice with other programs; I just haven't had the need to try to fix it as long as all I had to do was make sure it was the only program running.

But all of the sudden yesterday, I lost the ability to have noise come out of my speakers except through realplayer.

Any help? Please?

Run alsamixer in the terminal and check if something important is muted (press 'm' to toggle mute).

---

### Post by tolremeno on 2007-10-26
nope. Nothing was muted.

And like I said, I can still get sound from realplayer ... but nothing else.

---

### Post by mali2297 on 2007-10-26
> **tolremeno said:**
> nope. Nothing was muted.

And like I said, I can still get sound from realplayer ... but nothing else.

Have you made sure that Realplayer isn't running in the background somewhere? Reboot to be absolutely positive.

---

### Post by tolremeno on 2007-10-26
Ok, this is interesting. 

I searched the forums to find out why you can't run realplayer and anything else, and I came across the alsa-oss fix ([link]("http://ubuntuforums.org/showthread.php?t=168080")). I edited realplayer's script so it started with alsa-oss, Then I restarted realplayer and amarok, hitting play in both. Then I closed realplayer and sound works with any program. 

And btw - I had the problem on a fresh session.

edit: marked solved. Thanks all!

---

### Post by mali2297 on 2007-10-26
> **tolremeno said:**
> Ok, this is interesting. 

I searched the forums to find out why you can't run realplayer and anything else, and I came across the alsa-oss fix ([link]("http://ubuntuforums.org/showthread.php?t=168080")). I edited realplayer's script so it started with alsa-oss, Then I restarted realplayer and amarok, hitting play in both. Then I closed realplayer and sound works with any program. 

And btw - I had the problem on a fresh session.

So I guess you can mark the thread as solved.

---

### Post by iflanery on 2007-10-29
> **tolremeno said:**
> Ok, this is interesting. 

I searched the forums to find out why you can't run realplayer and anything else, and I came across the alsa-oss fix ([link]("http://ubuntuforums.org/showthread.php?t=168080")). I edited realplayer's script so it started with alsa-oss, Then I restarted realplayer and amarok, hitting play in both. Then I closed realplayer and sound works with any program. 

And btw - I had the problem on a fresh session.

edit: marked solved. Thanks all!

I tried that link, read the fourth post down, edited the file mentioned, and now the sound on RealPlayer works perfectly. Thanks. :)

---

