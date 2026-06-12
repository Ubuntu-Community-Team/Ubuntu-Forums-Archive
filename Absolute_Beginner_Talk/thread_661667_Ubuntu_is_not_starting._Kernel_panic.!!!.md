---
title: "Ubuntu is not starting. Kernel panic.!!!"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-08
In the update manager 3 of updates can not be installed,so i want to install them from synaptic manager.

Something happened while installing and synaptic manager give an error that i must "there is a an error and i must install updartes from terminal".
I clicked synaptic again but it gave the same error and  it closed.
Then i want to restart computer maybe the problem will be solved .
But no.

"Starting up.
Loading please wait.
18.385846 Kernel panic -not synching:attempted to kill init! "

My computer doesn't start...
What should i do???
Very sad.

---

### Post by Sef on 2008-01-08
Go into GRUB and see if you can go into the grub menu (by pressing esc), and see if highlight recovery mode and see if you boot that way.

---

### Post by rhc on 2008-01-08
I m a newbie.sorry.
I meet with linux 2 days ago.

You mean to write to terminal grub and from there?

Can u behave like telling to a dumb?

---

### Post by philinux on 2008-01-08
Reboot and when you see grub stage 1.5 on your screen hit the esc key.

Wait while a menu appears. Highlight the recovery option and press enter.

---

### Post by Sef on 2008-01-08
When the computer first boots, you have about 3 seconds to press escape (esc), and it will take you into the grub menu.  Your regular kernel should be highlighted, and there should be an 3 other kernels too.  One is the current recovery mode which you want to try first.  If that don't work, then try the other kernel and last the other kernel in recovery mode.

---

### Post by rhc on 2008-01-08
I hesistated that am i missing something and i write to yahoo images "grub " . 
[http://www.flickr.com/photos/pip/310634284/](http://www.flickr.com/photos/pip/310634284/)

are you talking about this by sentence "grub stage 1.5"

i never see a message while my computer starting.

no message about grub. never before.

---

### Post by rhc on 2008-01-08
yeah,i think it is very quick so i didn't see it.
I entered recovery mode. 2nd kernel mode.
It gave the same error with a different number.

---

### Post by (((X))) on 2008-01-08
When I first met linux, I had that every time:P
reinstalled it 30 times or so
..I always used root acconunt

---

### Post by philinux on 2008-01-08
> **rhc said:**
> yeah,i think it is very quick so i didn't see it.
I entered recovery mode. 2nd kernel mode.
It gave the same error with a different number.

Whats is the exact error thats being reported?

---

### Post by rhc on 2008-01-08
So every time will i lose my data?
I didn't do anything also.
Synaptic did it.
(i  m like problem child)

---

### Post by rhc on 2008-01-08
> **philinux said:**
> Whats is the exact error thats being reported?

Like in my first message;

18.385846 Kernel panic -not synching:attempted to kill init!

But the number front is different.

---

### Post by philinux on 2008-01-08
Ok reboot and press the esc key again to get the grub menu.

Below the first recovery entry is there another kernel boot entry. If so highlight that and press enter.

---

### Post by rhc on 2008-01-08
> **philinux said:**
> Ok reboot and press the esc key again to get the grub menu.

Below the first recovery entry is there another kernel boot entry. If so highlight that and press enter.


There are three options after esc.
First one kernel generic bla bal.
2nd one kernel generic recovery bla bla.
3rd one memtest+.

Are you talking about memtest?

---

### Post by philinux on 2008-01-08
No I was hoping you had an older kernel available to boot in grub.

---

### Post by rhc on 2008-01-08
> **philinux said:**
> No I was hoping you had an older kernel available to boot in grub.

So? :) no thoughts?

---

### Post by rhc on 2008-01-08
Is there no other way to reload kernel?
With the live session user mode maybe?

---

### Post by philinux on 2008-01-08
If it was me, and I stress the _me_. I have home on its own partition so for the 15mins it takes I would reinstall.

---

### Post by rhc on 2008-01-08
philinux how can i save my data in computer?
For example,is there a way to install ubuntu over again without formatting to save the data that now exists?

---

### Post by philinux on 2008-01-08
I hoped someone who knows about/seen kernel panic messages would have chimed in with a fix.

But no luck there.

This guide is what I followed. You do it from the live cd. I even backed up my home folder first to a usb pendrive, from the live cd. Useful disk that.

Paranoid or what.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by rhc on 2008-01-08
Thanks for help anyway.
I could'nt solve it and i ll format computer.

---

