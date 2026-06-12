---
title: "Installing latest Firefox--why not a straighforward way?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by caljohnsmith on 2008-03-17
I downloaded and installed Ubuntu 7.10 yesterday on my PC on a partition on my HD that all ready has Win XP on another partition, and it is up-and-running just fine after a bit of work. 

After getting my wireless card working with Ubuntu and my router, I loaded up Firefox, and immediately notice that it is 2.0.0.6, not the latest 2.0.0.12. So after researching a little about adding/removing programs in Ubuntu, I found in the threads here:

[http://ubuntuforums.org/showthread.php?t=716928](http://ubuntuforums.org/showthread.php?t=716928)

Is there some reason why I have to use a special installer, i.e. Ubuntuzilla, for Firefox? Is there any way I can just download the version of firefox from mozilla.com, uninstall the old version, and install the new version with the Ubuntu add/remove programs app? 

What I'm getting at, can someone point me to a really good tutorial on simply installing/removing programs in Ubuntu? I was hoping it might be as straightforward as Windows where you download the program you want to install from the web and simply install it with its installer app. Then when you want to remove it, you use the "add/remove programs". 

Thanks for your patience and any help! :)

---

### Post by raul_ on 2008-03-17
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

and 

[http://www.getdeb.net/]("http://www.getdeb.net/")

for installer packages

---

### Post by taurus on 2008-03-17
I am using firefox 2.0.0.12 on my machines running Gutsy.  Have you at least tried to update your machine?

```
sudo apt-get update
sudo apt-get upgrade
```
And of course, you need to enable all the repos in /etc/apt/sources.list first before you run those two commands.

---

### Post by jrib on 2008-03-17
Ubuntu makes a stable release every 6 months and then the repositories are frozen.  This means that there are no updates except for security issues or critical bugs.  This minimizes the risk that new bugs are introduced.

New firefox releases are basically security updates anyway.  What does the new version of firefox do that the current one in the repositories does not do?

Okay, in the past for example Ubuntu had 1.5 in a release when mozilla released Firefox 2.0.  Then there were many new features not available to Ubuntu Users.  This is a drawback, but because of the stable release policy, it's an unfortunate consequence.  

The advantage to using APT instead of downloading and installing things the windows way is exactly that you do not have to maintain your software yourself.  If you install firefox manually, you'll have to always check for a new release from mozilla that may contain a critical security fix and then install it.  On the other hand, with APT, it tells you when an update is available and you just tell it to do its thing.

You can always choose to install software manually.  Usually you just install to /opt or /usr/local.  But then you have to maintain this software yourself.  Back when 1.5 was in the repos and 2.0 was released, people used these instructions: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) .

Personally, I would recommend sticking to the repositories until you get to the point where you don't need the wiki page to know how to do this, then of course you can decide for yourself if it's worth the trouble.

See: [https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)

---

### Post by fourscore on 2008-03-17
Firefox 2.0.0.12 is available  as an update.   You just need to run Update Manager which will list out all the available updates.  

Since you are dual booting with Windows,  you can share the  Firefox  bookmarks, browsing history etc  between  Windows and Ubuntu. See link for more details : [http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761)

---

### Post by caljohnsmith on 2008-03-17
> **taurus said:**
> I am using firefox 2.0.0.12 on my machines running Gutsy.  Have you at least tried to update your machine?

```
sudo apt-get update
sudo apt-get upgrade
```
And of course, you need to enable all the repos in /etc/apt/sources.list first before you run those two commands.

I opened up sources.list and found that almost all the web links were commented out and preceded by "Line commented out by installer because it failed to verify:" Is it OK to uncomment all the websites? I'm curious why they wouldn't be listed as an option to enable in the "Software Sources" program under the "third-party software" tab. 

I'm not afraid of doing things at the command line and modifying files directly, but I wish these type of operations were incorporated into the Ubuntu GUI programs. ;-)
-------------------
Fourscore: When I used the Update Manager to check for new updates, it claimed everything was up to date after running "check". It didn't say anything about Firefox 2.0.0.12 being available.

---

### Post by Ub1476 on 2008-03-17
Open System>Administration>Software Sources

This is the GUI for the sources.list. I suggest you do** not** enable backports, but the rest are fine.

---

### Post by forrestcupp on 2008-03-17
> **caljohnsmith said:**
> I opened up sources.list and found that almost all the web links were commented out and preceded by "Line commented out by installer because it failed to verify:" Is it OK to uncomment all the websites? I'm curious why they wouldn't be listed as an option to enable in the "Software Sources" program under the "third-party software" tab. 

I'm not afraid of doing things at the command line and modifying files directly, but I wish these type of operations were incorporated into the Ubuntu GUI programs. ;-)
-------------------
Fourscore: When I used the Update Manager to check for new updates, it claimed everything was up to date after running "check". It didn't say anything about Firefox 2.0.0.12 being available.

This is what you need to do.  An easier way to enable the repos you want is to go to System->Administration->Software Sources.  Make sure all of the boxes are checked in the Ubuntu Software tab, then click the Updates tab.  Check the boxes that say 'Pre-released updates' and 'Unsupported updates.'  Then close that and open a terminal and do the update/upgrade.
```
sudo apt-get update
sudo apt-get upgrade
```
and you should end up with the newer FF2.

Edit:
someone beat me to it.  But I disagree with the Backports thing.  I've never run into any trouble with it.

---

### Post by raul_ on 2008-03-17
Me neither. At least when I used Ubuntu anyway. There aren't many dishonest people in the free software world (I hope I don't get proved wrong).

---

### Post by Ub1476 on 2008-03-17
Edit:
someone beat me to it.  But I disagree with the Backports thing.  I've never run into any trouble with it.[/QUOTE]

Me neither, but I recall when Compiz 0.6.2 came into backports, and a lot of people had trouble with it. There's a reason for it not being enabled by default..

---

### Post by Paqman on 2008-03-17
You can always roll back to the previous version if an update from the Backports causes some breakage. I don't see any reason not to enable it, especially since it's exactly what the OP was asking about.

---

### Post by Myglaren on 2008-03-17
It should (does for me anyway) update itself BUT it is always about a week late.  I imagine that this is because the Ubuntu developers check out the update to ensure that it doesn't break anything.

If only it were so simple with Vista.  I always have to do a clean install as Vista always screws it up.

---

### Post by stchman on 2008-03-17
> **caljohnsmith said:**
> I downloaded and installed Ubuntu 7.10 yesterday on my PC on a partition on my HD that all ready has Win XP on another partition, and it is up-and-running just fine after a bit of work. 

After getting my wireless card working with Ubuntu and my router, I loaded up Firefox, and immediately notice that it is 2.0.0.6, not the latest 2.0.0.12. So after researching a little about adding/removing programs in Ubuntu, I found in the threads here:

[http://ubuntuforums.org/showthread.php?t=716928](http://ubuntuforums.org/showthread.php?t=716928)

Is there some reason why I have to use a special installer, i.e. Ubuntuzilla, for Firefox? Is there any way I can just download the version of firefox from mozilla.com, uninstall the old version, and install the new version with the Ubuntu add/remove programs app? 

What I'm getting at, can someone point me to a really good tutorial on simply installing/removing programs in Ubuntu? I was hoping it might be as straightforward as Windows where you download the program you want to install from the web and simply install it with its installer app. Then when you want to remove it, you use the "add/remove programs". 

Thanks for your patience and any help! :)

Just let Ubuntu update itself.  If you have an internet connection then Ubuntu will let you know there are updates.

---

### Post by KCormier on 2008-03-17
As everyone said, go in and update your list of sources (through the gui manager).  Then either run update manager if you prefer the gui, or open up a terminal and then
```

sudo apt-get update;
sudo apt-get upgrade [-qqy]; *look for comment below

```
* -qq will run it in super quiet mode where you don't see the list of everything going by.  It'll still show errors and necessary information, just not download status and that sort of stuff
-y will automatically answer yes to any prompts asking if you want to install this or that.  I find it's more convenient when i've been messing with the latest alphas for ubuntu.  with 400+ updates in just a week or two (thank god for the busy ubuntu developers!) the -qq and -y options are wonderful.  -qqy is just combining the two btw.

Anyways, asside from the qqy option most of that has been already said.  My real reason for posting was to make a note of why your sources.list has most of the sources commented out.  On default, when ubuntu is installed it tries to make a connection to each update server, and each server it finds unavailable, it comments out so that it never tries to connect again.  What happens if you don't have an internet connection?  Well...now you see.  I see what they're trying to do, but I think it would be much smarter if they first checked for an internet connection, then if the connection existed but servers weren't assesable, it might be a good idea to comment out that server...   Even then though, the server might just be down temporarily.  I guess that's one i should take up with the developers thought, huh?  lol.  Good luck w/ ubuntu and enjoy :)  It's a slight learning curve but it really is wonderful once you get used to it!

-Kevin

---

### Post by philinux on 2008-03-17
Ubuntu has it's own compiled version of firefox so when the updates, security or otherwise, come through they are only few days after the mozilla release.

The current version in the repo's is 2.0.0.12.

Version 3 is just around the corner.

---

### Post by caljohnsmith on 2008-03-17
Thanks so much for all of your replies, everyone; I did get Firefox 2.0.0.12 successfully installed. As suggested, I went into the Software Sources program and enabled download of most everything, and then I used the Update Manager to download all of the updates instead of doing it from the command line. :-D

---

