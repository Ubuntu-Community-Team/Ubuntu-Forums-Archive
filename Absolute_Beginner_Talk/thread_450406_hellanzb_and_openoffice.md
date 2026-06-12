---
title: "hellanzb and openoffice"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by IsleOf on 2007-05-21
I found a tutorial on this site to download nzbs par and unrar all in one. However things have changed with feisty. I tried to follow the updated tutorial at the end but found it a bit difficult to follow.
I have hellanzb, unrar and par2 installed so i was wondering if someone could help me from there.

Is there a way openoffice can save files as xls?

As im new to linux is there a general tutorial on commands and how the filing system etc works with ubuntu. (for some light reading when on nightshift tonight:) . I obviously need to learn more.

---

### Post by justleen on 2007-05-21
what goes wrong with the script? do you get any errors?
(where did you get the script/can you post the script?)

As far as i know, in Open Office, you can simply go to File> save as, and select xls format..

---

### Post by IsleOf on 2007-05-21
This is the thread i got it from

[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+par+rar](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+par+rar)

I tried the method on the first post. Didnt work then read it on the last page. From that i have got hellanzb installed. par and rar were already in the Ubuntu ive downloaded.
Nothing went wrong with the script i just couldnt really make sense of what my next steps would be.

Cheers

---

### Post by justleen on 2007-05-21
i had a look at that tread, but as far as i can tell, you should be able to just run hellanzb  on a nzb file?
can you start it from the command line with just hellanzb?

---

### Post by IsleOf on 2007-05-21
If i type in terminal
> hellanzb

I get

hellanzb v0.10 (config = /etc/hellanzb.conf)
(changeme) Opening 4 connections...
hellanzb - Now monitoring queue...

I take it this means hellanzb is running. Ive still to configure hellanzb to run from my newsgroup account.

---

### Post by justleen on 2007-05-21
the config file is in /etc/hellanzb.conf. just open it with gedit, read through it, and edit your server details.

```
sudo gedit /etc/hellanzb.conf 
```

Let me know if you still have problems..( i use nzbperl myself, but if you cant get it to work ill install hella once i get home..)

---

### Post by IsleOf on 2007-05-21
Cheers. Unfortunately ive got to go out now so wont have a chance to play with it probably until tomorrow. (need to find my news account details again anyway)
Will be doing a bit of reading on ubuntu tonight in work;)

Cheers

---

