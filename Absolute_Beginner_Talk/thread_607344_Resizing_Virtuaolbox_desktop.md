---
title: "Resizing Virtuaolbox desktop"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-11-08
I can resize the Virtualbox Window but my desktop stays the same size. How do I fix this? I tried their forum, but to no avail.

---

### Post by chuckyp on 2007-11-08
You would have to change the resolution on the virtual OS that you are running.  Or you could full screen the virtual box window as well.

---

### Post by scwinn on 2007-11-08
When I full size the VB window, it resizes but the Windows desktop does not.

---

### Post by scwinn on 2007-11-08
Ok I adjusted the screen resolution in Windows and it is a bit better but I cannot get the same resolution as my LINUX desktop. Why?

---

### Post by tombott on 2007-11-08
Have you installed the VirtualBox Guest add-ons?

Open VirtualBox, Goto Settings for your Virtual Machine
Goto CD ROM - Mount ISO - VBoxAdditions.iso

/opt/VirtualBox-1.4.0/additions/VBoxGuestAdditions.iso

Start Your VM, open My Computer double click on the CD-ROM and install

Remember to set it back to your CD-Rom drive afterwards.

This should enable you to enter Full Screen Mode etc.

Tom

---

### Post by scwinn on 2007-11-08
When I tried this I got an error saying that the image was not available. What did I do wrong?

---

### Post by tombott on 2007-11-08
Can you find the if you browse to /opt/VirtualBox-1.4.0/additions

If it does not exist I have uploaded it for you [COLOR="Red"][here]("http://freetowatchtv.co.uk/images/ubuntu/VBoxGuestAdditions.iso")[/COLOR]

Let me know when you have downloaded it so I can remove the file.

Tom

---

### Post by scwinn on 2007-11-08
Thanks for your help you have been very helpful. I have struggled a bit with LINUX over the last year, but I am determined to grow in it. It is exciting to learn something new, and be M$ free.

I have dowmloaded the file. I use VB 1.5.2. I hope it will work. Perhaps you can tell me what to do next. I will update you tomorrow.

Thanks again!

---

### Post by scwinn on 2007-11-08
I found the solution. I downloaded the Guest addons 1.5. I had the 1.4 add ons as well. Now The add ons are installed. and I am looking at a beautiful FULL SCREEN.

Thanks! Thanks! Thanks!

A couple of more questions whe you have a chance.

I got VB working by fluke. I want to install on another 2 computers. How do I install from CD? Everytime I try I create the virtual disk... but I cannot get Windows to install.

Also. When I run the Virtual Machine it says that there are Virtual didsks that are not mounted. What is wrong?

Thanks again!

---

### Post by tombott on 2007-11-09
Glad to hear you got the first problem solved.
I have to crash out now, but I will reply tomorrow morning with regards your other issues, but knowing how great this forums is chances are somebody else will have replied with a solution before I wake up!

---

