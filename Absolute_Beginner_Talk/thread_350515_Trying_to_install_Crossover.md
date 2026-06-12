---
title: "Trying to install Crossover"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-31
I've searched through the forums and haven't seen this problem. I'm truly trying to get my problems resolved without asking too many questions. I downloaded the trial version to my desktop and following the instructions in one of the threads. This is the result in the terminal: 
 cd ~/Desktop
kliljedahl@kliljedahl-desktop:~/Desktop$ chmod 755 install-crossover-standard-prerelease-6.0.0beta3a.sh
chmod: cannot access `install-crossover-standard-prerelease-6.0.0beta3a.sh': No such file or directory
kliljedahl@kliljedahl-desktop:~/Desktop$ sudo ./install-crossover-standard-demo-6.0.0.sh
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/kliljedahl' directory does not belong to you.
Point $HOME to your home directory and try again.

What do I need to change to do this?

---

### Post by taurus on 2007-01-31
Why not just install it to your own $HOME directory.

```
./install-crossover-standard-demo-6.0.0.sh
```

---

### Post by kliljedahl on 2007-01-31
What I need to know is how to: Point $HOME to your home directory and try again.

---

### Post by kliljedahl on 2007-01-31
> **taurus said:**
> Why not just install it to your own $HOME directory.

```
./install-crossover-standard-demo-6.0.0.sh
```

And I got:  ./install-crossover-standard-demo-6.0.0.sh
bash: ./install-crossover-standard-demo-6.0.0.sh: No such file or directory
kliljedahl@kliljedahl-desktop:~$

---

### Post by taurus on 2007-01-31
You need to be in the Desktop directory because you saved it there.

```
cd ~/Desktop
./install-crossover-standard-demo-6.0.0.sh
```

---

### Post by kliljedahl on 2007-01-31
Thank you so very much, it's installing. I will learn the commands, I really will.

---

### Post by TehMark on 2007-01-31
me too :D  those pesky commands!

---

### Post by nlow04 on 2007-02-04
I'm new to Ubuntu Linux Operating system.  I tried to install Linux crossover standard and I got this message:

Could not open the file /tmp/install-crossover-standard-demo-6.0.sh using the Western(ISO-8859-15) character coding.

Please check that you are not trying to open a binary file.  Select a different character coding from the menu and try again.

I also changed my character coding and it produced this message:

Could not open the file /tmp/install-crossover-standard-demo-6.0.sh using the Unicode (UTF-8) character coding.

Please check that you are not trying to open a binary file.  Select a different character coding from the menu and try again.

Please advise.   Thanks.

---

### Post by Hex0x75 on 2007-02-07
> **nlow04 said:**
> I'm new to Ubuntu Linux Operating system.  I tried to install Linux crossover standard and I got this message:

Could not open the file /tmp/install-crossover-standard-demo-6.0.sh using the Western(ISO-8859-15) character coding.

Please check that you are not trying to open a binary file.  Select a different character coding from the menu and try again.

I also changed my character coding and it produced this message:

Could not open the file /tmp/install-crossover-standard-demo-6.0.sh using the Unicode (UTF-8) character coding.

Please check that you are not trying to open a binary file.  Select a different character coding from the menu and try again.

Please advise.   Thanks.

Sounds to me that you are viewing the file in question by going to PLACES -> Home Folder and then trying to double click the file. What you need to do is to open a terminal window by going to Applications -> Accessories -> Terminal or Applications -> System Tools -> Konsole. From there try running the application with the ./install-crossover-standard-demo-6.0.sh or by typing:
sh install-crossover-standard-demo-6.0.sh
either command should work fine for you.
Hope it helps,

---

### Post by Anatasia on 2008-05-11
luke@kylekatarn:~$ cd ~/Desktop
luke@kylekatarn:~/Desktop$ ./install-crossover-pro-6.2.0.sh
bash: ./install-crossover-pro-6.2.0.sh: /bin/sh: bad interpreter: Text file busy
luke@kylekatarn:~/Desktop$ ./install-crossover-pro-6.2.0.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./setup.sh: 201: /home/luke/.setup18332: not found
The setup program seems to have failed on x86/glibc-2.7
Check the system requirements at:
[http://www.codeweavers.com/products/cxoffice/requirements/](http://www.codeweavers.com/products/cxoffice/requirements/)

You might be missing the 32bit compatibility libraries

Sorry,I'm totally new to Ubuntu and this is the warning I've got.I'm using Ubuntu 8.04 64bit.How can I find glibc library?

Edit:eh,sorry.After install Wine everything seems to be ok right now.Sorry for any annoyment I've made.

---

