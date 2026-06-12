---
title: "[SOLVED] Please help me! I'm BRAND NEW to Ubuntu! Resolution Problem!!"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by josh995 on 2008-04-14
Ok, well, I just installed ubunto via Wubi...

Well, I have to say... I LOVE it.

Except... The screen resolution... I have a Samsung 22 inch LCD monitor that's capable of 1680x1050, but ubuntu is only letting me choose either 640x480 or 800x600...

I'm using the beta version of 8.04 so I really hope someone can help me!

Please, PLEASE don't use all these technical terms, because, like I said, I'm new to Ubuntu (been using for... 15 minutes...), so I really don't know all of the stuff!

Where do I go, what do I click on, what do I type, etc...

I really, really would appreciate it if anyone helped me! Thanks!!

By the way, I'm 'dual booting' with Windows Vista and Ubunto 8.04, but like I said, I installed ubuntu using Wubi.

thanks again!

---

### Post by Michael.Godawski on 2008-04-14
Welcome.

Did you have installed the drivers for your graphic card? What is your graphic card by the way?
To give us more information go to Applications > Accessories > Terminal
There type these commands and enter your login password when asked:

```
sudo lshw
```

Copy and paste the output here.

You can also check if there are drivers inactive when you go to System > Administration > Restricted Drivers Manger. Check the box next to the inactive device.

---

### Post by josh995 on 2008-04-14
**Edited**

---

### Post by PmDematagoda on 2008-04-14
I believe this is what we are looking for:-
```
*-display UNCLAIMED
description: VGA compatible controller
product: GeForce 6100 nForce 430
vendor: nVidia Corporation
physical id: d
bus info: pci@0000:00:0d.0
version: a2
width: 64 bits
clock: 66MHz
capabilities: pm msi vga_controller bus_master cap_list
configuration: latency=0
```

Now as Michael.Godawski said, did you install the Nvidia driver?

---

### Post by Michael.Godawski on 2008-04-14
Sorry it is morning here and my brain is still sleeping.

The other command:
```
lspci
```

But you will become a little more comfortable with the terminal I hope.
The commands will list all hardware and pci devices of your machine so it is easier to help.
[B]
edit[/B]: thx PmDematagoda, must really wake up first.

---

### Post by josh995 on 2008-04-14
Wow. WOOOOWWW! I did the driver update and it said something about my graphics card so I updated it and it worked! My screen is now crystal clear!

Wow.

This is amazing. I think I've officially been converted to an Ubuntu user.

I seriously can't thank you enough. Thank you so much. Really, thank you!!!!!!!! :) :) :)

Edit: However, I do have a question, the font is really, really tiny. It's really clear, but really tiny. What can I do to fix that?

Thanks again, to both of you!

Edit again: Oh yeah, I mean the font in firefox is tiny.

---

### Post by Michael.Godawski on 2008-04-14
Hey you make my day.
:)

You can help by marking this thread as solved. You can do that by using the Thread Tools in the upper right corner of the thread.

---

### Post by seshomaru samma on 2008-04-14
fonts?
system>preferences>appearance>fonts

in firefox-
edit>preferences>content>fonts&colours

---

### Post by hyper_ch on 2008-04-14
> **josh995 said:**
> This is amazing. I think I've officially been converted to an Ubuntu user.

More problems will arise once you start using it more intensly... but you've found out where to get help from ;)

---

