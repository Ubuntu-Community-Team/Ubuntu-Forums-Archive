---
title: "This is my 2nd day, I'm trying to install java"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-12
Hello, I have been trying to install java and firefox plugins for java on my xubuntu 6.0.6 1LTS

I have installed both automatix2 and EasyUbuntu and have added repositories. All of my repositories are checked in synaptic/settings/repositories and I have added wine to the add/custom repositories in synaptic.

This is my saved sources.list pasted below:


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


The code I pasted below is what happened when I followed instructions from this guide: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)


me@me-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
me@me-laptop:~$ sudo update-alternatives --config java
No alternatives for java.
me@me-laptop:~$ sudo chmod a+x jre-1_5_0_08-linux-i586.bin
chmod: cannot access `jre-1_5_0_08-linux-i586.bin': No such file or directory
me@me-laptop:~$ sudo ./jre-1_5_0_08-linux-i586.bin
sudo: ./jre-1_5_0_08-linux-i586.bin: command not found
me@me-laptop:~$ cd /usr/lib/firefox/plugins
me@me-laptop:/usr/lib/firefox/plugins$ sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
me@mer-laptop:/usr/lib/firefox/plugins$ cd /usr/lib/mozilla/plugins
me@me-laptop:/usr/lib/mozilla/plugins$ sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
me@me-laptop:/usr/lib/mozilla/plugins$
me@me-laptop:/usr/lib/mozilla/plugins$


** I was wondering if someone could guide me in the right direction for a begginer, thanks,
-c.

2nd question: I edited my sources.list and pressed save and it saved as sources.list.saved

how do I make that sources.list.saved list, the main sources.list?

---

### Post by FizDev on 2006-10-12
Try using the Automatix you installed, I believe you can install Java with it. You shouldn't have any problems! :)

By the way, the main sources.list is located in /etc/apt/
Just replace the one there with your one.

---

### Post by crimesaucer on 2006-10-12
could you explain "how to use the program" for automatix2?? I thought that it was just something that would run in the background to enable my web browseing and certain media players to show video. thanks.

Also. I think I added my changes of my saved sources.list.saved to my sources.list correctly, please tell me if this is proper procedure:

sudo mousepad /apt/etc/sources.list (then edit the additions, save, close,) then run sudo apt-get update

correct? I think my problem was that I edited my sudo mousepad /apt/etc/sources.list then saved it and didn't close it and continued trying to get the java, so it save as a sources.list.saved? does that sound right.

thanks. And as confused as I am, it's pretty fun learning and this xubuntu is so fast when browseing.

---

### Post by Crashmaxx on 2006-10-12
No, Automatix doesn't run in the background. It is just a script to install a bunch of common programs.

Just go to Applications>System Tools>Automatix and choose what you want to install. Then java should work, and it should setup-up your sources.list automatically.

Hope that helps.

---

### Post by crimesaucer on 2006-10-12
is having duplicate sources.list entries bad:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

thanks.

---

### Post by FizDev on 2006-10-12
Hmm.. not too sure about Automatix -->2<--
But all you should have to do is open a terminal and type either
```
automatix
```
or
```
automatix2
``` (I suppose)

Then just check the line where it talks about the Java JRE, click OK then wait and enjoy ;)

---

### Post by crimesaucer on 2006-10-12
Thank you crashmaxx and fizdev, I'll try those ways right now.

Is it better to use terminal? I'm starting to get used to it, for my second day at least.

Does EasyUbuntu work the same way as automatix2?

---

### Post by FizDev on 2006-10-12
Yep

---

### Post by crimesaucer on 2006-10-12
So fizdev, I should edit and delete all duplicate repositories?

actuall, those are the ones I checked in the synaptic manager's repository settings, huh?

---

### Post by FizDev on 2006-10-12
Sorry for the confusion :S
> **crimesaucer said:**
> Does EasyUbuntu work the same way as automatix2?
Yep

And about the duplicate repositories, you should delete them, though I don't think it will create any problems.

---

### Post by Crashmaxx on 2006-10-12
Yeah, get rid of the duplicates, they will just cause problems.

But for reference, you don't need to directly edit sources.list, I prefer to use synaptic>repositories. It has an add button for additional ones.

---

### Post by GregB on 2006-10-12
Why all of that to install Java?  It's alot simpler, although it took me a couple of days of searching the forums to figure out how easy it really is:

Enable the Multiverse and Universe repositories by going to System > Administration > Software Properties; Select 6.06-LTS (Source) and then click add. Check all the boxes (Multiverse, Universe, etc) then click OK.  Click Close, then Reload.

From there, you can either use the Add/Remove program (Search for Sun Java) or even easier, open a terminal and use the following commands:

sudo apt-get install sun-java5-jre
sudo apt-get install sun-java5-plugin
sudo update-alternatives --config java (to set the default java to the newly installed Sun)

---

### Post by crimesaucer on 2006-10-12
thank you both, and I'll check out the EasyUbuntu also.

I used the repositories/ in settings / for synaptic at first, then I followed instructions for the automatix2 and I saw how it could be done through terminal and then I added repositories from this page: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories) in terminal and it was fast besides a little confusion and of course my duplicating three of them, and I really liked working with terminal. 

and I used the add+/custom to add the wine in synaptic/settings earlier so...at least I'm learning a few different ways.lol 

Thanks for all of the help.

---

### Post by crimesaucer on 2006-10-12
Greg B, this is what I did. I checked all of those repository boxs, right off the bat, on the first day, then since it was my first day, I read the forums and thought automatix2 and EasyUbuntu sounded like a good idea. Yet obviously, I might have installed them correctly through terminal, but I hadn't learned how to actually run the programs yet,(I still haven't, this is only my second day on a linux, ever) and so after going to the Firefox plug in page and trying to visit a site that requires java, I realized I still needed java so I started to read about simple codes to write like:

me@me-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin

but every time I put that code into terminal, I got this response:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

so, after re-editing my sources.list and adding a freecontrib gpg key and a freecontrib repository, and a canonical repository and all of the updates for main restricted universe multiverse repositories, then updating in terminal with sudo apt-get update, and then writing:

sudo apt-get install sun-java5-jre sun-java5-plugin

and then HOLY SH*T!! ...IT WORKS!!! I INSTALLED USING TERMINAL and not even automatix2 or EasyUbuntu!!! all of this while chatting with you on this forum. hah ha. This is pretty fun...(yeh, yeh...newb installs java5 and thinks he's a hacker now...lol..ha..hah..ha...I can hear the heckling!)

---

### Post by crimesaucer on 2006-10-12
So I'm sure no one is reading this thread, but I'll ask here anyway before making a new thread.

So since I properly installed the java5 and the java5plugin, and have installed the wine repository earlier, now if I run automatix2, if I check boxes like the java/flash plug-ins and a program like wine, with already having them installed, will that matter?

Do I even need wine, if they have wine offered in automatix.

and when I close automatix2, I should go back to my original source.list, correct.

thanks if anyone can explain.

---

### Post by Linux&amp;Lizards on 2006-10-12
automatix rock just click on all the java plug-in options and then hit start.
thats what i did and now my computer is working fine:)

---

### Post by crimesaucer on 2006-10-12
well... this is just my 2nd day, and I didn't even know that I had to open automatix2 like a program until just 5 minutes ago, and during my last day while wondering why the automatix2 (which I thought just worked like "plugins") wasn't playing java, (yes..I am stupid.) I just went ahead and taught myself how to install java5 and the plugin using terminal, without the use of automatix2 or EasyUbuntu.

Now I'm wondering if it is all right to use the automatix2 program and check the box with the flash/java plugins, since I now have already installed it properly. (useing the terminal and a text install page)

I'm wondering if I should just go through a list of everything I need, that automatix2 offers, and try to install them on my own using terminal.

Any suggestions.

---

