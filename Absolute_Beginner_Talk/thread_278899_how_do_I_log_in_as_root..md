---
title: "how do I log in as root."
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by timmins on 2006-10-17
is it possible to log onto my computer as "root" and change the preferences of my reformatted drive (BTW, I formatted it to ext 3, was that right?), I wan't to change the preferences so I can access it when I'm logged in. I try to log onto ubuntu on startup but when I type in the password, I get a message that says "the system administrator cannot log in from this page".what is the easiest way to change the permissions on this HD.

---

### Post by ciscosurfer on 2006-10-17
Take a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by girishv on 2006-10-17
sudo chmod 777 /your_directory
please dont forget to change 777 to some thing you want.

you can not login to ubuntu systm as a root (by default), but if you really want to be a root, you can use
sudo su -

the sudo password is the same as the password of the first user you added.

Girish

---

### Post by timmins on 2006-10-17
I'm sorry guys, I'm a real noob at this. I see both of your instructions and they both kinda look like chinese (I know I'm an idiot, but I need help)

If someone would give me a step by step guide of what to do, this idot would forever be in your debt.

I want to open my "computer" browser, under "places". I then want to right cligh on a newly formatted HD, click on the permissions tab and change the permissions so I can access and write to the harddrive as a user.

plese help, I'm about to rip my hair out, with all of these commands that I don't know what to do with.

---

### Post by drummer on 2006-10-17
> **girishv said:**
> sudo chmod 777 /your_directory
please dont forget to change 777 to some thing you want.

Ahh... DON'T do that, permissions are there for a reason. Read through the link posted above and it tells you in there how to enable the root account if you want to.

---

### Post by timmins on 2006-10-17
Example #1

sudo chown bob:bob /home/bob/*

Example #2

sudo /etc/init.d/networking restart

    *

      NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.



this is retarded.... chown WTF, man I'm really beginning to get frustrated.

could somebody give me a little guide please. I mentioned what I wanted to do in my last post.

---

### Post by monktbd on 2006-10-17
> **timmins said:**
> 
this is retarded.... chown WTF, man I'm really beginning to get frustrated.


it is not retarded it is just different to what you are used to. :).

> 
I want to open my "computer" browser, under "places". I then want to right cligh on a newly formatted HD, click on the permissions tab and change the permissions so I can access and write to the harddrive as a user.


ok press alt-f2 and write gksudo nautilus, then you can do it with the nautilus window that opens. but close it after you have changed the permissions.

another way would be to use the command line interface (terminal) to do so, it actually goes faster like that:

> 
sudo chown bob:bob /myNewHDFolder


so what does this do?
sudo gives you administrator rights for the following command.
the following command is chown which means only change owner.
the bob:bob you have to replace with your username there, actually they describe the group and the user you want to change the ownership of the folder to. username and groupname are usually the same for a given normal user.
then all you need to add is the folder you want to change the owner of. which is /myNewHDFolder. 
actually if you are on the commandline and you dont know exactly what the directory name is just hit tab once or twice to see the options.

like write 
> 
cd /hom

and hit the tab key to get it completed to cd /home.
hit tab again and you will see possible choices coming up. like maybe bob if you have a user like that.
edit: cd is actually for switching directories.

---

### Post by TheWizzard on 2006-10-17
on the issue of root permissins, please do read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

> I want to open my "computer" browser, under "places". I then want to right cligh on a newly formatted HD, click on the permissions tab and change the permissions so I can access and write to the harddrive as a user.

am i correct that you added an extra hdd? 
if that's the situation, you'll want to edit fstab. 
for permissions, make sure you belong to the group "users".

---

### Post by yman on 2006-10-17
take a look at this:
[http://www.ubuntuforums.org/showthread.php?t=275551](http://www.ubuntuforums.org/showthread.php?t=275551)

someone had the same problem as you.

---

### Post by caravel on 2006-10-17
To log in as root you have to enable the root password.

```
sudo passwd root
```

Give it a password and then log in.  It's your computer to break as you will.  Personally I haven't found anything yet that I can't do using sudo, which I happen to like the whole idea of alot better than being logged in as the root user.  You'de be better off heeding the advice of the previous posters.

---

### Post by aysiu on 2006-10-17
Please read this link, which people have posted more than once already:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

If you must make *graphical* root changes, read this instead:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

There's absolutely no need to log in as root graphically.

---

### Post by timmins on 2006-10-17
> **yman said:**
> take a look at this:
[http://www.ubuntuforums.org/showthread.php?t=275551](http://www.ubuntuforums.org/showthread.php?t=275551)

someone had the same problem as you.

I trird dphilips and aysiu suggestions both times, I get the message "the permissions cannot be changed".The HD I'm trying to modify is the master drive, does that have anything to do with it?

---

### Post by aysiu on 2006-10-17
Generally, changing permissions is a bad idea and can render your system unusable. The second link I posted will let you modify any file without changing the permissions.

---

