---
title: "My Files Disappeared!!"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by neonmagnolia on 2008-04-11
Okay, *absolute* beginner here ... I was about to copy a couple files from my external drive when all of a sudden, without having any knowledge of pressing the delete or any other keys, a folder disappeared. I checked the trash bin but could not find the folder. This happened a few weeks ago when I first installed Ubuntu, but I didn't fret because I had all the files backed up. Now, an entire folder of about 3000 photos has gone missing, literally in the blink of an eye. It first turned into some unknown file type with just a blank page as an icon rather than the folder icon, now its gone.

Does anybody have any clue what I did, how I can get my files back, and how I can prevent this from happening again?

Edit: I unmounted and remounted the drive, and the folder with the photos is in tact. (THANK GOD!) The videos folder is there as well, but I get an error message saying that Nautilus cannot display the contents, and to try another viewer.

---

### Post by superprash2003 on 2008-04-11
is it an NTFS external drive?

---

### Post by neonmagnolia on 2008-04-11
Yep.

---

### Post by superprash2003 on 2008-04-11
have you installed ntfs3g?

---

### Post by neonmagnolia on 2008-04-11
nope, what is it?

---

### Post by superprash2003 on 2008-04-11
its a support for ntfs drives .. go to terminal and type the following

sudo apt-get install ntfs-config

sudo apt-get install ntfs-3g 

then unmount your drive, if mounted
then go to applications->system tools->NTFS configuration tool

check "enable write support for external drive" , it should mount now and you should not have any problems

---

### Post by prshah on 2008-04-11
> **neonmagnolia said:**
> 
Edit: I unmounted and remounted the drive, and the folder with the photos is in tact. (THANK GOD!) The videos folder is there as well, but I get an error message saying that Nautilus cannot display the contents, and to try another viewer.

You must install "restricted-extras" to see most video formats: in a terminal, give the command ```
sudo apt-get install ubuntu-restricted-extras
```

> **superprash2003 said:**
> have you installed ntfs3g?

If ntfs-3g is NOT installed, he cannot even see the damned thing in the first place, so that's not his problem.

> **neonmagnolia said:**
> nope, what is it?

It's something you don't need if you have Ubuntu 7.10 (Called Gutsy Gibbon), and if you can see the contents of your external drive anyway.

---

