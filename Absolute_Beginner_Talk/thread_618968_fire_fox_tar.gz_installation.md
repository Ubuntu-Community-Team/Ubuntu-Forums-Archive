---
title: "fire fox tar.gz installation"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Gildp67 on 2007-11-21
Well I just down loaded the latest fire fox and thunder bird and they are tar.gz, being a noob to all this how do I install them. please make it as easy and step by step as you can, as I have never installed any tar.gz files yet. Thanks for any and all help

---

### Post by Paul820 on 2007-11-21
Firefox and thunderbird are available in the repositories System->Preferences->Synaptic Package Manager

---

### Post by mikewhatever on 2007-11-21
[http://ubuntuzilla.wiki.sourceforge.net/?token=81fb76cdaba37a133f62caaa26739429](http://ubuntuzilla.wiki.sourceforge.net/?token=81fb76cdaba37a133f62caaa26739429)

As already mentioned, firefox is already installed in Ubuntu.

---

### Post by MrFSL on 2007-11-21
If you are looking to use the absolute latest which might not be in the repos and you have downloaded the tar files from mozilla then you simple need to extract them.

These are static binaries that don't need to be installed nor compiled. Just extract and go.

Greets.

---

### Post by Gildp67 on 2007-11-21
yes these are the latest and greatest, should I extract to a certain folder in the system folder or where? and so I am straight on this I just extract and no need to do any kind on installation process? The icon to run the program is somewhere in the extracted folder?just sitting here thinking it just cant be that easy, Thought I had read that you had to use built in programs to extract and install programs downloaded as tar.gz files. I seem to be even more confused than I was earlier. How do I know or find out what has to go through an installation process or what just gets extracted and run?

---

### Post by aysiu on 2007-11-21
Simply extracting the .tar.gz does not install Firefox. It does not create a working menu item for you. It does not allow the command *firefox* to launch Firefox. It doesn't link Firefox to any of your multimedia plugins. And it leaves Firefox in your home directory.

Listen to mikewhatever. You need UbuntuZilla.

---

### Post by MrFSL on 2007-11-21
> The icon to run the program is somewhere in the extracted folder?just sitting here thinking it just cant be that easy, Thought I had read that you had to use built in programs to extract and install programs downloaded as tar.gz files. I seem to be even more confused than I was earlier. How do I know or find out what has to go through an installation process or what just gets extracted and run?

When downloading source files. (Non-compiled code) Which are often packaged in tar.gz or tar.bz files then you would have to go through the whole:
```
./configure
make
sudo make install
```

The directly downloaded versions of firefox and thunderbird have a pre-compiled binary that can be used to launch the program. You can extract it to wherever you'd like and use it from there. (I extract mine to the /opt folder)

> Simply extracting the .tar.gz does not install Firefox. It does not create a working menu item for you. It does not allow the command firefox to launch Firefox. It doesn't link Firefox to any of your multimedia plugins. And it leaves Firefox in your home directory.


True - (mostly). Simply extracting does not "install" in the common sense but the program is still quite usable. Extracting does not create a working menu item but the download contains everything you need (including an icon file) to create your own... etc. 

I disagree that it necessarily leaves Firefox in your home directory since that is quite defendant on where you extract it too and where you set up links etc.

 > I seem to be even more confused than I was earlier. How do I know or find out what has to go through an installation process or what just gets extracted and run?

I'm sorry to have confused you. I think that the mozilla group pre-compiles this to try and make it easier, but I understand how it can be confusing. What I do with these types of files is extract them, then look at the contents for a readme file or and install file that will let me know what I should do next.

If that doesn't work you can always go back to the manufacturer and ask on their website. 

Here:
[http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)
are some generic instructions offered by mozilla to install this binary package in Linux. 

> Listen to mikewhatever. You need UbuntuZilla. 
@aysiu
Need? I agree that in some instances it might make things easier but it surely isn't conducive to learning more about how the O/S is laid out, nor how mozilla has chosen to package their software downloads etc.

---

### Post by aysiu on 2007-11-21
> **MrFSL said:**
> 
I disagree that it necessarily leaves Firefox in your home directory since that is quite defendant on where you extract it too and where you set up links etc. I didn't see any instructions above about extracting to somewhere outside home or setting up links. If someone downloads the .tar.gz and double-clicks it to extract, it will extract to the home directory or the desktop directory within the home directory.

> @aysiu
Need? I agree that in some instances it might make things easier but it surely isn't conducive to learning more about how the O/S is laid out, nor how mozilla has chosen to package their software downloads etc. I didn't see the OP asking to learn how the OS is laid out. Telling someone to "simply extract the .tar.gz and go" does not help her learn anyway.

If someone wants to learn, then these instructions are best:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

This page also outlines all the major methods for getting the Mozilla version of Firefox installed:
[HowTo Install the Latest Firefox in Ubuntu (Ultimate HowTo)](http://ubuntuforums.org/showthread.php?t=330386&highlight=firefox)

---

### Post by stchman on 2007-11-21
> **Gildp67 said:**
> Well I just down loaded the latest fire fox and thunder bird and they are tar.gz, being a noob to all this how do I install them. please make it as easy and step by step as you can, as I have never installed any tar.gz files yet. Thanks for any and all help


Mozilla website download for Firefox and Thunderbird are pre-compiled binaries so you won't need to make them or compile them.  If you wish to compile from source then I believe Mozilla has the source in their developers section.

The latest Firefox pertinent to Ubuntu is in the repositories.  You won't need to do anything.

As far as Thunderbird, if you run Gutsy then you get Thunderbird 2.  Feisty or earlier has Thunderbord 1.5.

If you want to install the latest Thunderbird in Feisty or older then use my Thunderbird 2 script.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

It is in the Scripts section.

If you wish to install Thunderbird 2 on Gutsy use the following command:

```
sudo apt-get -y install thunderbird
```

I hope this helped.

---

