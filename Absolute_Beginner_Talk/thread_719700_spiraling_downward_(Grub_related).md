---
title: "spiraling downward (Grub related)"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by lookitseman on 2008-03-09
OK, let's start down this very bad chain of events

[LIST=1]
[*]Installed Eclipse w/Aptana, Ubuntu Studio Theme w/Apps, (maybe a few other apps)
[*]Next thing I know, I can't boot up...some error before I hit the the login screen. Looking back I wish I had written it down.  Pretty sure it was gnome related.
[*]Logic kicked in, booted from the live-cd, used that xorg.conf to overwrite my current xorg.conf, figured it'd give me a clean slate.
[*]Rebooted and got to my desktop :).  Repatched my audio (to asla something.15), and found that Jack Control is giving me hell.  I also started getting gnome-settings-daemon errors :(....realized that the xorg.conf patch probably wasn't the best route.  Found plenty of threads on the daemon topic, none seemed to give the answer I was looking for.  As a result, none of my other drives were mounting either.  [Posted]("http://ubuntuforums.org/showthread.php?t=440648&page=2") about the jack control problem...no luck.
[/LIST]
Fast forward a few days to last night...
[LIST]
[*]Moved my documents to another partition and decided to overwrite the current partition from a image made using partimage a month ago (using live-CD).
[*]Rebooted to see that somehow the rt kernel options are no longer in GRUB, only the generic kernel (and I don't even know what that is...) !?
[*]Went through a tutorial to fix my GRUB, no luck.  After doing a little research, I went to my /boot folder, and found the vmlinuz files for the generic kernel, but not the rt, where'd they go?
[*]Rebooted into Live-CD again to wipe that partition and just start completely from scratch, thinking that would help (good 'ol logic again).  After install the GRUB options haven't changed and the vmlinuz files for the rt kernel are still missing! :mad:
[/LIST]

So that's where I am now. I'm a programmer/computer geek, but I'm also a linux noob...making me just smart enough to be dangerous on this thing.  Partitioning and GRUB blows my mind, I follow the steps in the tutorials, but I have no clue what I'm doing.
[LIST]
[*]What's the generic kernel?
[*]Where'd my vmlinuz files for the rt go?
[*]Where did those vmlinuz files come from?
[*]Why weren't the rt files recreated when I reinstalled Ubuntu?
[*]what's the purpose of a /boot partition?
[*]Is there a failsafe to get around those gnome-settings-daemon errors and just start from a clean slate like I (poorly) tried to do?
[*]How would I get back to my old (and newly formatted) Ubuntu Partition?
[/LIST]

I'm so lost...any and all help would be great.  Vista is my Linux failsafe (backwards logic, I know), anchored into partition slot 1, so I guess I'll be on there while I figure this out.

Thanks!!!

---

### Post by HermanAB on 2008-03-09
Learn how to compile and install the kernel from source.  That will take you through the whole process.

---

### Post by lookitseman on 2008-03-18
> **lookitseman said:**
> 
[LIST]
[*]What's the generic kernel?
[*]Where'd my vmlinuz files for the rt go?
[*]Where did those vmlinuz files come from?
[*]Why weren't the rt files recreated when I reinstalled Ubuntu?
[*]what's the purpose of a /boot partition?
[*]Is there a failsafe to get around those gnome-settings-daemon errors and just start from a clean slate like I (poorly) tried to do?
[*]How would I get back to my old (and newly formatted) Ubuntu Partition?
[/LIST]


Generic kernel is apparently what I've supposed to be using all along...it seems to be the standard.  The 'rt' kernel I have been using stands for realtime, which is apparently streamlined for purposes like audio recording.

One question down!

I ended up scraping the whole install and starting over, I've done this three times now, it's getting frustrating.  I grew a brain and wrote a script to mass-install packages and programs that I had on my system in the event that I need to wipe everything clean again.  It means I have to reconfigure programs and such but it saves me tons of time reinstalling everything.  I keep all of my files on a separate partition anyway, so no big loss.

I'm also doing regular(-ish) backups using a method I saw in a [Ubuntu Weekly Newsletter]("http://ubuntuforums.org/showthread.php?t=713369") which apparently has stood the test of time.

---

### Post by handydan918 on 2008-03-18
The script sounds useful...care to share it?

:)

---

