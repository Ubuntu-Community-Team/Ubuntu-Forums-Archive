---
title: "hangs up on booting"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by modi2709 on 2008-01-02
As soon as the booting is complete and the desktop background comes, it gets hanged.
I can not do any operations, cant get the command window, all i see is an empty orange background.

This is just the second time i am starting ubuntu, two days back everything was well. I am new to it. My friend helped me install it. He has been using ubuntu for over 2 years now and he can not figure out what exactly has gone wrong.
He suggested i would get some solutions over here.
So please help this rookie!

Thanks,
Kankshit Modi

---

### Post by ~LoKe on 2008-01-02
Can you boot up the recovery mode without issues?

---

### Post by The Tronyx on 2008-01-02
You may want to run the following:
> 
sudo apt-get install bootchart

That will install a program which will create a .png image showing you the process time during boot of various...well, processes.  Looking at that should be a push in the right direction.

I've also always found that booting the kernel with nosplash speeds things up a lot as usplash has caused me many a hangup.

---

