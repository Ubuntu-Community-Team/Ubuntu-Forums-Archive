---
title: "startx"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by aleek on 2007-10-23
Hi,

Would very much appreciate help. Have tried to google and search ubuntu forums to solve my problem, but without luck.

I have followed this guide step by step so far:
[http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html](http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html)

First of all I am not sure what input box means:

"

Type the following code in the input box:

startx

"

My guess is that it is in the console I should type this....?

If I type startx as root in the console then get Fatal server error and unnable to connect to x server for example of all the errors.

Any advice?

thanks

---

### Post by Daveth on 2007-10-23
yes, they do mean a terminal for that part of the tutorial. The config stuff is using Kate, a text editor, to make new entries. You can cut and past some/ all of those commands, which will stop you making silly typo errors. 

I must admit not being able to make head nor tail of your startx root bit of the post!

Good luck with that one!

---

### Post by FXEF on 2007-10-23
> **aleek said:**
> Hi,

Would very much appreciate help. Have tried to google and search ubuntu forums to solve my problem, but without luck.

I have followed this guide step by step so far:
[http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html](http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html)

First of all I am not sure what input box means:

"

Type the following code in the input box:

startx
11)
"

My guess is that it is in the console I should type this....?

If I type startx as root in the console then get Fatal server error and unnable to connect to x server for example of all the errors.

Any advice?

thanks

The link you listed is for installing Ubuntu on a Playstation 3. 

Is that what you have done?

If you are trying to use startx with a normal Ubuntu install on a PC, startx will return errors because X is auto started in the Ubuntu boot process. X is already started.

Linux loads in this order:
1) Linux kernel
2) X server
3) Window manager / desktop environment

FXEF

---

### Post by aleek on 2007-10-24
Yes, I´m installing kubuntu om my ps3. 

Thanks a lot for both of your replies, I will probably go back to feisty fawn since I can´t get anything to work right now.... 

I´m gonna try to read as much as possible regarding ubuntu and try again later.

thanks again,

al

---

