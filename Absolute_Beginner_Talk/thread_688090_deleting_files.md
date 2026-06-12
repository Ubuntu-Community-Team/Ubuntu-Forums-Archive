---
title: "deleting files"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by revanthedarth on 2008-02-05
Well, i have a problem with deleting files. I know that when i delete a file, it can be recovered. How am i supposed to delete a file for good, so that no one finds out?

Recovering programs even say that they can recover files after format. I know that that's not possible on most cases, but i can't format either.

The problem is on an XP machine, not mine. So Windows-specific programs will do too.

---

### Post by wolfen69 on 2008-02-05
```
sudo apt-get install secure-delete
```
sorry, didnt see the last line. for xp, eraser is a good free secure delete/wipe program. [http://www.heidi.ie/eraser/](http://www.heidi.ie/eraser/)

---

### Post by Ex-windows on 2008-02-05
yes I second that. eraser can rewrite the files up tp 35 times if you want. Will also do entire folders and the Trash bin. You can also use it to erase (overwrite) the unused disk space. It is an excellent program. Jus type "eraser" into google or yahoo. Itshould be easy to find.

---

### Post by revanthedarth on 2008-02-05
Thanks. But i have already deleted the files. Will eraser help?

---

### Post by Ex-windows on 2008-02-05
Not really sure I guess you could erased the unused spave and Stop the system restore function and restart it ( if it is on)
 Also there should be a way to turn off the Paging File or something to that effect.
 Try typing DR XP into a search there was a great site with xp tweaks. . Also SPybot search and destroy (Free) has alot of extra tweaks that might help. It;s been over a year so IDont remember .I see if I can find my old links.

SCRATCH  the Dr xp.
Sorry I cant find those links But another way occurred to me and that is maybe "recover the files" Then Use eraser to Erase
Itried Google with Delete Files and then XP Tweaks. You might find more info there.

[http://en.wikipedia.org/wiki/File_deletion](http://en.wikipedia.org/wiki/File_deletion)
[http://tech.yahoo.com/blog/null/50840](http://tech.yahoo.com/blog/null/50840)

---

### Post by nemilar on 2008-02-05
From the command line, the
```
shred
```

tool (installed by default, I believe) can be used to overwrite a file many, many times, which will make sure it's really, really gone.

One thing, though, is that as of ext3, when you delete a file, it's not just marked as "empty space" but left with its contents in tact (this is the case in Windows, and with ext2); the file is overwritten with zeros, so it is a lot harder to restore a deleted file without a whole bunch of work.

But if you really don't want a file to ever, ever be recoverable, shred will do the trick.

**EDIT:** whoops, I missed the last line about XP, too.  The above is for Linux machines, obviously.

---

### Post by hyper_ch on 2008-02-05
Well, even it would require to overwrite several times in order to not be able to restore it anymore (in a forensic lab). The safest solution IMHO is a total encryption of your harddisks... then you just need to normal delete the file. While using a strong password they can read the 0s and 1s but wouldn't be able to put it together to its true meaning.

---

### Post by Linder on 2008-02-28
> **hyper_ch said:**
> Well, even it would require to overwrite several times in order to not be able to restore it anymore (in a forensic lab). The safest solution IMHO is a total encryption of your harddisks... then you just need to normal delete the file. While using a strong password they can read the 0s and 1s but wouldn't be able to put it together to its true meaning.

I work as a computer forensic within law enforcement, and I can say that even though you encrypt your disk, it can still be cracked and viewed. Many semi-experts think they know a lot about computers, when in fact they do not. Your encryption is never safer than your password is.

---

### Post by hyper_ch on 2008-02-28
sure it can be cracked... but using no encryption at all makes it a lot simpler to get data out of it... but then a fully encrypted system with a 20+ key passphrase (number, case sensitivity, special chars) will take some effort to get cracked...

Either there's a security issue with the encryption method
or
a weak password was used
or
you have to relay on brute force

Nothing is 100% safe but you can raise the security levels by that.

---

### Post by Linder on 2008-03-04
> **hyper_ch said:**
> sure it can be cracked... but using no encryption at all makes it a lot simpler to get data out of it... but then a fully encrypted system with a 20+ key passphrase (number, case sensitivity, special chars) will take some effort to get cracked...

Either there's a security issue with the encryption method
or
a weak password was used
or
you have to relay on brute force

Nothing is 100% safe but you can raise the security levels by that.

100% correct.

---

