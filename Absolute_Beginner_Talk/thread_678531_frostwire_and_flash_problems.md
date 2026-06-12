---
title: "frostwire and flash problems"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by gcnakul on 2008-01-26
******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)


+

cant view any youtube videos
though i have Adobe Flash Player plugin installer installed

---

### Post by LukeCarrier on 2008-01-26
Hello there,

The flash player installation fails at the moment because Adobe have updated it, and the installer that's currently in the repositories believes its got a faulty file. I don't know when this will be fixed, but [this thread]("http://ubuntuforums.org/showthread.php?t=636397") should help for now.

A little further down the page in blue are a couple of download liinks, download the package that's right for you computer, save it to the desktop.

Now open a terminal window and type:
```
sudo aptitude remove flashplugin-nonfree
```
then press enter, and follow the prompts. When this is finiahed, close all web browser windows, then double click the install file you just donloaded. Click install package, enter you password when prompted. You've just installed the flash player, so the problems with flash are now fixed.

As for you Frostwire problem, I'm sorry to say I have absolutely no idea what's wrong with it. I've had problems in the past but have found the people in their community are good at troubleshooting this sort of problem, maybe you'd like to go and ask over there?

Hope this helps you,
Luke.

---

