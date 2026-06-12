---
title: "[SOLVED] Wine is unable to install on PPC Ubuntu 8.04 Hardy"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by Chucklz15 on 2008-08-26
Hi all, I am having a problem installing wine and blueman on my PPC ubuntu 8.04 hardy. I go to the wine site and run the terminal commands, 
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

That works so then I do this one,
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

And I think it works. Now I try this one,
```
sudo apt-get update
```

And It fails at the end:
```
Fetched 2269B in 1s (1671B/s)
W: Failed to fetch http://download.tuxfamily.org/blueman/dists/hardy/Release  Unable to find expected entry  blueman/binary-powerpc/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://ports.ubuntu.com/dists/hardy/Release  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
chucklz@CHUCKLZ:~$ 

```

What can I do to fix this?

Thanks

---

### Post by flaggh on 2008-08-26
Wine does not run on the PPC platform.  It is intel only.

---

### Post by Chucklz15 on 2008-08-26
Is there something that can do the same things that are available for PPC chips?

---

### Post by DGortze380 on 2008-08-26
> **Chucklz15 said:**
> Is there something that can do the same things that are available for PPC chips?

Now you'd be talking about an x86 emulator. Try googling around, but I think after emulating x86 and running wine or a vm, you're performance and compatibility would be in the tubes.

---

### Post by Chucklz15 on 2008-08-26
Thanks, I was just wondering why it wasn't installing.

---

