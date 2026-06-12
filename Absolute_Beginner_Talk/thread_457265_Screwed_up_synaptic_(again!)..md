---
title: "Screwed up synaptic (again!)."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by fjf on 2007-05-28
...Trying to install virtualbox.  Gdebi seemed hanged (after one hour of thinking about it) and I tried to stop it shutting down the system.  Remember I come from windoze (if that's an excuse!).  Anyway, now gdebi says it cannot open the .deb file, and synaptic says that virtualbox must be reinstalled, but there is a file missing, and internal error opening cache.  And refuses to go any further.  Help, please!!.

---

### Post by Hobo Joe on 2007-05-28
Try:
```

sudo aptitude purge virtualbox

```
Then:
```

sudo aptitude install virtualbox

```

I've never used virtualbox, so I'm not sure it's in the universe repositories, so make sure you have the repository for it before trying to install.

---

### Post by Happy_Man on 2007-05-28
```
sudo apt-get -f install
```

See if that fixes it.....

---

### Post by forestpixie on 2007-05-28
and if you still have problems Bapoumba gave me this which might help

dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by fjf on 2007-05-28
This last dpkg--remove did it!.  Thankyou, Thankyou, Thankyou!.

---

### Post by forestpixie on 2007-05-28
If it's mine that helped - thank Bapoumba - I just remember the headache!!!

:)

---

### Post by bapoumba on 2007-05-28
You're both welcome ^^

---

### Post by fjf on 2007-05-28
Well, it seems I was too optimistic. I tried to install virtualbox again, and (an hour later) gdebi is still thinking.  What can be done now (because it is clear I should not stop gdebi again)?.

---

### Post by forestpixie on 2007-05-28
Hi - if I'd known you were going to have another go I would've told you I did and ended up in the same place again #-o

But if nothing else it'll be easier getting it sorted - it all got a bit ](*,) for me and I left it alone - till next time

Have you seen this

[HTML][http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)[/HTML]

or you might look at vmware

[HTML][http://ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows](http://ubuntuforums.org/showthread.php?t=342631&highlight=virtual+windows)[/HTML]

[HTML][https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO)[/HTML]

Good luck though and if nothing else your threads on p1 again

:)

---

