---
title: "[SOLVED] Fix Numlock"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by snkiz on 2007-08-23
How do you make numlock's default status on when gdm boots?

---

### Post by forestpixie on 2007-08-23
If your bios doesn't keep it on you could install numlockx
 In aterminal

sudo apt-get install numlockx

then 

numlockx on

might need superuser if so 

sudo numlockx on

---

### Post by MillDaKill on 2007-08-23
Thanks for the fix.  You could do this as well.

> 
sudo apt-get install numlockx
echo "numlockx on" >> ~/.bashrc


This will append the numlockx on command at the end of your .bashrc script.  whenever you log into the computer it will get executed.

---

### Post by quantumcheese on 2007-08-23
> **MillDaKill said:**
> 
This will append the numlockx on command at the end of your .bashrc script.  whenever you log into the computer it will get executed.

But he asked to have numlock on at the gdm screen.  Putting numlockx into .bashrc won't turn it on until he's already logged in.

---

### Post by forestpixie on 2007-08-23
It just works from the start, once it's in and on - or at the least it does for me. I installed it, turned it on then and haven't touched it since.

Which is also how i understood it to work from previous threads.

---

### Post by snkiz on 2007-08-23
thanks for the fix btw as I understand x server programs run weather your logged in or not so a program like numlockx should do the trick I only wonder if it will still be active after a reboot.

---

### Post by snkiz on 2007-08-25
:confused: This is strange, I checked my bios It says numlock is on, I installed numlockx it seems to function from the comand line. Yet when I log out it goes off. When I reboot Its on during boot sequence but as soon as the kernel starts loading it goes off. :confused: 

I don't get it... I do have a confesson  to make, I'm using edubuntu 7.04, It was the only alternate  cd I could get my hands on as my burner is fubar. But I don't think that should matter, should it?

---

### Post by mnorwood154 on 2007-08-27
I'm running Feisty and had the same problem.  Sorry, don't remember where I found this but it should go in your /etc/X11/gdm/Init/Default before the line that reads exit 0

if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi

This is what fixed it for me.

---

### Post by snkiz on 2007-08-28
thanks that did the trick.:)

---

### Post by Yizi on 2007-08-28
nice trick woked for me as well.

Thanks

---

