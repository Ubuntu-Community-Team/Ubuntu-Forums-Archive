---
title: "How to update kernel to linux-2.6.21.3 ????"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by sharky2x2x on 2007-05-26
Hi there,

I'm trying to update my kernel version from linux-2.6.15.28-386 to linux-2.6.21.3 due to the problems i had while using ubuntu 7.04, as many people i had problems to connect using my wireless connection, so i've decided to update my kernel to see if i can make it work again, I'm currently running ubuntu 6.06. I've read some tutorials already but i don't get to any point in particular, My greatest progress was download and install the kernel but when trying to update the GRUB menu i ****** it up ](*,)](*,) ( i wont tell you how, youll beat the sit out of me) and i lost all work done, Can somebody point me to a good tutorial on how to update your kernel. I've googled it already but nothing.

thanks in advance for your help.

Sharky2x2x

---

### Post by sharky2x2x on 2007-05-26
any new ideas?

---

### Post by snakedr on 2007-05-26
I used the following Master Kernel Thread [*http://ubuntuforums.org/showthread.php?t=311158&highlight=compile+kernel*]("http://ubuntuforums.org/showthread.php?t=311158&highlight=compile+kernel")
with some slight modifications.

Change the references for the 2.6.20 source to the 2.6.21.3 source.

If all goes well you will end up with 2 .deb files to install the new kernel. After you install the .deb files the installer automatically adds the necessary entries to the grub menu. Your previous kernel will still be there to boot your system if your new kernel won't boot.

By the way I'm running linux kernel 2.6.21.2.

---

### Post by sharky2x2x on 2007-05-27
Hi there,

Thanks for your help,im gonna give it a try and ill let you know later on today. I have a question for you snakedr, what made you choose 2.6.21.2?

thanks
Sharky2x2x

---

### Post by sharky2x2x on 2007-05-27
Hi there
 It worked like a charmed, thanks for your help, the problem now is that my wireless is completely gone ( lol ) :):):):):):):)

But thats a different story.....

Sharky2x2x

[[IMG]http://www.myimghost.com/img/9fff3a625c0e9c8f5f54f5c573808c35/Done_it.png[/IMG]](http://www.myimghost.com)

---

### Post by snakedr on 2007-05-27
I compiled the 2.6.21.2 kernel the day before the new kernel came out. According to the changelog of the 2.6.21.3 kernel the only change had to do with one item. I think I'll wait for a few more changes before I update again.

What kind of wireless are you dealing with?

---

### Post by sharky2x2x on 2007-05-30
Hi ,

Sorry for the delay in my response but i've been a bit busy for the last couple of days.

The wireless connection i used to have ;) was a 3Mb regular home connection, wireless card IPW2200G , i can see the card in the devices manager but i'm afraid i dont know how to activate it. Be a bit more specific about what details you need and i'll let you know.

Thanks for your help
Sharky2x2x

---

