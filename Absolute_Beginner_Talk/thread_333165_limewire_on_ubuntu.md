---
title: "limewire on ubuntu"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-07
ok, i want to get limewire on my linux...i dont know how to un zip an rpm file, and i really dont know what else to do please help, o and i also forgot my super user password so if anybody can help me with that that would be appreciated and im pretty sure that i need that to install that alien archive manager thing for the rpm files](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by ajmorris on 2007-01-07
an rpm file is a self installing package. Just install it with an application like adept. Alternatively you could get frostwire from the repositories. It is basically the same application.

---

### Post by guysmiley25 on 2007-01-07
Im on a windows machine at the moment but don't install limewire install frostwire, same thing but easyer.

From memory you should just be able to in the terminal type

sudo apt-get install frostwire

There is a gudie somewhere with better instuctions i'll get back to you

---

### Post by guysmiley25 on 2007-01-07
Try [http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by Sniper99 on 2007-01-07
ok, now i have a really dumb problem, and i am not sure how to fix it.....i lost my super user password
:twisted:

---

### Post by ajmorris on 2007-01-07
I assume ur using gnome.

Go to system, administration, Users and Groups then right click on root in the box that comes up and go to properties. In that box there is a thing that says set password by hand. Just change the password there.

---

### Post by wildkarde on 2007-01-07
[http://www.ubuntuforums.org/showthread.php?t=240093&highlight=lost+password](http://www.ubuntuforums.org/showthread.php?t=240093&highlight=lost+password)

---

### Post by Sniper99 on 2007-01-07
i didn't lose my login password, i logged in as the system admin, i think, and i can log in but i cant do any su login
:twisted:

---

### Post by wildkarde on 2007-01-07
Did you set up a password for user 'root'?  If this doesn't sound familiar, chances are you didn't.  Try using sudo instead.  If it asks for a password, use your regular login password.  

```
sudo apt-get install frostwire
```

---

### Post by Sniper99 on 2007-01-07
ok, it ran a check on some tree dependencys but it came up with


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frostwire

---

### Post by Sniper99 on 2007-01-07
and just a by the way, is sudo the same as su, cuz i dont remember if i set a root password, i have tried every password i have ever used in the past, and none work so i doubt i even set one

---

### Post by Sniper99 on 2007-01-07
thank you so much i actually just downloaded the file from the website, and its installing as i write this, thank you, i hope it works......

---

### Post by Sniper99 on 2007-01-07
ok, i got frostwire, all fine and dandy, now i need to get java and i downloaded the self extracting file, and it says i need su permissions, am i just screwed right now or does sudo work

---

### Post by al1b1 on 2007-01-07
Download easy ubuntu and run. It will add the extra repostries

---

### Post by Sniper99 on 2007-01-07
how do you download the easy version...all i see is the link to download all the linux version

---

### Post by candtalan on 2007-01-07
> **Sniper99 said:**
> and just a by the way, is sudo the same as su, cuz i dont remember if i set a root password, i have tried every password i have ever used in the past, and none work so i doubt i even set one

Sudo is su in a protection box, allowing certain actions to be taken, one at a time. Su sign in allows everything to happen anywhere, unrestrained. Quite powerful, dangerous and usually unwise and unneccessary.

Ubuntu has su  (that is th eroot account) disabled by default, for easy good practice. It can be enabled, no problem.

---

### Post by wildkarde on 2007-01-07
this is what poster meant when he said easy ubuntu

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

### Post by guysmiley25 on 2007-01-07
Sorry I think I lead you in the wrong direction there. frostwire is not in the repositories. To get frostwire go

```

wget -c http://www.users.on.net/~stubby/FrostWire-4.10.9-2.i586.deb
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```

I found that at [http://ubuntuguide.org]("http://ubuntuguide.org")

In ubuntu insted of having a root/admin account somebody came up with the idea of sudo. so it you want to do anything as a root then all you have to do it run it wil sudo infount of it.

Also If your looking for a program, what you should first do is cheak [http://ubuntuguide.org]("http://ubuntuguide.org") and if not there cheak apt.

```
apt-cache search program-i'm looking-for
```

and if it comes up with somthing then

```
sudo apt-get install something
```

Hope that helps.

---

### Post by qamelian on 2007-01-07
> **guysmiley25 said:**
> Im on a windows machine at the moment but don't install limewire install frostwire, same thing but easyer.

From memory you should just be able to in the terminal type

sudo apt-get install frostwire

There is a gudie somewhere with better instuctions i'll get back to you

It's based on the same code but it is not the same thing and is not necessarily easier. In general, Frostwire is unusable on my laptop consuming 65-98% of my CPU. Limewire seldom uses more the 25% and is usually closer to 6%.

---

### Post by guysmiley25 on 2007-01-08
Strange, I get the opposite effect on my laptop. But I moved away from limewire/frostwire long ago and switched to gitfd.

---

