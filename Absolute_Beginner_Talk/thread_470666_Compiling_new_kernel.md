---
title: "Compiling new kernel"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2007-06-11
Dear friends,

I do not have internet connection in my desktop, however, I can download new kernel from elswhere and want to compile the new kernel in the desktop. I searched through old postings, but I got confused as I am not an technical expert. Pls guide me what exactly I have to do to compile a new kernel - I mean please inform the sequence of operations (including commands) I have to go through.

Thanks & regards,

Raj

---

### Post by mlentink on 2007-06-11
Why do you want to compile a new kernel? 
Writing and compiling kernels is work for specialists, not something for us mere users.

Perhaps you just want to upgrade your kernel?

---

### Post by Seisen on 2007-06-11
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

You will also have to download all these packages ```
build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
``` and their dependicies and install them on your computer also before you can build a new kernel.

---

### Post by ikonia on 2007-06-11
why do you want to build a new kernel ?

more so this question if your a beginner.

---

### Post by Seisen on 2007-06-11
Why are you guys putting people down for wanting to build a kernel. Maybe he just wants to learn how the kernel works. Give the person some credit for trying to take the initiative at least

---

### Post by rajsarkar on 2007-06-11
Dear friends, 

Let me tell you the whole story. I run an NGO ([www.krittibas.org](www.krittibas.org)) and we have an IT lab with 3 desktop PCs. We have been running Edubuntu since its first version and the lab is very popular among the local students. 

All the three desktops are pretty old but all of them have 256 MB of RAM. Thats why the workstation installation of Edubuntu runs quite well. However we don't have any internet connectivity in the village where the Lab is situated. 

Unfortunately the Feisty Fawn has been released with a bug for which PS/2 mouse does not work under Feisty. This bug does not affect aal desktops but it affects the desktops in our lab. We were so frustrated when we found that after a fresh installations the mouse was not working at all. Later through the forum I came to know that the bug was reported long back and I was surpirsed how the final version was released without solving the problem. This particular issue is quite well known in the forum and have caused much pain to a hardcore ubuntu lover like myself. Believe me I was shattered, I still can't believe that this has actually happened. 

As you have pointed out the easiest way is to upgrade the latest kernel which may solve the problem but because of the unavailability of internet we can't do that. That is why I want to download the latest kernel and compile it in our lab. If a step by step guide is available I can do it as I have very limited technical knowledge. I am purely a user. 

Hope I have clarified all the confusions. Your help will be appreciated. 

Raj

---

### Post by Seisen on 2007-06-11
If you follow the guide I gave you it will help compile a new kernel. Go here and you can find all the dependencies for what you need to compile the kernel. You will have to search for the files individually that I listed in the previous post. The dependencies for the files have the red dots next to them.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by Skrynesaver on 2007-06-11
Perhaps you should take a look at [setting up a local cache of the repository]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher") for one of the machines on you local network.  This could be updated anytime you get the opertunity to bring the repository cache machine off-site.

---

### Post by mlentink on 2007-06-11
Thx Skrynesaver,

If I read it correctly, what Raj wants is a method to update his machine with new packages (even the new kernel packages) without being connected to the internet. Personally, I think he's much better served with a method to do that, than with a method to compile his kernel from scratch, which is much more error-prone, especially for someone, as Raj himself points out, with relatively low experience. 
If I am mistaken, no doubt Raj will set me straight.

---

### Post by rajsarkar on 2007-06-12
Friends,

THank you very much for all your replies. If I am getting you correctly then I think I have got a solution for my problem as outlined below - 

1. I install Ubuntu in a mchine with internet connection
2. Create a local repository in this machine.
3. Update the kernel and also install new applications as per our need.
4. Burn the local repository in a CD.
5. Use this CD to update desktops in our lab 

Thanks once again. I can do it. 

Regards,

Raj

---

