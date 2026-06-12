---
title: "Few beginner questions"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by karuzo on 2008-02-01
Hello all,
   Originally I intended to post this thread on one subject, but as I was typing I remembered I have a few more I am after answers for and decided to concentrate them into one post:

- I was wondering: Is there anyway to modify the shortcuts directory in the start menu for any program? I've installed a program that did not create a shortcut under the 'Games' and I'd like to add it myself. Further more, is it possible to add sub-directories under 'Games'? Do you need root for that? If so, how? All I know is 'sudo su' in terminal which as I understand will not give me the ability to root manage things under 'X', or am I wrong? DO I need to log into ubuntu as root for such modifications?

- Regarding uninstalling programs - programs I did NOT install via 'Add/Remove' - how do you uninstall them? Can you simply delete the associated directories?

- I basically kept ubuntu 7.10 at its default appearance (though I enabled 3d effects). It seems that over time, from the moment I logged in, it takes a while for the desktop to appear (about 20 seconds which was not like that after a clean install). Anyone had experienced something similar? Is it normal behavior?

Thanks,
    Doron

---

### Post by emarkd on 2008-02-01
1.  Be very careful as root.  Linux won't hold your hand and will do whatever you tell it, even if it's a bad idea.  You can add shortcuts to your menu by right-clicking and selecting Edit Menus.  You don't want to create subdirectories and change where things are installed.  While Windows groups all the files for a program together, Linux groups like files together.  For example, all the libraries go together, all the docs go together, the binaries go together, and so on.

2.  Run System > Administration > Synaptic and search for them.  They should be there.

---

### Post by jan quark on 2008-02-01
or you can use terminal commands

for packages got from synaptic,  use
```

sudo apt-get remove --purge name of package
```
for  downloaded packages  use 

```
sudo dpkg -r name of package
```

---

### Post by PeterJS on 2008-02-01
> **karuzo said:**
> Hello all,
   Originally I intended to post this thread on one subject, but as I was typing I remembered I have a few more I am after answers for and decided to concentrate them into one post:

- I was wondering: Is there anyway to modify the shortcuts directory in the start menu for any program? I've installed a program that did not create a shortcut under the 'Games' and I'd like to add it myself. Further more, is it possible to add sub-directories under 'Games'? Do you need root for that? If so, how? All I know is 'sudo su' in terminal which as I understand will not give me the ability to root manage things under 'X', or am I wrong? DO I need to log into ubuntu as root for such modifications?

There's a menu Editor at System > Preferences > Main menu

Here's the help page on sudo/root privileges. Root logins are explicitly disallowed by default, in addition to the root account being locked, because login in as root is generally a bad idea, and there's generally a much better way to do what you need to.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> 
- Regarding uninstalling programs - programs I did NOT install via 'Add/Remove' - how do you uninstall them? Can you simply delete the associated directories?

That's the thing of it, there are no associated directories to delete. In linux files are organized by function not which program they are associated with. See the where are my files link in my sig for more info.

---

### Post by karuzo on 2008-02-03
> **emarkd said:**
> 1.  Be very careful as root.  Linux won't hold your hand and will do whatever you tell it, even if it's a bad idea.  You can add shortcuts to your menu by right-clicking and selecting Edit Menus.  You don't want to create subdirectories and change where things are installed.  While Windows groups all the files for a program together, Linux groups like files together.  For example, all the libraries go together, all the docs go together, the binaries go together, and so on.
So does that mean if I want to remove 'Dark Horizon' I need just to delete all folders associatd/named with the game's name?

> **emarkd said:**
> 2.  Run System > Administration > Synaptic and search for them.  They should be there.
Well - I installed 'Dark Horizon' NOT through the add/remove and it is NOT in the Synaptic.
Thanks,
    Doron

---

### Post by karuzo on 2008-02-03
> **jan quark said:**
> or you can use terminal commands

for packages got from synaptic,  use
```

sudo apt-get remove --purge name of package
```
for  downloaded packages  use 

```
sudo dpkg -r name of package
```
Thanks jan quark. What would be the package name though? Is it the name of the file I executed to install? What would it be in the case of 'Dark Horizon' for example?
Thanks,
    Doron

---

### Post by karuzo on 2008-02-03
> **PeterJS said:**
> There's a menu Editor at System > Preferences > Main menu

Here's the help page on sudo/root privileges. Root logins are explicitly disallowed by default, in addition to the root account being locked, because login in as root is generally a bad idea, and there's generally a much better way to do what you need to.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


That's the thing of it, there are no associated directories to delete. In linux files are organized by function not which program they are associated with. See the where are my files link in my sig for more info.

I should have figured out regarding the menu editing. Thanks.
So, to remove a program I need to figure its functions or what? I am not sure I am following.
Thanks,
    Doron

---

### Post by wesley_of_course on 2008-02-03
This post by jdong  helped my log-in time considerably - [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

log-in to desktop was indeed faster ;  Gutsy 

Hope this helps .

---

### Post by PeterJS on 2008-02-03
> **karuzo said:**
> I should have figured out regarding the menu editing. Thanks.
So, to remove a program I need to figure its functions or what? I am not sure I am following.
Thanks,
    Doron

Removing them from the menu or completely removing programs from the system?

---

### Post by karuzo on 2008-02-03
> **PeterJS said:**
> Removing them from the menu or completely removing programs from the system?
Removing completely, like world of padman
Thanks,
    Doron

---

### Post by karuzo on 2008-02-03
> **wesley_of_course said:**
> This post by jdong  helped my log-in time considerably - [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

log-in to desktop was indeed faster ;  Gutsy 

Hope this helps .

Thanks for pointing this. However, it seems as there is a risk with the terminal commands if mistyped. I gue
ss I can wait a bit and/or 'suffer' the longer log-in process.
Thanks,
     Doron

---

