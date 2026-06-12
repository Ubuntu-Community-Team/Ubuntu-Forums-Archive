---
title: "How to Help Yourself"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2006-03-11
I thought it might be nice if we all contribute some tips on common ways to solve problems. If there is a similar thread please let me know and perhaps we can merge them or at least reference it. Also, I will make another post in this thread containing a list of all the commands, configuration files, and all of the URLs. Finally, I strongly encourage others to contribute their ideas and I will add more ideas if they occur to me. Perhaps if there is enough demand, we can make a wiki (again if doesn't exist already)

1. Search this forum (not just the beginner section) 
2.    **[https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")**  The first stop for Howtos.
2.a.**[http://doc.gwos.org/index.php/Main_Page]("http://doc.gwos.org/index.php/Main_Page")**  This looks fantastic! Thanks matthew!!
2.b.**[http://help.ubuntu.com]("http://help.ubuntu.com")** "*The main Ubuntu documentation website*" Thanks mattheweast!

3. **[http://tldp.org/]("http://tldp.org/") **more Howtos and tutorials and even book-length works.

4. **[www.google.com/linux]("http://www.google.com/linux")** One of the best all-purpose tools. Often I'll type in parts of error messages and find anothers solution very quickly; or I'll get ideas for further research. Also I frequently can help someone else by finding drivers or even solving their problems by getting information they didn't have; and learn something in the process.

4a. [http://sourceforge.net]("http://sourceforge.net") and [http://freshmeat.net]("http://freshmeat.net") These sites are great for finding more Open Source Software. Sometimes you can find some project here that will solve an unusual problem.

4b. The software manufacturer's website: Use the website's* search* feature, look for *documentation*, and look for* mailing list archives*. 

5. **synaptic**: Search the repositories of nearly 18,000 packages to find the best tool for the job. If one isn't working, maybe you can find another of a similar type. There is a search function in synaptic that makes it easy to find packages.

6. **man** pages. These are on your system and are essential reading. The information is terse, but it is another good starting point. If your looking for man pages related to a topic try this: **man -k keyword** This will give you a list of man pages with brief descriptions. The command name and description is searched. I use this all the time.

7. **locate**: Of course you can use the **find** command, but this is much easier to use and you don't need to learn the special language of regular expressions. You do need to update the database that locate uses. You do this with the **updatedb** command: ```
sudo updatedb
``` If you install software and need to search the new files, you run this first. Note: this can take a little time, so don't worry if your terminal doesn't respond. You can run this in the background with ```
sudo updatedb &
``` or just make another tab in your terminal (if you use gnome-terminal) with CTRL-SHIFT-T When it is done you just type:```
locate keyword
``` You don't have to know the whole filename. If your looking for files related to java, for instance, just type: ```
locate java
``` 
8. **grep**, **cat**, and pipes: Often, when troubleshooting, you want information from **dmesg** or*** /var/log/messages*** or other files that have lots of information in them. If I wanted to see information in dmesg related to USB, for instance I could type:```
dmesg | grep usb
``` The vertical bar is called a pipe and what it does is take the output of the command on the left (dmesg here) and send it as input to the command on the right (grep) This is one of the beauties of Linux. Many of the command line tools can be used in this way. So if I want to find descriptions of important configuration files related to CUPS I can type: ```
man -k cups | grep config
``` You can have even more pipes in one command if you want. **cat** just outputs the information in a file and is often used with a pipe: ```
cat /var/log/messages | grep usb
``` Will give you all the lines in /var/log/messages (a very long file) that contain the word usb in it.

9. The **/etc** directory and hidden configuration files:  The **/etc** directory contains very important, global, configuration files. It has many subdirectories relating to specific software. For instance, if your trying to configure the Gnome Display Manager (gdm) you'll find it in ***/etc/gdm***.  Some other important files in the etc directory include ***/etc/profile*** which has some system-wide defaults and*** /etc/inittab*** which controls aspects of how your computer starts (especially its default runlevel). Hidden files are files that start with a period. They can be seen by using the -a switch to the ls command. type this in your home directory:```
ls -a
``` and you'll see lots of files and directories that begin with a period. These are your user configuration files and are very useful when configuring programs. You can find things like your bookmarks file within the your browsers' configuration directory.

10. Processes: I use the **ps** command all the time.  The most common usage is **ps -ef** Again, this can be used with grep to narrow what your looking for. Say your troubleshooting power management and you know ACPI has something to do with that. You can type: ```
ps -ef | grep acpi
``` top is a more sophisticated and powerful tool for working with processes.

11. Hardware information:

(a) **dmesg** used with grep will give you important messages related to the hardware problems you are experiencing.

(b)***/var/log/messages*** has important information. When testing a device you can do this: ```
tail -f /var/log/messages
``` This uses the tail command which, by default, gives you the last 10 lines of a file. The -f means "follow" which just keeps scrolling the last 10 lines of that file. Then you plug your device in and watch the terminal for the new entries to /var/log/messages (they are appended to the file, so by seeing the last 10 lines you can see the latest changes)

(c) **/etc/fstab** and **mount**: ```
cat /etc/fstab
``` is essential when troubleshooting devices. The man page and howtos found through the URLs given here will explain what the entries mean and how to make them. Typing mount by itself will tell you what devices are currently mounted on your system, along with other useful information.

(d) **lsmod** and **modprobe** lsmod lists the modules that are currently loaded on your system. A driver typically takes the form of a module. A module is a way to add something to the kernel (the Linux OS). When a kernel is compiled it has the most relevant options included. Options that aren't used often, or are specific to less common hardware, are included in the kernel as modules that must be loaded. modprobe adds or removes modules depending on circumstances. Often you will be adding a driver module, but sometimes you also have to remove conflicting modules.

(e) **lshal** **hal-device-manager**: HAL stands for Hardware Abstraction Layer.  According to this site: [http://www.ometer.com/hardware.html]("http://www.ometer.com/hardware.html")  referred by the HAL website: [http://www.freedesktop.org/wiki/Software/hal]("http://www.freedesktop.org/wiki/Software/hal") The purpose of HAL is to provide > a nice, user-friendly interface to the hardware of a typical desktop system. lshal lists all of the devices that IT knows about on your system (hint: use grep to find your device as this list is usually long) hal-device-manager is a GUI-based way to see your devices and can be more pleasant to use than lshal

(f) **udev**  "How come my device file keeps changing. First it was /dev/sda1 now it is /dev/sdb1 Why is this happening to me??" :) **udev** is relatively new and its function is to dynamically create devices.  In the olden days, the ***/dev*** directory was huge. Now it just contains relevant files. However, what this means is that when you plug in a device today it is given one device filename. When you plug it in tommorow it might get a different device filename. Read the man pages related to udev (man -k udev). There you can learn about writing simple *udev rules* that will, among other things, allow your device filenames to be the same every time. 

12. Software installation issues:  

(a) If your compiling software that isn't in a repository, it will typically be a ***.tar.gz*** file or ***.tgz*** file or ***.tar.bz2*** or something similar.  After you download move it to a standard installation location such as ***/usr/local*** or your home directory.  I often use /usr/local however you need to use the sudo command to move files and run commands there:
```
tar xvzf filename.tar.gz
``` Note if this is a .tar.bz2 you use a j instead of the z in the previous command (tar xvjf). Then go into the new directory that is created and read the ***README*** and ***INSTALL*** files.  Typically you will then do this inside the newly created directory
```
./configure
``` 
```
make
``` ```
sudo make install
``` **Important:** *Compiling software requires certain tools, i.e. programs. For instance, among other things, you need the "make" program and a compiler like "gcc". In Ubuntu, the simplest way to ensure you've got these is to install the **build-essential** package.* Thanks nanotube for this suggestion!

 If you get warnings, don't worry about them. If you get errors you'll need to find out why. Usually the first line of the error is most important. If your missing some library or need to update a library, often that isn't that hard to fix. You can use the repositories (look in synaptic) or, if it isn't there, you can track it down with [www.google.com/linux]("http://www.google.com/linux")

(b) Update your system regularly. Not only will this prevent software problems such as dependency issues during software installation it will also improve the operation of your software, eliminate bugs, improve the security and overall operation of your system substantially. Type this: 
```
sudo apt-get update
``` 
and then
```
sudo apt-get upgrade
``` (c) Try running the program using **sudo** just to determine if your problem is related to *file permissions* (definitely seek out a howto about file permissions)

---

### Post by cvcaelen on 2006-03-11
Usefull info in here

learned new things

Thanks

Christiaan

---

### Post by Klejs on 2006-03-11
Thanks alot for this one, learned a few new things on the way too...

---

### Post by chuckyp on 2006-03-11
You may want to correct the tips.

sudo apt-get update  (Fetches a list of packages currently availibe up to date)

Then

sudo apt-get upgrade (To upgrade any packages that you have currently installed.)

I dunno let me know if i'm wrong i'm extremely tired.

---

### Post by Iowan on 2006-03-11
Here's another good one:[http://www.howtoforge.com/]("http://www.howtoforge.com/")

---

### Post by Pragmatist on 2006-03-11
> You may want to correct the tips.

sudo apt-get update (Fetches a list of packages currently availibe up to date)

Then

sudo apt-get upgrade (To upgrade any packages that you have currently installed.)
Thanks for the correction.  I'll make the change right now in the Original Post.

---

### Post by matthew on 2006-03-11
Hey, Pragmatist!

Great post, man!! Thanks for helping the community! You get a link in my sig for sure. I would also like to suggest adding the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page") to the list.

---

### Post by Pragmatist on 2006-03-11
URLs:
[https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")
[http://tldp.org/]("http://tldp.org/") 
[www.google.com/linux]("http://www.google.com/linux")
[http://sourceforge.net]("http://sourceforge.net")
[http://freshmeat.net]("http://freshmeat.net")
[http://www.howtoforge.com/]("http://www.howtoforge.com/")
 [http://doc.gwos.org/index.php/Main_Page]("http://doc.gwos.org/index.php/Main_Page")

FILES:
/var/log/messages
/etc
/etc/profile
/etc/inittab
/etc/fstab
/dev
/usr/local
README (in newly uncompressed tarball directory)
INSTALL  (in newly uncompressed tarball directory)

COMMANDS:
man
man -k 
updatedb
locate
sudo
grep
cat
dmesg
ls -a
ps
ps -ef
tail
tail -f
lsmod
modprobe
lshal
hal-device-manager
tar
apt-get update
apt-get upgrade

---

### Post by noswal on 2006-03-11
Use this link before installing ubuntu, ideally have a second computer running.

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by kittycatsexycat on 2006-03-11
I'm not very good at the whole linux thing and have just changed back to breezy after trying dapper... Thanks for your tips...
:KS

---

### Post by Wolki on 2006-03-11
This is a seriously cool thread, Pragmatist.

Maybe you yould include a sentence about needing the -dev packages of libraries when compiling from source? This is not immediately obvious, and thus sometimes confusing people.

---

### Post by void_false on 2006-03-11
Thanks. Great work. 
I found out that I was using 'ps' with BSD syntax all the time :cool:

---

### Post by klytu on 2006-03-12
Excellent post! 

This might seem obvious, but the Ubuntu Starter Guide also contains loads of useful info. In Breezy Badger the guide is found in Help. For Hoary Hedgehog see [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/).

---

### Post by Nord on 2006-03-12
Thanks for all the links.

They should be really helpful to a newbie like myself.

Nord

---

### Post by Lord Illidan on 2006-03-12
Nice one..

---

### Post by hezral on 2006-03-15
I saw the link to this thread on your sig Pragmatis. Thanks its really helpful :)

---

### Post by jrib on 2006-03-17
Good idea Pragmatist. I am sure it will be helpful to many.

[QUOTE=Pragmatist]
```
sudo make install
```
[/QUOTE]
Just one minor thing.  I think it would be better if you recommended the use of checkinstall instead of make install so that user-compiled source still get a package and are managed by the package manager.  [http://wiki.ubuntu.com/CheckInstall](http://wiki.ubuntu.com/CheckInstall) for info

---

### Post by meborc on 2006-03-17
i guess that some tutorial videos are great for beginners :rolleyes: 

go to [http://video.google.com](http://video.google.com) and search for ubuntu or linux ... 

tip, make your browser window smaller to get better/faster video quality

---

### Post by 347tfw on 2006-03-20
I think I,m going about this all wrong I want to take agun now and shoot my computer,just started in a pc last year built my own put  in two os figured I had no bad habits to break and it might be easy to learn as much as I dislike windows(feel like big brother watching me) it was easier to understand although I,m still learning.But this linux just baffles me,I've been trying to download and install plug ins so my totem player will stream on the web I think I,m doing things right but nea,nea.,and I can,t seem to import my msn mail to my thunderbird email am I thick headed or is this common?:confused:

---

### Post by Pragmatist on 2006-03-20
> I've been trying to download and install plug ins so my totem player will stream on the web I think I,m doing things right but nea,nea.,and I can,t seem to import my msn mail to my thunderbird email am I thick headed or is this common?

That is a very reasonable question and I'm sure it is one that several people have asked before.  You should definitely post your question by starting a thread in this (the beginners) forum.  Also, you could read some of my suggestions here about how to find out more information.  

The purpose of this particular thread is to provide others with troubleshooting tips and techniques, this involves ways of gathering information, useful tools, typical  general techniques (like how to install software...but not, how to install this specific program).  The advantage of this method is that when you learn a new technique you can apply it to **many** different situations.  You learn how to solve problems in general, rather than how to solve problem X.

You are welcome to add any general tips you discover.  This thread will best serve its purpose, however, if it doesn't get caught up solving very specific, individual, problems.

Thanks :)

---

### Post by Brunellus on 2006-03-20
If and when you DO need to ask for help:

1) Ask a question, don't plead for mercy.  Thread titles like
HELP!!!!LIFE OR DEATH SITUATION!!!!! CAN'T CONNECT TO THE INTERNET!!! are annoying and unhelpful.  Say what you need to say--Can't connect to internet--wireless?--and don't freak out.  We understand that it's a crisis for you, but you won't get any further ahead by screaming bloody murder. 

which leads me to

2) Give us as much information as possible.  What hardware do you have?  What version of Ubuntu?  What did you do just before the problem?  How have you tried to fix it yourself?  How much experience do you have?

Simply crying for help in the absence of information will not get you any responses.

---

### Post by mattheweast on 2006-03-23
Nice thread, but dude: you haven't put the main Ubuntu documentation website in the list of documentation.

It is at [http://help.ubuntu.com](http://help.ubuntu.com)

Matt

---

### Post by Madpilot on 2006-03-24
A few things that will (in my experience) help you get better help:

* Start your own thread - see also the advice about giving your posting an informative title, not just something like "HELP!!!!!!!!!!!!!!!!!". A real title saves everyone's time.

Back to 'start your own thread' - especially, please don't add to one of the sticky'd threads with a new request for help - I don't know about others, but I for one don't pay nearly as much attention to the sticky threads as I do to the live ones, and it's easy for a new post with a problem to get lost on a sticky thread.

Also, I'd advise "one problem or set of problems per post" - just like in the sticky threads, if you add something totally new in the middle of an established thread it could well get lost.

Oh, and +1 to everything Brunellus says just a few posts up!

This shouldn't even need to be said, but I will: Be polite. Being rude won't actually get you help any faster - quite the opposite, in fact.

---

### Post by zourcast on 2006-03-26
I've opened a thread with a link I tought would be interesting for starters, but that thread is already way back, so a thought it would be nice to put that link here. It is a complete tutorial for beginers, on how to use linux.

[http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide]("http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide")

SD-Plissken, also replyed, with a couple of links I think are very interesting for those hwo wish to start using the command line.

[http://www.linuxdevcenter.com/linux/cmd/]("http://www.linuxdevcenter.com/linux/cmd/")
[http://www.ss64.com/bash/]("http://www.linuxdevcenter.com/linux/cmd/ http://www.ss64.com/bash/")

---

### Post by GFN-Murray on 2006-03-26
******I bought the Ubuntu 5.10 install disk, but no matter how I try to install it, the PC keeps restarting. I went throught ALL the options of the F buttons, but it still won't install. Any ideas? I can be reached on YIM as gfnmurray

---

### Post by Pragmatist on 2006-03-26
> Originally Posted by: **GFN-Murray**
I bought the Ubuntu 5.10 install disk, but no matter how I try to install it, the PC keeps restarting. I went throught ALL the options of the F buttons, but it still won't install. Any ideas? I can be reached on YIM as gfnmurray

Please start a new thread for this problem.  This thread is about giving self-help advice.

Thanks.

---

### Post by gr0kzer0 on 2006-03-28
I'd just like to point out that at http://linux.org theres a great Beginners and Intermediate Course (online, and free of course) that teaches u to do an awful lot via the command line. Even tho the gui has a reputation as "easy to use", once u know the CLI u will use it quicker and to much greater effect than fiddling with mouses and menus. Check out the courses, no harm in trying after all.

---

### Post by patrick295767 on 2006-03-30
Thank you for this very nice thread, Pragmatist !!!! This contributes to the excellence of this forum.

Cheers

---

### Post by Rwildau75 on 2006-03-31
Many thanks for this, and also for it being pinned.

---

### Post by daredevil on 2006-04-12
good work pragmastic. i also hav a thread similar to this. u may hav a look at it here.

```
[http://ubuntuforums.org/showthread.php?t=135596](http://ubuntuforums.org/showthread.php?t=135596)
```

---

### Post by daredevil on 2006-04-12
good work pragmatist. i also hav a thread similar to this. u may hav a look at it here

```
[http://ubuntuforums.org/showthread.php?t=135596](http://ubuntuforums.org/showthread.php?t=135596)
```

---

### Post by clarkth on 2006-04-19
I'm very new to Linux and of course Ubuntu.  Thanks for the tips and links, it's all starting to come together.

---

### Post by LazyBoyDash on 2006-04-26
This message helps alot. I'm really wanting to poke around and get my hands dirty, but it's frustrating to try and get things configured the first time. I've been using Windows machines as long as I can remember, so I'm not sure where to look to find programs and set them up. This will save me some time. Thanks.

---

### Post by Rinzwind on 2006-04-26
addition to the 1st post.

The command **which** locates the place of an executable inside your path.

So **which fuser** would give:
**/usr/sbin/fuser**

:)

---

### Post by confused57 on 2006-04-30
This hasn't been updated in awhile, but some of the links may be of use:

[http://www.ubuntuforums.org/showthread.php?t=13042](http://www.ubuntuforums.org/showthread.php?t=13042)

---

### Post by nanotube on 2006-05-02
by the way, you might want to add a tip to install the build-essential package, before the "installing stuff from source" bit. because otherwise you are gonna get an error that "make" does not exist, and other nasty surprises like that.

---

### Post by meborc on 2006-05-02
and the two guides (one for breezy and one for dapper) are linked in my sig.

---

### Post by barbarian on 2006-05-05
> 1. Search this forum (not just the beginner section)
2. [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) The first stop for Howtos.
2.a.[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) This looks fantastic! Thanks matthew!!
2.b.[http://help.ubuntu.com](http://help.ubuntu.com) "The main Ubuntu documentation website" Thanks mattheweast!

3. [http://tldp.org/](http://tldp.org/) more Howtos and tutorials and even book-length works.

4. [www.google.com/linux](www.google.com/linux) One of the best all-purpose tools. Often I'll type in parts of error messages and find anothers solution very quickly; or I'll get ideas for further research. Also I frequently can help someone else by finding drivers or even solving their problems by getting information they didn't have; and learn something in the process.

4a. [http://sourceforge.net](http://sourceforge.net) and [http://freshmeat.net](http://freshmeat.net) These sites are great for finding more Open Source Software. Sometimes you can find some project here that will solve an unusual problem.

4b. The software manufacturer's website: Use the website's search feature, look for documentation, and look for mailing list archives. 

Nice links set, thanks

---

### Post by Reprobate on 2006-05-06
Hello All,

I just loaded the system and, while I wrote down the answers that I gave to the prompts {building an account other than root, along with the password, et al} when the system booted up, I was unable to log in.  I know that I can go through the process again with perhaps better note-taking, but since the intallation never asked for a root password, I am hoping that there is some default that I can use.   Barring that, I am hopeful that I can at least skip some of the long download process by rewriting only specific parts.

Please let me know if there something that I did NOT do, should HAVE done, or CAN do to reclaim control of my laptop and still run Ubuntu Linux.

Thanks friends,
Reprobate

---

### Post by nanotube on 2006-05-06
you don't need a root password. 
for a quick primer on the way ubuntu manages permissions and root, check
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

basically, when you need to do something as root, you use command "sudo", and use your **user** password to authenticate.

---

### Post by Reprobate on 2006-05-06
[QUOTE=nanotube]you don't need a root password. 
for a quick primer on the way ubuntu manages permissions and root, check
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

basically, when you need to do something as root, you use command "sudo", and use your **user** password to authenticate.[/QUOTE]
NanoTube,

Oops, I have no way to log in at all.  The account that I was prompted for (and religiously wrote down the input for) I am denied access to.  The sudo thing would be fine but I can not get past the username/password screen.

Again, any help is welcome and very much appreciated.

Thanks much,
Reprobate

---

### Post by Pragmatist on 2006-05-06
[quote=Reprobate]NanoTube,

Oops, I have no way to log in at all. The account that I was prompted for (and religiously wrote down the input for) I am denied access to. The sudo thing would be fine but I can not get past the username/password screen.

*** Again, any help is welcome and very much appreciated.***

Thanks much,
Reprobate[/quote] 
This is not the appropriate place to solicit help for individual problems.  The purpose of this thread is to *provide general information* on how a person can go about *helping themselves* to solve a problem.

Please create a seperate thread for your query.

Thanks.

---

### Post by zenkoanlife on 2006-05-07
Thanks Pragmatist and all the others that posted links in this thread!  I just installed ubuntu last week and have gotten a load of good stuff from these links.

---

### Post by confused57 on 2006-05-08
This thread is a must read for anyone new to Ubuntu and Linux.  I started a thread in the "Absolute Beginner Section" that I should have posted here listing a few helpful links, many of which have already been mentioned earlier.  I hope nobody minds that I just link to the thread, rather than retyping the entire post  here:

[http://www.ubuntuforums.org/showthread.php?t=172365](http://www.ubuntuforums.org/showthread.php?t=172365)

Some excellent threads in "Absolute Beginner Talk":

[http://www.ubuntuforums.org/showthread.php?t=171507](http://www.ubuntuforums.org/showthread.php?t=171507)
[http://www.ubuntuforums.org/showthread.php?t=230634](http://www.ubuntuforums.org/showthread.php?t=230634)


[B]
Dual booting with 2 harddrives[/B] without installing Grub on the windows mbr(follow the instructions by "lha"):

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Installation Guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

**Dualboot with one hard drive**:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
Note: Setting up dualboot of Windows & Ubuntu on a single harddrive, Windows **MUST** be on a partition **prior** to Ubuntu...e.g. Windows on hda1, Ubuntu on hda2.  Windows could be installed after Ubuntu as long as it's on a partition located before the Ubuntu partition, but grub would need to be reinstalled:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857)

---

### Post by confused57 on 2006-05-10
Some Hints & Tips:

After installing Ubuntu for the first time, I recommend enabling the extra repositories(universe&multiverse), easiest way is to click "System--Administration--Synaptic Package Manager" and follow the instructions from the Ubuntu FAQ(Install Applications) link.  It can also be done by going to the terminal and entering  "sudo gedit /etc/apt/sources.list"(without quotes), then remove the # in front of anything that looks like a url.

I recommend installing "Automatix", which can be found in the forum section "3rd Party Ubuntu Projects".  

Whenever you ask for help in any Linux forum, you'll most likely get instructions to enter commands using the terminal(Applications---Accessories---Terminal).  The terminal prompt opens in your home(~) directory, prompt will end with $, after which you'll type in or preferably copy&paste the commands one line at a time, press "enter" after entering each command.  A command prefaced by "sudo" means you need root privileges to execute and will need to enter your password(after pressing "Enter").

An example:
```
cd  /boot/grub
sudo  cp  menu.lst  menu.lst_backup
gksudo  gedit  menu.lst
```

1.) "cd  /boot/grub" changes the working directory to the grub directory
2.) "sudo  cp  menu.lst  menu.lst_backup creates a backup
3.) "gksudo  gedit  menu.lst  opens the file in the text editor "gedit"(similar to notepad in windows).

Don't copy & paste any of the above commands, I've double spaced so you can see where the space is.

If you have a problem after making changes, just restore from backup by:

```
cd  /boot/grub
sudo  cp  menu.lst_backup  menu.lst
```

Linux is case sensitive when entering commands and file names.

If for some reason, you're not able to start the GUI desktop after making changes, you can press Ctrl+Alt+F1, which should get you to a text command prompt, where you can restore a backup.  Also, you need to use the text editor "nano" in the command prompt,  e.g.  sudo nano /boot/grub/menu.lst

Ctrl+Alt+F7 switches to desktop, or type "startx"(without quotes) to restart the GUI.
Ctrl+Alt+Del reboots your computer, handy to know if your system freezes.

Your "Home Folder" (Places---Home Folder) is where you'll save personal files.  Files downloaded to the desktop can just be dragged and dropped into your home folder.

Go through and read some of the links in this thread, excellent resources.

I wanted to briefly mention some of the necessary directories you may need to modify to configure your system:

```
gksudo gedit /boot/grub/menu.lst
```
This is your grub menu, where you can change which OS you want to boot first, if you're dualbooting, or add an OS to boot.

```
gksudo gedit /etc/apt/sources.list
```
This is where the repositories are located that Ubuntu uses to update your system.  Uncomment(remove the #) anything that looks like a URL to enable a repository.  I just noticed, I've already mentioned this above.

```
gksudo gedit /etc/X11/xorg.conf
```
This is the directory to make changes for such things as your graphics driver, monitor resolutions, etc.

```
sudo dpkg-reconfigure xserver-xorg
```
This is a way of configuring your system hardware, same things you can do with above, except in an interactive mode...you can change the resolutions that you want your monitor to display, graphics driver, etc.

```
gksudo gedit /etc/fstab
```
This file shows the partitions on your computer, mount points, options, etc.  Here's an excellent guide for /etc/fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

You can run the following first to determine where the partitions are located and change them accordingly in the /etc/fstab file:
```
sudo fdisk -l
```
This guide explains partitioning quite well:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Note: 1(one) and l(lowercase L) are difficult to differentiate in commands.
menu.lst(lowercase "L"),  X11(one), fdisk -l("L")

Note:  It is recommended to use "gksudo" instead of "sudo", when executing commands in the GUI.  I believe aysiu has an explanation of why
         on his "Psychocats" website...gksudo is less likely to cause problems.

I'll update this section as I go along, but wanted to mention the above for now.

---

### Post by Denim on 2006-05-31
Another new user sending thanks to all that have contributed to this thread, and forum. I'm surprised this forum isn't a default bookmark after an install. Fantastic source of information.

Hope I can help the cause soon.

---

### Post by Leftville on 2006-06-05
Wow, I'd forgotten about Google Linux. Thanks for the post, there's some good stuff in here and I learned a few new things.

---

### Post by Ob1 on 2006-06-21
Most popular documentation resources

*Note: click for the link*

[Official Ubuntu Help]("https://help.ubuntu.com/")

[the wiki Ubuntu]("https://wiki.ubuntu.com/")

[The Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

[The Linux Documentation Project]("http://www.tldp.org/")

[man.splitbrain.org all "man"(manual) pages, many find it better to read them from their web browsers]("http://man.splitbrain.org/")

---

### Post by confused57 on 2006-06-24
Here is aysiu's website of tutorials & howto's:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)


A definite "must-read" for beginners.

---

### Post by nanotube on 2006-06-25
and while we are at it, i might add all the links i have in my sig. :) just in case it changes, here they are again:

[My Comprehensive Ubuntu Breezy Customization Howto]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles")
[An excellent guide on various methods of installing software on Ubuntu]("http://monkeyblog.org/ubuntu/installing/")
[Frequently Asked Questions on these forums (suggestions of more FAQs are welcome)]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ")
[How to ask questions the smart way]("http://www.catb.org/~esr/faqs/smart-questions.html")

---

### Post by criptic on 2006-06-25
Well guys, ive read through this and WOW...

im also new to linux, i have played around with an really old red hat and even tried DSL (damn small linux) but i feel that ubuntu will be best for me untill i "get my footing" then i can start on fedora, altho no one seem's to recommend it (altho this is a noob forum) but we shall see as time goes on...

so thanks alot guys, great posts and links, i cannot wait to learn and be able to contribute to the community...

and may linux live forever!

---

### Post by cochrannd on 2006-06-28
Great post, it has helped a lot with some of the noob questions.  I hate posting them and posts like this keep me from doing it.  Thanks

---

### Post by ryanh06 on 2006-07-04
Hello all, I am new around here and this thread was the 1st one that I looked into, and I am a happy camper to say the least. Thanks so much, and I can't wait to install Dapper Drake :)

---

### Post by cornelious0_0 on 2006-07-15
Yet another very nice thread for a newb like me...thanks a bunch.

---

### Post by Who on 2006-07-21
I regularly find myself pointing people to 

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

It is simple and clear. I searched this thread and saw no references to it - did I miss them, or do people have reasons for not using this?

---

### Post by klytu on 2006-07-21
> **Who said:**
> I regularly find myself pointing people to 

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

It is simple and clear. I searched this thread and saw no references to it - did I miss them, or do people have reasons for not using this?

I had posted an alternate older link to the same information waaay back near the beginning of the thread. ;)

---

### Post by Cyraxzz on 2006-08-03
The free Linux Doc books at Linux.org, great knowledge there.

[http://www.linux.org/docs/online_books.html]("http://www.linux.org/docs/online_books.html")

And the O'Reilly Open Books.

[http://www.oreilly.com/openbook/]("http://www.oreilly.com/openbook/")

---

### Post by SeaRox on 2006-08-10
I was working on my windows 2000 machine at work trying to post a reply to this thread when Internet Explorer had an error and had to close.  Why am I using Linux again?

Back to this thread - Good stuff!!  Being proactive will help you learn the linux world much faster than sitting around waiting for the experts to personally answer your questions.

Thanks for taking the time to point us n00bies in the right direction.

---

### Post by Major_Stitch on 2006-08-21
Don't want to be a post-maker but I just have to say BUMP!
People switching from other OS-es (like I had) just have no idea that it can be so simple to get help in Ubuntu.

Now, just to get the people read the stickies :)

---

### Post by standard235 on 2006-12-28
Thanks. I'm on Feisty Fawn and the update manager wasn't working. I knew I had to use terminal. I'm just starting to understand the commands. I have the rm command, which I still can't get to work, the apt-get upgrade, and things like su and sudo.

6.06 LTS... bleh. 6.10... blehhh. 7.04... WOO!

---

### Post by richpor_1 on 2006-12-28
This is amazing... Where was this post when I was installing my system??

This should be a STICKY!!!

---

### Post by confused57 on 2006-12-28
> **richpor_1 said:**
> This is amazing... Where was this post when I was installing my system??

This should be a STICKY!!!

This used to be a separate Sticky, but now it's just a link in the "Sticky:Read This First...", 
kind of gets lost in all the links given(which, by the way are excellent).

---

### Post by SoloSalsa on 2007-05-12
I think you should replace Google Linux.  I mean, really: does anyone know how it works?  Does anyone know what it searches, or how to submit a page?
No.  And so you all know, Ubuntu Forums is not included in Google Linux (yeah yeah, gasp, because this is a HUGE resource :)).
Instead, or at least in addition to, mention [The Linux Search Engine]("http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o").  It is a Google Custom Search of several Linux related sites (including Ubuntu Forums, of course!).  And, one can collaborate and include other sites, as well.  I found it significantly MORE useful than Google Linux.

---

### Post by Mungojerrie on 2007-05-12
Thanx, guys - this has been sooooo helpful to me! I have wanted to try Linux for a long time, but it took a while to stop being a scaredy cat and take the plunge, and I am now so glad I did. Had a few teething probs but thanks to this excellent thread, I can now sort them all out. Cheers!  =D> 

Linda.

---

### Post by southernman on 2007-06-12
Found this link in a signature and just had to look... <---needs all the help I can muster sometime.

Great choice for a thread Pragmatist. Thank you, to you and all those who contributed links and suggestions for inclusion.

'scuse me, kinda getting a warm fuzzy feeling about now. Oh nevermind, that's something else all together! ;)

Anyhooo, just wanted to say thanks. I've added a link in my siggy too!

---

### Post by squee on 2007-06-13
That was great thanks. Its helped me sort out a lot of little annoying problems.

You forgot just one command though....

fortune

not the most useful but one of the best!!!!

---

### Post by phillip63 on 2007-08-16
Thanks ,I have only limited use for a computer and only am familiar with windows , but i like what i see in UBUNTU and am lost but i will use your tips right now

---

### Post by MaximB on 2007-08-16
Stick It !

---

### Post by SpiritIsReality on 2007-08-26
howdy

linux search engine
[http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o)
can search ubuntuforums.org by typing:
site:ubuntuforums.org "your search words"

google advanced search
[http://www.google.ca/advanced_search?hl=en](http://www.google.ca/advanced_search?hl=en)
...in the all words, try including the words, linux feisty
...try ubuntuforums.org in the domain, or ubuntu.com

google guides
[http://ubuntuforums.org/showthread.php?t=413599](http://ubuntuforums.org/showthread.php?t=413599)
[http://codeidol.com/other/google-hack/](http://codeidol.com/other/google-hack/)

free linux books online
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)

the sticky threads here
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)


trails

---

### Post by kwiter on 2007-10-20
Dual troubles with PowerPC 7.10, I updated my iMac G4 and now to boot I have to type old as the 7.10 drops to a shell at initramfs and when I try to install from the Live CD on my Powerbook Wallstreet G3 with 512 megs of Ram in it I get the same initramfs as well and it never gets to the desktop
Where am I going astray? I may need to just download 7.04 again and go back if all else fails.

Using BootX1.2.2 on the Powerbook, I can get 6.06 to load fine tho with it if I make the space for Ramdisk 104576 instead of the default 8167 or so.

Thanks , Desperate to put Ubuntu on my Powerbook and G4 iMac again!

---
[http://www.urbanskinz.com](http://www.urbanskinz.com)

---

### Post by Pragmatist on 2007-10-21
> **kwiter said:**
> Dual troubles with PowerPC 7.10, I updated my iMac G4 and now to boot I have to type old as the 7.10 drops to a shell at initramfs and when I try to install from the Live CD on my Powerbook Wallstreet G3 with 512 megs of Ram in it I get the same initramfs as well and it never gets to the desktop
Where am I going astray?...

The title of this thread is "How To Help Yourself".  Its goal is to provide *general *information, resources, and techniques that are useful in almost any troubleshooting situation*.*  It is not a place to resolve individual problems.

Post a new thread if you want help on your specific problem.  You will have a much greater chance of getting an answer.

Thanks.

---

### Post by Anduu on 2008-03-09
Been a while since this has seen the front page.

Still relevant IMHO.

Bump :KS

---

