---
title: "deleting songs from ipod nano does not make free space"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by larsdk on 2007-09-13
Hi,

I have the exact same problem as stated in [this thread]("http://ubuntuforums.org/showthread.php?t=310585") 

However, it doesn't seem that anyone has come up with a solution yet. Any suggestions as of how to get rhytmbox to delete ipod files (and actually freeing up space on the iPod while doing so). Or even to another program that can handle the iPod better? It is an iPod Nano (2GB silver)

Thanks in advance
Lars

---

### Post by Hallvor on 2007-09-13
Are you able to open the ipod "drive" with Nautilus? If so, try pressing Ctrl+h and look for a folder called .trash. The deleted files should be there. Open the folder and delete the files from the .trash folder.

I had the same problem with an mp3-player from Creative.

---

### Post by Spr0k3t on 2007-09-13
This is common with most removable media, not just MP3 players.  A quick fix is to remove the files yourself (hidden directories) or eject the drive.

---

### Post by brennydoogles on 2007-09-13
> **Spr0k3t said:**
> This is common with most removable media, not just MP3 players.  A quick fix is to remove the files yourself (hidden directories) or eject the drive.

Do the files in .Trash get deleted upon eject??

---

### Post by larsdk on 2007-09-13
> **Hallvor said:**
> Are you able to open the ipod "drive" with Nautilus? If so, try pressing Ctrl+h and look for a folder called .trash. The deleted files should be there. Open the folder and delete the files from the .trash folder.

I had the same problem with an mp3-player from Creative.

Yup - I can do that, **but** the .Thrashes on the iPod is empty, as is the Thrash-bin on my desktop.   Ejecting/unmounting does not seem to have an effect either.

Could it have anything to do with old itunes settings ?

---

### Post by AtrejuT on 2007-09-13
I have a regular 30Gig iPod, and Banshee works quite well for me. Maybe you should have a look at that.

> 
Do the files in .Trash get deleted upon eject??


So far they are not AFAIK. But I hope at some point in the future they will be ;-)

---

### Post by notwen on 2007-09-13
I have a older 4GB iPod Nano and upon unmounting the volume, I am prompted to empty the trash should there be any to empty at all.  Same for my external USB drive and thumb drive.

---

### Post by larsdk on 2007-09-13
> **notwen said:**
> I have a older 4GB iPod Nano and upon unmounting the volume, I am prompted to empty the trash should there be any to empty at all.  Same for my external USB drive and thumb drive.

no such thing for me when unmounting. And no files in the .Thrashes folder either... 

It just removes the files so that they no longer can be played from the iPod, but I just cant seem to make more space on the iPod :confused:

---

### Post by notwen on 2007-09-13
Have you tried plugging your iPod into a different computer to see if it would see any files that you may no be seeing in Linux.  Other than checking the .trash folders, I'd recommend browsing all of the iPods hidden folder structure and locate whats taking up all your room.  What all applications have you used since you noticed this issue to add/remove music to and from your iPod?

---

### Post by jspangler on 2007-09-13
I had good luck managing my ipod with gtkpod, which you can find in the repositories.

---

### Post by LowSky on 2007-09-13
banshee works fine on my ipod. also try gtkpod.

---

### Post by notwen on 2007-09-13
+1 GTKPod.  Small and compact.

---

### Post by tech9 on 2007-09-13
what program do you use for your i-pod, banshee?

---

### Post by larsdk on 2007-09-13
just tried the gtkpod - same thing happening there... When selecting "delete from iPod" it doesn't even make the song unplayable from the iPod -  i tried Banshee with no luck there either...

---

### Post by larsdk on 2007-09-13
> **tech9 said:**
> what program do you use for your i-pod, banshee?

That too :) (and gtkpod, amarok and rythmbox)

---

### Post by agds on 2007-09-13
> **brennydoogles said:**
> Do the files in .Trash get deleted upon eject??

Typically, no.  In some cases, files deleted from removable storage devices will appear to go to your desktop environment's trash, in which case that must be emptied—before unmounting the drive—for space to be freed.

---

### Post by larsdk on 2007-09-14
no one knows how to solve this? Its really annoying :confused:

I have tried unmounting after deleting (it does not say anything on unmount) and I have tried amarok, banshee as well as gtkpod and my iPod is just as full as ever (however now, I can't play the songs any longer)

Any help appriciated
Lars

---

### Post by stijngysemans on 2007-10-21
i have got the same problem.
I will delete my files when i connect my ipod to a windows pc :(

it says that files cannot be deleted out of the trash because it's a read-only FS.

---

