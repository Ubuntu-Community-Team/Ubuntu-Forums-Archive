---
title: "How do you upgrade to firefox 2.0 in dapper?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by kevinlang21 on 2006-12-24
I went to the mozilla site and downloaded firefox 2.0.0.1.tar.gz. Now what? I looked online but i couldn't understand anything.

---

### Post by MkfIbK7a on 2006-12-24
do you have synaptic? or adept? or automatix?

---

### Post by Sef on 2006-12-24
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by kevinlang21 on 2006-12-24
I finished building my computer  today and i just finished installing the os 2 hours ago, so i have all of the default stuff. (yes to synaptic and adept) i don't think i have automatix

---

### Post by kevinlang21 on 2006-12-24
Thanks

---

### Post by kevinlang21 on 2006-12-24
I stopped understanding at the configure part

---

### Post by Sef on 2006-12-24
> When you're in the correct directory you execute a configure script: ./configure.

You may need to change directories.  If you downloaded to your desktop, then you need to change to there.

Example: 

> sef@jokat1:~$ cd ~/Desktop
sef@jokat1:~/Desktop$

---

### Post by kevinlang21 on 2006-12-24
I downloaded it into apps, and i can get into apps on my terminal, but i don't understand what i'm supposed to do after that. Am i supposed to type "./configure" by itself?

---

### Post by MkfIbK7a on 2006-12-24
yup

---

### Post by kevinlang21 on 2006-12-24
It says > bash: ./configure: no such file or directoryno such file or directory

---

### Post by MkfIbK7a on 2006-12-24
go to synaptic and search firefox check the boxes that you need and you got it!

---

### Post by kevinlang21 on 2006-12-24
Sorry for my stupidity, but isn't that firefox 1.5?

---

### Post by Sef on 2006-12-24
> Sorry for my stupidity, but isn't that firefox 1.5?

If you are using Dapper, yes.  So you're not so stupid.  Upgrades in applications in Dapper will be slow in coming since it is the stable version they don't want to introduce any problems by introducing new applications or other software.

---

### Post by MkfIbK7a on 2006-12-24
in other words you cant get firefox 2.0 in dapper?

you mean its not in the repos?

---

### Post by David Corrales on 2006-12-24
To the OP, the way I did it was to simply untar the file inside my home directory so it looks like /home/user/firefox, and then changed my preferred browser pointing to it.
Some might say that's unsecure, but in reality, if your regular firefox was breached, it'd have the same permissions you do, so it'd be similar.
For the plugins, after untarring I removed the plugins folder and created a symlink to the system one.

---

### Post by kevinlang21 on 2006-12-24
ok then. thanks guys.

---

### Post by Sef on 2006-12-24
> ok then. thanks guys.

You're welcome.   If you have any more questions, please post them.

---

### Post by obsidion on 2006-12-24
> **kevinlang21 said:**
> I went to the mozilla site and downloaded firefox 2.0.0.1.tar.gz. Now what? I looked online but i couldn't understand anything.

Log in to a terminal either bring one on your desktop or log into a tty.
Using a desktop one will be better that way you can refer back here.
Now go to the directory you downloaded the file to. You will be in your home directory when you open the terminal. Now type ls and see if the file shows up. If it does copy it to a universal directory like /usr/share/
type sudo cp firefox (hit tab it will autocomplete the name) /usr/share/ enter. Note there is a space between the end of the file name and the /usr. Note the password is your first user one, make sure you are logging in as that user.
Now cd /usr/share
then sudo tar zvxf firefox hit tab again and enter.
This will install firefox to its own directory in /usr/share

To make sure this has happened

ls and make sure there is a firefox directory, directories appear in a different colour from files.

 Now cd /usr/bin
there you need to set up a symlink and over write the default firefox one. The easiest way is to sudo rm firefox.

Now sudo ln -s /usr/share/firefox/firefox  enter note the first letter after the sudo is a small L

 The /usr/share/firefox/firefox is assuming that that is the directory vreated. If its another naem eg firefox2 or something make sure you use that in making the symlink.


You can now activate the new firefox from either the menu entry as we have hopefully delted the old symlink or by alt-F2 and typing firefox in the box. You can create and icon on the desktop as well should you want to.
Go to the help about box when firefox lauches to make sure it is the new one. Note if you have installed a lot of extensions there could be some probelms loading if they are incompatible with the new version.

---

### Post by Sef on 2006-12-24
> in other words you cant get firefox 2.0 in dapper?

you mean its not in the repos?

Yes, that is correct at this time.

---

### Post by flyingbrass on 2006-12-24
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by kevinlang21 on 2006-12-25
Got It!!!:d :d :d

---

### Post by saphil on 2006-12-25
firefox2.0.0.1 download does not have a configure file in it... 
I just did this download..  
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.1](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.1)

source is at
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.1/source](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.1/source)
I am going to look at that...  source is over 35MB... and it is taking a ridiculous amount of time to decompress the file into /tmp...

Now I am going to do the ./configure  .. it failed
Mozilla says (WAEFRTFM) "
> Though it is possible to manually call configure with command-line options, this is not recommended. Instead, place a .mozconfig file in your source directory (mozilla/.mozconfig) or in your HOME directory (~/.mozconfig). 
You may also set the MOZCONFIG environment variable to the full path of your configuration file: 
 export MOZCONFIG=~/mozilla/mozconfig-firefox

.mozconfig contains two types of options:[LIST]
[*] Options prefixed with mk_add_options are passed to client.mk, and are usually options controlling cvs checkout and update.
[*] Options prefixed with ac_add_options are passed to configure, and affect the build process.[/LIST]These options will be automatically used when ./configure or make -f client.mk are run.
Yes, this is going waaaay beyond what I had hoped to be doing on Christmas day.  It is 10:00  I am clocking out for the day.

At the last minute I saw AYSiu's script, which ran beautifully, however I do not know where it put the 2.0.0.1 version, both links (firefox and firefox.ubuntu) in /usr/bin are to 1.5.x....

Retraction... I had a firefox window open on desktop 2, so all my attempts to start the new firefox were just pulling from the 1.5 version that was STILL RUNNING.  lol  I am definitely clocking out now.  There is a Guinness waiting with my name on it.

Happy Christmas

---

### Post by daktari on 2007-02-02
Is there a target date for repo-ing firefox 2.x - at least for Dapper LTS**?**

---

### Post by kinson on 2008-01-13
I found a simple way to sort this out (I upgraded from Dapper to Gutsy, but preferred Dapper, so I'm back to Dapper with Firefox 1.5).

I went to [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and followed the link to download UbuntuZilla at: [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Followed the instructions to install and run UbuntuZilla for firefox, and it worked like a charm. I didn't even know what was happening, lol !! :D

Cheers,
Kinson

---

### Post by kinson on 2008-01-13
You should try using UbuntuZilla, its very simple (read the installation and usage instructions though !!), and automated :)

[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Cheers,
Kinson

---

