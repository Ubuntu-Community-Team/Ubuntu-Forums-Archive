---
title: "Is there a way to use Widows programs on Ubuntu Gnome?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by kpiper1993 on 2007-08-22
I have a program want to install that only works on Windows.  Is there a way to use Widows programs on Ubuntu Gnome?
THANKS

---

### Post by deadgobby on 2007-08-22
What program do you want to install? There is Wine. Wine is a windows emulator and it does it best to lie to the program that it is running on windows. Well, some times a good lier gets caught and starts to BS their way through. Thus some good mojo to get the program to work with Wine.
Gobby

---

### Post by Terl on 2007-08-22
You can try to use Wine ([Wine HQ for more info]("http://www.winehq.org/")).

What is the program?

---

### Post by asmoore82 on 2007-08-22
> **deadgobby said:**
> What program do you want to install? There is Wine. **Wine is a windows emulator** and it does it best to lie to the program that it is running on windows. Well, some times a good lier gets caught and starts to BS their way through. Thus some good mojo to get the program to work with Wine.
Gobby

This is just a **flat WRONG** and **VERY irresponsible** to say to a new user.

It is very difficult to properly configure Wine and even then it may not support the
Windows App that you want to use in Linux. However one thing that we can say for
sure is that Wine is in no way, shape or form a "windows emulator."

In fact, that is originally what the project name stood for ...
WINE = Wine Is Not an Emulator.

If you decide to try to use Wine, it is important tha you don't start out in an emulator mindset
or you are certainly doomed to fail.
[http://winehq.org/site/myths#slow](http://winehq.org/site/myths#slow)

---

### Post by wpshooter on 2007-08-22
> **asmoore82 said:**
> This is just a **flat WRONG** and **VERY irresponsible** to say to a new user.

It is very difficult to properly configure Wine and even then it may not support the
Windows App that you want to use in Linux. However one thing that we can say for
sure is that Wine is in no way, shape or form a "windows emulator."

In fact, that is originally what the project name stood for ...
WINE = Wine Is Not an Emulator.

If you decide to try to use Wine, it is important tha you don't start out in an emulator mindset
or you are certainly doomed to fail.
[http://winehq.org/site/myths#slow](http://winehq.org/site/myths#slow)

I agree.

From my experience, you need to run Linux programs under a Linux O/S and Windows programs under a Windows based O/S.  Trying to skirt around this, is more trouble than it is worth !!!

---

### Post by Dr Small on 2007-08-22
Wine is not really all that hard. I have gotten windows apps to run on wine before. It is rather very simple. But like they said, it will not run all of the windows apps.

Dr Small

---

### Post by rich.bradshaw on 2007-08-22
Yeah, WINE is good for very simple apps, or just to use things occasionally, but it's normally better to find a true replacement.

Same way you probably can fit a ford engine in a porsche, but it's probably easier to just use a porsche one. It's better anyway!

---

### Post by kevdog on 2007-08-22
Install virtual box and then install windows within virtual box.  That would probably be better for you than WINE.

---

### Post by deadgobby on 2007-08-22
> **asmoore82 said:**
> This is just a **flat WRONG** and **VERY irresponsible** to say to a new user.

It is very difficult to properly configure Wine and even then it may not support the
Windows App that you want to use in Linux. However one thing that we can say for
sure is that Wine is in no way, shape or form a "windows emulator."

In fact, that is originally what the project name stood for ...
WINE = Wine Is Not an Emulator.

If you decide to try to use Wine, it is important tha you don't start out in an emulator mindset
or you are certainly doomed to fail.
[http://winehq.org/site/myths#slow](http://winehq.org/site/myths#slow)

 I am not going to back down and say that Wine is not a Windows emulator even if Wine is usually thought of as a Microsoft Windows emulator, the Wine developers would prefer that users thought of Wine as a Windows compatibility layer for Linux. Wine does not require MS Windows, but it can use native system dll files in place of its own if they are available.  What the program does best and best it does it lies to a Micro Soft program to run. It does not work all the time and thus you need to lie to it more to make it work. 
 Some people say the computers never lie. Of course they don't. The end user does and the end results of the  user wins. Humans only can tell computer and numbers to lie. Like of example the book 2001. HAL was told to lie. It is a human nature to lie and we do it a lot. You lie to it and make believe it doing some thing that it should not. It how it works and how many other things in life works. 
Gobby

---

### Post by moredhel on 2007-08-22
Then you are being stupid. Because it /isn't/ an emulator. Try looking up what emulators do.

9_9

---

### Post by asmoore82 on 2007-08-22
> **deadgobby said:**
> I am not going to back down and say that Wine is not a Windows emulator even if Wine is usually thought of as a Microsoft Windows emulator, the **Wine developers would prefer that users thought of Wine as a Windows compatibility layer for Linux**. Wine does not require MS Windows, but it can use native system dll files in place of its own if they are available.  What the program does best and best it does it lies to a Micro Soft program to run. It does not work all the time and thus you need to lie to it more to make it work. 
 Some people say the computers never lie. Of course they don't. The end user does and the end results of the  user wins. Humans only can tell computer and numbers to lie. Like of example the book 2001. HAL was told to lie. It is a human nature to lie and we do it a lot. You lie to it and make believe it doing some thing that it should not. It how it works and how many other things in life works. 
Gobby

:confused: you seem to be most unhelpful.

this is NOT a debate nor it is an exploration of developers thoughts, emotions, hopes and dreams.

WINE IS NOT AN EMULATOR; This is just a plain and simple FACT of life that no amount of 
"lie this lie that" jargon will change.  Wine is the most viable way to run a native Windows
applicaiton on a UNIX machine. Emulators are actually more reliable but with a
key (pun intended) difference: It is Free and Legal to run whatever you want with Wine
but you need a valid License for Winders to run it in a Virtual Enviroment or Emulator.

P.S. my FUD-sense is tingling.

---

### Post by deadgobby on 2007-08-22
So a person lies on what key to use don't  they.

---

### Post by yogo on 2007-08-22
> **kevdog said:**
> Install virtual box and then install windows within virtual box.  That would probably be better for you than WINE.



I have installed Virtual Box, when you say install windows within, do you mean a full fledged several gigabyte install? Are there any guides for doing this?

Sounds probably more complicated that it is.

TIA

---

### Post by Terl on 2007-08-22
The guide at virtualbox is very good and can walk you through it.  In a nutshell, yes, you will be doing a regular windows install in virtualbox.  The toolbars/menus are fairly self explanatory.

Also, to be honest, when I installed it the first time I thought "cool" but then after thinking on it longer I figured if I need windows it would be easier to just dual boot.  There are advantages and disadvantages but bottom line is, if you really really need a windows app it might be best to dual boot.  My preference now is to just find a linux app that does what I need.

---

### Post by WarholsGhost on 2007-08-22
I prefer Crossover linux, it's easyer to configure and more stable with some programs.

---

### Post by kevdog on 2007-08-22
The only advantage virtual box offers is that you dont need to reboot to start windows.  A native installation (or dual boot) does offer the advantage of windows being more "zippier" -- important if gaming is your thing.

---

### Post by AndyCooll on 2007-08-22
> **kevdog said:**
> The only advantage virtual box offers is that you dont need to reboot to start windows.  A native installation (or dual boot) does offer the advantage of windows being more "zippier" -- important if gaming is your thing.

That might be an "only" advantage, but it can be a big one. I disagree with the comment that says it is easier to dual-boot. It's more of a pain-in-the-****. However as kevdog says, if gaming is your thing then it's really the only option.

Wine is a good alternative, but not all apps run under it. I only needed Windows to play my Football Manager game (a number cruncher, not graphics intensive) and for ages played it via an XP VMware image. It ran just as smooth as if it were on an XP only machine. Since then I've got it working under Wine and this is even more convenient. It wasn't that hard as it turns out, however I did have to do a bit of homework and find out exactly how others had got it running before me.

So, in all truth, it really depends on exactly what you need a Windows environment for. And although I disagree with Terls "dual-booting" comment I do agree with his final thought that finding a Linux alternative is the best option of all.

:cool:

---

### Post by phr0ze on 2007-08-22
> **asmoore82 said:**
> :confused: you seem to be most unhelpful.

this is NOT a debate nor it is an exploration of developers thoughts, emotions, hopes and dreams.

WINE IS NOT AN EMULATOR; This is just a plain and simple FACT of life that no amount of 
"lie this lie that" jargon will change.  Wine is the most viable way to run a native Windows
applicaiton on a UNIX machine. Emulators are actually more reliable but with a
key (pun intended) difference: It is Free and Legal to run whatever you want with Wine
but you need a valid License for Winders to run it in a Virtual Enviroment or Emulator.

P.S. my FUD-sense is tingling.

Umm. WINE is an emulator and you are tricked into thinking it's not because of it's nifty acronym. WINE is Not a hardware emulator. It is a software emulator. If you read the WINE faq page it says it's not a hardware emulator. Notice the keyword. They know they are a software emulator. Futher if you read  on, they state they are a compatability layer. Look up compatability layer on Wikipedia and you will see a compatability layer is for emulating a guest environment on a host environment.  Here is a [link]("http://en.wikipedia.org/wiki/Compatibility_layer"). 

Wine has written API's which emulate the windows native API's.

---

### Post by feistyfirsttimer on 2007-08-22
I always find this Wine's an emulator, no it's not, argument funny.  It's good to remember that in its early days, the developers said Wine stood for Windows Emulator... then later on they decided it was an acronym for Wine Is Not an Emulator.  It's all pretty academic anyway, whether you want to call it an emulator or not... the end result of what it does (when it works) is what counts.

All that being said, Wine can be difficult to get working, as can its Crossover relation.  I think the important question here is: what is the Windows program that the OP wants to use?  The best thing to do is surely to try and find a Linux application that can do the same job.  It is possible to find such programs.

The best programs to run in Linux are Linux programs.  The best place to run Windows programs is on a Windows computer.  There are a couple of Windows apps that I have to use sometimes and that I can't find working Linux alternatives for.  So I've kept an XP partition on my hard drive for those times when I absolutely positively have to use my Windows programs.  That's probably the best solution, though there's also VMWare nowadays.

---

### Post by asmoore82 on 2007-08-22
> **phr0ze said:**
> Umm. WINE is an emulator and you are tricked into thinking it's not because of it's nifty acronym. WINE is Not a hardware emulator. It is a software emulator. If you read the WINE faq page it says it's not a hardware emulator. Notice the keyword. They know they are a software emulator. Futher if you read  on, they state they are a compatability layer. Look up compatability layer on Wikipedia and you will see a compatability layer is for emulating a guest environment on a host environment.  Here is a [link]("http://en.wikipedia.org/wiki/Compatibility_layer"). 

Wine has written API's which emulate the windows native API's.

WINE = Wine Is NOT an Emulator.

That wiki article you referenced is total bunk!

Wine is a RE-IMPLEMENTATION of the Windows API. It emulates nothing.

"Re-implementation" is a big word but has proper meaning and should not be glossed over by "emulation."

take these prime examples ...

1. Firefox is a re-implementation of a web browser.
2. Xorg is a re-implementation of the X11 Windowing System.
3. The Linux kernel is re-implementation of a UNIX kernel.

would you so readily call these 3 situations a case of "emulation?"
I think not.

---

### Post by phr0ze on 2007-08-24
1. Firefox is a web browser. No one would confuse this for emulation.
2. xorg releases X11, The latest is X11R7.3
3. Linux is a Unix-like OS implemantation. Is is not an emulator. AFIAK Linux will not run a binaries compiled for unix.

---

### Post by dresman on 2007-08-26
How do you use wine.Its very confusing to me.plz help!!!!:confused:

---

### Post by edd07 on 2007-08-26
It's fairly easy. First, you need to install wine from Add/Remove Apps, Synaptic or typing this into a terminal

```
sudo apt-get install wine
```

Once it's installed you will be able to open .exe files by double clicking on them, but it is recommended that you open them in a terminal so, if there's any errors, you get messges that can help you fix them. You do this by typing

```
wine /path/to/file.exe
```

I have Wine installed and I successfully run Macromedia Dreamweaver 8 without any problems, for example, but you can check if the program you need works with Wine from [WineHQ's Application Database]("http://appdb.winehq.org/")

---

### Post by Bakon Jarser on 2007-08-27
Frank's Corner has an additional list of programs that work in wine and a guide on how to get them working.

[http://frankscorner.org/](http://frankscorner.org/)

And it really doesn't matter if wine is an emulator or not.  It's all just semantics.  All that mattters is that it works, kinda :)

---

### Post by gabz8472 on 2007-08-27
I'm not much more than an end user myself, so I won't argue on the points of wether WINE is an emulator or not. But my suggestion is first to find an equivalent program to the one you're trying to run. If there  isn't any, then try to use WINE. The instructions on using it can be found in other threads and are pretty straightforward. that's how i did it. it worked for me, might work for you.  I've also seen threads that suggest using VMWare to run a full windows installation but haven't used or tried it. Like I said, explore.

---

### Post by gabz8472 on 2007-08-27
I'm not much more than an end user myself, so I won't argue on the points of wether WINE is an emulator or not. But my suggestion is first to find an equivalent program to the one you're trying to run. If there isn't any, then try to use WINE. The instructions on using it can be found in other threads and are pretty straightforward. that's how i did it. it worked for me, might work for you. I've also seen threads that suggest using VMWare to run a full windows installation but haven't used or tried it. Like I said, explore.

---

### Post by Orbital75 on 2007-08-27
I use Virtual Box and it works pretty well.... 
However, I wouldn't even attempt to install it without aleast 1 gig of ram.
It will run but be very slow and may even crash with less.
Remember, when you are running a virtual machine your running
two OS's at the same time.  Windows and Ubuntu will both need
ram.

---

