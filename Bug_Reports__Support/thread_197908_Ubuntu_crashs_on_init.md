---
title: "Ubuntu crashs on init"
date: 2006-06-16
forum: Bug Reports / Support
---

### Post by ramongadelha on 2006-06-16
Today I received an notification of update. Ok, I have downloaded the update files and installed. 

After the update, appeared an notification saying to reboot my pc. Done, I rebooted!

But when initing my Ubuntu, my system is stopped on "Loading hardware modules".

Ah, I had reiceved two kernel images; 386 and 686.

I tried to init with the 386 image and done! No system is stopped!

But when try with 686 image my system stops on "Loading hardware modules", simple and quiet.

bye! 
:)

---

### Post by rbalfour on 2006-06-16
if 686 is working, you don't need 386

$ sudo aptitude purge linux-386
to  remove it.

---

