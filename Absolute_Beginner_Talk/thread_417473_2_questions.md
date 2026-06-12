---
title: "2 questions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-04-21
Hi, i just installed Ubuntu 7.04 a couple of minutes ago. But i have some problems. 
1: when start the computer i get the choice between 6 OS, I only have vista and ubuntu but i can apparently choose many types of ubuntu and vista + vista recovery mode + something i didn't understand. I only wan't Ubuntu or vista. And i wan't a timer on eks. 6 seconds, so it stands in 6 secs and if i don't choose ubuntu within 6 secs vista will start. 

2: when i try to start compiz the screen just turns white and i have to restart the computer :( 

sorry for my bad english

---

### Post by Happy_Man on 2007-04-21
Well, to get rid of all the extra kernel listings you will have to edit the grub menu:

```
 sudo gedit /boot/grub/menu.lst 
```

And the compiz problem seems to be a graphics card issue. What kind of graphics card do you have?

---

### Post by ajmannen on 2007-04-21
I hava Nvidia GeForce Go 7300, do you think i should drop Compiz and go for Beryl?

---

### Post by bulldog on 2007-04-21
> **Happy_Man said:**
> Well, to get rid of all the extra kernel listings you will have to edit the grub menu:

```
 sudo gedit /boot/grub/menu.lst 
```

And the compiz problem seems to be a graphics card issue. What kind of graphics card do you have?

Please use 'gksudo' for graphical applications,to avoid problems with the .ICEauthority.

Just comment out the lines in your menu.lst by putting a # in front of the line.

Did you install any driver for the graphics?

---

### Post by ajmannen on 2007-04-21
I have not installed anny drivers, do i need to?

I deleted the other start up options (like windows recovery mode wich i can start from windows) was that bad?

---

### Post by Sef on 2007-04-21
> I hava Nvidia GeForce Go 7300, do you think i should drop Compiz and go for Beryl?

No, because Compriz and Beryl are going to merge.

---

### Post by bulldog on 2007-04-21
To use compiz or Beryl,it could be a good idea to install the nvidia driver.

I personally use Beryl and Emerald and it works like a charm,it has some more advanced options as compiz,but can be less stable to use.
But I use it for about 2 months now on Feisty,and had no trouble yet.:)

---

### Post by Happy_Man on 2007-04-21
Didn't Desktop Effects prod you to install some restricted driver or another upon first start? If not, go into Restricted Drivers Manager (System --> Administration --> Restricted Drivers Manager) and install from there.

---

### Post by ajmannen on 2007-04-21
I have one "rstricted" driver but i 't know how to install it:confused:

And i rather wan't beryl instead of Compiz, (looks better on you tube :D) so how to uninstall Compiz, and how to install drivers

PS: The name of the driver that is restricted is Atheros Hardware Acces Layer (HAL)

---

### Post by bulldog on 2007-04-21
You don't have to un install compiz,just install the nvidia driver and beryl.

Take a look at this site and you'll find what you're looking for and more.........

[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#)

---

