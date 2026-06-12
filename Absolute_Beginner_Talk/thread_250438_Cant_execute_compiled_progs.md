---
title: "Cant execute compiled progs"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by MoTeX on 2006-09-04
Ok, I've searched a lot for this on the net and I havent been able to find anything that fixed it.

After successfulluy compiling a .cc C++ simple program -even copy/pasted Hello World-, using 'g++ -o whatever -c filename.cc', I cant execute it (bash: ./Pe: Permission denied). And if I do a ls, it doesnt appear as an executable file. So.. what can I do. 

I remember that a couple of days ago, I did compile and run programs with no problem at all, and which is more strange is that I got the error once, closed all other apps and then tried again, and it worked! But now, it doesnt, even after reboot. Its getting really annoying and I have homework to do..:~(

I installed g++ (4.0) using synaptic, and after some time with the prob i tried doing a 'sudo apt-get install build-essential' and that isntalled some things, but didnt fix the problem.

please help me. Im new to linux and I dont know what to try...

thank you.

edit: forgot to mention, I used the ./P thing, so its not that.

---

### Post by amo-ej1 on 2006-09-04
> 
After successfulluy compiling a .cc C++ simple program -even copy/pasted Hello World-, using 'g++ -o whatever -c filename.cc', I cant execute it (bash: ./Pe: Permission denied). And if I do a ls, it doesnt appear as an executable file. So.. what can I do.


Ah, you pass the "-c" flag to g++, this will result g++ to only compile.

```

edb@lapedb:/tmp$ vi test.cpp
edb@lapedb:/tmp$ g++ -c  test.cpp
edb@lapedb:/tmp$ ls -hal test.o
-rw-r--r-- 1 edb edb 703 2006-09-04 09:51 test.o
edb@lapedb:/tmp$ g++ test.cpp
edb@lapedb:/tmp$ ls -hal a.out
-rwxr-xr-x 1 edb edb 6.7K 2006-09-04 09:52 a.out

```

So when you want to compile you specify the -c flag, when you want to compile AND to link you should not put the -c flag. Only the linker will produce the executable.

---

### Post by BitTorrentBuddha on 2006-09-04
```
sudo chmod 755 /path/to/program.cc
```
Replace /path/to/program.cc with the path to the program.

---

### Post by cocteau on 2006-09-04
To tell you the truth I don't have any experience using g++ from the command line. However, I've never had any problems running anything using Anjuta, so I suggest giving that a try.

---

### Post by MoTeX on 2006-09-04
Thank you so much!! it was the '-c' flag!!! I cant belive i spent so much time on this! 

Thank you all for your fast replies.

-A now happy ubuntu user

---

