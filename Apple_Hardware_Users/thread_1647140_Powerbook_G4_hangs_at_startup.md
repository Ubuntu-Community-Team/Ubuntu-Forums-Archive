---
title: "Powerbook G4 hangs at startup"
date: 2010-12-16
forum: Apple Hardware Users
---

### Post by user1397 on 2010-12-16
So my friend surrendered his old powerbook g4 to me the other day.  He said it 'crashed' and wanted me (the computer geek) to take a look at it.

So it starts up, I see the apple logo and the loading circle, eventually it goes to a blue screen and a mouse cursor pops up (which I can move around). But then, the cursor disappears, and another loading circle...loads? Still a blue background...then it just does that forever.

I've tried a few things from this article: [http://support.apple.com/kb/TS1411?viewlocale=en_US](http://support.apple.com/kb/TS1411?viewlocale=en_US)

Holding shift at startup does not work.
I was able to get into single-user mode but none of the commands work because it says the disk is 'read-only' for some reason.

Running fsck there are some I/O errors and it attempts to repair some bad sectors...but hangs.

Does this just sound like the hard drive is fried? Or what else could it be?

My friend said he didn't do anything out of the ordinary before this happened.

---

### Post by shawnhcorey on 2010-12-17
Does it boot using a Live CD?

---

### Post by user1397 on 2010-12-17
> **shawnhcorey said:**
> Does it boot using a Live CD?

Yes it does! i forgot to mention that in my last post.  I downloaded and burned the maverick powerpc image, and the mac booted it perfectly.  I could peer into the hard drive (I mounted it), but it also said it was read only so there wasn't too much I could do.

---

### Post by shawnhcorey on 2010-12-17
Try mounting the drive with sudo.  On a Live CD, there is no password.

```
sudo mount ...
```

---

### Post by user1397 on 2010-12-17
> **shawnhcorey said:**
> Try mounting the drive with sudo.  On a Live CD, there is no password.

```
sudo mount ...
```
I've already tried that. No matter what, it still says it's a read-only filesystem and I can only view certain folders in the mac hd.  Some folders have a grey x in the corner, and when I try to open them, it says that I don't have the correct permissions.

I've tried several commands using sudo, such as mv and cp of certain system files (like the /Library/Preferences/loginwindow.plist file which has the startup program list) but it won't let me do anything...

I've even tried a sudo chmod to no avail...

If I can't recover the OS, I want to at least recover the important documents, but I can't even copy his home folder without permissions...help! :confused:

---

### Post by drkages on 2010-12-21
Did you try a more specific tool like Partition Magic.

I use it when ubuntu fails for my data recovery needs, however seeing that is a powerbook not sure if will even load

---

### Post by user1397 on 2010-12-21
> **drkages said:**
> Did you try a more specific tool like Partition Magic.

I use it when ubuntu fails for my data recovery needs, however seeing that is a powerbook not sure if will even load

hmm well I've never used Partition Magic but I have used things like GParted...are they basically the same?

Still, I don't see how something like GParted could help me, as far as I know it can only create/resize/delete partition on a hard drive.

---

### Post by yugnip on 2010-12-21
You need the disk for the apple OS he is currently running. From that you can run Disk Utility repairs to see if it's the HD or just corruption. In lieu of having a disk, you could alternatively connect it to another mac via [Target Mode]("http://support.apple.com/kb/ht1661") and run Disk Utility that way.

Hope this helps

---

### Post by user1397 on 2010-12-22
> **yugnip said:**
> You need the disk for the apple OS he is currently running. From that you can run Disk Utility repairs to see if it's the HD or just corruption. In lieu of having a disk, you could alternatively connect it to another mac via [Target Mode]("http://support.apple.com/kb/ht1661") and run Disk Utility that way.

Hope this helpsThanks. I'm going to try an install disc next, and thats the last thing I can do.  It keeps saying disk I/O error whenever I try to perform any command in single-user mode, so I'm pretty sure the drive's just fried, but can't be too careful...

edit: actually I was wondering, when I booted up the ubuntu live cd, i could peer into the mac osx drive and see all of the folders.  In the home directory though, inside the user folder, all of the folders which are important, such as documents, pictures, music, and videos are all grayed out sotospeak, and I can't copy/move/paste/anything with them.  Is there a way to override this using ubuntu? I can't really think of another way to safely copy the important documents...there's definitely some stuff in there that would be quite disastrous to my friend if he were to lose them...

---

### Post by yugnip on 2010-12-22
If the drive isn't too corrupted (it mounts) accessing via Target Mode as  I stated above would be the easiest way to grab the files needed. 

Otherwise, in linux, right click on the files/folders you need and choose 'open as admin'.

---

