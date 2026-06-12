---
title: "[SOLVED] Bootup / Check Disc Error: Last Mount 49,710 Days Ago"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-14
So I've been running a dual boot of Ubuntu Feisty (and Windows XP) for about a week now. I did the default guided dual boot setup from the live disc, didn't mess around with any advanced stuff. Just the guided partition on the hard drive.

For a week, I haven't had any boot problems. I haven't been tinkering with any thing crazy. Today I restarted the computer for some other problem and when it was loading up Ubuntu, it said something along the lines of "hasn't been checked for errors in the 27 startups" - which was freaky, but reasonable - I tend to shut down my computer a lot and I probably have started it up 27 times since I installed. It didn't find any errors, and loaded up fine.

Well, I had to restart again, and this time I got a crazier message along the lines of:
Super Block Last Mount is in the future
Super Block Last Write is in the future
Drive hasn't been checked for errors in 49,710 days

I freaked and quickly looked for a pen, started writing stuff down. When I got one, I came back and it had a red "Error" message and I didn't have time to jot it down, it said it was fixing it and it fixed it very fast - and loaded up Ubuntu like normal and I wasn't able to see the error specifically.

I am scared to shut down now. I am wondering

1) Why this happened out of the blue when it was fine for a week?
2) What it means? (I know I don't have the error message, but at least what is the deal with the in the future/49,710 days bit)
3) Should I be worried?
4) Will this affect my Windows, or is this contained in Ubuntu?
5) Has anyone seen this before?

Really any comments would be appreciated - this kind of stuff scares me because this computer has never had any problems, and when I started seeing stuff like this on any old computer I've had before, it was usually the beginning of the end.

---

### Post by BobCFC on 2007-07-14
I had a similar message the other day when I reset the bios and the date was set to the year 2000. Is your clock set to 1871 lol?

It was fine when I set the correct date. I wouldn't be too worried about loosing data or anything.


Once I had a dual boot set up where ubuntu and xp had a scandisk war when I rebooted.  I never lost anything.



EDIT: Also if you want to go back and look at the messages from bootup look in the file /var/log/dmesg
There also seem to be fsck specific logs in the /var/log/fsck directory

---

### Post by keyboardashtray on 2007-07-14
> **BobCFC said:**
> I had a similar message the other day when I reset the bios and the date was set to the year 2000. Is your set to 1871 lol?

It was fine when I set the correct date. I wouldn't be too worried about loosing data or anything.


Once I had a dual boot set up where ubuntu and xp had a scandisk war when I rebooted.  I never lost anything.

LOL - I never had to mess around with BIOS, so I don't see how it could have gotten the impression it was 1871 - unless....you know, I did pick Chicago as the city in my time zone when I set the date - maybe my computer is having a flash back to the Great Chicago Fire. I'm beginning to see a connection...

In all seriousness, it's good to hear somebody had a similar problem, and that you never lost data. I'm going to have to lookup Scan Disc war situations, Windows did do one right after I installed Ubuntu but that was it. I haven't been going in to Windows much, but I did today. And I have a few times before today, too. Just not a lot.

Still, I didn't mess around with BIOS settings, and other than my two scans in Ubuntu today and my initial scan in Windows after I installed Ubuntu, I haven't had any scan disc problems, and I just wonder why it all came out of the blue.

---

### Post by keyboardashtray on 2007-07-14
> **BobCFC said:**
> EDIT: Also if you want to go back and look at the messages from bootup look in the file /var/log/dmesg
There also seem to be fsck specific logs in the /var/log/fsck directory

I checked /var/log/dmesg, and a few others in there, using Find to find the word Future (which I know was in the original msg at start up) and didn't find any reference. I also checked /var/log/fsck.

---

### Post by ReaderRat on 2007-07-14
Ubuntu checks the integrity of the file system on a regular basis, I believe every 30th bootup. This is normal and nothing to worry about. It also does this if the BIOS clock is off, sometimes.

---

