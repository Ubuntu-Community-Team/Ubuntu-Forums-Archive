---
title: "synaptic package manager question"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by cbiscuit on 2006-12-20
I think i accidentally typed plf in the sourcelist.  this is my first day using linux and i am using ubuntu 6.06.  how can i access the source list and delete the "plf" that is on line 33 according to the error message.

right now the synaptic package manager will not display any packages because of this error.  please help!

Error message

E: Type 'plf' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Error message

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Thanks

---

### Post by Dev05 on 2006-12-20
Open your sources.list file with

gksudo gedit /etc/apt/sources.list

When it prompts for your password, just type it in. Make your changes, save and close the file. After, you can go into Synaptic and do "Reload" to update your lists of packages.

---

### Post by dpar on 2006-12-20
Try this in terminal.

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

sudo gedit /etc/apt/sources.list

now edit and save sources.list , then do a    sudo apt-get update

I hope this is clear as mud....lol

Edit: oooops Dev05 beat me to it

---

### Post by cbiscuit on 2006-12-20
Thanks so much that was helpful
CNG

---

### Post by lifemaximum on 2006-12-22
Does anybody knows how to get the synaptic package manager reseted to original state!

I keep getting the following error :

```
E: The package hl1430lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

my synaptic package manager is useless rite now and it doesn't show any packages in its list. I am pretty upset the comp is useless if i cannot get anything installed on it ....would apperciate if anyone could help me with that/

---

### Post by dbbolton on 2006-12-22
> **lifemaximum said:**
> Does anybody knows how to get the synaptic package manager reseted to original state!

I keep getting the following error :

```
E: The package hl1430lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

my synaptic package manager is useless rite now and it doesn't show any packages in its list. I am pretty upset the comp is useless if i cannot get anything installed on it ....would apperciate if anyone could help me with that/
i deleted my all of the content in sources.list, saved it, and ran synaptic to reconfigure it by pressing the nice little check boxes under 'repositories' :)

but that was in edgy..

---

### Post by lifemaximum on 2006-12-22
Thanks but it didn work ...

---

