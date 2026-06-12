---
title: "Couple of problems and annoyances..."
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by groovestix on 2006-08-27
Hello!

I proudly installed Ubuntu this morning (after long night of 60GB backup) and so far it's been running great.

I have couple of small (or not) questions that has been bugging me since I started using this great OS.

1. Where do I install things to? Is there a common directory I should know of, maybe something like Program Files in Windows... ?
2. How do I install manually downloaded programs?
Ex. I downloaded Firefox since I though that it's better to use Mozilla's original version of it (Is that a good idea BTW?) and the file:

firefox-1.5.0.6.tar.gz

is sitting on my desktop waiting. I opened it, and I see how it works, but I still have no idea how to install it.
3. I use lots of Macedonian language, so even though I figured out how to download the support itself, I have no idea how to Alt-Shift it. :)
4. I have lots of things I want to transfer from a NTFS (Windows XP) machine. That's possible, right?
5. Is there a way to have a passwordless user ?

Thanks!

---

### Post by tribaal on 2006-08-27
Glad you like Ubuntu!

Most of the installed programs *binaries* go to /usr/bin.

However, you don't really need to know that, from a practical point of view: one of the best features from Ubuntu is it's automated install system.

Instead of downloading the programms yourself, you let "apt-get" go this for you.

For example, installing Mozilla Firefox is done by opening a terminal and typing in "sudo apt-get install firefox".
Alternatively, you can use Synaptic (found in you "System" menu under Administration > Synaptic package manager).

Hope this answers some of your questions...

- trib'

---

### Post by groovestix on 2006-08-27
Right!
So which Firefox is better?

---

### Post by charbo on 2006-08-27
I recommend using the package management system to install. What is installed is sometimes more customized for the distribution, and all sorts of dependency issues are automatically taken cared of.

Advantages of compiling and installing from source code is that you can use the most cutting edge version, and it may run a bit more efficiently, because it would be more optimal for your hardware.

However, the advantage of using the package from the regular repository is that other knowledgeable people have already done the verification work for you. And that is pretty big.

So, I would recommend using ubuntu package version.
Following link would show you how to install source and other software. Jagot posted on another post.
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

I don't know about Macedonian language support. Alt-Shift is used to go into Macedonian input in Windows? You probably need to install Macedonian Input Method. I do not know anything about this, sorry...

You can get stuff from ntfs machines, of course. There are many ways you can do this. If the ntfs machine is running ftp server, you can just get stuff from there by ftp. If ntfs machine is sharing a volume and you want to connect to it, you can do that, too. For this, probably you would use Samba.

I believe Suse installed passwordless by defualt, so I know you should be able to set up your system to be passwordless, but I don't know how, off hand. I like to keep having to type password for the security reasons, though.

Hope this helps.

---

### Post by annda on 2006-08-27
i found the easiest way to change keyboard layouts is to add the 'keyboard indicator' to your panel and work with its preferences. it will let you choose how you switch between the layouts (called groups, because you can have more than one layout for each language).

and greetings to sunny Macedonia!

---

### Post by Anonii on 2006-08-27
> **tribaal said:**
> Glad you like Ubuntu!

Most of the installed programs *binaries* go to /usr/bin.

However, you don't really need to know that, from a practical point of view: one of the best features from Ubuntu is it's automated install system.

Instead of downloading the programms yourself, you let "apt-get" go this for you.

For example, installing Mozilla Firefox is done by opening a terminal and typing in "sudo apt-get install firefox".
Alternatively, you can use Synaptic (found in you "System" menu under Administration > Synaptic package manager).

Hope this answers some of your questions...

- trib'

About your language problem now.
I hope you have GNOME, because I dont know about KDE. Go to one of the panels. Add to panel the "Keyboard Indicator" by right clicking on the panel and selecting Add to Panel. Right click it, it should be saying "USA" or something. Go to the layouts tab, add your language. Then go to the "Lay out Options" tab, and there should be a bolded "Group Shift/Lock behaviour" in the middle, expand it, and select the combo of keys you want :)

Good Luck.

---

### Post by groovestix on 2006-08-27
Greeeeeat! This is awesome! Thanks so much dudes!
Alright that's done, and in meantime I fixed my Flash support in FireFox. I have one more question to ask - I wanted to use "[Hack Attack: Top 10 Ubuntu apps and tweaks]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php")" to install someof the apps. This is what I get when I try to execute the commands in the terminal:

groovestix@Toupee:~$ apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
groovestix@Toupee:~$ apt-get install beagle
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


What's the meaning of this?

---

### Post by Anonii on 2006-08-27
> **groovestix said:**
> Greeeeeat! This is awesome! Thanks so much dudes!
Alright that's done, and in meantime I fixed my Flash support in FireFox. I have one more question to ask - I wanted to use "[Hack Attack: Top 10 Ubuntu apps and tweaks]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php")" to install someof the apps. This is what I get when I try to execute the commands in the terminal:

groovestix@Toupee:~$ apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
groovestix@Toupee:~$ apt-get install beagle
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


What's the meaning of this?

APT can only be used as the superuser (root)
Be sure to use the "sudo" command before APT.
Like: 
sudo apt-get install beagle.
It will then ask you for the superuser password, and after that, ta~ta!!!

The superuser account is required for countless of jobs in Linux, like editing protected documents, using applications, installing them and configuring them. But you shouldnt abuse root, its a double-edged blade.
Its important to learn to use the sudo command, check this out:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by confused57 on 2006-08-27
Here's an excellent link for installing things in Ubuntu:

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by GonZo1323 on 2006-08-27
> **groovestix said:**
> Greeeeeat! This is awesome! Thanks so much dudes!
Alright that's done, and in meantime I fixed my Flash support in FireFox. I have one more question to ask - I wanted to use "[Hack Attack: Top 10 Ubuntu apps and tweaks]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php")" to install someof the apps. This is what I get when I try to execute the commands in the terminal:

groovestix@Toupee:~$ apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
groovestix@Toupee:~$ apt-get install beagle
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


What's the meaning of this?


that top 10 list is sweet!!!

---

### Post by groovestix on 2006-08-28
Yeah the list is a must!

I still have problems installing from it though...

1. This one is about Beagle.
groovestix@Toupee:~$ sudo apt-get install beagle
Reading package lists... Done
Building dependency tree... Done
Package beagle is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libbeagle0
E: Package beagle has no installation candidate
groovestix@Toupee:~$ sudo apt-get install libbeagle0
Reading package lists... Done
Building dependency tree... Done
libbeagle0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2. VLC
groovestix@Toupee:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc

3. Also I don't know why/how, but my "Add/Remove applications" has been acting strange. It won't let me check anything (ex. screenshot).

---

### Post by chimerical_brio on 2006-08-28
I was having the same problems as you are. What you need to do is enable the Universe and Multiverse repositories in Synaptic. Go System->Administration->Synaptic, then Settings->Repositories. Highlight "Ubuntu 6.06 LTS (Binary)" and click Edit. Check the Universe and Multiverse options, and close that window and the repositories window. Click Reload in Synaptic, and you should be ready to go. I know you'll be able to install Beagle in Synaptic, and probably from the terminal, although I'm not 100% sure.

As for your other problem, I have no clue. :oops:

---

### Post by Anonii on 2006-08-28
> **groovestix said:**
> Yeah the list is a must!

I still have problems installing from it though...

1. This one is about Beagle.
groovestix@Toupee:~$ sudo apt-get install beagle
Reading package lists... Done
Building dependency tree... Done
Package beagle is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libbeagle0
E: Package beagle has no installation candidate
groovestix@Toupee:~$ sudo apt-get install libbeagle0
Reading package lists... Done
Building dependency tree... Done
libbeagle0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2. VLC
groovestix@Toupee:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc

3. Also I don't know why/how, but my "Add/Remove applications" has been acting strange. It won't let me check anything (ex. screenshot).

First of all, I love your temper, I'd be angry in your situation :P
Anyway, from what I see beagle cant be installed because APT cant find it. So, we will find an alternate way. Use Firefox, and go to the search box on the upper right, use the "Ubuntu Packages" search. Search for "beagle". You get some results. Go to the first:
"dapper (gnome): indexing and search tool for your personal data [universe]
0.2.6-1ubuntu5: amd64 i386 powerpc"

There will be a list of dependencies (important, cant be installed without them), recommended (it will work allright without them) and suggested packages. These will probably be needed later, but anyway, continue to "Download beagle" in that box there is a list of architectures. You chose your architecture, probably i386. (Click on i386 <:) Select a freaking mirror, and get that .deb package!

Hooray, now you have a .deb package, you have no idea what to do.
Get on the terminal. I guess you know how to use it, at least basicaly. Get into the directory that the .deb package was downloaded (probably Desktop) and use the following command:
*sudo dpkg -i bea*.deb*
It will probably be installed all right, _BUT_ it will also probably ask for dependencies. If thats the case, you have to go to that page with the -recommended, depending and suggested- packages and download the dependencies you need. 
There is probably an easier way, by adding a line into your /etc/apt/sources.list, than doing all these, but... well, I dont know how to find that line in Ubuntu, and I think thats not like Debian.
I hope you fix it, else post your problem here.
Good luck.

---

### Post by groovestix on 2006-08-28
Hahaha, that was a funny freaking answer! :)) JK.
Wow .deb packages are the way kids!
It was really easy to track down each dependency needed and plus installing with the GUI was super easy too.
BTW I'm really not upset/angry Anonii.

P.S. I followed the instructions by chimerical_brio, but I still get the same error message in "Add/Remove Applicationas".
:)

---

### Post by Anonii on 2006-08-28
So... I guess, problem solved, eh?

Any more questions? >:3

---

### Post by groovestix on 2006-08-28
Yeah, it's all good now. Now it is time to transfer the 60GB back. :(

Thanks a lot dudes and dudetes. :cool:

---

