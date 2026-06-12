---
title: "I need esc: at starup"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-10-10
Hello.To get my computer to start I have to press Esc: at startup. I then get a list of kernels.
kernel 2.6.15-27-k7
kernel 2.6.15-27-k7 recovery
kernel 2.6.15-27-386
and then 6 more options. Using arrow-keys I can hi-light 2.6.15-27-386; then press <enter> and it continues the startup.
I'd like someone to tell me how to alter the sequence so that the 386 is first in line, or perhaps how to get rid of the first 2 options.
Any help will be very much appreciated...............thanks Sarum

---

### Post by aysiu on 2006-10-10
Paste this command in [the terminal:](http://www.psychocats.net/ubuntu/terminal) ```
sudo nano -B /boot/grub/menu.lst
``` Find the line that says ```
default 0
``` (which means the default is the first entry) and change it to ```
default 2
``` (which means the default will be the third entry.

There's also another option called ```
hidden menu
``` If you comment out that line ```
#hidden menu
``` then you won't have to press Escape to see the menu.

Finally, save (Control-X, Y, Enter)

---

### Post by sarum on 2006-10-10
Thanks aysiu for your help - and all within an hour of asking.
Cheers .............Sarum

---

