---
title: "How to install thunderbird 1.5.0.2"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by maspiotis on 2006-04-24
I am a total noob, and am trying to install thunderbird.  It seems like the instructions posted on the Ubuntu wiki assume that I know much more than I do.  Is there a simple step by step way I can install Tbird, maybe with apt-get.  I downloaded Tbird to a temporary file and was able to extract it, but after that I am clueless as how to proceed.  Any help would be appreciated, though keep in mind referring me to Mozilla's instructions or the how to on the wiki won't be enough.  I have been there and am too much of a noob to know what they are talking about.  

Thanks,
Michael

---

### Post by aysiu on 2006-04-25
If you apt-get, you're going to get version 1.0.7: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

If you want 1.5.0.2, download [this script](http://www.ubuntuforums.org/showpost.php?p=950010&postcount=21) to your desktop and then go to a terminal and copy and paste these commands: ```
cd ~/Desktop
mv installnewthunderbird.sh.txt installnewthunderbird
chmod +x installnewthunderbird
./installnewthunderbird
```

---

### Post by maspiotis on 2006-04-25
Thanks, but I am still having a problem.

 I followed your instructions, which I will explain step by step for all the other noobs out there who are trying to do all this stuff for the first time.

First, I clicked on the link you provided for thunderbird 1.5.0.2 "this script" from there I downloaded the script by clicking on the link: installnewthunderbird.sh.txt (1.1 KB, 
then I opened it, then I went to the file menu of my text editor and clicked saved as and saved the script to my desktop.  Then I copied the command in your post, opened a terminal (applications menu, click accessories, click terminal) then pasted the command in the terminal.

Everything seemed to work, I went to the applications menu, and under internet there are the icons for thunderbird. However it does not want to open, I restarted the computer but It still won't open, I have breezy badger by the way.

Thanks very much for your help.
Michael

---

### Post by aysiu on 2006-04-25
That's weird.

Can you go back to a terminal and copy and paste these commands in? ```
cd /opt/thunderbird
./thunderbird
``` and then post back whatever output comes out...?

---

### Post by maspiotis on 2006-04-26
This is what I get


maspiotis@michaelsrobot:~$ cd /opt/thunderbird
maspiotis@michaelsrobot:/opt/thunderbird$ ./thunderbird
maspiotis@michaelsrobot:/opt/thunderbird$
maspiotis@michaelsrobot:/opt/thunderbird$

thanks for your help

---

### Post by aysiu on 2006-04-26
That's odd.

Maybe try this...? ```
cd /opt/thunderbird
sudo chmod +x thunderbird
./thunderbird
```

---

### Post by maspiotis on 2006-04-26
Tried that this is what I get:


maspiotis@michaelsrobot:~$ cd /opt/thunderbird
maspiotis@michaelsrobot:/opt/thunderbird$ sudo chmod +x thunderbird
maspiotis@michaelsrobot:/opt/thunderbird$ ./thunderbird

Thanks again,
Michael

---

### Post by aysiu on 2006-04-26
Hm.

I'm not sure what's wrong.

Last resort: ```
sudo apt-get update
sudo apt-get install --reinstall mozilla-thunderbird
mozilla-thunderbird
```

---

### Post by maspiotis on 2006-04-26
Ok, I tried that and this is what I get

maspiotis@michaelsrobot:~$ sudo apt-get install --reinstall mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 92 not upgraded.
Need to get 0B/10.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
maspiotis@michaelsrobot:~$ sudo apt-get install --reinstall mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 92 not upgraded.
Need to get 0B/10.4MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
maspiotis@michaelsrobot:~$

thanks again,
Michael

---

### Post by joshrobinson on 2006-04-26
could always just download it from the mozilla website, extract it wherever you want it.. say your home directory

then create a launcher to it on your desktop or your panel

---

### Post by aysiu on 2006-04-26
That *abort* looks bad. Unfortunately, I don't know what the problem is.

---

### Post by maspiotis on 2006-04-26
maspiotis@michaelsrobot:~$ cd ~/Desktop
maspiotis@michaelsrobot:~/Desktop$ mv installnewthunderbird.sh.txt installnewthunderbird
maspiotis@michaelsrobot:~/Desktop$ chmod +x installnewthunderbird
maspiotis@michaelsrobot:~/Desktop$ ./installnewthunderbird
Updating repositories list

Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done

Making sure libstdc++5 and the old Thunderbird are installed

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gcc-3.3-base
Suggested packages:
  mozilla-thunderbird-offline mozilla-thunderbird-typeaheadfind
  mozilla-thunderbird-inspector mozilla-thunderbird-enigmail
Recommended packages:
  xprt-xprintorg
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5 mozilla-thunderbird
0 upgraded, 3 newly installed, 0 to remove and 83 not upgraded.
Need to get 10.4MB/10.8MB of archives.
After unpacking 32.4MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main mozilla-thunderbird 1.0.7-0ubuntu05.10 [10.4MB]
Fetched 10.4MB in 25s (409kB/s)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.3-base.
(Reading database ... 56661 files and directories currently installed.)
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-8ubuntu1_i386.deb) ...
Selecting previously deselected package mozilla-thunderbird.
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.0.7-0ubuntu05.10_i386.deb) ...
Successful preinst
Setting up gcc-3.3-base (3.3.6-8ubuntu1) ...
Setting up libstdc++5 (3.3.6-8ubuntu1) ...

Setting up mozilla-thunderbird (1.0.7-0ubuntu05.10) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

done.


Backing up old Thunderbird preferences

cp: cannot stat `/home/maspiotis/.mozilla-thunderbird': No such file or directory

Creating symlink to new version data-dir ~/.thunderbird


Changing to home directory


Downloading Thunderbird from the Mozilla site

--13:07:06--  [http://mozilla.mirrors.tds.net/pub/mozilla.org/thunderbird/releases/1.5.0.2/linux-i686/en-US/thunderbird-1.5.0.2.tar.gz](http://mozilla.mirrors.tds.net/pub/mozilla.org/thunderbird/releases/1.5.0.2/linux-i686/en-US/thunderbird-1.5.0.2.tar.gz)
           => `thunderbird-1.5.0.2.tar.gz'
Resolving mozilla.mirrors.tds.net... 216.165.129.134
Connecting to mozilla.mirrors.tds.net|216.165.129.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,600,318 (10M) [application/x-gzip]

100%[====================================>] 10,600,318   519.69K/s    ETA 00:00

13:07:27 (505.33 KB/s) - `thunderbird-1.5.0.2.tar.gz' saved [10600318/10600318]


Unzipping the .tar.gz file

I thought I would try again by reinstalling Ubuntu, then following your instructions again, still I have the same problem.  I copied and pasted the goings on in the teminal to see if you could spot the problem.

Thanks,]
Michael


Removing the unzipped .tar.gz

rm: cannot remove `thunderbird-1.5.tar.gz': No such file or directory

Linking launcher to new Thunderbird

Adding `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'

The new Thunderbird is installed.
maspiotis@michaelsrobot:~/Desktop$

---

### Post by Just4 on 2006-04-26
Some of the errors in that script happened to me as well, I too am having the problem of not being able to launch Thunderbird.

---

### Post by ElijahLofgren on 2006-04-27
If you follow the instructions on [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion) it's really easy to get Thunderbird 1.5.0.2

Then you can launch Thunderbird by running (it is case sensitive):
thunderbird

(I just updated the page for Thunderbird 1.5.0.2)

Let me know if you have more problems. Please paste any errors you get in your post.

Hope this helps,

Elijah

---

### Post by maspiotis on 2006-04-29
Thanks for the reply, but, like I said in my original post, I am a total noob.  The following:    *

      Gunzip & untar the download and put it whereever you'd like the new version to reside. FirefoxNewVersion recommends /opt, where new static packages are often installed. It will work just as well sticking it in your home directory. For /opt:

sudo tar -C /opt -x -z -v -f thunderbird-1.5.0.2.tar.gz

    *

      To put it in your home direcory do basically the same thing, but change /opt/ to ~ and you can leave out the sudo's
    *

      Almost done - to be able switch off between running either the older package you might have installed and the new version, add a new symbolic link:

sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird

    *

      As the older version will be installed as /usr/bin/mozilla-thunderbird, this will allow you to run that one as mozilla-thunderbird and the new one with thunderbird. To avoid confusion or get rid of the old link altogether just do:

sudo mv /usr/bin/mozilla-thunderbird

Is a total foreign language to me, could you rewrite those instructions so even a rank novice like me could follow them,

Thanks,
Michael

---

### Post by ElijahLofgren on 2006-04-29
[QUOTE=maspiotis]
Is a total foreign language to me, could you rewrite those instructions so even a rank novice like me could follow them,

Thanks,
Michael[/QUOTE]

Sure, I'll get started re-writing [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion) right away. I'll post back once I think it's easier to understand and if you still have problems let me know. ;)

---

### Post by ElijahLofgren on 2006-04-29
I have tried to make the instructions easier to understand. Please check out the new instructions at:
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

Let me know if you have problems and I'll do the best I can to help. ;)

---

### Post by wyngdlyon on 2006-04-29
[QUOTE=ElijahLofgren]I have tried to make the instructions easier to understand. Please check out the new instructions at:
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

Let me know if you have problems and I'll do the best I can to help. ;)[/QUOTE]
I used the above instructions to install Thunderbird, but when I launch the program I get the following errors:

(thunderbird-bin:10418): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(thunderbird-bin:10418): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-ba sic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(thunderbird-bin:10418): Pango-CRITICAL **: _pango_engine_shape_shape: assertion  `PANGO_IS_FONT (font)' failed

Any help would be greatly appreciated. 

Thanks

---

### Post by ElijahLofgren on 2006-04-29
[QUOTE=wyngdlyon]I used the above instructions to install Thunderbird, but when I launch the program I get the following errors:

(thunderbird-bin:10418): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(thunderbird-bin:10418): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-ba sic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(thunderbird-bin:10418): Pango-CRITICAL **: _pango_engine_shape_shape: assertion  `PANGO_IS_FONT (font)' failed

Any help would be greatly appreciated. 
[/QUOTE]

If you're not using Ubuntu Dapper Drake then I would try upgrading to it. That's what I'm running right now and installing and running Thunderbird 1.5.0.2 worked great. See: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

---

### Post by wyngdlyon on 2006-04-30
[QUOTE=ElijahLofgren]If you're not using Ubuntu Dapper Drake then I would try upgrading to it. That's what I'm running right now and installing and running Thunderbird 1.5.0.2 worked great. See: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)[/QUOTE]


That worked perfectly ...thank you very much.

---

### Post by BaronofBB on 2006-04-30
[QUOTE=joshrobinson]could always just download it from the mozilla website, extract it wherever you want it.. say your home directory

then create a launcher to it on your desktop or your panel[/QUOTE]

Hello,
This is my first post here, and I use Thunderbird with Suse 10. I am trying Ubuntu as an alternative to Suse due to certain shortcomings.

However, I couldn't get Thunderbird to install here either. I followed this thread and did all that was recommended and got nowhere. It just refuses to launch.

All I can say is that on Suse, it takes one download, one extraction and two key clicks and it's up and running. It's the same file I'm using on both platforms, so why should one work with no effort at all, and one won't work at all?

---

### Post by ElijahLofgren on 2006-04-30
[QUOTE=BaronofBB]Hello,
This is my first post here, and I use Thunderbird with Suse 10. I am trying Ubuntu as an alternative to Suse due to certain shortcomings.

However, I couldn't get Thunderbird to install here either. I followed this thread and did all that was recommended and got nowhere. It just refuses to launch.

All I can say is that on Suse, it takes one download, one extraction and two key clicks and it's up and running. It's the same file I'm using on both platforms, so why should one work with no effort at all, and one won't work at all?[/QUOTE]

If you get an error message, could you paste that here? That will be useful in helping us find out what your problem is.

Sorry, it's not easily working for you. :-k Each distro has their various advantages and disadvantages, you just need to find the one that works best for you.

It could be that Thunderbird 1.5.0.2 will only work with Ubuntu Dapper Drake (I don't know. I haven't tried it on Breezy): See: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta) for more info.

Also, if you haven't take a look at: [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

Hope this helps. :)

---

### Post by aysiu on 2006-04-30
[QUOTE=ElijahLofgren]
It could be that Thunderbird 1.5.0.2 will only work with Ubuntu Dapper Drake (I don't know. I haven't tried it on Breezy)[/QUOTE] For the record, it works on Breezy--I have tried it.

---

### Post by Pugaciov on 2006-05-09
[QUOTE=aysiu]If you apt-get, you're going to get version 1.0.7: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

If you want 1.5.0.2, download [this script](http://www.ubuntuforums.org/showpost.php?p=950010&postcount=21) to your desktop and then go to a terminal and copy and paste these commands: ```
cd ~/Desktop
mv installnewthunderbird.sh.txt installnewthunderbird
chmod +x installnewthunderbird
./installnewthunderbird
```[/QUOTE]

Hi all
I tried using these instructions but I always get this error when I launch with the command thunderbird

(QFA)Talkback error: Can't initialize.

..and everytime I launch it I get the profile creation window.

---

### Post by ElijahLofgren on 2006-05-09
[QUOTE=Pugaciov]Hi all
I tried using these instructions but I always get this error when I launch with the command thunderbird

(QFA)Talkback error: Can't initialize.

..and everytime I launch it I get the profile creation window.[/QUOTE]
It seems like more people have had success following: [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

---

### Post by Pugaciov on 2006-05-09
[QUOTE=ElijahLofgren]It seems like more people have had success following: [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)[/QUOTE]

I had an error at the first step, so at this point I think I've messed up with profile folders...

---

### Post by ElijahLofgren on 2006-05-09
[QUOTE=Pugaciov]I had an error at the first step, so at this point I think I've messed up with profile folders...[/QUOTE]
You can just skip that step. The other think you tried probably already did that for you.

Try starting here:
[https://wiki.ubuntu.com/ThunderbirdNewVersion#head-0c82a667f92d14dbae8687c4758e6600c1acff30](https://wiki.ubuntu.com/ThunderbirdNewVersion#head-0c82a667f92d14dbae8687c4758e6600c1acff30)

---

### Post by Pugaciov on 2006-05-09
[QUOTE=ElijahLofgren]You can just skip that step. The other think you tried probably already did that for you.

Try starting here:
[https://wiki.ubuntu.com/ThunderbirdNewVersion#head-0c82a667f92d14dbae8687c4758e6600c1acff30](https://wiki.ubuntu.com/ThunderbirdNewVersion#head-0c82a667f92d14dbae8687c4758e6600c1acff30)[/QUOTE]

I always have the same problem, the error
(QFA)Talkback error: Can't initialize.
...and the profile thing. By the way, if I choose the default folder for the profile I receive this:
[[IMG]http://img257.imageshack.us/img257/6227/error0nx.th.png[/IMG]](http://img257.imageshack.us/my.php?image=error0nx.png)

](*,)

---

### Post by Pugaciov on 2006-05-09
Finally it works!
I deleted both old and new (created during those attempts) profile folders in /home and now it seems to work, but if I type thunderbird on the terminal I still have that string of error.
Anyone knows what that could be?

Thanks

---

### Post by ElijahLofgren on 2006-05-10
[QUOTE=Pugaciov]Finally it works!
I deleted both old and new (created during those attempts) profile folders in /home and now it seems to work, but if I type thunderbird on the terminal I still have that string of error.
Anyone knows what that could be?

Thanks[/QUOTE]
I'm not sure. I've never gotten that error. I'm running Ubuntu Dapper Drake and running "thunderbird" does not produce any errors.

---

### Post by Pugaciov on 2006-05-10
[QUOTE=ElijahLofgren]I'm not sure. I've never gotten that error. I'm running Ubuntu Dapper Drake and running "thunderbird" does not produce any errors.[/QUOTE]

Searching around I found out that some people have this error launching Firefox 1.5.x.x or Thunderbird 1.5.x.x, but with no problems for the software itself, like me.

---

### Post by NanoPC on 2006-05-13
I had Thunderbird running perfectly for a long time.I tried to install a dictonary, and next time I reinitialize it  I got this message:

(QFA)Talkback error: Can't initialize.

New account setup...etc.

I tried in /opt/thunderbird
./thunderbird
but it's not working..

Any ideas?
Thanks

---

### Post by NanoPC on 2006-05-13
I fixed it :D 
I had to create another profile and next copied all the files in the old profile except for prefs.js.
But I had to add my accounts settings manually :(

---

### Post by ElijahLofgren on 2006-05-13
[QUOTE=NanoPC]I had Thunderbird running perfectly for a long time.I tried to install a dictonary, and next time I reinitialize it  I got this message:

(QFA)Talkback error: Can't initialize.

New account setup...etc.

[/QUOTE]
You could try what worked for Pugaciov:
[QUOTE=Pugaciov]Finally it works!
I deleted both old and new (created during those attempts) profile folders in /home and now it seems to work...
[/QUOTE]

You could try this:
1. Go to your home folder in the File Manager. 
2. Click "View->Show Hidden Files"
3. Find the ".thunderbird" folder and rename it to something like ".thunderbird-backup"
4. Try re-running Thunderbird and reset up your account and see if things work.

Edit: I see making a new profile worked. Good. :)

---

### Post by NanoPC on 2006-05-13
Thanks anyway! :-)

---

### Post by benuski on 2006-05-14
Okey.  I first tried to follow the Thunderbird new version script thing without having the ubuntu version installed first... I installed and ran the script and everything... and then when I tried to click the button to launch it, nothing every popped up.  Then I tried to follow the wiki version and that didn't work either.  So I did a "rm -rf" to delete  the version i downloaded, and now when I try to run the Ubuntu version, it gives me 

> Cannot launch entry

Details: Failed to execute child process "mozilla-thunderbird" (No such file or directory)

help!

---

### Post by ElijahLofgren on 2006-05-14
[QUOTE=benuski]So I did a "rm -rf" to delete  the version i downloaded, and now when I try to run the Ubuntu version, it gives me 

>  Cannot launch entry

Details: Failed to execute child process "mozilla-thunderbird" (No such file or directory)


help![/QUOTE]
Try this:
```
sudo mv /usr/bin/mozilla-thunderbird-old /usr/bin/mozilla-thunderbird
```

---

### Post by benuski on 2006-05-14
nope.... still the same thing....is there any way to wipe everything about thunderbird away and then start over with downloading the package manager version and then upgrading to the new version?

---

### Post by ElijahLofgren on 2006-05-15
[QUOTE=benuski]nope.... still the same thing....is there any way to wipe everything about thunderbird away and then start over with downloading the package manager version and then upgrading to the new version?[/QUOTE]
I would try this:
```
sudo apt-get remove mozilla-thunderbird
sudo apt-get install mozilla-thunderbird
```

---

### Post by benuski on 2006-05-15
It still doesn't work... when i try and do that, I get this in the terminal:

> Setting up mozilla-thunderbird (1.0.8-0ubuntu05.10.1) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


---

### Post by ElijahLofgren on 2006-05-15
[QUOTE=benuski]It still doesn't work... when i try and do that, I get this in the terminal:[/QUOTE]
Hmm.. Sounds like a bug in the package. Maybe now would be a good time to try out Ubuntu Dapper Drake. It will be released as final in June, but it already has Thunderbird 1.5
See: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

---

### Post by benuski on 2006-05-15
[QUOTE=ElijahLofgren]Hmm.. Sounds like a bug in the package. Maybe now would be a good time to try out Ubuntu Dapper Drake. It will be released as final in June, but it already has Thunderbird 1.5
See: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)[/QUOTE]

Now that I've installed Dapper, the problem is still there... i don't get it

---

### Post by ElijahLofgren on 2006-05-15
[QUOTE=benuski]Now that I've installed Dapper, the problem is still there... i don't get it[/QUOTE]
Neither do I. 
Maybe if you try this:
```

sudo apt-get --purge mozilla-thunderbird
sudo apt-get install mozilla-thunderbird

```
Even with those errors, does running mozilla-thunderbird still work? It may be that you can just ignore those errors.

---

### Post by benuski on 2006-05-15
[QUOTE=ElijahLofgren]Neither do I. 
Maybe if you try this:
```

sudo apt-get --purge mozilla-thunderbird
sudo apt-get install mozilla-thunderbird

```
Even with those errors, does running mozilla-thunderbird still work? It may be that you can just ignore those errors.[/QUOTE]

Well, due to that problem and to other annoyences, I decided to delete all of my ubuntu and just reinstall it, so thats what I'm doing.  *shrug*

---

### Post by keheikev on 2006-05-18
I am having trouble with the applications internal help not opening. I first tried installing thunderbird with automatix but I got something called mail/news with the installation and the help about icons not opening fully ie no thunderbird logos. any comments appreciated. Right now I am happy Ive got a whole app in breezy 5.10.:KS 
Keheikev
I wont give up if you wont!;)

---

### Post by ElijahLofgren on 2006-05-18
[QUOTE=keheikev]I am having trouble with the applications internal help not opening. I first tried installing thunderbird with automatix but I got something called mail/news with the installation and the help about icons not opening fully ie no thunderbird logos. any comments appreciated.[/QUOTE]
The internal help is just a link to: [http://www.mozilla.org/support/thunderbird/](http://www.mozilla.org/support/thunderbird/)

Probably the reason it's not opening is Thunderbird needs to be told to use Firefox for opening links.
You can fix this by doing the following:
Try adding the following lines to ~/.thunderbird/{random string}.default/prefs.js
user_pref("network.protocol-handler.app.http", "firefox");
user_pref("network.protocol-handler.app.https", "firefox");

The reason there are no thunderbird logos and it's called "mail/news" is because of the Mozilla Trademark Policy.
See the following:
[http://www.mozilla.org/foundation/trademarks/policy.html](http://www.mozilla.org/foundation/trademarks/policy.html)
[http://www.mozilla.org/foundation/trademarks/faq.html](http://www.mozilla.org/foundation/trademarks/faq.html)
[http://ubuntuforums.org/showthread.php?t=123113#3](http://ubuntuforums.org/showthread.php?t=123113#3)

---

### Post by keheikev on 2006-05-18
Thanks for the reply. I did get thunderbird opening links and the help button. Now I am investigating the icons. Kind of a ubuntu 5.10 question but I guess  I need to change the permissions on /usr/share/icons in order to cut and paste the ones that came with the thunderbird folder to make a good looking launcher.
Thanks so much. Let me know what you know about ruby on rails....
Keheikev:KS

---

### Post by joshrobinson on 2006-05-18
[QUOTE=keheikev]Thanks for the reply. I did get thunderbird opening links and the help button. Now I am investigating the icons. Kind of a ubuntu 5.10 question but I guess  I need to change the permissions on /usr/share/icons in order to cut and paste the ones that came with the thunderbird folder to make a good looking launcher.
Thanks so much. Let me know what you know about ruby on rails....
Keheikev:KS[/QUOTE]

thunderbird 1.5.0.2 is in the dapper repositories now.. should be there in breezy

---

### Post by ElijahLofgren on 2006-05-19
> **keheikev]I am having trouble with the applications internal help not opening. I first tried installing thunderbird with automatix but I got something called mail/news with the installation and the help about icons not opening fully ie no thunderbird logos. any comments appreciated. Right now I am happy Ive got a whole app in breezy 5.10.:KS 
Keheikev
I wont give up if you wont! said:**
> 
Thunderbird 1.5.0.2 finally made it into Dapper.

From the changelog:
> 
  * Rework the Debconf www-browser selection so it automatically chooses to
    use gnome-control-center's choice if it detects it installed, otherwise
    falling back to x-www-browser (launchpad.net/{31841,34546,41706,25704})
...
* Add proper branding (Yay, we're Thunderbird again, not Mail/News, and we
    have an icon and an about box, oh my!), icon thanks to Andy Fitzsimon,
    integration mangling thanks to Alexander Sack. (launchpad.net/19439)

So it sounds like your problems will be fixed with Dapper's Thunderbird 1.5.0.2 :) 

[QUOTE=keheikev]
Thanks for the reply. I did get thunderbird opening links and the help button. Now I am investigating the icons. Kind of a ubuntu 5.10 question but I guess I need to change the permissions on /usr/share/icons in order to cut and paste the ones that came with the thunderbird folder to make a good looking launcher.

Instead of copying over the icon I would just choose the icon from the Thunderbird folder:
1. Right click on the launcher you created.
2. Choose Properties
3. Click on the icon (on the left of "Name:")
4. Type /opt/thunderbird/icons and hit "Enter"
5. Click on mozicon50.xpm
6. Click the "Open" button.

Or instead you can just copy the icon to /usr/share/pixmaps:
```
sudo cp /opt/thunderbird/icons/mozicon50.xpm /usr/share/pixmaps/
```

[QUOTE=keheikev]
Let me know what you know about ruby on rails....
[/QUOTE]
I don't know much about it. I started learning it, then I was going to learn CakePHP instead, then I found CMS Made Simple which works great so I stopped learning CakePHP. I was learning Ruby on Rails and CakePHP so that I could easily re-write a CMS that I wrote.

---

### Post by keheikev on 2006-05-25
[QUOTE=ElijahLofgren]Thunderbird 1.5.0.2 finally made it into Dapper.


So it sounds like your problems will be fixed with Dapper's Thunderbird 1.5.0.2 :) 
[/QUOTE]
Does this mean that I can install the software with apt-get or synaptic now because when I browsed for tbird it wasnt there in synaptic and I have additional repositories enabled?

Instead of copying over the icon I would just choose the icon from the Thunderbird folder:
1. Right click on the launcher you created.
2. Choose Properties
3. Click on the icon (on the left of "Name:")
4. Type /opt/thunderbird/icons and hit "Enter"
5. Click on mozicon50.xpm
6. Click the "Open" button.

Or instead you can just copy the icon to /usr/share/pixmaps:
```
sudo cp /opt/thunderbird/icons/mozicon50.xpm /usr/share/pixmaps/
```
.[/QUOTE]
I used the above terminal command to copy the icon to pixmaps. What if I had browsed to some other folder say the one on my desktop. If that icon is deleted or moved does that break a link to the icon? Why is it when II use the create launcher 
dialog it is greyed out in the right pane? I browsed instead to /opt/thunderbird/chrome/icons/default and selected default.xpm but now I can select at will (it works) where as before the right pane was greyed out? Is it something to do with usr/share/pixmaps this behavior was esp true when I browsed to the folder on my desktop to use the icon there in the chrome folder.
Keheikev
:KS I wont give up if you dont
waiting for the final dapper

---

### Post by ElijahLofgren on 2006-05-26
[QUOTE=keheikev]Does this mean that I can install the software with apt-get or synaptic now because when I browsed for tbird it wasnt there in synaptic and I have additional repositories enabled?
[/QUOTE]
Once you've upgraded to Dapper Drake just run this:
```
sudo apt-get install mozilla-thunderbird
```

Then just run it with:
```

mozilla-thunderbird

```


[QUOTE=keheikev]
I used the above terminal command to copy the icon to pixmaps. What if I had browsed to some other folder say the one on my desktop. If that icon is deleted or moved does that break a link to the icon?
[/QUOTE]
Yes, I think so (don't really understand what you mean).

[QUOTE=keheikev]
Why is it when II use the create launcher 
dialog it is greyed out in the right pane? I browsed instead to /opt/thunderbird/chrome/icons/default and selected default.xpm but now I can select at will (it works) where as before the right pane was greyed out? Is it something to do with usr/share/pixmaps this behavior was esp true when I browsed to the folder on my desktop to use the icon there in the chrome folder.
[/QUOTE]
I think this odd behaviour has to do with Gnome's icon picker not being very usable nor featureful. The KDE one is *much* better. ;)

---

### Post by keheikev on 2006-05-27
> 
I think this odd behaviour has to do with Gnome's icon picker not being very usable nor featureful. The KDE one is *much* better. ;) 
I think what you said in your last sentence summed it up. Funny how now that the command you gave me to add the icons to the pixmaps folder got the icon picker to work correctly. I dont have any need to fix the program with the right icons in place and no linkeage.
  I am plannig to upgrade to the new version as soon as I start to understand what I have currently installed. I do plan on having a torrent available so that the file gets downloaded quicker for everyone. I think it took 24 hours or so for me to get 5.10 on bit torrent as not to many were downloading the file in December of this year. Either that or bandwidth shaping.
Thanks for the replies again
Kev
:KS

---

