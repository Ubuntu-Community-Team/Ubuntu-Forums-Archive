---
title: "Cannot Install ANYTHING!"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by tel93 on 2008-01-16
Sorry, but I'm a Linux n00b. I wanted to ditch WIndows so badly, so I installed Ubuntu Gutsy. I have never had Linux on my computer before, so I don't know much about it. Even so, this may seem like a silly question, but how do you install packages without experiencing a dependency error?

Also, could anyone tell me how tomake my second monitor work (not clone). Additionally, I can't enalbe desktop effects. Could someone please help me?

---

### Post by scizzo on 2008-01-16
Well lets start with the package install errors.

What happens when you try to install. Can you give us the errors?

How much of the installation have you done for ubuntu? No extra settings or anything like that?

---

### Post by tel93 on 2008-01-16
No extra settings. They are just "dependency errors", for different packages each time. :(

---

### Post by shibu on 2008-01-16
hi ..

Welcome  tel93

try running the command below to see why you are getting dependency error.

sudo apt-get check

Thanks

---

### Post by SOULRiDER on 2008-01-16
HaVe you been downloading debs from sites? the best thing you can do is install programs using Synaptic, if you cant find them there then yes, look for debs and install the dependencies manually.

To use two monitors you'll have to have your video drivers set up.

To use desktop effects monitors you'll have to have your video drivers set up.

What kind of video card do you have?

---

### Post by mcduck on 2008-01-16
Read this: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by philinux on 2008-01-16
Before you install anything either check in Application>Add Remove or System>Admin>Synaptic Package manager.

Also click the medibuntu link below and follow the instructions there to enable their repo's

(Repo's = repositories = webservers containing software etc)

---

### Post by tel93 on 2008-01-17
I did download packages, and I tried to install them via Synaptic. Some inbuilt packages seem to work, but the vast majority have problems. By the way, I have an Nvidia GeForce 6200 with 256mb of video ram, purchased in 2006.

---

### Post by tel93 on 2008-01-17
[[IMG]http://img153.imageshack.us/img153/2382/screenshotbracksisahoboqg3.th.png[/IMG]](http://img153.imageshack.us/my.php?image=screenshotbracksisahoboqg3.png)

I type in sudo apt-get check, and I get that.

BTW I tried installing other debs with sudo aapt-get check, but none of them seemed to work.

---

### Post by tel93 on 2008-01-18
bump!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Aelfric5578 on 2008-01-18
Can you cut and paste the actual output you get when you try to install something? It doesn't matter what.  Anything that's given you problems.

---

### Post by jahisthebalance on 2008-01-18
alright, its

sudo apt-get install "..."    

now, that "..." is the name of what you're trying to install, you type the name without the quotes, or ellipses.  

much software will populate on the applications menu, somewhere after the terminal runs through its business check out a program called Envy, which a program available on the internet that is supposed to automate a good deal of video card stuff, specifically nvidia ones.

---

### Post by bodhi.zazen on 2008-01-18
the syntax is 

sudo apt-get install package

check does not install :

> check
[indent]check is a diagnostic tool; it updates the package cache and checks for broken dependencies.[/indent]

You can also use ADD/Remove programs or synaptic.

---

### Post by scizzo on 2008-01-18
The output from apt-get check did not give any errors. Either if you have problems installing packages from the internet I suggest you take a look at the repos and also follow the other instructions given on the thread.

If you for example run:

```

sudo apt-get update

```

Then the output should be all the repos and checks towards the internet sites you have in the source treee.

Please run this and see if it checks the links. Otherwise check so that you do not use the cdrom anymore since that might still be enabled in the repos.

You can view: /etc/apt/sources.list and look at the top repo to see if the cdrom is having a # infront of it.

---

### Post by shoeboxin on 2008-02-20
I am having a similar problem to this. When I try to install ANYTHING, either by synaptic or in the terminal, I cannot. It says dependency errors. For example:

```
kevin@KevinCalvert-laptop:~$ sudo apt-get install gnome-vfs-obexftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-vfs-obexftp: Depends: libopenobex1 but it is not installable
E: Broken packages

```

I also attempted to download the libopenobex1 package directly and install manually but received the same dependency errors. Anyone have any idea. Is it just a bad install of Ubuntu? I am running 7.10 gutsy

---

### Post by shoeboxin on 2008-02-20
Bump...If anyone has an idea that would be great. I would rather not reinstall ubuntu.

---

