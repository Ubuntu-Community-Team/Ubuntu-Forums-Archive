---
title: "[SOLVED] I dunno how to set up a program"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by ENigma885 on 2007-12-07
Ok i'm an absolute Ubuntu user  but i really like it .Actually i duuno wat's going on i have some problems that i face in a daily manner with Ubuntu.(I will try to state the ones that i can identify others i can't even name them) Anyways....
1st it's about programs and installation:-

1.Is Synaptic tool the only source of applications in Ubuntu?(if it isn't plz give me other ways to get applications)
2.Synaptic tool is downloading stuff and installing..but i really want to know where these stuff are being downloaded and installed ..and wat if i want the program source (like the .EXE in Winows) to set up it any time not to be dependent on an Internet connection .
3.Sometimes i download programs from Synaptic and install them but there aren't  in Applications window ,where can i launch them? 
4.i found some sources of Linux applications on the internet..but i have some questions concerning them:
[a] i downloaded a codec pack -from Softpedia.com- and i dunno how to install the downloaded file it's (.tar.bz2) When i double click on it,it only opens (File Roller) archive manager so wat's next??
[b] is there a common file extension of Linux executable files? (i found some .tar.gz and many..)
[c] is it save to download any Linux application from any source on the internet (i heard that viruses r not a big deal in Linux ,but how about other threats like spywares .adwares and trojans ?? do they exist in Linux?)

hope u can help

Thanx Ubuntu 
( I hate PIRACY. I hate Windows Monopoly. I hate interfering with my PRIVACY. I like FREEDOM that's y I adore UBUNTU)

---

### Post by Emerzen on 2007-12-07
1.  No.  For the absolute beginner go to Places-->Add/Remove Software

2.  A major difference between *NIX and Windows is the idea of a registry, which *nix doesn't have.  Basically, a "package" contains the binary files needed for the program and the configuration scripts.  When installing, the binaries most often go to /usr/bin and the configuration files go someplace in /etc/name_of_program just installed.  Configuration scripts are simply text files that you can modify directly if you wish.  User specific config's end up in your home directory /home  but you need to press ctrl+h to see them.

3.  If you use Add/Remove you should see them.  Otherwise, go to System-->Preferences-->>MainMenu.  Select "Add new item."  then Browse to the location of the binary "usually /usr/bin.
********sometimes logging out and back in does it for you though.  Or,
```
sudo killall gnome-panel
```

4. Applications come in 3 main categories:  
  a.  a package which can be identified with .deb extension  (easiest for beginners as Synaptic monitors everything for you)
  b.  a binary file which can just be run
  c.  source code-- I don't advise a beginner install from source and it is 99.9% of the time unnecessary.

Always check for the program in Add/Remove (make sure 'all software sources' is selected).  Next try synaptic.  If that fails, check out [www.getautomatix.com/](www.getautomatix.com/), a program that will install many codecs and popular programs for you.

---

### Post by atomkarinca on 2007-12-07
Under Applications menu you can find "Add/Remove...", like Synaptic Package Manager you can search for programs using this tool. The good thing is you don't have to necessarily type in the name of the program, but you can search according to the description of a software. For example when you type "demux" you will have programs that does demuxing.

You can find the executables under /usr/bin. Most of the GUI software is found under Applications menu, if it's not you can find it under /usr/bin.

tar.gz or tar.bz2 files are archive files (just like .zip, .rar or .z7 files). You can extract them right-clicking and selecting "Extract Here". You should find a file called INSTALL in the unzipped folder. Mostly there are 3 easy codes: first open up a terminal, browse into that folder:

```
cd /path/to/the/folder
./configure
make
sudo make install
```

As a reminder: NEVER DO THESE STEPS IF YOU'RE NOT SURE THE SOURCE IS TRUSTED.

---

### Post by oldos2er on 2007-12-07
There's Add/Remove too, but it'll show you the same apps as Synaptic. Synaptic can show you where each file in a package is installed, right-click on a package, choose Properties, Installed Files. 
 If you download a program that's not showing up in the menus, type its name in a terminal. Linux executable files generally don't have file extensions (e.g. 'firefox'); instead they rely on permissions that set or remove an executable "bit." See [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) .

---

### Post by mgmiller on 2007-12-07
For most of your codecs and flash and java and stuff like that, just run synaptic and search for "ubuntu-restricted-extras"  (without the quote marks)

for virtually everything else go to [http://medibuntu.org/]("http://medibuntu.org/")

and click on the "Repository Howto" link at the top of the page and follow the instructions to copy and paste about 2 lines into a terminal.   

Takes about 10 seconds to do the whole thing.

You don't have to go all over the web to get all your codecs and stuff working.

---

### Post by erfahren on 2007-12-07
> **ENigma885 said:**
> Ok i'm an absolute Ubuntu user  but i really like it .Actually i duuno wat's going on i have some problems that i face in a daily manner with Ubuntu.(I will try to state the ones that i can identify others i can't even name them) Anyways....
1st it's about programs and installation:-

1.Is Synaptic tool is the only source of applications in Ubuntu?(if it isn't plz give me other ways to get applications)
2.Synaptic tool is downloading stuff and installing..but i really want to know where these stuff are being downloaded and installed ..and wat if i want the program source (like the .EXE in Winows) to set up it any time not to be dependent on an Internet connection .
3.Sometimes i download programs from Synaptic and install them but there aren't  in Applications window ,where can i launch them? 
4.i found some sources of Linux applications on the internet..but i have some questions concerning them:
[a] i downloaded a codec pack -from Softpedia.com- and i dunno how to install the downloaded file it's (.tar.bz2) When i double click on it,it only opens (File Roller) archive manager so wat's next??
[b] is there a common file extension of Linux executable files? (i found some .tar.gz and many..)
[c] is it save to download any Linux application from any source on the internet (i heard that viruses r not a big deal in Linux ,but how about other threats like spywares .adwares and trojans ?? do they exist in Linux?)
As for 2) All the packages available in Synaptic (from the Ubuntu repositories) are available here: [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)
(you'll notice that's on the "Gutsy" section) -- if you ever need to you can search that using Google, like:
*name-of-package* site:packages.ubuntu.com/gutsy/

There is one important thing about what you ask that needs pointing out though:
There is a fundamental difference between Linux and Windows when it comes to installing programs. Programs in Linux oftentimes rely on "dependencies", which are basically existing software that provides basic functionality (like interaction with the OS). This isn't a bad thing since programers can use existing software to provide common functions when developing their programs. Many programs may utilize the same ones. 

You may have heard the term "dependency hell", Linux users of days past sometimes had to go track down the dependencies required to install a program. That's where Synaptic comes in. It's a "package manager" and will automatically install the dependencies needed. If you look at some of the packages on the Ubuntu Software Packages site you'll see that the packages will have a list of packages with red dots that are required. Those are the dependencies and need to be installed before the package itself.
see: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Add/Remove programs in Ubuntu is just a simpler interface for Synaptic. 

As far as exactly where the packages are installed to, as mentioned the executables themselves often go into /usr/bin (/bin is mainly for system programs) - games sometimes go into /usr/games. 

I kind of wondered where everything "went" at first too, the file system looked a bit complex to me as well. If you go and look at the information for a package on that site at the bottom of the page it will say "list of files" - that wll show exactly where all the files for the program will go on the system.
look at the list for [tuxkart](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=tuxkart&version=gutsy&arch=i386)  for example: [http://packages.ubuntu.com/gutsy/games/tuxkart](http://packages.ubuntu.com/gutsy/games/tuxkart)

For more info about the Linux file system see:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)
[linux_file_structure.jpg](http://bp3.blogger.com/_Vbsj-yhipTw/RvaiatPBPBI/AAAAAAAAABs/yjx3hPlEUNw/s1600-h/linux_file_structure.jpg)

Also see: [How to Install *Anything* in Ubuntu](http://monkeyblog.org/ubuntu/installing/)

As atomkarinca pointed out the tar.gz or tar.bz2 archives usually contain the source and need to be compiled and installed (not as hard at it sounds). You need the required dependencies installed first (which includes any utilities needed to compile it, but "build-essentials" is one that is pre-installed on Ubuntu.) You can also compile software and make a .deb out of it (using checkinstall). You can then save it to install later, and/or it can then be uninstalled through Synaptic - click on "Status" on lower left then in the list on the left it'll be under "Installed (local or obsolete).
For more info on that: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
(use the "checkinstall --install=no" option. that will create a .deb that you can install anytime.)

You mentioned getting a codec pack from Softpedia, you really shouldn't need to do that. All the codecs you most likely need are available through the repositories. You need to have all the repositories listed in your /etc/apt/sources.list though. see: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
(make sure you do the part where it mentions entering the key for Mediubuntu).

There's more info on this for Ubuntu but see: 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
basically you need the w32codecs and the ones listed here: [https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

(I personally like using VLC and the mozilla-vlc-plugin. I uninstall the totem-mozilla plugin)

... you probably have everything you need installed by now though - lol !

-- hope that helped.

---

