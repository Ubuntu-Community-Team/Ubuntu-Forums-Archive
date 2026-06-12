---
title: "[SOLVED] Is it possible to manually upgrade Eclipse"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by excogitation on 2008-03-08
I installed Eclipse (3.2) using Synaptic.

The problem is it doesn't come with WST and I can't find that in Synaptic.

So I thought it might be possible to download the latest Eclipse IDE for Java EE Developers
and just replace the old installation (overwrite usr/lib/eclipse).

Obviously that's not the way to go (Software Updates -> Find and Install and Manage Configuration aren't working after that).

So either how do I get WST or how can I upgrade to JEE?

btw. what does GCJ version mean?

---

### Post by buntu_Geek on 2008-03-08
What i know is there is an all in one eclipse package with wtp tools included...

You can get it from this:
[http://archive.eclipse.org/webtools/downloads/drops/R1.5/R-1.5.0-200606281455/](http://archive.eclipse.org/webtools/downloads/drops/R1.5/R-1.5.0-200606281455/)

And one more thing.... there is some problem with some of the eclipse plugins in ubuntu 7.10...

Eclipse works best in 7.04 (feisty).. i have worked in it..

I suggest you to work in feisty if u want full power of eclipse....

Hope that helps..

---

### Post by excogitation on 2008-03-08
Actually this version is a bit old... (June 28, 2006),

Current versions:
... [Eclipse Webtools]("http://download.eclipse.org/webtools/downloads/") ...

I installed the Eclipse IDE for Java EE Developers package which comes with WST.

The thing is just that Help->Software updates->... isn't working - which I thought was
a problem I caused - but now it seems like I'm not alone with that problem so I wasted
countless hours trying to get to understand what I was doing wrong...

Anyways I still need to figure out how to get "Find and Install..." to work (nothing happens
after klicking on it) to install the Android plugin.

---

### Post by buntu_Geek on 2008-03-08
The reason is that , eclipse doesnt resolve the dependencies and we have to manually resolve those things... 
But i found out that its even tougher than it seems....(with the latest eclipse)
I dunno when is IBM going to develop a more smarter Eclipse...

---

### Post by Inxsible on 2008-03-08
I never use the version from the repos.

I have always installed the version from the eclipse.org website. All you have to do is download the appropriate version that you want (and for your OS architecture) and simply unpack it.

I currently have Eclipse Europa 3.3 installed and it works great.

---

### Post by excogitation on 2008-03-09
@Inxsible: Is your "Find and Install... working? - I mean does a window open after you click on it?

---

### Post by buntu_Geek on 2008-03-09
Btw.. you can check this how to for installing and updating plugin.. if you are doing any mistake unknowingly...

[http://open.ncsu.edu/se/tutorials/install_plugin/](http://open.ncsu.edu/se/tutorials/install_plugin/)

---

### Post by excogitation on 2008-03-09
> 1.1.1 Select Help > Software Updates > Find and Install. Select  Search for new features to install. Click Next.

The problem is, that when I click Find and Install... there should open a new window (I know from previous versions) but nothing happens.

> Anyways I still need to figure out how to get "Find and Install..." to work (nothing happens
after klicking on it) to install the Android plugin.

---

### Post by excogitation on 2008-03-18
Seems my Ubuntu was "broken" - at least I had some major
problems and now that I reinstalled it this problem doesn't
exist anymore.

A bit disappointing - but maybe in the future I'm able to
sort out such problems differently.

Seems my expectations towards linux were too high - in compoarison - I'm still using my XP I installed when I got this laptop about 4 years ago.

---

