---
title: "install troubles"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by evoasis on 2006-01-28
brand new to ubuntu, used gentoox about 2 yrs ago on xbox, so im pretty much a newb... annyyywho, glad to have gotten rid of xp, no trying this which came with the latest linux magazine as a free distro...

 the problem begins and..ands at what i thought would be an easy install of a simple program.. GAIM. use it on windows and remembered using it on xbox gentoox...this is what pops up when i try to install...

Could not open "gaim_2.0.0cvs2-1_i386.deb"

Archive type not supported.

thanks for any pointing in the right direction....

---

### Post by evoasis on 2006-01-28
appears gaim came withubuntu, so, even if it wasnt installed, why does it say that error?

---

### Post by evoasis on 2006-01-29
one more thing, this synaptic , where and what and how can i use this to download stuff, like wine, so i can enter commands..
for example...
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by dueY on 2006-01-29
Looks like you tried to download the new gaim?  Not sure where you got the package from but I'm also not so sure the latest gaim is stable yet, it's still beta.

And as for the "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" 

```
sudo gedit /etc/apt/sources.list
```

and add that line in there.

---

