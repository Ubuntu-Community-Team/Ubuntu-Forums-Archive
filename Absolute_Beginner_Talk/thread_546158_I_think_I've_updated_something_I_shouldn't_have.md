---
title: "I think I've updated something I shouldn't have"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by lsweet on 2007-09-08
So it seems that I've installed something I shouldn't have -- and I can't figure out what it may have been.

I believe was checking out alternate multimedia pacakages for creating my own DVD's and added a repository to my system, downloaded whatever it was that I was downloading and then was prompted to do updates.  I opened the update manager and was presented with a host of items to download/update.

I glanced through them and found that none of them seemed out of the ordinary and updated.  Everything was fine.

Today I worked away at enabling my G15 keyboard, rebooted X as instructed and when I loaded back into X, my window borders were all gone.  I fiddled with Compiz/Emerald for a bit to find out the culprit and discovered that emerald was it.  I decided to just take it out and reinstall it.  Now, it won't install.  Gives back an error of:

```

emerald:
 Depends: libemeraldengine0 but it is not going to be installed

```

I can't install that package independently either...

As a side note, when doing playback of music, I'm getting static -- something that was also working before.

So the big question is, is there a way of identifying updates in the system and perhaps removing/downgrading back to where there was no issue?

---

### Post by noworry on 2007-09-10
I have also updated from the repos today and I lost all my window borders (using Ubuntu feisty, compiz-fusion, amaranth repository). So I tried to reinstall compiz fusion and emerald and got the same error, unable to install emerald or libemeraldengine0. Don't know whats wrong where. Can anybody help in this?

---

### Post by noworry on 2007-09-10
I got my emerald window borders back !!!, of course by reverting to the older version of emerald. Here are the steps,

first get your standard ubuntu borders using command the "metacity --replace &" (you can use this one to get ubuntu borders, whenever it disappears)

comment out or uncheck all the other repositories you have added except the standard ubuntu and the amaranth repo.

do an "sudo apt-get update" and then install emerald by doing "sudo apt-get install emerald emerald-themes".

replace your current window decorator by running "emerald --replace" and you ll get your emerald themes and borders back !!!

---

