---
title: "HP Web JetAdmin 8.1 SUSE or Fedora"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by MTUser2007 on 2007-12-26
HP supplies Web JetAdmin to administer HP network printers. I have and use the Windows version. In my attempt to transition to/learn more about Linux, I found that HP provides versions for Linux, specifically a version for SUSE or Fedora. Any suggestions on which will have the greatest chance of compatibility with Ubuntu?

Any other suggestions for making programs written for other versions of Linux work with Ubuntu?

Thanks.

---

### Post by blueridgedog on 2007-12-26
I used that under windows as well.  As I seem to recall it was principally Java.

If it is available for RH as an RPM, you can use the alien package tool:

[http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)

---

### Post by MTUser2007 on 2007-12-26
> **blueridgedog said:**
> I used that under windows as well.  As I seem to recall it was principally Java.

If it is available for RH as an RPM, you can use the alien package tool:

[http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)

If I mouseover the links, HP shows them having the .selfx extension for both of them:

[http://www.hp.com/bizsupport/wja/live/manual/8.1/installs/wja81-3748-fe.selfx](http://www.hp.com/bizsupport/wja/live/manual/8.1/installs/wja81-3748-fe.selfx)

If you click the links the download lists them as binary. I am not sure what that means in relation to rpm.

---

### Post by blueridgedog on 2007-12-26
I suggest you download it and see what extracts.  It may extract into something.  Then we can see what the next step is.  I have started downloading it as well and will see what it produces.

---

### Post by blueridgedog on 2007-12-26
Downloading and chmod'ing this to 700 and running it produces a graphical installer.  It may work.  See screenshot.

---

### Post by MTUser2007 on 2007-12-27
> **blueridgedog said:**
> Downloading and chmod'ing this to 700 and running it produces a graphical installer.  It may work.  See screenshot.

Sorry, I am an absolute beginner - I don't know what chmod'ing a file is. I tried googling it and can see it is about changing permissions, but I could not find anything on how that is actually accomplished.

Please can you help?

---

### Post by blueridgedog on 2007-12-27
If the file is say called wja81-3748-fe.selfx and it is in your home directory, you would open a terminal and:

```
chmod 700 wja81-3748-fe.selfx
```

or for simplicity sake:

```
chmod 777 wja81-3748-fe.selfx
```

chmod is simple, it deals with the permission of the Owner, Group and Other. 

These can be Read, Write or Execute, referenced as RWX.  So for Owner, Group and Other, they are referenced as RWXRWXRWX.

Each RWX pair can by referenced as a value from 0 to 7 due to binary numbering as follows:

0 = Nothing
1 = Execute
2 = Write
4 = Read

So the RWXRWXRWX string can represented by three numbers form 0-7.

if you wanted all of the above for the owner and the group, then the result would be 770.  If you wanted read and write for the owner only, but read for the others it would be 644 (a classic permission number).

Good luck.

---

### Post by blueridgedog on 2007-12-27
I neglected to tell  you that the wja81-3748-fe.selfx file will need to be run as the root or "superuser" account.  This can be done by changing to the directory that has the wja81-3748-fe.selfx file and running:

```
sudo ./wja81-3748-fe.selfx
```

Having said all of the above, keep in mind that there is no gurantee that this will work, but breaking new ground is the Linux way.

---

