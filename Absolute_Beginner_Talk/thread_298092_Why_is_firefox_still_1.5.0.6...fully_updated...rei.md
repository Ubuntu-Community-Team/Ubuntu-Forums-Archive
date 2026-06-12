---
title: "Why is firefox still 1.5.0.6...fully updated...reinstalled even"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-11-12
Hi all,

I've kept my system fully updated, whenever there's a system update available. I upgraded firefox to 1.5.0.7 when it was released in Ubuntu. I look at HELP ....ABOUT...and it still shows 1.5.0.6.

I went to Synaptic and checked the version number in the repos. I reinstalled, had to download 8MB, got the message that I had to restart firefox.....did so. Still 1.5.0.6.

It's no biggy, but any ideas?

---

### Post by bulldog on 2006-11-12
Well it's a shot in the dark,but how do you start firefox??

Try to start it from the original ubuntu menu and see what happens.

---

### Post by mdsmedia on 2006-11-12
Hmmmm...nice shot. I thought that might actually be it. But no different.

Thanks anyway :)

---

### Post by xyz on 2006-11-12
Yeah same here, I can't figure it out!
First time I installed
[nanotube and friends script]("http://www.ubuntuforums.org/showthread.php?t=293301&highlight=firefox+2")
I had 2.0 installed.
Then I had to restore my system (backup.tgz) and tried the script again.
About FF says 1.5.0.7 with all my bookmarks, chosen theme and so on but no sign of a freshly FF 2.0 install.

Now when I run:
```
gksu firefox
```
It opens the same (1.5.0.7) yet different FF because my chosen theme, bookmarks are gone.
I realize it's not the case but it looks like I have 2 FF 1.5.0.7...the first one seems to be the version I had before installing 2.0 and the 2nd one is the same but was installed according to the script above!!!

---

### Post by bulldog on 2006-11-12
> **xyz said:**
> Yeah same here, I can't figure it out!
First time I installed
[nanotube and friends script]("http://www.ubuntuforums.org/showthread.php?t=293301&highlight=firefox+2")
I had 2.0 installed.
Then I had to restore my system (backup.tgz) and tried the script again.
About FF says 1.5.0.7 with all my bookmarks, chosen theme and so on but no sign of a freshly FF 2.0 install.

Now when I run:
```
gksu firefox
```
It opens the same (1.5.0.7) yet different FF because my chosen theme, bookmarks are gone.
I realize it's not the case but it looks like I have 2 FF 1.5.0.7...the first one seems to be the version I had before installing 2.0 and the 2nd one is the same but was installed according to the script above!!!
I'm not sure if I understand you correctly,but firefox as a user is not the same as firefox as a root.
All changes you made in firefox as a user don't affect the root firefox.
It's basicly the same app. but with different profiles.

---

### Post by xyz on 2006-11-13
Thanks bulldog and yes I realize it's different profiles.
It seems I have a problem with the script...despite the fact that it did install fine the 1st time I ran it.
Then I had to restore my system and the script no longer does the job.
I guess I'll try to install FF 2.0 differently which is no problem but the mystery remains...

Note that the backup.tgz I used to restore was very recent.

---

