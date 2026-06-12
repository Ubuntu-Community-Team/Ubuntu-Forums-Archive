---
title: "How do I install software"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by kappa962 on 2005-12-30
I've used computers extensively for over 20 years(DOS and Windows), and searched all through this forum, but I can't seem to figure out what the heck I'm doing.

I have downloaded Firefox 1.5 since Ubuntu comes with 1.07. After downloading it, I was no closer to running 1.5 than before except I had a .gz file sitting on my desktop forever that I couldn't figure out what to do with.  Finally I found a webpage that mentioned zcat, so I did zcat firefox-1.5.tar.gz | tar xvf, which gave me a firefox folder on my desktop in addition to the .gz file, but still no idea of how to install firefox 1.5.

I also downloaded java for linux, with a similar result, except I had to find the sh command instead of zcat. But I'm in the same situation here: now I have a .bin and a folder for java on my desktop, but I don't know that I'm getting closer to having it installed.

I've been in the windows world for too long-- I'm used to just double-clicking on a downloaded file and having the program be installed. I have no idea where else I can look for information on how to do this.
        -Mark

---

### Post by rjwood on 2005-12-30
Hi and Welcom aboard,

Search "Automatix" by arnieboy and you will be on your way...Good Luck and again---Welcome!:)

---

### Post by 23meg on 2005-12-30
Take a look at this first: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

For Firefox see this: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

For java, this: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by kappa962 on 2005-12-30
[QUOTE=rjwood]
Search "Automatix" by arnieboy and you will be on your way...Good Luck and again---Welcome!:)[/QUOTE]

Thanks. That looks like it will do the trick, but surely there is another way to install software besides using a custom installation program? I'm not scared of the command prompt, I just don't have a clue where to find a thread or webpage that will explain what I need to know.

---

### Post by Nomearod on 2005-12-30
Install software in Ubuntu is much more easy than in Windows. You just need to learn how to do it.

Synaptic is probably the easiest way to install software. Go to System - > Administration and Open synaptic.

You just need do enter the name of the program an it install it.

To install FireFox 1.5. You could had a repositourie with it in Synaptic or just use Automatix.

To know how to isntall Automatix check this thread:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Other way to install things in Ubuntu is use a *deb package.

If you download a *deb package you just need to enter this in the console:

sudo dpkg -i  name-of-the-program.deb

It will install the program that you downloaded.

If you want to know more about this, and know how to have more than 17.000 ready to install in Synaptic. Check this site:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)

One of the most important parts is this:

[http://ubuntuguide.squarecows.com/doku.php#repositories](http://ubuntuguide.squarecows.com/doku.php#repositories)

---

### Post by rjwood on 2005-12-30
In my experience on Ubuntu, just doing what I have needed to do on a daily basis is how I have learned. As you install "automatix" you will be learning. If you read the entire 'automatix' thread you will learn alot about the process and how bugs and enhancements occur. It's fasinating to me. Then again, I don't have the experience you do so, your route may be different. Either way it all works!:) Happy to converse with you!

---

### Post by steve.horsley on 2005-12-30
[QUOTE=kappa962]Thanks. That looks like it will do the trick, but surely there is another way to install software besides using a custom installation program? I'm not scared of the command prompt, I just don't have a clue where to find a thread or webpage that will explain what I need to know.[/QUOTE]

OK. Since you asked - here's how I installed firefox for myself.

Unzip the tarball. I had previously listed the contents of the tarball and seen that it contains a directory called firefox, so I know that this directory will be created when I unzip it. To list the contents instead of extracting, use option t (tabluate) instead of option x.
(options are Xtract, Verbose, gZipped, Filename)
```
tar xvzf firefox-blah.tar.gz
```
Rename the folder that you just unzipped (I tend to keep several versions around)
```
mv firefox firefox-1.5
```
Copy the newly created directory to where I want the install (/opt). 
I deliberately copy the folder rather than move it in order to get the file ownership set to root.
```
sudo cp -r firefox-1.5 /opt
```
At this point I can run firefox with the command **/opt/firefox-1.5/firefox**. Before trying this as a normal user, I have heard that you must run Firefox as root first time round so that it can create some needed files in its install directory. I don't know if it's still true, but I do it just ot be safe. I use these two commands to launch firefox as root, and then exit again:
**Update**: It seems this step is not really needed - it's only the "talkback" feature that needs it. I am also worried that this step might create some files in your .mozilla folder that are owned by root and therefore not writeable as you. So if you do this, you may also need to fix up the ownership again, and I have added those commands
```
sudo su
/opt/firefox-1.5/firefox
(close firefox again)
chown -R steve:steve ~/.mozilla
exit
```
Firefox is normally launched with the command **firefox**, which is a link in /usr/bin. This needs removing, and a new link to the new folder creating instead:
```
sudo rm /usr/bin/firefox
sudo ln -s /opt/firefox-1.5/firefox /usr/bin/firefox
```
You can delete the old version of firefox when you are happy the new version is working, or leave it there (as I have). You can also delete the directory tree that you unzipped before copying to /opt:
```
rm -rf firefox-1.5
```

Hope this helps
Steve

---

### Post by kappa962 on 2005-12-30
You guys are awesome. Thanks.
       -Mark

---

### Post by rjwood on 2005-12-30
This is the place to be!!!

---

### Post by lostinubuntu on 2005-12-31
Hi! I'm also a ubuntu newbie and also am having problems installing FireFox 1.5. 

I read the instructions at _[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)_ but I am still totally lost on how to carry out the installation.

It says "Download [WWW] firefox-1.5.tar.gz from [WWW] mozilla.com, and change to the directory you downloaded it to." --> what do they mean by 'change to the directory?'

"Install it to /opt/firefox:" --> i'm sorry but what does this mean too?

 From the code below,

 "sudo cp firefox-1.5.tar.gz /opt/
 cd /opt
 sudo tar xzvf firefox-1.5.tar.gz
 sudo rm firefox-1.5.tar.gz"
 
I know we're supposed to key in this codes, but where do we key them in? Do we key them in "Applications -> Accesories -> Terminal"? I tried doing so, but i keep getting error messages like this:

cp: `firefox-1.5.tar.gz': specified destination directory does not exist
Try `cp --help' for more information.


I cannot seem to get beyond this point of the installation. Sorry for sounding like a ubuntu-dummy but hope u guys can help me out... Thanks a million!

---

### Post by WeToddEd on 2005-12-31
[QUOTE=Nomearod]Install software in Ubuntu is much more easy than in Windows.[/QUOTE]

I beg to differ, good sir.  Clicking the "NEXT" arrow is the easiest.  Infact, 99% of Windows software is installed without you knowing!  It installs itself!  So what if it's spyware, adware, and viruses?  I prefer the easy way.  I'm a Windows fan.

---

### Post by rjwood on 2005-12-31
[quote=WeToddEd]I beg to differ, good sir.  Clicking the "NEXT" arrow is the easiest.  Infact, 99% of Windows software is installed without you knowing!  It installs itself!  So what if it's spyware, adware, and viruses?  I prefer the easy way.  I'm a Windows fan.[/quote]
Then be a windows fan---who cares??

---

### Post by lostinubuntu on 2005-12-31
[QUOTE=lostinubuntu]Hi! I'm also a ubuntu newbie and also am having problems installing FireFox 1.5. 

I read the instructions at _[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)_ but I am still totally lost on how to carry out the installation.

It says "Download [WWW] firefox-1.5.tar.gz from [WWW] mozilla.com, and change to the directory you downloaded it to." --> what do they mean by 'change to the directory?'

"Install it to /opt/firefox:" --> i'm sorry but what does this mean too?

 From the code below,

 "sudo cp firefox-1.5.tar.gz /opt/
 cd /opt
 sudo tar xzvf firefox-1.5.tar.gz
 sudo rm firefox-1.5.tar.gz"
 
I know we're supposed to key in this codes, but where do we key them in? Do we key them in "Applications -> Accesories -> Terminal"? I tried doing so, but i keep getting error messages like this:

cp: `firefox-1.5.tar.gz': specified destination directory does not exist
Try `cp --help' for more information.


I cannot seem to get beyond this point of the installation. Sorry for sounding like a ubuntu-dummy but hope u guys can help me out... Thanks a million![/QUOTE]


Hi! With regards to the problem, I have managed to figure out a way to install automatix and run it to help me in the installation. Thanks anyway! :)

---

### Post by mszl_1 on 2005-12-31
hi all
this has nothing to do with firefox however i have issues installing software from cd/dvd's. i get the message i dont have the right permissions (cant give exact wording as im at work) it is easier from windows point of view but leaving windows is better. i found linux to have most of the programms i needed but i have install a couple of things to make it like i had my xp box. i understand this to be a learning curve and dont mind going through the curve. i just want to know how to install from cd or dvd. thanx

---

### Post by thepcdoctor on 2006-01-05
Quote" Install software in Ubuntu is much more easy than in Windows." 

I don't think so....

---

### Post by etc on 2006-01-05
[QUOTE=thepcdoctor]Quote" Install software in Ubuntu is much more easy than in Windows." 

I don't think so....[/QUOTE]
How so?

---

### Post by Mustard on 2006-01-05
[QUOTE=mszl_1]hi all
this has nothing to do with firefox however i have issues installing software from cd/dvd's. i get the message i dont have the right permissions (cant give exact wording as im at work) it is easier from windows point of view but leaving windows is better. i found linux to have most of the programms i needed but i have install a couple of things to make it like i had my xp box. i understand this to be a learning curve and dont mind going through the curve. i just want to know how to install from cd or dvd. thanx[/QUOTE]

I would suspect your permissions problem is to do with the files not having executable permissions.  This would be easy to change on a hard drive installation, as you could simply use the chmod command to give the files executable permission, but with a CD/DVD being read only media, I would suspect that this would'nt be so straightforward.  Perhaps copying the installation files onto your hard drive and then using the chmod command to give them permission to execute would work.

For the chmod manual try this command in terminal...

```
man chmod  #manual for chmod.  Remember to press 'q' to exit the manual.
```

If you do a search around the forums you will find many references to this process.

---

### Post by rjwood on 2006-01-05
[quote=thepcdoctor]Quote" Install software in Ubuntu is much more easy than in Windows." 

I don't think so....[/quote]

What a silly argument.. ok install one of the programs from linux in windows. Doesn't work--right?? so you sit there and keep trying and it still doesn't work. Now I can say that installing software in windows is tooooooo hard.. That's basically what the arument is in reverse.

There are sooooo many programs available for linux from sooooo many different sources that it seems flooded. There are soooo many different linux distros out there and almost anyone of theme can be interchanged (program wise that is) if you FIDDLE with it and tweek things a little. That seems difficult at first but gets fairly easy eventually. 

So you can go to the store (thats work--right) in and out of your car, deal with the sales people bring your software home- install it- and then have to pay for upgrades in about a month or so and then sit at your computer and fight against all the spam-- adware-- spyware invasions and in between that you get to use the program a little. Now thats alot of work and I consider that part of the installation and useing the programs in windows. 

On the other hand you can sit down at your computer, go to synaptic press a couple of key's and install up to like 1700 programs already compiled and ready for your OS and enjoy safe--fun--honest--computing. BTW those 1700 programs are just the real easy ones---there are thousands more outher to tweek a little (oh so hard to do) and it's all free. now you tell me which is easier.

Don't forget. in order to use your windows box you have to go to work and earn the money first---with windows that is part of installing the software if you really want to get technical about it.

I'm ranting---and I'll stop now. urggg

---

### Post by hen3rz on 2006-01-05
Hello,

Im a newb at all of this as well and i just discoverd something. On the bottom of the Applications Menu is the Add Programs button. All you do is go through and select what programs you want installed and it goes out and does it all :D :D.

I do understand that this doesnt cover everything.. but so far i have found all the programs ive been trying to install on it!

---

### Post by Chipmunk on 2006-01-05
Yep that pretty much does cover all of the basic stuff and some quite advanced stuff too. Coming from windows (6 year veteran of it lol) I found Ubuntu installs to be difficult, but then I took a step back and thought "it's not really more difficult, it's just different".

Windows just seems easier to some people because they're used to it. I first installed ubuntu for several reasons.
1. Faster than windows xp
2. More stable
3. Geek points :D
4. I wanted to learn now rather than later, windows is too expensive anymore

Yes, it's hard to adjust, I believe i am what they call a "windows power user", who are apparently the most difficult to teach new tricks, we know enough to be dangerous but not enough not to be.

However, with the help of this forum, google, and of course the easy install cd, I am making it just fine :)

---

### Post by borisattva on 2006-01-06
Hello,

I am trying to install gaim-rhythmbox plug in and following its instructsion i typed

sudo sd ./configure
which fails with 'configure error c compiler cannot create executables and instructs me to 'view config.log' i typed
'view config.log' i got a long list of lines, i found one portion which appears to be the source of the probelm, but i am having probelms understaindg is 

> configure:2396: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME "gaim-rhythmbox"
| #define PACKAGE_TARNAME "gaim-rhythmbox"
| #define PACKAGE_VERSION "1.5.0.1"
| #define PACKAGE_STRING "gaim-rhythmbox 1.5.0.1"
| #define PACKAGE_BUGREPORT "jon@oberheide.org"
| #define PACKAGE "gaim-rhythmbox"
| #define VERSION "1.5.0.1"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2435: error: C compiler cannot create executables
See `config.log' for more details.


this is actually the contents of the log, the rest was just lines upon lines of varibale setting and no explicit error. little help?

---

### Post by borisattva on 2006-01-06
figured it out... i didnt have a compiler installed.

pulling 'build-essential' from synaptic pushed the configu process much further (should something like that be installed by default ?)
but now hit a new road block where the gaim version requirement of >=0.79 is mistakenly rejecting version 1.5

a suggested instruction follows as 
> 
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the gaim_CFLAGS and gaim_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
unfortunately i dont understand what it means. typing pkg-config at the terminal yielded to nothing.

---

