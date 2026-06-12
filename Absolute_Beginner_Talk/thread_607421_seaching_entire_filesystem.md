---
title: "seaching entire filesystem"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by singlewc on 2007-11-08
Okay, I give up...

Sorry for bringing up the dark side, and for speaking in terms of drives, vs filesystems, but its the  language I am conversant in.

In windows, if I am looking for a file that I only know is on the C partition, I go to the C:\ directory and type dir filename /s and it will search the entire partition.

I have a partition with ubuntu on it. How do I get 'all the way to the top' of the partition, and search the entire ubuntu/linux  system for 'filename'?

The search applications give me root, usr, etc, lib, and on and on, but I don't want to look in every one individually. I want /

FWIW, at the moment, I want to get rid of every file named vmware* on the entire ubuntu system/partition, so I want to do one search, for every instance.

Little help please?

Thanks a lot,

John

---

### Post by llamakc on 2007-11-08
```

sudo updatedb

```

```

locate vmware

```

---

### Post by singlewc on 2007-11-08
> **llamakc said:**
> ```

sudo updatedb

```

```

locate vmware

```

Thanks. that did the job.

Any chance there is a method to 'locate and delete'   vmware* in one fell swoop?

I know it would be dangerous, but I am experimenting,  not running a company or even a serious install yet, and I figure to have to reinstall Ubuntu a few more times, once I get more comfortable, and figure out  how to make things work the way I want.

Much obliged,

John

---

### Post by ubnewbie2 on 2007-11-08
Why not just uninstall it using add/remove?

---

### Post by llamakc on 2007-11-08
> **singlewc said:**
> Thanks. that did the job.

Any chance there is a method to 'locate and delete'   vmware* in one fell swoop?

I know it would be dangerous, but I am experimenting,  not running a company or even a serious install yet, and I figure to have to reinstall Ubuntu a few more times, once I get more comfortable, and figure out  how to make things work the way I want.

Much obliged,

John

That depends on how you installed it. What method did you use to install it, and what how-to did you follow to do so?

---

### Post by singlewc on 2007-11-08
> **ubnewbie2 said:**
> Why not just uninstall it using add/remove?


It was not installed by Ubuntu's package managers. When I looked for it, to do just that, it was not there.

<shrug>

Thanks,

John

---

### Post by mridkash on 2007-11-09
Try this,

Go to Places>Search for files then write vmware in 'name contains' and select Filesystem in 'look in' dropdown list. Search for it and select all files that come up, right click on them and move to trash. Then you can empty trash to delete them permanently.

---

### Post by hyper_ch on 2007-11-09
if you install vmware with ther install.pl script then there should also be an uninstall script... otherwise you have installed vmware through APT so you should be able to delete it through apt also.

---

