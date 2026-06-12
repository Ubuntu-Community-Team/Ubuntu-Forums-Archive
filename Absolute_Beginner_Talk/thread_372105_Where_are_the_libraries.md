---
title: "Where are the libraries??"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-02-27
i have already done
apt-get install build-essential 

when i try to compile both with my programming environment (Scite) or the command line:
cc program.c

I get the error that 
studio.h no such file or directory

what gives?

---

### Post by Tomosaur on 2007-02-27
> **humbll said:**
> i have already done
apt-get install build-essential 

when i try to compile both with my programming environment (Scite) or the command line:
cc program.c

I get the error that 
studio.h no such file or directory

what gives?

It's not studio.h. it's stdio.h. It means 'Standard I/O'.

---

### Post by jordanmthomas on 2007-02-27
For the record, there are lots of c libraries / (headers is what they are actually called) in
```
/usr/include
```

---

### Post by humbll on 2007-02-27
Great, thank you for pointing out my error. But now I have a new problem:
After compiling it i get a file called whatever.o (from whatever.c) but i am unable to run it.

If i doubleclick it i am told there is no application to run it, and if i try running from command line i get "command not found" even though i am in the directory where it exists. I also tried:
make whatever.o 
but that did not help either.

 This is my first shot at C programming, in case you have not inferred that by my first error. Thank you for your patience and assistance.

---

### Post by jordanmthomas on 2007-02-27
Try compiling it like so:
```
gcc -o nameOfExecutable source.c
```
where nameOfExecutable is what you want to call it and source.c is your source code.
The -o switch specifies the name of the compiled program so you can find it easily.

then, try
```
./nameOfExecutable
```

I'm not sure why it compiled itself as a library.

---

### Post by humbll on 2007-02-27
> **jordanmthomas said:**
> Try compiling it like so:
```
gcc -o nameOfExecutable source.c
```
where nameOfExecutable is what you want to call it and source.c is your source code.
The -o switch specifies the name of the compiled program so you can find it easily.

then, try
```
./nameOfExecutable
```

I'm not sure why it compiled itself as a library.

Ok that works! what i did before was 
gcc whatever.c

and that was how i got 
whatever.o

this time i used your way and got 
whatever
with no extension.

So any source i compile in this manner must be executed by prefixing the name of the compiled executable with:
./
?why can i not just type the name of it, what is the point of the 
./
when i am sitting in the directory where the executable resides?
Anyway, thank you for the assistance, i really appreciate it.

---

### Post by jordanmthomas on 2007-02-27
for security reasons, . (your current directory) is not in your PATH variable.
Some dultz may try to put cp in a directory that actually deletes something...not likely though

```
gedit ~/.bashrc
```
put this in there:
PATH=$PATH:.

save and log into a new terminal
Now, . will be in your path and you can just type whatever instead of ./whatever

Personally, I don't mind putting ./ so this is not in my bashrc

---

