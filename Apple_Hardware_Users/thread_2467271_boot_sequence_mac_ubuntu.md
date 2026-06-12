---
title: "boot sequence mac/ ubuntu"
date: 2021-09-21
forum: Apple Hardware Users
---

### Post by janhaex on 2021-09-21
Hy everybody,

I just installed Ubuntu 20.04 in dual boot on my iMac 27" mid 2011 (Mac OS High Sierra). But now it always automatically starts up in Ubuntu, unless I hit my option key, then I can choose between Ubuntu en Mac OS. Is het possible one way or the other to get that choice every time I power up my iMac without pushing that option key?

Many thanks for your answers! 



Jan.

---

### Post by grahammechanical on 2021-09-22
Just to confirm. When you first installed Ubuntu did you get a Grub boot menu that allowed you to choose between Ubuntu and Mac OS? Try running this command and see if the output mentions the Mac OS.

```
sudo update-grub
```

P.S. The command will ask for a password. It is the password you choose during the Ubuntu installation process. Do not expect to see the password printed on the screen.

Regards

---

### Post by ActionParsnip on 2021-09-22
Easy peasy
```

sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
sudo update-grub

```
The number in the file dictates the order, so if you make the number lower than the Linux file in /etc/grub.d then it appears earlier.

---

### Post by janhaex on 2021-09-22
Hello [COLOR=#000000]grahammechanical,

[/COLOR]When I first installed Ubuntu, I didn't get the Grub boot menu.

I used your commandline and got the following result:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289184&stc=1[/IMG]

That "Initrd-schijfkopie", could this be the Mac OS?

After the commandline, I restarted my iMac, but the Grub boot menu still doesn't show up.


Kind regards,


Jan

---

### Post by janhaex on 2021-09-22
Hello [COLOR=#000000]ActionParsnip,

I also tried your commandline, but got the following error-message:

[/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289185&stc=1[/IMG]

Again I restarted my iMac, but still no Grub menu...


Kind regards,


Jan.

---

### Post by bobunderwood99 on 2021-09-22
[https://linuxnewbieguide.org/how-to-install-linux-on-a-macintosh-computer/](https://linuxnewbieguide.org/how-to-install-linux-on-a-macintosh-computer/)

---

### Post by ActionParsnip on 2021-09-23
What is the output of:
```

ls /etc/grub.d/*

```
Thanks

---

### Post by janhaex on 2021-09-23
Hello everybody,

In the meanwhile I'm using rEFInd bootloader. After trying many different things in terminal, without the success I hoped for, i found rEFInd on SourceForge.net.

I downloaded and installed it directly in Ubuntu, and after rebooting, it's working. :P

Nevertheless, I wish to thank everyone wo helped me with his/her advice. For now this thread can be closed. 
Hope to meet you again in the future...

Regards,


Jan

---

### Post by ajgreeny on 2021-09-23
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit as most users know very little about Apple hardware.

---

### Post by janhaex on 2021-09-24
@[COLOR=#000000]ActionParsnip[/COLOR]
I was too happy too soon :( rEFInd worked just for a few days.
I got the following result inserting your commandline:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289197&stc=1[/IMG]
[COLOR=#000000][/COLOR]
But nothing further, no boot manager at restart;

Regards,

Jan

---

