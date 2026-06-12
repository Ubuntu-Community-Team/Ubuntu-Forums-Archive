---
title: "100%pure beginner,various questions.."
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by bigben on 2006-05-26
Thank you for this friendly looking forum.Just installed ubuntu and using linux the first time after 15years of windows experience:rolleyes: 

Now I have NO IDEA what to do,I've read the stickys and did search for about 2 hours now for concrete answers but it so much information that i lost the overwiev,thats why ill ask a few basic questions for now and will try to find my way around other more advances questons later on..Im here to stay,to learn and in a far future:p ,to help others..So you wont get rid of me that easy
Here are my requests:

1.) where is the command line,how do i enter commands
2.) which version am I using,i've seen many names round here,dont know what they all mean..?!
3.) How do i install appz for cd/dvd burning,winamp,vlc player ect??

Sure this  been posted in similair forms many times before,did use the search function but couldnt really find the answers..
Thanx for any replies and hope to become less of a noob soon!:D

---

### Post by carlosqueso on 2006-05-26
1) the command line is under applications->accessories->terminal (I beleive)
2)you probably are using Breezy, but use your new command line and type ```
lsb_release -a
``` and it'll tell you.
3)to install new apps, first type ```
sudo gedit /etc/apt/sources.list
``` into a terminal and replace what it says with the proper one on this page: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)  then browse through synaptic package manager to find what you want.  [http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183) has some ideas.

---

### Post by bruce89 on 2006-05-26
You should use a mirror, for instance I use [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu).  Replace gb with where you live (us, de, fr etc.)

---

### Post by ozPATT on 2006-05-26
g'day! I know exactly how you feel... after 13 years of windows, i couldn't even comprehend a computer with no microsoft on it, before i installed ubuntu. 

so, to answer your questions as best i can - very much a newbie here myself.. 

1a) the command line is under Applications>Accessories>Terminal
1b) to enter commands, I am not so good with that, so I will have to leave that one, but if you go to [http://www.oreilly.com/catalog/debian/chapter/book/ch04_01.html]("http://www.oreilly.com/catalog/debian/chapter/book/ch04_01.html") then you should find some useful starting tips. :)

2) if you just went to ubuntu.com and pressed download, you will be using Ubuntu Breezy Badger v5.10 (i think ;)) I am not sure though how you find out apart from when you install it. There is however a new version of ubuntu coming out on 1st June, called Dapper Drake, which is still in testing until then, but is pretty much near completion, so quite a few people seem to have that and just updating daily to have everything there come 1st June (including me. :))

3) installing applications, you can find a good list of equivalents in one of the stickies here, and you will find that most things are already installed. if you go to Applications>Add/Remove, then have a hunt through there, you should be able to install what you are missing. 

hope that helps, Patrick

ps.. not sure how much you know about linux, but i knew absolutely nothing, to the point where i didn't even know where i was supposed to set up a file structure or anythng... so just in case you dont know, the home folder is your 'home'. :) pretty much like My Documents I guess. keep everything in there, and you should be ok. :D

---

### Post by confused57 on 2006-05-26
The Sticky "How To Help Yourself" is a good place to start:

[http://ubuntuforums.org/showthread.php?t=142716&page=5](http://ubuntuforums.org/showthread.php?t=142716&page=5)

---

### Post by bigben on 2006-05-26
wow,thanx..quick and easy instructions from you guys! BUT I only got to the point where i used the "sudo gedit /etc/apt/sources.list" coomand,saved the file but now dont know how to proceed installing/viewing the already installed appz..as you said that most are already installed...nero=gnomebaker....ok,but where is gnomebaker and how do i "activate" it?

to bruce89:i really have no clue what your refering to..:(

---

### Post by carlosqueso on 2006-05-26
Actually...gnomebaker isn't installed.....I beleieve that you can go under one of the system menus and look for something called **synaptic package manager**.  You can then enter your password and can then search for and download programs.    Many of these will appear in your menu, but some you will need to type the name in the command line.  If you know the package name, you can also type ```
sudo apt-get install <name of package>
``` so gnomebaker would be ```
sudo apt-get install gnomebaker
``` it all comes down to what is easier for you.

---

### Post by Lord Illidan on 2006-05-26
Now that you have saved the file, just enter these commands.

```
sudo apt-get update
```

This will reload package information from the repositories..

```
sudo apt-get dist-upgrade
```

This will upgrade your system

```
sudo synaptic
```

This brings up synaptic, an app you can use to browse the repositories and install programs. You can search for packages, too..

---

### Post by bigben on 2006-05-26
cool,i think its kinda starts working now :) managed to at least start xmms lol
one thing i wonder is why when installing a theme for gnome,it gives me the error message "invalid file format"? what do i do wrong?

---

### Post by bruce89 on 2006-05-26
[QUOTE=bigben]wow,thanx..quick and easy instructions from you guys! BUT I only got to the point where i used the "sudo gedit /etc/apt/sources.list" coomand,saved the file but now dont know how to proceed installing/viewing the already installed appz..as you said that most are already installed...nero=gnomebaker....ok,but where is gnomebaker and how do i "activate" it?

to bruce89:i really have no clue what your refering to..:([/QUOTE]
Never mind then.

---

### Post by Sef on 2006-05-26
> sudo apt-get install <name of package>

When installing packages by command line, use update first and use aptitude and not apt-get.

sudo apt-get update

sudo aptitude install (package_name)

aptitude is an updated apt-get.  If you need to remove a package, it works much better.


> Now that you have saved the file, just enter these commands.

Code:

sudo apt-get update


This will reload package information from the repositories..

Code:

sudo apt-get dist-upgrade


This will upgrade your system

Wait to upgrade.  On 1 June, Dapper will be stable and offer you the choice of wether to upgrade or not, by clicking on a button.

> You should use a mirror, for instance I use [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu). Replace gb with where you live (us, de, fr etc.)

Bruce was trying being helpful, but having you download to the country to where you are from, but it automatically does that.

---

### Post by Lord Illidan on 2006-05-26
[quote=bigben]cool,i think its kinda starts working now :) managed to at least start xmms lol
one thing i wonder is why when installing a theme for gnome,it gives me the error message "invalid file format"? what do i do wrong?[/quote]

How did you try to install it?

---

### Post by bigben on 2006-05-26
well,i read in a different thread that u can just drag n drop a link to the themes preferences window.that didnt work and i downloaded several pack,then tried adding them by "install theme" and specifying the location of the folder..

edit: i get a "sudo: timestamp too far in the future: May 27 02:03:53 2006 " message every time i try to install new appz ect..

---

### Post by IYY on 2006-05-26
You can drag and drop. Try it with a simple theme:

[http://art.gnome.org/themes/gtk2/1213](http://art.gnome.org/themes/gtk2/1213)

Go here, and drag that link into your theme window. Does it work?

Or just drag this: [http://art.gnome.org/download/themes/gtk2/1213/GTK2-ClearlooksQuicksilver.tar.bz2](http://art.gnome.org/download/themes/gtk2/1213/GTK2-ClearlooksQuicksilver.tar.bz2)

---

### Post by Lord Illidan on 2006-05-26
From where did you get the packs. You might need to unzip them further, that's why...

---

### Post by bigben on 2006-05-26
YII:yes,they worked,wonder why the other ones didnt work,is it the same with using a background theme on the desktop?
Lord Illidan: i got the [http://ftp.gnome.org/pub/gnome/sources/gnome-themes-extras/0.8/gnome-themes-extras-0.8.0.tar.gz](http://ftp.gnome.org/pub/gnome/sources/gnome-themes-extras/0.8/gnome-themes-extras-0.8.0.tar.gz)
,i did unzip em and put them into a seperate folder..now i see that all these new file extensions dont tell me much..i've seen some kickass screenshots from peeps round this forum and i just need to brighten up the whole look..
I mentioned that there is a a "sudo: timestamp too far in the future: May 27 02:03:53 2006 " message everyt time i try n install an app throu the command line..any ideas why? i did already update as mentioned above..
thanx again for showing me around..!:)

---

### Post by Lord Illidan on 2006-05-26
The sudo timestamp : Is the time on the clock well adjusted?

Also, the .tar.gz you just downloaded. Are the extracted files .bz2? What are their extensions?

---

### Post by bigben on 2006-05-26
the clock is well adjusted,i pasted a command i found on google to make the clock stay tuned,so far its been running on time and didnt jump every 15 min..
regarding the tar.gz..its a 19mb file with several subfolders/themes? and it has many different files/extensions..one of them is called "install" ;) but didint work for me..:(

---

### Post by Sef on 2006-05-26
> regarding the tar.gz..its a 19mb file with several subfolders/themes? and it has many different files/extensions..one of them is called "install"  but didint work for me..

How did you try and install it?

---

### Post by Mustard on 2006-05-26
[QUOTE=bigben]the clock is well adjusted,i pasted a command i found on google to make the clock stay tuned,so far its been running on time and didnt jump every 15 min..
regarding the tar.gz..its a 19mb file with several subfolders/themes? and it has many different files/extensions..one of them is called "install" ;) but didint work for me..:([/QUOTE]

The one marked 'INSTALL' would most likely be a text file containing the instructions to install.

---

### Post by Lord Illidan on 2006-05-27
Mind telling us the location of this theme?

---

### Post by bigben on 2006-05-27
hi,
ithis is the download link[http://ftp.gnome.org/pub/gnome/sources/gnome-themes-extras/0.8/gnome-themes-extras-0.8.0.tar.gz]("http://ftp.gnome.org/pub/gnome/sources/gnome-themes-extras/0.8/gnome-themes-extras-0.8.0.tar.gz")

I have a question about installing cdrdao for k3b...not sure how to do that..is it ok to ask in the same thread or should i start a new thread for each question?
Greetz

---

