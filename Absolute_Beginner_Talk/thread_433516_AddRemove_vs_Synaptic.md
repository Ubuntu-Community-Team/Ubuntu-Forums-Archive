---
title: "Add/Remove vs Synaptic???"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by katch22 on 2007-05-05
I have used both Applications>Add/Remove and System>Administration>Synaptic Package Manager to install things. Mostly I have installed from the command line with  "sudo apt-get install some_package". My question is: is there a difference in these different methods of installation? They are all drawing from the same repositories right? So what's the point in having so many ways to do it?

---

### Post by tommcd on 2007-05-05
Personally, I have never understood why we need add/remove when we have synaptic. Synaptic is a GUI front end for apt-get, and offers more options. I'm not sure if add/remove uses apt-get or something else. I always use synaptic. It is easy enough and lets you see dependencies, conflicts, suggested optional dependencies, etc.
Here is a basic explanation if the 2 methods:

[https://help.ubuntu.com/community/InstallingSoftware?highlight=%28remove%29%7C%28add%29#head-0b8eb2d741913dcf23a574e4a11b00c55df7cc59](https://help.ubuntu.com/community/InstallingSoftware?highlight=%28remove%29%7C%28add%29#head-0b8eb2d741913dcf23a574e4a11b00c55df7cc59)

---

### Post by akudewan on 2007-05-05
Yes, they are all using apt-get in the background. Its just a matter of convenience and what you like to use. Synaptic, for instance, allows you to easily search of packages, even using "Descriptions".

---

### Post by katch22 on 2007-05-05
> **akudewan said:**
> Yes, they are all using apt-get in the background. .

AHA! This is just what I suspected! Thank you for clearing it up! 

[QUOTE=tommcd] Personally, I have never understood why we need add/remove when we have synaptic. [/QUOTE]

Yes, my point exactly! It would make it much nicer/simpler for us new users if there were not such redundancies!

---

### Post by Famicommie on 2007-05-05
> **katch22 said:**
> AHA! This is just what I suspected! Thank you for clearing it up! 



Yes, my point exactly! It would make it much nicer/simpler for us new users if there were not such redundancies!

Add/Remove is meant for users with minimal PC experience. It is an easy, point and single click affair. Synaptic is more powerful, and the GUI can be intimidating to people who aren't confident about what they are doing.

---

### Post by ubnewbie2 on 2007-05-05
I have found a few times where add/remove can't locate the software I want (when I search) but synaptic does, so, as they are working from the same sources, I have to conclude add/remove's search is either buggy or inferior.

---

### Post by Rhaddad on 2007-05-05
I allways thought they were the same, just different UI

---

### Post by sorcererx84 on 2007-05-05
AFAIK Add/remove uses Synaptic in the background.

---

### Post by zekica on 2007-05-05
I think that add remove uses lists from files located in **/usr/share/app-install**, and that it then selects which packages are going to be installed from data in those files. That is the reasnon Add/Remove can't find all available software.

---

### Post by Pobega on 2007-05-05
The best package manager available is Aptitude, if you have the patience to learn how to use the terminal a bit (And aren't afraid of typing a bit). Aptitude works just like apt-get, except when it comes to removing packages it is smarter. You can aptitude from the command line just like you would apt-get:

aptitude install <whatever>
aptitude search <whatever>

You can also search all installed/broken/cruft files using Aptitude's search scheme:

aptitude search ~i | grep linux

Will show you all of the installed packages with linux in it's name.

Aptitude is a very useful tool, and if I were you I would read the documentation in /usr/share/docs/aptitude (It may be a capital A in aptitude, I forgot) for more information.

---

### Post by srt5 on 2007-05-05
One of the greatest things about Linux is that you have the ability to choose, nothing is forced on you. Add/Remove and Synaptic are two ways of doing the same thing. Add/Remove may be slightly easier for new users. :)

---

### Post by ubnewbie2 on 2007-05-05
> **srt5 said:**
> One of the greatest things about Linux is that you have the ability to choose, nothing is forced on you. Add/Remove and Synaptic are two ways of doing the same thing. Add/Remove may be slightly easier for new users. :)

Not if it misses when you search for the name of software that you need to install.  Doesn't help a new user to be told the software isn't available, when in reality it is - as a quick search in Synaptic soon reveals.

---

### Post by mcduck on 2007-05-05
> **ubnewbie2 said:**
> Not if it misses when you search for the name of software that you need to install.  Doesn't help a new user to be told the software isn't available, when in reality it is - as a quick search in Synaptic soon reveals.

If all (over 20 000) packages available in repositories were added to Add/remove, it would not be the easy tool it is now.

The idea is that Add/Remove provides easy way to install & remove selection of the most popular applications, while Synaptic is the more full-featured interface for apt-get.

I would not recommend using aptitude, as it can act a bit strange every now and then, and since 6.10 apt-get is able to do the same things, including removal of packages installed as dependencies. Apt-get is just lot more solid than aptitude is.

But, as mentioned, freedom of choice is important in Linux world. Use whatever tool you feel most comfortable with.

I usually use apt-get for quick installing of packages when I now exactly what I want, Add/Remove to search for nice games and useful software, and Synaptic for all serious package management tasks.

---

### Post by ubnewbie2 on 2007-05-05
> **mcduck said:**
> If all (over 20 000) packages available in repositories were added to Add/remove, it would not be the easy tool it is now.




I don't understand.  It has been said here that they are both using apt-get, so if apt-get knows about it, it's name is already in the local database from the repositories I have configured on my machine, downloaded last time I did an update. All add/remove has to do is search the data correctly.

---

### Post by srt5 on 2007-05-05
> **ubnewbie2 said:**
> Not if it misses when you search for the name of software that you need to install.  Doesn't help a new user to be told the software isn't available, when in reality it is - as a quick search in Synaptic soon reveals.

That is a valid point, however if you are completely new to the world of Linux (like I was a year ago), the Add/Remove program is a great tool for providing the user with basic functionality (just enough to get you up-and-running) without the need to even understand the concept of packages and dependencies. It's very intuitive and easily accessible through the Applications menu.

I agree that as a users understanding of Linux grows, then it is useful to learn about other ways of installing software, which is why I tend to use the command line/synaptic for installing most applications.

The point that I was trying to make though is that once you enter the world of Linux, you have the choice, so if Add/Remove meets your needs as a user and your comfortable with it, then great :) if not then you may feel that you have more control from using apt-get on the command line, aptitude or synaptic package manager, if you don't like either of them then you could try automatix whereas in Windows you're more or less stuck with the Windows installer or InstallShield.

---

### Post by mcduck on 2007-05-06
> **ubnewbie2 said:**
> I don't understand.  It has been said here that they are both using apt-get, so if apt-get knows about it, it's name is already in the local database from the repositories I have configured on my machine, downloaded last time I did an update. All add/remove has to do is search the data correctly.

It use apt-get to install things, but it doesn't search apt's database for available packages. It has it's own list of software, selected by Ubuntu developers, that contains some of the most popular applications. Like already said, it's not supposed to be a full-blown package management tool, only a nice & easy way to install some of the most common applications.

---

### Post by ubnewbie2 on 2007-05-06
> **mcduck said:**
> It use apt-get to install things, but it doesn't search apt's database for available packages. It has it's own list of software, selected by Ubuntu developers, that contains some of the most popular applications. Like already said, it's not supposed to be a full-blown package management tool, only a nice & easy way to install some of the most common applications.

But it has multiple choices for it's scope, and one of them is "ALL available applications" which is supposed to include 3rd party apps, all open source, plus the supported ubuntu apps.  The trouble is, it's not ALL the apps available, despite what it says.

---

### Post by srt5 on 2007-05-06
> **ubnewbie2 said:**
> But it has multiple choices for it's scope, and one of them is "ALL available applications" which is supposed to include 3rd party apps, all open source, plus the supported ubuntu apps.  The trouble is, it's not ALL the apps available, despite what it says.

In all fairness, the authors do acknowledge that their application doesn't meet all of the advanced needs. This is a section of text which is taken directly out of the Help file under the Introduction heading.

> Only simple additions and removals can be performed with Install and Remove Applications. For more advanced needs, the Synaptic Package Manager is used.

I guess the Add/Remove program just wasn't designed to install everything. In fact, I think this is a good thing since giving a new user a choice of ALL packages might be quite overwhelming. At least this way they can install most of the most common applications without even having to understand the concept of dependencies. 

As I mentioned in a previous post, I guess the important thing is that you are comfortable using whichever program you choose, so if Add/Remove meets your needs then great, if not, then Synaptic is available just like the authors suggest.

---

