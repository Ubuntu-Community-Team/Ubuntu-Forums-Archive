---
title: "phone manager needed..."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-13
hi i have a w300i & k750 and i want to syncrinize with my ubutnu... 
any good application you might know or tested on your own for controling-syncronizing the phone through my pc?

---

### Post by hyper_ch on 2007-11-13
DON'T DO WHAT peodlelol  SAYS!

That will erase your whole homefolder!

---

### Post by Inxsible on 2007-11-13
> **someoneouthere said:**
> hi i have a w300i & k750 and i want to syncrinize with my ubutnu... 
any good application you might know or tested on your own for controling-syncronizing the phone through my pc?
[COLOR=Red] Yes don't do what peodlelol  says.[/COLOR]

when you say synchronize, what are you exactly looking for?
you can sync all your contacts etc using Evolution. If you are only looking to sync SMS and your phone book, you can use Wammu, which is pretty decent in backing up SMSes, call records and contacts etc.

---

### Post by someoneouthere on 2007-11-13
first i just did it....

what can i say???
 thank god i didn't have  a lot of things....
is there any way bring them back????

secondly i m looking for suncronazation with evolu...
sending reading im/ex-porting contracts,notes generally get the most of it....
i tried wammou but with the specific phone, the features are very limited....

---

### Post by Inxsible on 2007-11-13
> **someoneouthere said:**
> first i just did it....

what can i say???
 thank god i didn't have  a lot of things....
is there any way bring them back????

secondly i m looking for suncronazation with evolu...
sending reading im/ex-porting contracts,notes generally get the most of it....
i tried wammou but with the specific phone, the features are very limited....

Too bad ! I dont think you can get back everything from your home, especially since he had given a remove command of recursive and force (-rf) which means you lost all your settings and you probably won't be able to login if you shutdown your machine. You will have to probably re-install all of the apps again-- which is still not a guarantee that everything will work. Your best bet is to re-install Ubuntu.

Next time: try to find out what the command does, before executing it. Having said that, this is the first time, I have seen some miscreant on this forum. Normally, people here are nice and want to help you unlike peodlelol

What features are you looking for?

I use Wammu with my W810i and it does what I need.

---

### Post by hyperair on 2007-11-13
I actually find that Wammu's has more features than the PC Suites for Nokia and SE. For example, you can't send a message from your computer via PC Suite can you ;)

As for recovering your home partition, there's always testdisk, which is available in the repositories, but it isn't worth the effort if you don't have much files. Also you don't need to install Ubuntu again. It's just a destroyed home folder. It'll fix itself.

---

### Post by Inxsible on 2007-11-13
> **hyperair said:**
> I actually find that Wammu's has more features than the PC Suites for Nokia and SE. For example, you can't send a message from your computer via PC Suite can you ;)
+ 1 on that !! :)

---

### Post by someoneouthere on 2007-11-13
i agree that wammu is a top application,,, but comparing to the support list i propably have to buy another one....cell phone to get it fully running...

---

### Post by Inxsible on 2007-11-13
Unfortunately, you are not the only one that peodlelol got to

[http://ubuntuforums.org/showthread.php?t=611762](http://ubuntuforums.org/showthread.php?t=611762)

---

### Post by someoneouthere on 2007-11-13
he did it again now???

---

### Post by bulldog on 2007-11-13
> **Inxsible said:**
> Unfortunately, you are not the only one that peodlelol got to

[http://ubuntuforums.org/showthread.php?t=611762](http://ubuntuforums.org/showthread.php?t=611762)

If you see this again copy his post and report to the forum admin.[quote his post]

---

### Post by someoneouthere on 2007-11-13
what exacly this command does expect from deleting the home folder does it affect other things like permissions or tha admin rights???

---

### Post by Inxsible on 2007-11-13
> **bulldog said:**
> If you see this again copy his post and report to the forum admin.[quote his post]
I already did that !!

---

### Post by someoneouthere on 2007-11-13
this command exept from deleting the home folder does affect other regions like admin rights?

---

### Post by hyper_ch on 2007-11-13
```

sudo rm -rf ~/*

```

sudo --> do as superuser (as computer administrator)
rm --> remove
-rf --> "recursive" (go also into subdirectories and do the stuff there) and "force" don't ask for confirmation
~ --> that's the location of your home folder. If your user name is "tim" then it would be /home/tim
~/* --> apply the preceeding command to all files/folder in your user home

---

### Post by stchman on 2007-11-13
> **hyper_ch said:**
> ```

sudo rm -rf ~/*

```

sudo --> do as superuser (as computer administrator)
rm --> remove
-rf --> "recursive" (go also into subdirectories and do the stuff there) and "force" don't ask for confirmation
~ --> that's the location of your home folder. If your user name is "tim" then it would be /home/tim
~/* --> apply the preceeding command to all files/folder in your user home

That is one DANGEROUS command.

---

### Post by hyperair on 2007-11-14
I'd say be very thankful he didn't ask you to use 
```

sudo rm -rf /

```

Now THAT would be a tough one to fix. That one practically wipes your hard disk clean. I'm not sure about mounted partitions but there is a good chance that it will do that.

EDIT: Make that "hard disks". Every mounted one of them.

---

