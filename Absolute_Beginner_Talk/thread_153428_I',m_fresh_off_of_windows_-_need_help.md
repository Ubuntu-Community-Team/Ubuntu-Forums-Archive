---
title: "I',m fresh off of windows - need help"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by fsfast on 2006-03-31
I am fresh off of windows and am attempting to install programs from the internet.

I am used to double clicking on .exe files which automatically open up and install.

In Ubuntu this seems more complicated.

I downloaded the linux version of Skype - this file is sitting on my desktop

When I double click on this file the archive manager opens with the message below:

Could not open "skype_1.2.0.18-2_i386.deb"
Archive type not supported.

In the help menu provided with Ubuntu I see that I should be using the synaptic package manager to install files.  However, this file does not list even with the search.  I've tried adding universe, multiverse and backports - still with no luck.

What procedure do I follow to add programs?  I will also attempt to add java to Firefox - this is a .bin file.

Thanks

---

### Post by Jason_25 on 2006-03-31
When you right click, does it say open with package manager?  If so, click that and it will start a graphical installer window.  If not, then you need to open up a terminal and type
```

cd Desktop
sudo dpkg -i skype_1.2.0.18-2_i386.deb

```

---

### Post by fsfast on 2006-03-31
Thank-you for the instuctions - I found the terminal and copied your post.
Apparently with linux we have to learn some programming language.
This is the text given after hitting the enter key. 

Selecting previously deselected package skype.
(Reading database ... 61269 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-2_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3-mt | libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
fred@ubuntuYCBFF01:~/Desktop$

---

### Post by darkwarrior0404 on 2006-03-31
yeah I'm having the same problem with java, i installed   the       jre-1_5_0_06-linux-i586-rpm.bin            and I'm not figuring out what to do from here, though I'm running ubuntu....

---

### Post by Jason_25 on 2006-03-31
You can try apt-getting libqt3-mt , libqt3c102-mt , and libstdc++5.  It may be easier to search for them in synaptic as they may have slightly different names.  Personally, I always just download the static tarball and be done with it.  I don't have time to waste away at those errors.

---

### Post by Madpilot on 2006-03-31
Skype isn't in Ubuntu's repositories because of licensing issues.

There's a wiki page for Skype, though - not sure if you've found it:
[http://wiki.ubuntu.com/SkypeHowto/](http://wiki.ubuntu.com/SkypeHowto/)

And for your Java install:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

For future reference:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by fsfast on 2006-03-31
Thanks to Jason_25 and madpilot for your responses.

I am gathering that I should only be installing programs that are specifically tested by Ubuntu.  Not all Linux programs or even those debian based will work easily with Ubuntu.  

I should be looking for programs in Ubuntu's repositories.

---

### Post by trent dillman on 2006-04-01
Automatix installs Skype. Query the forums for Automatix.

---

### Post by Jason_25 on 2006-04-01
[QUOTE=fsfast]
I am gathering that I should only be installing programs that are specifically tested by Ubuntu.
[/QUOTE]
This is not not true.
 >  Not all Linux programs or even those debian based will work easily with Ubuntu.  

This is true.

Like I said before, I recommend you download the static tarball, extract it (say to your home folder), make your shortcuts if you want, and you'll be all set.

---

### Post by darkwarrior0404 on 2006-04-01
uhmmm, welllll aside from what programs we use to do things, does anyone know how to install java from terminal? or? I installed java to desktop and i dont know what to do now, any answers??](*,)

---

### Post by Mustard on 2006-04-01
[QUOTE=darkwarrior0404]uhmmm, welllll aside from what programs we use to do things, does anyone know how to install java from terminal? or? I installed java to desktop and i dont know what to do now, any answers??](*,)[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by fsfast on 2006-04-01
What is the purpose of the static tarball.  These are all strange terms to me for someone 3 days into linux.

Is this similar to automatrix.

If I need the static tarball where do I find it on the net.

---

### Post by Mustard on 2006-04-01
[QUOTE=fsfast]What is the purpose of the static tarball.  These are all strange terms to me for someone 3 days into linux.

Is this similar to automatrix.

If I need the static tarball where do I find it on the net.[/QUOTE]

I'm not following what you are saying.  What static tarball are we talking about?  Where is this mentioned?  I think I need to see some context that it is being used in to understand what you are asking.

---

### Post by Tripmonkey_uk on 2006-04-01
I think that Java should already be installed.
Is it the web browser plugin you need?
Instead of Automatix, try [EasyUbuntu]("http://easyubuntu.freecontrib.org/") instead.
Automatix isn't licensed under the GPL (for those that care) like EasyUbuntu is & it also makes changes to your source list, which can be very annoying if you've already spent time tweaking it yourself.
EasyUbuntu will allow you to install the plugin & Skype plus more.
Hope that helps!

---

### Post by BoneKracker on 2006-04-01
While automatix or easyubuntu are useful to get you up and running quickly, it is still important that you understand how to use your system.  This is not Windows - and Windows does not represent "the best of all possible worlds".  Realize that Windows (or DOS) if you go back that far, was also unfamiliar and somewhat difficult for you when you had not yet learned it.  Likewise, you will need to learn some new things about this environment.

I think you will find it very empowering to read some of the documentation that people are pointing out to you (e.g.,  the RestrictedFormats howto).  Enjoy!  : )

---

### Post by fsfast on 2006-04-02
[QUOTE=Jason_25]You can try apt-getting libqt3-mt , libqt3c102-mt , and libstdc++5.  It may be easier to search for them in synaptic as they may have slightly different names.  Personally, I always just download the static tarball and be done with it.  I don't have time to waste away at those errors.[/QUOTE]

Thanks to all again for responses.  I'm enjoying Ubuntu the more I spend time with it.
It was suggested by Jason_25 to download and install static tarball to deal with problems when installing programs - I hope I'm making sense.

---

### Post by Mustard on 2006-04-02
[QUOTE=fsfast]Thanks to all again for responses.  I'm enjoying Ubuntu the more I spend time with it.
It was suggested by Jason_25 to download and install static tarball to deal with problems when installing programs - I hope I'm making sense.[/QUOTE]

I'm guessing here, but I think he is saying that its a tarball installation with all dependencies included?  I've never heard the phrase before, but that's not saying much really.  I've only been on linux since June last year.

---

### Post by belikralj on 2006-04-02
I'm not sure what you want but java is available over synaptic as well. If you are after the java compiler look for the gcj or gjc I can't remember which one, in synaptic. All the other java libraries, apps... are also available there.

I haven't yet explored the command line to get java because I found all I needed over synaptic (I am a bit attached to X and synaptic since I'm fresh out of Win XP).

sorry if I misunderstod what you ment.

---

### Post by Jason_25 on 2006-04-03
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

The last one on the bottom is the one I use.

---

