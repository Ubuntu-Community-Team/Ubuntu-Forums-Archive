---
title: "External Hard Drive..."
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-23
Okay so I can see it, it mounts but for some reason when I try to put a RAW file in the HD from Ubuntu, it errors out.  Any ideas?  It works fine with text or JPG format files but something happens with RAW.

**ps, I have posted on another thread asking how to open RAW images in GIMP as UFRAW doesn't seem to be working.  If this is part of the problem, let me know.

---

### Post by taurus on 2007-11-23
What is the error message when you try to save a RAW file to that external harddrive?  What format/filesystem is that harddrive anyway?

---

### Post by Ubun2User on 2007-11-23
Error "I/O error" while copying "/desktop/IMG_1531.CR2".

But it works fine in Vista...

---

### Post by timcredible on 2007-11-23
what filesystem is the drive?  if it's ntfs, you need to change it to ext3 (if you're not going to use it with windows), or fat32 (if you're going to use it with windows).  keep in mind that fat32 doesn't support file permissions, if that's important to you.  as for opening raw files, you probably want dcraw instead, it works great with digikam, and i've used it with gimp (although i find that digikam does 99% of what i need, so i don't use gimp much).

---

### Post by Ubun2User on 2007-11-23
It is NTFS...if I change it, will it delete everything on it?

If NOT, how do I change it?

---

### Post by Ubun2User on 2007-11-23
FYI, I also DL'd DigiKam but when I extract it, nothing happens.

---

### Post by Dr Small on 2007-11-23
if you reformat the drive to ext3 from NTFS (or reformat in general) it will completely erase the drive and reformat it into ext3 format.

You would be best off to backup everything on that drive to your current drive (if you have the room for it), and then reformat. When it is ext3, just copy all of the files back over.

Dr Small

---

### Post by taurus on 2007-11-23
> **Ubun2User said:**
> FYI, I also DL'd DigiKam but when I extract it, nothing happens.

Digikam is available from the repos.

```
sudo apt-get update
sudo apt-get install digikam
```

---

### Post by Ubun2User on 2007-11-23
Ok, put the first line of code in and got a bunch of stuff back then it reads...

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg                              
  Could not resolve 'hendrik.kaju.pri.ee'
99% [Connecting to hendrik.kaju.pri.ee]


Hmmm?

---

### Post by Ubun2User on 2007-11-23
Here is the thing on the HDD...I will want to use it on Windows possibly one day so should I just use FAT32?  I don't care to "restrict" anything as I will only use the external to store photos (I am a photographer).

?

---

### Post by Ubun2User on 2007-11-23
> **Ubun2User said:**
> Ok, put the first line of code in and got a bunch of stuff back then it reads...

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg                              
  Could not resolve 'hendrik.kaju.pri.ee'
99% [Connecting to hendrik.kaju.pri.ee]


Hmmm?

Okay, went ahead and put the second line of code in and it seems to be DL'ing...I will report back.

---

### Post by taurus on 2007-11-23
You added some extra repo in /etc/apt/sources.list, haven't you?  On top of that, you added the wrong release, _Feisty_!  

You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of this line to comment it out.

```
http://hendrik.kaju.pri.ee feisty
```
Save it and then run

```
sudo apt-get update
sudo apt-get install digikam
```

---

### Post by Ubun2User on 2007-11-23
Thanks, seems to be working!

---

### Post by Ubun2User on 2007-11-23
Okay, now I need to install DCRAW, as a plugin for DigiKam?  Please help!





*********I just want to say, I love Ubuntu and I LOVE THIS FORUM AND THE FOLKS!!!!******

---

### Post by Ubun2User on 2007-11-23
Anyone?

---

### Post by Ubun2User on 2007-11-23
> **Ubun2User said:**
> Here is the thing on the HDD...I will want to use it on Windows possibly one day so should I just use FAT32?  I don't care to "restrict" anything as I will only use the external to store photos (I am a photographer).

?

Also, please do not forget about this questions, its probably one of the most important parts.  If I get access to my external HD and the ability to open RAW files, I am removing WINDOWS!!!!!

---

### Post by Dr Small on 2007-11-23
Just make it fat32 so it can be compatible with Windows and Linux ;)

---

### Post by Ubun2User on 2007-11-23
Okay, how do I reformat to make it FAT32?

---

### Post by Ubun2User on 2007-11-24
> **Ubun2User said:**
> Okay, now I need to install DCRAW, as a plugin for DigiKam?  Please help!


Please don't forget about the above question...:)

---

