---
title: "[SOLVED] Script to find out all specs"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-30
Okay is there some kind of command script or something that can tell me all the hardware specs that are on that one computer.

---

### Post by emarkd on 2008-01-30
How about:

```
lshw
```

---

### Post by fedex1993 on 2008-01-30
ty that worked perfect i wish there was a shorter command but it doesnt bother me at all

---

### Post by jordanmthomas on 2008-01-30
four letters is too long?  :lolflag:
I think I know what you meant.  How about
```
sudo lshw -short
```

---

### Post by Rocket2DMn on 2008-01-30
You can also do
```
sudo lshw -class *something*
``` Where *something* can be network, processor, memory, etc...

---

### Post by emarkd on 2008-01-30
This all brings up a good learning opportunity for any new user who happens upon this thread.  You can always learn more about any command given to you on this forum by going to the terminal and running

```
man 'command'  
```

to read the manual page for that command.  If there's nothing there, some software goes the other route, which is to include an info page.  You can read info pages by running

```
info 'command'  
```

These two commands can help you learn much as people expose you to new commands.

---

### Post by jordanmthomas on 2008-01-30
Also, the --help switch is usually helpful
```
lshw --help
``` for example

---

### Post by p_quarles on 2008-01-30
My favorite:
```
sudo lshw -html > ~/hardware.html
```
Now you can open the "hardware.html" file in your web browser and get a nicely formatted list of your specs.

---

### Post by Dr Small on 2008-01-30
> **p_quarles said:**
> My favorite:
```
sudo lshw -html > ~/hardware.html
```
Now you can open the "hardware.html" file in your web browser and get a nicely formatted list of your specs.
Yeah, I was going to post that :p
[http://php.8ez.com/drsmall/blog/?p=178](http://php.8ez.com/drsmall/blog/?p=178)

Dr Small

---

### Post by fedex1993 on 2008-01-30
ty very much everyone and thanks for helping

---

### Post by seventhc on 2008-01-30
> **p_quarles said:**
> My favorite:
```
sudo lshw -html > ~/hardware.html
```Now you can open the "hardware.html" file in your web browser and get a nicely formatted list of your specs.
wow, I like that one a lot...does this work with other commands too??

---

### Post by Rocket2DMn on 2008-01-30
You can't really do the html thing with other commands, but you can output to files, like
```
sudo fdisk -l > ~/fdisk_output.txt
```

---

### Post by seventhc on 2008-01-30
nice, Thanks :)

---

