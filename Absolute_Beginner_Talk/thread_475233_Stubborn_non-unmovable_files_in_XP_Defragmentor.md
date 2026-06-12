---
title: "Stubborn non-unmovable files in XP Defragmentor"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by pluviosity on 2007-06-15
Hi,

I'm trying to set up my Dell Inspiron 6000 for dual-boot with XP.  I've defraged my harddrive several times so that I can partition it, but there's a chunk of non-unmovable files near the end that won't move.  Any suggestions?

---

### Post by Bohlio on 2007-06-15
I've heard that that is ok, But dont hold me on that, Wait for a more educated member to back this up :-)

---

### Post by Skidpad on 2007-06-15
A copy/paste from my answer the other day when this came up (I had the same problem when installing):

"Here are a couple of threads I posted in regarding installation on an XP laptop (mine included). It's probably your hibernation file - XP won't let Ubuntu move it for installation...but you can - read these links"

[Link #1]("http://ubuntuforums.org/showthread.php?t=378825")

[Link #2]("http://ubuntuforums.org/showthread.php?t=366409")

---

### Post by pluviosity on 2007-06-15
Skidpad, I tried the advice in the links you posted.  It DID get rid of the green unmovable files, but those were already at the front of the drive.  I have some blue so-called movable files at the end that have been in the same position despite defragging a lot.  Got any other ideas?

---

### Post by ryanVickers on 2007-06-15
Is it green?  This is the page file, kind of like a swap partition on linux.  I would just do your partitioning, it should be fine.

Oops, too slow!

---

### Post by Skidpad on 2007-06-15
You may want to download the trial version of Diskeeper, which is a more advanced/complete defragmentation program.  I tried it before finding the soutions I posted above.

[Here]("http://consumer.diskeeper.com/downloads/Downloads.aspx?RId=1220&SId=1&CId=1&Aeid=0&Apid=0")

The pagefile can be disabled...see links in post 3 above.

---

### Post by ryanVickers on 2007-06-15
Good idea.  I still think the best tool for not being fragmented is using linux! :p

---

### Post by pluviosity on 2007-06-15
Haha, that's one of the reasons I'm giving Ubuntu and Linux a chance :)

---

### Post by pluviosity on 2007-06-16
OK, I ran Diskeeper a couple of times, even boot-time, with no luck :(

---

### Post by ryanVickers on 2007-06-16
How much is it, say, in pixels?  if it's just a couple tiny stripes on a HD bigger than about 20Gb, I would say it's fine!

That's one of the nice things about gparted, and why it does what windows disk management itself can't - it moves the files out of the way while resizing.

---

### Post by pluviosity on 2007-06-16
I've attached a screenshot of the defragmenter.  It's the blue near the end that's giving me trouble.

---

### Post by ryanVickers on 2007-06-16
Doesn't seem like too much.  Is it actually giving you trouble, or are you just scared to shrink it with them there?  Because it should be fine; that's not alot - I once had about 8 pieces about half that size and it worked fine.

---

### Post by pluviosity on 2007-06-16
I just don't wanna lose my data.  I've backed up nearly everything important, but I need Windows in one piece at least until August when I go back to college because we only have dialup at home >.<

---

### Post by mcduck on 2007-06-16
Booting windows into safe mode before running defrag has always allowed it to move those files at the end of the partition. But based on that screenshot those files should already be movable. It seems just that windows defrqag is too stupid for the task :D

I'd say the best approach is to take backups of all important stuff and then just install Ubuntu.

---

### Post by floke on 2007-06-16
You can turn the page file off - not sure how so best google it - its somewhere in power management or whatever (forget how to use Windows ;)). But don't worry about it I had this before I discovered the page file thing and it shrinks fine - just demonstrated how crap Windows is really.

---

