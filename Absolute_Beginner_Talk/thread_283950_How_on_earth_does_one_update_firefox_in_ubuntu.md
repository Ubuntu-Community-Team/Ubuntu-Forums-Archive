---
title: "How on earth does one update firefox in ubuntu?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by internetworld7 on 2006-10-24
I know I'm new to the Linux scene and all but geez guys this process of simply udating Firefox to the new 2.0 version is like pulling teeth in ubuntu. By default I find that the update link in firefox for ubuntu 6.06 LTS is greyed out and disabled with NO OBVIOUS way to enable it! Why? How is that user friendly and intuitive? 

So you'd think all I have to do is just visit Mozilla and simply install the new version right? "Linux for human beings" Hmmm...don't think so. [-(  After downloading it, archive manager appears. What for? I don't care to archive anything I just simply want to install the newest version of Firefox. Now here's where things really start to get silly, you'd think that after extracting the files to my desktop or anywhere for that matter I'd simply be able to install it right? Nope. There's no install option or simple instructions on what to do next. Why? :-k 

Again I know I'm new to Linux (Like 2 hrs old) and I'm willing to read and learn but somethings should simply be automatic and as easy as 123, needing no explanation. 

Is there an easy way to to upgrade the browser? :confused:

---

### Post by aysiu on 2006-10-24
Why don't you wait two days? And your entire system will be updated, including Firefox.

I don't see why human beings wouldn't prefer having everything updated automatically instead of updating programs one by one...

---

### Post by internetworld7 on 2006-10-24
> **aysiu said:**
> Why don't you wait two days? And your entire system will be updated, including Firefox.

I don't see why human beings wouldn't prefer having everything updated automatically instead of updating programs one by one...

Well forgive my ignorance and like I said I am willing to learn and I know I can't learn everything in a day but how was I suppose to know that in two days the system will automaticly update everything :confused:  After installing ubuntu it checked for updates and installed 187 updates already. Is there more to the updating process? I thought that after 187 updates everything was current and ready to go. I assume that OpenOffice will be updated from version 2.0.2 to 2.0.4 as well? 

Also I tried to install Opera but got the following message: "Error: Dependency is not satisfiable: libqt3c102-mt" Anybody knows what that means in plain English? :mrgreen:

---

### Post by taurus on 2006-10-24
Because in two days (or less than two days now), the new release, Edgy Elf, will be out!  Then, you can either upgrade your Dapper to Edgy or you can do a fresh install; it's up to you...

---

### Post by paradj on 2006-10-24
> Originally Posted by aysiu  
Why don't you wait two days? And your entire system will be updated, including Firefox.

I don't see why human beings wouldn't prefer having everything updated automatically instead of updating programs one by one...

never had Windows Antivirus (2003-2006)?

as for the  "libqt3c102-mt" this is a KDE Qt GUI library component you should be able to install it thru synaptic. 
Search for "libqt3-mt"

---

### Post by kerry_s on 2006-10-24
I think you need to read up on synaptic, that is the gui front end for apt-get it gives you access to thousands of packages(software). You also proable never turned on all the repo's, you'll need to do that so you'll get the backport updates.-> 
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Sweet Spot on 2006-10-24
> **aysiu said:**
> Why don't you wait two days? And your entire system will be updated, including Firefox.

I don't see why human beings wouldn't prefer having everything updated automatically instead of updating programs one by one...

On this one occasion, I'm going to have to go w/the OP here. Ironically enough, I was at a friend's house today, installing Ubuntu. When I did my install, everything went honky dorey, but of COURSE, that was all different today, on HIS machine ! 

Let's see, first off, the freekin' Mozilla devs decided that today was a fine day to totally redo their website, so now the layout for extensions and themes etc, is totally different. No biggie though, looks good. The problem was though, that one of the most useful extensions for Firefox, was updated to work with FF 2.0, and so I had to TRY and explain why he couldn't use tabbrowser preferences because of how the update process for FF was different in Ubuntu. I probably sounded like an idiot trying to make sense at that....

Then, we spent way too much time trying to figure out how to get his wireless to work, and failed, miserably. But I"ll try to get the answers to that later..... 

Yeah, it would be nice if FF updates were available like....immediately. 

Doug

---

### Post by steveneddy on 2006-10-25
Remember that this isn't windows from microsoft, this is Ubuntu. It is going to be different, and some things you are going to have to relearn, or actually learn something nesw and different.

Synaptic can be found by going to System-->Administration-->Synaptic Package Manager.

This is where you find all of the software that is made available to you from the folks that distribute Ubuntu, Debian (where Ubuntu came from) and the Linux community.

To update Firefox, open a terminal. Gnome terminal can be found under Applications-->Terminal.

Type in:

> sudo firefox

then go to Help in Firefox, then Check for updates. One has to be a root user to perform administration function on Linux. It keeps you from bungling up a good install on accident by clicking on something or accidently installing something that you shouldn't have.

Go to the website that aysiu has - the psychocats site, and read about Ubuntu there.


good Luck.

-SE

---

### Post by fandelau on 2006-10-25
> **internetworld7 said:**
> Again I know I'm new to Linux (Like 2 hrs old) and I'm willing to read and learn but somethings should simply be automatic and as easy as 123, needing no explanation. 

Is there an easy way to to upgrade the browser? :confused:

Well, small steps internetworld7, small steps...
As some one mentioned in one of the replies, read up on apt-get and synaptic that would help greately when installing/upgrading/uninstalling any piece of SW you want in or out of your computer.
A great site for Dapper setup is [Ubuntu Starter Guide]("http://ubuntuguide.org/wiki/Dapper"), well written, very detailed, excellent piece of documentation for setting up your Dapper box.
Pay special attention to the part where the repositories are explained. Repositories are sites where SW packages are stored. Apt-get and synaptic look at these repositories for new installs, and upgrades, so it's a matter of having the right repositories for the SW you wish to install... Once you setup the repositories  that you need, upgrades are "automatic and as easy as 123, needing no explanation." ;) 
... Or you could wait until the new Ubuntu release, Edgy Eft, just a couple of days from today, and get the new Firefox version already included, then...
If impatient, break the glass and use this procedure ;) ... 
[http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/")
I hope this helps...

---

### Post by SunnyM on 2006-10-25
[http://ubuntuforums.org/showthread.php?t=248158](http://ubuntuforums.org/showthread.php?t=248158)

---

### Post by aysiu on 2006-10-25
> **Sweet Spot said:**
> 
Let's see, first off, the freekin' Mozilla devs decided that today was a fine day to totally redo their website, so now the layout for extensions and themes etc, is totally different. No biggie though, looks good. The problem was though, that one of the most useful extensions for Firefox, was updated to work with FF 2.0, and so I had to TRY and explain why he couldn't use tabbrowser preferences because of how the update process for FF was different in Ubuntu. I probably sounded like an idiot trying to make sense at that.... First of all, you can install Firefox 2.0 from Mozilla in Ubuntu. You don't have to use Ubuntu's 1.5.0.7.

Secondly, it cuts both ways. My favorite extension, Tab Mix Plus didn't have an update for 2.0, so I tried installing Tabbrowser Preferences, and that borked my "I'm Feeling Lucky" search bar behavior.

Life's a b***h when it comes to compatibility and versions. That's the way it is.

---

### Post by tubasoldier on 2006-10-25
Honestly there is an "easy way" to install firefox 2 for the next couple of days before you can upgrade through synaptic. 

Download the firefox.tar.gz file from their website. Extract the archive, and then execute the "firefox" script in the folder. It will not be integrated into your system very well, but it will still retain and use all the preferences you set wile using firefox 1.5. In two days upgrade your os and delete the firefox folder.

---

### Post by aysiu on 2006-10-25
If you don't like waiting for Ubuntu's Firefox to update, take a look at this thread: [HowTo: A script to install the latest Firefox](http://ubuntuforums.org/showthread.php?t=151179)

---

### Post by SandroG on 2006-10-25
Guys, guys, guys....

Way too much complication in here. There are a couple of reasons why I cannot yet update to Edgy until next week or later, and so I share part of internetworld7 plight's. I have tried the forum for two days and things did not work perfectly or not at all when trying different methods to install FF2. 

The best piece of advice is that of steveneddy.

KEEP IT SIMPLE GUYS! His is the definitive recomendation. Easy and effective, and your Granny can do it.

On the top left hand side of your screen click on Applications --> Accessories --> Terminal

Type in the new window that opens the command:
sudo firefox
Press enter
Enter your password

Firefox will then open with root priviliges
In Firefox's menu click on Help --> Check for Updates

Voila!
Simple!

Thanks steveneddy!

---

### Post by Bachstelze on 2006-10-25
Please use gksudo instead of sudo to run GUI apps as root...

---

### Post by LookTJ on 2006-10-25
Have you tried this in terminal?

```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by aysiu on 2006-10-25
> **SandroG said:**
> 
KEEP IT SIMPLE GUYS! His is the definitive recomendation. Easy and effective, and your Granny can do it.

On the top left hand side of your screen click on Applications --> Accessories --> Terminal

Type in the new window that opens the command:
sudo firefox
Press enter
Enter your password

Firefox will then open with root priviliges
In Firefox's menu click on Help --> Check for Updates Apart from the fact the command is *gksudo firefox*, I don't see how that will work. If you have the Ubuntu build of Firefox, it's not self-updating until Ubuntu updates it. The self-updating feature has been turned off. And I don't believe even the Mozilla build will self-update from 1.5.0.7 to 2.0. As far as I can tell, the self-updating works for only newer security upgrades of the same version (1.5.0.6 to 1.5.0.7, for example).

Are you really telling me you used a Ubuntu build of Firefox 1.5.0.7, did *sudo firefox* and were able to update to 2.0?

---

