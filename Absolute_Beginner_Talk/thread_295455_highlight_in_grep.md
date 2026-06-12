---
title: "highlight in grep"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-08
Hi there,
I'm learning grep and I was wondering if there is a way to highlight or color  the matched word.

:confused: 

Thanks

---

### Post by Jussi Kukkonen on 2006-11-08
```
grep --colour=auto
```

There's also a bash feature you might like: Add
```
export GREP_OPTIONS="--colour=auto"
```
into your .bashrc to have that on always.

---

### Post by helphope on 2006-11-08
Thanks for answering, but I realize that I'm chewing more than I can bite.

> **Jussi Kukkonen said:**
> ```
grep --colour=auto
```

You mean I have to insert the previous string in the terminal?

> **Jussi Kukkonen said:**
>  There's also a bash feature you might like: Add
```
export GREP_OPTIONS="--colour=auto"
```
into your .bashrc to have that on always.

To me this sound like ... :confused: :confused: 

Thanks

---

### Post by Jussi Kukkonen on 2006-11-08
Cool, I'll take it a little slower:
Let's say I'm searching for the word "usb" in the file /var/log messages:
```
grep -C3 usb /var/log/messages
```
Now, that works, but it's not easy to see the searched word, especially when I used "-C3" to see three lines of context for all occurrences. Let's put on the highlight:
```
grep -C3 --colour=auto usb /var/log/messages
```
Ok, that does it: all occurrences of "usb" are now red. 


Now the second tip: If I know I always want higlighting on, I can make grep default to using it (so I don't have to specify it with "--colour=auto" every time I use the command). There's a file in your home dir called ".bashrc". You can edit it with e.g. 
```
gedit ~/.bashrc
```
Add the export-line I mentioned to the end of the file. Now every new terminal you open should have colour coding on by default when you use grep .

---

### Post by helphope on 2006-11-08
My compliments. You could write it better
Very clear and very helpful

Thanks a lot

---

### Post by helphope on 2006-11-08
Sorry, I meant "you couldn't write it better" :-#

---

