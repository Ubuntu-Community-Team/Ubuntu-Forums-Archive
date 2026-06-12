---
title: "700m Widescreen/ Pantech PX500"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by keenanjparsons on 2007-07-21
I installed the 915resolution and then edited one of the lines to include the 1280x800. Then I verified that it would with sudo killall gdm then sudo gdm and it comes back in 1280x800 mode. Perfect. Tried to edit the bootmisc.sh file and it seems that no matter what I do I cant get it to work, i.e. boot automatically into 1280x800. Furthermore, it seems when I went back in to edit the bootmisc file, it is blank. What should I do? In gedit what is the proper steps for closing it so the file saves properly. I know there are alot of posts on this and I really did attempt to resolve this issue before posting. Any insights would greatly be appreciated. In addition any links to setting up the px500 sprint wireless aircard? I don't have internet connection any other way, and rebooting into windows to try to solve my ubuntu problems is frustrating. Thanks for any help.

---

### Post by Foxmike on 2007-07-24
I don't know about the file you are talking about, but if you open it using
```
gksudo gedit <name-of-the-file-here>
```
then you should be able to save it afterwards.  If you just open the file without the "gksudo" in front, the file will open in read-only state.

---

### Post by NDH2008 on 2008-01-14
I also need help setting up the PX500...:guitar:

---

### Post by svQuick on 2008-01-23
I run a px500 on kppd with no little problems.  I find a few issues with unexpected shutdowns and dhcop errors but overall it works. My service provider is sprint and they have an ubuntu how to.  I have set it up on many laptops and it works.

---

