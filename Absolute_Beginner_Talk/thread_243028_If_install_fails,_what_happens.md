---
title: "If install fails, what happens?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Dantu on 2006-08-24
I just tried to install EasyUbuntu and I ran this:

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.022.tar.gz)
tar -zxf easyubuntu-3.022.tar.gz
cd easyubuntu
sudo python easyubuntu.in

Something looks like it's getting installed but after a while I get a message stating that I need to solve the problem with the broken packages..(?)

Which packages?

This is what it writes in terminal:

System sanity check: PASSED!
['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list']
In update ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--update-at-startup']In Install ['/usr/sbin/synaptic', '--hide-main-window', '--non-interactive', '-o=dir::etc=./conf', '-o=dir::etc::sourcelist=sources.list', '--set-selections']

Any bright ideas?

---

### Post by Metacarpal on 2006-08-24
That text is normal, it's just EasyUbuntu doin' its thing.  What is the exact error message you got about broken packages?

---

### Post by Dantu on 2006-08-25
The exact message is (translated from swedish):
"Could not continue, Check the broken packages!"

Shall I check them in Synaptic?

---

### Post by kinematic on 2006-08-25
it's an obvious step to take ;)

---

