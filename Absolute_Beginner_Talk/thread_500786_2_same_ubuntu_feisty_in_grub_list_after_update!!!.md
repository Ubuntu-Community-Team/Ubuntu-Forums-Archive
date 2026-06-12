---
title: "2 same ubuntu feisty in grub list after update!!!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by iamgans on 2007-07-14
i just updated feisty from update manager, now when i boot there are 2 same ubuntu in the grub menu list before windows vista! And 2 ubuntu(recovery) also! is this usual? there was only 1 of each before i updated!



ubuntu newbie from mauritius... my first post...

---

### Post by AlexenderReez on 2007-07-14
open synaptic....(make sure you are using the first kernel appears in grub...)
search kernel linux ....

you can see you have install 2 difference kernel...remove older one...

search linux image...

hm...also...remove old kernel.....

---

### Post by brownknight on 2007-07-14
it is normal. if you check you will see the versions are different. you always want to use the latest

---

### Post by agurk on 2007-07-14
Yep, previous posters are correct; if you look carefully, you will see that the two kernels listed in your GRUB menu are in fact not the same.
Sometimes when you update your system, a new kernel is downloaded and installed, but the system does not remove the old one automatically. This is good, because, should there be a problem with the new kernel, you can use the old one.
When you have checked that the new kernel works fine, you can use Synaptic to remove the old kernel and it will be automatically removed from the GRUB menu as well.

---

### Post by iamgans on 2007-07-15
yep... i just checked the versions... the last numbers were 15 and 16... the updated one works fine... 
i'll search and remove the old kernel from synaptic...



thnks... jah bless...

---

