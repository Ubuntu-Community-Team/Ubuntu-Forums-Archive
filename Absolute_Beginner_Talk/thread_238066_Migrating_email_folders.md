---
title: "Migrating email folders"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-08-17
Hello all!

I have thunderbird for windows and it is possible in thunderbird to import your entire outlook email folder. I actually haven't tried it yet, but I will this afternoon as soon as I've backed everything up. 

My question is, when I get thunderbird in ubuntu, how easy/difficult/impossible is it to import my email from my windows thunderbird to my ubuntu thunderbird?

Thanks in advance,

Cheers,
David K

---

### Post by Denis on 2006-08-17
This can be done. I think it's best to copy some directories from Windows thunderbird to Ubuntu thunderbird. 

If you have set up an email account in Windows Thunderbird, look for the directory where the Thunderbird settings are kept. This will probably be somewhere in C:\Documents and Settings\username\Application Data\. Look for a "mozilla-thunderbird" or "thunderbird" directory. In there you will find your Thunderbird profile in a folder that is named like this: $$$$$$$$.default

This folder contains al your account settings and email. All your mail is in the "Mail" subfolder. 

In your Ubuntu system you will find a similar directory for Thunderbird (if you have set up an email account in Thunderbird). The location is /home/username/.mozilla-thunderbird/$$$$$$$$.default

Now you can just copy over the mail (or a selection of it) from the Windows folder to the Ubuntu directory. You can use a partition both Windows and  Ubuntu can access to copy it. You can also use a CD, USB stick etc. of course. 

Good luck with it ;)

---

