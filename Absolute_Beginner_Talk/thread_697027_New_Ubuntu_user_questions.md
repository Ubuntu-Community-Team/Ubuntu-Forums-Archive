---
title: "New Ubuntu user questions"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by garygib35 on 2008-02-14
I'm completely new to Linux and am making this transition from Windows OS with that in mind I know there is a learning curve.

Recently I installed Ubuntu because of the positive comments so many people made about it's ease and windows like "feel".  Now that I've used it for awhile I have some questions.  I would like to install a program that will meet or exceed ITunes capability.  Is such a program available?

I've noticed I can't install any available Linux program that shows up on the "available program install list" because of "compatibility" issues, why is that?  Forgive my ignorance but if it's on the list shouldn't I be able to install it and if I can't install it then why is it on the list?  Where can I get a list of programs that are compatible with Ubuntu and when I attempt to install a program from that list, I don't have to search out and update a bunch of other programs so the one that I'm actually trying to install will install?

I hope all that makes sense.

---

### Post by LowSky on 2008-02-14
what list are you talking about? the one from the menu Add/Remove?

as for iTunes, try banshee, or amorok, or exaile

---

### Post by PeterJS on 2008-02-14
> **garygib35 said:**
> I'm completely new to Linux and am making this transition from Windows OS with that in mind I know there is a learning curve.

Recently I installed Ubuntu because of the positive comments so many people made about it's ease and windows like "feel".  Now that I've used it for awhile I have some questions.  I would like to install a program that will meet or exceed ITunes capability.  Is such a program available?

Amarok is highly recommended and covers pretty much everything iTunes does, if you want to stick with the Gnome look and feel try Rhythmbox.

> 
I've noticed I can't install any available Linux program that shows up on the "available program install list" because of "compatibility" issues, why is that?  Forgive my ignorance but if it's on the list shouldn't I be able to install it and if I can't install it then why is it on the list?

Not sure which list you're looking at, is it the add/remove programs list?

> 
 Where can I get a list of programs that are compatible with Ubuntu and when I attempt to install a program from that list, I don't have to search out and update a bunch of other programs so the one that I'm actually trying to install will install?


 You don't have to handle installing dependant programs by hand, the package system does that for you. In windows each application is fully stand alone, and doesn't depend on any others. But in linux to conserve disk space, and make the process of sharing libraries more efficient, each package only contains the files directly related to it, and a list of which packages contain the other files that it needs.

For installing things one of the best methods is using Synaptic Package Manager, which can be found at System > Administration > Synaptic Package Manager.

The complete guide to installing things also has good directions about enabling extra software sources which may be the issue.
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mtgrocks04 on 2008-02-14
I also recommend Amarok for a media player, It is a great program.   As for the installing problems it is possible that the repositories are not active.

---

### Post by gniltaws on 2008-02-14
I like [Songbird]("http://songbirdnest.com") because it is available on Linux as well as Windows and MacOS.  I just like to be able to use the same program on multiple platforms.  

Here are some directions for installing it: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

Also, do some research about the apt-get command.  This is one of the best things about Linux.

-Todd

---

### Post by billgoldberg on 2008-02-14
> **gniltaws said:**
> I like [Songbird]("http://songbirdnest.com") because it is available on Linux as well as Windows and MacOS.  I just like to be able to use the same program on multiple platforms.  

Here are some directions for installing it: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

Also, do some research about the apt-get command.  This is one of the best things about Linux.

-Todd

Note that songbird is still in developers version, so it might be a bit unstable to use as default.

For 2.

Strange.

follow me on this:

Instead of trying to install it using add/remove, try using apt-get in the terminal (applications -> accessories).

Lets say you want to install banshee.

give in this code:

```
sudo apt-get install banshee
```

then it will list the error.

Copy that error here

note: every program in the repositories (the standard ones) is compatible for your ubuntu install.

---

