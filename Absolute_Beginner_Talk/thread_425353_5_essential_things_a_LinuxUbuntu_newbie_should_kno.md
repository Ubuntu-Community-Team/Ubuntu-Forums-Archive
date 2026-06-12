---
title: "5 essential things a Linux/Ubuntu newbie should know."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mijj on 2007-04-27
I suspect the biggest problem someone has with a background in Windows only and little tech background is culture shock.   Things are done differently in Ubuntu (despite a similar looking desktop) .. and you cant get very far without developing some technical expertise.

Please list here what you think the 5 essential things someone technically naive and brand new to Linux/Ubuntu should know.

Dont assume technical expertise.  

Dont assume that learning the nitty gritty of linux will be entertainment.

:)

---

### Post by Calash on 2007-04-27
1 - Let go of Admin.  Windows practically forces this down your throat.  You must be admin to do just about anything.  Let it go, you do not need that with Ubuntu.  Sudo lets you be admin when you need it, and when you don't you are a normal user and safe.

2 - There are no drive letters.  If you have more than 1 hard drive it is mounted under the root.  It takes some getting use to but it does work well.

3 - Google.  Learn to love it.  Going from Windows to Linux is not easy, especially for those of us who know the technical aspect of Windows.  Linux, as a whole, has a massive community behind it.  Search often :)

4 - Learn the terminal commands now, before it is too late.  You will need it in the event that something goes wrong with X and you no longer have a GUI.  The Live CD helps in this event, but the command line is your friend in Linux.

5 - <CTRL><ALT><Backspace> - Restarts X, but kill everything when it does it.  Make sure you have nothing open before you press these keys.

---

### Post by papercuts on 2007-04-27
I guess essential ones would be: 

1. If you can't play your media right after install (mp3, video), don't panic. There is a reason for this but you can easily change it. 
2. Applications in Ubuntu are in packages. Most of them are install-ready but sometimes you might have to compile them. Learn how to compile now, to save yourself confusion later. Also learn some basic terminal commands. 
3. Check all the menus provided before you jump into conclusions. everything you need is most likely there. Make sure you go through Preferences tab. Don't change the layout of the panels before you know what they are about. 
4. When you don't like the way a software is working remind yourself to give it time. You need about one to three months of trial to get confortable in Ubuntu. 
5. If you don't like it, don't use it. If you don't get it, don't hate it. Set it aside and come back again later.

---

### Post by Seisen on 2007-04-27
1.Beryl is beta so it might break your machine
2.Sudo and gksude are your friends
3.Synaptic is your friend
4. Automatix is not your friend
5.If don't get an answer right away calm down, somebody will answer it eventually.

---

### Post by whee on 2007-04-27
1) There are several ways to install Software in Ubuntu.
  a) Applications>Add/Remove
  b) System>Synaptic package manager
  c) apt-get (terminal)
  d) aptitude (terminal)
  e) installation file .deb (this works like in windows)
  f) installation from source (involves make-files and compiling etc.)
*g) Automatix (see point 3)

2) After a clean install of Ubuntu(or many other Linux distro's for that matter) all ports are either stealth and/or closed, this is not the case in Windows, so Windows can get infected with all sorts of malware within minutes after installation as long as the ethernet cable is plugged in.(or connected to the interned in any other way, wifi, usb, bluetooth, etc)
This gives some initial breathing room to my opinion after a fresh install of Ubuntu/Linux.
But this to my opinion does not nessecarily mean that Ubuntu would never need an additional personal firewall, anti-virus scanner or anti-spyware software.(Though not everyone would agree with me on this)

3) When i first started out with Ubuntu Automatix seemed like the holy grail, but later when i became more familiar with Ubuntu there seemed to be conflicts between the "official" ways of installing/maintaining/updating/upgrading software in Ubuntu and the applications installed via Automatix. This doesn't have to be a big problem, but i found it to be a slight nuisance. So when i switched from Dapper to Feisty i decided not to install Automatix anymore.(Although i still find that Automatix offers better solutions to some things in Ubuntu than official Ubuntu ways(like installing a whole bunch of codecs at once)

4) Ubuntu is known as an easy Linux distribution, but that doesn't mean(in my opinion) that there isn't a learning curve. (Also do not get scared because of editing a configuration file every now and then or typing some command in the terminal, there will come a time when all these things will make perfect sense)

5) Linux distributions, like Windows are not always free from problems(even though some hardcore proponents might have claimed this on some forum somewhere on the internet)
I've ran into problems, but like with Windows you learn more about the system/OS, it's trial and error.
But the advantage with Linux is is that you can learn the OS/Distribution in a very deep way, as it is open source unlike windows, you can learn the structure of the system and understand better how it operates, this makes problem solving alot easier.

6)(bonus?) Once you understand the basics, then things like terminal commands and flags are a handy tool, you can script everything in Linux like mad.
Also learning where everything is in the directory tree of Ubuntu/Linux will eventually become handy knowledge.(you'll then know where applications are installed, or where configuration files are or where commands are stored that you use in the terminal etc.)

---

### Post by Josey on 2007-04-27
Expect to break your video drivers if you like to mess around with them and be able to fix xorg from a command line.

The first time I did this I thought I would have to reinstall the OS but it's fixed with a simple command.  So if your sitting at a command line after the message "unable to start gdm" then the following is a savior.

```
sudo dpkg-reconfigure xserver-xorg
```

that command should be committed to memory.

fixing it manually is also an option for the more advanced noob

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by LuisGMarine on 2007-04-27
Wow outstanding job!

I would like to add that when you ask questions here on the forum try to give as much information as you possibly can.  Don't just sit there and say, " My system freezes!!! HELP!!! ."

That doesn't fly to well with most people, instead try to be more descriptive as to when it freezes if anything you do causes it to freeze , etc etc.

Another cool little command for beginners to know is the xkill command. This kills the application that has crashed/froze/ whatever down in a second.  Just open up a terminal type in ' xkill ' without the quotation marks and click on the program, and it is gone.

Also if someone above hasn't already mentioned it, go ahead and visit the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") this helped me out a lot at the beginning and from time to time I see myself going back just to fill my head with more information.  :guitar: 

-LuisGMarine

---

### Post by Bachstelze on 2007-04-27
1. Linux is not Windows.

2. Just because you can do it does not mean it's the right thing to do.

3. If it's not broken, don't fix it.

4. Easiest way never leads anywhere.

5. Google is your friend.

---

### Post by freebird54 on 2007-04-27
1. Not only are there lots of ways to install software in Ubuntu, there is lots of software waiting for you to try it.  BUT - try one thing at a time.  If you try to get everything happening at once, you most likely will end up re-installing at least once.

2. These forums are great.  They have been great for a long time -  and they have a search feature that is also great.  Try a few key words of your problem in the search, and you will at a minimum learn what people need to know to help you fix it!

3.  There is a reason that there are multiple versions of the OS available.  The names are even a pretty good guide to their 'personality' at the moment.  Dapper = pretty smooth, Edgy is, Feisty needs you to keep a tight leash on it!  Please choose according to the balance of your need for features, or stability.

4. Yes you can customize everything.  No, the forums won't know what you've done unless you tell them.  MAKE A NOTE of each change you make, when you make it.  (I suggest keeping a text editor open, and add a line when you find something out, or do something - and save before trying the new setting!)

5. NO, it is not yet perfect.  YES, it is better in many ways than the proprietary alternatives.  Yes, you can put it on as many computers as you want -for as long as you want.  Yes - it can inter-operate with a lot of alternatives.  Yes, unless your work is VERY specialized, you can get it done in fine style right here.  Yes, it plays nice with others - including other distros, Windows, etc.  NO - it does not do everything ever thought of - yet.

And finally - if you let it be, it can be more fun than you thought a computer itself could be.!

---

### Post by Bachstelze on 2007-04-27
2b. When someone tells you that it "Works For Me" (TM), that doesn't necessarily mean it will work for you.

---

### Post by Alex N on 2007-04-27
Well, I am working with computers for 22 years now, and I worked with command line maybe more
then many of you played FPS. Remember TECO ? Even heard about it ?

Things that are noteworthy, but causes no problems:
1. No drive letters - no problem at all, because most of Win installations nowadays has ONE BIG C: partition.

2. Software installations goes to different directories (something to /var, something to /usr, something to /etc)
and there is NO WAY to change it. Under Windows I can control the process. 

3. Some things should be done via sudo, some not. It looks strange from win point of view, but I understand all about security. The rule of thumb is "try to do it from your account, if there are problems with permissions, think a little and try sudo"

4. Commands are different. It's a trouble, but there is info.

5. Some things are done in a completely different way. Get used to it.

6. Some software just does not exist. Be prepared. Almost always there is some replacement, but this is not always have the same quality. For example, there is no good NC clone. MC and gnome commander are way far  behind FAR. But this is only one side of a problem. Some excellent Unix software never existed on Windows too. Also there are packages that are more complete and useful on Linux.

Currently I have very negative experience with Ubuntu. So here are real problems (for win user)

1. Almost all software I use now exists in both Windows and Linux incarnations. Firefox, PHP, MySQL, Eagle CAD, OpenOffice, etc etc. I decided to move to Linux only after I carefully counted all software I use.
Among programs that I am using now on Win there are only few that do not exist on Linux. From my experience with Ubuntu I found rule number 1:
** The more "Unixish" is the origin of the software, the more difficult it is to configure it under Linux.
examples : FreePascal  just installs. Apache requires a lot of config editing.

2. The interoperability of the software is between awful and terrible. Upgrade manager ruines my boot
sequence every time it installs new kernel. Every time. Synaptic easily brings packages into "deadlock"
state, when it can not remove it and can not install it and it does not work (happened with apache, php, mysql in sequence, now with opera). If there is just one package, 90% chance that it will work as is. If it cooperates with other packages - most likely you'll have to tune it manually. xvidtune does not work with Nvidia drivers. etc, etc.

3. The community support is... well... for Ubuntu I'll use the word "insufficient", for other Linux distros some really bad words should be used. I think there is a slogan, often missed by Linux guys : 
RTFM is not an answer.

4. Some programs are using real "hacks" to make them working properly. The first example is Grub.

There are also some good news (for me)

Ubuntu works with hardware MUCH BETTER than Windows. Do not believe the contrary. MUCH better.
Even my Epson scanner, which driver NEVER worked under Win for me, and NOBODY could ever solve
this problem - works with Sane without a single problem in all modes. All my hardware works with Ubuntu - a big surprise.

---

### Post by az on 2007-04-27
1.  If it doesn't work, it's a bug.  It's not your fault.

2.  In 99 percent of the problems you will face, someone else has faced that problem and found an answer.  Often, they already documented it.  This applies to the user as well as the developer.

3.  The software is compatible at the source level, and not at the binary level.  You cannot just download anything from anywhere and install it.  That being said, someone has probably already built it for your disto.  Your distro should be able to provide everything you need. 

4. GNU/linux is all about software freedom.  That means there are other ways to make money from software than selling it.  You can't compare how things work in the proprietary software world with the way things work in the free-libre world.

5.  It's easy to give back to the community. If not by developing code, you can file bugs, write/organize documentation, artwork, advcocay events, etc...

---

### Post by crimesaucer on 2007-04-27
From a beginner to a beginner, some of these tips might help.

here are 5 from me:

1.) read this thread and play around with your terminal: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

2.) read this because there is some good info in it: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

3.) Installing things like Beryl and Conky will teach you some things about your system with a "hands on" approach to it. And then when you finish, you will have some new apps that you can be proud of. When you read the install wiki's of Beryl and the "How To" for Conky 1.4.5, all you really have to do is follow the detailed directions, and if you run into problems, then jump onto a forum and ask questions. Also use the forum search, and google search.

4.) Read the ubuntu forums and try to learn. If you haven't ever heard of something, then click onto the thread to see what it's all about. Read about other people's problems that are similar to the one's you've encountered. 

5.) this one might not be a good tip, but it helped me. Basically, a lot of the files you will mess with are hidden, so uncheck the hidden box in your file system:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-44-1.png[/IMG]


p.s.- I also like that someone told you about:

```
xkill
```

that is a good way to close anything that freezes up. And I also liked how someone said don't use Automatix. You can install most everything you need from the wiki pages and it's also a good way to learn your system instead of depending on a program to get your java and flash updated and installed.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

and my last added tip that helps me learn sometimes is that I always look the commands up that you see given to you on the help forums or in the installation guides. That way you can learn some of the command options: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

using the link above, you can see what this command and it's options do:

```
tar -xvf dunnowhat.tar
```

There might be better guides for this, but it's what I found and use as a cross reference to the forums.

---

### Post by kpkeerthi on 2007-04-27
Read [The Ubuntu Desktop Guide]("http://help.ubuntu.com") before you mess with your setup.

---

### Post by xpod on 2007-04-27
I`ve only one thats really worth mentioning on top of whats already been said 

DONT listen to any gumph,fud,manyakka or bulls**t

> 4. Automatix is not your friend

---

### Post by chrisftcc on 2007-04-27
Hello All,

First I'd like to say, I absolutely LOVE Linux....I am a regular Windows user as well, but as soon as I move into my house, I will have room to have two machines..one Vista one Ubuntu..(yes, I use Virtual PC already, but nothing like having a dedicated box)....Ubuntu is shaping up to truly be a contender against future Windows OSes....I love the support community...Keep up the good fight and the good work...

1.  Read the Sticky's (in the forums)..even if you think you know it all; you don't..

2.  Take a live CD and a command book (any Linux for Beginners or google for commands in Linux) and become familiar with using a terminal session; Practice, Practice, Practice; Things sometimes are just a lot easier when you can drop to command line and type it out.

3.  Unlearn Windows.  Takes some getting used to; but can be done with time.  Since that's what many users have grown up with, it is very difficult to part ways with the Windows way...

4.  Don't expect it to work on the first try;  Sometimes it's hardware, sometimes it's software...sometimes, it's just your dogone fingers that can't type.  You WILL have a moment where something won't work as advertised.  Don't give up..There is always an answer somewhere...You just need to have the time available to find it...

5.  Free.....If you hang in there long enough, you can totally jettison that beast that is Windows.....and just think of ALL of the hard earned $$ that you saved 

Vista compatible machine $600-$1000
Vista = at least $200-$300
Office = another $300
Photoshop = $300-$400

the list goes on and on and on.....

For the most part, whatever you can do in Windows, you can do with Linux...just takes some time, effort, patience and a lot of tweaking.  But if I never have to buy another application or piece of software, it is well worth it..

---

### Post by heatpumpcontrol on 2007-04-28
> **LuisGMarine said:**
> Wow outstanding job!

I would like to add that when you ask questions here on the forum try to give as much information as you possibly can.  Don't just sit there and say, " My system freezes!!! HELP!!! ."

That doesn't fly to well with most people, instead try to be more descriptive as to when it freezes if anything you do causes it to freeze , etc etc.

Another cool little command for beginners to know is the xkill command. This kills the application that has crashed/froze/ whatever down in a second.  Just open up a terminal type in ' xkill ' without the quotation marks and click on the program, and it is gone.

Also if someone above hasn't already mentioned it, go ahead and visit the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") this helped me out a lot at the beginning and from time to time I see myself going back just to fill my head with more information.  :guitar: 

-LuisGMarine

As s newbie, I've was looking for a 'task manager'. Well you can right click on the top task bar, 'add to panel'. Drag and Drop System Monitor and Force Quit to the top task bar (or bottom if you prefer) and close the Panel. Now you'll have access to 'force quit' a program as described above and/or you can kill a precess by double clicking on the 'system monitor' and killing the process under 'processes'. Works nicely.

heatpumpcontrol.... thanks to everyone... I'm learning

---

### Post by lepz on 2007-04-28
(1) Twenty odd years using/fixing windows doesn't mean Diddly here, your a n00b deal with it. :lolflag:

---

### Post by mijj on 2007-04-28
> **heatpumpcontrol said:**
> As s newbie, I've was looking for a 'task manager'. Well you can right click on the top task bar, 'add to panel'. Drag and Drop System Monitor and Force Quit to the top task bar (or bottom if you prefer) and close the Panel. Now you'll have access to 'force quit' a program as described above and/or you can kill a precess by double clicking on the 'system monitor' and killing the process under 'processes'. Works nicely.

ooo !!! ... that's a good one!

---

### Post by yabbadabbadont on 2007-04-28
I only have one.  When working in a terminal or at the command line, the commands for removing, renaming, and copying files will not, by default, prompt you when you are about to overwrite something (or remove something important).  If you are not sure about the command you are about to run, don't run it as there very rarely is a way to undo it.  Many a noob (including me, many, many years ago) have been burned by running something like:```
rm * .bak
``` when they should have run ```
rm *.bak
```  Spaces in the wrong place will make you regret ever having installed Linux (or Unix, which is where I got burned).

---

### Post by seshomaru samma on 2007-04-28
I can only think of one:

1. If you want it easy - buy a preinstalled Linux or ask your geek friend to install it for you

otherwise - be prepared to do some learning and googling

---

### Post by Nythain on 2007-04-28
top 5 things huh... im sure most this has been said already but here we go...

1. Dont be afraid of the terminal... it is your friend, it gives you much info when things dont work and you can accomplish more with ajust a few commands there than many minutes of clicking and navigating a desktop environment... and you WILL have to be there eventually

2. Learn the file structure of Linux... abandon thoughts such as "where software is installed" and start thinking, "where the system groups similar types of files". Everything you install gets files thrown all over your system for the most part.

3. Sudo... when used correctly it is your best friend, also gksudo and kdesu, remember that if you are going to run a graphical program, use the graphical sudo command and not normal sudo.

4. ./configure, make, make install... the basics of source compiling... not everything you want/need will be in teh repos (though i shall say Virtually everything is).

5. And finally, lets see... oh yeah... patience... every problem can be fixed, with enough patience, help, and research, thats one of the things that makes linux so great, while windows does a nice job of saying your screwed, linux says, we have a problem you should take a look at

---

### Post by 8rdx on 2007-04-29
0) **Have patience**. (That is a given.)
1) Be certain of your reasons for trying linux. Are you really having severe problems with Windows or do you just like the idea of linux idea because it's free? "Dual boot" is probably the best option for newbies. Removable hard drive might be better (considering that myself).
2) Accept that linux may have problems with your hardware. Maybe it's too old, to new, or just problematic. ubuntu is the first distro I tried that worked with my scanner, even though I bought it because it was listed on the SANE website.
3) Accept that linux has far fewer applications than Windows, and there may not be any alternatives for what you have in Windows. I have yet to see a tax app that can e-file under linux. If you are a gamer, you will be very disappointed.
4) Read the documentation. Read a book or two about linux, or even the particular distro (there are many ubuntu books out there - from n00b to *nixpert). Learn all you can about using the command line, there are many things that can ONLY be done with it.
5) Separate the wheat from the chaff. When you need help, there is waaaayyyy too much of it available. You may have to read through many posts to find the answer that works for your situation. Some people go off on tangents or hijack threads. Trolls just want to start trouble. Accept that there may not be a solution.
:)

---

### Post by j002 on 2007-04-29
1. Linux Is Not Windows.

2. 95% of install problems are caused by faulty hardware.

3. Get .deb files to install (and get the dependencies from the *same* site).

4. Graphical applications are safer to use (and easier) than the command prompt - use them if possible.

5. Just becuse you used Unix at university, doesn't mean setting up Linux will be easy.

---

### Post by mijj on 2007-05-05
5 things selected from the following link will probly be useful ...

[[COLOR="SeaGreen"][SIZE="3"]_**Seven Steps to Feisty Fawn Bliss**_[/SIZE][/COLOR]]("http://desktoplinux.com/articles/AT3648616185.html")


... relates to Kubuntu though ... not Ubuntu! ... <slaps the article for being about the wrong flavour>

---

### Post by Pistolla on 2007-05-05
Automatix is not yer enemy. if anything, it is yer acquaintance! Not necessarily your friend but it works really well for what i need (notr it is whtat i need)
The rest i can agree with whole-heatedly. Except, mebbe add google/linux is yer friend. It (and these forums and the forks provided) have been entirely helpful. Just don't get "caught up" in peeps who like one thing and hate another. if you do, then it won't matter what OS you have. See and observe here and you WILL NOT be disappointed...promise
Pistolla

---

