---
title: "How to install downloads"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Roaster on 2007-08-02
Hello all, I've installed Ubuntu 7.04 on my home built, dual booting with XP Pro. I must say it was much easier than I thought it would be! Now comes the learning process. I'm dumb as a rock when it comes to Ubuntu, so........I've done all the updates. When I download a tar.gz thingy I cannot, do not, know how to install it. I am becoming acquainted with the Terminal but as I said very new to this. To be specific, I downloaded Adobe Reader_enu-7.0.9-1.i386.tar.gz because when I go to the Synaptic Package Manager to get acroread I get the warning that this is "not authenticated and could cause damage to the system". How do I install this download? Thanks in advance

---

### Post by Paul820 on 2007-08-02
A tar.gz file is just an archive like .zip or .rar, you can just right click it and click extract here. It's what's inside what you have to install. :)

---

### Post by pyros on 2007-08-02
Here's some instructions on installing, as well as a great general resource for those getting started with ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PDF_Reader_.28Adobe_Reader.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Ek0nomik on 2007-08-02
Could you post the exact error message you are getting by using Synaptic?  It's a problem that you should probably fix and not avoid fixing.  :)

If the link pyros provided you with works, than excellent!  Although by using 'aptitude' I would presume you get the same error that you have been getting by using Synaptic, since Synaptic is a front end for apt.

If you want to install from the tar.gz file you have you first need to extract the contents.  Think of the tar.gz file as a wrapper that goes around a piece of candy.  It simply holds the contents or data (maybe not the best analogy in the world, but bear with me)

You can untar it graphically by right clicking, or you can issue this command in the terminal:

```
tar -zxvf Adobe Reader_enu-7.0.9-1.i386.tar.gz
```

This will make a folder in the directory you were in when you issued the command.  Now you have a folder with a bunch of "stuff".

You need to compile the program now.  If you have never done so before, you may need to install a few tools.  Issue this command (if you aren't sure, just do it anyways)

```
sudo apt-get install build-essential
```

Now you need to navigate into the directory where the files are, and install it.

It will go something similar to this:

```
cd AdobeReader
make
sudo make install
```

You can also read the instructions provided by the makers of the program, usually in a file called README.

```
ls -la #This will list the contents in your current working directory
gedit README
```

---

### Post by Roaster on 2007-08-02
That is just what I needed, EkOnomik. I need to learn to use the Terminal and you gave be the info line by line! Thanks. The warning I get in the Synaptic Package Manager is 'You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system'. I suspect the warning is because it is not supported by Ubuntu, maybe? Thanks again.

---

### Post by philip793 on 2007-08-02
:KSI need help with that too.:KS

---

### Post by Roaster on 2007-08-02
This also very helpful, Pyros! appreciate it!

---

### Post by Ek0nomik on 2007-08-03
> **Roaster said:**
> That is just what I needed, EkOnomik. I need to learn to use the Terminal and you gave be the info line by line! Thanks. The warning I get in the Synaptic Package Manager is 'You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system'. I suspect the warning is because it is not supported by Ubuntu, maybe? Thanks again.

You can just accept that message.  It's just saying that the package isn't signed.

I have gotten that a few times myself.

Were you able to compile the program or are you still having trouble?

---

