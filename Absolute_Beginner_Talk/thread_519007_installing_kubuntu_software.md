---
title: "installing kubuntu software"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-06
here us my problem...pretty much any installation guide is for ubuntu, and I can't find one just for kubuntu.  I don't know how to install programs/software on kubuntu.  I tried looking up different sites and its all gibberish to me cuz i need to make changes and i find it really hard to follow along.  I would really appreciate it if some1 could help me understand how to install things on kubuntu without all the confusion of skipping back and forth.  maybe a step by step or something that tells me what im looking for and how to do it.

ne1 please...even if u messaged me this, it would really b appreciated, THANK YOU

---

### Post by Inxsible on 2007-08-06
1) ```
sudo apt-get install <program-name>
```

2) ```
sudo aptitude install <program-name>
```

The above two methods should be the same no matter if you have Ubuntu or Kubuntu or Xubuntu

There may be differences in the GUI way of installing stuff. I dont use Kubuntu, so I wouldnt speculate.

---

### Post by jnorthr on 2007-08-06
The command line should be used for apt-get as i found this more reliable than aptitude. Use the 'man' command to review the manual pages that describe it or see [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get) Can you advise as to what you are trying to install as we may be able to walk you thru the first one until you get the hang of it.:)

---

### Post by por100pre1 on 2007-08-06
I think Adept Manager is the GUI program for installing programs in Kubuntu...

---

### Post by jd65pl on 2007-08-06
See installing via the command line on [this]("http://jamie.dumbill.googlepages.com/l_how_to_vids.html") page

---

### Post by Inxsible on 2007-08-06
> **jnorthr said:**
> [COLOR=Red]The command line should be used for apt-get as i found this more reliable than aptitude.[/COLOR] Use the 'man' command to review the manual pages that describe it or see [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get) Can you advise as to what you are trying to install as we may be able to walk you thru the first one until you get the hang of it.:)
Why do you say that? I have always used aptitude, since it keeps track of dependencies and never had a problem ever. But I guess that difference doesn't matter since Edgy, since apt-get also included features to track dependencies.

---

### Post by ron999 on 2007-08-06
Hi Firestorm
With Ubuntu we can install programs using  Synaptic Package Manager.
I think that the equivalent with Kubuntu is called Adept Installer.

---

### Post by kebes on 2007-08-06
As Inxsible said, you can use "apt-get" or "aptitude" on the commandline to install/uninstall software in Ubuntu and Kubuntu. If any instructions for Ubuntu describe using the commandline (a.k.a. terminal), then they will work in Kubuntu also.


If you want to install things graphically, in Kubuntu there is a package manager called "Adept." So any instructions for Ubuntu that refer to "Synaptic" will work in Kubuntu if you just use "Adept" instead. The interface is just a bit different but very intuitive.

To use Adept, you go:
K Menu->Add/Remove

This will open a browser where you can see software categorized. If you know the name of the software you want to install you can go:
System->Administration->Synaptic package manager.

This will list all available packages, and allow you to select the ones you want.


To install some pieces of software, you need to download a file and manually install it. This is quite rare, however. Often what you need is in the repositories. If you ever need to do a manual install, there are guides to help. For example:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you run into trouble with a particular installation, you can of course post  a question on the forums.


Hope that helps.

---

### Post by por100pre1 on 2007-08-06
> **jnorthr said:**
> The command line should be used for apt-get as i found this more reliable than aptitude.

Are you sure about your findings? :rolleyes:

---

### Post by bowens44 on 2007-08-06
sudo apt-get install synaptic.

then use synaptic

---

### Post by hyper_ch on 2007-08-06
I tend to think aptitude is more reliable than apt-get and aptitude also installs the recommended packages which I like :)

---

### Post by Inxsible on 2007-08-06
> **hyper_ch said:**
> I tend to think aptitude is more reliable than apt-get and aptitude also installs the recommended packages which I like :)

I second that.

---

### Post by FireStorm102389 on 2007-08-06
I just want to thank ALL of u for all of ur input on this matter...however i can't tell u what im going to install because I am just trying to figure out how to do it...I downloaded a few things off the internet for it from the official ubuntu site so they should be good...they give me 2 different types of file names but im sure i can figure that out...neways...ty, and if I run into any more trouble I will make sure to post it in the forums cuz im sure some1 else will have the same question sooner or later.

---

### Post by Inxsible on 2007-08-06
> **FireStorm102389 said:**
> however i can't tell u what im going to install because I am just trying to figure out how to do it. ???
If you tell us what you are installing, maybe we could help you figure it out a lot faster. Just a thought :)

---

