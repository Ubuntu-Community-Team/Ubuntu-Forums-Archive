---
title: "Is it hopeless?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-07
Hello again folks.

Here's the rundown...

I MOVED (not Copied) all of my personal XP files over to my Kubuntu drive, and then formatted my entire XP disk. All of the files were successfully on Kubuntu in a Folder I made just for the transfer.

After the format and re-install of XP, I MOVED (again, not copied) the files from the Kubuntu back to the XP disk. When I was setting up Outlook, I went to find the data file that had all my old e-mails and contacts, and I couldn't find it. It was late, so I shut everything down and went to bed, thinking that was the least of my worries.

However, this morning, when I went to access other files, I realized *all* of them were missing; they're not on XP, they're not on Kubuntu. Apparently, some data was moved, as every Folder that I moved is on the drive, but no files are contained within.

if it were 2-3 dozen files, it wouldn't be a problem, but *everything* from the past 4 1/2 years (about 10 gigs) are now unaccounted for.

I downloaded the program that allows Windows to see ext2/3 file systems hoping it was just a Windows fluke, but stil the same--can see every folder within the Backup Folder I created, but no files.

Is it a lost cause, or is there any way of salvaging the info?

Thanks in advance!

Jay
(very frustrated with MS at the moment)

---

### Post by whizbaby on 2006-09-07
(1)How did you *"move"* it exactly? (to check what could have happened)
(2)What you experience is because of little misunderstandings when it comes to computer data, let me explain:
Imagine a sheet of paper with a couple of telephone numbers on it. Now consider a file containing exactly this list of telephone numbers. Most people tend to think the one is like the other, but the information on the sheet would be harder to modify/remove. The file will be away in a second, and so anything in any size can be away in a second (like a couple of year's data in your case, think of a library suddenly disappearing from one sec to the other). I say this because you 'moved' data to back it up, which is a particularly bad idea (what if there is a power outage during moving, What will happen to the data?). The right way is to copy and check if everything is there (that's what you hopefully have learned now).
Real-world and computer-data have to be treated completely different. 
(3)Though, *really* erasing a file from a hard drive so that it can never be recovered (even not by professionals) and without destroying the hard drive is a task for special programs (e.g. shred), so there are chances that you still can recover the data either on the formatted drive or the partition you first moved it to (only in the case the data really was moved).  There are free programs (testdisk, to name one) which you can use to check filesystems for removed data (you'll have to read the manual).

---

### Post by enopepsoo on 2006-09-07
just don't write any files to either of the partitions until you have tried to undelete, because the OS sees empty space where the undeleter may see some of your 3 years of data.

\\:D/ \\:D/ \\:D/ \\:D/

---

### Post by whizbaby on 2006-09-07
So, in conclusion, it's not completely hopeless!

---

### Post by bodhi.zazen on 2006-09-07
How good are you at data recovery and how much time do you have?

Your best bet is to physically remove the HD in question and access it from another box. Mount the drive as RO. At this point you are hoping your data in any "free space" was not overwriten. If you keep the drive mounted rw you more then likely will have data loss.

Not sure what data recovery package would be best.

I would say your situation is dire, you almost certainly will have some data loss.

---

### Post by Imsati on 2006-09-07
Well, I managed to get it back. Somehow I put it (or it just wound up?) on the Desktop "Home" folder. I thought it was very odd as I specifically created a Folder that was burried (to reduce risk of accidentally deleting it) that only I knew where it was.

I had done work earlier (by a few hours) playing around with placing a Home Folder on the Desktop, but deleted it after I played around for a bit.

Just by pure luck I noticed the Folder had reappeared on the Desktop and instead of deleting it, I opened it up and imagine my surprise.

Yes, Move is bad...Copy is our best friend. Quite a few lesons learned.

Thank you all so much!

--Jay (who will get this Unix stuff down pat one day!)

---

