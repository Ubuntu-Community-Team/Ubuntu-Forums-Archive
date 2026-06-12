---
title: "Utterly Bizzare"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by rhylan on 2007-08-26
Hi everyone, I've only been using Ubuntu for the past 3 days so there may well be a simple explanation for this but I can't understand why this is happening. 

My 2 problems are (and I believe they are connected) is that first, my bit torrent client Ktorrent starts leaking memory as soon as I open it, literally from the first second. Its pretty bad as well. It instantly uses up about 300mb of memory which means that I pretty much always have to re-boot after trying to open it. I have no idea why this is...

My second problem is that other torrent programs like Azureus just vanish the minute I open them. I open the program, it starts up then literally just closes a few seconds later of its own accord. I have caught Ktorrent turning itself off a few times before (not instantly, maybe after a few hours usage), but to be honest at the time I thought I was just going mad and that I had turned the program off myself. 

I've got no idea why these two problems might be, but I think they're connected because they both happened at the same time. I first found out about the memory leakage when I left Ktorrent on overnight, then in the morning found it had turned itself off. When I tried to restore the program thats when I saw how much memory it was leaking. I've tried re-booting (obviously) as well as re-installing Ktorrent. When I gave up on Ktorrent I tried downloading Azureus and thats when I found out about the sudden closing problem. Similar things have happened with all programs that I've tried to download torrents with, even opera!

Again, I might be missing something quite simple here but I can't fathom any reason at all why these two faults may be.

Thank you for your time, and for any help that you can spare.
Rhylan.

---

### Post by Her Ghost on 2007-08-26
re: Azureus Problem:

I had the same problem with azureus, deleting the  ~/.azureus/logs directory fixes it.  I think I read that it was something to do with the Azureus updater - you can check this by running it from the console and checking the output (I think that's what I did, anyway!).

---

### Post by wolfen69 on 2007-08-26
bittornado and bittorrent (ubuntu's default torrent manager) work great. try one of those if you cant figure out your problem.

---

### Post by rhylan on 2007-08-26
Cheers, just tried Bittornado and it seems to work fine, so thanks for the heads up on that one. Still can't get my other programs to work however but I may just have to accept that as one of Ubuntu's little quirks. Which is no big deal really, I can't imagine Ubuntu will be like  XP, which had hundreds of little 'quirks'

---

### Post by rhylan on 2007-08-26
Thanks for your quick reply herghost, I know i'm being amazinly noobish here but I can't find that particular directory on my system, would love to try it. Do you reckon it could be a problem with java? I could just be clutching at straws with that theory though,..

Thanks for your help!

---

### Post by Hobo Joe on 2007-08-26
I've had that same problem with Azureus.

I just installed Deluge. It's another torrent program, and it seems just as good as Azureus.

---

### Post by Anzan on 2007-08-26
> **rhylan said:**
> Thanks for your quick reply herghost, I know i'm being amazinly noobish here but I can't find that particular directory on my system, would love to try it.

A GUI way of doing this: check the option "view hidden files" in your home folder.

---

### Post by Mud.Knee.Havoc on 2007-08-26
> **rhylan said:**
> 
My 2 problems are (and I believe they are connected) is that first, my bit torrent client Ktorrent starts leaking memory as soon as I open it, literally from the first second. Its pretty bad as well. It instantly uses up about 300mb of memory which means that I pretty much always have to re-boot after trying to open it. I have no idea why this is...

My second problem is that other torrent programs like Azureus just vanish the minute I open them. I open the program, it starts up then literally just 

Ktorrent is a program with fantastic potential... I used to go back to it over and over again, hoping that the showstopping bugs would be fixed (yes, I submitted bug reports), but there would always be some other kind of bug that would turn me off.  I finally gave up on it.

I've been using Azureus ever since, with no problems.  The problem that you've been having, with it refusing to open (or loading, then disappearing) is something I've run into, and judging by this forum, many others have, as well.  Check out this link for a solution on page 2: [http://ubuntuforums.org/showthread.php?t=473676&highlight=azureus+problem&page=2]("http://ubuntuforums.org/showthread.php?t=473676&highlight=azureus+problem&page=2")

It's a problem with a particular version of java not getting along with Azureus.  Easy to fix, thankfully. :)

---

### Post by Mud.Knee.Havoc on 2007-08-26
Just a follow-up explanation that will come in handy in the future...

In linux, a file or directory beginning with a period (.azureus) will be hidden.  You can see it by clicking "View Hidden Files" as another poster mentioned, or if you're using the command line, just "cd" into it as if it's any other directory.  If you check out the hidden files in your home directory, you'll be amazed... there are a lot of them!  Usually, if you need to configure a certain program, you can find its configuration files in a hidden directory or file in your home directory.

---

