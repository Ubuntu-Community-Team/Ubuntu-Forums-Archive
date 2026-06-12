---
title: "How to Install tar.gz, tar.bz2, etc."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by davidajohnson12 on 2008-03-14
Hello,
I am very new to Linux, so bear with me. I have probably read 100 posts on this topic and none of them seem to help. I have tried the procedure where you type code into terminal, I have tried using the Add/Remove program and I have tried using synaptic. Here is my situation: I have Ubuntu installed and I would like to install various programs such as Pidgin (which is a tar.bz2 file) and songbird (which is a tar.gz file). However, when I try the terminal procedure, I always get errors and I think it must have something to do with the fact that I am just copying what the forums say to type and I really don't understand what I am typing. When I try the Synaptic procedure and the Add/Remove procedure, I can never find the file that I downloaded, to be able to mark it for install. I have tried enabling other repositories, etc, but I have hit a brick wall. All I would like to do is install these programs that I downloaded from the internet the easiest way possible.

I tried using synaptic by following the instructions on the link below (which claims "how to install ANYTHING in Ubuntu"), but like I said, I can't find the file that I downloaded AND I cannot figure out how to add that file to Synaptic.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I apologize for my inaccurate usage of some technical terms, but as I previously mentioned, I really don't understand linux quite yet. Hopefully I will have a better grasp in the future. Thank you in advance to anyone who replies. I really appreciate everyone's assistance in my transition from windows.

Dave

---

### Post by EvilBro on 2008-03-14
> **davidajohnson12 said:**
> When I try the Synaptic procedure and the Add/Remove procedure, I can never find the file that I downloaded, to be able to mark it for install.
I might be mistaken, but I don't think you've fully grasped the idea of Add/Remove. It is not for installing files you've downloaded. It is for installing application from repositories. Just type in the program you want to install in the search bar. If it exists in the repository, tick the box next to it (tick means 'turn green' here) and press 'apply changes'.

---

### Post by drbob07 on 2008-03-14
It'd probably be more useful to know exactly which tar.gz files you downloaded. You may have downloaded source or binary archives, and compiling source code is different from installing binaries

---

### Post by finer recliner on 2008-03-14
i would suggest not bothering how to deal with tar files yet, they are a bit harder to work with instead of using a package manager (i.e. synaptic)

synaptic does not download installers for you, it downloads AND installs the programs for you. after marking a package for installation. you just click the Apply button and you're done. 

Pidgin should show up for you in Applications > Internet. you don't even have to restart the computer. 

if that doesn't work, try typing this command in the terminal:
```
sudo apt-get install pidgin
```

post the output of that if get an error

---

### Post by RealPSL on 2008-03-14
Dave,

Assuming you are running Gutsy (7.10) and memory serves me correctly you already have pidgin installed. If you do not you can install the version that comes with 7.10 from the Add/Remove programs under the applications menu. Just enter pidgin in the search box. When it comes back just click the check box and hit apply changes.

Songbird does not appear to be available from the default which will make it's install a little more challenging. You can reference Song Bird installation guide here [http://www.arsgeek.com/?p=615](http://www.arsgeek.com/?p=615). Based on references it seems to be fairly useful.

---

### Post by Afkpuz on 2008-03-14
Ok, here is how you use synaptic.  

1.) Open it
System>Administration>Synaptic package manager

2.) Search for the program you want to find
Just click the button that says "Search" at the top and type in "pidgin"

3.) Check the box next to pidgin and then hit apply

That will install anything that is stored within the repositories. 

Some people showed you some code to type in.  something like:
```
sudo apt-get install pidgin
```

That is the command line version of the steps I listed above.  If you ever want to install something and you know the exact name of the package in the repos (you can find the package name in synaptic), then you can use 

```
sudo apt-get install PAKAGENAME
```

---

