---
title: "[SOLVED] Question about Skype"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-05
I'm trying to install Skype on a spare computer which has 6.06

After downloading the Skype file I get this error when trying to install it:-

ERROR  Dependancy is not satisfiable:   libasound2

Does that mean I'm missing a file, or what?

---

### Post by quandary on 2007-12-05
Yes, actually you're missing a library.

Go to console and type:
sudo apt-get install libasound2

Then retry installing Skype.

---

### Post by wormser on 2007-12-05
Yes, it means you are missing a file.  Skype is dependant on libasound2 for it to work.  How are you installing Skype?  Did you download a .deb or from the repositories?  A year ago Skype from the repositories had issues and it was best to download the .deb from Skype.com.  That may have changed.  The following command will install the libasound2 package.

```
sudo apt-get install libasound2
```

---

### Post by mikewhatever on 2007-12-05
I do not think you can install the latest stable version of skype on 6.06. The software is too new. Medibuntu repository has the appropriate version.
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by quandary on 2007-12-05
> **mikewhatever said:**
> I do not think you can install the latest stable version of skype on 6.06. The software is too new. Medibuntu repository has the appropriate version.
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

don't know about 6.06, but works excellently on 7.10

---

### Post by mikewhatever on 2007-12-05
> **quandary said:**
> don't know about 6.06, but works excellently on 7.10

L Campbell has 6.06, so who cares whether is works on 7.10.

---

### Post by L Campbell on 2007-12-06
> **mikewhatever said:**
> L Campbell has 6.06, so who cares whether is works on 7.10.

Thanks for the help here.

I tried everyone's suggestions but nothing worked.

Synaptic shows that I have the ' libasound2 ' files and, despite even  re-loading them, I'm still getting the error.

What I ended up doing was to install Gizmo.  I guess it uses other files as I had no problem getting it to work.

Kind regards.

---

### Post by a.v.l on 2007-12-06
> **L Campbell said:**
> Thanks for the help here.

I tried everyone's suggestions but nothing worked.

Synaptic shows that I have the ' libasound2 ' files and, despite even  re-loading them, I'm still getting the error.

What I ended up doing was to install Gizmo.  I guess it uses other files as I had no problem getting it to work.

Kind regards.

I installed it on 6.06 using Automatix without trouble. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by quandary on 2007-12-21
> **mikewhatever said:**
> L Campbell has 6.06, so who cares whether is works on 7.10.

He anyway shouldn't use old software, so what about the following:
```

user@desktop:~$ sudo apt-get update
user@desktop:~$ sudo update-manager -c
user@desktop:~$ sudo apt-get dist-upgrade

```

---

### Post by ShelJ on 2007-12-22
> **quandary said:**
> don't know about 6.06, but works excellently on 7.10
I tried the Medibuntu.org suggestion and it worked for me.  I'm using Xubuntu Gutsy, so I had tio replace "feisty" w/ "gutsy" in the cmd line, but it still worked.

---

