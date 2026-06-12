---
title: "My hard drive died and grub returns error 21"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Bakon Jarser on 2008-01-06
I have (had) 2 hard drives.  Windows was installed on my IDE hard drive and then I installed Ubuntu on my SATA hard drive.  Today my IDE hard drive died (a sign from the computer gods to not use Windows:)) and when I rebooted the computer I get grub error 21.  How do I make Ubuntu load now?

---

### Post by c0met on 2008-01-06
Hi,

Below are a couple of links that will help you out with your problem. The second link will lead you to a bootable CD of a program called [COLOR="DarkRed"]**SuperGRUB**[/COLOR]. I have used this. It's easy to understand and it restored my system easily and without fuss. I'd imagine that this one would be a good one for you to try. It's certainly an excellent program to keep handy!

[[COLOR="Blue"]http://users.bigpond.net.au/hermanzone/[/COLOR]]("http://users.bigpond.net.au/hermanzone/")

[[COLOR="Blue"]http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html[/COLOR]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by mike^_^ on 2008-01-06
try booting to a live cd and see if you can repair your mbr from the grub shell.

```
# grub
```
```
grub> find /boot/grub/stage1
```
```
grub> root (hdx,x)
``` using the value returned from the previous command
```
grub> setup (hd0)
```

---

