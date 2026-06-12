---
title: "Firefox install won't work"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by waste301 on 2008-04-11
I'va had great problems with firefox, and am trying to reinstall it.

I install it with add remove and get a pop-up error saying:

Failed to execute child process "firefox" (Too many levels of symbolic links)

---

### Post by mohnkern on 2008-04-11
How are you trying to install it?

Try from the command line:

sudo apt-get install firefox

---

### Post by waste301 on 2008-04-11
> **mohnkern said:**
> How are you trying to install it?

Try from the command line:

sudo apt-get install firefox

sudo apt-get install firefox
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  wamerican openoffice.org-l10n-common openoffice.org-thesaurus-en-us
  myspell-en-gb myspell-en-us myspell-en-za openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za wbritish openoffice.org-help-en-us
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


It still won't run - same message.

---

### Post by Het Irv on 2008-04-11
Try removing all the Firefox files and settings with```
sudo apt-get purge firefox
```
Then try reinstalling Firefox with ```
sudo apt-get install firefox
```

---

### Post by waste301 on 2008-04-11
> **Het Irv said:**
> Try removing all the Firefox files and settings with```
sudo apt-get purge firefox
```
Then try reinstalling Firefox with ```
sudo apt-get install firefox
```

sudo apt-get purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wamerican openoffice.org-l10n-common openoffice.org-thesaurus-en-us
  myspell-en-gb myspell-en-us myspell-en-za openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za wbritish openoffice.org-help-en-us
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 26.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 143326 files and directories currently installed.)
Removing firefox ...
Purging configuration files for firefox ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
matt@mattspc:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wamerican openoffice.org-l10n-common openoffice.org-thesaurus-en-us
  myspell-en-gb myspell-en-us myspell-en-za openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za wbritish openoffice.org-help-en-us
Use 'apt-get autoremove' to remove them.
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/9197kB of archives.
After unpacking 26.7MB of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 142824 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Setting up firefox (2.0.0.13+1nobinonly-0ubuntu0.7.10) ...
Please restart any running Firefoxes, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

No luck I'm afraid - clciking the Firefox link at the top of my destop still says:

could not lauch application

Failed to execute child process "firefox" (Too many levels of symbolic links)

---

### Post by fraser35 on 2008-04-11
hi,
noob here so bear with me, I''ve just installed Hardy and its great but Firefox runs for 10 mins then crashes, tried doing all the updates but the issue remains....any pointer?---(keeping in mind that I'm a noob---plz keep it simple lol)

---

### Post by tango_ninja on 2008-04-11
@ fraser35,  go to the Absolute Beginner Talk and click on **Make New Post** in the upper left-hand corner. This will enable the community to focus specifically on one problem per thread. :)

@ waste301, If i am correct, **too many symbolic links** refers to either a linking loop, or 8+ links from launcher to actual file launched (in this case, the firefox link on your desktop). Can someone confirm this?

Have you tried launching firefox from Terminal instead of desktop GUI? If not, try it and see how you fare....

---

### Post by waste301 on 2008-04-11
bump - ignore threadjacker please

---

### Post by waste301 on 2008-04-11
> **tango_ninja said:**
> @ fraser35,  go to the Absolute Beginner Talk and click on **Make New Post** in the upper left-hand corner. This will enable the community to focus specifically on one problem per thread. :)

@ waste301, If i am correct, **too many symbolic links** refers to either a linking loop, or 8+ links from launcher to actual file launched (in this case, the firefox link on your desktop). Can someone confirm this?

Have you tried launching firefox from Terminal instead of desktop GUI? If not, try it and see how you fare....

matt@mattspc:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found

Still no luck.  I've never seen "symbolic links" before.  If anyone knows how to delete these links or what they are please help.

---

### Post by tango_ninja on 2008-04-11
hehe not installed? yikes :)

try:
```
sudo apt-get autoremove firefox
sudo apt-get purge firefox
sudo apt-get install firefox
```

then run:
```
firefox
```

I know you already tried the ol' uninstall - reinstall trick but from your terminal start it seems that somehow firefox isn't installed....

---

### Post by Het Irv on 2008-04-11
Tango_Ninja has something I missed.  After you get Firefox installed, try recreating your desktop icon.

---

### Post by dca on 2008-04-11
...you know I may be out of line here, but if after running 'purge' on apt-get to remove firefox completely you may try d/l the new beta version (3.0+ that ships w/ Ubuntu beta) direct from 'www.getfirefox.com' and make sure it's the tar-balled one for Linux.  Extract it, move it to the /opt directory and follow the remaining steps from their website....

---

### Post by waste301 on 2008-04-11
> **tango_ninja said:**
> hehe not installed? yikes :)

try:
```
sudo apt-get autoremove firefox
sudo apt-get purge firefox
sudo apt-get install firefox
```

then run:
```
firefox
```

I know you already tried the ol' uninstall - reinstall trick but from your terminal start it seems that somehow firefox isn't installed....

matt@mattspc:~$ sudo apt-get autoremove firefox
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wamerican openoffice.org-l10n-common openoffice.org-thesaurus-en-us
  myspell-en-gb myspell-en-us myspell-en-za openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za wbritish openoffice.org-help-en-us
The following packages will be REMOVED:
  firefox myspell-en-gb myspell-en-us myspell-en-za openoffice.org-help-en-us
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-thesaurus-en-us wamerican wbritish
0 upgraded, 0 newly installed, 11 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 92.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 143326 files and directories currently installed.)
Removing firefox ...
Removing myspell-en-gb ...
Updating OpenOffice.org's dictionary list... done.
Removing myspell-en-us ...
Updating OpenOffice.org's dictionary list... done.
Removing myspell-en-za ...
Updating OpenOffice.org's dictionary list... done.
Removing openoffice.org-help-en-us ...
Removing openoffice.org-l10n-en-za ...
Removing openoffice.org-l10n-en-gb ...
Removing openoffice.org-l10n-common ...
Removing openoffice.org-thesaurus-en-us ...
Updating OpenOffice.org's dictionary list... done.
Removing wamerican ...
Removing wbritish ...
/usr/sbin/update-default-wordlist No wordlist elements installed.
/usr/sbin/update-default-wordlist No wordlist elements installed.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
matt@mattspc:~$ sudo apt-get purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
matt@mattspc:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox-gnome-support latex-xft-fonts
Recommended packages:
  ubufox
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/9197kB of archives.
After unpacking 26.7MB of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 142047 files and directories currently installed.)
Unpacking firefox (from .../firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb) ...
Setting up firefox (2.0.0.13+1nobinonly-0ubuntu0.7.10) ...
Please restart any running Firefoxes, or you will experience problems.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
matt@mattspc:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found
matt@mattspc:~$ 


That is what happend.  Clicking the FF icon in next to "system" still causes:

Failed to execute child process "firefox" (Too many levels of symbolic links)

---

### Post by dca on 2008-04-11
...I mean one small caveat, make sure you do it as a last resort and that the old vers is completely removed.  Don't know if the /usr/lib directories need to remain for the 'plugins' (flash, etc) to work...

---

### Post by waste301 on 2008-04-11
> **dca said:**
> ...you know I may be out of line here, but if after running 'purge' on apt-get to remove firefox completely you may try d/l the new beta version (3.0+ that ships w/ Ubuntu beta) direct from 'www.getfirefox.com' and make sure it's the tar-balled one for Linux.  Extract it, move it to the /opt directory and follow the remaining steps from their website....

> **Het Irv said:**
> Tango_Ninja has something I missed.  After you get Firefox installed, try recreating your desktop icon.

How?

I would be willing to reinstall ubuntu, if it is deemed necassry and would not destroy all data that I have on the drive - I do need a working firefox if that is what it takes.

I really think that the problem has to do with "symbollic links" if anyone knows anything about them.

---

### Post by tango_ninja on 2008-04-11
ever thought of using a different browser, like epiphany ?:)
I know, that's not the point. 

Symbolic links would be a completely anticipated error when launching from the launcher (shortcut). but when launching in terminal, and getting the message *firefox not installed* i think it may be more than that.... either way, i'm out of suggestions, i hope someone else on the forum has some insight.

Here is a post from another thread in which the user actualy reinstalled the OS for firefox to work:

> **bigbrownbear said:**
> Thanks all for the suggestions, problem is solved, firefox is launched and I am online. 
For those that have the same problem, I will explain. I went into terminal and wrote several commands (actually everyone I could think of) including: firefox google.com (nothing), gksudo firefox (nothing), Alt+F2, firefox safe-mode (nothing) and eventually gksudo apt-get install firefox browser (E: couldn't find package browser)- even though it was said by the package manager to be fully installed! 

Before jumping off something high, I decided to re-install the whole OS, but using the disc from Canonical; the originally installed disc was a copy purchased from linux specialists OSDisc.com. Both were 7.04, none were Beta version. Install went flawlessly, and Bingo, firefox arrived along with help files which were also missing on the original install. 

I am not going to flame OSDisc, there may have been a problem with my disc's media, or with the copying process particular to the disc I was sent, though I will make a bug report to them in case it's rectifiable. Also their customer service and delivery is first rate.  But for anyone who has taken the same route as me and found the same problem, it may be better to re-instal with a Canonical disc.  Good luck.  

---

### Post by waste301 on 2008-04-11
> **tango_ninja said:**
> ever thought of using a different browser, like epiphany ?:)
I know, that's not the point. 

Symbolic links would be a completely anticipated error when launching from the launcher (shortcut). but when launching in terminal, and getting the message *firefox not installed* i think it may be more than that.... either way, i'm out of suggestions, i hope someone else on the forum has some insight.

Here is a post from another thread in which the user actualy reinstalled the OS for firefox to work:

OK - if the problem is unsovable I can deal with that.  I've backed up my bookmarks online and can re-install ubuntu.  Will that erase data on my current installation?  Music etc?  Also - if I am going to do that then a link to the newest, most stable LiveCD would be appreciated.

---

### Post by Het Irv on 2008-04-11
Yes it will erase your data, but you can use QuickStart (see sig) to back-up of your /home.  You can then move the data to an external source.

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) (a link to the latest stable version)
[www.ubuntu.com](www.ubuntu.com)   (use this link if you want the beta version of 8.04, to be released in 2 weeks)

---

### Post by stchman on 2008-04-11
> **waste301 said:**
> I'va had great problems with firefox, and am trying to reinstall it.

I install it with add remove and get a pop-up error saying:

Failed to execute child process "firefox" (Too many levels of symbolic links)

If you are running Ubuntu Firefox is installed by default.

Kubuntu you have to install it.

```
sudo apt-get install firefox
```

---

### Post by tango_ninja on 2008-04-11
you will lose data definitely, it will rewrite your partition.

do you have a burner or external drive? you should be to backup most things...

---

