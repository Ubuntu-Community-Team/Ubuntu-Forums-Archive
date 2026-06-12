---
title: "Grub Question"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by TecTec on 2006-04-01
Do you know if it is possible to install grub on another hard drive from Ubuntu?
I have 2 hard drives in my computer and right now Grub is on one and Ubuntu is on the other. Is there a way to fix this without reinstalling Ubuntu?

Thanks

TecTec

---

### Post by souki on 2006-04-01
yes you can, from the grub shell by setting the grub root device and installing grub to the mbr
for example (only example), if your boot partition is on hda1 and you want to install grub on the first disk:
root (hd0,0)
setup (hd0)

hd0 is the first disk (hda)
hd1 is the second disk
hd0,0 is the first partition of the first disk (hda1)

be prudent, read the doc before : [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

---

### Post by TecTec on 2006-04-01
I relealized i have another problem. after I installed Ubuntu I reinstalled XP (for unrelated reasons) and in doing so i moved its boot sequence. Before it was on the same hard drive as GRUB is on now but now it is on the hard drive I want GRUB on. So now when GRUB loads it just gives an ERROR 17 and stops so i can't boot into Ubuntu anymore. How would I fix this?

TecTec

---

### Post by souki on 2006-04-01
when you boot your computer, can you see the grub menu (you have to press [Esc])?
if so, you can try to fix the root partition by pressing [E]
you should see somthing like this:
```
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-19-686 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-19-686
```

---

### Post by Mustard on 2006-04-01
Might I suggest that while you are mucking around with Grub, you try this disk...

[http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=219714](http://freshmeat.net/projects/supergrub/?branch_id=62132&release_id=219714)

It will probably allow you to boot to Ubuntu until such a time as you come to terms with installing grub manually.

I've been using it lately just mucking around with Grub, because I have often been confused with how Grub works.  It's a pretty ordinary looking interface, with no frills, but it seems to do the job. :)

---

