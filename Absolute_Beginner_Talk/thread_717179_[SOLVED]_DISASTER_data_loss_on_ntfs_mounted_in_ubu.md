---
title: "[SOLVED] DISASTER data loss on ntfs mounted in ubuntu"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-03-06
My hard drive has an NTFS partition first with Windows XP x64 and an ext3 partition for Ubuntu next, and then the swap. I had the NTFS partition mounted while using Ubuntu, and while a very important folder was selected I accidentally pressed delete. It is very near the up arrow on my keyboard, don't ask. I didn't find the folder in the trash; I suppose this is because it was on a windows partition?

WHAT DO I DO??????:confused::confused::confused: This could be a big disaster if there is no way to get the files back.

---

### Post by {BzF}~JOKesTER on 2008-03-06
One Thing You Can Try Is In The NTFS Drive Folder Click The "View" Tab In The Top Of The Screen In The Folder - And Click "Show Hidden Files" Now There Should Be A New Folder Named ".Trash-username" {Replace Your Username With username} And In That Trash You Should Find Your Folder - {Unless That Delete Command Overides The Trash - Doubtfull}

Hope This Helps 

Tell Me If It Works Out

:)

---

### Post by HereInOz on 2008-03-06
First up you need to unmount that drive IMMEDIATELY, and remove it from the machine, to make sure that no more data is written to it.

You then need to put that drive in a Windows machine, and run a data recovery program which will "undelete" the file and get it back for you.

There are many around - some you pay for, some you can get for free.  Typically the pay for ones are better at getting things back, but if you have just done this, and not written any data over it, you may get it easily with a free utility.

So, after you have removed the NTFS drive, to save any inadvertent overwrites, search for undelete utilities or data recovery utilities with something like Google, or check out places like download.com, nonags.com, and those sorts of things.

Good call from the Jokester, though, hunt around for .Trash-username and you may get lucky.

---

### Post by {BzF}~JOKesTER on 2008-03-06
He Doesn't Need To Do Ant Of That If It's Still In The NTFS Drives Trash Dude..

Chill.:popcorn:

---

### Post by HereInOz on 2008-03-06
Exactly, that is why I wrote the last line of my post.  If it is still there, he is in luck.

Not Dude by the way.  Never have been, never will be.

---

### Post by {BzF}~JOKesTER on 2008-03-06
Ok Sorry I Won't Call You Dude - lol

---

### Post by dinostabOMG on 2008-03-06
Thank you both very much, especially for your promptness!!

The .trashes folder was still there. I got everything back. And much more easily than I was expecting.

I will even likely make my deadlines, which I was NOT expecting.

THANKS.:)

edit: I realise the solution was simple and my panic does betray my n00bery. But, that is why I frequent this forum, and the simple solution was just what I needed. Whew.

---

### Post by {BzF}~JOKesTER on 2008-03-06
No Problem - Everyone Needs Help Once In Awhile:KS:KS:):):)

---

### Post by dinostabOMG on 2008-03-06
A quick afterthought: Is there a way to get Nautilus to ask me "Are you sure you want to do that" like Windows does when I accidentally hit delete? Even if only in secondary volumes. That would have saved me some stress today.

---

### Post by ThreeTrees on 2008-03-07
I'm glad you're O.K. now.  The info in this thread will help if I do something similar!

Your problem is the kind of thing I meant when I posted [http://ubuntuforums.org/showthread.php?t=716558]("http://ubuntuforums.org/showthread.php?t=716558").

---

