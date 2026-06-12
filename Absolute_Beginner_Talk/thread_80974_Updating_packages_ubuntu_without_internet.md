---
title: "Updating packages/ ubuntu without internet"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by Lisa_T on 2005-10-23
Is it possible to update Ubuntu repositories without an internet connection? My x20's modem doesn't seem to want to work- in either Win or Ubuntu. (secondhand machine).

---

### Post by aysiu on 2005-10-23
The packages have to come from somewhere.
It is possible to download packages from another computer and then install them individually, but this requires at least some computer to have internet access.

---

### Post by Lisa_T on 2005-10-23
That's not a problem. I have another laptop with broadband access, any number of flash drives, and a cd/dvd re writer, so compiling 'repositories' that way would be no problem. Then I'd need to work out how to get them installed!

---

### Post by blastus on 2005-10-23
An short explanation of repositories may help. Ubuntu uses "repositories" to install software. A repository is a collection of packages. A package is a file with a .deb extension. A package is an archive (like ZIP) and it contains the necessary instructions to install itself on your computer. OK, so a repository is a bunch of packages. In addition to a list of packages, each repository has metadata associated with it. This metadata consists of a list of packages that are in the repository, along with some additional info about each package.

For example, if repository A contains the packages...

packagea.deb
packageb.deb
packagec.deb
packaged.deb

...then the metadata for repository A will contain references to these 4 packages. The packaging system can become quickly complicated due to the fact that some packages may be dependent on other packages. For example, packagea.deb may be dependent on packageb.deb and packageb.deb may be dependent on packagec.deb and so forth. Fortunately, there is a tool that can handle these dependencies for us automatically.

The command to install packages from a repository is called apt-get. However, in order to use apt-get it needs to know where to find the repositories. The file /etc/apt/sources.list contains a list of repositories that apt-get uses.

```
sudo apt-get update
```
This command tells apt-get to retrieve the metadata information for each repository that is listed in /etc/apt/sources.list. Remember, the metadata for a repository contains a list of the packages in that repository. If you change the list of repositories (i.e. by editing /etc/apt/sources.list) then you must run "sudo apt-get update." It is a good idea to run "sudo apt-get update" every once in a while anyway because the repositories may change (i.e. old packages removed and new packages added.)

```
sudo apt-get install mozilla-firefox
```
This command tells apt-get to install the given package. In this case, it would install the package that is called "mozilla-firefox." It will automatically install the mozilla-firefox package and it will install any packages that it depends on. Keep in mind, that the name of a package is not the filename of a package. For example, the filename for the mozilla-firefox package may be something like firefox_1.0.7-0ubuntu20_i386.deb. The name of a package is part of the metadata for that package and it is stored inside the .deb file for that package. Since .deb files are archives, you can open them up in a file archiver and take a look at their contents.

```
sudo apt-get install mozilla-firefox --print-uris
```
This command is similar to the previous, except that instead of installing the mozilla-firefox package it will print out the URIs of each package that it would have installed. A URI is a Uniform Resource Indicator) but it may not specify a location. However, for all purposes, the URIs that the above command will return will be URLs (a URL is a type of URI.)

```
sudo apt-get upgrade
```
This command tells the packaging system to install the newest versions of every package. As with the previous command, you can use the "--print-uris" option to print out a list of URLs for each package that would be downloaded. When apt-get installs packages it first has to download them. It downloads them to the directory /var/cache/apt/archives. Before apt-get attempts to download a package, it first checks to see if the package file is already in /var/cache/apt/archives. If it is then it uses it, otherwise it downloads the package file into that directory.

Now since your target Ubuntu machine does not have Internet access at all, you can't even issue a "sudo apt-get upgrade --print-uris" command. Therefore, you must have access to a Ubuntu machine somewhere that has Internet access so that you can determine what packages you need to download. 

Now with the packaging system, each repository is specified by a URL. The Ubuntu repositories are specified with http:// URLs. However, you can also specify file:// URLs. This means that you can create a local repository and use it. Remember, a repository contains a list of package files and metadata about that list. To create a local repository from a list of package files, you use the "dpkg-scanpackages" command to create the metadata info for the repository. See this thread [HOWTO: Custom repo (local or remote)](http://www.ubuntuforums.org/showthread.php?t=42862).

However, even if you have access to a Ubuntu machine that has Internet access, if that machine does not have the exact same list of packages installed on it, you could run into problems (i.e. you can download packages that the other machine doesn't need and not download packages that the other machine needs.) I'm not sure what the solution is to this because you can't just download a service pack in Ubuntu like you can in Windows. It would be nice if Ubuntu provided a cumulative update CD or something like that you could simply download and add to your list of repositories so you could easily update a Ubuntu machine without an Internet connection. I would find this extremely useful as I'm on dialup.

---

### Post by gamerchick02 on 2005-10-24
Is there a way for you to network your laptop and your Ubuntu box together so you can get the updates you need?  I'd recommend getting a router to do this.  

Just a quick thought, and good luck with getting your updates!

Amy

---

### Post by Lisa_T on 2005-10-24
Well, the laptop i use for internet is win xp and as all my phd work is on it, I'd prefer not to mess around with it. However, it is wireless, and I think I have a spare wireless card lying around. Could I piggyback the internet connection across wireless/ bluetooth? H'mm. Perhaps it would be less complicated to simply reinstall ubuntu on my x20 and make sure that the modem is hooked up.. which leads to another couple of questions:

If I reinstall ubuntu, what happens to the current partitioned disk set up? I don't want to risk losing win 98 even if i do hate it. 

..and am I right in thinking that Ubuntu talks about ethernet when it really means internet? 'Cos when it asked me about ethernet something or other during installation I said i didn't need it- since I *don't* use my ethernet connection, ever! I know the modem on the x20 is definitely working, even though I couldn't even connect thru windows, but then the internet connection wizard on 98 is always a bit dodgy. The modem made all the right noises; the info just didn't download..

..and is the update process rather like activation on win xp- does everything happen automatically or do you need to physically dial up a connection first? Trouble is, my Win XP machine is using AOL broadband, and I have an idea that that can't be transferred across to Linux.

I agree occassional CDs would be MUCH more helpful!

---

### Post by Akkerkop on 2005-10-25
Looking at most of the posts i can see that whenever you want to install any packages use: "apt-get", and "./configure -> make -> make install". 

I am a WinXP & Ubuntu (newbie) user. At the moment i've got a WinXP internet connetion, GPRS through bluetooth dongle and cellphone. I'm trying to setup a connection in Ubuntu. So i'm not online with Ubuntu to install any packages.

I've downloaded the following files (from WinXP): 
bluez-utils_2.19.orig.tar.gz
gnome-bluetooth-0.6.0.tar.gz
obexserver_1.0-3.tar.gz

Now i want to "install" them, and i aint got a clue how to. I've tried the process "./configure -> make -> make install", but get a error: "No C compiler found...". 

What am i doing wrong? Do i miss the plott??

Please can someone advise on how to install anything without a internet connection?

---

### Post by gamerchick02 on 2005-10-28
[QUOTE=Lisa_T]Well, the laptop i use for internet is win xp and as all my phd work is on it, I'd prefer not to mess around with it. However, it is wireless, and I think I have a spare wireless card lying around. Could I piggyback the internet connection across wireless/ bluetooth? H'mm. Perhaps it would be less complicated to simply reinstall ubuntu on my x20 and make sure that the modem is hooked up.. which leads to another couple of questions:

If I reinstall ubuntu, what happens to the current partitioned disk set up? I don't want to risk losing win 98 even if i do hate it. 

..and am I right in thinking that Ubuntu talks about ethernet when it really means internet? 'Cos when it asked me about ethernet something or other during installation I said i didn't need it- since I *don't* use my ethernet connection, ever! I know the modem on the x20 is definitely working, even though I couldn't even connect thru windows, but then the internet connection wizard on 98 is always a bit dodgy. The modem made all the right noises; the info just didn't download..

..and is the update process rather like activation on win xp- does everything happen automatically or do you need to physically dial up a connection first? Trouble is, my Win XP machine is using AOL broadband, and I have an idea that that can't be transferred across to Linux.

I agree occassional CDs would be MUCH more helpful![/QUOTE]


Hmmm...

Your computer is looking for any network it is connected to.  You can access the internet through a network if it is allowed (my school had internet access through the network as default, my work didn't have it as default).

You don't have a straight up (wired) LAN card in either machine?  I was thinking that maybe you could use the wireless through the laptop and hook the desktop to the laptop via a straight-through cable.  This would be like using the laptop as a router, since it is getting a wireless signal and transferring it to the desktop.

Now, I have no idea if that will work or not, but it seems like it would.  I mean, the connection would go from the laptop to the desktop, right?  It would be like using the laptop as an antenna for the internet (if that makes any sense!) and that signal would be transfered to the desktop.  If this is what you mean by piggybacking...

It can't hurt to try.

Hope it helps.  Good luck!

Amy

Edit for spelling.

---

### Post by DigitalAxis on 2005-12-16
Here's my plan (this is probably the LEAST elegant way to do it) to make a supplimentary CD...

In short form, I get a list of installed packages, download all the packages, then remove the ones that are on the install CD.

1.) Install apt-show-versions **apt-get install apt-show-versions**
2.) Save output (which is all installed packages) to a file **apt-show-versions > installed**
3.) Somehow filter this list down to a list of packages.  I used something like **cat installed | awk '{print $1}' > install** followed by a search-and-replace of the file 'install' in kate, and then joining all the lines.  I'd do that in sed but I'm not that good with regular expressions and removing /unknown is tricky when / is the delimiter
4.) Remove all the old packages in /var/cache/apt/archives/ so you'll only have the latest packages.  I suppose if you wanted to keep the old ones as a safety net you could just move them somewhere
5.) Run **apt-get -d --reinstall install `cat install`**.  This basically just gets all the packages on the list without really reinstalling. (reinstall is necessary so it actually does the downloading)
6.) Now take one of the install CD manifest lists, and strip it down to just the names of the packages in the on-CD repository.  I think I used sed and kate for this.
**cat ubuntu-5.10-install-i386.list | sed 's/.*/// / > cdlist**
7.) cd /var/cache/apt/archives and run rm `cat cdlist`
8.) Now you've got just the packages that aren't on the install CD.  Then you make a repository according to the instructions in that other link, and stick it on a CD.  In case you're wondering, Kubuntu and Xubuntu fit on one CD with hundreds of megabytes to spare.

Any thoughts on how this procedure could be cleaned up/scripted/simplified?  I'm aware of the --print-uris feature of apt-get, but I'm not sure how to impliment it in this procedure.

---

