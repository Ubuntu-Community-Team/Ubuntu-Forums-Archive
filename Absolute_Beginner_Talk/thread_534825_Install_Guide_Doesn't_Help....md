---
title: "Install Guide Doesn't Help..."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Wudugast on 2007-08-25
I want to install a program I downloaded called NEStopia. I downloaded the two things the website told me to download and unzipped them in the same folder on my desktop. Now I don't know what to do. The directions say:

Unzip the core source, then unzip the Linux overlay source over it. ( I did that) Change to the directory you unzipped everything in and type “make." (This doesn't work. When I type "make" in the nautilus, it only searches for "make" and finds a thing called a make file.)

 If you have problems, make sure you have these packages:

(I downloaded the packages from the Ubuntu universe)

- General development (also called “GCC” and “G++”) plus their dependancies
- GTK+ 2.4 or later and the development packages
- The ALSA library and it’s development packages
- SDL 1.2.11 and it’s development package

What do I need to do to install my program?

---

### Post by Billy_McBong on 2007-08-25
[COLOR="Blue"]you are supposed to type "make" in the terminal ( applications > accessories > terminal )[/COLOR]

---

### Post by GMachine_24 on 2007-08-25
You realize you are compiling this program from source code, right?

gm

---

### Post by Wudugast on 2007-08-25
Thanks.

I don't know how to use the terminal, though. It says it's supposed to be in the directory, but all I get is:

root@name:/home/name#

How do I make it go to the directory I want? Just typing in the address doesn't work.

---

### Post by Wudugast on 2007-08-25
I really don't know what I'm doing with this. All I gather is that I'm supposed to use the terminal to make some kind of executable file or a package that Ubuntu will install... and that I have to make it out of all of these files I downloaded.

Someone else told me to get a program called Kconfigure to install this, but I don't know what to do with it. I've messed around with it a bit and it doesn't recognize any of the files as something it can use.

This is a pain. Why can't programs that aren't on the add/remove list just work when you download them, like all the others do? What am I supposed to do with all this stuff?

---

### Post by GMachine_24 on 2007-08-25
> **Wudugast said:**
> Thanks.

I don't know how to use the terminal, though. It says it's supposed to be in the directory, but all I get is:

root@name:/home/name#

How do I make it go to the directory I want? Just typing in the address doesn't work.

You should research some basic Linux commands. The command you want, I believe, is 'move' as in:

sudo mv /locationofyourfile/filenameyouwanttomove /pathtofolderyouwantfilein

as a real-world example

sudo mv /home/username/Desktop/Nestopia /usr/local/Nestopia

assuming /usr/local/Nestopia is where you want these files to go. To create the Nestopia directory you

cd to /usr/local and then

sudo mkdir Nestopia

and to make the directory writable

sudo chmod 777 /Nestopia

You should also read up on compiling a program from source code. What you're attempting is fairly advanced.



hope this helps

gm

---

### Post by JimmyBEng on 2007-08-25
[QUOTE=Wudugast]This is a pain. Why can't programs that aren't on the add/remove list just work when you download them, like all the others do?[/QUOTE]

because the person who put together the program you want, only provides source code. So take up ease of install with them.  However, compiling from source is no big deal.

Here is the first tutorial I was able to find:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code")

I'll look around for a second, and maybe an intro to the command line, just give me a chance to search

---

### Post by JimmyBEng on 2007-08-25
ok, as promised.

lots of information on the terminal is here:

[http://ubuntuforums.org/showthread.php?t=171507]("http://ubuntuforums.org/showthread.php?t=171507")

another page on installing is here:

[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

Hope this helps

---

### Post by Wudugast on 2007-08-27
Thanks a lot, everybody! :)

This should help. If I have more questions, I'll post them in a few days. I don't have time to get around to playing with this for now, but we'll see.

---

### Post by Wudugast on 2007-08-27
okay, here's what's going on now.

I've become familiar enough with the command line to change directories and try to compile the source, but I get a lot of error messages... way too many to even try to copy and paste them here.

I think I am missing important development files, but the names don't match up on synaptic package manager. I am having the most trouble finding GTK+ 2.4, ALSA and SDL 1.2.11. The only one I could find was GCC.

Any tips on how to find these packages?

---

