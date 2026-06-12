---
title: "Can't Access Folder on USB Drive"
date: 2010-10-16
forum: Apple Hardware Users
---

### Post by skaught77 on 2010-10-16
I have an odd problem.  First, I had a network hard drive fail that had my whole iTunes library on it.  But I had a backup on a 1 TB USB drive, so no problem.  I copied my backup to my iMac and all was good.  However, I discovered that only the A-M folders from my music library copied, leaving N-Z on the backup drive.  This happened because my backup drive started fritzing out, disconnecting randomly.  So when I try to copy over the remaining folders, the USB drive decides to stop mounting completely.  ARG.

Here's where it gets weird.  Though it won't mount to my iMac (the drive just clicks away without showing up on the desktop), it DOES mount when I turn on Ubuntu (with Fusion).  Great, right?  Well, I thought so.  All the folders on the drive appear, and I can get into all of them EXCEPT the iTunes folder.  There's an "X" on the folder and when I click on it it says, "The folder contents could not be displayed -- You do not have permissions necessary to view the contents of 'iTunes'."

Why can I get in all the other folders, but not this one folder (the only one I want to get into, of course)?  I could get into it just fine while it was mounting on the iMac.  I just want to copy the folders and be done with it.  Help!

Scott

---

### Post by MisterGaribaldi on 2010-10-17
Likely as not something has gotten corrupted on the drive.

In theory, you can always try:

Applications > Accessories > Terminal > "sudo nautilus"

That will give you an instance of Nautilus as root. Under "normal" conditions you can then do anything you want. However, even root can't cure corrupted data.

Anyhow, if that works, then probably the files and folders copied over will all inherit root ownership. You can do a recursive change ownership (i.e. "chown -R") to the resulting copied materials.

I'm also open to the possibility in suggesting all this that there may be some better way out there.

---

### Post by skaught77 on 2010-11-03
Just wanted to drop back in to say I solved the problem.  After trying every trick in the book to change permissions on the folder/files I wanted, using testdisk to fix the missing partition (it wouldn't...said I needed another program), trying to change the owner of the files, and a myriad of other mysterious sounding commands, I almost gave up.  I have no experience with Linux or using terminal commands, so I fully expected to do something eventually that would destroy everything.
 
I had tried the "sudo nautilus" command, which let me open the folder and see all the music files, but when I tried to copy them, it told me I didn't have permission.  It even let me play the songs, but not copy or move them.  So I knew the files were there and they WORKED.  At the last moment, I tried the "send to" menu option you get when you right-click on the files and to my amazement...it worked.  I copied all my missing iTunes music over to another drive (thousands of songs) and everything was perfect.
 
PHEW.  Why the thing won't let you "copy" files, but will let you "send to" files, I have no idea.  I wasn't going to debate with the drive.  
 
Now...time to go back to my original REALLY dead drive (two 500 GB LaCie drives linked together to make a 1 TB drive) to see if I can relink them or whatever to save all my movies files.  The iTunes library on my backup drive was the important thing, though.
 
Thanks!
 
Scott

---

