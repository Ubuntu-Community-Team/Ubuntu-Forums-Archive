---
title: "Total Linux Newbie"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by triggfamily on 2006-11-11
I know you guys have heard this many times before, but I am a total Linux newbie. I switched from Windows XP to Ubuntu Edgy about 2 weeks ago, and I think I have done rather well so far.  I have been using this website to figure out how to install programs, transfer files from Windows (I did a complete wipe before I figured out I needed to 'convert' certain files).  I have mpeg working on Totem and many other things.  I think I get the hang of this somewhat; however, some of the language you use is still foreign to me.

What I am trying to figure out right now is that I am so used to how Microsoft ran things that I don't know if it is necessary in Ubuntu such as:

1.  I used to run pop up blockers, AV, AS, and such on Windows to keep from getting bombarded with stuff.  Is there any kind of security measures I need to take with Ubuntu?  I read some of the documentation and tried to install something to check my vulnerability, but the install didn't work.

2.  Because of the way the file system is in Ubuntu, I am figuring I don't need to run something similar to a Defrag, but is there any residual files to be removed from surfing the net or installing and uninstalling programs/packages?

3.  While my Internet works just fine, is it possible to share files on my home network?  I have 2 other computers running Windows XP (1 pro/ 1 home), and sometimes I need to swap files back and forth.

4.  Is there any suggestions (I know there are lots of them) on how to make my experience with Ubuntu more fantastic than what it is?

5.  Is there a way that when I am running Evolution and click on a link in an email that it opens up Firefox to view it?  Right now I click on the link and nothing happens, then I have to open up Firefox, go back to my email and click on it again.  then it opens a new tab.

6.  I had a problem yesterday with an activeX on a website and Firefox, I could find no plugin for version 2.0???

I thank everyone for their suggestions and support in advance.  I absolutely love this program and it is nice to have a trustworthy solution other than Microsoft to run.  This program has impressed me tremendously, with such a smooth install and everything else has been much smoother.  I know there are answers out there for my questions, but I don't understand what they were saying (the language was just a little over my head).

Triggfamily

---

### Post by ThrobbingBrain66 on 2006-11-11
1. Ubuntu already has a built-in firewall called iptables, however you can install a frontend for configuring it.(sudo aptitude install firestarter)

2.  you can use ```
sudo aptitude autoclean
``` to clear out junk filesand use the 'Installed (local or obsolete)' function in synaptic to get rid of packages that are no longer needed--becareful with this though, not all packages listed are not needed, be sure to read the description before deleting.  also installing localepurge gets rid of a lot files you dont need.

3-5 sorry, cant help there.

6.  you can try to install beryl or compiz for some super sweet eye-candy if your computer is robust enough. [http://www.ubuntuforums.org/showthread.php?t=272104](http://www.ubuntuforums.org/showthread.php?t=272104)

---

### Post by kvonb on 2006-11-11
Some quick answers:

1) No! Relax and enjoy the freedom, these stone-age tools are not needed in Ubuntu

2) No! Relax and enjoy the freedom.

3) Easy, run Nautilus (file manager), right click on a folder and select "share folder", go through the questions.

4) Automatix, [http://ubuntuguide.org/wiki/](http://ubuntuguide.org/wiki/), these forums (feel free to ask as many questions as you like, you will be treated very well).

5) Dump Evolution and install Thunderbird instead.

6) Sorry, I know nothing about activeX :)

Above all, welcome to Ubuntu and congrats on taking the plunge, it can be a bumpy ride, but I believe it is well worth it.

There are so many applications available for Ubuntu that I'm sure you will eventually find just about everything you will need, if not, just ask on the forum, someone should be able to help.

Have a look at the links in my signature below, they lead to some useful info (and some rubbish :D), but you might find something useful to make Ubuntu even more fun.

Regards,  Kev :)

---

### Post by mark_g on 2006-11-11
1. You don't really need an antivirus scanner in ubuntu, unless it's a mailserver or something. Windows viruses can't run on Ubuntu, so... Also, if you use Firefox, it can block popups.
What program did you try to check for vulnerabilities? You can use Nessus to check for this, although this is also more appropriate for servers.

2. There is a defrag program for ext2 filesystems, however, I've never used it, so you probably won't need to either.
There is a 'cache' which stores web pages, but you can empty that in your browser settings or e.g. in Firefox "Extra" > "Clean Private Data"
If you uninstall a program, it is possible that there are 'orphaned' programs. Also, apt-get stores all the packages you have downloaded in a cache directory. This includes previous versions of programs you have on your system. 
Apt-get autoclean is a good start to clean this up, but there are more ways.

3. Sure. You could use samba to share windows network resources. Personally, i use ubuntu as an ftp-server to share files, so whatever you prefer.

4. Read and experiment is the way for me. Also, the Ubuntuguide is really helpful for beginners as well as these forums of course.

5. Can't really help you since I don't use Evolution anymore. Maybe a little bug in Evolution, not sure.

6. Never had that, maybe if you could say which website it was, I can see.

---

### Post by triggfamily on 2006-11-11
1.  This isn't a mailserver...so I guess I will take the advice and enjoy my freedom...I have seen the popup blocker on firefox work....I just am trying to figure out where I can go to change a setting (such as I say to allow popups on that site, but later I change my mind)  And nessus is what I tried to install, but I got lost somewhere or my computer did and it came back off....I didn't understand it one bit.

2.  will use the autoclean and private data to start....sounds pretty easy

3.  will try the couple of suggestions for this...I don't understand the ftp-server thing though....I just hope I can get the computers to see each other.

4.  I feel like I have read lots of things, thus all the stuff I have done already to the computer, will keep playing....that's the fun part...install and uninstall till I find something I like.  I just have to be able to understand sometimes.  (been doing lots of internet searching)

5.  If evolution is so bad...why have it with the package....guess I need to figure out how to switch from evolution to thunderbird.

6. this is the website I was at yesterday...there is a free song I was trying to download...

[http://www.homemadesimple.com/en_US/download.do;jsessionid=60194BB713E0BC42407B377C751D3F70?method=installActivex](http://www.homemadesimple.com/en_US/download.do;jsessionid=60194BB713E0BC42407B377C751D3F70?method=installActivex)

---

### Post by bollix47 on 2006-11-11
To allow a pop-up on a certain website open firefox and go to:

edit - preferences - content - block pop-up windows - exceptions

Type the domain name (e.g. ubuntuforums.org) and click on allow.

As to active X I know of no way to get this for the linux version of firefox.  You could try installing the windows version under wine but I doubt you want to get into anything that complex if you're just starting out.

Good luck and enjoy the experience.

---

### Post by triggfamily on 2006-11-11
Thank you...I have heard ALOT about wine...but I haven't exactly figured out what that is, where it is, or how to use it yet...

I am installing thunderbird now...and will get that up and running before deciding to remove evolution, but I don't see where to uninstall evolution...

---

### Post by localuser on 2006-11-11
Welcome aboard triggfamily.  I think you'll not find a more helpful group than on these forums.

Come back with any questions you have.  Keep in mind that many of your questions will already have been answered, so you can always search the Ubuntu forums to see what you find.  Also, remember that Google is your friend.

Enjoy your newly found freedom :)

---

### Post by That_Geek on 2006-11-11
you should be able to uninstall evo by unselecting it in the add/remove window

---

### Post by triggfamily on 2006-11-11
didn't see evo in the add/remove window...

also thunderbird is doing the same thing as evo did...I have to open up firefox manually before clicking on a link in an email...the link itself doesn't open up firefox for me....maybe I am just used to microsoft and am asking too much?

Triggfamily

---

### Post by raqball on 2006-11-11
I use evolution and don't have any issues with it. Thunderbird is not a PIM like Evolution is 

[[[shrug]]]

---

### Post by triggfamily on 2006-11-11
Do you not have a problem with links in an email opening up firefox then when you use evolution?  I kindof like evolution better than thunderbird...and as it stands I can't get either one of them to do it anyway....

Here is another question...I had my sys lock up the other day, but I can't ctrl+alt+del like in windows to shut it down to restart....I had to power off the puter instead.....how should I handle this when it happens?

Triggfamily

---

### Post by localuser on 2006-11-11
> **triggfamily said:**
> didn't see evo in the add/remove window...

Go to System | Administration | Synaptic Package Manager

This is a better way to add/remove software packages

> **triggfamily said:**
> also thunderbird is doing the same thing as evo did...I have to open up firefox manually before clicking on a link in an email...

See if this helps...

Go to System | Preferences | Preferred Applications

Choose which applications you want to have the system open automatically

---

### Post by triggfamily on 2006-11-11
Thank you...I got it to work with the preferred applications link...

I do like the package manager, but I haven't totally figured it out yet...coming from windows to linux is a big step when you are used to the add/remove window.  I have installed alot from manager though and I am learning alot.  doing a search on evolution in the package manager did find it, however since you fixed my other problem I don't think I will get rid of it.

Thank you

---

### Post by localuser on 2006-11-11
> **triggfamily said:**
> however since you fixed my other problem I don't think I will get rid of it.

There's no particular reason to get rid of it, other than the nagging feeling that its sitting there wasting hard disk space.  But if you can sleep at night knowing this, then I would just leave it alone ;)

---

