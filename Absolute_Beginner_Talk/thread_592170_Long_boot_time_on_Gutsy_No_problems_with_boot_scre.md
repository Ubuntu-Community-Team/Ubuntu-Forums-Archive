---
title: "Long boot time on Gutsy/ No problems with boot screen"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Habo on 2007-10-26
Hi all.

First, excuse me for my bad English. 

Since today morning my Ubuntu 7.10 booting about 4 minutes long!  Normal boot is about 1 min. I didn't made any system changes, so I don't understand what's gone wrong. After boot everything works normally.

Here is my Bootchart:
[ATTACH]47850[/ATTACH]

Thanks for any help.

---

### Post by khurrum1990 on 2007-10-26
Hi, did u happen to do anything new on ur computer before u closed it the time before this problem occurred.

---

### Post by Habo on 2007-10-26
hi, khurrum1990

thx for your response.

I forgot to say that shooting down computer is taking  long time to.

No I didn't change nothing special... just tried to change some GTK themes without any problems. I didn't change any hardware components or installed new software. I would like to compare some boot logs, but I don't know which logs should I compare to see the changes. I have installed bootchart after that boot problem, so I cannot compare PNG pictures.

But maybe that boot problem is pointed to another problem I that have sometimes: 
My computer periodically freezes without any specially reason. That happens often if I'm using some peer to peer software like Azureus or Amule. Sometimes I experience freezing if I'm using Mozilla Firefox to. In that case, when I try to reboot y computer, boot process stops and fsck checks automatically my hard disk. Sometimes I'm getting message, that fsck is not able to check it automatocally and I need to start it manually. After that, fsck checks my hard disk, corrects some superblocks and inodes and after reboot everything works fine.

Today morning, after few hours normal work, amule disappeared without freezing of computer. After reboot with fsck check and correction of inodes I'm experiencing that slow booting.

Thanks,

Habo

---

### Post by Qwerty_ on 2007-10-26
Have a look here

[http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

---

### Post by Habo on 2007-10-26
Hi Qwerty,

thanks for response but the solutions described on:

[http://ubuntuforums.org/showthread.php?t=580903]("http://ubuntuforums.org/showthread.php?t=580903") doesn't work for me. My computer still needs 4 min  to boot.

Here is Bootchart after that changes:
[ATTACH]47857[/ATTACH]

Habo

---

### Post by joop905 on 2007-10-26
To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

---

### Post by Habo on 2007-10-26
thx joop905, but that method was described in:

[http://ubuntuforums.org/showthread.php?t=580903]("http://ubuntuforums.org/showthread.php?t=580903")

and didn't work for me. I don't have problem with missing boot splash.

---

