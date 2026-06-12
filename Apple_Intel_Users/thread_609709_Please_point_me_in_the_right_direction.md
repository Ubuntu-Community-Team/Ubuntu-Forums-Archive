---
title: "Please point me in the right direction"
date: 2007-11-11
forum: Apple Intel Users
---

### Post by Wharf Rat on 2007-11-11
I figured someone here can point me in the right direction because this is not an Ubuntu problem. 

My daughter has a Mac iBook G4.  OSX 10.4.?

It suddenly has problems launching certain programs.  Firefox dies just after it tries to load a new (or restore) session.

Same for MS Word.  In fact nothing that is a web browser will load.

In order to reload Firefox, I had to download it to my Ubuntu machine and share the folder to slide it over to her Mac.


She is concerned about the "Happy Virus" going around her campus.  I am not too concerned about a virus on OSX.

I suspect something corrupted. (All updates are in place)  I have removed and reloaded Firefox to no avail.  I also tried to install Clam for Mac.  No luck either.  I am not really a Mac person and find it a bit frustrating.  Tried to load Ubuntu but the G4 would no cooperate.

i don't even know which Mac forums to haunt.  Please send me in the right direction.

---

### Post by ronocdh on 2007-11-11
Why not just back up her data and reformat? I hate to be so blunt, but if you're worried about corruption, do that, before you lose something. You might also want to investigate replacing the drive.

---

### Post by cyberdork33 on 2007-11-11
A G4 is not an Intel Mac, it is a PPC Mac

What tools are you using to uninstall firefox? Have you tried booting your OSX disc and verifying the disc / repairing?

---

### Post by Wharf Rat on 2007-11-11
My thanks to both of you for the response.

Don't worry about being blunt.

1. FF removal -- I just pulled it to the trash. Are there special tools for this? Honestly, I have not fooled with a Mac for years.  She only brings me the machine when it is broken.

2.  Reinstall OS - I was not really sure this was necessary.  I did perform an update.  I think there was about 50MB download from Apple and a restart.

Also, she does not know where the original OSX disk is located. 


I have been moving to Linux away from XP for several months.  Retaining the original OS disk seems like a foreign concept now.

---

### Post by cyberdork33 on 2007-11-11
there are several configuration / preference files that are not deleted by simply dragging an app to the trash. Try [AppDelete]("http://reggie.ashworth.googlepages.com/appdelete"), it is free.

You can also do repairs from the commandline after starting in single-user mode (hold cmd-s on startup). The prompt will give you instructions to run fsck.

---

### Post by Wharf Rat on 2007-11-11
Cyberdork33,
Thanks for the reply.

I found the HD utilities and ran them verifying permissions and HD.  HD reports and error that indicateds HFS needs repair.

Currently, I am following your instructions above.
/sbin/fsck -fy

---

