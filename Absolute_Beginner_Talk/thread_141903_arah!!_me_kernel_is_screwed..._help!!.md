---
title: "arah!! me kernel is screwed... help!!"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by B3Nji on 2006-03-09
well at least me thinks its the kernel... 
I have been using Ubuntu  for just under a week, totally love it! I have no nasty windows on me laptop anymore :mrgreen: 
I saw a neat application called uPower. Bootup theme thing. in the instructions it said to uninstall the kernal after removeing the old boot theme program uSplash which comes with ubuntu. I did install the kernel again, but i dont think i installed the correct one . it comes up with a kernel error now and refuses to boot into the xwindows, but i do have terminal access.. oh and uPower runs! lolz. 

Was wondering if there is some command line thing i can do to reinstall me kernel etc. I was a pro when it came to windows but i really dont know much about linux. Want to get into the swing of things. 

my laptop is a Dell XPS 2 laptop, pentium m 2ghz, anymore info just ask. 

Cheers for your help guys un gals!

---

### Post by B3Nji on 2006-03-09
*bump*

I think its a program called synaptic that i should use to install the kernel, thought i dont know the commands to do so. I really dont want to reinstall ubuntu, it took me ages to install me graphics drivers and set up my wireless on this thing. 

thanks for your help

---

### Post by cilynx on 2006-03-09
Synaptic requires that you've got the graphical running.

What's the error that it throws?  Generally, kernel errors don't stop you from starting X.  The one exception is if you're using the commercial nVidia drivers which require a kernel module.

To answer your specific question about installing the stock kernel:
```

sudo apt-get install linux-686

```

---

