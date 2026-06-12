---
title: "[SOLVED] Am I going to kill Kubuntu by installing and deinstalling?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by NeillHog on 2007-08-03
Two weeks ago I installed Kubuntu and since then I have been installing the programmes that i need. Occasionally I install a programme to test and then another before deleting the one I don't like.

If I had of done this in Windows then each install would have added "stuff" which the deinstall would then have missed and before long the hard disc and memory are clogged with rubbish.

Does this also happen in Ubuntu? Or is it clever enough to delete the components I no longer need?

Can I carry on experimenting?

Thanks for any and all answers!

Neill

---

### Post by Rocket2DMn on 2007-08-03
Sometimes config files will be left over, so when you remove with apt-get, do
```
sudo apt-get --purge remove *packagename*
```

---

### Post by Cypher on 2007-08-03
Experiment by all means. In most cases when programs are deleted, they remove all traces of themselves, but some programs leave the configuration file back in case you want to re-install them. If that isn't something you'd like, then you can do "sudo dpkg --purge <package name>" to completely remove a package.

---

### Post by NeillHog on 2007-08-03
Thank you both of you.

I take it the config files are not a problem. They are small on the disc and they are not loaded in to memory.

I keep all my "data" on a second hard disc so come the day I reinstall then everything "left over" in /home/ or where ever is going to get deleted anyway :-) Don't know if this is a good idea but it seemed good when I thought of it :-)

Thanks

Neill

---

### Post by Rocket2DMn on 2007-08-03
There's nothing wrong with that.  The advantage to keeping the config files is if you reinstall the program, your old settings will be in place.

---

### Post by NeillHog on 2007-08-03
OK!
Thanks!
I'll sleep better now.

---

### Post by Hospadar on 2007-08-03
Also, sometimes extra packages are installed as dependancies when you install some package, and then are no longer needed when you remove that package.  if you do ```
sudo apt-get autoremove
``` it will remove all of these superflous packages.

---

### Post by NeillHog on 2007-08-12
Thanks all of you for all the help.

Maybe in a year I will still be using Ubuntu after all :-)

---

