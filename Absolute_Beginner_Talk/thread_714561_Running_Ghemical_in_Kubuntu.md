---
title: "Running Ghemical in Kubuntu?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by daimyo505 on 2008-03-03
Hello, I have a newbie question.

I am wanting to use the program Ghemical but I am running Kubuntu. I am not yet at a skill level where I can download packages, know the command sequence to run them in a shell, and get them to work.

First question: Can I run a GNOME program in Kubuntu 7.10 (KDE)?

Second question: I am trying to modify my source list so that I can have Adapt Installer find Ghemical and do all the dirty work for me. How do I point my source list to make sure I can install Ghemical?

Thanks in advance.

---

### Post by mgranet on 2008-03-03
1. Yes
2. Goto a terminal and type 

sudo nano /etc/apt/sources.list

Delete all of the '#'s in front of the words 'deb'. Save with Ctrl-O and exit with Ctrl-X

---

### Post by daimyo505 on 2008-03-03
None of my 'debs' were coded out. I even tried to add one, when I tried early. I found it in a link saying I just needed to add that to my source list.

```

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

#Added by ME 2008-01-26 to try and get DVDs to work
deb http://packages.medibuntu.org/ gusty free non-free
#Added by ME 2008-03-03 to try and get Gabedit, or Ghemical to work
deb http://mirrors.kernel.org/ubuntu gusty main universe multiverse

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free

```

---

### Post by hhhhhx on 2008-03-04
system>adminastartaion>software sourses> 
check everything in the first 3 tabs
then reload your sourses through the synaptic

---

### Post by mgranet on 2008-03-04
> **daimyo505 said:**
> None of my 'debs' were coded out. I even tried to add one, when I tried early. I found it in a link saying I just needed to add that to my source list.

```

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

#Added by ME 2008-01-26 to try and get DVDs to work
deb http://packages.medibuntu.org/ gusty free non-free
#Added by ME 2008-03-03 to try and get Gabedit, or Ghemical to work
deb http://mirrors.kernel.org/ubuntu gusty main universe multiverse

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

# Upstream Opera
# GPG key: 6A423791
deb http://deb.opera.com/opera etch non-free

```

Everything looks fine there. Did you go into Adept Manager and type in Ghemical into the searchbox? According to what I can see, it is in the Universe, which you have enabled.

---

### Post by mgranet on 2008-03-04
> **xhhux said:**
> system>adminastartaion>software sourses> 
check everything in the first 3 tabs
then reload your sourses through the synaptic

He's using Kubuntu.

---

### Post by hhhhhx on 2008-03-04
> **mgranet said:**
> He's using Kubuntu.
oops, my bad ssry :(

---

### Post by mgranet on 2008-03-04
> **xhhux said:**
> oops, my bad ssry :(

I can see how you could miss that bit. In comparison, there aren't many of us around.

[http://www.google.com/trends?q=Ubuntu%2C+Kubuntu](http://www.google.com/trends?q=Ubuntu%2C+Kubuntu)

---

### Post by daimyo505 on 2008-03-04
> **mgranet said:**
> Everything looks fine there. Did you go into Adept Manager and type in Ghemical into the searchbox? According to what I can see, it is in the Universe, which you have enabled.

Yeah, unfortunately it doesn't come up. 

I also tried to do a
```
sudo apt-get update
```
but still the package is not available  :(

---

### Post by mgranet on 2008-03-04
Hrm....This is an odd one. Have you tried ```
sudo apt-get install ghemical
```

---

### Post by mgranet on 2008-03-04
Here's an idea. How about you comment out all your sources, and paste in mine, and we can see what happens.

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
```

---

### Post by daimyo505 on 2008-03-04
Ok, after figuring out that I couldn't have the Adapt installer open when I tried the command

```
sudo apt-get install ghemical
```

It looked like it installed the packages but I don't see it in my start bar, or in the Adapt installer.

I will try the second suggestion in a minute.

---

