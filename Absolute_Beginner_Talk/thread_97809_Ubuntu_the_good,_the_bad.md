---
title: "Ubuntu: the good, the bad"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by lukeprog on 2005-12-01
Ubuntu was easy to install and runs fine on an old Pentium III machine. Setting up the interface how I like it, printers, and network were all pretty easy. I've dabbled lightly with a few other user-friendly Linux distros like Fedora, MEPIS and even Linspire, but I like Ubuntu the best so far. However, I do have a few questions:

1. The user account I created during install, "ecrl", is the only account listed in users and groups. Where is the root account? I was never prompted to set up a password for it.
2. My flash drives won't automount, and I don't see them in /dev when I plug them in.
3. How do I install software not available through Synaptic? For example, I downloaded and extracted Firefox 1.5 and double-clicked the Firefox-bin file and nothing ever happens. Also, I downloaded "Wink for Linux" from [here]("http://freeware4u.com/modules/mydownloads/singlefile.php?lid=235") and extracted it and can't get anything to run. How do I install and run non-Synaptic programs?

I'm still working to get MP3s and DVDs playing. I think I'll eventually figure that out through the support docs, though.

Anyway, thanks for any help you can offer!

P.S. I work for the East Central Regional Library system in Minnesota and, when I know Linux 1/10th as well as I know Windows, I plan to deploy it across my library system for all public access PCs. Alas, we'll still have to use Windows for staff computers because the Dynix cataloguing software only runs on Windows.

---

### Post by Vlammetje on 2005-12-01
[QUOTE=lukeprog]Ubuntu was easy to install and runs fine on an old Pentium III machine. Setting up the interface how I like it, printers, and network were all pretty easy. I've dabbled lightly with a few other user-friendly Linux distros like Fedora, MEPIS and even Linspire, but I like Ubuntu the best so far. However, I do have a few questions:

1. The user account I created during install, "ecrl", is the only account listed in users and groups. Where is the root account? I was never prompted to set up a password for it.
2. My flash drives won't automount, and I don't see them in /dev when I plug them in.
3. How do I install software not available through Synaptic? For example, I downloaded and extracted Firefox 1.5 and double-clicked the Firefox-bin file and nothing ever happens. Also, I downloaded "Wink for Linux" from [here]("http://freeware4u.com/modules/mydownloads/singlefile.php?lid=235") and extracted it and can't get anything to run. How do I install and run non-Synaptic programs?

I'm still working to get MP3s and DVDs playing. I think I'll eventually figure that out through the support docs, though.

Anyway, thanks for any help you can offer!

P.S. I work for the East Central Regional Library system in Minnesota and, when I know Linux 1/10th as well as I know Windows, I plan to deploy it across my library system for all public access PCs. Alas, we'll still have to use Windows for staff computers because the Dynix cataloguing software only runs on Windows.[/QUOTE]


1. Ubuntu does not set a root user by default. Use 'sudo' instead when you need temp root access

2?

3. Download debian files and install them in terminal, or download bin files, set them to executabel and execute them. Else compile from source. worked for me so far.

---

### Post by Brunellus on 2005-12-01
1) Ubuntu has no root account by default;  it instead uses sudo.  Visit the RootSudo wikipage for a better explanation of why this is so.

2) your flash drives should be automounting to /media/usb.  are you running in gnome and is gnome-volume-manager running?

3) double-click installs dont' happen in ubuntu.  For Firefox, you'd need to open a terminal window, cd to the directory where you downloaded the binary, and execute the binary with

sudo ./Firefox-bin

it'll prompt you for your user password.  

Also, I recommend you visit the AddingRepositoriesHowto on the wiki to enable the universe and multiverse repositories.  If you still require a package that is not in those repositories....

If the package is a .deb package, you can install it by hand by executing

 sudo dpkg -i yourpackage.deb 

(of course, do this in the directory where your .deb is located).  Be aware that this does not resolve dependencies for you automatically, so you will need to take note of the package's dependencies and satisfy them yourself.

If you must compile packages from source, first execute:

sudo apt-get install build-essential

which will download and install the necessary tools.  Then follow the instructions in the readme for each program you wish to install.  Again, this does not resolve dependencies--or even notify you of them--so be sure you can satisfy all dependencies yourself.

4) For DVD and mp3 support, consult the RestrictedFormats wikipage.

5) Good luck with your linux rollout.  Consider also investigating Edubuntu, which implements the excellent LTSP project.  That way, you can run many thin clients off a single server--ideal in a library environment.  Consult the Edubuntu project page and [www.ltsp.org](www.ltsp.org) for details on that.

---

### Post by ubuntu27 on 2005-12-01
1) You can use this trick: [http://ubuntuguide.org/#openfilesasrootviarightclick](http://ubuntuguide.org/#openfilesasrootviarightclick)

You said that you have trouble with MP3 and DVD, I suppose also WMA, and other codecs.
You can install those codecs following this Guide. 
Note: I am assuming that you are using Ubuntu Breezy B.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

EDIT: Brunellus already game you the answer to all your questions :P

Ah! You can Find Edubuntu here: [http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by lukeprog on 2005-12-01
EDIT - wow, so may new posts, nevermind what I originally asked.

---

### Post by Kvark on 2005-12-01
[QUOTE=lukeprog]1. The user account I created during install, "ecrl", is the only account listed in users and groups. Where is the root account? I was never prompted to set up a password for it.[/QUOTE]
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

[QUOTE=lukeprog]3. How do I install software not available through Synaptic? For example, I downloaded and extracted Firefox 1.5 and double-clicked the Firefox-bin file and nothing ever happens. Also, I downloaded "Wink for Linux" from [here]("http://freeware4u.com/modules/mydownloads/singlefile.php?lid=235") and extracted it and can't get anything to run. How do I install and run non-Synaptic programs?[/QUOTE]
To make synaptic find many more programs then it does by default:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

To install .deb files:
Type this in a terminal: sudo dpkg -i filename.deb

To install .tar.gz files:
1. Install the package called build-essential with synaptic.
2. [https://wiki.ubuntu.com/ConfigureMakeMakeInstall](https://wiki.ubuntu.com/ConfigureMakeMakeInstall)

[QUOTE=lukeprog]I'm still working to get MP3s and DVDs playing. I think I'll eventually figure that out through the support docs, though.[/QUOTE]
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

[QUOTE=lukeprog]P.S. I work for the East Central Regional Library system in Minnesota and, when I know Linux 1/10th as well as I know Windows, I plan to deploy it across my library system for all public access PCs. Alas, we'll still have to use Windows for staff computers because the Dynix cataloguing software only runs on Windows.[/QUOTE]
Great, the visitors won't be able to mess up Linux systems once you set up their user rights tight enough. :)

---

### Post by lukeprog on 2005-12-01
Neither program I downloaded has source code, just a binary executable in the .tar.gz archive. When I try to run firefox-bin as sudo, I get: 

./firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

When I try to run wink as sudo, I get:

./wink: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by griz on 2005-12-02
For problem 2, getting flash drives to work, try:
sudo modprobe -r ehci-hcd
in a terminal.  Worked for me.

---

### Post by Brunellus on 2005-12-02
[QUOTE=lukeprog]Neither program I downloaded has source code, just a binary executable in the .tar.gz archive. When I try to run firefox-bin as sudo, I get: 

./firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

When I try to run wink as sudo, I get:

./wink: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/QUOTE]
what you're seeing are unmet dependencies.  You'd need to satisfy those dependencies manually to get the programs to work.  

If they're not critical, you could wait until proper packages are available in the repositories, and then you could just apt-get them--thus satisfying all your dependencies automatically.

---

### Post by lukeprog on 2005-12-08
Let's see if I've got this. Ubuntu prompted me to create an account during install. I used **ecrl** for username and **edna** for password. Every time I want to do something that requires superuser access, I don't log into a root account, I just type in my edna password and get temporary superuser access. So, if I wanted a public account I would create, say, user **all** with no password. Then from all, if I wanted to do something that required superuser access, I would be prompted for the ecrl password, edna. If I didn't know the password, I wouldn't be allowed to make that change.

Or am I still totally confused?

---

### Post by lerrup on 2005-12-08
Just a bit.  If your public account is not in the sudoers (i think) file the person won't be able to do any sudo type work.  other accounts can be added but if they are not there they cannot do sudo type operations.

---

### Post by Jormundgand on 2005-12-08
A user cannot use sudo unless they're on the /etc/sudoers list. Generally only the first account, created upon installation, is listed; subsequent created accounts are not added unless you specifically do it.

---

### Post by Brunellus on 2005-12-08
the first account created on an ubuntu install is added to the sudoers file.  all subsequent accounts are not.  It's kind of like being "it" in a game of tag.  Only the person who is "it" can make other people "it".

Incidentally, looking ahead to your anticipated rollout, here are a few neat links:

[https://wiki.ubuntu.com/UbuntuInLibraries?highlight=%28Libraries%29](https://wiki.ubuntu.com/UbuntuInLibraries?highlight=%28Libraries%29)

[https://wiki.ubuntu.com/OEMInstaller](https://wiki.ubuntu.com/OEMInstaller)

---

### Post by lukeprog on 2005-12-08
Lol, you guys are ALL over it. Things couldn't be clearer about sudo now. Thanks so much!

<Novice commentary>
Ubuntu want list:
1. Easier software installation. There's gotta be a way to just download software and install it without compromising security.
2. Easier software installation.
3. OEMInstaller features are apparently under development. Me want now.
4. Streamlined install for basic proprietary formats support, like DVD playback, MP3, and flash. I.E. "If it's legal in your nation, just type **apt-get install propformats**."
5. Tutorial "videos" as in Linspire (but without space-consuming audio) would probably be very useful to super-newbies.
6. Software for Linux in general needs better GUIs. The standards for Linux software GUIs seem pretty low, probably because it's been a geek-only OS until quite recently.
</Novice commentary>

---

### Post by Brunellus on 2005-12-08
[QUOTE=lukeprog]Lol, you guys are ALL over it. Things couldn't be clearer about sudo now. Thanks so much!

<Novice commentary>
Ubuntu want list:
1. Easier software installation. There's gotta be a way to just download software and install it without compromising security.
2. Easier software installation.
3. OEMInstaller features are apparently under development. Me want now.
4. Streamlined install for basic proprietary formats support, like DVD playback, MP3, and flash. I.E. "If it's legal in your nation, just type **apt-get install propformats**."
5. Tutorial "videos" as in Linspire (but without space-consuming audio) would probably be very useful to super-newbies.
6. Software for Linux in general needs better GUIs. The standards for Linux software GUIs seem pretty low, probably because it's been a geek-only OS until quite recently.
</Novice commentary>[/QUOTE]
apt-get is the easiest way going.  No dependencies, and automatic updates. Install once, upgrade occasionally, never say die (er, downtime).  I love it.

Also, for your media needs, please peruse the [RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) wikipage.  This stuff can't be in the default distribution for obvious legal reasons.

As far as GUIs:  the Linux philosophy has always sought to build engines first, and then worry about the interfaces.  Expect a lot of activity in interface development in the next few years as more commercial players get more heavily into the act.  For instance, Novell is sinking a good deal of money into useability testing and research which might eventually, through the magic of free software licensing, enter GNOME and other environments.

General advice to newbies:  I always say this (search my posts!)--migrating to a new OS is like moving to a foreign city.  The first days, weeks, and months are difficult--you don't know where anything is, nobody speaks your language (and you don't speak theirs), you don't know the bus/train/subway/tram network.  The culture shock is intense, and you end up disoriented and wanting your mother.

Then, after a while, you learn things.  Word by word, you learn the language, meet people, make friends, find where things are, learn how to get places.  

After a while, it becomes home, and you start showing your visiting friends around town and all the cool things your new city has that are found nowhere else.

The main thing is to constantly remember:  Things are different here.  This is not the home and the life I left behind.

---

### Post by lukeprog on 2005-12-08
Lol. About USB. The flash drive I was trying is apparently too fat and won't go in quite all the way (just a few millimeters short, I'd guess). It goes in all the way just fine on other PCs, just not this old one. I tried another flash drive that isn't as fat and Ubuntu recognized it immediately.

---

### Post by ed_d on 2005-12-08
Nice to see another Minnesotan using this fine product!

You will find this community the best at answering your questions. 

I figure, if my wife could learn to use Ubuntu, pretty much anyone can. I would like to come and visit your site when you are up and running to see Ubuntu in the mainstream in action.

---

### Post by lukeprog on 2005-12-08
Brunellus:

A useful analogy, but Linux is changing and improving so much faster than an entire city can. That's why I'm hoping (and occassionally, recommending) that a city as good as Ubuntu keep its best properties (security, stability, resource efficiency, networking, free software, modular structure, extreme customizability, etc.) and rapidly aquire some of the best features of the place I came from, too, like easy software installation, intuitive graphical interfaces, even more software availability, a better menu system (Windows' file-and-folder structure to its start menu is far more sensible than GNOME or KDE's approach, if you ask me), etc.

Whenever I troubleshoot beginner or intermediate computer users' Windows machines, I mention that viruses, spyware, system crashes and overpriced software are essentially exclusive to Windows. Linux and MacOS don't have these problems. But I still can't go so far as to actually recommend they switch to a particular Linux distro yet because it would be way over their heads. Not because it's "not Windows", but because it's not as instantly useable as Windows is to computer newbies. We're not quite there, imho.

---

### Post by lukeprog on 2005-12-08
Oops, another post.

Re: fulfilling dependencies on libmozjs.so and libstdc++.so.5 to install Firefox 1.5 and Wink for Linux in Ubuntu.

I think I found where I can download libmozjs.so, [here]("http://rpm.nogin.org/libmozjs.so.html"), but I don't know what to get on that page or how to install it.

If it's not in the basic repositories, I'm finding Linux software installation particularly tricky.

---

### Post by MonsterBox on 2005-12-08
If you've downloaded a tarball file, the best way that I've learned to install it is the following process. This assumes you have source in your tarball:

1.) Unpack the tarball to a temporary directory.
2.) cd into that directory in a terminal window
3.) enter the command: .\configure
4.) wait patiently
5.) once that has finished and you've read the output to  your satisfaction, enter the command: make
note: the make command will compile the program that is currently sitting in your folder. you need compilers to do this (which Ubuntu is pretty good about having installed) and it will take some time so
6.) get your caffienated beverage of choice
7.) when make has run successfully (this may take more than one attempt if you need to get additional dependencies, which make will tell you you need) then enter the command: sudo make install
This command will actually install the program.

Now, the one problem with this is that you have installed the program outside of Synaptic. As a result, you cannot use Synaptic to remove/maintain it.

If you have downloaded a binary (usually a *.deb package), I'm told there is a way to create a custom repository that you can then configure Synaptic to find so it will maintain it properly, but I haven't learned anything about that yet.

Disclaimer: This is all from notes I've taken and I just started using/learning Linux last week, so it may not be 100% accurate. If anyone smarter than me would like to correct me, please do so. ;)

:cool:

---

### Post by hanspb on 2005-12-08
Instead of using sudo make install, use sudo checkinstall. This makes a .deb package, installs it and includes it in the package database so it turns up in Synaptic.

---

### Post by MonsterBox on 2005-12-08
Beautiful!

I have altered my notes.

Thanks!

:cool:

---

### Post by lukeprog on 2005-12-08
hanspb: wow, nice. I'll have to try that.

For easy software installation, [Klik]("http://klik.atekon.de/") looks promising, but I'm unnerved that I was not prompted for a sudo password when doing **wget klik.atekon.de/client/install -O -|sh**. None of it actually worked, anyway: Firefox 1.5 and RealPlayer still have unmet dependencies I can't find, and all other software I tried complains about kdialog being an unknown command (even for gnome software like [vim-gnome]("http://vim-gnome.klik.atekon.de/")).

But I'm not asking for help with Klik. I'm still wondering how to get Firefox 1.5 running. Does it take a long time to show up in the repositories?

---

### Post by janrinok on 2005-12-08
Well you are partly correct.  Using your password 'edna' when you type sudo will do exactly what you want.  However, when you set up a new user 'all' you will have to give it its own password and, if you want to be able to access sudo from that account, you will have to add it to the list of 'sudoers' (/etc/sudoers).  In that file you can give your new account access to everything, nothing or any combination in between.  Try 'man sudoers' for more explanation, or google for it.  There really are very few occasions when you actually need a full root account - in fact, I cannot think of any but I'm sure that someone will correct me if I claim that there is _never_ any need for it.  And using the sudoers file means that you can give each user just as much access as they need without compromising the rest of the system.  Jan

---

### Post by janrinok on 2005-12-08
Sorry for my last post - I seem to have missed several pages of replies!  I am answering a query on the bottom of page 1 and here we all are on page 3!.  Honestly, sometimes I am awake....  Jan

---

### Post by kaamos on 2005-12-08
[QUOTE=lukeprog]So, if I wanted a public account I would create, say, user **all** with no password. Then from all, if I wanted to do something that required superuser access, I would be prompted for the ecrl password, edna. If I didn't know the password, I wouldn't be allowed to make that change.

Or am I still totally confused?[/QUOTE]

You could simply decide not to make the user "all" belong to the users that can use sudo. Then if someone from the "all" account attempts to use sudo they get only a warning that they do not have permission, and this attempt would show in system logs.

EDIT: Nevermind, janrinok was faster than me.

---

