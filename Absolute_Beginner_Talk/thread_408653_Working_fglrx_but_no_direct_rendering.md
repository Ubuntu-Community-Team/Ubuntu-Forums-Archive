---
title: "Working fglrx but no direct rendering"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by vlees91 on 2007-04-13
after 5 hours of working on it, i dont have a missing xfree86-DRI any longer. But direct rendering is still not activated.
Composite is false and as driver i use fglrx.
My graphics card is a ati radeon x600

---

### Post by afternine on 2007-04-13
Make yourself a favour (I never thouhgt I'd make such a post but here it is): take your ATI card out and throw it out of the window. Get an Nvidia and leave peacefully with linux ever more. I had the same problems, I did so and never looked back. With ATI and linux you'll just have headaches. 

Bye

---

### Post by vlees91 on 2007-04-13
(i think so too, but thats not an option for me now....)
so please some serious answers

---

### Post by Mana82 on 2007-04-13
can u explain how u made that missing error message go away... i am new to linux but i think i remember seeing the command to check the drivers or somethign and i am pretty sure i got that same error message.  

also how do i check for direct rendering :)

i have had ubunut and beryl installed for the last 2 days now and i am loving it... the only problem is that videos esp 720p videos run choppy fullscreen, they run fine tho when i have them windowed.  could this missing error message be contributing to it?

i have tried to revert back to the old ati drivers that i had before i installed fxglr ones (which i did right before i installed beryl i think)....

thanks in advance for your help.

---

### Post by vlees91 on 2007-04-13
hmmmm
just restarted the system and now.... i have a missing XFree86-DRI again....
weird

and i did nothing. i only restarted the system (not "restart" but shutdown and then agaian the startbutton)

---

### Post by vlees91 on 2007-04-14
problem solved
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
the first Method (without compiling anything) works...
but there was only one thing i had to do: sudo apt-get install linux-restricted-modules-$(uname -r)
and then install the xorg-driver again

---

