---
title: "How do I completely delete a file from a Windows Partition?"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2007-12-07
Whenever I access my Windows Partition and delete files they are not wiped.  They are simply moved to a "trash" directory.  
How do I actually delete them instead of moving them so that I can free up some space?

---

### Post by stchman on 2007-12-07
> **curiousnoob said:**
> Whenever I access my Windows Partition and delete files they are not wiped.  They are simply moved to a "trash" directory.  
How do I actually delete them instead of moving them so that I can free up some space?

You can highlight the file and do a shift-delete.  Another way to do it is the rm method.  I know that many are going to do a double take on this but if you type the following in a termial opened up in the Windows partition and type the following:

rm -rf <windows file you wish to delete>

will delete the file you wish to.  This all assumes that you have write access to your Windows partition vis ntfs-3g or the partition is FAT-32.

---

### Post by rsambuca on 2007-12-07
You can also delete them from the Nautilus file browser.  If you go to the root directory of the drive and select "View Hidden Folders", you will see one called .trash-<yourusername> which contains all of the deleted files.  You can just select that folder and delete it.  POOF!  Gone forever.  When you delete something else the folder will re-appear.

---

### Post by Mad_Dawg on 2007-12-07
You could just empty the trash the next time you boot Windows.  OR, are you accessing these files from the Linux side?  If so, how do you do that?

---

### Post by The Cog on 2007-12-07
Or in nautilus, go Edit->Preferences, click the Behaviour tab and check the option to include a delete command. Then you can right-click files end select to delete them.

---

### Post by rsambuca on 2007-12-07
> **Mad_Dawg said:**
> You could just empty the trash the next time you boot Windows.  OR, are you accessing these files from the Linux side?  If so, how do you do that?

The windows trash is different.

---

### Post by stchman on 2007-12-07
Shift-Delete is far easier.

---

### Post by Niniel on 2007-12-07
> **rsambuca said:**
> The windows trash is different.

How so?

It's the same as the standard Ubuntu trash - it's a folder deleted files are moved to. 
When you activate the "Delete" option the trash folder is bypassed. 
But does that actually wipe the file?

As far as deleting files on the NTFS partition from Ubuntu is concerned, I haven't have any problems with that... works just like files in Linux proper. 
So what is the problem?

---

### Post by rsambuca on 2007-12-07
> **Niniel said:**
> How so?

It's the same as the standard Ubuntu trash - it's a folder deleted files are moved to. 
When you activate the "Delete" option the trash folder is bypassed. 
But does that actually wipe the file?

As far as deleting files on the NTFS partition from Ubuntu is concerned, I haven't have any problems with that... works just like files in Linux proper. 
So what is the problem?

I just meant that the Windows recycle bin is not the same place as the .trash folder.  They are different.  ie. When you delete a folder on the ntfs drive from linux, it won't appear in the Windows Recycle Bin, but it is still safely in the .trash folder.

---

### Post by Niniel on 2007-12-11
Ah, ok, that makes sense.

But I am  curious now - is there a file wiping utility in ubuntu? A shredder? Or is that something that is done by default when the trash is emptied or bypassed?

---

### Post by HermanAB on 2007-12-11
Shredders don't work on log structured file systems.  If you 'overwrite' a file several times, all you end up with is *more* copies of it on the HDD than you had before.

Cheers,

H.

---

### Post by lgambett on 2007-12-11
...consider also that recovering a deleted file on an ext3 filesystem (Ubuntu default) is not as easy as recover a file under NTFS / FAT32 filesystems. A shredder is no longer necessary...
Luca

---

### Post by Niniel on 2007-12-11
Uhm, that doesn't make any sense to me, would you mind explaining?

I was under the impression that securely wiping a file is done by overwriting it with random data several times - how would that spread the file around?
But if it is as you say it is, I guess then I'd have to wipe all free space in order to really get rid of my deleted file/s - is there a tool for *that*?

---

### Post by Niniel on 2007-12-11
> **lgambett said:**
> ...consider also that recovering a deleted file on an ext3 filesystem (Ubuntu default) is not as easy as recover a file under NTFS / FAT32 filesystems. A shredder is no longer necessary...
Luca

Why is it "not easy"?

However, "not easy" is not the same as "impossible", so I don't see how this negates the need for a shredder.

---

### Post by Tom Mann on 2007-12-11
you can use dd or wipe in order to wipe files

if you go into a console and type:

wipe --help

you will get basic information on wiping files. (NB: They have to currently exist - I'm not sure about wiping reclaimed space and wouldn't want to guess for your hard drive's sake!)

---

### Post by HermanAB on 2007-12-11
The only way to reasonably securely delete data on a disk is to activate the built-in delete utility that resides in the controller of all modern disk drives:  [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The other way to erase data is to always encrypt all your data and forget the key.

'Wipe' and 'shredder' utilities only work with Ext2 and nobody uses that anymore.

Cheers,

H.

---

### Post by natehall on 2007-12-11
> **Niniel said:**
> Ah, ok, that makes sense.

But I am  curious now - is there a file wiping utility in ubuntu? A shredder? Or is that something that is done by default when the trash is emptied or bypassed?
Try typing this in the terminal  

    man shred

then type q to get out.

---

### Post by HermanAB on 2007-12-11
Even the shred man page explains very clearly that it doesn't actually work...

---

### Post by Tom Mann on 2007-12-11
If not shred - dd?

---

### Post by HermanAB on 2007-12-11
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by Niniel on 2007-12-11
Yes, I read that... but that's about wiping physical hard drives, not individual files (I liked the part about the utility of just bending your magnetic disks). And it's mainly about defense against professional data recovery. 
So what in Ext3 causes "wiping" of files to not work? Why are you saying that overwriting a file with random data will create more copies of the file? I still don't get it.

---

