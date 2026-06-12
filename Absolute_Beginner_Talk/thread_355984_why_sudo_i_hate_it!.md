---
title: "why sudo? i hate it!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-02-07
man sudo is so annoying.

can anyone tell me how to get rid of having to use it every time i want to do something.

or

explain why its useful...

---

### Post by meng on 2007-02-07
I find it useful because if I log in as root I might "forget" that I'm root and do something catastrophic by accident. Also, I think theoretically a cracker has to guess both your username and your password in order to hack your box, whereas if the root password is enabled, you don't have to guess the username (it's root!) but only the password.

If you don't like sudo, you can set a root password (sudo passwd root), or else choose another distro.

---

### Post by Maestro23 on 2007-02-07
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jordanmthomas on 2007-02-07
I hate to sound like a jerk, but the very fact that you have to ask shows why sudo is helpful.
Running everything with absolute power is bound to lead to troubles.  One typo and you can be in an unhappy place.
By typing sudo in front you protect your computer from yourself.  Also, it protects your computer from some malicious friend walking by.

You can get rid of it a few ways.  a)  create a password for root and log in as root
```
sudo passwd root
```
or
b)  you can at least make it to where you don't have to type your password to use sudo.
```
sudo visudo
```
look in there...there should be a comment that tells you how to allow your user to run with elevated priviliges and not have to use a password.

Have a read here for more information:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)


**edit  -- I was beaten

---

### Post by aysiu on 2007-02-07
```
man sudo
``` *is* annoying. That's why I just use it without reading the manual.

If you dislike *sudo* that much, use just about any other Linux distro... or Windows.

Mac OS X and Ubuntu use *sudo*. Deal with it. Or leave it.

---

### Post by meng on 2007-02-07
> **aysiu said:**
> ```
man sudo
``` *is* annoying. That's why I just use it without reading the manual.
*Groan* :D (good one aysiu!)

---

### Post by bodhi.zazen on 2007-02-07
> **aysiu said:**
> ```
man sudo
``` *is* annoying. That's why I just use it without reading the manual.

If you dislike *sudo* that much, use just about any other Linux distro... or Windows.

Mac OS X and Ubuntu use *sudo*. Deal with it. Or leave it.

:lolflag: 

Now **that** is funny ...


> **jinxjinx said:**
> man sudo is so annoying.

can anyone tell me how to get rid of having to use it every time i want to do something.

or

explain why its useful...

LOL jinxjinx

Maestro23 gave you a good link.

In a nutshell : sudo increases security and protects you from yourself ;)

Give it some time, it will grow on you.

If you are going to do some heavy duty sys admin :

```
sudo -i
```

Just type exit when you are done :D

---

### Post by Stu09 on 2007-02-08
[http://xkcd.com/c149.html](http://xkcd.com/c149.html) :D

[img]http://imgs.xkcd.com/comics/sandwich.png[/img]

---

### Post by kevinlyfellow on 2007-02-08
:lolflag: thats awesome.

---

### Post by IYY on 2007-02-08
> If you dislike sudo that much, use just about any other Linux distro... or Windows.

Just make sure it's not Windows Vista, because that one asks for confirmation far more often than Ubuntu.

---

### Post by meng on 2007-02-08
> **IYY said:**
> Just make sure it's not Windows Vista, because that one asks for confirmation far more often than Ubuntu.
Yeah but it's not sudo, and you can turn it off (at your own risk of course).

---

### Post by greymongrey on 2007-02-08
> **bodhi.zazen said:**
> 

Give it some time, it will grow on you.

If you are going to do some heavy duty sys admin :

```
sudo -i
```

Just type exit when you are done :D
Very helpful info. Thanks.

---

### Post by kinson on 2007-02-08
> **Stu09 said:**
> [http://xkcd.com/c149.html](http://xkcd.com/c149.html) :D


LOL !!! This is hilarious :p 

> **meng said:**
> Yeah but it's not sudo, and you can turn it off (at your own risk of course).

True. Kinda funny how things have changed. I read its realli irritating, and keeps popping up for the most menial tasks. Heh.

Kinson

---

### Post by bodhi.zazen on 2007-02-08
> **jinxjinx said:**
> man sudo is so annoying.

can anyone tell me how to get rid of having to use it every time i want to do something.

or

explain why its useful...

Not to beat a dead horse ...

But your mentality has been fostered for years by windows and now even windows is changing.

Running all the time with full access to sys files is a very bad habit.

For example, lets say you want to change your network settings, with full access you change your system files without and "hassle". but by the same token any virus/malware has the same open freedom.

With Linux you can access your system files with sudo, but malware can not.

As I said, even windows is changing. There was a time when one booted a windows box without any type of login screen. Windows has users and administrators. Most windows users make the mistake of running as an administrator all the time, thus enabling easy access to malware.

Security is a fine balance between restricting access yet maintaining ease of use. sudo is one method and most Linux users appreciate it, although some prefer to disable sudo and su.

---

### Post by kinson on 2007-02-08
> **bodhi.zazen said:**
> 

As I said, even windows is changing. There was a time when one booted a windows box without any type of login screen. Windows has users and administrators. Most windows users make the mistake of running as an administrator all the time, thus enabling easy access to malware.
.

I remember laughing away when we could just get into Windows 98 systems by hitting the ESC key :lolflag: 

Btw, I love your signature, regarding the break ubuntu, and keep the both parts....so cool ! :D

Cheers,
Kinson

---

### Post by sdide on 2007-02-08
Hey, 

It depends.

I do not use sudo myself, I made a root password, and I log in as root when I do things that need root priviliges, that is what I am used to, and that is how I do it.

The important thing is : You should not be root unless you NEED to be root, (which is seldom.)

sudo is supposed to help with that,

if you get a bad habbit of logging in gdm with you root account and start browsers and whatnot using root, you could get in real trouble, 

Opening a shell and typing the wrong command as root can be fatal for your system and data,

To recap: 
You don't need sudo - at all.
if you want to get rid of it, do: 
```
sudo passwd root
```

and set the root password.
Then you can log in with ```
su -
```

and you'll be root, and you can do your thing and log out. 

However logging in as root, is NOT recommended!

---

