---
title: "How do I completely delete a user including the home folder?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-05-13
I want to delete a user and re-create the user name with all the default settings in place, but when I delete the account the home folder is still there. When I recreate the user name the settings are what they were before :mad:

---

### Post by heimo on 2007-05-13
If the user exists (DANGEROUS, removes users home directory):
```
sudo deluser --remove-home username
```To just delete home directory (DANGEROUS):
```
sudo rm -r /home/username
```

username = user which will be removed / who's home directory will be removed

---

### Post by Wim Sturkenboom on 2007-05-13
```
man deluser
```
>        If called with one non-option argument and without the  --group option,
       deluser will remove a normal user.

       By  default,  deluser  will  remove  the user without removing the home
       directory, the mail spool  or any other files on the  system  owned  by
       the  user.  Removing  the home directory and mail spool can be achieved
       using the --remove-home option. If the --home option is given,  deluser
       will  only  remove the user if the directory given to the --home option
       matches the user&#8217;s real home directory.

       The --remove-all-files option removes all files on the system owned  by
       the  user.  Note  that  if you activate both options --remove-home will
       have no effect because all files including the home directory and  mail
       spool are already covered by the --remove-all-files option.

I think that that pretty much covers it.

---

### Post by bodhi.zazen on 2007-05-13
> **Amablue said:**
> I want to delete a user and re-create the user name with all the default settings in place, but when I delete the account the home folder is still there. When I recreate the user name the settings are what they were before :mad:

Well, what settings ? you can restore a lot of default settings by deleting dot ( . ) files in /home.

Don't delete all of them though :)

---

### Post by Amablue on 2007-05-13
> **bodhi.zazen said:**
> Well, what settings ? you can restore a lot of default settings by deleting dot ( . ) files in /home.

Don't delete all of them though :)

Y'see, that's part of the problem. I was screwing with stuff and I don't know exactly what I did. So instead of trouble shooting for a half hour, I'd rather just wipe it and start clean. I don't have anything I can't reset quickly anyway.

---

