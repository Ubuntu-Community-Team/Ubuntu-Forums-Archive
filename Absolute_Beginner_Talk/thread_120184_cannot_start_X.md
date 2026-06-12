---
title: "cannot start X"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by mesocool on 2006-01-21
I tried this tutorial [http://doc.gwos.org/index.php/Transparent_Terminals](http://doc.gwos.org/index.php/Transparent_Terminals) and set the script to order 0 in Startup Programs at step 6, then I cannot start X any more.. 

Anyone knows how to stop or delete the script set up in the startup program?

Thanks..

---

### Post by amohanty on 2006-01-21
In grub, select the recovery console
Enter your password
do the following:
> cd ~/your_username
vi .gnome2/session-manual

then for every line that that starts with a **0,**
type:
> dd
One **dd** will delete one line.

Then for the line that starts with **num_clients** change the number at the end to be one less than it is right now. To do so do the following _in order_:
0. Move the cursor using arrow keys to the start of the number - for eg if the number is 1 put the block cursor right on top of 1 - if it is 21 put it right on top of 2
1. Press **x** as many times as needed to remove the number - it will be the number of apps you have added to the startup list.
2. Press **a** and then type in the number - 1
3. Press ESC

To save press the following keys _in order_
> ESC
:
wq
ENTER

and yes thats a colon
HTH

---

