---
title: "Using wine to install Yeah Write Word Processor"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by zippytex on 2007-03-29
If you go to yeahwrite dot com, you will find a great little word processor, called Yeah Write.  It is amazing.  If you click on the fan mail list and scroll down, you will see a listing by someone using Wine and installing and using it under Linux.  Yeah Write is a Windows Program.   I updated my Wine and put the Yeah Write executable on the destop and double clicked it, but nothing.  I found the wine under usr and bin, but how do I get wine to accept the Yeah Write.  This word processor is great.  It is graphic and the opening screen actually show a filing cabinet with drawers, you label the drawers, like My Writing, and then click on the drawer and the file folders appear.  You label them, say one is called short stories.  You click on short stories and there they all are lined up.  It is great!  I would be willing to pay someone to help me run this under Linux.  Thanks for listening.:confused:

---

### Post by %hMa@?b&lt;C on 2007-03-29
> **zippytex said:**
> If you go to yeahwrite dot com, you will find a great little word processor, called Yeah Write.  It is amazing.  If you click on the fan mail list and scroll down, you will see a listing by someone using Wine and installing and using it under Linux.  Yeah Write is a Windows Program.   I updated my Wine and put the Yeah Write executable on the destop and double clicked it, but nothing.  I found the wine under usr and bin, but how do I get wine to accept the Yeah Write.  This word processor is great.  It is graphic and the opening screen actually show a filing cabinet with drawers, you label the drawers, like My Writing, and then click on the drawer and the file folders appear.  You label them, say one is called short stories.  You click on short stories and there they all are lined up.  It is great!  I would be willing to pay someone to help me run this under Linux.  Thanks for listening.:confused:

nobody wants your money :lolflag: just go to terminal and try typing
wine /path/to/yawrite.exe

---

### Post by ceeg on 2007-03-29
Download Yeah Write off of their website and save it to your Home directory. 

Open a Terminal.

In Gnome, you do this by Applications -> Accessories -> Terminal.
Make sure the file is there.
```

ls ~| grep yw

```

You should see yw32.exe

Type this: 
```

wine yw32.exe

```

See if that works.

---

### Post by zippytex on 2007-03-29
Thanks very much.  I was able to click the install, but it came back with this error message.

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b


I was able to install some of my favorite programs.

Also, I did not mean to offend anyone by offering money for assistance.  I guess I've been with windows too long.  

Thanks.

---

### Post by ceeg on 2007-03-30
> **zippytex said:**
> Thanks very much.  I was able to click the install, but it came back with this error message.

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b


I was able to install some of my favorite programs.

Also, I did not mean to offend anyone by offering money for assistance.  I guess I've been with windows too long.  

Thanks.

Does the program work despite those warnings? I'm assuming it does because those are warnings and not errors.

Congrats :)

And no-one is offended, we know how frustrating it can be at times.

---

