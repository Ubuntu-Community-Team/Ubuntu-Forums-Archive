---
title: "root user, permission denied after installing GeoGebra"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by sonhadorpr on 2007-10-15
Dear Ubunteros.

I have been here a few months now, and I have learned a lot from the posts, on how to use and fine-tune my Ubuntu machine.

And on this learning voyage, and after spending many hours in front of the PC, I have done something that I think I Messed-up my Ubuntu machine at college.
This is what I did.  

I installed a new program that some users asked me about, since they use it on Windows, to be able to use it on the Ubuntu, it's called GeoGebra, and it runs on many platforms.

Right after the DL and installation of the GeoGebra for Linux, I try to run Mozilla FireFox to find some info on how to use the program, and the system tells me that I don't have sufficient privileges to run FireFox, from the GDE.  I find this odd, and I'm thinking maybe somehow I eliminated super user privileges to my user....so I decide to re-boot the machine, and log in as root.  When I turn the machine on, a crap-load of error msgs come on screen, and it NEVER gets to the login screen for a GUI login, as GDE or KDE(since I installed Kubuntu on top of Ubuntu), ...

Here's a list of the error msgs that come up as I boot up.  (Apparently they scroll so fast, that I can't see all of them, and here's all I was able to type up):

...done.

* Starting NFS common utilities

...done.

/etc/rc2.d/S23ntp: 31: getent: Permission denied

/etc/rc2.d/S23ntp: 31: cut: Permission denied

* Starting NTP server ntpd

* user "ntp" does not exist

/etc/init.d/alsa-utils: Error: No amixer program available.

* Setting disc parameters...

...done.

* Starting anac(h)ronistic cron anacron

...don.

* Starting deferred execution scheduler atd

...done.

* Starting periodic command scheduler crond

...done.

* Enabling additional executable binary formats binfmt-support

/etc/rc2.d/S90binfmt-support: 50: update-binfmts: Permission denied

...fail!

/etc/rc2.d/S98usplash: 82: clear: Permission denied

* Checking battery state...

...done.

* Running local boot scripts (/etc/rc.local)

...done.

This is all it does, and it doesn't do anything else.
so I switch to tty4 doing CTRL+ALT+F4.
When I log in as user root on tty4, I get this other error msg, right after the part where it says that Ubuntu comes AS-IS, yadda, yadda...
it gives me Permission denied in the following areas:

-bash: /usr/bin/groups: Permission denied

-bash: /usr/bin/dircolors: Permission denied

-bash: /usr/bin/mesg: Permission denied

All this just seems very odd....when I try to run ANY command, like:

sudo, telnet, ssh, ftp, finger, clear, apt-get install .... anything from root, it tells me Permission denied
The only thing I was able to do is:  mkdir, and change dirs from one side of the system to the other using cd, and also see the dirs using ls...that's it!   Everything else, is Permission denied.

So, What am I thinking??? Somebody hacked my machine at the U!!!????

I do not know...all I know is that the machine was working fine right before installing the GeoGebra, and now it isn't.

So now, none of the users in my machine can login in the GUI, just the shell...and still..they can't do anything!

So I humbly ask my very Wise Ubunteros....
Besides sacrificing all the hours of hard work and etc, etc....by re-installing the entire OS from zero......is there any way to correct this problem?
Any suggestions?

Like I said, everything seems very odd.
Thank you in advanced for all of your help, suggestions, and comments on resolving this matter.

Greetings from Puerto Rico

ROM

---

### Post by dwhitney67 on 2007-10-15
Are you able to verify root's PATH environment variable?  Try to see if you are able to run:

# echo $PATH

Verify if /usr/bin is in the results.  If it is not, then temporarily add it using this statement:

# export PATH=$PATH:/usr/bin

From there, hopefully the anomaly within your system can be tracked down.

P.S.  It is a shame that Greetings from 'La Isla Del Encanto' is accompanied by vulgar words in your post.

---

### Post by sonhadorpr on 2007-10-15
You are absolutely correct!
I am ashamed...
I'm sorry.....I will re-edit the post now.
Thank you for telling me that.
ROM

---

### Post by sonhadorpr on 2007-10-16
Editing of the first post done!
I will follow your instructions tomorrow at the U...since I'm at home right now.
Thank you again!
ROM

---

### Post by sonhadorpr on 2007-10-16
This is what I get when following your instructions.

I am able to login as root, still giving me the same Permission denied msgs...
I write the command you gave me
echo $PATH
and this is what I get:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

/usr/bin is in the results...
what do I do with that info?
Step-by-step instructions will be appreciated.
Thanx for your help.
ROM

---

### Post by twiceasworn on 2007-10-16
When it is giving you the permissions errors, is it saying (Permissiong Denied:  Read-Only Filesystem)?

Also could you post the output of 

```
cat /var/log/messages
```

and 

```
cat /var/log/dmesg
```?

---

### Post by dwhitney67 on 2007-10-16
Also do a quick inspection of the permissions set on the files in /usr/bin.  For the most part, all of the files should have root:root ownership and -rwx-r-xr-x permissions.  For example, for /usr/bin/mesg:

[FONT="Courier New"]-rwxr-xr-x 1 root   root       4308 2007-04-10 14:45 mesg[/FONT]

---

### Post by haldean on 2007-10-16
It could be that your UIDs are messed up, or that some users were deleted. Check /etc/passwd to see if root, daemon, bin and sys all exist - the first few lines of /etc/passwd should look like so:

```
$> cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh

```

at least that's what it looks like on Fiesty... it might look slighty different on other versions, but those users all need to be there and root must have UID 0. The line for the root user should look like the first line above.

---

### Post by sonhadorpr on 2007-10-16
It only says Permission Denied, _NOT_ Read-only filesystem.
However, I'm growing increasingly frustrated and have decided to do a clean install again..
however, when I tried to do this, the system detected that the 40GB HDD had some space, and recommended me to use a 25.1GB partition to run the new install....I'm hoping I am able to access all the other info on the rest of the HDD.
Funny thing is, I put in a Gentoo Live CD and it didn't read that partition, it only offered to do a 4GB partition for swap, and use the rest of the $) for /hda1....SO, I'm gambling on the Ubuntu, who did see this partition, and let's see what happenes after it finishes...
I'll keep you guys posted..
Thank you all for your help.

ROM

---

### Post by sonhadorpr on 2007-10-16
I gambled on the newer install of Ubuntu, and it worked.
It reads the other file system, and I have access to all the files, so now I'm running one machine with 2 Ubuntus...however, when the machine boots up and I choose the other Kernel, for the older Ubuntu SO that was there earlier, it still gives me problems....
I need to go ahead and follow the instructions and suggestions other users have given me..
IF NOT...I rather just leave it alone, the way it's running now, and use the other system as back-up...it just bothers me that I have to re-install all the programs I use most.  NO GeoGebra this time!!!

I'll keep you guys posted.
Thanx.

ROM

---

### Post by dwhitney67 on 2007-10-16
I don't know jack about GeoGebra, but with most 3rd-party software packages, you should be able to install it into a user (non-root) area.  If you want to share it with others on the system, then you would need to install it in an area accessible by each user... but once again, this area does not have to be directly within the root-tree of the system.  Needless to say, most 3rd-party apps are generally installed in /opt.

---

### Post by sonhadorpr on 2007-10-16
Dear Whitney67:
Most of the files on /usr/bin are owned by root, but the protection it has is different than the one you wrote.
This is what I have:

-rw-r--r--   1 root     root          4308 2007-08-09 06:00 mesg
another file reads:
lrwxrwxrwx  1  root     root            7 2007-09-17 16:06 makempy -> texexec

one file reads:
-rw-r--r-- 1  daemon     daemon         38464 2007-08-09 06:00 at

Some other files have a different set of protection attached to them:

drwxr-xr-x     5 root     root             4096 2007-10-11 17:42 docubs all the way to docuzh some change numbers from 1, 2, 5, 6

This is all I can see in this screen.

---

### Post by sonhadorpr on 2007-10-16
hey twiceasworn:
if I run these commands, many things come up on screen, I don't think I am able to remember them all, since they came up really fast!! how can I copy and paste them?
I'm on shell, and the copy and/or paste commands don't work.

---

### Post by sonhadorpr on 2007-10-16
> **haldean said:**
> It could be that your UIDs are messed up, or that some users were deleted. Check /etc/passwd to see if root, daemon, bin and sys all exist - the first few lines of /etc/passwd should look like so:

```
$> cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh

```

at least that's what it looks like on Fiesty... it might look slighty different on other versions, but those users all need to be there and root must have UID 0. The line for the root user should look like the first line above.
Dear haldean, I was able to follow the command you gave me, and all the users are where they are supposed to be, exactly as you wrote them in.
Any other suggestions?

Thanx.
ROM

---

### Post by dwhitney67 on 2007-10-16
> **sonhadorpr said:**
> Dear Whitney67:
Most of the files on /usr/bin are owned by root, but the protection it has is different than the one you wrote.
This is what I have:

-rw-r--r--   1 root     root          4308 2007-08-09 06:00 mesg
another file reads:
lrwxrwxrwx  1  root     root            7 2007-09-17 16:06 makempy -> texexec

one file reads:
-rw-r--r-- 1  daemon     daemon         38464 2007-08-09 06:00 at

Some other files have a different set of protection attached to them:

drwxr-xr-x     5 root     root             4096 2007-10-11 17:42 docubs all the way to docuzh some change numbers from 1, 2, 5, 6

This is all I can see in this screen.
Well that appears to be the problem.  I would run this command on your files in /usr/bin:

$ sudo find /usr/bin -type f -exec chmod 755 {} \;

This command will change every file in /usr/bin (skipping links and dirs) to have the correct permissions.  Hopefully your system will be stylin' after that.

---

### Post by sonhadorpr on 2007-10-16
Well, thank you, I couldn't use sudo either, but I managed to use chmod, and grant access to /usr/bin/  with the help of a professor, from the math department.

Thank you.

ROM

---

### Post by dwhitney67 on 2007-10-16
Great!  Have you tried to reboot to see if the system is "happy"?

---

### Post by sonhadorpr on 2007-10-17
it doesn't let me use sudo
I'm gonna be working on that.
The site admin from GeoGebra contacted me, after I posted a bug report.
He wants me to do it again, and replicate the problem.
I really don't want to do it, because fixing the problem is a major pain, at least for a newbie like me.

If anybody wants to go ahead and install GeoGebra from their site [www.geogebra.org/](www.geogebra.org/)  and report any problems you might encounter, or not.
Make sure you choose to DL the geogebra*.bin file, from the 2 options, There's a web install, and DL the actual file.  Make sure you have JRE, and make sure you know which version of the JRE you are using, he asked me all these questions, and I couldn't answer...I told him...the one that is in the repositories, and the isntaller from your site, and I use Ubuntu 7.04 latest stable edition.

I'll gladly appreciate it.

Make sure you let me know how it turns out.

ROM

---

### Post by sonhadorpr on 2007-10-17
If anybody is interested in replicating the problem:

Go to [www.geogebra.org/](www.geogebra.org/)
on the address bar on top you will see that is says [http://www.geogebra.org/cms](http://www.geogebra.org/cms)

On the left hand side you will see a couple of links:

Home
About
WebStart
Download
Help
Screenshots
Examples
Future
Credits
Contact
Support GeoGebra!

Go to Download, you will now find yourself in
[http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=71&Itemid=55](http://www.geogebra.org/cms/index.php?option=com_content&task=blogcategory&id=71&Itemid=55)

I did not use the GeoGebra Web Start, don't know why...maybe this is the problem...I have no idea.

You will see these 2 links:

    *GeoGebra WebStart
    *Download GeoGebra

Select the second one, DL GeoGebra:

You will now find yourself in this page:

[http://www.geogebra.org/download/install.htm](http://www.geogebra.org/download/install.htm)

At the top, you will see a java link, that says:
Recommended Installation for Your Platform.

Don't click on that!
Go down to the 4 options starting with Windows, Mac OS X, Linux, and other Java-enabled platforms

You will see a green > arrow, the picture of Tux, and the Word Linux in green.
Click there. 
It will send you this file:

GeoGebra_3_0_0_0_Release_Candidate_1.bin

Save it where ever you want..
and FOLLOW the instructions given to you by the GeoGebra website, for installation of the program, after the DL finishes.

The instructions are on that same page, just scroll down.

This is what I did!!

If anybody tells me that they got the exact same problem, then, there really is a problem with the installer, IF NOT...
then I'm the idiot who granted root access to the program, the program went into hack mode, and did this all on its own.

Thank you again, guys, for all your help.

ROM

---

### Post by Yves Kreis on 2007-10-17
Dear,

The installer of GeoGebra has been created by myself and I was pointed here by sonhadorpr who seems to have encountered problems (which I could not reproduce so far).

The installer has been tested extensively on Debian by myself and on other Linux flavors by others and noone encountered such problems. By default the installer chooses ~/geogebra as installation folder and /opt/geogebra if the user has root permissions. It puts a shortcut into ~/bin by default and into /usr/bin if the user has root permissions.

I would be pleased if someone could try the installer from [http://www.geogebra.org/download/](http://www.geogebra.org/download/) and tell me if there is really something wrong. I will try myself to install Ubuntu on a machine tomorrow and test it myself, but I am neither a Linux export nor an Ubuntu user...

Best Regards,
Yves

---

### Post by Yves Kreis on 2007-10-20
I installed Ubuntu 7.10 on a test machine today... 

Some conclusions: 
* gij shows the full version as: java full version "gcj-1.5.0" 
* sun-java5-jre shows the full version as: java full version "1.5.0_13-b05" 
* sun-java6-jre shows the full version as: java full version "1.6.0_03-b05" 
The gij is thus not recognized by the release candidate 1 but might (its not the major priority) be recognized by a newer one. 

I tested the release candidate 1 installer with both java versions of sun. I could still not reproduce the problems and I am now closing this issue until someone else can reproduce it. 

Best Regards, 
Yves

---

### Post by sonhadorpr on 2007-10-20
Thank you Yves, for your time and effort.
I have been very busy at the university with my classes, and have not had the time, to re-do the installation the exact way I had done it before, so I cannot tell you that the problem came up again.
I sahll try it later, but however, you posted that you tried it on Ubuntu 7.10, my problem came on Ubuntu 7.04...I don't see why THAT should be a problem, however, you didn't use the same OS I did.

Like I said, I'll keep you posted if it comes up again....again..thank you for your interes in this problem.

ROM

---

### Post by Yves Kreis on 2007-10-20
Dear ROM,

I have been testing the installer on Debian for some months now and Ubuntu is Debian based. So I don't see what the difference in Ubuntu 7.04 and 7.10 could be... and the default download was 7.10, so I chose that one (and I didn't see a 7.04 download). However I tested the installer on a 7.04 VMware virtual machine and couldn't reproduce the problem either.

Best Regards,
Yves

---

### Post by sonhadorpr on 2007-10-20
Well, like I said, maybe I messed up somewhere along the lines of installation, and messed up the OS...somehow.
I guess I'll never really know.
Thank you for all your help.

ROM

---

