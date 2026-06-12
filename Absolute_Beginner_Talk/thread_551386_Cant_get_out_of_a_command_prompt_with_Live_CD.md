---
title: "Cant get out of a command prompt with Live CD"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by CAD-MAN on 2007-09-15
Hi

Ive just received a laptop (Dell Inspiron 1520), and Im trying to install Ubuntu on it alongside Vista.

I was told to do the following, because apparently there are some problems getting the Live CD to boot properly:

> When you first pop in the UBUNTU Feisty CD you must do the following:

At the LiveCD initial boot screen do the following:

Move The Cursor Down To Safe Video Mode
Select F6 for more options
Add the following option to the beginning of the options list:
break=top (and put a space after it)
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

This didnt work, and Im given the following error: /bin/sh: piix: not found
And now Im stuck in this command promt.

Can someone please tell me how to get out of this command prompt? I don't mind if I cant install Ubuntu yet really (although, if someone could give me tips on getting it to work, I'd be most thankful).

Thanks...

---

### Post by mikeyphi on 2007-09-15
Type exit at the prompt and the terminal should close.

---

### Post by lisati on 2007-09-15
Clicking on the "close window" icon (the little X) should work as well.

---

### Post by CAD-MAN on 2007-09-15
Thank you both very much!!! Theres nothing worse than having a brand new laptop that you cant use!

I'm downloading the alternate Ubuntu CD with the text installer, hopefully that will work more smoothly.

---

