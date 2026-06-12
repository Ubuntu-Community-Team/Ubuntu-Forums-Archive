---
title: "[SOLVED] avi to dvd and other problems."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-18
I have spent the last week trying to write avi to dvd, fine, but they won't play on my stand alone player.
I have loaded and unloaded most of the burner programs and now have another problem. I found last night that I have files missing.
Going through the help files and following the instructions on "Playing DVDs" I find that 'libplay0' is not found. I have re-installed all on that page including Java, but it's still missing.
Can someone take me in hand and lead me, by the nose if need be?

---

### Post by ugm6hr on 2008-01-18
> **newbeeman said:**
> I have spent the last week trying to write avi to dvd, fine, but they won't play on my stand alone player.

You want to play the DVD in a regular (i.e. non-computer) DVD player?

Then you can't just copy the files onto DVD.  You have to re-encode them.

There are a couple of programs that will do that for you: 
DeVeDe: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) (I use this)
ManDVD: [http://www.getdeb.net/app.php?name=ManDVD](http://www.getdeb.net/app.php?name=ManDVD)

To play DVDs on Ubuntu: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by newbeeman on 2008-01-18
> **ugm6hr said:**
> You want to play the DVD in a regular (i.e. non-computer) DVD player?
Then you can't just copy the files onto DVD.  You have to re-encode them.
There are a couple of programs that will do that for you: 
DeVeDe: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) (I use this)
ManDVD: [http://www.getdeb.net/app.php?name=ManDVD](http://www.getdeb.net/app.php?name=ManDVD)
To play DVDs on Ubuntu: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Sorry, perhaps I wasn't plain enough. During the trials to burn avi to dvd I found files missing. So my main concern is to replace the missing file, see my first post.

---

### Post by newbeeman on 2008-01-18
Bump

---

### Post by ugm6hr on 2008-01-18
> **newbeeman said:**
> Sorry, perhaps I wasn't plain enough. During the trials to burn avi to dvd I found files missing. So my main concern is to replace the missing file, see my first post.

I still don't think you are being clear. ** When do you get the error about the missing file?**  Can you play DVDs or not?

I have just searched my file system - I don't have a libplay0 either.  And there is no such package in the repos.

If the problem is you can't play DVDs, then I would suggest you follow the advice in STEP 3 of this: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) (which uses VLC instead of gxine in the help files).

If the problem is that you can't burn avi to DVD, then you need to explain exactly what it is that you are trying to write to the DVD (i.e. data DVD with avi files, playable DVD video).  My previous 2 suggestions were for the latter.

---

### Post by oldos2er on 2008-01-18
When you say "loaded and unloaded," does that mean you're using apt-get or Synaptic to install and uninstall these programs?

 I'd try the program DeVeDe; I've had good luck with it.

---

### Post by newbeeman on 2008-01-18
> **ugm6hr said:**
> I still don't think you are being clear. ** When do you get the error about the missing file?**  Can you play DVDs or not?

I have just searched my file system - I don't have a libplay0 either.  And there is no such package in the repos.
.

I have problems 'playing' dvds on my machine. So I went to the Ubuntuy help files on my machine and followed the instructions. It states clearly that you need 'libdvdplay0', so as a noob I followed, to find I don't have that file.
Presumably it's necessary.
This is a mute point, I have decided to wipe and re-install, get rid of the stuff added in error hopefully start again.
Thanks for the effort.

---

### Post by ugm6hr on 2008-01-18
> **newbeeman said:**
> I have problems 'playing' dvds on my machine. So I went to the Ubuntuy help files on my machine and followed the instructions. It states clearly that you need 'libdvdplay0', so as a noob I followed, to find I don't have that file.
Presumably it's necessary.
This is a mute point, I have decided to wipe and re-install, get rid of the stuff added in error hopefully start again.
Thanks for the effort.

That Help file must be wrong.  I don't have that file, and can't find it in Synaptic Package manager either.

If you follow the previously linked How-to, you should be able to play DVDs in VLC.

---

### Post by oldos2er on 2008-01-18
I agree, the help file is wrong. You don't need to reinstall. If you could tell us exactly what problems you're encountering playing DVDs, I'm sure we could help.

---

### Post by newbeeman on 2008-01-18
> **oldos2er said:**
> I agree, the help file is wrong. You don't need to reinstall. If you could tell us exactly what problems you're encountering playing DVDs, I'm sure we could help.

It would appear my CD/DVD is not seen by programs. It used to automatically pick up when a either disc was inserted, now nothing.

---

### Post by ugm6hr on 2008-01-18
> **newbeeman said:**
> It would appear my CD/DVD is not seen by programs. It used to automatically pick up when a either disc was inserted, now nothing.

Did you reinstall or not?

Can you access CDs if you go to "File System" in nautilus and double-click?  If yes - then you have turned auto-mounting off.  If no - there is a problem with the drive.

---

### Post by oldos2er on 2008-01-18
> **newbeeman said:**
> It would appear my CD/DVD is not seen by programs. It used to automatically pick up when a either disc was inserted, now nothing.

 Can you post the output of "cat /etc/fstab"?

---

