---
title: "Problem installing or using Fractint"
date: 2011-09-28
forum: Art &amp; Design
---

### Post by PayPaul on 2011-09-28
Found the program Fractint using Synaptic. It's listed as a manual install and is not to be found in applications. How do I start the program? Has anyone here ever used it?

---

### Post by 2F4U on 2011-09-28
Try to use whereis to locate the place where it is installed. You should then be able to start it out of a terminal.

---

### Post by PayPaul on 2011-09-28
> **2F4U said:**
> Try to use whereis to locate the place where it is installed. You should then be able to start it out of a terminal.

How or where do I enter that? Is it a command in terminal? After I find it how do I actually start the program?

I did find it but it's another one of those mostly text and enter random values fractal generators. It's not much of GUI interface at all. There's no menu to speak of and one has to go to a list of commands to even get it going. Another program for the trash. 

Thanks for your help.

---

### Post by 2F4U on 2011-09-28
Ok, here is a small example. I open a terminal and enter the following

```
cschwangler@T60:~$ whereis mousepad
mousepad: /usr/bin/mousepad /usr/share/man/man1/mousepad.1.gz
cschwangler@T60:~$ /usr/bin/mousepad

```

This starts mousepad, which is the default GUI editor in Xubuntu, but this works with most GUI programs.

---

### Post by PayPaul on 2011-10-11
Here's what I got when I entered that command. Thanks for showing me what should appear.

```
paulw@ubuntu:~$ whereis fractint
fractint:
paulw@ubuntu:~$ 
```

---

### Post by Dry Lips on 2011-10-12
Assuming you have correctly installed fractint, 
you would run it by typing
```
xfractint
```in the terminal window. Are you familiar with fractint 
from the good old DOS days? If not, you press "Esc" once you have 
launched the program in order to access the menu...

---

