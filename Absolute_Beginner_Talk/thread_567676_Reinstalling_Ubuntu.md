---
title: "Reinstalling Ubuntu?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by liamwithers on 2007-10-04
Hi, I want to reinstall Ubuntu but have all my memory back as I have used most of it and want to start a fresh. Can't delete most of my things because they are in folders only root can access. I've downloaded so much junk that I've had enough. If I download the Livecd, boot from it and then Install from the Livecd, will it wipe all my current things and install from the beginning again?

Thanks, Liam

---

### Post by overlord.gaurav on 2007-10-04
If you are going to re-install Ubuntu on the same partion of the current installation, you will have to format it. If you format your driver (partition), it is obvious that all the data will be erased that was existing on it.

---

### Post by T700 on 2007-10-04
Yes, if you do a fresh install from the Live CD, you will over write everything that is currently there.  I'm sure you understand this, but just don't forget that everything means EVERYTHING.  Pictures.  Emails.  Everything.

Paul

---

### Post by liamwithers on 2007-10-04
How exactly do I format my partition? Sorry, I'm 13 so even though I've been using Linux since June last year, I'm still a complete newb lol.

---

### Post by liamwithers on 2007-10-04
Ahh ok, thanks paul. Yep, I'm ready to delete everything. All I want installing is Flash, Java and E17 tbh.

---

### Post by Scunizi on 2007-10-04
/home/{your_user_name} is where all your data is stored.. as in docs, spreadsheets, music, pic additional programs you've installed (mostly).  There are things that are outside of that directory that is only accessable by root (for copy, delete etc..)  .. 

If you reinstall you will more than likely lose everything.  Backup your date in your home then go for it.. When installing again use the manual partitioning tool and create a seperate partition for /home.   That way when and if you reinstall again you're data will remian intact..

---

### Post by liamwithers on 2007-10-04
The thing is, I don't want all my crap lol. I want a COMPLETE re-install of Ubuntu.

---

### Post by liamwithers on 2007-10-04
Also... will the install of Feisty be pretty simple? No dodgy things I have to go through?

Thanks, Liam

---

### Post by overlord.gaurav on 2007-10-04
> Also... will the install of Feisty be pretty simple? No dodgy things I have to go through?

Thanks, Liam
Yes, its  very simple.
And by the way, age doesn't matter, much. I'm 14.

---

### Post by liamwithers on 2007-10-05
I came back to my pc after going downstairs and it told me there wasn't enough space to complete the download. I had 40 odd mb left :S???

Anyway, even if it did fully download, I would have about 4 mb free. I cleared just enough space for it to download.

Surely 180mb extra will allow it to work?

---

### Post by macogw on 2007-10-05
That should be fine.  You could've like...."rm *" in your home directory...I'm sure that would've freed a lot of space.

Also, so you know, "sudo apt-get clean" empties out your apt cache, which is equivalent to deleting all your Setup.exe's  It tends to free up a lot of space.

---

