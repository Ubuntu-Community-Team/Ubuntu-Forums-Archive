---
title: "Help with Java--Lots of Problems"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by darkwarrior0404 on 2006-04-01
jre-1_5_0_06-linux-i586-rpm.bin        <-- I have installed this to my desktop, and I am absolutely clueless where to go now, I've asked and looked at 10+ different websites and everything tells me directions that don't work, in my synaptic package manager, when i start it, it gives me this message

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

So i press okay, go to settings>repositories and then i get this list, i have enabled the multiverse and universe, which boxes need to be checked from here, cause I'm having a feeling that a error of mine may be in this and not letting me install java now.  could this be the problem? What do I do now??

---

### Post by localzuk on 2006-04-01
Take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) - near the bottom there are instructions on how to use java. The rpm you have downloaded is not really much use to you - you need the other version (non rpm). But then the site above should tell you all you need to know :)

---

### Post by darkwarrior0404 on 2006-04-01
Thanks, downloading the .bin file now, so with Ubuntu 5.10 rpm files don't work? I'm new to Linux and still trying to get in the swing of things haha, and about repositories from synaptic, does anything special need to be done in order to do it this way from Wiki?

Edit: How do you make a file Executable?

---

### Post by taurus on 2006-04-01
```

sudo chmod 755 filename

```

---

### Post by darkwarrior0404 on 2006-04-01
> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Alright I'm having problems *still* I've tried changing one of the universe things to univers multiverse, and im following directions but nothing is working, it's hopeless lol.. because if i enable the repositories, it starts giving me errors and what not, ](*,)  im so stumped on what to do next, because if I type in the commands from the terminal it tells me, it always gives me some weird error as well and this makes the second day I've tried getting java on here, :-k  hmmmm what to do??:confused:

---

### Post by darkwarrior0404 on 2006-04-01
> I am trying to enable more repositories, so i am following this tutorial
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
but what deos it mean by copying and pasting "over" the sources.list????
obviously i am quite capable of copying and pasteing but what deos it mean by "over"?

cheers


Okay with a mix of that site, and [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) <--that site, its now installing through the terminal, I think I just had the repositories screwy, any ideas?:eek:

---

### Post by darkwarrior0404 on 2006-04-01
> darkwarrior0404@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
darkwarrior0404@ubuntu:~$ sudo gedit /etc/apt/sources.list
darkwarrior0404@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [13.8kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [915kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [38.0kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.2kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 4376kB in 2m53s (25.2kB/s)
Reading package lists... Done
darkwarrior0404@ubuntu:~$ sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mozilla-browser mozilla-firefox galeon
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  j2re1.4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.5MB of archives.
After unpacking 60.3MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse j2re1.4 1.4.2.02-1ubuntu3 [22.5MB]
Fetched 22.5MB in 15m2s (24.9kB/s)

Preconfiguring packages ...
Selecting previously deselected package j2re1.4.
(Reading database ... 61888 files and directories currently installed.)
Unpacking j2re1.4 (from .../j2re1.4_1.4.2.02-1ubuntu3_i386.deb) ...
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...


and for instance if i try going to yahoo chat now, it still says java isnt installed?](*,)

---

### Post by darkwarrior0404 on 2006-04-01
help, anyone? O.o

---

### Post by darkwarrior0404 on 2006-04-01
Please anyone lol, its going on 24+hrs trying to figure something out as small as java, I check the version through the terminal and it says its right there, but it doesnt say I have it whenever I check it like with some java chat or even on java's website, : (:confused:

---

### Post by mrpeanut on 2006-04-01
Did you install the new version of Firefox?  Chances are that you have java, but just have to create a symbolic link to get it to work.  That's what I had to do.  I'll search around a bit and see if I can find it again.

---

### Post by darkwarrior0404 on 2006-04-01
I have Firefox 1.5   is that the newest? If not how do I upgrade it? very new to Ubuntu and well yeah lol](*,) sorry for being so annoying

---

### Post by Omnios on 2006-04-01
This is the wiki link Java is almost at the bottom of the page.

 [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=AddingJavaSupport")

---

### Post by darkwarrior0404 on 2006-04-01
> darkwarrior0404@ubuntu:~$ sudo apt-get install j2re1.4
Reading package lists... Done
Building dependency tree... Done
j2re1.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


it says I already have it??

> dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXXVeZl1M/sun-j2re1.5_1.5.0+update06_i386.deb'.
    copy sun-j2re1.5_1.5.0+update06_i386.deb into directory /home/darkwarrior0404/Desktop/

The Debian package has been created in the current directory. You can
install the package as root (e.g. dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb).


Removing temporary directory: done
darkwarrior0404@ubuntu:~/Desktop$


Does this mean it done it right??? hope I did something right finally....:-k

---

### Post by christhemonkey on 2006-04-01
You now need to do what it says and type:
```
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
```

---

### Post by darkwarrior0404 on 2006-04-01
> darkwarrior0404@ubuntu:~/Desktop$ sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
(Reading database ... 63977 files and directories currently installed.)
Preparing to replace sun-j2re1.5 1.5.0+update05 (using sun-j2re1.5_1.5.0+update06_i386.deb) ...
Unpacking replacement sun-j2re1.5 ...
Setting up sun-j2re1.5 (1.5.0+update06) ...

darkwarrior0404@ubuntu:~/Desktop$ 


Okay, after this completes, do I have to restart my computer?? Because I went to Java's website to verify that it had went, and its still telling me I need plugins... there is no hope ](*,)

---

### Post by christhemonkey on 2006-04-01
You need to make sure you make the extensions where they should be:
```

cd /home/username/.mozilla/plugins
ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

```

---

### Post by darkwarrior0404 on 2006-04-01
[QUOTE=christhemonkey]You need to make sure you make the extensions where they should be:
```

cd /home/username/.mozilla/plugins
ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

```[/QUOTE]


Alright I checked all of that and this is what I got

> darkwarrior0404@ubuntu:~$ cd /home/username/.mozilla/plugins
[email]darkwarrior0404@ubuntu:/home/username/.mozi[/email]lla/plugins$ ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
ln: `libjavaplugin_oji.so': File exists
[email]darkwarrior0404@ubuntu:/home/username/.mozi[/email]lla/plugins$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
ln: `/usr/lib/mozilla-firefox/plugins//libjavaplugin_oji.so': File exists
[email]darkwarrior0404@ubuntu:/home/username/.mozi[/email]lla/plugins$


---

### Post by christhemonkey on 2006-04-01
Then restart firefox and you should be good to go!

---

### Post by darkwarrior0404 on 2006-04-01
I do restart Firefox.. and still nothing? Is this user error? Would me having a Firefox theme hurt anything? :confused:

---

### Post by darkwarrior0404 on 2006-04-02
Alright good deal, I got it installed finally, still not sure exactly how I done it, just was talking to a guy and he told me to copy/paste stuff sooo it's working now, thanks everyone :mrgreen:

---

### Post by adamkane on 2006-04-02
Reference:
 [http://www.zoia.org/blog/archives/20...ubuntu-breezy/]("http://www.zoia.org/blog/archives/2006/01/09/bluej-en-ubuntu-breezy/")
 [https://wiki.ubuntu.com/RestrictedFormats#java]("https://wiki.ubuntu.com/RestrictedFormats#java")
 
 Add the universe and multiverse repositories, if you haven't already:
 [http://easylinux.info/wiki/Ubuntu#Ho...a_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")
 
 Install fakeroot and java-package:
 
```

sudo apt-get install fakeroot java-package

```[LEFT]
[/LEFT]
      Download and install J2SE Development Kit 5.0 Update 6 (Linux Platform):
 [http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp")
 
```

cd ~/Desktop
fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java

```

Select:
/usr/lib/j2sdk1.5-sun/bin/java

---

### Post by darkwarrior0404 on 2006-04-02
Hey thanks again : ) sorry to be such a nuissance (sp?) It's finally working now yay:mrgreen:  48 hrs !! lol

---

