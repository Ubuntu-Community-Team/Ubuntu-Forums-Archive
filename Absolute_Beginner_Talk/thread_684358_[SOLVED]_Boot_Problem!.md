---
title: "[SOLVED] Boot Problem!"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-01
Hello!
I had hardy, but now I installed gutsy. Now when I wanna boot my computer (when I turn it on) I get just a blank screen(first boot choice). I should boot my computer by recovery mode(second boot choice) and inside recovery mode type exit. after that I go to ubuntu and there is no problem. I though update may solve it, but it didn't. What should I do?
Thanks.

---

### Post by Crafty Kisses on 2008-02-01
> **Hoom@n said:**
> Hello!
I had hardy, but now I installed gutsy. Now when I wanna boot my computer (when I turn it on) I get just a blank screen. I should boot my computer by recovery mode and inside recovery mode type exit. after that I go to ubuntu and there is no problem. I though update may solve it, but it didn't. What should I do?
Thanks.

Hmmm, when you get the blank screen, can you type anything, or it's just blank?

---

### Post by Hoom@n on 2008-02-01
It's just blank.
+++
I installed it in two laptops. One Sony VAIO and one COMPAQ and both of them have this problem. (they are old laptops! but ubuntu can work with the graphics very good and all effects work+ubuntu can work with touch pads+it can work with all Fn buttons-> which you have to install their own recovery cd to be so in xp and if install a normal xp they wont work-> it means that ubuntu is better than xp in drivers for these two)
____
Thanks

---

### Post by jan quark on 2008-02-01
I would suggest trying the alternate CD
[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

it solved a lot of booting problems for me

---

### Post by Hoom@n on 2008-02-01
I pre-orderd gutsy before it released, so my ubuntu 7.10 cd is one of the first cds. You mean by downloading and install it again, I'l have no problem?
+++
If that iso in newer and that's the reason it's work, so updates should helped me. Why didn't?
____
Please help more!
Thnaks;

---

### Post by jan quark on 2008-02-01
I can't foretell things which lie in the future

but the Live CD is made to impress
and the alternate CD is made to guarantee a stable installation process 

it is worth a try

does anybody see another solution ? what are the alternatives when you sit in front of a blank screen and can't type anything?

One thing that strikes me is this
> 
I should boot my computer by recovery mode(second boot choice) and inside recovery mode type exit. after that I go to ubuntu and there is no problem.

you mean after you entered the recovery mode and leaved it again you could boot into ubuntu without any problems?

---

### Post by Hoom@n on 2008-02-01
First time when I entered the recovery mode, the last line was this: "root@hooman-laptop:~$". I didn't know what should I do, so I typed "exit". some lines printed on the screen and I went to the ubuntu login window and typed my user name and logged in and there were no problem at all. Second time I turned the computer on, again I couldn't boot by the normal mod and I got the blank screen. So I reset the computer and went to recovery mode and typed exit! This is working for me!
+++
What should I do?
+++
Thanks.

---

### Post by The Tronyx on 2008-02-01
When I hear of blank screen booting, I always assume it to be the Ubuntu splash screen as it gave me so many problems.

First of all:
> 
sudo apt-get install bootchart


That will create a .png image for you to present visual data as to what the problem is when you boot and this will give us a good starting point if the below does not solve the problem.

Secondly, let's try and boot up by passing the nosplash option to the kernel.  To do this:
> 
sudo gedit /boot/grub/menu.lst


This will bring up your grub boot options (more or less)  Now, there is some technical stuff in there but here is a sample of mine
> 
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro quiet nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

As you can see, the first part is my 'normal' boot.  The second one is clearly my recovery mode one as it is labeled such.  You may have a line that looks like this:
> 
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro quiet splash


Simply change that one string to 
> 
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro quiet **no**splash


In case you missed it, just ad 'no' (without the ' 's) to splash, save the file, close and reboot.  You can also edit this line from the grub menu when you boot but I find this way to be the easiest.  Feel free to PM me if you have any problems.

P.S.  Do not copy my kernel boot line, edit nosplash into yours as I would hate to cause more problems.  Good luck!

---

### Post by Hoom@n on 2008-02-01
Thanks, I gonna test it. But, what is splash? And what is the benefit of that program.(Is it this: By the log from that program we can find and solve the problem?)

---

### Post by jan quark on 2008-02-01
thats a splash its the loading screen
[http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png](http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png)
> 
Is it this: By the log from that program we can find and solve the problem?
i think so

---

### Post by Hoom@n on 2008-02-01
Thanks. Gonna test it.

---

### Post by Hoom@n on 2008-02-01
I didn't install that program, but I tryed nosplash mpde and everything was ok. What's the problem and how can I use splash mode?
+++
(I'm downloading the alternate version)
____
Thanks.

---

### Post by jan quark on 2008-02-01
so you your problem is gone, after you followed the above mentioned solution. everything works fine? ubuntu is booting correctly?

why bother with the unimportant splash screen

---

### Post by The Tronyx on 2008-02-01
> **Hoom@n said:**
> I didn't install that program, but I tryed nosplash mpde and everything was ok. What's the problem and how can I use splash mode?
+++
(I'm downloading the alternate version)
____
Thanks.

That is another issue to sort out.  There is some business about the splash image being the wrong size and because of it, some computers hang when booting with splash.  IMO, skip the splash screen, you look way more cool without it. :lolflag:

---

### Post by Hoom@n on 2008-02-02
Thanks!

---

### Post by Hoom@n on 2008-02-03
I installed ubuntu from the alternate disk and now everything is ok. include splash!

---

### Post by BoDwayne on 2008-05-22
For what it's worth I had the same thing happen with 7.04 and this fixed it.  

I have been running 7.04 on a computer for several months, when suddenly I had the same problem - black screen when trying to boot from the default choice, but if I went into recovery and typed EXIT at my desktop name prompt it would boot as normal.  It took me a while to find this thread, but simply changing that one line to **no**splash fixed it.

Thank you for leaving these threads in the archive.

---

### Post by timo74 on 2008-06-04
2point0 -

Was having similar problem with computer freezing on boot. Tried your "nosplash" edit rebooted and now everything works great. 

Thank you very much for taking the time to post in such detail. I am new to the linux system and probably would have never figured this out on my own.

Once again thankyou,
                     tim

---

