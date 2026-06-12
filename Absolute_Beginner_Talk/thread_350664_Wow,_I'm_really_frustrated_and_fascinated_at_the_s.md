---
title: "Wow, I'm really frustrated and fascinated at the same time"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Robotuner on 2007-01-31
So, now that I figure Ubunto is installed on my laptop, I have a number of things I would like to learn, but one step at a time.  I started to do some browsing with Firefox and found I needed to install Macromedia Flash.  So, I follows the link and downloaded it to the desktop.  The instructions then said to unpack it and type a bunch of stuff in the terminal.

Being a windows guy, I'm thinking that I could just double click on the package.  (It wasn't a rpm install but a ... something else). Anyway, eventually, I looked on the desktop and found what I presumed to be the file I installed and a folder.  Double clicking on the folder didn't do anything.  It took me awhile to figure out how to get to the terminal (via the menus) then it took me even longer to figure out how to navigate to the Desktop.

Eventually, I typed in the requisite command and installed Flash.

Back to Firefox, I soon realized that I had to install Real Player.  For this I had to figure out how to make a directory because just typing an installtion directory when one doesn't exist just didn't cut it.  After that, though, things went faster, having learn the cd command and after mistyping the about 10 times and then looking carefully and realizing that part of the string was in upper case.  So where am I going with this?

Simply want to know if I'm just doing it the hard way or can I just double click on most installation packages and do it from the file viewer?

---

### Post by raul_ on 2007-01-31
You can always install software with the Synaptic tool (look for it in the menu). In order to have more software available to you, tou have to enable some more repositories, so that Synaptic knows where to look. You can do that following these instructions:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

There are a lot of packaging systems in Linux, because there are many differente flavours. Ubuntu, being a Debian based distro, used the Debian packaging system, so, it uses .deb packages. If you double click those files, the software will be installed automatically. You can always install the software from source (usually the .tgz files) with a couple of commands. 

About the Flash Player, all you had to do was to copy the files to your plugins folder (i reckon that the installer sucks), a little search in the forums would have helped you.

Don't feel discouraged, if you're still starting, it's a good thing that you're not whining about Linux being so difficult, and having to actually type things in a command line. If you want to learn some useful commands have a look at this link:

[http://linuxcommand.org]("http://linuxcommand.org")

And welcome to the Ubuntu Community my friend :)

---

### Post by finer recliner on 2007-01-31
i actually recommend start doing *everything* in the command line. including the easy stuff (i.e. navigating your system, moving and renaming files etc.) you will learn much more much faster.

---

### Post by seshomaru samma on 2007-01-31
I suggest you read [this ]("http://doc.gwos.org/index.php/DapperGuide") (if you installed Ubuntu Dapper) or [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") (if you installed Ubuntu Edgy)

---

### Post by raul_ on 2007-01-31
> **seshomaru samma said:**
> I suggest you read [this ]("http://doc.gwos.org/index.php/DapperGuide") (if you installed Ubuntu Dapper) or [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") (if you installed Ubuntu Edgy)

I already posted a link :)

---

### Post by riven0 on 2007-01-31
Well, well, well... a new user who actually wants to learn. :D You're on the right track, Robotuner. I expect you'll be a Linux expert in a few months time. 

BTW, another good sites where I learned all the basic terminal commands as a beginnner was [tuXfiles]("http://www.tuxfiles.org/"). Great for new users.

Good luck!:KS

---

### Post by stucky on 2007-01-31
Don't get discouraged, there is a serious curve. Once you get passed it, you'll wonder how M$ stays in business. There are just several super important concepts that you'll learn quickly are critical. Follow the links that have been provided and feel free to post your questions. There's a ton of very cool people out there that will steer you right.

---

### Post by rccharles on 2007-02-01
> **Robotuner said:**
> So, now that I figure Ubunto is installed on my laptop, I have a number of things I would like to learn, but one step at a time. 

Automatix2 has most of what you are looking for.  See:

[http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html)

Robert

---

### Post by Sef on 2007-02-01
> Automatix2 has most of what you are looking for.

In [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-8fa840b0f29ed7a927231cb640610777ca2d9904"), it says this about Automatix:

> Warning Regarding Alternative Installation Methods

Warning: [WWW] EasyUbuntu and [WWW] Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release. 

---

### Post by jackrobinson on 2007-02-01
> **Sef said:**
> In [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-8fa840b0f29ed7a927231cb640610777ca2d9904"), it says this about Automatix:

The above claim is wrong. Breakages mostly occur because of faulty updates and lack of testing on the part of Ubuntu (hell they even break packages after an official release on the official main repository). This argument has been beaten to death many times. For all practical purposes I have tested Automatix, looked at its code and found it perfectly safe. As for Easy Ubuntu, I haven't tested it in a  while.

---

