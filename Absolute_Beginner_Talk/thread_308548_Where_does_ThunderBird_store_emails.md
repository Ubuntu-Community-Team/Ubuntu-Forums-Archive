---
title: "Where does ThunderBird store emails?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-28
Hi,

I can't understand where emails are stored. Some say it's on /var and others say it's on /home. What's the truth? Also what is stored in /var/www?? Is that something similar to "Temporary Internet Files" in XP?

Thanks

---

### Post by autocrosser on 2006-11-28
Thunderbird stores E-mail in a hidden folder in your /home---enable "see hidden" in your Menu>System>Preferences>File Management. The folder is .mozilla-thunderbird & the mail folder is inside the user profile (string of number/letters.default) The mail is stored as a text file--copy it to your desktop & work with it---DO NOT REMOVE THE FILE FROM THE FOLDER--you WILL bork Thunderbird if you do.

As for /var/www--I don't even have that directory---no idea what it is used for.

---

### Post by MartynA on 2006-11-28
Also I believe /var/www is for web documents you want to serve using apache - i.e. files for a website you want to host off your computer.

---

### Post by Ben Sprinkle on 2006-11-28
/var/www Is the default root folder for most web servers including Apache.

---

### Post by kilou on 2006-11-28
OK so it has nothing to do with either Internet cache for browsing or emails. Thanks alot!

---

### Post by hellraiser_rob on 2006-11-28
if you are using imap does it store anything locally? i think it would only download emails if your using pop

---

