---
title: "Need EASY BCD Error Solution"
date: 2013-08-12
forum: Any Other OS
---

### Post by nachinew on 2013-08-12
Hi,

I am currently using ubuntu 13.04, plan to installed dual boot, so I installed windows 8, after the successfull installation of windows 8, I installed Easy BCD and Add a New Entry for Dual Boot, After adding the Entry I restart and the new menu appears as Ubuntu, when I clicked that one, its showing like, below image, 

[IMG]http://s22.postimg.org/81drls0td/9484126215_5eb71c4b9c_z.jpg[/IMG]


I clear this problem by reinstalling GRUB using live CD, now both the OS working as dual. My question is I liked the Easy BCD Dual Boot Menu, How should I solve the Easy BCD error.

---

### Post by dannyboy79 on 2013-08-12
give this a read. [https://neosmart.net/wiki/display/EBCD/Ubuntu](https://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by nachinew on 2013-08-13
> **dannyboy79 said:**
> give this a read. [https://neosmart.net/wiki/display/EBCD/Ubuntu](https://neosmart.net/wiki/display/EBCD/Ubuntu)

not working... while selecting Ubuntu OS at start up. the Ubuntu is not loading.

Please find the error.

[IMG]http://s22.postimg.org/81drls0td/9484126215_5eb71c4b9c_z.jpg[/IMG]

---

### Post by oldfred on 2013-08-14
That error is not grub2 but grub4dos which is EasyBCD's Windows version of grub that it uses to chainload to Ubuntu's install of grub2. 
Either Ubuntu's grub is not correctly installed to the Ubuntu partition or EasyBCD is not configured correctly. 
Best to ask them as it is their issue. Only a few use EasyBCD as most of use use and prefer grub2.

---

### Post by nachinew on 2013-08-14
> **oldfred said:**
> That error is not grub2 but grub4dos which is EasyBCD's Windows version of grub that it uses to chainload to Ubuntu's install of grub2. 
Either Ubuntu's grub is not correctly installed to the Ubuntu partition or EasyBCD is not configured correctly. 
Best to ask them as it is their issue. Only a few use EasyBCD as most of use use and prefer grub2.

How to solve this issue.
Please Guide me

I can Solve by reinstalling grub via live Ubuntu, but I need a solution in Easy BCD

---

### Post by QIII on 2013-08-14
Perhaps oldfred's suggestion was not clear.

It would probably be best to find an EasyBCD forum and ask for help there.  While there are users here who may use EasyBCD, you would be more likely to get help quickly in a forum dedicated to EasyBCD, such as [this one](https://neosmart.net/forums/forumdisplay.php?f=7).

---

### Post by wildmanne39 on 2013-08-14
*Thread moved to **Other OS/Distro Support**.*

---

