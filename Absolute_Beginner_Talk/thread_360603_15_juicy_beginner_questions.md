---
title: "15 juicy beginner questions"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Pai on 2007-02-13
Over the past few days I've been playing around with my new setup, trying to get acquainted with Ubuntu for the first time.  Rather than posting every question I came across individually, I compiled the following list of questions.  Answer as many as you have time for or interest in. Thanks in advance.  

1. Pages are taking significantly longer to load than they did in Windows, almost as if I'm on a dial up connection. Yet download speeds are still 400+ kb/s.  I would understand if pages load slow on the first visit or two, but it has been over a week now.  Dapper was automatically connected to the internet, do I have to change some settings?

2. Firefox question: How do I access the Options?  On my Windows version of FF, the options appeared at the bottom of the Tools menu, but that is not the case now.  How do I change my connection settings, or homepage for example?

3. How difficult would it be to get Windows applications, such as Photoshop, running in Dapper?

4. Is there a Dapper equivalent to using ctrl+alt+del in Windows?  I think it is the System Monitor, right? Is there a keyboard shortcut to that?

5. Can I use Times New Roman, Arial, and other common fonts in Dapper?  I don't see them available when I create a new document, but when opening up a .doc I created back in XP, it was in Times and I was able to type new text in this font.

6. Why am I not the owner of this operating system? I just wanted to delete a folder of examples, and I am not able to. 
[img]http://img443.imageshack.us/img443/2572/permissionspnggr8.png[/img]

7. What is mounting? I read the description in the Ubuntu user manual, which stated that mounting media "makes the file system of the media available for access", but I'm not entirely sure what that means. It appears that by default, removable media is automatically mounted since my system recognized a flash drive of mine. Is that correct? Or does mounting add the contents of the removable media to my drive?

8. As an extension of question 7... what does unmounting do?  When I partitioned my drive while making the move to Ubuntu, I left a small recovery partition (provided by Dell) that I boot to instead of a CD if I want to reinstall XP. The location is "/media/sda3." This "DellRestore" drive appears on /home/*[name]*/Desktop with an option to "Unmount volume." What effect would this have? Can I remove this from my desktop?

9. How do you feel about Automatix?  I've kind of avoided this so far because I care to actually learn my way around Ubuntu, and it sounds like Automatix does a lot of the work for you.  Do you guys use/recommend it at all?  

10. What about EasyUbuntu: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
Excerpt from their site: "[i]EasyUbuntu is an easy to use (duh!) script that gives the Ubuntu user the most commonly requested apps, codecs, and tweaks that are not found in the base distribution - all with a few clicks of your mouse.

EasyUbuntu is so easy to use in fact, that even your grandma could be playing encrypted dvds, streaming Windows Media, and sporting the latest Nvidia or Ati drivers in minutes! And yes, EasyUbuntu is GPL.[/i]"

11. How can a command like "sudo aptitude install mozilla-thunderbird firefox gimp inkscape juk wine" actually work?  Not looking for a real specific answer. Apparently this is possible because of the repositories available, with the packages hosted there.  But how do you install a specific version of something, or control specific install instructions?  Sure it seems much more efficient than going through a windows installer, but I feel like I don't really have control or know exactly what I'm getting.  Are commands like these the preferred method of installing in general?

12. Why would anybody want to use **apt-get** instead of **aptitude**?  From what I've read, it sounds like they both do they same thing, except **aptitude** does a better job of handling dependencies.

13. Does an image editor come pre-installed **other than GIMP**, similar to MSPaint? I want something just for minor crops, that I used to do faster in Paint than I did in PS.  If not, is there one that you can recommend?

14. This evening the Software Updater told me that two updates were available, as seen below.  It appears that these updates are for FF1.5.*.., yet I'm currently using a version greater than FF2.0. What should I do?
 [img]http://img99.imageshack.us/img99/7312/screenshotsoftwareupdatot7.png[/img]

15.  I'm missing all sorts of FF plugins, but none are ever found.  What do I need to do about this? Example: 
[img]http://img211.imageshack.us/img211/2161/screenshotvo4.png[/img]

---

### Post by Alveric on 2007-02-13
Oh wow.

---

### Post by EvilMarshmallow on 2007-02-13
#3:  See winehq.com for an idea of windows programs running via WINE in Linux.  Sorry, no photoshop here... though there is an extension/plugin/thingy for the GIMP called "GIMPshop" which reorganizes the menus and whatnot to look more like PS.

#6:  "Root" is the super, above-all admin account to the computer.  By default, the Root account is disabled though, as you can do very nasty things to a computer with that kind of access.  Ubuntu uses sudo, a command that temporarily provides you with root access, to get at administrative tasks.  If you're typing something in the terminal and you get a message that you have to have root access to do it, just put sudo in front of it and it will prompt you for your password.

#7:  "Mounting" is the act of the operating system recognizing removable media.  It actually has to create a connection to the file system on the disk/flashdrive/cd/whatever and in the old days, you had to manually enable this by using the mount command.  Many types of media now autodetect the way they do in windows... but occasionally you'll run across one that requires you to manually mount the drive.  "Unmount" is equivalent to the "Safely remove hardware" feature in windows... it closes the file system down properly and disengages the media for removal.

#s 9 & 10:  Use them if you want.  Personally, I came to Linux to learn Linux.  I want to know as much as I can about it.  The desire for knowledge outweighed my impatience so I'm choosing to do it without Automatix or EasyUbuntu.  If you're in a hurry to get it up & running, try them out.  But you're missing some valuable education here... as you've seen since you switched, Linux is structured differently from Windows... and knowledge of how it's set up is certainly worth learning.

---

### Post by Brunellus on 2007-02-13
Good questions.  and there are answers.  It would have made sense to split them up into separate posts, though, as this makes for dense reading.

1) you'd probably have to disable ipv6 in firefox.  I believe it's in about:config, but search the forums for a better answer.

2) about:config has everything.  Options are still somewhere up in the menus--look around.  

3) Short answer is:  not on your life.  Long answer is:  use WINE.  Explanation to long answer:  WINE is a compatibility layer that allows you to use windows programs within Linux.  It is imperfect, and should be regarded as a last resort, in my opinion.  The preferable option is to use native applications wherever possible and save yourself the headaches.

4) usually, I ctrl+alt+F1 to get to a text console, log in there, and do whatever i need, including process killing.

5) See [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

6) you own everything in your home directory.  everything else is owned by root.  This prevents you from hosing your system by deleting key system files.  see [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

7) Linux and unix-type operating systems deal with disks as two things:  DEVICES and FILES.  as a DEVICE, the disk exists in the /dev filesystem (as, for instance, /dev/hda).  To make that device usable, you have to "mount" the device somewhere so that you can read and write to it.  Mounting attaches the device to a point somewhere in the filesystem (directory structure) that you can use.  Thus, you'd mount /dev/hda1 to /media/hda1 for instance.  Once you've done that, the files on that hard drive can be seen in the /media/hda1 directory.  

8) unmounting is the opposite.  It means that device is no longer an active part of your directory structure.  certain things can ONLY be done to unmounted partitions--filesystem checks and repairing corrupted data, for instance.  

9) I haven't used Automatix since before Dapper.  Ask them in their own forums.

10) EasyUbuntu is a fork of automatix.  I haven't used it.

11) yes.  If you trust the repositories, you trust apt.  Corrolary:  Do not add untrusted repositories to your /etc/apt/sources.list unless you really know what you're doing.

12) good question.  apt-get existed before aptitude, so many howtos continue to use apt-get.  Personally, I find it hard to break my apt-get habit because it's so much faster to type.  apt-get does not have a minesweeper game built into it, either.

13) Not by default.  Tuxpaint comes to mind.  But I use the GIMP, so I'm not fussed.

14) if you installed Firefox using Mozilla's tarball and script, it will not be handled by apt/synaptic.  anything you install outside ubuntu's package management system (deb/dpkg/apt) will not be handled by that system.  Maintaining it is your responsibility.  

15) see [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by az on 2007-02-13
1. Maybe dissable IPv6?  Try FasterFox extension?

3. You will be happier finding a free-libre alternative that was made to run on linux.  You can try to run some apps with wine, to emulate windows, but you will be dissapointed.

4. I always add the system monitor to my panel.  Just right-click on the upper panned and add stuff.

5. If you want the Microsoft fonts, install msttcorefonts from multiverse.  That being said, the bitstrream fonts are equivalent and free-libre.

6. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

7. In Unix, most things are treated like a file.  You can access your hardware as though it was part of your filesystem.  To mount a drive, is to assign the device a place in your filesystem to access it.  It can be whatever you want.

For convenience (and because that's what you expect to happen when you plug in a usb drive) removable media is automatically mounted when it is detected.  If it were not mounted, you would plug it in and nothing would happen.

Tree or four years ago, you would stick the drive into your box and then open up a terminal and run

mkdir /myusbdisk
mount  /dev/sda1 /mysubdisk
as root.  PITA.

8. Unmounting just disconnects the device from being accessed through your filesystem.

9. No comment. 

10. Automatix was based on EasyUbuntu.  I don't know how actively maintained it is these days, though.  Automatix was forked from EasyUbuntu, not the other way around.  Arnieboy had to have the GPL explained to him at one point regarding what he could and could not do.  That's why EasyUbuntu proudly states they are GPL-licenced.
See post number 40 of this: [http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629)


11. This is open source.  The software is excellent because it is distributed and built-upon by a large number of people who tackle specific areas of it.  Some of the software is incredibly innovative because of that.  There is no one person or company that decides what is best.  The community decides what is best.  In return the software can "turn on a dime" and adapt.  The only dissadvantage this offers to the end-user is that the way the different parts of the software interface is at the source code level.

To get the latest version of any software, you can compile it from source, and that gives you exceptional control over your system.  However, it's a friggin' nightmare to handle.  You risk breaking compatibility with part of your system because you upgraded another part of it and you did not have intimate knowledge of how they got along.

This is what distributions are for.  Your distribution takes a bunch of packages, tweaks them to run well and distributed them in binary (executable) form.  Everything is in a centralised repository.  Anything uploaded there is done so in source form and it gets compiled by the autobuilders.  This provides a lot of security.  Installing binary applications from third-party websites is a security risk.

12. Not really.  Aptitude can sometimes be overzealous.  Apt-get is more popular because it has more hooks built-in for use with frontends.  Apt is probably a bigger project and has more contributers than aptitude.  I think the developers of apt are more active in the debian culture than aptitude's (I dunno).
 

13. You can crop with F-spot.  I think it is the default photo viewer/manager in Feisty.

14. If you want to run the latest version of FF that you get from upstream, install it to your home drive so that you do not bork the package manager.

15.  You can use the totem mozilla plugin and then your media is played in totem.  I don't really know what the story is about liux plugins in firefox.

---

### Post by potterzot on 2007-02-13
Holy cow.  Maybe we should keep this around.

1. no idea

2. edit:preferences.  unless you are talking about advanced settings, accessible if you type about:config in the address bar

3. I recommend gimp instead of photoshop, but use synaptic to install wine and try it with that...this is a big big topic.

4. only thing I know of is to open a terminal and type ps -A.  gives you a list of all processes running.  you can also type top, which organizes them by memory usage.  To kill a process that has hung, type kill <process id number> in the terminal.  You can only kill processes owned by you unless you use sudo kill <#>

5. hmm...there are some similar ones called Nimbus.  Openoffice has them, but I don't know if they are easily usable as say the desktop fonts.

6. to delete folders not owned by you, use open a terminal and navigate there, and type sudo rm -r <folder name>.  You are probably getting this because ubuntu does not enable a root account by default and you are not root, so you don't own system folders.  It's a security measure and a slight pain in the ***, but it's fast once you figure it out.

7. mounting doesn't copy anything, it just adds the mounted item (e.g. usb flash drive) to a  location in the system.  it's just like when you insert a drive into a windows machine.  It actually is a lot more complicated for other stuff, but flash drives and cameras and cd's work pretty much the same as in windows.

8. if you unmount that drive, it just removes the location, but not the partition.  it is safe to remove the partition if you won't use windows again (I think).  just as mounting doesn't copy, unmounting doesn't delete, it just removes the location of the drive on your system.  you could remount it by typing mount /media/sda3 /home/<you>/dell or something.

9. if automatix is the thing that downloads all the restricted content stuff, it might be nice if you are a beginning user of linux.  I ahven't used it.  benefit of doing it yourself is you would know what you are downloading/installing (e.g. mp3 codec, flash player, etc...)

10. no idea

11. this could be a long long answer, but simply, it is a database of applications and the dependencies (other applications).  when you type that command, aptitude finds the latest version in your sources and downloads and install it.  it is easy to uninstall (use remove/purge instead of install).  I haven't trying to use version control with apt, but I'm pretty sure you can.

12. don't know

13. diddo

14. hmm.  in edgy, 2 is the standard I think.  not sure what this is.  if you had installed 2.0 independent of using apt, then apt will still think that the previous other version should be updated.

15. search in synaptic for firefox, you'll find some of them.  flash and quicktime come to mind, I think they are both in the sources.  make sure you have universe,multiverse, etc... enabled in your apt source files (/etc/apt/sources.list)

phew!

---

### Post by deanlinkous on 2007-02-13
> 1. Pages are taking significantly longer to load than they did in Windows, almost as if I'm on a dial up connection. Yet download speeds are still 400+ kb/s.  I would understand if pages load slow on the first visit or two, but it has been over a week now.  Dapper was automatically connected to the internet, do I have to change some settings?
You might try this
1)open firefox
2)type **about:config**
3)type **ipv6** in the filter field
4)you should have a line that starts with network.dns.disableIPv6 if the VALUE on the right side is set to FALSE then double click anywhere on the line to set it to TRUE
5)restart firefox and see if it helps

> 2. Firefox question: How do I access the Options?  On my Windows version of FF, the options appeared at the bottom of the Tools menu, but that is not the case now.  How do I change my connection settings, or homepage for example?
edit>>preferences

> 3. How difficult would it be to get Windows applications, such as Photoshop, running in Dapper? Sorry if I want windows programs I will use windows. You may want to look for a package called GimpShop though.

> 4. Is there a Dapper equivalent to using ctrl+alt+del in Windows?  I think it is the System Monitor, right? Is there a keyboard shortcut to that? System>>Administration 

> 5. Can I use Times New Roman, Arial, and other common fonts in Dapper?  I don't see them available when I create a new document, but when opening up a .doc I created back in XP, it was in Times and I was able to type new text in this font.
Search the repos for fonts.SHould be some "common" fonts available if you want them. 

> 6. Why am I not the owner of this operating system? I just wanted to delete a folder of examples, and I am not able to. 

Because the most powerful account on your system is probably the owner. You can learn about sudo if you want to have a way to access that power account. 
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

> 7. What is mounting? I read the description in the Ubuntu user manual, which stated that mounting media "makes the file system of the media available for access", but I'm not entirely sure what that means. It appears that by default, removable media is automatically mounted since my system recognized a flash drive of mine. Is that correct? Or does mounting add the contents of the removable media to my drive?Often removable media is auto-mounted which simply means it is "seen" by the operating system and it is accessible.

> 8. As an extension of question 7... what does unmounting do?  When I partitioned my drive while making the move to Ubuntu, I left a small recovery partition (provided by Dell) that I boot to instead of a CD if I want to reinstall XP. The location is "/media/sda3." This "DellRestore" drive appears on /home/*[name]*/Desktop with an option to "Unmount volume." What effect would this have? Can I remove this from my desktop?It simply means that the operating system will not "see" it and it will not be accesible.

> 9. How do you feel about Automatix?  I've kind of avoided this so far because I care to actually learn my way around Ubuntu, and it sounds like Automatix does a lot of the work for you.  Do you guys use/recommend it at all?   I don't use it. I don't recommend it. If it does any work for me then I guess I am slacking because I havent done any and I havent used it. :D

> 10. What about EasyUbuntu: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
Excerpt from their site: "[i]EasyUbuntu is an easy to use (duh!) script that gives the Ubuntu user the most commonly requested apps, codecs, and tweaks that are not found in the base distribution - all with a few clicks of your mouse. Sorry but what I want installed I will install myself. I do not need to trust others or depend on others to provide for me. 
> 
EasyUbuntu is so easy to use in fact, that even your grandma could be playing encrypted dvds, streaming Windows Media, and sporting the latest Nvidia or Ati drivers in minutes! And yes, EasyUbuntu is GPL.no comment

> 11. How can a command like "sudo aptitude install mozilla-thunderbird firefox gimp inkscape juk wine" actually work?  Not looking for a real specific answer. Apparently this is possible because of the repositories available, with the packages hosted there.  But how do you install a specific version of something, or control specific install instructions?  Sure it seems much more efficient than going through a windows installer, but I feel like I don't really have control or know exactly what I'm getting.  Are commands like these the preferred method of installing in general?Sure you have control, do you have the knowledge and skill needed to use this control? If not, stick with a package. :)

> 12. Why would anybody want to use **apt-get** instead of **aptitude**?  From what I've read, it sounds like they both do they same thing, except **aptitude** does a better job of handling dependencies. Get your aptitude off my dependencies please. :) Well, aptitude doesnt work without apt so at least some of aptitudes yumminess comes from apt. I use apt.

> 13. Does an image editor come pre-installed **other than GIMP**, similar to MSPaint? I want something just for minor crops, that I used to do faster in Paint than I did in PS.  If not, is there one that you can recommend?gThumb should be installed and should do this.

> 14. This evening the Software Updater told me that two updates were available, as seen below.  It appears that these updates are for FF1.5.*.., yet I'm currently using a version greater than FF2.0. What should I do? weird....


> 15.  I'm missing all sorts of FF plugins, but none are ever found.  What do I need to do about this? Example: 

Personally I would install totem-xine-firefox-plugin and there are others packages to install that should provide most media formats.


next....... :D

---

### Post by Rhubarb on 2007-02-13
Wow, what a nice helpful community.
I can't seem to offer any help here, as you've all beaten me to it!
Well done everyone :KS

---

### Post by igknighted on 2007-02-13
1) Sounds like ipv6 isn't disabled.  Not sure how to disable it though.

2) I believe edit -> preferences is what you want.  Might have moved w/ FF2, hence the difference you see.

3) You could try wine, I dont know if photoshop runs on it tho.  I think, unless you are doing something VERY specific, GIMP can fulfill your needs.  Give it a shot and see what it does.  You could also try crossover to get photoshop working if you really need it, but that is a commercial program and costs money.

4) I know automatix can set up that shortcut for you, if you go to system -> preferences -> keyboard shortcuts you might be able to designate one there.

5) Yes, there is a package with MS ttf fonts, I know automatix installs it, I don't know the exact package name however.

6) You can make yourself temporarily the sys-admin with the 'sudo' command before any command you give, but you are not the owner for a reason.  In normal day to day operations you don't need to mess with system files, and leaving them editable would make your system vulnerable to hackers/malware/viruses/etc.  It takes some time to get used to, but its one of the reasons linux is far more secure than windows.

7) Mounting a drive is something that is done in all OSes, but most just gloss over the fact.  Basically what happens is the OS needs to set an access point to the file system before you can access it.  In windows, if you plug in a USB drive it shows up as F:/ or something similar.  It was mounted there.  When you click "safely remove hardware" it unmounts it, or shuts and locks the door.  Ubuntu does the same thing, but you get to pick the mount point.  Typically, /media/<pick a name> is used for removable media, and /mnt/<pick a name> is used for local media (other HDs, partitions, etc.).  If you for some reason wanted to disconnect a drive (to remove it, or god knows what other reasons) you would unmount it.

8) This might be a reason to unmount.  If you unmount you wont be able to browse that partition, but that seems to be what you would want.  To permanently do this, remove the line refering to /dev/sda3 from your /etc/fstab file (to access it, type in a terminal 'gksudo gedit /etc/fstab'.)

9) If you feel like learning the system don't use it, but its always there as a backup if you want it.  I don't use it normally, but there are some nice things it does (like the ctrl-alt-del shortcut)

10) Use automatix over easyubuntu, more choices and better coded I feel.

11) There is in fact a repository (several, actually) that hold all this software.  It allows you not to worry about downloading software that could be hazardous to your system.  People online only tend to post the install command, but if you use synaptic (it is a GUI frontend to the same system) you can get more details regarding the packages in question.  Also apt-cache search <package> will give you more info on it as well.  This is the preffered install method.  It takes care of making sure any dependencies are fullfilled so your programs work properly.  You can always add 3rd party repo's, or install software from other sources.  This is less secure, but does expand your options.

12) This is true, but many find apt-get easier to type, and its new/not standard in some other ditro's, so a lot of people don't know it exists.

13) dunno on this one, try browsing synaptic and seeing if you find one you like.  add/remove software might also be a place to try.

14) or this one

15) You need to install mplayer-plugins, sun-java5-plugin and the flash plugin (I always get it from the adobe site).  Automatix will install these for you if you want, or you can check [www.psychocats.net](www.psychocats.net) for more info on doing it yourself.

Hope this helps, welcome aboard!

---

