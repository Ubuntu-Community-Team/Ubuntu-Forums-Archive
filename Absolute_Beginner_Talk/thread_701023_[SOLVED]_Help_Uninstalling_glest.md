---
title: "[SOLVED] Help Uninstalling glest"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by sevenearths on 2008-02-18
I tried the above technique on 'glest' and 'wallpapoz'

didn't work

:(

---

### Post by HermanAB on 2008-02-18
Hmm, I recommend against removing programs, since it can result in collateral damage that you may only discover much later and by then you won't know what the heck happened.

Cheers,

Herman

---

### Post by sevenearths on 2008-02-18
what happens if you can find the package, like the problem im having with 'glest' at the moment.

its time like this i wish i had a nice gui list

:confused:

---

### Post by oldos2er on 2008-02-18
> **sevenearths said:**
> I tried the above technique on 'glest' and 'wallpapoz'

didn't work

:(

 How did you install these packages?

---

### Post by bodhi.zazen on 2008-02-18
use locate to find the package :

```
locate <name_of_.deb>
```

You can then remove the package with dpkg

sudo dpkg -r --purge /path/to/.deb

---

### Post by sevenearths on 2008-02-18
I installed by hand. 'glest' comes as a 'run' package, so i used the following command lines:

(I've been looking for the code for the last couple of minutes.... can't find it, so below is my best guess)

```
sudo chmod +x <file>.run
sudo sh ./<file>.run
```

the binaries can be found on the following page:

[http://liflg.org/forum/viewtopic.php?t=906]("http://liflg.org/forum/viewtopic.php?t=906")

and I tried uninstalling with the following command line stuff:
```

arthur@arthur-laptop:/usr/local/games/glest$ sudo apt-get remove glest_3.1.0-multilanguage
[sudo] password for arthur:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glest_3.1.0-multilanguage
arthur@arthur-laptop:/usr/local/games/glest$ sudo apt-get remove glest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glest
```

any ideas?

---

### Post by sevenearths on 2008-02-18
no joy

I installed a .run file

more can be found at:
[URL="http://ubuntuforums.org/showthread.php?p=1569177#post1569177"]
http://ubuntuforums.org/showthread.php?p=1569177#post1569177[/URL]

PLUS the folder '/usr/local/games/glest' contains a file 'uninstall' (no prefex)
my be I can somehow use this....

---

### Post by bodhi.zazen on 2008-02-18
@sevenearths : I see now you "hijacked" two old threads.

Your issue IMO is unrelated to either, so I pulled and merged them.

It the .run does not have an uninstall option you will need to manually remove the packages.

```
locate glest
```

Now manually delete all those files / directories.

In the future, best create a new thread rather then post on multiple unrelated threads.

---

