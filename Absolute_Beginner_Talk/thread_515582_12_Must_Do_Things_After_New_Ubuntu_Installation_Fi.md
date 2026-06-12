---
title: "12 Must Do Things After New Ubuntu Installation Fiesty Fawn 7.04"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by designwiz on 2007-08-02
The very first time I installed Ubuntu Fiesty Fawn 7.04, just like every other new Linux user and wit the hang of windows xp/vista in the background i tried around experimenting with the new linux.. try to play arnd

1.Try to play mp3-->didnot work
2.Tried to play video--> said no codecs

Searched Alot on the net and finally came across an article that helped me and may/would help you too!

This is a compilation and installs almost the basic needed softwares/codecs to make u feel good about your new O.S

Note:This is a compilation and the orginal article is here
[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html]("http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html")

**[SIZE="3"]1. Update your system Part 1[/SIZE]**
Go to System-->Administration-->Update Manager
Does the necessary updates!

**[SIZE="3"]2.Installing enabling additional Repositories[/SIZE]**
Now many applications need additional repositories to be installed or some to be enabled in Synaptic package manager so before trying out steps given below ensure that repositories in order.

Launch Synaptic Package Manager (System -> Administration -> Synaptic Package Manager ) , then in Synaptic package manager go to (Settings -> Repositories ) you will find window like this . Ensure that all the check boxes are marked leaving source code(if you want to you can enable this also but you are not going to need this unless you are software developer) 

Now you have to add additional repositories , close synaptic package manager and type the following command in the terminal window (Application -> Accessories -> Terminal )

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - 
**_[CENTER]AND[/CENTER]_**
> sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

After your done with this type in the terminal

> sudo apt-get update



**[SIZE="3"]3.Installing Multimedia Codecs[/SIZE]**
w32codec is a collection dll files from windows that helps in decompressing major video/audio formats allowing them to be played flawlessly on Linux Media players , however because of legal issues associated with it is not included with Ubuntu . To Install the package type the following command in the terminal window(assuming repositories are in order and they are set up correctly as described above ),keep in mind that codecs are downloaded from Medibuntu repositories and not Ubuntu hence be sure you have activated the repositories correctly as described in first step of this article.(Jus do it, it works just fine)

Type in the Terminal
> sudo aptitude install w32codecs
and in addition also type
> sudo aptitude install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

**[SIZE="3"]4.Installing Video Players[/SIZE]**
To install video player to play your video files/movies
Type in terminal
> sudo aptitude install libxine-extracodecs xine-ui mplayer mplayer-skins vlc vlc-plugin-* mozilla-plugin-vlc

**[SIZE="3"]5.Installing Audio Players[/SIZE]**
To install audio players to play your music
Type in the terminal

> sudo aptitude install xmms xmms-mad xmms-skins xmms-wma mpg123 banshee amarok

**[SIZE="3"]6.Installing Macromedia Flash Plugin[/SIZE]**
To install Flash plugin on ur browser(firefox)
Type in terminal
> sudo aptitude install flashplugin-nonfree

**_[CENTER]OR[/CENTER]_**
Open a flash site in your browser, firefox will automatically detect that flash has not been installed, Click on Install Missing Plugins and follow the simple instructions

**[SIZE="3"]7.Installing Beryl and Eye Candy[/SIZE]**

Follow the stickys on the ubuntuforums

[B][SIZE="3"]8.Installing Java Runtime environment v6.0 With Mozilla Firefox plugin
[/SIZE][/B]
Similar to Macromedia Flash , today Java applets and applications have become a integral part of internet browsing experience however java runtime is not installed by default in Ubuntu to install java Runtime Environment with plug in for Mozilla Firefox type the following command in the terminal window.

> sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
After installation click on yes to complete installation

**[SIZE="3"]9.Installing Adobe Reader : -[/SIZE]**
*the following command would only work if Medibuntu repositories are configured properly so be sure you have installed it correctly as described in the beginning of article .*
> sudo aptitude install acroread

**[SIZE="3"]10 . Installing Downloading & P2P tools - amule , Downloader for X ,azureus[/SIZE]**
Downloader for X is a nice download manager that allows downloading files from Internet , pausing them and downloading them later . It also supports splitting file into number of segments so that files could be downloaded quickly . However one thing that i didn't like about is it's interface is somewhat difficult as compared to some of the download manager available on Windows.

Anyways to install " Downloader for X " type the following command in the terminal window.
> sudo aptitude install d4x 

nstalling azureus : - Azureus is one of the more popular bittorrent client available on both Windows and Linux , based on java it is one of the most powerful bittorrent client.

To install azureus type the following command in the terminal window : -
> sudo aptitude install azureus 

**[SIZE="3"]11.Installing Microsoft True Type Fonts[/SIZE]**
To install Microsoft True Type fonts on Ubuntu type the following command in the terminal window .

> sudo aptitude install msttcorefonts

Now Fonts would automatically be downloaded from the internet and installed .

**[SIZE="3"]12.Installing Unrar( to view rar files)[/SIZE]**
Installing Unrar : -

RAR is one of the very widely used archives on Windows , however unrar tool to decompress RAR is not shipped with distribution and has ti be installed manually.

> sudo aptitude install unrar 

Hope this compilation was usefull to you!

Yeh one more thing Remember to Read and Backup your files before you start messing around.
Cheers!

---

### Post by Steve1961 on 2007-08-02
All of this stuff can be found here:

[http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)

---

### Post by designwiz on 2007-08-02
hmm that the a real nice site.. dint find it first thought this would help new users :)

---

### Post by uibesteven on 2007-08-02
it really helps a lot

---

### Post by hyper_ch on 2007-08-02
What is Adobe Reader needed for?

---

### Post by designwiz on 2007-08-02
Though i do completely agree with the fact that Document Viewer does the job but sometime looses out on formatting, also take longer to load huge files, it worked better with adobe reader
p,s This is a personal opinion and may not be true in all cases!

---

### Post by stinger30au on 2007-08-02
> **hyper_ch said:**
> What is Adobe Reader needed for?

so you can read PDF files.
there is a pdf file viewer available thru synaptic

---

### Post by Hallvor on 2007-08-02
Even Dapper reads pdfs out of the box.

---

### Post by gkumar26 on 2007-09-03
GREAT stuff man! Really helps out a lot. [Here]("http://ubuntuforums.org/showthread.php?t=33183") is another thread titled "**New to Linux? Need a program?**" for beginners which compares windows/linux programs. Also, if you want to install .exe files as used in windows, **wine** is a great program for that.Here is the [link]("http://ubuntuforums.org/showthread.php?t=528151&highlight=wine+installer") --Look at Post #5 for specific instructions :)

---

