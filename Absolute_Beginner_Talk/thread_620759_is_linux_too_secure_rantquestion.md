---
title: "is linux too secure? rant/question"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Lagos on 2007-11-23
ive been installing and setting up ubuntu on my system for the past week. i log in, put in my password, then go try to open an application, put in my password, type something into the terminal, put in my password.... and all the while im thinking, why is liunx trying to protect me from myself?  if im logged in as an administrator, shouldnt i be at least able to install/remove software without having to enter the password again, or install drivers?  hell, i tried to double click on a txt file (not even a linux scrip, just my own file), and ubuntu acted like i was about to start world war 3 and needed my lauch codes. 

is there a simple way to configure how often you have to enter in your password? you would assume that an administrator account would have some basic privileges to install new software and change a few settings using the gui, yet might need root access when editing a script file directly.

---

### Post by LaRoza on 2007-11-23
You are not logged in as an administrator. Enable the root account for that. I don't recommend it.

What are you doing so much that requires admin access?

---

### Post by LaRoza on 2007-11-23
> **Lagos said:**
> is there a simple way to configure how often you have to enter in your password? you would assume that an administrator account would have some basic privileges to install new software and change a few settings using the gui, yet might need root access when editing a script file directly.

You'll have to enter the password when every you want to do something as root. If you plan on running a bunch of programs or having to edit such files, you can use:

```

gksudo nautilus

```

Be careful, this will do everything as root.

---

### Post by LaRoza on 2007-11-23
Here, you might find this interesting:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Other distros do things differently.

---

### Post by Lagos on 2007-11-23
> **LaRoza said:**
> You are not logged in as an administrator. Enable the root account for that. I don't recommend it.

What are you doing so much that requires admin access?

well, besides just trying to setup my hardware, im downloading software to try out. almost everywhere i turn, i have to type in my password just to get basic things done. no one else uses the computer besides me, and im already doing "risky" things to script files just to get my hardware working. the only difference is that i keep having to sudo every 5min.  

gksudo nautilus... thats a good tip. thank you.

---

### Post by Paulmd on 2007-11-23
> **Lagos said:**
> ive been installing and setting up ubuntu on my system for the past week. i log in, put in my password, then go try to open an application, put in my password, type something into the terminal, put in my password.... and all the while im thinking, why is liunx trying to protect me from myself?  if im logged in as an administrator, shouldnt i be at least able to install/remove software without having to enter the password again, or install drivers?  hell, i tried to double click on a txt file (not even a linux scrip, just my own file), and ubuntu acted like i was about to start world war 3 and needed my lauch codes. 

is there a simple way to configure how often you have to enter in your password? you would assume that an administrator account would have some basic privileges to install new software and change a few settings using the gui, yet might need root access when editing a script file directly.


To answer your question: No, Linux isn't TOO secure. Up to Vista, window's non-admin users had very high privileges, and, by default, the administrator account is the one that gets used in a single user system.

This means that convenience trumps security: which is the root cause of most of the virus/spyware/malware nightmare that Windows users face. It's true that the virus writers aren't pressing Linux any near as hard as they are pressing Windows, but still, without the much higher level of security in Linux OSes, Linux too would be awash in viruses. 

If Linux either lets up it's guard, or becomes a big enough target for virus writers, then there will be a real test of EXACTLY how good Linux's security really is.


I'm of the opinion that you should just type sudo when you need it. Your machine will be all set up soon enough, and you won't have to type it very often after that.

---

### Post by tiachopvutru on 2007-11-23
Plus, if you think about it, installing softwares and drivers are all important stuffs. It's not like you're required to input your password everytime you open an application.

To expand on the Vista part, it's even more annoying... I forgot how often it pops up but apparently, all you do is click the button "OK" everytime a windows pop up when you install software (among a lot of other stuffs).  I'm pretty most people that use it just click OK just for the sake of it.

---

### Post by sstusick on 2007-11-23
If Linux didn't require you to input your password whenever you wanted to install a program...any program could install without your consent. Look at Windows...

---

### Post by Lagos on 2007-11-23
i agree that its good as a security feature, but it would be nice to just log in once with as root, do all the tweaking you need to do, and then go back to being a normal user. i guess i should/could make a root account for that.

---

### Post by sstusick on 2007-11-23
I like having to type in the password whenever I have to do something...I like knowing that I control the computer...it doesn't control me.

---

### Post by LaRoza on 2007-11-23
In Windows, I create a limited user account for myself to try to emulate the Linux behavior.

---

### Post by Paulmd on 2007-11-23
> **tiachopvutru said:**
> Plus, if you think about it, installing softwares and drivers are all important stuffs. It's not like you're required to input your password everytime you open an application.

To expand on the Vista part, it's even more annoying... I forgot how often it pops up but apparently, all you do is click the button "OK" everytime a windows pop up when you install software (among a lot of other stuffs).  I'm pretty most people that use it just click OK just for the sake of it.

IIRC, there's a few-second delay before the OK button can be clicked, to defeat the auto-OK reflex. Installs/running certian applications like regedit, and msconfig now require admin username and password.  Many lesser actions can be authenticated with lower credentials. Not sure if the rules vary between Vista Business (which I use at work), and  say Home Basic.

Better than it was. Not perfect.

---

### Post by ugm6hr on 2007-11-23
> **Lagos said:**
> and all the while im thinking, why is liunx trying to protect me from myself?

I think this is a common feeling.  I think the problem is Ubuntu is not protecting you from yourself, it is protecting you from malicious people on the web, in programs you've downloaded etc.

Requesting the password every 15 minutes ensures that an external person / website / script etc cannot do untold damage without knowing the password.

Having a root account potentially exposes you to risk during the entire time you are logged in as root.  So perhaps best not to visit any unknown websites or open any potentially suspicious files when logged as root.

I have a taskbar shortcut for* gksudo nautilus* for those occasions I want to do some fiddling...

---

### Post by starcannon on 2007-11-23
typing a password in is a very small price for the peace of mind that comes with things being built around the concept of security. just my 2 cents on it.

once you've done it awhile it isn't a big deal, just takes some getting used to, welcome to Ubuntu, enjoy, and my advice is, do not circumvent the security features, its one of the things that makes Linux great.:KS

---

### Post by kvonb on 2007-11-23
-

---

### Post by LaRoza on 2007-11-23
> **Lagos said:**
>  and all the while im thinking, why is liunx trying to protect me from myself? 

It is not protecting you from yourself. You can do anything you want to your home directory, that is yours to mess around with.

---

