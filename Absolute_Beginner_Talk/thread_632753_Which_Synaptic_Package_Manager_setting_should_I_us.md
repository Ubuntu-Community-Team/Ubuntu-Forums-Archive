---
title: "Which Synaptic Package Manager setting should I use??? Will I re-claim disk space?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-12-05
Hello Ubuntians....

The Synaptic package manager in Ubuntu 7.10 does not delete packages after installing them but instead keeps them in 'cache'.

With the Synaptic Package manager open go:

settings>preferences>files

Once this opens you will find three choices listed under "Temporary Files":

1. Leave All downloaded packages in cache.

2. Delete downloaded packages after installation

3. Only delete packages which are no longer available.

I would like to know what item# 2 means??? I.E. "Delete downloaded packages after installation"

I tried to find information pertaining to each option and its effect but to no avail. Maybe someone here can be helpful to me?

I was thinking to choose option #2 because I believe that by so doing I can gain additional disk space on my hard drive???????????????

I would also like to understand option # 3 if someone can explain.

Now I just wait for the expert opinions to tell how I should move.


Thank you everyone.

---

### Post by mikewhatever on 2007-12-05
About the second option, the packages you install are first downloaded, then installed. If chosen, these packages will be deleted after the installation.

---

### Post by jasmuz on 2007-12-05
Hello,

2nd option allows you just to download-->install and then.. Poff! all your downloaded files are deleted from your drive and no longer cached. (Meaning that if you download something and uninstall it, but want to reinstall everything.. you must redownload everything again)

3rd option states, that after a prudent lapse of time files will be kept, passed that.. they will be deleted.

---

### Post by lentomies on 2007-12-05
Well I guess that answers my questions.


thank you!

---

### Post by lentomies on 2007-12-05
By the way, will I reclaim disk space?

---

### Post by crjackson on 2007-12-05
> **lentomies said:**
> By the way, will I reclaim disk space?

Yes - you will get back the space occupied by the cached files.

You can also clean it instantly by:

```
sudo apt-get clean
```

---

### Post by hydraconsole on 2007-12-28
i didn't know anything about this. can i just use the sudo apt-get clean to delete the downloaded packages? is that what sudo apt-get clean is for?

thanks

---

### Post by cjm5229 on 2007-12-28
> **hydraconsole said:**
> i didn't know anything about this. can i just use the sudo apt-get clean to delete the downloaded packages? is that what sudo apt-get clean is for?

thanks
Yes, Also sudo apt-get autoclean, and sudo apt-get autoremove.

---

