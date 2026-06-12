---
title: "Firefox woes..."
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by brother_of_jared on 2005-12-22
So I download the newest version of Firefox which I believe is 1.5. I want to install it in Ubuntu or even update this one I am running right now (Version 1.0.7).

Documentation says to open the archive in the folder you wish to run Firefox from. I have it in a temp folder on my desktop... I don't want it there... How do I finish this install or better yet, how do I get version 1.0.7 to update to 1.5 ?

Thoughts?

---

### Post by fordfan753 on 2005-12-22
What I did:

Uninstall all firefox stuff
Download archive from mozilla.org
Extract the folder from the archive
Rename the folder to firefox-1.5
Copy the folder to /usr/local/lib   ie, it's now /usr/local/lib/firefox-1.5
Copy the "firefox" file from the folder to /usr/local/bin
Run firefox with the command "firefox" and yay, you have firefox 1.5

---

### Post by Vorian on 2005-12-22
[QUOTE=fordfan753]What I did:

Uninstall all firefox stuff
Download archive from mozilla.org
Extract the folder from the archive
Rename the folder to firefox-1.5
Copy the folder to /usr/local/lib   ie, it's now /usr/local/lib/firefox-1.5
Copy the "firefox" file from the folder to /usr/local/bin
Run firefox with the command "firefox" and yay, you have firefox 1.5[/QUOTE]

do that, or install automatix  [http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563") 

It will upgrade your firefox, plus install all the media codex youll need for mplayer, and alot more...

Good luck Mahonri;)

---

### Post by brother_of_jared on 2005-12-22
[QUOTE=fordfan753]What I did:

Uninstall all firefox stuff
Download archive from mozilla.org
Extract the folder from the archive
Rename the folder to firefox-1.5
Copy the folder to /usr/local/lib   ie, it's now /usr/local/lib/firefox-1.5
Copy the "firefox" file from the folder to /usr/local/bin
Run firefox with the command "firefox" and yay, you have firefox 1.5[/QUOTE]


uhmm "Run firefox with the command" hmmm.. how? Sounds like a command line thing? Sorry, but I am still VERY new to the linux way of things. Windows was "Double-Click installer, crash, double-click it again, pray, not-crash, cheer, run program, crash, swear, etc"

---

### Post by Vorian on 2005-12-22
[QUOTE=brother_of_jared]uhmm "Run firefox with the command" hmmm.. how? Sounds like a command line thing?[/QUOTE]

Follow the instructions for installing and using automatix.  It is Great.

p.s.  terminal help for beginners:) 

[http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners]("http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")

---

### Post by brother_of_jared on 2005-12-23
[QUOTE=Vorian]Follow the instructions for installing and using automatix.  It is Great.

p.s.  terminal help for beginners:) 

[http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners]("http://ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")[/QUOTE]


Where do I find AutoMatix? :confused:  This is getting confusing.. all this to run a newer version of a browser already installed?

---

### Post by Vorian on 2005-12-23
[QUOTE=brother_of_jared]Where do I find AutoMatix? [/QUOTE]
[URL="http://ubuntuforums.org/showthread.php?t=66563"]
http://ubuntuforums.org/showthread.php?t=66563[/URL] 

Read the thread, its much more than installing a browser.  Intalling plugins (not extensions) is a bit different in linux than in windows.  

Good luck Mahonri ;)

---

### Post by brother_of_jared on 2005-12-23
[QUOTE=Vorian]Good luck Mahonri ;)[/QUOTE]

You even spelled it right.. cool :cool:  Wonder how you know that name.. :eek:

---

### Post by akniss on 2005-12-23
[QUOTE=brother_of_jared]So I download the newest version of Firefox which I believe is 1.5. I want to install it in Ubuntu or even update this one I am running right now (Version 1.0.7).

Documentation says to open the archive in the folder you wish to run Firefox from. I have it in a temp folder on my desktop... I don't want it there... How do I finish this install or better yet, how do I get version 1.0.7 to update to 1.5 ?

Thoughts?[/QUOTE]

If all you want is firefox 1.5, then there's really no need for automatix (unless you want it, I don't want to seem like I'm persuading against it).  This thread will step you through it.  I have very little linux experience and it worked for me with no trouble at all.
[http://www.ubuntuforums.org/showthread.php?t=79283](http://www.ubuntuforums.org/showthread.php?t=79283)

---

### Post by towsonu2003 on 2005-12-23
Couldn't understand how this thread went to automat... For firefox, just follow all installation steps one by one in [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

You do **not** need to remove 1.0.7 or add anything else other than firefox. Follow the wiki instructions.

I personally am more or less against tools like automatix because it will stop your learning. You have to learn this thing to use it, and every step in installation will help you learn more. 

Some automation is nice, but even that is too much sometimes...

I understand your frustration with installing new stuff and it being hard... Well, as long as you stick to synaptic (apt-get front end; System > Administration > Synaptic -hit reload for a list of applications while connected to internet), it is easier than Windows. Once you go outside the repositories (pool used by synaptic) then it is hard. Even then, installing firefox by following the wiki page is very easy when comparing to other installation methods...

As a side note, I do not remember how many programs I failed to install because I did not know about package managers and repositories... Compiling is sometimes hard, especially when you don't understand what it is telling you... Anyway, as a newbie, you (and I) should not have to compile anything unless you really need a crucial program that is not in repositories (very unlikely) or unless you need some special drivers (someone from the forum will help after you do the homework ;) )

Also, well, you will get used to it just like you got used to double clicking .exe files... People (me included) learn how to use windows so early that they forget they had to learn how to use it... 

Good luck and enjoy. If you follow the wiki but can't install firefox, you might wanna post a new thread and specify that you followed the wiki step by step.

---

### Post by Vorian on 2005-12-23
[QUOTE=towsonu2003]Couldn't understand how this thread went to automat... [/QUOTE]

I think for a noobie, especially a MS noob, automatix is a great way to save days (or weeks) of compiling.  First thing they have to overcome is the terminal, then apt-get vs synaptic vs .....  then theres dpkg at untar etc...

I remember being new to ubuntu/linux, it was very frustrating.  Thats why I suggested automatix for firefox, because it helps solve the next question of how to install mplayer:p    

Just trying to help a noob:???:

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=Vorian]it helps solve the next question of how to install mplayer[/QUOTE]
lol :) yes indeed

---

