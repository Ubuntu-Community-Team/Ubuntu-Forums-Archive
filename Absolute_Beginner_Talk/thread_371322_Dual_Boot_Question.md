---
title: "Dual Boot Question"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Msonier on 2007-02-26
i have a quick question. 

I am currently dual booting XP and Edgy. When the boot menu comes up i have an option between around 4 different kernels (each with a normal and recovery mode, making around 8 options) plus my XP option. First off, how do i change the default kernel (i don't remeber the number i am using but i have to scroll down to the -generic version (since it has SMP support by default), i would liek this one to be the defualt option. Also, can i limit how many options appear? all i would really like is my current kernel, and the recovery version (perhaps one other previously workign one if soemthign goes askew as i continue to learn?) and XP.

---

### Post by mikewhatever on 2007-02-26
If you uninstall the kernels you do not use, I think that GRUB menu will get updated. If so, you'll be left with only one kernel at the top of the menu and the entry for Windows.
In case you decide to keep some, one way is to hash them out in the menu, or to change the default number from 0 to the one you want.. Here is a good page with all of it : [http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

---

### Post by Coelocanth on 2007-02-26
You can uninstall the ones you don't want with Synaptic Package Manager. Just search for 'linux' and scroll to the kernel images. Mark them for removal and remove them. Your Grub menu will be updated. I just recently got rid of 3 kernels I didn't want with this method and it worked like a charm.

---

### Post by Msonier on 2007-02-26
> **Coelocanth said:**
> You can uninstall the ones you don't want with Synaptic Package Manager. Just search for 'linux' and scroll to the kernel images. Mark them for removal and remove them. Your Grub menu will be updated. I just recently got rid of 3 kernels I didn't want with this method and it worked like a charm.

Yeah, i guess i'll just go through and delete them, i went through menu.lst and tried setting howmany (i think that was the entry) to a lower number but it didnt change anything so i just commented on all the ones i didn't want showign up (so now i only have my curretn kernel, current recovery mode, memtest and XP). 

Thanks for the replies.
-M

---

