---
title: "Backup Thunderbird emails in Ubuntu?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-05-19
I've previously used MozBackup in Windows, but have not come across an alternative for Linux. Is there such a thing, or is there a standard way of doing this?

Thanks in advance!

---

### Post by Bachstelze on 2007-05-19
Why do you ant to backup your emails ? Is it so you don't lose them if you need to reinstall Ubuntu ?

---

### Post by Martin on 2007-05-19
Your mails are kept in your home directory in .thunderbird/****.default/Mails/your account/ within the directory for the account you wan to back up you will see all your mail folders as text files. It would'nt be hard to write a somlpe script that grabbed and compressed them every now and again. Or if it doesn't need automating just do it manually from time to time.

---

### Post by qprfact on 2007-05-19
I'm just paranoid about losing anything, that's all!

How would I go about compressing them?

---

### Post by Bachstelze on 2007-05-19
```
cd
tar czvf thunderbird.tgz ./thunderbird/
```

Will make a gzipped tarball of all your Thunderbird peronal data, including your emails, in the file thunderbird.tgz, which you can then save to a safe location.

---

### Post by yabbadabbadont on 2007-05-19
Strange.  On every version of Ubuntu that I have so far used (all of them since warty) the thunderbird profile is stored under ~/.mozilla-thunderbird and not ~/.thunderbird.  I wonder why yours is different?

---

### Post by yabbadabbadont on 2007-05-19
> **HymnToLife said:**
> ```
cd
tar czvf .thunderbird thunderbird.tgz
```

Will make a gzipped tarball of all your Thunderbird peronal data, including your emails, in the file thunderbird.tgz, which you can then save to a safe location.

You have the parameters to tar reversed....  I hope he hasn't used your command yet.

---

### Post by Bachstelze on 2007-05-19
The command I posted above assumes it's in .thunderbird, since that's what was said earlier. Of course change it if it's different for you. I guess that depends on your Thnderbird version, I don't use it anyway...

yabbadabbadont, right you are, I corrected ;)

---

### Post by qprfact on 2007-05-22
No, haven't tried yet - what should I do instead?

---

### Post by Bachstelze on 2007-05-22
I corrected it, just do as said in my message above.

---

### Post by qprfact on 2007-05-22
Thanks - will do!

---

### Post by pswaney on 2007-05-27
It's easy enough to back up .mozilla-thunderbird with tar, the hard part is trying to restore it. I installed Ubuntu Feisty Fawn 7.04 then installed the ubuntu version of Thunderbird. I then started and closed Thunderbird. Next I untarred my old home directory in ~/temp and tried to copy ~/temp/.mozilla-thunderbird to ~/.thundebird-mozilla. But the file browser refused to copy and gave me an error code that referenced a lock file.

I went to the thunderbird web site and tried to follow their directions for moving my profile but that was mostly about windows with only vague references to linux.

I'm at a loss, will some of you kind people tell how to restore my thunderbird profile?

---

