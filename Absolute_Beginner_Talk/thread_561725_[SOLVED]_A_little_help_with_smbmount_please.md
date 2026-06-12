---
title: "[SOLVED] A little help with smbmount please?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jordanmthomas on 2007-09-27
Hello, I am having some troubles with smbmount.

I can connect to my share fine in nautilus or konqueror, but I'd like to mount it somewhere.

Server/share:   **//zeus.pclab.tntech.edu/users/jmthomas21**
My username:  **pclab\jmthomas21** (May be what's giving me trouble)

So, if I go to smb://zeus.pclab.tntech.edu/users/jmthomas21 in either of the two aforementioned file managers, it asks for my username and password.  I put it in and I can browse no problem.

Great!  So, I figure I'll just mount it somewhere so I can get to it quickly later.  I fire up my trusty terminal and make a directory called pclab
```
mkdir pclab
```
Now, I try to use smbmount to mount the share:
[FONT="Courier New"]```
[B]&#9484;&#9472;(jordan@ttyfscker:pts/0)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(1:21:32:%)&#9472;&#9472; [/B]sudo smbmount //zeus.pclab.tntech.edu/users/jmthomas21 pclab -o username=pclab\\jmthomas21,password=$MYPASS

15854: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```[/FONT]
What am I missing here?  I am guessing it doesn't like the name of the share, but the file managers don't seem to mind it.

---

### Post by moffa on 2007-09-27
What I use is:

```
 sudo mount -t smbfs -o username=guest,password=guest //192.168.1.100/share /home/me/sharefolder 
```

so it is basically sudo mount -t smbfs -o username=[username],password=[password] //[share ip]/[share path] [mount path]

---

### Post by jordanmthomas on 2007-09-27
```
[B]&#9484;&#9472;(jordan@ttyfscker:pts/3)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(~)&#9472;&#9488;
&#9492;&#9472;(22:41:%)&#9472;&#9472; [/B]sudo mount -t smbfs -o username=pclab\\jmthomas21,password=$MYPASS //149.149.24.9/users/jmthomas21 /home/jordan/pclab   &#9472;&#9472;(Thu,Sep27)&#9472;&#9496;
16403: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

Same thing.  :(

Am I incorrect in thinking that pclab\\jmthomas21 becomes pclab\jmthomas21?  I think I'm right because otherwise I get an access denied error instead of a nonexistent share error.

---

### Post by jordanmthomas on 2007-09-28
Any more suggestions perhaps?

---

### Post by jordanmthomas on 2007-10-02
I asked over at the Arch forums and they found a thread here at the Ubuntu forums that answered my questions. :lolflag:  

I swear it wasn't there when I searched.  

It turns out you can't mount samba shares that are more than one directory from the very top (who knew?) and I didn't have access to the directory right above mine.  

Anyway, this thread solved my problem:
[http://ubuntuforums.org/showthread.php?t=470171](http://ubuntuforums.org/showthread.php?t=470171)

---

