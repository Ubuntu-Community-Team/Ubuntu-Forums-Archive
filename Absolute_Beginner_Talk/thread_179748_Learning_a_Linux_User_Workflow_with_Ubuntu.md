---
title: "Learning a Linux User Workflow with Ubuntu"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Unoone on 2006-05-20
I'm not a constant Linux user so I often have trouble in the area of installation of packages or compiling software. I have often wondered how one comes an expert at Linux configuration. Do they use a Linux computer 24/7? Do they read the right Linux books, visit the right websites or network with other users? 

A Linux user is not an average computer user such as Windows user or a Mac user. A Linux user has to be aware or be made aware of many things seen and unseen in their operating system. Depending on the distribution that they use, a Linux user may have many documentation resources or very few. Often these resources are not from an official source or updated regularly. 

How does a new Linux user approach using Linux properly without any misconceptions? Before I used Linux, I thought that it was used mostly by computer whiz types. Now I see that this is not the case after talking to a wide variety of users like myself. However I still muddle through Linux task. I get stumped at many points due to a lack of general clarity areas of documentation. I wonder if a successful mastery of Linux is based on more chance than dedicated research of available information.

If you are a successful Linux/Ubuntu user can you give us new users any tips based on your progress?

1- Did you have previous Linux experience before using Ubuntu?

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was your progress based on trial and error?

3- Do you just have a knack for learning new tech? Did your previous experience as a &#8220;power&#8221; Windows or Mac user prepare you for Linux?

4- Did you read good Linux books and talk to the right Linux people?

If you answer these questions can you state your learning resources and web links please. Also can you add the question number  &#8220;-1&#8221; that refers to your Linux/Ubuntu experience? Thank you for your comments. Your participation in this thread may help new Linux users like myself to make better progress with Ubuntu.

---

### Post by adamkane on 2006-05-20
As far as Ubuntu is concerned, it started with some knowledgeable enthusiasts and this forum. 

The first users put together some Howtos for the thoroughly confused, and then the ball just started rolling. Everyone copied each others work. 

This is the first forum, where I've been able to contribute, because there were enough examples to get the idea of something, and then fill in any gaps in knowledge.

Areas to look at to get started with Linux/Ubuntu:

Howtos that use bash scripts.
Nautilus-scripts for Gnome.
Service menus for KDE.

A little more advanced:
Perl/Python scripting.
Apache/MySQL/PHP content management systems like Drupal.

---

### Post by Mustard on 2006-05-20
Looking at the options in the poll I think I could just about tick them all, except option 1.

I was a windows 'power user' with no linux experience.  My initial learning experience with Ubuntu was very much trial and error until such a time as I became aware of the most reliable places to find information.  The greatest assistance to me was the availability of the IRC support channel #ubuntu on irc.freenode.net.  From there I was directed to the right sources of information, shown some of the 'do's and don'ts' of using Ubuntu, and was given some exposure to experienced linux users who could guide me during my initial period of confusion.

I recall initially reinstalling Ubuntu at least 4-5 times, due to breaking my installation while attempting to configure or troubleshoot problems on my own, without the right information at hand.  There was also some ignorance on my part as to what was the best way to set up my installation in terms of partitioning, what software to use, what sources to get software from and the correct methods of configuring permissions and ownership.  For quite a while I had two installs of Ubuntu, one that I used for tinkering with and the other one that I never touched unless I knew what I was doing.  This at least allowed me to have a working installation at all times.  It certainly saves me a lot of pain to do it this way, as I really hate destroying a perfectly good installation by pushing the envelope too far and then having to start from scratch again.

Undoubtedly the best learning experience for me was to be mentored by experienced linux users on the IRC support channel. Along with this I kept my own 'database' of information such as lists of helpful links, copies of tutorials etc on my machine that were locally accessible rather than requiring me to search them out each time I needed them.

I think I also brought some good skills with me from my windows 'power user' days, in that I knew of the existence of wikis, IRC support channels, and forums.  Many novice windows users that I know don't really know how to find information online, or which places to go looking.  They might type something into google, but thats not always helpful unless you know what types of resources you are after.  I started with the forums, as I knew that was going to be the place where I could get that first kick start in terms of finding information.  From there I wanted to get more 'real time' assistance, so I found the IRC support channel.  The other factor that probably doesn't get mentioned much is that I have a lot of time to learn linux.  More time than most people would want to spend learning an operating system. :)

My links for information would be,
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

[http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)   
(The search function in the forum is invaluable. The tips and tricks section of the forum was an excellent resource.)

[http://help.ubuntu.com/](http://help.ubuntu.com/)
(Official Starters Guide, also available in the Help menu option in the System menu)

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)   (the newest incarnation of the Ubuntuguide (Breezy Badger)

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)  (The Ubuntu Document Storage Facility, which stores useful tutorials that were created in the forums)

[http://www.google.com/linux](http://www.google.com/linux)  (the linux specific google search function for general information on linux)

[http://packages.ubuntu.com](http://packages.ubuntu.com) (the list of all packages available in Ubuntu)

In IRC (**channel:** #ubuntu **server:** irc.freenode.net)

Ubotu, the IRC help bot, can answer many common questions for example, typing any of these phrases into the #ubuntu help channel will trigger ubotu to give you the facts on that information..

!restricedformats
(information on playing mp3s, DVDs, Java, Flash)
!java
!javadeb
!repos
(information on enabling repositories and copies of default sources.list)
!easysource
(a web tool for creating a localised sources.list that uses local mirrors)

as well as many more factoids.

Localised help was found through reading the many manuals that are installed when you install software through apt-get/Synaptic, using the 'man' command in the terminal..

Examples..
```
man apt-get
```
```
man cd
```
```
man pwd
```
```
man mv
```
```
man cp
```

This is a picture below of my little wiki database of information I have compile using the the Zim desktop wiki software. :)
[[IMG]http://img68.imageshack.us/img68/4351/wiki7mn.th.png[/IMG]](http://img68.imageshack.us/my.php?image=wiki7mn.png)

---

### Post by macdo on 2006-05-20
I came to Ubuntu from Debian. I managed to upgrade to Debian Sid (the unstable version of Debian is always called Sid, because Sid breaks toys) - and Sid did his worst, so I had to reinstall, at a time when Ubuntu was making waves. Not being one to avoid a perfectly good band-wagon, I jumped on... 
The community is what has kept me sane.
I'm fortunate in that I have a geek brother, who's only a phone call away - but I don't often call him any more :)
The other thing that really helped me was knowing what to google for - and having two PCs, so that I **could** google when it all went pear-shaped. 

And yes, I did have prior experience of Windows. My first linux lasted for exactly 37 minutes - my USB cable modem wasn't playing nice at all. It took me about three years to try again, and I've never looked back.

The only linux book I've got is 'Linux for  Dummies' (in French: Linux Pour Les Nuls), such an old edition that it doesn't even recognise the existence of KDE. The most useful thing about it (and the only part I ever use) is the list of commands...

---

### Post by Unoone on 2006-05-20
Thanks everyone for responses so far. I am a Windows power user myself. My first taste of Linux was with Knoppix Livecd's, next Mandrake installs, then Mandriva and now Ubuntu. My Windows experience helped me to understand partitioning and operating system file structures and commands, etc. I experienced how easy it is with Linux to get access to development tools. This is my main reason for using Linux. The Ubuntu community is very helpful. I still have so much to learn. I will check out the resources that you listed they are very helpful. I hope that other users share their own experiences here.

---

### Post by Ozitraveller on 2006-05-20
[QUOTE=Unoone]I'm not a constant Linux user so I often have trouble in the area of installation of packages or compiling software. I have often wondered how one comes an expert at Linux configuration. Do they use a Linux computer 24/7? Do they read the right Linux books, visit the right websites or network with other users? 

A Linux user is not an average computer user such as Windows user or a Mac user. A Linux user has to be aware or be made aware of many things seen and unseen in their operating system. Depending on the distribution that they use, a Linux user may have many documentation resources or very few. Often these resources are not from an official source or updated regularly. 

How does a new Linux user approach using Linux properly without any misconceptions? Before I used Linux, I thought that it was used mostly by computer whiz types. Now I see that this is not the case after talking to a wide variety of users like myself. However I still muddle through Linux task. I get stumped at many points due to a lack of general clarity areas of documentation. I wonder if a successful mastery of Linux is based on more chance than dedicated research of available information.

If you are a successful Linux/Ubuntu user can you give us new users any tips based on your progress?

1- Did you have previous Linux experience before using Ubuntu?

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?

3- Do you just have a knack for learning new tech? Did your previous experience as a “power” Windows or Mac user prepare you for Linux?

4- Did you read good Linux books and talk to the right Linux people?

If you answer these questions can you state your learning resources and web links please. Also can you add the question number  “-1” that refers to your Linux/Ubuntu experience? Thank you for your comments. Your participation in this thread may help new Linux users like myself to make better progress with Ubuntu.[/QUOTE]

1- Did you have previous Linux experience before using Ubuntu?
[COLOR="Red"]Yes, I came from Debian and still use Debian along with a long list of other distros I have tried, and also SCO Unix.[/COLOR]

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?

No, if/when I need to know something I do the research.

3- Do you just have a knack for learning new tech? Did your previous experience as a “power” Windows or Mac user prepare you for Linux?

Yes. No, see above.

4- Did you read good Linux books and talk to the right Linux people?

Yes, I do read linux books and articles, and a lot of other stuff as well. I find these forums an excellent resource too.

---

### Post by Ozitraveller on 2006-05-20
[QUOTE=Unoone]I'm not a constant Linux user so I often have trouble in the area of installation of packages or compiling software. I have often wondered how one comes an expert at Linux configuration. Do they use a Linux computer 24/7? Do they read the right Linux books, visit the right websites or network with other users? 

A Linux user is not an average computer user such as Windows user or a Mac user. A Linux user has to be aware or be made aware of many things seen and unseen in their operating system. Depending on the distribution that they use, a Linux user may have many documentation resources or very few. Often these resources are not from an official source or updated regularly. 

How does a new Linux user approach using Linux properly without any misconceptions? Before I used Linux, I thought that it was used mostly by computer whiz types. Now I see that this is not the case after talking to a wide variety of users like myself. However I still muddle through Linux task. I get stumped at many points due to a lack of general clarity areas of documentation. I wonder if a successful mastery of Linux is based on more chance than dedicated research of available information.

If you are a successful Linux/Ubuntu user can you give us new users any tips based on your progress?

1- Did you have previous Linux experience before using Ubuntu?

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?

3- Do you just have a knack for learning new tech? Did your previous experience as a “power” Windows or Mac user prepare you for Linux?

4- Did you read good Linux books and talk to the right Linux people?

If you answer these questions can you state your learning resources and web links please. Also can you add the question number  “-1” that refers to your Linux/Ubuntu experience? Thank you for your comments. Your participation in this thread may help new Linux users like myself to make better progress with Ubuntu.[/QUOTE]

1- Did you have previous Linux experience before using Ubuntu?
[COLOR="Red"]Yes, I came from Debian and still use Debian along with a long list of other distros I have tried, and also SCO Unix.[/COLOR]

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?
[COLOR="Red"]No, if/when I need to know something I do the research.[/COLOR]

3- Do you just have a knack for learning new tech? Did your previous experience as a “power” Windows or Mac user prepare you for Linux?
[COLOR="red"]Yes. No, see above.[/COLOR]

4- Did you read good Linux books and talk to the right Linux people?
[COLOR="red"]Yes, I do read linux books and articles, and a lot of other stuff as well. I find these forums an excellent resource too.[/COLOR]

---

### Post by iball on 2006-05-20
**1- Did you have previous Linux experience before using Ubuntu?**
I am a relatively recent Ubuntu convert.  I started using Linux about 5 years ago, with Redhat 7.0.  Later came Mandrake, Redhat 9, Slackware, Debian and then Ubuntu.

**2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?**
I generally carefully do my research, before trying something new.  I have discovered new tricks by talking to other people, and reading through Linux books, and posts on forums such as this.

**3- Do you just have a knack for learning new tech? Did your previous experience as a &#8220;power&#8221; Windows or Mac user prepare you for Linux?**
I think I do have a 'knack' for technology.  I used to be a Windows Power User, but having used Linux for 5 years my skills are getting rusty.  I now think how crippled Windows actually is, and how counter-intuitive it is to use.

**4- Did you read good Linux books and talk to the right Linux people?**
Some books that I have got are "The Redhat Linux Bible", which I got when I used Redhat 9.  That doesn't apply much to Ubuntu though.  Other than that, I know a few helpful Unix guys.  I find the best Linux resource is the Web though.

> How does a new Linux user approach using Linux properly without any misconceptions?
You have to realise that Linux is NOT Windows.  Once that hurdle is overcome, the learning curve starts to flatten significantly.

--Ian

---

### Post by garner_nc on 2006-05-21
1- Did you have previous Linux experience before using Ubuntu?

I started in 1996 with Slackware and Kernel 1.0.13. It's been a long time ago.

2- Do you feel that you learned mostly by chance based on information discovery when needed? Was you progress based on trial and error?

A lot was trial and error. The hard lessons from failed trials were the ones most remembered.

3- Do you just have a knack for learning new tech? Did your previous experience as a “power” Windows or Mac user prepare you for Linux?

   New technology comes pretty easy to me. I wasn't a "Power User" of any other OS.

4- Did you read good Linux books and talk to the right Linux people?

First book I got was "Linux Encyclopaedia" by Workgroup Solutions. It was a collection of various how-to's collected fromthe internet.  I had "Running Linux" at one time but I got away from Red Hat.

---

