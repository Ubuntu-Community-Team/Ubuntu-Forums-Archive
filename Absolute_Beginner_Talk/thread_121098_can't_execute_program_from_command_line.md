---
title: "can't execute program from command line"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by msharris35 on 2006-01-24
I have very recently loaded Ubuntu onto mu computer so I am new to linux and ubuntu. I am trying to use it to build a program and then execute the program from command line. 

I have installed the build essentials files.

I have built the program using make and makefile with no errors. 
But when I try to run the program "P0" at the command line, I  only get the line:

bash: P0: command not found

which doesn't execute the program. I have run this program on another linux system and it works fine, but here I get nothing.
I am assuming I don't have soemhting setup properly or I am not doing something properly. 

Can someone please tell me might be wrong?

---

### Post by linuxden on 2006-01-24
```
./ make install
``` would be the natural command after

```
./configure
```
```
./make
```

---

### Post by msharris35 on 2006-01-24
I am really new to this linux and I don't understand the ./make or ./configure?

---

### Post by linuxden on 2006-01-24
check out section 7.2 that is where it talks about compiling...

[http://www.faqs.org/contrib/yal/page7faq.htm](http://www.faqs.org/contrib/yal/page7faq.htm)

google is your best friend learn to love it... ;o)

---

### Post by Mustard on 2006-01-24
[QUOTE=msharris35]I am really new to this linux and I don't understand the ./make or ./configure?[/QUOTE]

No..you wouldn't be alone there. :)

I have a feeling someone wasn't thinking things through when they posted. ;)

Its make and make install.  Not ./make and ./make install.  ./configure is just fine though.

---

### Post by msharris35 on 2006-01-24
I tried the ./configure command but when I receive :

./configure: no such file or directory

It doesn't seem to reconize this one...    any suggestions?

---

### Post by linuxden on 2006-01-24
[QUOTE=Mustard]No..you wouldn't be alone there. :)

I have a feeling someone wasn't thinking things through when they posted. ;)

Its make and make install.  Not ./make and ./make install.  ./configure is just fine though.[/QUOTE]

LMAO!!

My laziness to retype [ CODE] [ /CODE] has been shown...lmao no more copying and pasting for me... ;o)

---

### Post by Perfect Storm on 2006-01-24
make sure you're in the right directory/folder when doing it.

---

### Post by msharris35 on 2006-01-24
I am located in the current directory with the files I am compiling along with  makefile. Which directory should I be located in when running the ./configure command prior to the make and then make install?  

From what have read I need the ./configure to create the make file. I have a makefile, would this overwrite it or add to it?   

When built the program previously on a different computer already set up on linux, I only need the "make" create the application, is ubuntu differnt?

---

### Post by steve.horsley on 2006-01-24
I'm not familiar with making executables, but since you say you thing it made OK, here are a couple of really simple things to check:

Is the executable marked as executable? Right-click and select properties and make sure it is executable by the owner. From command line, **ls -l** and make sure the line starts with **-rwx**. If not, set the executable flag with **chmod +x filename**. 

Unlike windows, the current directory is not in your path. Instead of just giving the filename, you must quote the directory too. Hence you type ./configure instead of just configure. So you need to type ./P0, not just P0.

HTH

---

### Post by msharris35 on 2006-01-24
I checked and verified the file "P0" is marked as an executable.  

when i tried the ./P0 it gave me an error: 

error while loading shared libraries: libstdc++.so.5:cannot open shared object file: no such file or directory

I loaded a few more of the libraries and it now seems to work...

thanks

---

### Post by Mustard on 2006-01-24
Well done. :)

---

