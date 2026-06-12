---
title: "virtualbox question"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-05-31
i have been able to succesfully install vbox and all its dependencies (doesnt complain when i type "VBoxManage"). but i cant get the gui version to start. nothing happens when i launch from the applications menu.

it works fine on my i386 dapper machine

---

### Post by forestpixie on 2007-05-31
Try VirtualBox in terminal

---

### Post by supersonicdarky on 2007-05-31
o jeez. more missing dependencies >_>

---

### Post by lazyart on 2007-05-31
sudo apt-get install -f

---

### Post by supersonicdarky on 2007-05-31
now im getting this when i try to run a vm
```

Unknown error initializing kernel driver (VERR_INVALID_PARAMETER).
VBox status code: -2 (VERR_INVALID_PARAMETER).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

---

### Post by forestpixie on 2007-05-31
quick question please - what does 

sudo apt-get install -f

do?

---

### Post by bodhi.zazen on 2007-06-01
> **forestpixie said:**
> quick question please - what does 

sudo apt-get install -f

do?

man apt-get :

> -f
--fix-broken
    Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(8) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

---

### Post by forestpixie on 2007-06-02
Thank you - keep forgetting 'man'

:)

---

### Post by bodhi.zazen on 2007-06-02
> **forestpixie said:**
> Thank you - keep forgetting 'man'

:)

:lolflag:

Yea, I know. The funny thing about them is at first they are all Greek .... (or worse). The first time I saw a man page I literally thought *wtf*. I did not understand a single word.

So we all learn to problem solve in other ways, which is fine.

BUT ...

Once you are an intermediate user, GO BACK to the man pages :)

You will find them invaluable :twisted:

---

