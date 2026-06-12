---
title: "Removing the boot loader so XP will load."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by kingbuxton on 2007-05-20
I dual booted XP and 7.04 - pigged about with it for two days and still can't get Nvidia drivers on nor get my desktop into 1280. Enough is Enough.

Getting shut of Ubuntu is easy, how do I remove the boot loader without having to reinstall XP?

Weekend wasted, sooner I am rid of it the better. Will try again when 7.10 is out, maybe they will have the basics sorted by then. I wont hold my breath.

---

### Post by bobplano on 2007-05-20
you need to restore the windows mbr, which stands for something like master boot record. if you have the recovery XP cd then you can choose the restore option and type in "fixmbr" (without the quotes). if you don't but your computer still boots right, then you can go on the internet and search for fixmbr and there are some programs that restore it.

---

### Post by starcraft.man on 2007-05-20
Easiest way is just to pop in your install cd (Xp I guess) and go to the recovery console and type in fixmbr. That should do it. Then of course make sure the Ubuntu partition is deleted.

I would like to make one thing clear, don't blame Ubuntu for your difficulty installing drivers (and consequently getting proper resolution). Driver issues are never Ubuntu's fault, it is simply the case that most companies either don't have budgets to make versions for linux or they don't care to. In your case, I have no idea why nvidia drivers did not install correctly, as the Nvidia drivers work verywell. [Envy,]("http://www.albertomilone.com/nvidia_scripts1.html") the installer script has worked every time I have used it, and in almost every case I have recommended it (I broke my comp with it once, did something stupid after running it). Did you try that? If it failed even with that, perhaps something was bad with your Ubuntu install? 

In any case, its undortunate you had such a bad experience, perhaps next time you will have more luck. Bye.

---

### Post by kingbuxton on 2007-05-20
Yeah, I tried everything, Envy was one of several methods of getting them on and they all failed. And now my thread has come to an end, so I guess nobody knows what the errors are or how I sort them. Oh I am sure Ubuntu or Linux in general aren't totally to blame. And I only had another go as I upgraded to an nVidia card and figure nVidia drivers verged on fool proof. I don't specifically expect a Windows double click and reboot, I ubnderstand Linux is a bit more hands on and not maid for morons,  but two days wasted is a bit much for what should be such a simple task.  

[http://ubuntuforums.org/showthread.php?t=448758](http://ubuntuforums.org/showthread.php?t=448758)

It's not like I haven't really tried. But this has pushed my patience to the limit. I don't have enough knowlege of the inner doings of Linux to fathom it myself, I am sure I could, should I have such knowlege.

The MBR thing will have to wait now, I didn't think it was as easy as that. Thanks for the replies.

---

