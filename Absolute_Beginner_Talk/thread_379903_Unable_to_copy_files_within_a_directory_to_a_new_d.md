---
title: "Unable to copy files within a directory to a new directory"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by DigitalDaiquiri on 2007-03-09
For some reason I am unable to copy all of the files recursively within a folder to another folder.  Using the "cp -r" command in the command line interface copies the entire folder to the new directory, so that it is essentially a directory within a directory.  I am looking to copy the files within, for example, /tmp/digitaldaiquiri to /tmp/digitaldaiquiri2, not /tmp/digitaldaiquiri2/digitaldaiquiri .  Does anyone have any suggestions?  Thank you all for your time!

---

### Post by nanotube on 2007-03-09
so, say you have a directory, /tmp/dir1, and you want to make a copy of it, say, /tmp/dir2
just do the following
```
cp -r /tmp/dir1 /tmp/dir2
```

the trick is, just make sure that /tmp/dir2 does not exist before you issue the cp command.

---

### Post by jkeidel on 2007-03-09
would cp -r tmp/* tmp2 work?

---

### Post by dhughes on 2007-03-09
Wait a second...

 I think you need to add a /* after the file you are moving 

 cp -r /tmp/digitaldaiquiri/*  /tmp

 Something like that, the /* is the key to it.

---

### Post by nanotube on 2007-03-09
> **jkeidel said:**
> would cp -r tmp/* tmp2 work?

yea, if say /tmp/dir2 already exists, then you can achieve the same effect with
```
cp -r /tmp/dir1/* /tmp/dir2
```

---

### Post by DigitalDaiquiri on 2007-03-09
> **nanotube said:**
> yea, if say /tmp/dir2 already exists, then you can achieve the same effect with
```
cp -r /tmp/dir1/* /tmp/dir2
```

You guys are amazing!  Thank you very much for your help; I was able to do exactly what I was hoping to.

---

