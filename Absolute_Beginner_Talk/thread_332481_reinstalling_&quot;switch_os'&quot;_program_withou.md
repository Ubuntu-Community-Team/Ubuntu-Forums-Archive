---
title: "reinstalling &quot;switch os'&quot; program without reinstalling ubuntu"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-01-06
hello there :) happy new year and stuff :P

i have 2 big problems and i'd be very thankful if i get some hints how to solve them :)

the first one is, as the title says, i have recently reinstalled my windows but now i can't see that "switch between os' " program, where i was choosing what os i wanna run. how do i install them again without installing the whole ubuntu, cause i have lots of settings that i dont wanna make them all again.

the second one is about my cdrom.. i dont know why, whenever it reads a cd, the computer is restarting and after restart, my pc doesnt show me the cdrom drive... i have to close my pc, and run it again with the cd within so that it works... and btw, it makes a weird noise when computer restarts, some cooler over there seems as it stops and very quickly starts again...](*,) (my source has 400W)

---

### Post by ajmorris on 2007-01-06
Which boot manager or "switch os" program are you using?

---

### Post by the_nomad on 2007-01-06
that ive installed from ubuntu cd

---

### Post by ajmorris on 2007-01-06
if it is grub. can you get into linux?

---

### Post by the_nomad on 2007-01-06
i belive so....

---

### Post by ajmorris on 2007-01-06
then boot into linux and go to a command line. type in [PHP]sudo grub[/PHP]
then in the grub shell type : [PHP]root (hd"your drive number",partition number)[/PHP]
then type [PHP]setup (hd0)[/PHP]

---

### Post by ajmorris on 2007-01-06
for example i have to do 

[PHP]sudo grub
root (hd0,5)
setup (hd0)[/PHP]

---

### Post by the_nomad on 2007-01-06
ok i tried but i cant grub to boot into linux :(

---

### Post by ajmorris on 2007-01-06
you're using  lilo are you? If that's the case sorry i have never used lilo and can't help.

---

### Post by the_nomad on 2007-01-06
lilo? sorry, whats that?:)

---

### Post by ajmorris on 2007-01-06
grub and lilo are the two linux boot managers.

---

### Post by ajmorris on 2007-01-06
have you tried running the grub from you ubuntu live cd. (Assuming you are using grub)

---

### Post by the_nomad on 2007-01-06
no... how do i run it using the live cd?

---

### Post by ajmorris on 2007-01-06
boot the live cd and do a sudo mount -w "you partition" then just do the same steps as before.

If you still get errors can you please post them here.

---

### Post by Obor on 2007-01-06
If you have a Ubuntu live CD handy you can follow [>this thread<]("http://ubuntuforums.org/showthread.php?t=224351")

---

