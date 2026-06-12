---
title: "kubuntu doesnt detect my partitions, ndiswrapper not installing"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-07-30
my friend installed kubuntu feisty, but like when i installed ubuntu and all my windows drives were mounted on the desktop , his drives didnt mount... can you help?


and about the second problem.. he wants to install ndiswrapper , so he downloaded the latest version.. extracted it , then cd to that folder using terminal and gave these commands 

sudo make uninstall

make

sudo make install

but it gives some error on the last part.. its a clean install of kubuntu so mayb build essential is not installed.. can you tell me a good guide about installing it from the cd???

like if sudo apt-get install build-essential didnt work , and he has to go to synapitic and install it from cd.. hes new so i would like a good step by step guide to do that

---

### Post by Inxsible on 2007-07-30
you need to post the fstab here. See if the automount option is included for the said drives.

```
kdesu kate /etc/fstab
```

---

### Post by threeonethree on 2007-07-30
ok but the first priority is to install ndiswrapper , so he can connect to the net .. how can he install the build-essential package from cd when he is using ubuntu .. using the adept package manager?

---

### Post by threeonethree on 2007-07-30
help?..

---

