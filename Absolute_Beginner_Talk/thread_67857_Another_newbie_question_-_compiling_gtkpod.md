---
title: "Another newbie question - compiling gtkpod"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by raincloudboy0 on 2005-09-21
I was trying to install gtkpod, the program that lets you work with your iPod from Linux, and I got as far as compiling. I did the ./compile command in the terminal and, after a lot of text, got 

configure: error: no acceptable C compiler found in $PATH

as the end result. The directory where the files to compile are located is tmp, because I didn't know where better to put it.

What should I do to make this work? Thank you.

---

### Post by katu on 2005-09-21
looks like you're missing the compiler. 
```
sudo apt-get install build-essential
``` 
should download the needed packages and solve the problem. 
The compile should work after this.
cheers,
Katu
[COLOR=Red]
EDIT: corrected typo in the command.[/COLOR]

---

### Post by raincloudboy0 on 2005-09-21
Thanks a bunch.

---

### Post by raincloudboy0 on 2005-09-21
Sorry to bother you again, but I did that and got the message

E: Invalid operation build-essential

---

### Post by mlomker on 2005-09-21
That was a typo.  Should be:

```

sudo apt-get install build-essential

```

---

### Post by raincloudboy0 on 2005-09-21
You certainly got me farther than I had before, but I'm beginning to think I really am just inept. I did what you said, it worked, I did ./configure again and there was a lot of text again, and this came up.

configure: error: *** Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
See `config.log' for more details.

I know I'm asking a lot of questions. I really appreciate these responses.

---

### Post by mlomker on 2005-09-21
> I know I'm asking a lot of questions. I really appreciate these responses.

This is normal stuff when you compile your first few programs.  I'm not going to tell you the answer this time, but I'll tell you how to find the answer.

Go into Synaptic and search on that error message **gtk+**.  Find the package with a similar name but ending in **-dev** or **-devel**.  That's what it is looking for.  Sometimes you have to download a few before you get the right one.

---

### Post by raincloudboy0 on 2005-09-22
Well, I've got to go away this weekend so I'll give all this stuff a try when I get back. :)

---

### Post by katu on 2005-09-22
I'm really very sorry for the typo up there. Should have triple checked...  
:oops:

---

