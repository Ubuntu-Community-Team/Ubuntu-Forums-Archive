---
title: "[SOLVED] Firefox 2.0.0.5 shows as 2.0.0.4"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2007-07-21
I updated Firefox 2.0.0.4 to 2.0.0.5 (via update manager). However, in Ferefox [Help] [About Firefox] the version still shows as 2.0.0.4. I restarted the PC/Ubuntu 7.04/ but it still shows the old version number.

In the Instal/Uninstall application the version number listed there in the details is 2.0.0.5

Can I conclude that the update failed or that it was successful?

Thanks

Laurent

---

### Post by por100pre1 on 2007-07-21
Seems like it failed somehow... weird. Check version number with Synaptic.

---

### Post by por100pre1 on 2007-07-21
Lets reinstall it anyway:

```
sudo aptitude reinstall firefox
```

---

### Post by lduplantie on 2007-07-21
Symaptic shows 2.0.0.5. Forgot to mention, but it may not be important, I use the French version of Firefox/Ubuntu.

Laurent

---

### Post by lduplantie on 2007-07-21
I reinstalled Firefox.
The process indicated that it was replacing firefox 2.0.0.5+1-0ubuntu1 (using .../firefox_2.0.0.5+1-0ubuntu1_i386.deb) ...

End result : No change still showing 2.0.0.4

---

### Post by por100pre1 on 2007-07-21
> Symaptic shows 2.0.0.5. Forgot to mention, but it may not be important, I use the French version of Firefox/Ubuntu.

That's not a problem... I use the spanish version.

>  I reinstalled Firefox.
The process indicated that it was replacing firefox 2.0.0.5+1-0ubuntu1 (using .../firefox_2.0.0.5+1-0ubuntu1_i386.deb) ...

End result : No change still showing 2.0.0.4

No ideas here... maybe removing then installing back again... maybe install with [ubuntuzilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla")... notthing sure here...

---

### Post by the.phantom on 2007-07-21
just a hunch?
in the terminal 
type

gksudo firefox

and that will start ff as root, then look at the help about and see what version that is ?

i know by using ubuntuzilla i have not had any troubles with ff or t-bird and have done several updates over the last 8 months?

---

### Post by lduplantie on 2007-07-21
I tried Ubuntuzilla as Add/Remove was asking to use Synaptic. Ubuntuzilla is simpler.

Update was successful with 2.0.0.5

Thanks to all

---

### Post by por100pre1 on 2007-07-21
> **lduplantie said:**
> I tried Ubuntuzilla as Add/Remove was asking to use Synaptic. Ubuntuzilla is simpler.

Update was successful with 2.0.0.5

Thanks to all

You're welcome! By the way Ubuntuzilla is good for installing the latest versions of Thunderbird and Sea Monkey too.

---

