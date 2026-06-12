---
title: "java"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by alentejo-rose on 2007-03-19
Hi I am new to Linux  and have just downloaded java  jre-1_5_0_11-linux-i586-rmp-bin I have it on my desktop but have no idea what to do to install it! PLEASE help :)

---

### Post by r4ik on 2007-03-19
Try,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Good  luck !

---

### Post by Rui Pais on 2007-03-19
> **alentejo-rose said:**
> Hi I am new to Linux  and have just downloaded java  jre-1_5_0_11-linux-i586-rmp-bin I have it on my desktop but have no idea what to do to install it! PLEASE help :)

Hi,
i presume that you mean jre-1_5_0_11-linux-i586-r**pm**-bin file.

Note that you probably want jre-1_5_011-linux-i586.bin and not the rpm self extracting one.

to install follow the instruction on sun's site (next to download link):
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

good luck

---

### Post by aa.ivanov on 2007-03-19
This is a binary installer. You open a terminal, go to the directory where you've wrote the file and execute it
```
sh jre-1_5_0_11-linux-i586-rmp-bin
```

if I were you I would have opened synaptic and install sun-java5-bin

---

### Post by fatphilthethird on 2007-03-20
> **alentejo-rose said:**
> Hi I am new to Linux  and have just downloaded java  jre-1_5_0_11-linux-i586-rmp-bin I have it on my desktop but have no idea what to do to install it! PLEASE help :)

Why not just use Add/Remove programs? Sun Java is listed in there and seems the easier way.

Fat

---

### Post by Chemist on 2007-03-20
you could try automatix

---

### Post by thefoolisme on 2007-03-20
I think the easiest way for a newbie to install Java is definitely going through Add.remove programs.  I messed with the original files from Sun and some of the other java installations yesterday, and couldn't get any of them to work right via the tutorials.  I went to Add/remove programs (or synaptic manager, I can't remember) and voila!  it was done in no time  :-)

---

### Post by alentejo-rose on 2007-03-20
> **fatphilthethird said:**
> Why not just use Add/Remove programs? Sun Java is listed in there and seems the easier way.

Fat
Hi thanks for the information.. I tried this option and this is what I got.

The use, modification and distribution of Sun Java 5.0 Runtime is restricted by copyright or by legal terms in some countries.
Sun Java 5.0 Runtime cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by alentejo-rose on 2007-03-20
> **Chemist said:**
> you could try automatix
I am sorry I dont understand what you mean  but then I am totally lost with this programme. 
thanks for the reply  though!

---

### Post by alentejo-rose on 2007-03-20
> **Rui Pais said:**
> Hi,
i presume that you mean jre-1_5_0_11-linux-i586-r**pm**-bin file.

Note that you probably want jre-1_5_011-linux-i586.bin and not the rpm self extracting one.

to install follow the instruction on sun's site (next to download link):
[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

good luck
Hi  I have tried this and when i have typed in password as in step 2 this is what comes up on my screen:

alentejo-rose@alentejo-rose:~$ su
Password: 
su: Authentication failure
Sorry.
alentejo-rose@alentejo-rose:~$  


So I dont know what I am doing wrong. 
thanks for the suggestion though

---

### Post by Rui Pais on 2007-03-20
> **alentejo-rose said:**
> Hi  I have tried this and when i have typed in password as in step 2 this is what comes up on my screen:

alentejo-rose@alentejo-rose:~$ su
Password: 
su: Authentication failure
Sorry.
alentejo-rose@alentejo-rose:~$  


So I dont know what I am doing wrong. 
thanks for the suggestion though

sorry to have induced you in error... those are generic instructions and Ubuntu use a special security model, with sudo.

redo the instructions, but replace any su with sudo.

---

### Post by Rui Pais on 2007-03-20
More detailed, like this:
```
chmod a+x jre-1_5_011-linux-i586.bin
```
then
```
sudo ./jre-1_5_0-linux-i586.bin
```

---

