---
title: "C programming &amp; Ubuntu"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by witten on 2007-04-10
Hi everyone,

I just want to compile a relatively easy code written in C with gedit...

My code is :

#include <stdio.h>

int main()
{
printf("Hello cruel world!\n");
return(0);
}

I save this file under the name goodbye.c in a folder named prog in my home folder. Now when i come to compile this in the terminal window i write the following

cd /home/prog
ls
goodbye.c
gcc goodbye.c -o goodbye

but the following error happen 

goodbye.c : 1.19 : error : stdio.h : No such file or directory
goodbye.c : In function 'main' : 
goodbye.c : 5 : warning : incompatible implicit declaration of built-in function 'printf'

What i'm doing wrong ? The code is really simple and there are no errors....why the gcc don't compile my code ?

Thanks for your answers

Steeve - try to learn C

---

### Post by jordanmthomas on 2007-04-11
Try installing build-essential.  It's possible that installing gcc doesn't install any headers.

```
sudo aptitude install build-essential
```
Then try compiling.

---

### Post by witten on 2007-04-11
It works !

Thanks for the help !

Steeve - now can practice in C

---

### Post by witten on 2007-04-11
Just one more question....

Need i to install anything else to be up and running with all in C ? 

Thanks

Steeve

---

### Post by girishv on 2007-04-11
If you are doing simple c programming, then build-essential package is good enough. You have to install other dev packages if you are gonna do some graphical programming etc.

Girish

---

### Post by LaurelLynn on 2007-04-11
Dear witten,

Once you get comfortable with C, there are a lot of tools that can help with your programming.

If you like Integrated Development Environments there are several, Eclipse is one with visual studio like features. It has pluggins for many languages, as well as excellent tutorials.

For C#,  Mono and MonoDevelop give you command line and IDE based .NET programming.

Glade is my personal favorite, it´s farely easy to use.  It is a GUI builder for the Gtk toolkit. The beutiful thing about it is that it outputs the GUI in language independent XML. To use it you link to the library for your language and make a few calls to initialize it. You can even port it to Windows if you absolutely must.

Those are my favorites, but it´s hardly a complete list, such a list would be almost endless.

I hope I didn´t just completely confuse you.    (If so you can bookmark the page, and read it again in about three months)

---

