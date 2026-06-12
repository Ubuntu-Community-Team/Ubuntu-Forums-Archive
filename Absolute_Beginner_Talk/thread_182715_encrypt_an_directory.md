---
title: "encrypt an directory"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-05-26
I am new when it comes to encryption bu is it possible to encrypt only a directory? And how do I do that?

I only found how to encrypt the hole harddrive in search :)

---

### Post by angkor on 2006-05-26
What dir do you want to encrypt? If you want to encrypt your home dir, put it on a separate partition and encrypt that.

I don't know about encrypting directories though, couldn't find anything.

---

### Post by jimcooncat on 2006-05-26
By putting "crypt" in Synaptic's search box, I came up with these for files:

bcrypt, ccrypt, mcrypt, and rsyncrypto. 

That last one looks interesting, rsyncrypto. I use blowfish with SSH for speed, so bcrypt would be the second one I'd try.

For a whole directory, you could just tar it up first, then encrypt it.

You can also use the block level device crypto by using a file as a block device. I've seen it done, and have done it myself with some long-forgotten scripts. Don't ask me how right now though! 

You might also want to check out EncFS: [http://arg0.net/wiki/encfs](http://arg0.net/wiki/encfs)

---

### Post by IsKall on 2006-05-26
okey, thanks for the help.

---

### Post by 2501 on 2006-05-30
I am using ccrypt and it works. I went to the target directory and then:

ccrypt -e *.*file extension*

After that just enter your personal key and the new encrypted files will have the extension *.cpt. 

done.

I hope this helps.

-2501 

ps: you can type also more than one extension:

ccrypt -e  *.c  *.bz  *.tgz *.bz2

---

### Post by Jadd on 2007-12-14
I guess you could use truecrypt and mount the crypted drive to a directory.

---

### Post by Jadd on 2007-12-14
You can also use encfs:
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by airtonix on 2007-12-19
encfs is the way to go. nautilus-scripts around that let you right click a folder and encrypt it with a supplied passphrase/word

requires admin to setup initially though

---

### Post by bone2006 on 2007-12-27
I liked truecrypt in windows, bu I honestly didn't like all the terminal commands for truecrypt.
encfs looks very promising.  I was looking the link below and was wondering are there any problems with kubuntu?
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by kpkeerthi on 2007-12-27
Try [cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html")

---

### Post by hyper_ch on 2007-12-27
> **bone2006 said:**
> I liked truecrypt in windows, bu I honestly didn't like all the terminal commands for truecrypt.

All the commands?

There's basically three commands needed
(1) create a container
(2) mount a container
(3) umount a container

That's all you need and it's not that difficult.

---

### Post by bone2006 on 2007-12-28
Maybe it's the commands are not easy for me to memory.  Even mounting an ISO file I have to google.  I just can't seem to memorize "mount -t iso9660 -o loop image.iso" yeah I can memorize the mount part............but the rest I always forget if I'm mounting once a month.  Seems just to mount an ISO file is easier to google.  If I typed in "mount -t iso9660 -o loop image.iso /mnt/image/" daily than it wouldn't be a problem.  

Maybe I should try the CLI and put some alias and give truecrypt a try.  I found this short tutorial
[http://tinyurl.com/yrayca](http://tinyurl.com/yrayca)

---

### Post by hyper_ch on 2007-12-28
you can put them in a shell script, that way you just run the script and don't have to remember the actual command...

---

### Post by bone2006 on 2007-12-28
Truecypt was much much easier than I thought.  I didn't realize that I could pass it -c and it would interact asking me the encryption I wanted and things of that nature.
I created an alias for the one encrypted volume I want to use, so that seems to work for me.

Every now and then I read people telling me I should create a shell script, but really clueless when it comes to that, are there any tutorials out there for that?

---

### Post by hyper_ch on 2007-12-29
Well, a good resource to start is: [http://www.linuxcommand.org](http://www.linuxcommand.org)

However you can make it very simple:

(1) create a file tcmount.sh

(2) fill it with this code:
```

#!/bin/bash
MOUNT COMMAND

```
Replace the mount command with the actual command you use to mount it

(3) Make that script executable

(4) Run it ;)

And for umount do the same...

---

