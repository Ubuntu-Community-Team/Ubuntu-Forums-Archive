---
title: "how i can create a directory in / by my own user?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-25
Hi
Thank you for reading my post
How i can create a directory inside / with my own user?
I can create one with sudo mkdir  dirName but it will not be accessable for my own user.
my user is legolas and directory name that i wan to create is legolasstuff

Thanks

---

### Post by louistan3 on 2007-05-25
i dont know exactly on how to use this command but i thnk u need ```
chown
```

u can read the man pages for it by doing ```
man chown
``` in the terminal

i thnk its probably sumthn like ```
sudo chown root:legolas dirName
``` hope this helps... :)

---

### Post by Outrunner on 2007-05-25
You don't need to acces it by your own user, you can use nautilus in super user mode

```
gksudo nautilus
```

or navigate to it in the terminal 
```
 cd /dir_name
```

---

### Post by Terl on 2007-05-25
> **legolas_w said:**
> Hi
Thank you for reading my post
How i can create a directory inside / with my own user?
I can create one with sudo mkdir  dirName but it will not be accessable for my own user.
my user is legolas and directory name that i wan to create is legolasstuff

Thanks

I am confused as to what you are trying to do.  You can make as many directories as you want within your home.  Are you wanting to make directories outside your ~ directory?  Why?  The more you mess around in sudo adding things the greater the risks....

---

### Post by tkjacobsen on 2007-05-25
sudo mkdir /legolasstuff
sudo chown -R legolas:legolas /legolasstuff

the '-R' option is for Recursively so not only the folder but also the content (although you think you have none this is necessary) will owned by legolas

---

### Post by sonofusion82 on 2007-05-25
> **Terl said:**
> I am confused as to what you are trying to do.  You can make as many directories as you want within your home.  Are you wanting to make directories outside your ~ directory?  Why?  The more you mess around in sudo adding things the greater the risks....
agreed. for most people migrating from windows, a common habit is to create directories in root directory. in linux, we usually create our directories in home directory unless it is some system files that needs to be shared between users

---

