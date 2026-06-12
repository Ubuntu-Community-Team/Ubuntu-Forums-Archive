---
title: "Copying files from Vista to Ubuntu"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Eric the Grey on 2007-05-29
Hello;

Fresh install of Ubuntu (Feisty) on a dual-boot machine with XP (the XP boot is used for beta testing).

I"m trying to copy my documents, pictures and such from my Vista machine over my home network onto the Ubuntu box but so far, failing to do so.

When I try to copy, I either get a read error, or the system simply does not copy the files.

The error I get most often when trying to open the folder is:

> Nautilus cannot display "smb://orac/temp/Documents".
Please select another viewer and try again.

The user ID I'm using to log into the vista box has full read/write permissions to the shared folder, and the folder itself, as well as everything underneath it has rights set to "Everyone" with full control.

Any ideas that will make it easier to copy these documents other than using my USB key to do so (at 250 mb, it will take about a dozen transfers to get everything...)


:cool: Eric the Grey

---

### Post by Ek0nomik on 2007-05-29
You could setup a shared partition (FAT32).

Windows and Linux both read FAT32 partitions natively, so that is one solution.

---

### Post by Eric the Grey on 2007-05-29
That would require reformatting a drive, and I'm not really interested in doing that.

The file system should not be an issue, since I'm copying from one running OS to another.


:cool: Eric the Grey

---

### Post by gohanssjn on 2007-05-29
You say the Vista login has read/write permissions, but have you loaded the ntfs read/write drivers in Ubuntu?  I think it's called ntfs-3g, but someone will probably correct me on that!

Oh, a network, I didn't see that either ](*,)

---

### Post by Ek0nomik on 2007-05-29
Ohhh all this transfering is happening over a network.  It isn't actually from different partitions on your computer?

Then this would be a networking/samba problem, yes?

---

### Post by Eric the Grey on 2007-05-29
> **Ek0nomik said:**
> Ohhh all this transfering is happening over a network.  It isn't actually from different partitions on your computer?

Then this would be a networking/samba problem, yes?

It is either a networking or permission problem.

A little more clarity:  I'm opening windows on my Ubuntu desktop, one for my home folder, and one to my vista desktop.  Then I'm trying to copy from vista, to Ubuntu.

I suppose I could set up Samba on Ubuntu, and set up a share there and do it the other way.  I've done that once, a long time ago.

Edit:  Samba is installed, and I have shared a directory, but cannot log in to it from windows using my user ID.


:cool: Eric the Grey

---

### Post by funkyfreak on 2007-05-29
hey guys..  Eric I see that you are having the same troubles as other with vista shares..  I don't know if this will work for you but try taking a read through my post at the end of this thread: [http://ubuntuforums.org/showthread.php?t=428093](http://ubuntuforums.org/showthread.php?t=428093)

I have never used linux before and thought I'd try it.. But I do support Vista for a job.   I have no troubles with either Kubuntu or Unbuntu 7.4 (which I  just installed tonight).. Kubuntu have me some troubles as said in the post but Ubuntu has  allowed me to access & copy (after hitting retry on an error) files to my wireless notebook..  so I think it is your setup on Vista as I have swiched OSs and can copy with both...

hope this helps.

Funkyfreak

edit: I should add that with ubuntu tonight I didn't even need to provide credentials

---

### Post by Ek0nomik on 2007-05-29
> **Eric the Grey said:**
> It is either a networking or permission problem.

A little more clarity:  I'm opening windows on my Ubuntu desktop, one for my home folder, and one to my vista desktop.  Then I'm trying to copy from vista, to Ubuntu.

I suppose I could set up Samba on Ubuntu, and set up a share there and do it the other way.  I've done that once, a long time ago.

Edit:  Samba is installed, and I have shared a directory, but cannot log in to it from windows using my user ID.


:cool: Eric the Grey

Vista is formatted as an NTFS drive correct?  What exactly isn't letting you copy files from Vista to Ubuntu?  Are you getting an error?  Is an option greyed out?

Linux can't **write** to NTFS drives natively, but it can **read** NTFS drives, so I don't see why there is a problem.

---

### Post by Eric the Grey on 2007-05-31
Funkyfreak, I followed your instructions and made the changes to my Vista networking, but it doesn't seem to have done any good.  I still cannot copy from one to the other.   :(

The good news is that my Ubuntu machine is a dual boot, with XP as the other OS, so I can copy to it, and then mount up the XP drive and copy things over that way, but it's a PITA if I want something right away.

> **Ek0nomik said:**
> Vista is formatted as an NTFS drive correct?  What exactly isn't letting you copy files from Vista to Ubuntu?  Are you getting an error?  Is an option greyed out?

Linux can't **write** to NTFS drives natively, but it can **read** NTFS drives, so I don't see why there is a problem.

Again, the formatting of the drive in question should not matter, as it is an active machine.  It works the same way a file server does, the remote machine handles all I/O to the disk, not the remote machine.

All I'm doing is dragging and dropping files from one folder on Vista to my home folder on Ubuntu.  I CAN right-click, and select copy and then select Paste here, but nothing happens.

Anyway, when I copy files, this is what I get:

> Error "Invalid parameters" while copying "smb://orac/...OMIX!!.URL".
Would you like to continue?

With an option to skip, cancel or retry.  Retry sometimes works, but it will never continue on with the other files selected (if any).  If I try to make another copy, it nothing happens, no error, no copy.


:cool: Eric the Grey

---

### Post by lazyart on 2007-05-31
Go to your Ubuntu box-- you said you have set your home folder to be shared, correct?

sudo smbpasswd -a *username*
sudo smbpasswd -e *username*

This will activate and enable sharing for your Ubuntu username.

Go back to Vista, browse the network and copy to your Ubuntu home folder.  Your Ubuntu username and password should work.

---

### Post by Eric the Grey on 2007-06-02
> **lazyart said:**
> Go to your Ubuntu box-- you said you have set your home folder to be shared, correct?

sudo smbpasswd -a *username*
sudo smbpasswd -e *username*

This will activate and enable sharing for your Ubuntu username.

Go back to Vista, browse the network and copy to your Ubuntu home folder.  Your Ubuntu username and password should work.

Thank you lazyart, that did the trick, from the Ubuntu/SMB point of view.  I can now copy from Vista to Ubuntu.  The other still doesn't work, but at least I can get files from one box to another.



:cool: Eric the Grey

---

