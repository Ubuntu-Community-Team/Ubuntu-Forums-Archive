---
title: "Replacing firefox 64 bit with firefox 32 bit"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by quickk on 2006-11-29
Hi everyone,

   I've spent probably what amounts to a few days trying to get firefox (64 bit) working with java and flash.  I can mostly get flash to work, and I can get java 1.4.2, but I need java 1.5.  It's my understanding that no such 64 bit plugin exist.  I've tried to install firefox 32 bit along side the 64 bit version, but I just can't get it to work properly.

My questions is this: is there any way to get completely rid of firefox64, and instead just have the default browser as firefox32?  Is there a reason to keep firefox 64 around?

I really don't see any merit to having the 64bit version of firefox installed as getting it to work with various plugins  seems to be the single greatest source of frustration out there for new linux users like me.  

On a side note, I was wondering how is it possible to uninstall things that were installed with apt-get install, or dpkg -i .  For example, in order to get firefox 32 to work, I tried the script at this link: [http://www.ubuntuforums.org/showthread.php?p=1174435]("http://www.ubuntuforums.org/showthread.php?p=1174435")
it installed firefox32 and java 1.4.2, among other things.  When I try to uninstall these things with dpkg -r, the system complains that no such package is installed.  I know that they are though, and that they should somehow be registered with the system, because the script installed them using dpkg -i.  How do I get the right names so that I can uninstall these things?  

Any help would be greatly appreciated!

---

### Post by pay on 2006-11-29
You can install firefox 32bit on amd64, but I have had great success running 32bit plugins on a 64bit browser using nspluginwrapper, maybe you should try that first.

---

### Post by quickk on 2006-11-29
I tried nspluginwrapper, but it only works for Netscape 4 plugins.  I really need the java 1.5 plugin, but unfortunately, there is no NS4 version so nspluginwrapper doesn't work.  Have you found a way?  

Are there any disadvantages to removing firefox 64-bit?  Is there a way to make firefox 32-bit the default browser (so that it opens when I click on a link in thunderbird, for example)?

One last question: say I get firefox 32 working.  How do I get totem plugins to work in firefox 32?  I've tried creating a symbolic link from the totem library files (the *.so ones), to the firefox32 plugin directory but firefox32 doesn't seem to see these plugins.  Am I missing anything?

Thanks!

---

### Post by pay on 2006-11-29
Heres how to install firefox32 [http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435) To get totem to work you would need the 32bit version of Totem. It would be easier to use the 32bit version of mplayer. To have firefox32 the default then look at the complete replacement section from that link. 
BTW netscape plugins basically are any linux plugins that work with firefox, java, flash, mplayerplug-in acroread are all examples of netscape plugins and I have gotten them all to work with firefox64 if you wanted to give nspluginwrapper another go. But the choice is yours. BTW to test if the plguin is working type "about:plugins" in firefox Goodluck.

---

### Post by quickk on 2006-11-29
Thanks for the help!  Ideally, I'd really like to get everything working with firefox 64 and teh nspluginwrapper.  I've spent a few solid days trying to achieve this goal, and have succeeded in installing everything (flash9, acroread, multimedia plugins), except for java.  To be specific, I CAN get java 1.4.2 to install (there's a native 64 bit plugin available), but whenever I try to install the 1.5 version, nspluginwrapper keeps giving me an error because it says that the java library file isn't a netscape 4 one.  If you look at the nspluginwrapper website [http://http://gwenole.beauchesne.info/projects/nspluginwrapper"]http://gwenole.beauchesne.info/projects/nspluginwrapper/"]http://http://gwenole.beauchesne.info/projects/nspluginwrapper]("http://gwenole.beauchesne.info/projects/nspluginwrapper/")
they specifically say that "nspluginwrapper is an Open Source compatibility plugin for Netscape 4 (NPAPI) plugins".  

If you somehow managed to get java 1.5 to work with this wrapper I'd be EXTREMELY interested in finding out how you did it (and I think that a lot of other people would be too!).

---

### Post by pay on 2006-11-30
Ok I was mistaken. sun-java-jre doesn't work with nsplugwrapper. I have Blackdown Java 1.4.2-03 working with firefo64, but it doesn't have a 1.5 version yet.

---

### Post by alican timur on 2006-11-30
is it possible in any way to use the last flash player plugin (9, i think) with firefox 64bit?

---

### Post by pay on 2006-11-30
Use it is with nspluginwrapper

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 d78
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Thats whats under my about:plugins in firefox

---

### Post by Unterseeboot_234 on 2006-11-30
I installed the NetBeans5.5_Java1.5_09 bundle which installed JRE and Java Web Start and they didn't work in 64-bit Firefox. I then went back to Automatix and let it install the "SwiftFox 32-bit" and let it add what plug-ins. Then, I had java 1.5 running as an applet, an embed jar and as JNLP (web start). But, I have to let Firefox Download Manager unload the file onto the computer, then I can double-click the download.jnlp and finally have my java running in Java Web Start. Such a hassle. If you think you HAVE installed JRE 1.5, you probably have and there will be links that I know NOTHING about. I had similar problems on 32-bit because that ubuntu installs all the other java. You have to quit 64-bit Firefox and fire up Swiftfox, otherwise things don't work.

I like 64-bit. There's just no software. Makes me focus on java / ruby. Wished I had more time for linux. And, I know the java that runs on 64-bit, 32-bit linux won't have a problem on M$ products.

---

### Post by non-free on 2006-11-30
> **Unterseeboot_234 said:**
> I installed the NetBeans5.5_Java1.5_09 bundle which installed JRE and Java Web Start and they didn't work in 64-bit Firefox. I then went back to Automatix and let it install the "SwiftFox 32-bit" and let it add what plug-ins. Then, I had java 1.5 running as an applet, an embed jar and as JNLP (web start). But, I have to let Firefox Download Manager unload the file onto the computer, then I can double-click the download.jnlp and finally have my java running in Java Web Start. Such a hassle. If you think you HAVE installed JRE 1.5, you probably have and there will be links that I know NOTHING about. I had similar problems on 32-bit because that ubuntu installs all the other java. You have to quit 64-bit Firefox and fire up Swiftfox, otherwise things don't work.

I like 64-bit. There's just no software. Makes me focus on java / ruby. Wished I had more time for linux. And, I know the java that runs on 64-bit, 32-bit linux won't have a problem on M$ products.

Swiftfox is not free software. It takes away your freedom to redistribute. It cant be included in any official repository because of this. Firefox is redistributable. Swiftfox takes the Firefox code then takes away a freedom Firefox has.

---

