---
title: "MacBookPro 11,3 iGPU"
date: 2021-06-23
forum: Apple Hardware Users
---

### Post by aliris on 2021-06-23
Hello!

I'm completely new to linux. I just installed Ubuntu 21.04 on my MacbookPro as Apple announced that my Model would not be supported on the upcoming  macOS Release. 
Overall I am very happy with the Speed and Usability of the System. My only problem is, that Ubuntu does not recognize the iGPU of my model as the MacbookPro seems to shutdown the iGPU as soon as it recognizes booting into another sytem.

I tried the following.

[https://github.com/0xbb/apple_set_os.efi](https://github.com/0xbb/apple_set_os.efi)

But it still does not show the iGPU via lspci. My problem is that is just do not know enough to go any further. I do not know how to study the problem. 

I tried the changing the macOS version in the apple_set_os.efi file and compile it and I also tried different versions of changes to grub.d/40_custom

Any suggestions are welcome to further investigate my problem.

Love Ubuntu but my Macbook is just running hot in the current configuration.

Thank you all for your help.

---

### Post by QIII on 2021-06-23
Moved to **Apple Hardware Users**

---

### Post by aliris on 2021-06-24
Got it to work with [https://gist.github.com/stefanocoding/c6dbf4489f330021bd9335d655c9fbbf](https://gist.github.com/stefanocoding/c6dbf4489f330021bd9335d655c9fbbf)

---

