---
title: "Firefox update"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by bobity on 2006-10-28
Hi,
This seems dumb but in lots of searching I can't find an answer.  I am running 6.06 LTS dapper drake, updated online to latest stuff.  Firefox 2.0 has come out, so I download firefox-2.0.tar.gz to the Desktop.  Now what do I do?  

The firefox 2.0 release notes are singularly uninformative.  Add/Remove software applications seems ONLY to look at the Internet for updates, as does Synaptic.  I can get neither to look into the file system.  Nor can I get the Update Manager to consider the idea that a new version of Firefox might exist.  I can see that an individual userID can install apps in their local /home just for themselves -- for Firefox of course I want to update the version for all users.  

I feel sure that this question must have been asked before, probably for some other application, but I haven't found a hint of it.

---

### Post by d3v1ant_0n3 on 2006-10-28
I had a quick look, and [ THIS](https://help.ubuntu.com/community/FirefoxNewVersion) seems promising.

The search function on these forums is very handy if you can just use the right terms in it. (I chose **Update Firefox**).

Hope that helps some.

---

### Post by TheWizzard on 2006-10-28
> so I download firefox-2.0.tar.gz 
this is a source package. 

it is always good if you learn to build from source, but firefox is not the ideal program to start learning. 
if you build from source make sure you always(!) use checkinstall. 

> The firefox 2.0 release notes are singularly uninformative.
they probably are. but you need some background. 

FF 2.0 will probably be backported (do you have the repos anabled) so it'll be available for ubuntu soon. new software works differently in linux.

---

### Post by Aranel on 2006-10-28
> **TheWizzard said:**
> this is a source package. 

it is always good if you learn to build from source, but firefox is not the ideal program to start learning. 
if you build from source make sure you always(!) use checkinstall. 


they probably are. but you need some background. 

FF 2.0 will probably be backported (do you have the repos anabled) so it'll be available for ubuntu soon. new software works differently in linux.

Um, no. If it were a source package, it would be called "firefox-2.0-source.tar.bz2." The one found at mozilla.com is a binary package that can be used universally on Linux systems.

Now, you have two options. First, you could follow their instructions and un-tar the archive to, say, /usr/lib/ with the following:

```
cd /usr/lib/
sudo tar -xzvf /[path]/firefox-2.0.tar.gz
```

Then if you want, create a symbolic link to its executable in /usr/bin/:

```
cd /usr/bin/
sudo ln -s /usr/lib/firefox/firefox .
```

Then just type "firefox" in the terminal, and you're all set.

Your second option, curiously enough, is Alien. Alien perceives Firefox as a Slackware package, so it can convert it to a Deb. Mozilla.com's Firefox is *not* a Slackware package, though, so if you use it to create a Deb with "sudo alien -d /[path]/firefox2.0.tar.gz" the resulting Deb will install itself in /firefox/. It's a tad simpler that way, albeit a bit on the redneck side, but it also gives you no freedom as to where you want to intall it.

So... take your pick. :)

---

### Post by uBo on 2006-10-29
is it not possble to install Firefox 2.0 on DAPPER from the repos?

i do not want to play with the mozilla version installation.

---

### Post by Bachstelze on 2006-10-29
No it's not since FF 2.0 has not been packaged for Dapper. You can request it in the backports section but I doubt you will get positive answers.

---

### Post by uBo on 2006-10-29
wow, that is a pity!

what is the logic and reason behind it?

---

### Post by TheWizzard on 2006-10-29
> **HymnToLife said:**
> No it's not since FF 2.0 has not been packaged for Dapper. You can request it in the backports section but I doubt you will get positive answers.

yeah, this is what backport repos are for, aren't they? they did in fedora! i certainly don't want to upgrade my system more than once a year. 
i was hoping with dapper (LTS!) i would be doing no new installs for a couple of years.

---

### Post by kc8hr on 2006-10-29
when you untar firefox, it is ready to go. I just put the whole directory in my ~/bin, and it ran fine.

Sadly, some of my favorite extensions didn't work, so I am sticking with firefox-1.5.0.7 instead.

---

### Post by Bachstelze on 2006-10-29
Why should there be a logic ? There's no FF 2.0 package for Dapper because no-one built it, as simple as that. If you want one, you're totally free to build it yourself.

---

### Post by esaym on 2006-10-29
hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

---

### Post by bobity on 2006-10-30
Thanks for this, and all the other helpful responses.  Sorry to take so long to get back to you, but I had trouble tracking down what had happened to my question.  I suspect subscribing to the thread might be a good thing.  After all that, the comments on FF2.0 as an upgrade to FF1.* aren't all that encouraging so I'll probably wait until 2.1 at least.  And then there's always Opera.... :-)

---

### Post by floridauser007 on 2006-11-02
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

worked great for me.

---

### Post by esaym on 2006-11-02
hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

---

### Post by floridauser007 on 2006-11-02
> **esaym said:**
> hehe: [http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)


if you want the desktop icon you will have to copy it from the default install location of /usr/share/applications/swiftfox.desktop and copy it over to /home/user/desktop


:-D

Isn't that swiftfox though?

---

