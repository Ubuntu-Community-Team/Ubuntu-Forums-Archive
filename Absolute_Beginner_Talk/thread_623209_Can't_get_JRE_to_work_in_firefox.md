---
title: "Can't get JRE to work in firefox"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by asbjornn on 2007-11-25
I need to install a browser plugin - Java Runtime environment, my browser tells me. My adept manager tells me I've got Sun Java 5.0 Runtime installed, but it doesn't effect firefox. How do I get this to work in firefox?

Please note I'm brand new in linux, so please take me slowly through all the steps. 

Asbjornn

---

### Post by Ub1476 on 2007-11-25
You have an earlier version of Java. Open add/remove, search for Java, remove "Sun Java 5.0 Runtime" and install "Sun Java 6 Web Start" (you can also install ubuntu restricted extras which also will install flash, codecs etc).

Make sure that Firefox allows Java. Edit>Preferences>Content.

---

### Post by asbjornn on 2007-11-26
Hi

Thanks for the answer and the warning, I did read the sticky about malicious commands, though.

I tried removing anything with java in the name, and then installed Sun java 6 web start. I didn't work, and neither did it when I tried installing Sun java web start (32bit) or Java 1.4 plugin for Mozilla/firefox. 

I've got java and java scripts enabled in firefox. 

Any ideas what I'm doing wrong?

Asbjornn

---

### Post by GSF1200S on 2007-11-26
Are you running the 64bit or 32bit version of Ubuntu? 

Open firefox and put the following in the address bar (hit enter):

```
about:plugins
```

and post the results here so we can see where fox is at.. :)

---

### Post by asbjornn on 2007-11-26
I'm running 64bit Ubuntu.
The about:config returns: 

Shockwave Flash
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	                                Description 	   Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	    FutureSplash Player 	spl 	Yes

Hop this makes some sense to you, I don't feel any wiser. 

Asbjornn

---

### Post by evilc on 2007-11-26
To get Java plugin to work with Firefox you must symlink it, Follow the info below ( don't forget to alter any dir & No.s to suit)

Example:

    * If Mozilla is installed in this directory:
      /usr/lib/mozilla-1.4/
    * and if the JRE is installed at this directory:
      /usr/java/jre1.5.0
    * Then type at the terminal to go to the browser plug-in directory:
      cd /usr/lib/mozilla-1.4/plugins
    * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
      ln -s /usr/java/jre1.5.0/plugin/i386/ns7
      /libjavaplugin_oji.so .

This works for Java6 as well, after doing above if you open Firefox in address bar type about:plugins you should see a list of java.

---

### Post by GSF1200S on 2007-11-26
> **asbjornn said:**
> I'm running 64bit Ubuntu.
The about:config returns: 

Shockwave Flash
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	                                Description 	   Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	    FutureSplash Player 	spl 	Yes

Hop this makes some sense to you, I don't feel any wiser. 

Asbjornn

Yes it does.. You meant 

```
about:plugins
```

right? regaurdless, it looks like thats what youve posted. Welcome to 64bit- the only thing still a bit of a pain is java plugins. Sun is supposed to release a plugin for 64bit fox with version 7, but of course they havent released 7 yet. Your workaround is to use the blackdown java plugin, but for whatever reason, it crashes whenever java is encountered on firefox. So, the solution is a bit complicated. You need to use the Swiftweasel web browser (variant of firefox- can use firefox plugins), and then install the blackdown 1.4 plugin for mozilla from add/remove programs. Another option is installing a seperate 32bit firefox browser where the regular java plugins work fine- there are walkthroughs for this on the forums..

I would stay stick with 64bit swiftweasel so that 64bit browsers recieve attention by sun, etc, but that of course depends on your needs. Blackdown has its issues and some java intense sites will cause problems...

---

### Post by GSF1200S on 2007-11-26
> **evilc said:**
> To get Java plugin to work with Firefox you must symlink it, Follow the info below ( don't forget to alter any dir & No.s to suit)

Example:

    * If Mozilla is installed in this directory:
      /usr/lib/mozilla-1.4/
    * and if the JRE is installed at this directory:
      /usr/java/jre1.5.0
    * Then type at the terminal to go to the browser plug-in directory:
      cd /usr/lib/mozilla-1.4/plugins
    * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
      ln -s /usr/java/jre1.5.0/plugin/i386/ns7
      /libjavaplugin_oji.so .

This works for Java6 as well, after doing above if you open Firefox in address bar type about:plugins you should see a list of java.

This works on a 64bit browser?? I just set up swiftweasel a month ago and the word was blackdown java was the only solution.. :confused:

---

### Post by evilc on 2007-11-26
Sorry, thought he was running 32b firefox? As GSF said running FF 32b may be your answer.

---

### Post by GSF1200S on 2007-11-26
> **evilc said:**
> Sorry, thought he was running 32b firefox? As GSF said running FF 32b may be your answer.

Damn... I was hoping you knew something I didnt :) Its odd that something as, dare I say java, would be the last thing to be fixed on the 64bit platform.. Everything else works great..

---

### Post by asbjornn on 2007-11-26
So, now I made it.

Swiftweasel crashed at my first try to use the JRE for something. So I had to go with the 32firefox. I found it a little somplicated to install, but now it works just fine. 

Thank you for your help

Asbjornn

---

