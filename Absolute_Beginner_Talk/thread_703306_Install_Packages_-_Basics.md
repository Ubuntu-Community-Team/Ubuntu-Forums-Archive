---
title: "Install Packages - Basics"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by akafudge on 2008-02-21
Guys, I have just installed Gutsy on my Thinkpad T43p with XP and it works great. However, as a novice and coming from a DOS background, I need to learn some basics so I don't make stupid mistakes that can be easily avoided.

The problem I have is that its not straight forward to understand the package install process. 

For instance, source code and install packages and how to treat them. In windows, it's easy to install a programme as they already compiled so, what is an equivilent in Linux? Also, if I have source code, how do I compile.

If there is a good guide anywhere that would be great.

Please bear in mind I have spent 20 years with DOS and Windows and 2 days experience of Ubuntu.

Cheers.

Jonathan

---

### Post by akafudge on 2008-02-21
Just found this....I'm reading :)

4 : HOW TO INSTALL SOFTWARE

Add/Remove - the basic method

The easiest way of installing a package is to use the 'Add/Remove' tool. Click Applications --> Add/Remove... to start it. First, find the package or packages you want to install. You can search for a keyword, such as 'email', or look through the categories shown on the left hand side of the window. Once you've found a package you want to install, tick the box next to its icon. You can do this for as many packages as you like.

Once you've finished choosing, click the Apply button at the bottom of the window. Another window will pop up, showing all of the packages you've selected and asking if you'd like to apply the changes. To install the packages, click Apply. You'll then be asked to type in your super-user/administrator password. Once you've entered it, another window will appear informing you of the installation progress. Once this has finished, click Close. Your new programs are installed, ready to use! 

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[http://www.beginningubuntu.com/software_1.html](http://www.beginningubuntu.com/software_1.html)


Cheers

Jonathan

---

### Post by FrozenFox on 2008-02-21
Be careful with your words, as not all Linux distros install software the same way. One 'package' for one linux distro may not work with another.

That said, in ubuntu, apt manages the software from the ubuntu repositories (archive of .deb files, essentially, which are very very roughly similar to .exe's in windows). If you find a .deb (it's recommended you always run synaptic, press refresh, and look for your software there first) on the web for your given program, it basically includes binaries for that program and instructions for apt as to what else the program needs to run. Naturally, .deb's for other systems (like different versions of ubuntu or debian) may or may not work correctly on something they weren't designed for, because of different/missing package versions or whatnot. As for installing from source, you will need to instlal build-essential via synaptic and read the README for whatever you're trying to compile, but typically, it is this same process:

cd /path/to/the/main/folder
./configure
make
sudo make install

And if you have problems in the configure part, just look at the error. It's usually pretty easy to resolve if you consider what it says or ask around. Just search for what it says it's missing in synaptic, and install it. Most of the time it also needs files for the dependency in question ending in -dev. For instance, if ./configure nags about not having LAME, search for and install lame in synaptic and if it still complains, repeat but install lame-dev or whatnot.

---

### Post by akafudge on 2008-02-21
Thanks Mr Fox, that is helpful. 

I assume a 'distro' is a form of Linux OS which implies all are different and therefore have differing installation characteristics.

Also, when you say Ubuntu repository, do you mean that within the Linux community, anyone that creates an application will load that into the various repository's for different Linux OS's and therefore, there is only one place for me to go to?

Bear in mind that I am from a Windows background where you need to search for apps across the web. In effect the web being the Windows repository!

Sorry for the basic questions :)

---

### Post by bumanie on 2008-02-21
Hi akafudge, welcome. A repository is a server where or group of severs that have ubuntu software on them. All the software (unless third party) has been tested for its integration with the OS and also for its coding integrity - in other words it is software that is safe to use and will work with ubuntu. You need to enable some of the repositories, because some of them contain proprietary software which you will need to get the best ubuntu experience. There are some 'third party' repositories, these are generally safe, but as they're not officially supported by Canonical, when installing them, you will receive a warning that you are installing software that may be unsafe.

---

### Post by FrozenFox on 2008-02-21
akfudge,

Indeed you are correct on the terminology I used.

To expand on previous comments by myself and other users:

The best way to get software is from the repositories. The program named Synaptic that comes with Ubuntu uses the backend/command line tool called apt to search the repositories / web page .deb archives defined in the file /etc/apt/sources.list. Synaptic provides you with a graphical interface to do all sorts of installation and removal of programs. It's really great because you can upgrade all of your files on your pc in mass with just a couple clicks (mark all upgrades button).  If you look in Administration in the start menu/start bar you will find "Software Sources". This tool will let you choose what kind of repositories are enabled. By default, the proprietary ("non-free") software repositories are disabled, ie anything that the Ubuntu developers themselves are unable to work on for licensing issues or don't find necessary for their main repositories and such to work on keeping current. The repositories do not always have the software you want, but very very often do. Your software is usually kept to a "stable" version in the repositories, but if you want a new version, you can always install a .deb file yourself or sometimes the authors of said software offer a repository you can add to your /etc/apt/sources.list. .deb files include the binaries for the program you want to install and also information about what other programs and libraries they need in order to run (termed "dependencies"). If you download a .deb (remember, not all .debs made for another system besides the exact one you are working on will work correctly or at all because of software version and existence issues in repositories), you can easily install it via just double clicking it, and see what files it installs by clicking over to the "Installed Files" tab.

---

### Post by mbsullivan on 2008-02-21
Hi All,

In general, I think that the basics of the repositories are covered by the previous posts. I just wanted to point you [here]("http://monkeyblog.org/ubuntu/installing/"). I haven't read over the whole thing, but it appears to be a fairly comprehensive (and understandable) primer to the Ubuntu repositories.

Mike

---

### Post by akafudge on 2008-02-22
Chaps, thats great, thanks very much.

The concepts are slightly odd to me coming from the Windows world but in practice I can see benefits and will certainly carry on with Ubuntu in a dual XP set up for the next few weeks whilst I build my experience of the basics.

I have been so impressed with the stability of Linux and Ubuntu so far that I am struggling to see what will keep me using XP and I see no reason to consider Vista at all. It's refreshing that it just seems to work!

I can see me making the switch over soon especially when my XPS M1330turns up.

Cheers.

---

