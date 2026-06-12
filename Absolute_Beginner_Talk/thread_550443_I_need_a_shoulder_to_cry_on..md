---
title: "I need a shoulder to cry on."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Dan-O on 2007-09-13
Ubuntu is a beautiful thing.  I want so badly to convert but, I can't...not yet anyway.  I don't understand the command line stuff and I find myself having to muddle through it at every turn.  I can't even get the Flash Player 9 installed.  I'm not sure if it is because my system is 64-bit or what....either way.  My command line days were supposed to be over when I left Windows 2000.  It feels odd and out of place to be using such a rudimentary form of wrestling code into the proper place.  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp.

Ok.

/rantoff

Help me get flashplayer 9 installed on this silly machine.  Help me get the graphics to do 3D for god sakes.

Dell Inspiron 1501
1gig memory
40g HD
AMD Turion 64X2 Mobile Technology

Thanks guys.
Dan-O

---

### Post by John.Michael.Kane on 2007-09-13
> **Dan-O said:**
> Ubuntu is a beautiful thing.  I want so badly to convert but, I can't...not yet anyway.  I don't understand the command line stuff and I find myself having to muddle through it at every turn.  I can't even get the Flash Player 9 installed.  I'm not sure if it is because my system is 64-bit or what....either way.  My command line days were supposed to be over when I left Windows 2000.  It feels odd and out of place to be using such a rudimentary form of wrestling code into the proper place.  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp.

Ok.

/rantoff

Help me get flashplayer 9 installed on this silly machine.  Help me get the graphics to do 3D for god sakes.

Dell Inspiron 1501
1gig memory
40g HD
AMD Turion 64X2 Mobile Technology

Thanks guys.
Dan-O

Can please post the output of the command below. 
```
uname -a
```
This will tell us if you installed the 64 or 32bit version of ubuntu.

---

### Post by Romanus81 on 2007-09-13
This site really helped me learn about command line:
[http://linuxcommand.org/](http://linuxcommand.org/)
This site has a lot of really good tutorials
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
Flash:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
For 3D effects you can get help here: 
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)
What graphics card card do you use?

---

### Post by RealG187 on 2007-09-13
I hardly know it I only know wine and paths and cd! I recetnly figured out it wasnt dir but something like ls!

---

### Post by overdrank on 2007-09-13
> **Dan-O said:**
> Ubuntu is a beautiful thing.  I want so badly to convert but, I can't...not yet anyway.  I don't understand the command line stuff and I find myself having to muddle through it at every turn.  I can't even get the Flash Player 9 installed.  I'm not sure if it is because my system is 64-bit or what....either way.  My command line days were supposed to be over when I left Windows 2000.  It feels odd and out of place to be using such a rudimentary form of wrestling code into the proper place.  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp.

Ok.

/rantoff

Help me get flashplayer 9 installed on this silly machine.  Help me get the graphics to do 3D for god sakes.

Dell Inspiron 1501
1gig memory
40g HD
AMD Turion 64X2 Mobile Technology

Thanks guys.
Dan-O

Hi well I am assuming you have the 64 bit version install but could you tell us which version you have? Feisty 7.04, edgy 6.10? Your 3d graphics, it would help us if you can tell us the model of your video card.

Edit to late and out of place

---

### Post by jimrz on 2007-09-13
> **Dan-O said:**
> Ubuntu is a beautiful thing.  I want so badly to convert but, I can't...not yet anyway.  I don't understand the command line stuff and I find myself having to muddle through it at every turn.  I can't even get the Flash Player 9 installed.  I'm not sure if it is because my system is 64-bit or what....either way.  My command line days were supposed to be over when I left Windows 2000.  It feels odd and out of place to be using such a rudimentary form of wrestling code into the proper place.  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp.

Ok.

/rantoff

Help me get flashplayer 9 installed on this silly machine.  Help me get the graphics to do 3D for god sakes.

Dell Inspiron 1501
1gig memory
40g HD
AMD Turion 64X2 Mobile Technology

Thanks guys.
Dan-O

first off, what 64 bit apps are you actually using (there are currently very few of these) that require you to use the 64 bit kernel. 

if the answer is none then just use the standard 32 bit kernel and you will have fewer issues like the one you describe.

in case you are wondering 64 bit procs work well with the generic kernel. my core2duo E6600 is running it and performs beautifully and rapidly (completes super_pi 20 in < 16 seconds).

---

### Post by steveneddy on 2007-09-13
```
sudo apt-get install cowsay
```

then

```
cowsay I don't know
```

learning the command line

---

### Post by Maestro23 on 2007-09-13
> **Dan-O said:**
> Ubuntu is a beautiful thing.  I want so badly to convert but, I can't...not yet anyway.  I don't understand the command line stuff and I find myself having to muddle through it at every turn.  I can't even get the Flash Player 9 installed.  I'm not sure if it is because my system is 64-bit or what....either way.  My command line days were supposed to be over when I left Windows 2000.  It feels odd and out of place to be using such a rudimentary form of wrestling code into the proper place.  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp.

Ok.

/rantoff

Help me get flashplayer 9 installed on this silly machine.  Help me get the graphics to do 3D for god sakes.

Dell Inspiron 1501
1gig memory
40g HD
AMD Turion 64X2 Mobile Technology

Thanks guys.
Dan-O

If you are running the 64-bit version of Ubuntu:

Flash doesn't natively work on the Ubuntu 64-bit edition.  You will have to use the work-around in the following link.

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by sstusick on 2007-09-13
> **Dan-O said:**
>  You purest that keep this stupid command line crap alive should be taken to the nearest tree and flogged to a bloody pulp. The command line is a wonderful and powerful thing, take the time to learn it and understand it and you will love it.

---

### Post by Dan-O on 2007-09-13
I'm using the Fiesty Fawn 7.04.  It is the 64 bit version.

The graphics for this thing are the ATI X1150 256Mb onboard graphics.

---

### Post by wheredidrealitygo on 2007-09-13
the command-line is seriously helpful.

 example: you've messed up your xorg for the bazilionth time and need to restore your xorg.conf without having to sort through piles of disks.

also remote server administration/ssh is very flexible with a CLI, very handy if you're in a limited user account environment (such as a workplace).

---

### Post by Dan-O on 2007-09-13
> **Maestro23 said:**
> If you are running the 64-bit version of Ubuntu:

Flash doesn't natively work on the Ubuntu 64-bit edition.  You will have to use the work-around in the following link.

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

O
M
G

You have got to be kidding me.  That's the work around?  Holy hell...maybe I should just stop now while I still have hair.  Do you see why Linux can't ween people off of M$....it's this kind of stuff man....honestly.

---

### Post by Dan-O on 2007-09-13
> **wheredidrealitygo said:**
> the command-line is seriously helpful.

 example: you've messed up your xorg for the bazilionth time and need to restore your xorg.conf without having to sort through piles of disks.

also remote server administration/ssh is very flexible with a CLI, very handy if you're in a limited user account environment (such as a workplace).

You're a former M$ employee.  I still use cmd line stuff in Windows once in awhile.  PING, Tracert, config /all, chkdsk and that's it.

I do video conferencing for a living.  I have to ping and tracert to codecs some times to make sure they are on or if there is line problem.

Linux wants me to use cmd line to load drivers or install software...something I realy haven't done since windows 98...last I can remember.

Why does Linux still need a CMD line to get this kind of stuff done?  Argh.

---

### Post by Dan-O on 2007-09-13
After much hair pulling and gnashing of teeth, also a quick call to my co-worker, I will be uploading the 32 bit distro of Feisty Fawn 7.04.  

I'm probably still going to be lost in the sauce because of the nature of cmd line stuff to get Flash Player 9 installed and ATI graphics working.

You guys bear with me.  I want this to work badly but, after 7 years, Linux still has this annoying little cmd line thing that brings back a myriad of heartbreak when I first tried to cut my teeth on Linux.

---

### Post by igknighted on 2007-09-13
> **Dan-O said:**
> O
M
G

You have got to be kidding me.  That's the work around?  Holy hell...maybe I should just stop now while I still have hair.  Do you see why Linux can't ween people off of M$....it's this kind of stuff man....honestly.

It doesn't work on 64 bit windows either... write adobe and tell them 64 bit is for real and you want flash.  Otherwise, use the free flash plugins like gnash, they work fine for 64bit.

---

### Post by nonewmsgs on 2007-09-13
all you have to do is copy and paste when you have to deal with the commandline.

---

### Post by igknighted on 2007-09-13
> **Dan-O said:**
> After much hair pulling and gnashing of teeth, also a quick call to my co-worker, I will be uploading the 32 bit distro of Feisty Fawn 7.04.  

I'm probably still going to be lost in the sauce because of the nature of cmd line stuff to get Flash Player 9 installed and ATI graphics working.

You guys bear with me.  I want this to work badly but, after 7 years, Linux still has this annoying little cmd line thing that brings back a myriad of heartbreak when I first tried to cut my teeth on Linux.

ATI driver can be installed through synaptic, and flash player can be installed via the little pop-up bar in firefox that tell you to install the plugin.  No need to touch the CLI for either of these.

It seems old-fashioned, but typing "apt-get install flashplayer-nonfree" is so much faster than clicking through a GUI.  Once you know the basics on the linux CLI it really does make life easier.  GUIs are great for some tasks, but there are many that once you learn on the LCI you realize that they are just more efficient there.  Thats why the CLI is still so prominent here, we use the best tool for the job, and while it might not be the sexy choice, sometimes thats the CLI.

---

### Post by z0phi3l on 2007-09-13
You better get used to the CL if you ever want to be an Admin or a server oprator, even in the Windows world the CL is THE best way to get most tasks done.


 Microsoft LIED to us when they said the CL was dead when Win2K came out, heck between Linux AND Windows (job) I use the CL more than the GUI, and I use the CL more at work working win Win2k and WinXP than I do at home with UBUNTU

---

### Post by science4sail on 2007-09-13
i concur

---

### Post by sstusick on 2007-09-13
> **igknighted said:**
> It seems old-fashioned, but typing "apt-get install flashplayer-nonfree" is so much faster than clicking through a GUI.  Once you know the basics on the linux CLI it really does make life easier.  GUIs are great for some tasks, but there are many that once you learn on the LCI you realize that they are just more efficient there.  Thats why the CLI is still so prominent here, we use the best tool for the job, and while it might not be the sexy choice, sometimes thats the CLI.
I couldn't agree more.

---

### Post by John.Michael.Kane on 2007-09-14
> **Maestro23 said:**
> If you are running the 64-bit version of Ubuntu:

Flash doesn't natively work on the Ubuntu 64-bit edition.  You will have to use the work-around in the following link.

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

On top of that method there's the one below
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

[ Flash script for Feisty 64.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.6.tar.gz")
Instructions
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.


As for your dislike of the CL you will need to adjust to using it, As almost every guide, and method posted on this forum makes use of the CL in some way. 

Also when members are answering your support questions be prepared to deal on a CL base. As most of the info you will be asked to post will come from the command output from the terminal.

---

### Post by newman on 2007-09-14
1. CLI is extremely useful is any OS.
2. 64bit OS is not ready for prime time - stick with 32bit unless you have a specific app that requires 64bit.
3 ATI sucks monkey balls to no end.

---

### Post by Maestro23 on 2007-09-14
> **SD-Plissken said:**
> On top of that method there's the one below
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

[ Flash script for Feisty 64.]("http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.6.tar.gz")
Instructions
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done.


As for your dislike of the CL you will need to adjust to using it, As almost every guide, and method posted on this forum makes use of the CL in some way. 

Also when members are answering your support questions be prepared to deal on a CL base. As most of the info you will be asked to post will come from the command output from the terminal.

Didn't know about the script for Feisty 64.  Thanks for educating me Plisk. :smile:

---

### Post by nonewmsgs on 2007-09-14
> **newman said:**
> 
2. 64bit OS is not ready for prime time - stick with 32bit unless you have a specific app that requires 64bit.
.

what a flame
64 bit is quite ready for the prime time.  it has many performance enhanements  but adobe refusing to make a 64bit version is not its fault.  i have been using the 64bit for a while and i love it.

---

### Post by John.Michael.Kane on 2007-09-14
> **newman said:**
> 2. 64bit OS is not ready for prime time - stick with 32bit unless you have a specific app that requires 64bit.

This not correct there are users that have issues under 32bit as well.

Also 64bit is ready for many users, and there are many who currently run 64bit only, however. If 64bit is not ready for prime time on your system or for needs then you should say that. however. To make a blanket statement that 64bit is not ready is not right.

---

### Post by John.Michael.Kane on 2007-09-14
> **Maestro23 said:**
> Didn't know about the script for Feisty 64.  Thanks for educating me Plisk. :smile:

No problem. not many use that script, As it currently only supports flash. Most 64bit users still need the 32bit firefox script which allows for java and flash.

---

### Post by Dan-O on 2007-09-14
Guys...I loaded the 32 bit Ubuntu 7.04 OS on the big machine and it's working like a champ.

I read through where someone said to use the "restricted" packages.  So, I went to the "Add/Remove" thing in Ubuntu and downloaded the packages.  Everything installed fine and I didn't have to CMD line at all....thank goodness.

I downloaded 32-bit Kubuntu 7.04 for the Dell Inspriron 1501 and performed the same operation with the Adept Manager and it's working as well.

Now....

Now that most everything is working and I can browse in a normal manner, I will take some time and learn command lines. 

Thanks for all the help.
Dan-O

---

