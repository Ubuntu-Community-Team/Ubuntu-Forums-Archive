---
title: "Checking what is safe to delete"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-06-07
I have run short of space on my linux partition and I have noticed a couple of folders are taking up MASSIVE amounts of space. 

I have about 20 mails in my Thunderbird inbox, nothing in the trash/sent/draft/etc folders but the .mozilla-thunderbird folder has about 500 megs or more in it. mainly taken up two files called "inbox" one stored in "local folders" and another in "pop.gmail.username"

Also I have a "sent" file of about 50 mb but nothing at all in my "sent" folder. This is very confusing. Are these much bigger than they should be or safe to delete?

I have another question about a folder called var/log which has some absolutely massive files in sometimes over 500 mb, are these safe to delete?

I would appreciate some help here as gnome failed to start a couple of times for me.

---

### Post by Bachstelze on 2007-06-07
Log files are safe to delete. They're just here to help troubleshooting a problem if something goes wrong but you can delte them safely if you really need to. Don't know about Thunderbird but deleting the file it puts in your home folder won't harm your system at all. At worst, you'll lose your profile.

---

### Post by BHelts on 2007-06-07
from aptitude manual

```
sudo aptitude clean
```

>        clean
          Removes all previously downloaded .deb files from the package cache
          directory (usually /var/cache/apt/archives).

this can clean up significant amounts of space.  if you man aptitude, you can look at autoclean which i think is more comprehensive.

---

### Post by tabithaboof on 2007-06-07
Thanks I think that helped with the .log files

---

### Post by jfinkels on 2007-06-07
> **tabithaboof said:**
> I have run short of space on my linux partition and I have noticed a couple of folders are taking up MASSIVE amounts of space. 

I have about 20 mails in my Thunderbird inbox, nothing in the trash/sent/draft/etc folders but the .mozilla-thunderbird folder has about 500 megs or more in it. mainly taken up two files called "inbox" one stored in "local folders" and another in "pop.gmail.username"

Also I have a "sent" file of about 50 mb but nothing at all in my "sent" folder. This is very confusing. Are these much bigger than they should be or safe to delete?

I have another question about a folder called var/log which has some absolutely massive files in sometimes over 500 mb, are these safe to delete?

I would appreciate some help here as gnome failed to start a couple of times for me.

Sending a file of size 50Mb may not necessarily store that file to your computer. It may just be stored on the mail server, depending on the kind of server.

And I think the ~/.mozilla-thunderbird/inbox file is the file that actually contains your mail, so I wouldn't delete that :D. I'm not too sure about that, though, and I'm no expert....

---

