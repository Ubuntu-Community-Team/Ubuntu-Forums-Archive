---
title: "Uninstalling apps and keeping the file system clean"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by jrjazzman on 2006-10-26
Packages and repositories are great, but sometimes you have to go outside the system to get the apps you need.  Given that a *nix program conventionally puts files all over the file system (/etc, /usr/share, /opt, ...), what's the best way to keep your file system from having orphaned files scattered about after installing/uninstalling programs?  

As a related question, can someone describes why *nix programs aren't more self contained in their own directory?

---

### Post by bulldog on 2006-10-26
Maybe is this topic of some help,

[http://ubuntuforums.org/showthread.php?t=140920%3Cbr%20/%3E](http://ubuntuforums.org/showthread.php?t=140920%3Cbr%20/%3E)

---

### Post by TheWizzard on 2006-10-26
[LIST]
[*]use aptitude instead of apt-get. aptitude keeps track of dependencies and removes them when you uninstall the program that needed it.
[*]use checkinstall if you build from source. 
[*]gtkorphan is a nice GUI tool to find unneeded dependencies. 
[/LIST]

it's a good thing to run "aptitude autoclean" once in a while. you can also run "aptitude clean" to get rid of all deb-files. 

check:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by jrjazzman on 2006-10-26
Although it probably wasn't clear, I was primarily referring to the tarball method of installing applications.  


> **TheWizzard said:**
> [LIST]
[*]use aptitude instead of apt-get. aptitude keeps track of dependencies and removes them when you uninstall the program that needed it.
[*]use checkinstall if you build from source. 
[*]gtkorphan is a nice GUI tool to find unneeded dependencies. 
[/LIST]

it's a good thing to run "aptitude autoclean" once in a while. you can also run "aptitude clean" to get rid of all deb-files. 

check:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by TheWizzard on 2006-10-26
> **jrjazzman said:**
> Although it probably wasn't clear, I was primarily referring to the tarball method of installing applications.

ok, tarballs are sourcecode. 
install and use checkinstall

then do 
```
./configure 
make
sudo checkinstall
```
now a nice deb-file is made and you can install that using dpkg -i
this makes sure the new program is added to the database of the package manager

---

### Post by jrjazzman on 2006-10-30
> **TheWizzard said:**
> ok, tarballs are sourcecode. 
install and use checkinstall

then do 
```
./configure 
make
sudo checkinstall
```
now a nice deb-file is made and you can install that using dpkg -i
this makes sure the new program is added to the database of the package manager

Great.  I see checkinstall available for download in synaptic.  Thanks for this suggestion.  I'm still curious to know how *nix admins kept file systems from filling up with old, unused files before things like package systems and checkinstall existed.  Also still curious about why unix applications traditionally distribute their files in so many shared directories, e.g. /etc, /usr/bin, etc.  I grew up on dos & windows, so I'm used to going to c:\program files\my app\ to find all the files for an application (for the most part).  I don't know how to do this on linux.

---

### Post by Phlosten on 2006-10-30
On *nix based systems it is not about making sure an application has all its own files together, it is about making sure every application uses common storage points for common type of files. ie all configuration files can be found in /etc and so forth.

---

### Post by jrjazzman on 2006-10-30
> **Phlosten said:**
> On *nix based systems it is not about making sure an application has all its own files together, it is about making sure every application uses common storage points for common type of files. ie all configuration files can be found in /etc and so forth.

yeah i see the logic in that, assuming that all applications have the same notion of file types.  Not sure the utility of the design though.  What's more common, needing to edit some files for a single application, or needing to edit a config file in /etc for each of several different applications?  I'd think the former, however I'm still learning the basics and may see the light at some point.

If anyone knows of a history of unix type thing that would describe the philosophy, please post a link.

---

### Post by bodhi.zazen on 2006-10-31
[History of Linux](https://netfiles.uiuc.edu/rhasan/linux/)

[Linux wiki](http://en.wikipedia.org/wiki/Linux)

---

### Post by jrjazzman on 2006-10-31
> **bodhi.zazen said:**
> [History of Linux](https://netfiles.uiuc.edu/rhasan/linux/)

[Linux wiki](http://en.wikipedia.org/wiki/Linux)

not sure why you bothered posting this, but you clearly weren't trying to help, assuming you're remotely familiar with the content of these resources.  thanks.

---

### Post by TheWizzard on 2006-11-01
> **jrjazzman said:**
> yeah i see the logic in that, assuming that all applications have the same notion of file types.  Not sure the utility of the design though.  What's more common, needing to edit some files for a single application, or needing to edit a config file in /etc for each of several different applications?  I'd think the former, however I'm still learning the basics and may see the light at some point.


trust me, it is much more convenient to have all config files in /etc. one major benefit is for making backups. a backup of /etc makes problem solving much easier.

---

### Post by jrjazzman on 2006-11-01
> **TheWizzard said:**
> trust me, it is much more convenient to have all config files in /etc. one major benefit is for making backups. a backup of /etc makes problem solving much easier.

Are /etc and /home the only directies that need to be backed up in order to restore the system?  If so, that would be a pretty big benefit.

---

### Post by bodhi.zazen on 2006-11-01
> **jrjazzman said:**
> Are /etc and /home the only directies that need to be backed up in order to restore the system?  If so, that would be a pretty big benefit.

No, it is not quite that easy, but here is an easy way to back up:

[Back up system with rsync](http://www.mikerubel.org/computers/rsync_snapshots/)

It is not as bad as it looks !

---

### Post by TheWizzard on 2006-11-02
> **bodhi.zazen said:**
> No, it is not quite that easy, but here is an easy way to back up:

[Back up system with rsync](http://www.mikerubel.org/computers/rsync_snapshots/)

It is not as bad as it looks !

for most purposes backing up /etc and /home is indeed sufficient to allow you to restore your system. backing up binaries is a waste of space because you can download them easily. you can make a list of installed software like this: 
```
$ dpkg --get-selections | grep -v deinstall > /backup/installed-software.log
```
and restore it like this: 
```
# dpkg --set-selections < /backup/installed-software.log
```

if you have plenty of space, you can create images of your hdd. [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) 


rsync is indeed a nice cli tool to make backups. i use this myself. 
for my laptop, i use rsync to backup my working folder over the network every time i logout! (i know i'm paranoid, but laptops can be stolen and i don't want to lose work)

you may also want to take a look at dirvish. > Dirvish is a fast, disk based, rotating network backup system.
With dirvish you can maintain a set of complete images of your filesystems with unattended creation and expiration. A dirvish backup vault is like a time machine for your data.

---

### Post by jrjazzman on 2006-11-02
I just discovered rsync this week and am loving it so far.  I had a similar method with winrar on windows, which is backing up my personal folders at least once per day in a diff fashion (sync vs. full re-copy).  

I'm going to try a dual pronged backup strategy.  

1) once a week do full backup with partimage
2) daily or more frequently rsync my /home and /etc folders.  Even with all the crap I have in /home (30 gb or so), the syncs are fast.

I was initially disappointed that rsync doesn't compress the backup, but I realize now that uncompressed is probably better for me because my external backup drive is big enough, so compression would just slow everything down with no real benefit in this particular case.  I'm still surprised it doesnt' have an option to compress the backup.  It's probably hard to implement.  Winrar does it (obviously, it's a compression prog), but in a ghetto way.  It basically creates a new temp archive file, which gets just as big as the original archive.  When it's done it deletes the original and renames the temp.  So you have to have enough space for your archive file's size x 2.

---

### Post by jrjazzman on 2006-11-02
> **TheWizzard said:**
> you may also want to take a look at dirvish.

dirvish looks nice.  I think the FAQ mentioned backing up open RDBMSs does't really work.  I assume similar restrictions apply to any open files.  I didn't see anywhere that they discouraged backing up the current root filesystem, which is what I'd want to do.  I know partimage cannot do this, I wonder if dirvish can do it?

---

### Post by bsussman on 2006-11-02
> **jrjazzman said:**
> Also still curious about why unix applications traditionally distribute their files in so many shared directories, e.g. /etc, /usr/bin, etc.  I grew up on dos & windows, so I'm used to going to c:\program files\my app\ to find all the files for an application (for the most part).  I don't know how to do this on linux.

Since the beginning of time, unix has been a cooperative environment, meaning that many libraries were developed and used by many projects.  It makes no sense for everybody to invent a routing to do the same thing.

Package management has been around practically since the beginning of time so this made it practical to use shared libraries and keep packages small and to the point.

There are guidelines on package building.  Of course there are competing package schemes.  debian and debian-based distributions use the .deb package and the standards for file placement documented at [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

there is a package importer that allows other package formats to be used, called alien.  After alll, a package is just some glorified tar-like file with a manifest and a few tags.  If you want to start studying, the hello package (that's right, a package for hello world, but of course they just couldn't leave well enough alone so it is multilanguage and will print out your mail as well :) ) is worth looking at.

codebase management and the ease with which it is done on unix and unix-like systems flows from this simple concept.

Unlike the proprietary works where walls are built and every install better have everything it needs or it might not work.

I am not biased, but I think the unix way is better  :-D

---

### Post by jrjazzman on 2006-11-02
> **bsussman said:**
> Since the beginning of time, unix has been a cooperative environment, meaning that many libraries were developed and used by many projects.  It makes no sense for everybody to invent a routing to do the same thing.


Thank you.  I think this makes some sense, and the advantages you discussed are pretty clear.  However, aren't there some pretty clear disadvantages also?  The idea of all libs being in one place reminds me of the dll hell days on windows.  COM and .NET fixed some of this by allowing programs to request specific versions of components.  In some ways I think linux does this also with symlinks.  A program can request a minimum or generic version by using the symlink, which usually points to a specific version.  This doesn't seem robust, although sometimes simple designs work really nicely.  

I'm not too familiar with the packaging systems yet, but it seems like they do not allow multiple versions.  You can "pin" to a specific version of a package, but you can't have multiple installed.  Am I right here?  If so, is this a reason for the fragility in doing major linux upgrades?  Most if not all distributions are pretty notorious for this; the most common thing to do is back your stuff up, then do a clean install.  

Of course, linux users tend to be serious system hackers, more so than  other OSs.. major manual modifications to libaries, etc.  The system upgrade process doesn't seem to be able to handle customizations such as installed packages outside of the official repositories, tarball installs, etc.  Most of the advice I've read is to uninstall any of these before you upgrade.  I guess this is why clean installs are more common - they're easier than trying to rolling back to a stock install before doing the upgrade.  

It's probably impossible to get statistics on failed upgrades (unless forum polls are scientific), but a lot of the reports point to the library and packaging system.  Package systems are a welcome imporvement to tarballs, but are they still the Achilles heel of linux?  Packages don't have UUIDs; I can declare that a certain package or library is a valid substitute for something that other packages depend on (is it the -supplies or -provides parameter?)  Awesome flexibility that you REALLY need unless you're ok with old versions of stuff in the offical repos, sub-par font rendering, etc.  Reminds me of the age old freedom vs. order debate... there's a balance to be struck.  

I'm still getting to know linux, so my comments are definitely based on igorance and incomplete information.

---

### Post by bodhi.zazen on 2006-11-02
> **jrjazzman said:**
> It's probably impossible to get statistics on failed upgrades (unless forum polls are scientific), ....

This is true, but not Linux specific. It applies to any OS. Try upgrading windows 98 to windows 2000 or windows 2000 to XP.

Major upgrades to an OS are not as smooth as backing up your data and starting with the new.

You can have different versions of some programs installed at the same time. It can get very messy.

Recent examples are running firefox version 2. You also may need to have different versions of gcc.

---

### Post by bsussman on 2006-11-03
> **jrjazzman said:**
>  In some ways I think linux does this also with symlinks. A program can request a minimum or generic version by using the symlink, which usually points to a specific version. This doesn't seem robust, although sometimes simple designs work really nicely. 

I do not see that much use of symlinks - more of the 'expected location of libs'. The exceptions seem to be things like php4/5 and apache/apache2. 

But builds can still require specific, non-generic libraries. The problems you describe do occur.  Have for many years (at least since the early 1990s.

> 

I'm not too familiar with the packaging systems yet, but it seems like they do not allow multiple versions. You can "pin" to a specific version of a package, but you can't have multiple installed. Am I right here?
Yes due to shared libs!
>  If so, is this a reason for the fragility in doing major linux upgrades? Most if not all distributions are pretty notorious for this; the most common thing to do is back your stuff up, then do a clean install. 
Dunno the statistics, but I suspect you are more right than not.

One of the issues preventing multiple simultaneous versions is the very nature of dynamic resolution.  If I have a program called bozofester in two versions, how shall I invoke one version instead of another.  If it needs a library called bogolib, how shall I write it to invoke one version of the libs rather than the other?  The common answer is static linking, which allows us to lock the invocation, at the cost of larger executables and lack of flexibility (like when we fix a bug in the lib, we need to relink the static mainline).
> 

Of course, linux users tend to be serious system hackers, more so than other OSs.. major manual modifications to libaries, etc. The system upgrade process doesn't seem to be able to handle customizations such as installed packages outside of the official repositories, tarball installs, etc. Most of the advice I've read is to uninstall any of these before you upgrade. I guess this is why clean installs are more common - they're easier than trying to rolling back to a stock install before doing the upgrade. 

It's probably impossible to get statistics on failed upgrades (unless forum polls are scientific), but a lot of the reports point to the library and packaging system. Package systems are a welcome imporvement to tarballs, but are they still the Achilles heel of linux? Packages don't have UUIDs; I can declare that a certain package or library is a valid substitute for something that other packages depend on (is it the -supplies or -provides parameter?) Awesome flexibility that you REALLY need unless you're ok with old versions of stuff in the offical repos, sub-par font rendering, etc. Reminds me of the age old freedom vs. order debate... there's a balance to be struck. 

I'm still getting to know linux, so my comments are definitely based on igorance and incomplete information.You are generally right on the mark. In a loose cooperative system like such as the Open Source Community, the hazards are there.

To a certain extent, the saving feature is that cooperators are more likely to work things out, surrounding a particular lib or family of libraries. A good example is the kde community. there are many projects, building to the libs and standards of the actual desktop manager's utility routines and libs. For example, the editor in quanta is kate and there are bridges tween them to coordinate at the project and software level.

The potential for foolishness or worse is there - this is why, for instance, debian is very conservative about release schedules.  ubuntu announced an intention to test hard and still be more timely with releases.

6.10 seems to be proving difficult.  the owners are trying to have it both ways - making a general release while suggesting that it is not a general release for everybody, only for those who do not mind a less that reliable codebase.  The traffic in these forums, the growing press, etc, seems to show that folks are discovering this.  It will be interesting to see who learns what.

In the old days it was easy - linux even numbered releases were meant for the masses and odd numbers were not.  And the socio-technical rules did not allow complaints from folks who ran the odd numbers and did'nt like the reliability :)

---

