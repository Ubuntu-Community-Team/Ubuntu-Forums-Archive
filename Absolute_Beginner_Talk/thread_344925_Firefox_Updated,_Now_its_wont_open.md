---
title: "Firefox Updated, Now its wont open"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-01-23
Alright, i just installed Ubuntu on my new computer, i have been using it on my old one for a while now so i am not a complete beginner, but i'm pretty confused.

So i installed ubuntu, Firefox was working fine, Rebooted after installing some programs with Automatix. got the system updat diolog telling i their was 98 new updates (the disk i used to install was from the first day of edgy relase, so ALOT of updates) I let it update, rebooted and tryed to open firefox, and it wont open.

I have tryed re-installing it with Synaptic, but still wont work. 

When i try and run it from the terminal i get:

```
james@hackers-dojo:~$ firefox
Segmentation fault (core dumped)

```

That doesnt sound good to me.

can anyone help?

thanks

---

### Post by Bachstelze on 2007-01-23
Autmatix is known to cause problems but I didn't know it could go that far... Can you afford a reinstall ?

---

### Post by Jamesbowden on 2007-01-23
I dont think it was automatix, I think firefox may have tryed to open and do updates for summin just before i pressed my reboot button, because i saw a dialog box of some sort. that could have F*cked it up. I could re-install ubuntu, becuase i have all my Data Backed up, but i rely cant be bothered, is their anyway, i could completely remove firefox, then install it again?

---

### Post by Bachstelze on 2007-01-23
Did you stick with the default Firefox that comes with ubuntu or did you install the build from mozilla.com ? Please paste the output of this command :

```
ls -l $(which firefox)
```

---

### Post by Jamesbowden on 2007-01-23
I get this:

```
lrwxrwxrwx 1 root root 22 2007-01-23 21:42 /usr/bin/firefox -> ../lib/firefox/firefox

```

I just stuck with the deafult that came with Ubuntu 6.10

---

### Post by Jamesbowden on 2007-01-23
/bump

---

### Post by Bachstelze on 2007-01-23
I can't help you about that, I'm a fraid. A segfault usually means there's a problem with some library linked to the executable and I can't see how this wouold happen with a default setup. What does this output ?

```
echo $LD_PRELOAD
```

---

### Post by Jamesbowden on 2007-01-23
> **HymnToLife said:**
> I can't help you about that, I'm a fraid. A segfault usually means there's a problem with some library linked to the executable. What does this output ?

```
echo $LD_PRELOAD
```

I get absolutly nothing, looks like its empty, it just runs the command and returns nothing:

```
james@hackers-dojo:~$ echo $LD_PRELOAD

james@hackers-dojo:~$ 

```

---

### Post by Bachstelze on 2007-01-23
Thats the way it should be. If you had something in it, it could have caused the problem by linking a library to Firefox that shouldn't have been. Now I really can't help further, sorry.

---

### Post by Jamesbowden on 2007-01-23
Sure you dont know how to remove and reinstall firefox? if not, can anyone else help?

---

### Post by Bachstelze on 2007-01-23
Sadly, lots of things in Ubuntu depend on Firefox so you can't remove it without asking for trouble. You could try to reinstall it with Synaptic but I can't see how this would help. Also, maybe you could try installing the Firefox from Mozilla.com followindg instructions [here](http://psychocats.net/ubuntu/firefox), maybe this one will work.

---

### Post by mnunez on 2007-01-27
I am having the exact problem.  Firefox was running well until the newest update(s) was/were applied.  Now I cannot open *any* website; Firefox closes unexpectedly as the site loads (even sites without flash, etc.) and terminal reports *segmentation fault.*  My color depth is 24 bit.  HELP.

---

### Post by mahiyar on 2007-01-28
Try Opera its a nice nifty browser.

---

### Post by mnunez on 2007-01-28
I tried to get Epiphany working last night (used Add/Remove) and it also crashes.  It loads the default ubuntu page fine, but if I try to load google.com (or similar) it reports an error and starts an error reporting process.  I may try Opera when I get home tonight.

Not having fun, yet.

---

### Post by mnunez on 2007-01-28
*Additional tidbit.  If Epiphany is run from terminal, it reports...*

(epiphany:28474): libgnomevfs-WARNING **: Failed to create service browser: Bad state

*Man, I hope someone who knows what this means is reading this.*

---

### Post by mahiyar on 2007-01-28
I have some good news, try this [http://ubuntuforums.org/showthread.php?t=186291](http://ubuntuforums.org/showthread.php?t=186291)

---

### Post by mnunez on 2007-01-28
Ok. Now synaptic closes shortly after I open it.  When run from terminal with sudo, it reports *segmentation fault* as well.  I'm lost.

---

### Post by mnunez on 2007-01-28
Now I got Synaptic working again by deleting the .bin files in a cache...

[http://www.techiegroups.com/showpost.php?p=602599&postcount=3](http://www.techiegroups.com/showpost.php?p=602599&postcount=3)

...but back to square one trying to get a browser to work.  I'm going to completely remove firefox and eiphany as posted elsewhere.

---

