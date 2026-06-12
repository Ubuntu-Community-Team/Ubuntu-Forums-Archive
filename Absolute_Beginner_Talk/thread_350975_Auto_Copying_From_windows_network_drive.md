---
title: "Auto Copying From windows network drive"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-02-01
Hey 

I'm writing an exam report (long story), and i need to make backup of it once in a while..
So the question is:

What should i do to copy a *.doc file  from a windows machine to my ubuntu machine every ten minutes automatically?

If i had the time, i would try to write it myself, but it's kinda a big report so.... :-)

Thanks..

---

### Post by EvilMarshmallow on 2007-02-01
Well,

You could write a script that copies the file

[INDENT]cp source destination[/INDENT]

and then set it in cron.  I don't know much about cron because I'm so new to linux but I do know that's what it's for... periodic tasks.

---

### Post by cmol on 2007-02-01
> **EvilMarshmallow said:**
> Well,

You could write a script that copies the file

[INDENT]cp source destination[/INDENT]

and then set it in cron.  I don't know much about cron because I'm so new to linux but I do know that's what it's for... periodic tasks.

I thought the same thing, but how do i choose a source when it's a network drive?

---

### Post by cmol on 2007-02-01
The path is:

smb://cmol-windows/SSO/Dream Theater - SSO.doc

Just tried ```
cp smb://cmol-windows/SSO/Dream Theater - SSO.doc /home
``` But that didn't work..

---

### Post by hyper_ch on 2007-02-01
Try this:

```
cp "smb://cmol-windows/SSO/Dream Theater - SSO.doc" /home/YOURUSERNAME
```

---

### Post by cmol on 2007-02-01
> **sjau said:**
> Try this:

```
cp "smb://cmol-windows/SSO/Dream Theater - SSO.doc" /home/YOURUSERNAME
```

Nope...

Returns this error

```
cp: cannot stat `smb://cmol-windows/SSO/Dream Theater - SSO.doc': No such file or directory
```

---

### Post by EvilMarshmallow on 2007-02-01
What if you simplify the file name, just to be sure?

Call it bob.doc or something with no caps, spaces or anything.  Rename it when you're done making copies of it.

That will eliminate any of the filename errors we might be committing.

Do you have to provide identification when you access the network share, or does it do it automatically for you?

---

### Post by cmol on 2007-02-01
> **EvilMarshmallow said:**
> What if you simplify the file name, just to be sure?

Call it bob.doc or something with no caps, spaces or anything.  Rename it when you're done making copies of it.

That will eliminate any of the filename errors we might be committing.

Do you have to provide identification when you access the network share, or does it do it automatically for you?

Returns this 
```
cp: cannot stat `smb://cmol-windows/SSO/DTSSO.doc': No such file or directory
```

It's auto...

---

### Post by EvilMarshmallow on 2007-02-01
Just found this:  Google is your friend!

[http://technonerd.wordpress.com/2007/01/24/script-to-backup-files-from-windows-share/](http://technonerd.wordpress.com/2007/01/24/script-to-backup-files-from-windows-share/)

---

