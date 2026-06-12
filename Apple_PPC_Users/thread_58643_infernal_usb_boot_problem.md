---
title: "infernal usb boot problem"
date: 2005-08-21
forum: Apple PPC Users
---

### Post by jameskl on 2005-08-21
[i'd still be interested in knowing if this can be done but i used carbon copy cloner and repartitioned my internal disk & have installed hoary on it – was very painless compated to my wrangling with the usb disk!]


i've been attempting to install hoary to an external usb drive on my tibook so that i can leave my internal drive as is.
after following many similar threads i thought this would work:

- boot install cd & run expert install so i can stop before the yaboot installation which is broken
- abort the install
- boot livecd so can use browser to cut n paste the file changes from [www.orawski.com/~timon/debianppc-usb](www.orawski.com/~timon/debianppc-usb) 
- then when i goto mkinitrd i get a heap of **/dev/null: Permission denied** messages

thinking the livecd hides the real filesystem from the user i tried booting from the install cd then chroot to the usbdisk and running mkinitrd but no joy either (still /dev/null: Permission denied)

can anyone shed any light on this problem?
thanks, james.

---

