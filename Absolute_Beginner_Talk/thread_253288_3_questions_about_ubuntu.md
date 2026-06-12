---
title: "3 questions about ubuntu"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by H3HI on 2006-09-08
[SIZE="5"][COLOR="Red"]Q1: (in my home pc)[/COLOR][/SIZE]

after installation the ubuntu, i used the sudo command in command line mode. 
ex: sudo apt-get install gnome-ppp

the system asked me to input the psw, i followed the wiki just press the 'enter', but these isnot any notice about invalid psw or execute the command, it just back to the command line.

when i used the graphic ui for the root function, ex: User and Computer. it also shows me the dialog of psw input, and i just click the OK, and it doesnot show me anything as like the command line mod. 

Of course, when i used the sudo or some root function, it will notic me input the psw again and again. :( .

i also install ubuntu in office pc by vmware, but above these problems have not been appeared. 

[SIZE="5"][COLOR="Red"]Q2: (in my office pc with vmware)[/COLOR][/SIZE]

i try to install the gnome-ppp to my ubuntu. 
i use "sudo apt-get install gnome-ppp"
the system notic me, cannot find the software package. 


[SIZE="5"][COLOR="Red"]Q3: (in my office pc with vmware)[/COLOR][/SIZE]

i download a rpm package to desktop, and use 
"sudo rpm xxx.rpm"
the system says "rpm command not found"


the follow pic is the screenshot of Q2 and Q3.](*,) 

that chinese is meaning about:
Line1: Reading the software package list....Finish
Line2: Analyzing the relation tree of software package...Finish
Line3: Cannot found the software package gnome_ppp
[IMG]http://forum.ubuntu.org.cn/files/thumbs/t_-2_410.jpg[/IMG]

---

### Post by wieman01 on 2006-09-08
Answer to question 3: You need to install the RPM package. RPM is a Redhat packaging manager which does not come with Ubuntu by default. But you can find it in the repositories:
> sudo apt-get install rpm

---

### Post by OffHand on 2006-09-08
1) you have to put in your password.
2) [https://help.ubuntu.com/community/Repositories/](https://help.ubuntu.com/community/Repositories/)

---

### Post by crispy_420 on 2006-09-08
If you have no option but use a RPM package, use alien to convert to DEB package. Just search the repo for alien. Once installed cd to the directory (or better yet install nautilus-terminal plugin to skip the cd process).
> alien <package_name>

---

### Post by CatKiller on 2006-09-08
> **H3HI said:**
> after installation the ubuntu, i used the sudo command in command line mode. 
ex: sudo apt-get install gnome-ppp

the system asked me to input the psw, i followed the wiki just press the 'enter', but these isnot any notice about invalid psw or execute the command, it just back to the command line.

when i used the graphic ui for the root function, ex: User and Computer. it also shows me the dialog of psw input, and i just click the OK, and it doesnot show me anything as like the command line mod. 

Of course, when i used the sudo or some root function, it will notic me input the psw again and again. :( .

For sudo commands, you should be entering your user password. It should only be blank if you haven't set a password.

> i try to install the gnome-ppp to my ubuntu. 
i use "sudo apt-get install gnome-ppp"
the system notic me, cannot find the software package.
The gnome-ppp package is in the Universe repositories. Check [http://ubuntuguide.org](http://ubuntuguide.org) or HOWTOs on this site for information on how to enable the Universe repositories.

> i download a rpm package to desktop, and use 
"sudo rpm xxx.rpm"
the system says "rpm command not found"

If you're going to use the rpm command, then you need to install the rpm package. It's in the repositories, so you can use Synaptic or apt-get to install it. However, it's advised that you use alien instead of rpm, since that will integrate the RPMs with the rest of your packages. alien is in the repositories too.

---

### Post by H3HI on 2006-09-08
> **crispy_420 said:**
> If you have no option but use a RPM package, use alien to convert to DEB package. Just search the repo for alien. Once installed cd to the directory (or better yet install nautilus-terminal plugin to skip the cd process).


i use the alien command a minute ago, system said "alien command not found". do i need to "sudo apt-get install alien"??

---

### Post by H3HI on 2006-09-08
> **OffHand said:**
> 1) you have to put in your password.
2) [https://help.ubuntu.com/community/Repositories/](https://help.ubuntu.com/community/Repositories/)


i have, but it says my password is invalid. :( :(

---

### Post by OffHand on 2006-09-08
> **H3HI said:**
> i have, but it says my password is invalid. :( :(

Did you put in a password during installation?

---

### Post by H3HI on 2006-09-08
> **OffHand said:**
> Did you put in a password during installation?

of course, how do you think how i can login the system.


but i'm staying in office, when i'm home, i will try again. thx your solution. :)

---

### Post by OffHand on 2006-09-08
> **H3HI said:**
> of course, how do you think how i can login the system.
Hehe yeah, you are right... still early here  ;)
> **H3HI said:**
> 
but i'm staying in office, when i'm home, i will try again. thx your solution. :)
No problem. You should be able to use sudo with the same password as you log in.

---

### Post by H3HI on 2006-09-11
still didn't know what happened. i reinstall the ubuntu that the sudo command is back. 

so, i can online now, and i can get the source for install package. :p 

thx all.

---

