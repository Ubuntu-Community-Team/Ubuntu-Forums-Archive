---
title: "Grub Trouble"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by sosamv on 2006-10-06
Grub was installed on my 1st HD MBR but i need in on my 2nd HD MBR, how can I install Grub on my 2nd HD MBR (wich is the one that has ubuntu on it)??

Thanx in advance =)

---

### Post by Kateikyoushi on 2006-10-06
Do you plan to remove the first one ? You could set in bios to boot from the first hdd which loads grub. Then no need to install grub again.
Is this a pata sata drive combination by chance ?

---

### Post by sosamv on 2006-10-06
uhm...i just cleaned my MBR and windows is starting normally, so i want to install GAG to choose between windows and ubuntu, but when i did, GAG is picking Windows properly, but when i select ubuntu im gettin a L9999 black screen and thats because grub is not installed on the MBR of my second HD, how can i do that?

---

### Post by jd65pl on 2006-10-06
You could see [this]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html") article on installing grub.

---

### Post by jd65pl on 2006-10-06
You may also find booting with the live cd and running the command below useful

```
man grub-install
```

---

### Post by bulldog on 2006-10-06
Just grab the live cd and do the following things.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

