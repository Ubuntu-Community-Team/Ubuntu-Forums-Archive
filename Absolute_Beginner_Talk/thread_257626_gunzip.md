---
title: "gunzip"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-09-14
Gunzip doesn't want to decompress scanModem.gz. It says it's a shell script and should be changed to a different format or something. What should I do?

---

### Post by kidders on 2006-09-14
Hi there,

Are you sure your file is a gzipped archive? (Just because its name happens to end in ".gz" means very little!)

---

### Post by blendmaster on 2006-09-14
Well, I'm pretty sure. The multiple sites I've used to find a modem driver for Linux tell me how to run this file (Linmodems.org is one site) using the terminal and everything. They say to do this:

```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

but gunzip tells me that the file is a shell script and needs to be renamed or something (at least, I think that's what it said). Is there any way to decompress it?

---

### Post by mitch.c on 2006-09-14
> **blendmaster said:**
> but gunzip tells me that the file is a shell script and needs to be renamed or something (at least, I think that's what it said). Is there any way to decompress it?
How about running file against it to make sure it really is gzipped:
```
file scanModem.gz
```
If it's really a gzipped file, it should tell you.

It might also be a good idea to post the exact message gunzip gives you.

---

### Post by blendmaster on 2006-09-14
> If it's really a gzipped file, it should tell you.

It might also be a good idea to post the exact message gunzip gives you.

Okay, I'll try this. The reason why I don't have the exact message is because I'm switching from Ubuntu and XP (I'm using XP to connect right now, in fact, I need scanModem to even connect on Ubuntu) and it's really annoying to switch OS's all the time. Thanks, time to try it out!

---

### Post by blendmaster on 2006-09-14
Here's what I'm getting:

----------------------------------------
What it says when I type:

```
file scanModem.gz 
```    

*Bourne shell script text executable*

----------------------------------------

What it says when I type:

```
gunzip scanModem.gz
```

[i]~/Desktop$ gunzip scanModem.gz

gunzip: scanModem.gz: not in gzip format[/i]

----------------------------------------

What it says when I double click the file icon on my desktop:

[i]The filename "scanModem indicates that this file is of type "gzip archive". The contents of this file indicate that it is a "shell script". If you open this file, the file might present a security risk to your system.

"...". To open the file, rename the file to the correct extension for "shell script", then open the file normally. "...".[/i]

What do I do to decompress it? I can open it with a text editor, but all I'm getting is code (not what the actual output should be). Once again, I appreciate all of your help!

---

### Post by mitch.c on 2006-09-14
> **blendmaster said:**
> Here's what I'm getting:

----------------------------------------
What it says when I type:

```
file scanModem.gz 
```    

*Bourne shell script text executable*

----------------------------------------

What it says when I type:

```
gunzip scanModem.gz
```

[i]~/Desktop$ gunzip scanModem.gz

gunzip: scanModem.gz: not in gzip format[/i]

----------------------------------------

What it says when I double click the file icon on my desktop:

[i]The filename "scanModem indicates that this file is of type "gzip archive". The contents of this file indicate that it is a "shell script". If you open this file, the file might present a security risk to your system.

"...". To open the file, rename the file to the correct extension for "shell script", then open the file normally. "...".[/i]

What do I do to decompress it? I can open it with a text editor, but all I'm getting is code (not what the actual output should be). Once again, I apreciate all of your help!

So there you go. It's not gzipped, it's a shell script. Do this:
```
mv scanModem.gz scanModem.sh
chmod +x scanModem.sh
./scanModem.sh
```

---

### Post by blendmaster on 2006-09-14
Another thing I don't understand is why it's even doing this when all the other sites don't explain any problems like this. Could it be a file error? If it is a file error, then why is the source code still there?

---

### Post by mitch.c on 2006-09-14
> **blendmaster said:**
> Could it be a file error? If it is a file error, then why is the source code still there?
It's not a file error. Someone, for some reason added the .gz extension. The source code you see is exactly what a shell script is... you run this, the commands in the file are executed, and this presumably sets up your modem.

---

### Post by blendmaster on 2006-09-14
Thank you mitch.c! You've been very helpful to someone completely new to Ubuntu! I'll try this and see what I get.

---

### Post by blendmaster on 2006-09-14
It worked! Thank you so much! I love Ubuntu!

---

