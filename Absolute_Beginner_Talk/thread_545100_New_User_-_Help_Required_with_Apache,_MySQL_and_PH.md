---
title: "New User - Help Required with Apache, MySQL and PHP"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by alan4573 on 2007-09-07
Firstly I would like to say Hi to everyone and thanks for this aweswome software.

I am very new to Ubuntu but not computing and on a very steep learning curve.

I installed Ubuntu (Feisty Fawn) on an old laptop two or three days ago and have encountered the usual problems and have managed to get round them. Main issue was with graphics card (Nvidia GeForce Go 5700). Resolved this by doing a completely clean install of Ubuntu and using Envy. (I still get freezing and crashing though if I try and use Desktop Effects but no doubt I will manage to figure that one out sooner or later - had the same issues with Vista but got there in the end).

Anyhows, now on to the main issue. I want to use Ubuntu primarily for web development as it has numerous advantages over Windows. When I first installed, I was able to install Apache2, Mysql 5 and PHP 5 and get them running no problem by following the instructions I found here somewhere. I used apt-get etc etc - (I'm still unfamiliar with the terminal so bear with me on that). I do loads of stuff using Joomla and I installed a Joomla on a test site no probs. That was when I started having graphics issues so I did a clean reinstall. Since then, I have tried to reinstall Apache2, MySQL 5 and PHP 5. All seemed to be OK. I can connect to MySQl and create databases et (I use Navicat - commercial windows APP through Wine), however when I tried to install Joomla, I got an error during set up saying there is no MySQL support. In Windows this would normally mean editing the PHP.ini file and adding support for MySQL but I haven't got the faintest idea where to find this file in Joomla and as I had the system working previously, I don't think there is a need to do it if the correct apps are installed.

So, my question is - what is the best way to get Apache2, MySQL5 and PHP5 up and running on Ubuntu? (Step by step please - I am still struggling with all the new terminology). I am prepared to do a reinstall of Ubuntu and start from a clean slate if required.

As I said, I would dearly love to dump Windows but until I can master this I can't afford to.

Thanks in advance for all your help.

Alan

---

### Post by hyper_ch on 2007-09-07
[http://www.howtoforge.com/perfect_setup_ubuntu704_p4](http://www.howtoforge.com/perfect_setup_ubuntu704_p4)  --> for mysql

[http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6) --> for apache/php5

---

### Post by alan4573 on 2007-09-07
Wow - that was quick.

Thanks. Will try that tonight.

---

### Post by frrobert on 2007-09-07
If you just are doing development and not trying to setup a production server  use xxamp from Friends of Apache  [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")
It is a preconfigured package of Apache, mysql, and php, along with ssl and ftp.
It is a quick and easy to install, extract and run.  You can configure it for either php4 or 5.  It uses 5 by default.

Hope this helps

---

### Post by alan4573 on 2007-09-07
Yes - it is purely a development server for testing.

All my live production sites are hosted externally.
This sounds like it could be the ideal answer.

Thanks for the suggestions so far.

Oh, just remembered one more quck question. I know that DW8 works with wine, but I prefer to use DW6 (I know - it's just my personal preference) - anybody know if that runs under Wine?

Cheers

---

### Post by hyper_ch on 2007-09-07
check out the wine appdb on their homepage ;)

---

### Post by jingo811 on 2007-09-07
> 
So, my question is - what is the best way to get Apache2, MySQL5 and PHP5 up and running on Ubuntu? (Step by step please - I am still struggling with all the new terminology). I am prepared to do a reinstall of Ubuntu and start from a clean slate if required.

In that regard this worked for me, however I can't adress your other problems.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

---

### Post by alan4573 on 2007-09-07
> **frrobert said:**
> If you just are doing development and not trying to setup a production server  use xxamp from Friends of Apache  [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")
It is a preconfigured package of Apache, mysql, and php, along with ssl and ftp.
It is a quick and easy to install, extract and run.  You can configure it for either php4 or 5.  It uses 5 by default.

Hope this helps

Hi,

I've tried this solution but no joy.
Downloaded the package to my desktop.
 Now I'm stumped. I extracted the contents of the package to the location specified and I get the LAMP folder, not xampp.

Then I am asked to log into a terminal as root by typing su. Did this and a password was requested. I enter the only password I have ever set up and I get an authentication error. In sheer exasperation, I have decided to reinstall Ubuntu and start again from scratch. 

How on Earth am I supposed to extract and install this package? In English and not Linux speak please. Why does even the most basic thing in Linux have to be so difficult? Why can't I download something , double click it and install it like I did in Windows?

I fear my foray into Linux may be coming to an end. I fully appreciate to have to learn some things, but why oh why is this so user unfriendly? I want to learn and use this so much, but there are barriers every step of the way. It feels like Linux does not want to convert Windows users.

All I want is a web server with MySQL and PHP. A simple task in Windows but a(nother) nightmare in Linux.

As you can guess I am a little frustrated.

Any help would be greatly apreciated before I give up on Linux and carry on topping up Gates' coffers. Basically, I'd rather pay (even if it is extortionate) for something that works rather than keep having to reinstall a whole OS because it is so use unfriendly.

Apologies for the rant - please please someone tell me step by step how to do this - remember I am totally new to Linux and things like "open a terminal and log on as root" means diddly squat to me.

Thanks:confused:

---

### Post by hyper_ch on 2007-09-07
just look at the howtoforge pages that I posted... they work :)

---

### Post by alan4573 on 2007-09-07
Thanks Dude,

I'm installing Gutsy now on my other box (In for a penny in for a pound as they say) - will let you know how it goes after it's done.

BTW - Gutsy looks awesome so far - I am starting to like Linux again  :lolflag:

---

### Post by alan4573 on 2007-09-07
> **hyper_ch said:**
> just look at the howtoforge pages that I posted... they work :)

Oh dear - here we go again.

Tried the very first thing and got this error message:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
alan@alan-ubuntu:~$ 


What is root? How do I log in to the terminal and get this thing to install?

---

### Post by Xyphus on 2007-09-07
root is synonymous with Administrator in Windows.  Ubuntu disables root access by default, but by using the command "sudo" (Super User Do) you can gain temporary admin rights.  When installing a package, you would issue the install command by prefacing it with "sudo"

ie:  sudo apt-get install (package name)

It will then ask you for your password, and once you enter it, it will proceed to install and configure the requested package.

---

### Post by alan4573 on 2007-09-07
> **Xyphus said:**
> root is synonymous with Administrator in Windows.  Ubuntu disables root access by default, but by using the command "sudo" (Super User Do) you can gain temporary admin rights.  When installing a package, you would issue the install command by prefacing it with "sudo"

ie:  sudo apt-get install (package name)

It will then ask you for your password, and once you enter it, it will proceed to install and configure the requested package.

Ah - now I understand. Pretty obvious really when you think about it.

Thanks a bunch.

---

### Post by alan4573 on 2007-09-07
Tried all this - no good. 

MySQL appears to work ok but PHP doesn't. When I try install Joomla I get a FF pop up saying "You have tried to open            which is a PHTML file from: [http://localhost](http://localhost)

Something is obviously cream crackered so I now need to uninstall Apache, MySQL and PHP and start over. How do I do this?

And More Importantly how do I get this to work?
This is farcical - and I am computer literate. This is precisely why Linux wil never ever overtake Windows. It's just too complicated to get the simplest things to work. 99.99% of computer users just want to be able to click an icon and everything works. I like a challenge I really do, but I am going to give this one last chance (if someone can give me instructions that actually work) on how to get Apache, MySQL and PHP up and running before I consign Linux to the dustbin and advise anyone I know never ever ever to go near it unless they fancy wasting hour after hour pulling out their hair.

Like I said, I'd rather pay for something that works rather than spend hours trying to get it to work - after all, time is precious - you only get it once. Once it's gone, it's gone - you never get it back.

---

### Post by alan4573 on 2007-09-07
> **jingo811 said:**
> In that regard this worked for me, however I can't adress your other problems.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

At last - a method that works. Thank you a thousand times.

Now I just need to figure out why I get crashes if I try a 3D game.

---

### Post by frrobert on 2007-09-07
Open a terminal window
change to the directory the downloaded file is in

run the following in the terminal  ```
sudo tar xvfz xampp-linux-1.6.3b.tar.gz -C /opt
```

to extract the file the password will be your linux password.

to run xampp type the following in the terminal ```
sudo /opt/lampp/lampp start
```

> **alan4573 said:**
> Hi,

I've tried this solution but no joy.
Downloaded the package to my desktop.
 Now I'm stumped. I extracted the contents of the package to the location specified and I get the LAMP folder, not xampp.

Then I am asked to log into a terminal as root by typing su. Did this and a password was requested. I enter the only password I have ever set up and I get an authentication error. In sheer exasperation, I have decided to reinstall Ubuntu and start again from scratch. 

How on Earth am I supposed to extract and install this package? In English and not Linux speak please. Why does even the most basic thing in Linux have to be so difficult? Why can't I download something , double click it and install it like I did in Windows?

I fear my foray into Linux may be coming to an end. I fully appreciate to have to learn some things, but why oh why is this so user unfriendly? I want to learn and use this so much, but there are barriers every step of the way. It feels like Linux does not want to convert Windows users.

All I want is a web server with MySQL and PHP. A simple task in Windows but a(nother) nightmare in Linux.

As you can guess I am a little frustrated.

Any help would be greatly apreciated before I give up on Linux and carry on topping up Gates' coffers. Basically, I'd rather pay (even if it is extortionate) for something that works rather than keep having to reinstall a whole OS because it is so use unfriendly.

Apologies for the rant - please please someone tell me step by step how to do this - remember I am totally new to Linux and things like "open a terminal and log on as root" means diddly squat to me.

Thanks:confused:

---

### Post by hyper_ch on 2007-09-08
you think operating a LAMP server belongs to the simplest things that computer users do?

is PHP enabled?
```

sudo a2enmod php5

```

---

### Post by jingo811 on 2007-09-08
> At last - a method that works. Thank you a thousand times.
You should've listened to me in the first place.  I went through the exact confusing experience as you when I wanted to go from WAMP to LAMP.

---

