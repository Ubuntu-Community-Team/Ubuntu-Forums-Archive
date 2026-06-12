---
title: "Hi,Im a new user!"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by thelinux_guy on 2006-10-14
Hi everyone!,I just did a fresh install of Ubuntu linux "the dapper drake" (6.06) and LOVE IT !!!! What a nice operating system,I came from the PC-BSD distro because it wasnt much a "mature" OS yet (It was missing many files and directories)Ubuntu is a very good OS as I can see and will probably use it forever,I have only one question,When you upgrade to the most resent version,lets say I have Dapper and want to upgrade to Edgy,Do I lose all of my apps/settings/files? or is there a way I can transfer all of this over to the latest release?

---

### Post by ewl1217 on 2006-10-14
With Ubuntu, you can easily upgrade from one version to the next, and even save all your current files, programs, and settings. You can either do it manually, by editing your sources.list (a file which tells Ubuntu where to download software from) and issuing the command to upgade, or by using the update notifier which will do things for you. Some people have had issues doing so, but it's worked every time I've done it. It is reccomended that you back up any important data beforehand.

---

### Post by orb9220 on 2006-10-14
The safest way is to have a seprate /home on a different partition. So if you have to do a clean install you will still have everything in the /home partition.

Example for mine is:

/ which is hda2 is 15gb
/home   is hda3 is 45GB
and 1 gb for swap.

---

### Post by thelinux_guy on 2006-10-14
> **orb9220 said:**
> The safest way is to have a seprate /home on a different partition. So if you have to do a clean install you will still have everything in the /home partition.

Example for mine is:

/ which is hda2 is 15gb
/home   is hda3 is 45GB
and 1 gb for swap.

What I do is have my Doc's on my External HD so when it gets mounted,Its name is 'My Documents"And if I need any of my document later I just go in and copy them to my desktop and delete or save them back to the external HD when im done...

---

### Post by CaveRat on 2006-10-14
> **orb9220 said:**
> The safest way is to have a seprate /home on a different partition. So if you have to do a clean install you will still have everything in the /home partition.

Example for mine is:

/ which is hda2 is 15gb
/home   is hda3 is 45GB
and 1 gb for swap.

Hmmm! So are you saying Edgy dist-update will only effect root and boot basically? I have home, var, swap, root, and boot all as separate partitions.

---

### Post by orb9220 on 2006-10-15
Sorry but have no knowledge about having seperate partions for /var ? that  is on / ?

But swap is always on seprate partition.

But yes if you make the effort to have /home on a separate partition then when you install dapper or edgy to / then that will not affect your installed programs.

Note: When you clean install make sure / and swap is the only thing being formatted. And you have set the right mount points. When gpart does it's thing it likes to autoset / to the largest partition which in my case is  my /home partition and I have to point / to my 15gb partition and not my 45gb home.

But I did have a dapper / root and did a clean install of edgy to root   and my home was intact and my gnome panels,gdesklets,ect... started up like I had them in dapper. But there can be some breakage with a few programs and needs to be updated. My biggiest was getting the new nvidia beta drivers setup as usual.

---

