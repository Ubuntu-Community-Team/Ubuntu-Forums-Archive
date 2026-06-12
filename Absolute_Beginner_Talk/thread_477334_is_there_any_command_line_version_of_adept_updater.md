---
title: "is there any command line version of adept updater? GUI based version has problems"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-18
Hi
thank you for reading my post
When I try to get updates for my ubuntu 7.04 running Kdesktop adept updater return an error like :


```

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages


```


after I select apply updates button.

Can some one please tell me what should i do, or whether there is any command line version of adept updater available?


Thanks.

---

### Post by Seisen on 2007-06-18
Post a screenshot of what packages you are trying to install, maybe their is a conflict.

---

### Post by legolas_w on 2007-06-18
Thank you very much
I attached the updater screen shot.


Indeed updater suggests that those packages need updates, I do not know what is each of them.
Thanks

---

### Post by Songwind on 2007-06-18
To answer the original question, the command line version is "apt-get".

The basic command is
```
sudo apt-get install package-name
```

There's more that can be done with it.  The man pages are pretty good (man apt-get).

---

### Post by Happy_Man on 2007-06-18
You want the command ```
sudo apt-get update && sudo apt-get upgrade
```

---

