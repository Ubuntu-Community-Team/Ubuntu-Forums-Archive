---
title: "Synaptic vs Aptitude vs Apt-get"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-05
So I've been reading around in the forums and lots of people use Synaptic, others use Aptitude and more use apt-get.

It seems like all 3 program are actually different package managers...

What are the differences between them? what are their strengths?  When should I use one and when should I definitely not use one?

---

### Post by hyper_ch on 2008-03-05
synaptic is gui based

apt-get and aptitude are cli based

aptitude does install also recommended software while apt-get only installs dependencies

---

### Post by DrMega on 2008-03-05
I like Synaptic. It is easy to use, I can search for stuff and see descriptions before I download, and I don't need to remember the command or know the package name in advance.

However, sometimes it is much quicker if you know the name of the package you want to just run apt-get. I guess its a matter of personal preference.

---

### Post by hyper_ch on 2008-03-05
apt-cache search music --> that will also give a list

and then if a specific file is missing, you can install apt-file and (and then build it's database:  sudo apt-file update)

---

### Post by anaconda on 2008-03-05
aptitude used to handle dependencies better than apt-get..

And synaptic is just a GUI that uses either of those.

it is much easier to install multiple packages using terminal than synaptic.. with synaptic you would have to search each package, but with terminal you can just copy/paste a loooong apt-get command and it will install everythin you need..

---

### Post by hyper_ch on 2008-03-05
> **anaconda said:**
> aptitude used to handle dependencies better than apt-get..
actually apt-get has improved a lot there... however if there are conflicting packages aptitude offers multiple options on how to "best" resolve them.

---

### Post by anaconda on 2008-03-05
> **hyper_ch said:**
> actually apt-get has improved a lot there... however if there are conflicting packages aptitude offers multiple options on how to "best" resolve them.

Yep, that is exactly why I said that aptitude **USED TO** handle dependencies better than apt-get..

Interesting that eg. in sidux it is recommended to use only apt-get and never aptitude!! So I guess apt-get has improved a lot  ;)

---

### Post by coolbrook on 2008-03-05
Ideally apt-get should return matches when you specify an incorrect package name.  Synaptic is boss.

---

### Post by vishzilla on 2008-03-05
I prefer Synaptic along with apt-get

---

