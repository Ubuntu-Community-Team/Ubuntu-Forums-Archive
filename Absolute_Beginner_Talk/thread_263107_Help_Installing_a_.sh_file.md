---
title: "Help Installing a .sh file"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-09-22
Hello,

I downloaded the Intel C++ compiler for Linux, it is in a tar.gz file in which I extracted it successfully. I think I have to change the directory from /home/myname/desktop to a folder in the main file system like /etc/.

I know the command is cd... and something, can someone help me out?

Andrew

---

### Post by ewl1217 on 2006-09-22
To change directories use the following command:
```
cd "directory you want to change to"
```
So to change to "/etc", for example use following command:
```
cd /etc
```

As far as C++ compilers, I think it would be easier your you to use GCC (short for the GNU Compiler Collection, which includes a C++ compiler). To install GCC and other useful development tools, use the following command:
```
sudo apt-get install build-essential
```

**EDIT:** If you still want to install the Intel C++ Compiler, I think that the proper directory to install it to would be in "/usr/local/bin".

---

### Post by andrew222 on 2006-09-22
Thank you very much ewl1217 for your reply.

To change to the directory using the command cd /usr/local/bin , would I then be able to place the install.sh file to that folder by cutting and pasting and then run the command 
   sh /usr/local/bin/install.sh     to install the file?

I will try this out and see how it works.

I think the GCC compiler sounds like a more proficient compiler and will have to get that one as well. I am continuing on to install the Intel C++ compiler to learn how to master the installing of a .sh file.

Thanks again,

~Andrew

---

### Post by lamego on 2006-09-22
andrew222,
you are not expected to copy the install script to /usr/local/bin .

You should not be spending time trying to install a compiler if you dont know yet to use the basic of your operative system.

Please give a read to:
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

I strongly advise you to install the "build-essential" package which includes GCC until you get some more experience with your system.

---

### Post by andrew222 on 2006-09-22
Thank you lamego for your reply,

I like your advice, I will spend some time to know the basics of the Linux operating system. I printed out the article from the URL and will read it several times.

I did install the 'build essential package. I went to my menu to find it and did not see it so I went to 'Applications/Add~Remove' and installed all items under 'programming'. Would Emacs 21(x11) be the interface for GCC?I know I have more to get familiar with in regards to familiarity with the 'build essential' package, I thought some helpful information from others would set me on the right path to start taking on things on my own.

Thanks again, hope you have a great weekend,

~Andrew

---

### Post by andypaxo on 2006-09-22
Hi,

You won't find GCC on a menu - it's not a graphical application. If you want to use it directly you'll need to use the command line.

If you want a graphical programming environment, have a look at Anjuta, KDevelop or Eclipse (You can download them all using apt or synaptic just like you can with build-essentials)

---

### Post by andrew222 on 2006-09-22
Thank you very much andypaxo, I will look into those.

I do appreciate all of the help from ewl1217, lamego and yourself.

I have some obvious researching to do before the next time I post to this forum ;-)

~Andrew

---

