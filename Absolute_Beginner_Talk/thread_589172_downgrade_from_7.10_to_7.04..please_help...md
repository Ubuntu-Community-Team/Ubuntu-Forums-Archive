---
title: "downgrade from 7.10 to 7.04..please help.."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by madu on 2007-10-23
Hi guys..


I was working fine with 7.04 and in the morning I saw this article on SD about Ubuntu 7.10.. so the first thing I did when I came to in the morning was to upgrade to 7.10.. and hell broke lose :(
Everything was wroking fine but after upgrade even my wired connection wasnt working.. suprisingly wireless is fine.. I use a Lenovo T60 and work with a external monitor.. 
first thing it complined after upgrading is about display.. I could not get the external monitor to work in correct resolution.. my Gaim isnt working.. I dont know what else isnt working..  and I dont have a xorg.conf file.. there are many xorg.conf1 and xorg.conf.original-0 files.. I tried to save one as xor.conf but strangely after a little while the file is gone again...

please.. please.. is there anyway I can role it back to 7.04... the way it was... any way??
please.. any help is greatly appreciated.. thank a million guys,,

Madu...

---

### Post by GSF1200S on 2007-10-23
> **madu said:**
> Hi guys..


I was working fine with 7.04 and in the morning I saw this article on SD about Ubuntu 7.10.. so the first thing I did when I came to in the morning was to upgrade to 7.10.. and hell broke lose :(
Everything was wroking fine but after upgrade even my wired connection wasnt working.. suprisingly wireless is fine.. I use a Lenovo T60 and work with a external monitor.. 
first thing it complined after upgrading is about display.. I could not get the external monitor to work in correct resolution.. my Gaim isnt working.. I dont know what else isnt working..  and I dont have a xorg.conf file.. there are many xorg.conf1 and xorg.conf.original-0 files.. I tried to save one as xor.conf but strangely after a little while the file is gone again...

please.. please.. is there anyway I can role it back to 7.04... the way it was... any way??
please.. any help is greatly appreciated.. thank a million guys,,

Madu...

Hmm, no you cant go back to 7.04. I can possibly help you fix a few things. You say you dont have an Xorg.conf??? Then you must be stuck at the command line, huh? If you are at the command prompt, you can try:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

which will generate a new xorg.conf.

If youre able to try and use gaim though, you should have an xorg.conf.. please look again and make sure before you create a new one.

For the ethernet problem, please post the results of 

```
iwconfig
```

and well go from there...

---

### Post by rsambuca on 2007-10-24
You can't downgrade without re-installing.

---

### Post by GSF1200S on 2007-10-24
oh crap... i made a mistake.. its not iwconfig- wow, what a stupid mistake.

Please post the results of:

```
ifconfig
```

sorry..:oops:

---

### Post by madu on 2007-10-24
Thanks a million guys..
The ethernet started to work after restarting the interface.. anyways the X1400 still seems to be having problems and I see I'm not the only one..
Tried few things.. even installed the newest ATI drive released yesterday.. there is an improvement but still not completely fine..
anyways I think I'm gonna re-install 7.04 again.. and upgrade when there is a proper X1400 driver released for ubuntu... Thanks heaps again fellas..

Madu..

---

### Post by sailor2001 on 2007-10-24
might I suggest you install 7.04 as a dual boot with 7.10 so you can go back to 7.10 at your leisure to update and do any repair needed while still maintaining a good working distro.

---

