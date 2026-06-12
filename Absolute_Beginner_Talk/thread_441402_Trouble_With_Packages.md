---
title: "Trouble With Packages"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by burntmonk on 2007-05-12
When I try to update, install packages, etc, I get this:
```
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```

When I checked that source list it looks like this:
```
# automatically added by gnome-app-install on 2007-05-12 12:02:10.381688
deb http://us.archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse #Added by software-properties

```

But of course I have no idea if it's right.

---

### Post by starcraft.man on 2007-05-12
Ah, I've seen this bug before. [This]("http://ubuntuforums.org/showthread.php?t=431922&highlight=Malformed+line+2+in+source+list") thread had same problem :)

First to fix the problem, type in these two lines in the terminal, Applications > Accessories > Terminal

```
sudo mv /etc/apt/sources.list.d/edgy-multiverse.list /etc/apt/sources.list.d/edgy-multiverse.list.backup
```

after that is done

```
sudo aptitude update
```

Then, I would recommend you replace your sources list... 4 lines doesn't seem right to me and I don't know the program that generated those...

You can copy and paste the edgy list [here]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories") and it should give you all the repos you need, make sure to get the key for medibuntu, its under the list. Make sure to run "sudo aptitude update" again after doing that too.

That should be it, have a nice day :)

---

### Post by burntmonk on 2007-05-12
When I did apt update, I got the same error.  Any ideas?

---

### Post by starcraft.man on 2007-05-12
> **burntmonk said:**
> When I did apt update, I got the same error.  Any ideas?

Wuups, silly me... ha! Sorry, I was a lil sleep deprived I guess, wasn't thinking right... the whole point of the command was to make it not use list.d and I had ya paste that in again... *grumbles at self*

Ok, since you already made the back up, just do this in terminal:

```
sudo rm /etc/apt/sources.list.d/edgy-multiverse.list
```

Then do update again, should work now, my bad monk >.>.

---

### Post by burntmonk on 2007-05-12
Cool, that worked.  Thank you very much.

---

### Post by starcraft.man on 2007-05-12
> **burntmonk said:**
> Cool, that worked.  Thank you very much.

Your welcome, sorry about giving ya bad fix, check out Ubuntu guide to learn a lot basics of Ubuntu and more advanced things. Have fun with Ubuntu. :)

---

