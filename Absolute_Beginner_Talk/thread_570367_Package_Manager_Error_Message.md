---
title: "Package Manager Error Message"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-10-08
I am getting the orange icon that I need to update my software, but when I click on it I get this message: Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 44 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I am new to Linux and do not understand this message and what I must do to correct the problem.

Your assistance will be appreciated.

---

### Post by hyper_ch on 2007-10-08
Please post the output of:

```

cat /etc/apt/sources.list

```

---

### Post by explorer716 on 2007-10-08
This is the output from entering:  "cat /etc/apt/sources.list"



## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.





## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

---

### Post by hyper_ch on 2007-10-08
Now have a look at that list. You see what is different?

---

### Post by wormser on 2007-10-08
> **explorer716 said:**
> “deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

That line looks like it is the problem.  Remove the " from around the rest.

---

### Post by explorer716 on 2007-10-08
Help!! I am clueless as to what the two previous messages are telling me.

---

### Post by PmDematagoda on 2007-10-08
Just edit the sources.list file by removing the " s around:-

```
“deb http://www.getautomatix.com/apt feisty main”
```

---

### Post by explorer716 on 2007-10-08
I am really new at this.  Can you please give me more detailed instructions on how to correct this problem?

---

### Post by PmDematagoda on 2007-10-08
Ok, first open up the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then once you get the source file for editing just do the changes as you would do with a text document. Take it easy as you are not going to destroy your system by making a mistake here, and mistake done can be easily fixed.

After you've done the necessary changes, save the file, close it or you may keep it open, no problem. And then try update manager again.

---

### Post by hyper_ch on 2007-10-08
and why do you want to use automatix anyway? It can break your system and it's not really needed.

---

### Post by PmDematagoda on 2007-10-08
> **hyper_ch said:**
> and why do you want to use automatix anyway? It can break your system and it's not really needed.

Yup, agree with you there, I don't use Automatix at all for installing stuff, use the repos or compile them myself, though I do keep Automatix just incase:).

---

### Post by explorer716 on 2007-10-08
I removed the line about "Automatrix" and it seems to have corrected the problem.

Thanks to all for your help.

---

