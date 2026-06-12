---
title: "Compiz Fusion on mac G5"
date: 2010-04-30
forum: Apple Hardware Users
---

### Post by lexley on 2010-04-30
I'm new on this forum and i have a question.

So. I Installed Ubuntu 9.10 PPC from the LiveCD on my Mac G5.
There is 4GB of ram in it. 2 CPU's and A Nvidia FX5200.

Now i want to install compiz fusion. I knew that Nvidia doesn't bring out PPC linux drivers. So what do i need to do to get compiz-fusion working?

Problem 2 is I can't find my Xorg.conf

so i hope someone can help me :)

---

### Post by conal on 2010-04-30
As far as I know the 'nv' driver that comes as standard with 9.10 will not be sufficient for Compiz as it has no 3D capabilities, you can switch to the 'nouveau' driver (you'll find instructions elsewhere in the forum) which makes more use of the card but still won't give you the 3D stuff you need for Compiz. 

xorg.conf doesn't exist by default in 9.10 you have to generate one yourself - google 'create xorg.conf ubuntu 9.10' or something for instructions.

What exactly are looking for from compiz? If it's simple effects such as shadows under windows then enabling composting in metacity does the job, with your specs it shouldn't trouble the system at all. Instructions are here: [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

I am hoping that when ubuntu ships with the Nouveau 3D stuff - maybe 10.10 or 11.4, then maybe better desktop effects will be possible on the powerpc - we'll have to wait and see.  

cheers

Conal

---

