---
title: "ln -s question"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-09-13
having a problem creating symlinks...

if i am in /etc/apache2/sites-available

and want to creat a symlink from 002-foo so the link sits in 
/etc/apache2/sites-enabled as 002-foo

i have to use the full directory in my sytax or else i get a red symlink...

ex ln -s /etc/apache2/sites-available/foo  /etc/apache2/sites-enabled/002-foo

when i try ./foo /etc/apache2/sites-enabled/002-foo i get the red symlink... 

do i always have to use the full path or is there a way around this?  sorry about this post being erattic but i have not slept yet...

thanks in advance

---

### Post by Najand on 2006-09-13
When making a symbolic link it is better to use full path for Target, because it may not be able to find the Target, unless when you are just trying to iimagine you are in the folder you are intending to make the link there). Let  me give you an example:
Let us imagine there is a file called "TARGET" in "/TGFOLDER" and we want to make a link in "/DSFOLDER" , if we use:
```

cd /TGFOLDER
ln -s TARGET /DSFOLDER

```
Then we will find a broken link in /DSFOLDER, becuase it tries to find the TARGET not in /TGFOLDER but in /DSFOLDER. Using short pathes are possible, becuase sometimes it is very useful when copying it to somewhere else and  wants to use it without changing any settings.
In your case, when you are in /etc/apache2/sites-available you make symbolic link in 2 different ways:
1. Using the  full pathname
```

ln -s /etc/apache2/sites-available/foo /etc/apache2/sites-enabled/002-foo

```
2. Going to the directory you are intending to make a symbolic link there (or just imagine you are there) and then use short path options (like ".." or ".") to make a symbolic link.
```

cd ../sites_enabled
ln -s ../sites-available/foo 002-foo

```

---

