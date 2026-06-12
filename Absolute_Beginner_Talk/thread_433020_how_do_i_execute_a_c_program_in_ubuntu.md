---
title: "how do i execute a c program in ubuntu"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by idcmurali on 2007-05-04
how do i execute a c program in ubuntu

I tried cc hello.c -o env.out 

it did nt work any idea

---

### Post by viciouslime on 2007-05-04
Don't you have to compile it first?

---

### Post by Balazs_noob on 2007-05-04
Hi
you have to compile it with the GCC compiler
go to the directory where the stuff is

then:

gcc -osource source.c
source is the name of the source :)
and you can run it with ./source

if you have a error , like it can't find stdio.h
you have to download build - essentials from Synaptic manager

hope this helped, Balazs

---

### Post by idcmurali on 2007-05-04
Hey thnks for replying ..but how do i get the GCC compliler ..i was actually documenting in a txt file & then saved that to .c exntesion & then tried running on the terminal ...is that the right way ?
please help me as i am damm new to linux

---

### Post by compmodder26 on 2007-05-04
Ubuntu doesn't ship with compilers by default.  Go to synaptic and install "build-essential", or if you are doing it by the command line: "sudo apt-get install build-essential".

---

### Post by idcmurali on 2007-05-04
Hey Thnks for that i have just started installing the build -essential 
one more question ...for the out do i need to type in GCC source.c -o ???

---

### Post by idcmurali on 2007-05-05
I AM still facing difficulties after installing the packages from teh command prompt 
I have a C program named Doc1.c 
when i type in gcc -o doc2 doc1.c 

i dont get the output ..can anyone tell me how do i get the output pls

---

### Post by Najand on 2007-05-05
Try and see if you get any output without the -o option:
```

gcc doc1.c

```
and try to run it using:
```

./a.out

```
If it didn't work then you have an error during compiling your program.

---

### Post by idcmurali on 2007-05-05
murali@murali-desktop:~$ gcc doc.c
gcc: doc.c: No such file or directory
gcc: no input files

Nope that didnt work 
This is the message i get

---

### Post by Najand on 2007-05-05
Are you compiling the file from the same directory? You have to change directory (cd) to the directory the c program is located at.

---

### Post by Outrunner on 2007-05-05
You said it's named Doc1.c not doc1.c. There's a difference, you know.

---

### Post by idcmurali on 2007-05-05
I have opened a blank document & compiled it & saved it with .c extension 
thats how i made doc.c ...is that the right way or hw do i do it ..i appreciate ur help sir

---

### Post by Najand on 2007-05-05
Hmm, linux is CASE SENSETIVE.... You must not confuse the capital letters with small ones.

---

### Post by Najand on 2007-05-05
When saving a document select the place (its PATH) you want to save and when compiling use that PATH befroe the name of that file or cd to that PATH before compiling.

---

### Post by idcmurali on 2007-05-05
Kewl ..i got that ..i tried with the same case as i have saved it to ..it is doc.c 
i have opened the terminal ....typed in gcc doc.c
gcc: doc.c: No such file or directory
gcc: no input files

this is what i have done ...is that gud

---

### Post by Najand on 2007-05-05
try to save it in your home directory.
Then open a terminal and then comile it like:
```

gcc ~/doc.c

```

---

### Post by idcmurali on 2007-05-05
When saving a document select the place (its PATH) you want to save and when compiling use that PATH befroe the name of that file or cd to that PATH before compiling.

Thnks for replying 
Didnt get yu ..Najand ..can yu explaing me clearly . as i am very much new to ubuntu ..i am so  dumb on this ...Like can yu take my example & help me ..i have the file doc.c on my desktop 
how do i execute it on the terminal window ..

---

### Post by idcmurali on 2007-05-05
when i tried i got thss

gcc ~/doc.c
gcc: /home/murali/doc.c: No such file or directory
gcc: no input files

---

### Post by Najand on 2007-05-05
If you have it on your desktop then you have to change dirctory to your desktop; then comiling it:
```

cd ~/Desktop
gcc doc.c -o doc

```
Then you can run it there too:
```

./doc

```

---

