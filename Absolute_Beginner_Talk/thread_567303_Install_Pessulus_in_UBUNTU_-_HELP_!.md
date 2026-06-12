---
title: "Install Pessulus in UBUNTU - HELP !"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Technobyte on 2007-10-04
Hi everyone please help. I am very very new to UBUNTU. I have installed UBUNTU on a machine and I am most impressed so far. I want to use this machine as a public machine and only want to give users access to the Internet ( Firefox ) and not allow them to fiddle with anything else.

I downloaded Pessulus. Can someone help me install this please. I have no clue...Sorry for sounding so dumb but UBUNTU is completely new to me and I need help. Anybody that can help I will really appreciate it.

---

### Post by wpshooter on 2007-10-04
> **Technobyte said:**
> Hi everyone please help. I am very very new to UBUNTU. I have installed UBUNTU on a machine and I am most impressed so far. I want to use this machine as a public machine and only want to give users access to the Internet ( Firefox ) and not allow them to fiddle with anything else.

I downloaded Pessulus. Can someone help me install this please. I have no clue...Sorry for sounding so dumb but UBUNTU is completely new to me and I need help. Anybody that can help I will really appreciate it.

Go into the Synaptic application manager portion of Ubuntu and do a "NAME" search for that application you are looking to install and if it is in the repositories, you can install it directly in Synaptic by checking the box and hitting the apply button.

Good luck.

---

### Post by por100pre1 on 2007-10-04
It is in the repositories, just do this:

```
sudo apt-get install pessulus
```

---

### Post by Technobyte on 2007-10-04
Sorry no luck here.Appreciate your response. Why do they have to make it so complicated ? I am a fairly literate computer user and my first time with UBUNTU but I am afraid they are loosing me here because it is so complicate to install one thing! Is it just me ??? I am really trying but I am missing something.

---

### Post by Technobyte on 2007-10-04
Guys I am confused...sorry and thanks for your patience. I have gone into the repositories and tried what you have suggested and no luck...

Can we go back to the start. I have downloaded Pessulus. It is in a folder on the desktop.

What do I do next how do i get it to run in Synaptic?

Thanks for your patience and your help I really do appreciate this.

---

### Post by por100pre1 on 2007-10-04
Which Ubuntu release are you using?

---

### Post by Technobyte on 2007-10-04
I am using 7.04

---

### Post by wpshooter on 2007-10-04
> **Technobyte said:**
> Guys I am confused...sorry and thanks for your patience. I have gone into the repositories and tried what you have suggested and no luck...

Can we go back to the start. I have downloaded Pessulus. It is in a folder on the desktop.

What do I do next how do i get it to run in Synaptic?

Thanks for your patience and your help I really do appreciate this.


If it is not in / program in Synaptic repositories, then you do not install it from there.

Here is what I would do.  Go into your home directory and make yourself a DOWNLOAD subdirectory.  I HATE downloading stuff to the desktop, I always download to either HOME or download directory.

Copy / move your application from the desktop to the download directory.

Then go to the terminal and CD to the download directory and see what is in the download directory by typing LS command.

There is possibly either an INSTALL program there that you would use to do the installation or there is possibly another file with the name of the software program that you would either extract to access other files that might be used to install the program.

Did you look on the website at which you downloaded this program for directions on how to install it ?

---

### Post by por100pre1 on 2007-10-04
> **Technobyte said:**
> I am using 7.04

Do this:

```
gksudo software-properties-gtk
```

and then ensure that the main, universe, restricted, and multiverse repositories are enabled.

---

