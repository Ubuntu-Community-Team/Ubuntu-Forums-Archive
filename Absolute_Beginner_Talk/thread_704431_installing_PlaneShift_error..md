---
title: "installing PlaneShift error."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Ojama10 on 2008-02-22
I tried installing Planeshift with the following code di not work. Any suggestions?



jason@jason-desktop:~$ cd Desktop
jason@jason-desktop:~/Desktop$ sudo chmod +x PlaneShift_CBV0.3.020_x64.bin
jason@jason-desktop:~/Desktop$ sudo ./PlaneShift_CBV0.3.020_x64.bin
./PlaneShift_CBV0.3.020_x64.bin: 13: : not found
./PlaneShift_CBV0.3.020_x64.bin: 13: aH: not found
./PlaneShift_CBV0.3.020_x64.bin: 13: &#65533;U&#65533;Ud&#65533;Ud&#65533;&#65533;@@: not found
./PlaneShift_CBV0.3.020_x64.bin: 13: Q&#65533;td/lib64/ld-linux-x86-64.so.2GNU: not found
./PlaneShift_CBV0.3.020_x64.bin: 13: ELF: not found
./PlaneShift_CBV0.3.020_x64.bin: 14: Syntax error: "(" unexpected




I'm running Ubuntu Gutsy on a PS3, could that be the problem of why nothing will install properly? wrong architecture?

---

### Post by taurus on 2008-02-22
If you are running i386, you cannot install x64 apps on it.  Try downloading the x86 version then.

---

### Post by Ojama10 on 2008-02-26
I tried downloading the x86 version aswell, and exactly the same code came up.

---

### Post by Zeotronic on 2008-02-26
While I dont understand what the error code you submitted says, I will raise the possibility that you are using a AMD processor rather than an Intel processor? I'm sure you would know, but I just thought I'd prod that in there anyways.

---

### Post by dtgolder on 2008-03-08
I had it end up calling the wrong directory. Solved it by putting a symbolic link in my home directory:

ln -s /opt ./opt

---

