---
title: "Dial-up Modem Problems"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-02-10
I am trying to set up a dial-up internet connection on a Compaq Presario 900. Ubuntu 6.10 is the only OS installed on the computer.

Ubuntu does not recognize the modem and I have searched numerous sites for the appropriate driver. 

The site that the DialupModemHowto page links to is excruciatingly unorganized, I feel more confused after reading it than I did initially.

And I cannot install a package file from my laptop because the computer doesn't have an internet connection, I'm trying to set it up! I need a file that I can download off my Dell running Windows Vista, transfer to the Compaq, and then run.

Every site that I encounter insists that I download a file using a package manager, but I can't without an internet connection! It is very frustrating, and I have nowhere to go. Even more frustrating are the files I've downloaded that work up to a certain point in the installation, and then try to connect to download a package file! I can't do that without an internet connection!

I've been trying to get this set up for more than a week and I'm about ready to give up.

How can I fix this problem?

---

### Post by jpeddicord on 2007-02-10
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You should be able to find the package you need there. :)

---

### Post by Shack_ on 2007-02-10
I couldn't find a driver for an HSF modem, which is what that modem is, so...

I've downloaded the package that the original installer file was trying to connect to the internet to download, and the installation seemed to go well, but, I still can't connect to the internet and the Device Manager says that the modems capabilities are unknown. I made sure that I downloaded the right package for the kernel type, so I don't know what else to do.

Would it be easier to buy an external modem? If so, where's the best place to look for Ubuntu compatible ones?

---

### Post by sardion on 2007-02-10
You probably need to install slmodemd (I had to).

Get that package (and its dependencies) from packages.ubuntu.com.  Other places in these forums have instructions about how to use slmodemd to set up pretty much anything

---

