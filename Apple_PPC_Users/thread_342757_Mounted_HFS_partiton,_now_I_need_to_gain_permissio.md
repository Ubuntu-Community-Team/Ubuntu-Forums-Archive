---
title: "Mounted HFS partiton, now I need to gain permission to trash folder"
date: 2007-01-20
forum: Apple PPC Users
---

### Post by jesstech on 2007-01-20
Here's an easy one for you:

I'm fixing a friend's iBook G4, who accidentally moved her /System/Library folder to the OS X Trash and shut down. Now the iBook refuses to start, throwing a errors about not being ale to find drivers for the platform.

So far I've been unable to boot into any single-user mode (kernel panics before I can get the chance) and restore the library from the terminal, so I burnt an Edgy live CD and have mounted OS X HFS+ partition mounted for read/write. Now, i simply need to get into the user's /.Trash folder to restore the library, but Edgy is telling me I don't have permisions.

I no unix whiz, but I know there's gotta be a way to gain access to this protected HFS+ directory. Otherwise, what other options do I have?

---

### Post by jesstech on 2007-01-20
nevermind, the disk is journaled so there's no way I can write to it anyway to move the folder. sonofa....

---

### Post by calum on 2007-01-21
> **jesstech said:**
> nevermind, the disk is journaled so there's no way I can write to it anyway to move the folder. sonofa....

Don't panic just yet... if it's one of the iBooks with a firewire port, you can start it in 'target disk mode'.  This effectively turns it into an external hard drive, that you can connect to another Mac with a firewire cable, and sort out the files on it that way.

See [http://docs.info.apple.com/article.html?artnum=58583](http://docs.info.apple.com/article.html?artnum=58583) for details.

---

### Post by jesstech on 2007-01-22
I already explored that as an option, but I don't have a 6pin - 6pin FireWire cable laying around here. They're kind of a white elephant in the PC world. I wanted to try ubuntu before I went out and purchased a cable for one-time use, but it looks like that's what is going to happen.

---

### Post by didg on 2007-01-22
If you have an OSX disk around you can unset journaling from diskutil.

---

