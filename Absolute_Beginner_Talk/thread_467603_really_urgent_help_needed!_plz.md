---
title: "really urgent help needed! plz"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-06-07
I posted this previously but the thread quickly died so I am forced to post again.
I have an acecad flair 2 tablet and it doesnt work properly in feisty. 
I can move the cursor arround but the placement off it is off and pressure sensitivity does not work.

As far as I could conclude from my own little homework, it is controlled by xserver-xorg-input-acecad. I installed that in synaptic package manager however it produces the result above. I found a newer version somewhere on the web but when I try to install it says dependency not satisfiable: libc6

I also found a driver at [http://acecad.sourceforge.net](http://acecad.sourceforge.net)
but apparently it does not have a ready installer and I need to compile it myself (which I don't know how)

Can someone please help me? This is very urgent.

---

### Post by dbbolton on 2007-06-07
> **Gmbrdilos said:**
> I posted this previously but the thread quickly died so I am forced to post again.
I have an acecad flair 2 tablet and it doesnt work properly in feisty. 
I can move the cursor arround but the placement off it is off and pressure sensitivity does not work.

As far as I could conclude from my own little homework, it is controlled by xserver-xorg-input-acecad. I installed that in synaptic package manager however it produces the result above. I found a newer version somewhere on the web but when I try to install it says dependency not satisfiable: libc6

I also found a driver at [http://acecad.sourceforge.net](http://acecad.sourceforge.net)
but apparently it does not have a ready installer and I need to compile it myself (which I don't know how)

Can someone please help me? This is very urgent.
1. download the source for the driver. 
2. ```
cd 'type the path to the folder containing the source'
```
3. ```
 ./configure
```
4. ```
 make
```
5. ```
 make install
```

---

### Post by Gmbrdilos on 2007-06-07
on step 3 I get this:
```
bash: ./configure: No such file or directory
```

---

### Post by dbbolton on 2007-06-08
> **Gmbrdilos said:**
> on step 3 I get this:
```
bash: ./configure: No such file or directory
```
ok, my bad. just check the README file in the acecad_3.1 folder. it tells you how to build from source.

---

### Post by kill4killin on 2007-06-08
go to the source directory and look to see if there is a file called INSTALL or README and see what they can tell you

Generally the source code downloads that you have to compile yourself come with both of those files and a file called configure. ./configure runs file and makes sure that you have all of the dependancies. If you do not have the configure file you can not compile the program.

---

### Post by Gmbrdilos on 2007-06-08
there is no file name configure and the readme that came with it is this: [http://acecad.sourceforge.net/README](http://acecad.sourceforge.net/README)

those instructions are unclear to me since I am relatively new to linux and never compiled anything before. I was hoping someone can brake down the readme for me

---

### Post by dbbolton on 2007-06-08
> **Gmbrdilos said:**
> there is no file name configure and the readme that came with it is this: [http://acecad.sourceforge.net/README](http://acecad.sourceforge.net/README)

those instructions are unclear to me since I am relatively new to linux and never compiled anything before. I was hoping someone can brake down the readme for me
well, everything in the readme with a $ in front of it is something that you need to enter in a terminal. i don't know how it break it down any further than that.

---

