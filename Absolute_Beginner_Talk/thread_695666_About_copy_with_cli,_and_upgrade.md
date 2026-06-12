---
title: "About copy with cli, and upgrade"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2008-02-13
Is it possible to copy several folders at the same time(meaning: using one command), using cli?

Lets say I have a folder, and the folder have 5 folders with files:. I want to copy only 3 of them; right now I know how to copy one and one with one command(using scp)

And do you know what the difference is for:
sudo aptitude upgrade
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

Thanks for any replay:-)

---

### Post by hyper_ch on 2008-02-13
Well, if those folders have something in common like a prefix or something:

```

cp -Rp folde* /to/new/location/

```

Or you could write a a shell script that copies a list....

for teh differences in aptitude I'd suggest to consult the manpages.

---

### Post by Trail on 2008-02-13
To copy:

```
cp file1 file2 file3 targetdirectory
```

To copy a directory with all files contained, use cp -r

---

### Post by jrib on 2008-02-13
> **_sAm_ said:**
> Is it possible to copy several folders at the same time(meaning: using one command), using cli?

Lets say I have a folder, and the folder have 5 folders with files:. I want to copy only 3 of them; right now I know how to copy one and one with one command(using scp)

If you have 5 folders, say ```
a b c d e
``` and want to copy a, b, and c somewhere you just do ```
cp -a a b c /path/to/somewhere/new
```.  The -a is the important part, see "man cp" for details or ask here if that is not clear.

> **_sAm_ said:**
> 
And do you know what the difference is for:
sudo aptitude upgrade
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

From "man aptitude":

> 
       safe-upgrade
           Upgrades installed packages to their most recent version. Installed
           packages will not be removed unless they are unused (see the
           section &#8220;Managing Automatically Installed Packages&#8221; in the aptitude
           reference manual); packages which are not currently installed will
           not be installed.

           It is sometimes necessary to remove or install one package in order
           to upgrade another; this command is not able to upgrade packages in
           such situations. Use the full-upgrade command to upgrade as many
           packages as possible.

       full-upgrade
           Upgrades installed packages to their most recent version, removing
           or installing packages as necessary. This command is less
           conservative than safe-upgrade and thus more likely to perform
           unwanted actions. However, it is capable of upgrading packages that
           safe-upgrade cannot upgrade.
           Note
           This command was originally named dist-upgrade for historical
           reasons, and aptitude still recognizes dist-upgrade as a synonym
           for full-upgrade.

First, "upgrade" is the same as "safe-upgrade".  I believe "upgrade" is deprecated now, and "safe-upgrade" should be used. It upgrades all your packages to the latest version without removing anything.  "full-upgrade" does whatever it takes to get your packages upgraded, including removing packages if it has to.  So if you use this, you need read carefully what aptitude wants to do before you accept it.

By the way, you should start new threads for unrelated questions because many people only look for unanswered posts.  So if I had only answered one question, the other would be less likely to be noticed.

---

