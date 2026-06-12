---
title: "removed wine and cannot install it again"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by K-a-M-u-Z-u on 2007-07-01
hi.
i wanted to clean allot of programs that i had installed in the past in wine, removing wine itself didt removed the programs so i have delete manualy the .WINE folder.
since then, i cannot Re-install wine.
i mean, i installed it, but i cant start any program with it.
when i do WINECFG in the terminal i get:
> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/nir', starting in the Windows directory.


when i go into DRIVES tab i get the messege:
> you dont have a Drive C.this is not so great.remember to click ADD in the drives tab to create one
but when i do ADD i get in the path:"../drive_c" 
when i do ok i get:
> err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'

even autodetect is not working.
what am i doing wrong?
thnx.

---

### Post by dfreer on 2007-07-01
Hmmm. Let's try making sure it is completely gone, so do this:
```
sudo apt-get remove --purge wine
sudo rm -Rv ~/.wine
sudo apt-get clean
sudo apt-get update
sudo apt-get install wine
winecfg
```

Once in winecfg, go to the Drives tab and click on autodetect. Does it work now?

---

### Post by K-a-M-u-Z-u on 2007-07-02
thanks man! it worked!
:p:p:p

---

### Post by Krosis on 2007-08-07
> **dfreer said:**
> Hmmm. Let's try making sure it is completely gone, so do this:
```
sudo apt-get remove --purge wine
sudo rm -Rv ~/.wine
sudo apt-get clean
sudo apt-get update
sudo apt-get install wine
winecfg
```

Once in winecfg, go to the Drives tab and click on autodetect. Does it work now?

I would also like to thank you.  I had some trouble with Wine after installing a game, had to remove it and I didn't know what the hell to do, because it wouldn't work when I would re-install it.

So thank you as well, you saved me from even more headaches.

---

### Post by dfreer on 2007-08-07
Glad to help :D

---

