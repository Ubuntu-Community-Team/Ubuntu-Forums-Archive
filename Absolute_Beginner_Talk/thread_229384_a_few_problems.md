---
title: "a few problems"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by OLT on 2006-08-04
ok here are my problems that ive come across that help would be greatly apricieated. 

1. I know that linux is virtually immune to viruses but there are multipule comptuer on my network and im looking for a free antivirus for linux with on access protection (also know as real time protection) so that i can not accidently send a virus to one of the computers on the network. 
2. Also since this is a dual boot computer i don`t think viruses can spread to windows unless i put it in that partion. My windows partion however shows up in linux with the command when i right click unmount volume at the bottom what would happen is I unmounted that partion in linux.
3. Finally im looking for having a small problem with the grub boot loader that came with ubuntu that there after an update there are 2 ubuntu recovery option in it. And its not a problem right now but i was wondering if there was a way to edit the boot loader so i that these would not show up

---

### Post by jd65pl on 2006-08-04
to edit grub open terminal and:

```
sudo gedit /boot/grub/menu.lst
```

Unmounting the windows partition shouldn't have any negative effect.

---

### Post by MaximB on 2006-08-04
1.there is a free antivirus at the add/remove programs
never needed to check it out so I don't know how good it is
2.nothing will happen to your windows
you just won't be able to see it with linux. (if you unmount)
3.already been anwered by jd65pl

---

