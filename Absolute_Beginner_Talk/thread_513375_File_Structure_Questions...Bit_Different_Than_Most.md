---
title: "File Structure Questions...Bit Different Than Most &quot;File Structure&quot; Posts"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by bunnyfly on 2007-07-30
Hello - I am quite new to Linux and have been baffled by the directory structure. I've slowly begun to understand it a LITTLE - but have some questions that haven't been answered by any of the posts/articles I've read.

#1 - Why are there so many "bin" directories and what determines where a program will install? In Windows and from what I've seen of Mac (I know I know it uses Unix underneath, but they do a commendable job of hiding it.) all of the applications get their own directory and all of those directories are in one place. In Linux, it seems as though I have programs scattered all over the place in various bins that have no correlation to where their configuration files are. I'm constantly frustrated trying to find configuration or readme files because once I've found which bin a program is in by editing the Gnome menu and peeking at an apps' properties and command line, then I have to spend 10 minutes rooting (hehe) through the directories trying to find their files. I tried doing a Nautilus search...but sometimes the files just don't pop up because they're named differently. So now, the most reliable (although pathetically tedious) way I've found is to go into Symantics and look through all of the files that a package installed.

Is there truly no consistency to where a program will sprawl its files out across my hard drive like a drunkard on a couch, or is there a magical formula that I don't know?

#2 - Also - if every drive, cd rom, and floppy is loaded as a mounted subdirectory of the root folder, how come I have files, or even folders for that matter at the level of "/"...since I have only one hard drive, shouldn't every single file I have be under /hd1/ or something like that? Why do I have a /bin/ or /home/usr/ instead of /hd1/bin/ and /hd1/usr/? What determines a folder's physical location when it is outside of the mnt or media? And what determines if it is outside of media?

3# - Can I trust that when I delete a package, that it will remove all of its files? If I, after journeying out to locate an apps' estranged configuration file, make a copy of it (app.config and app.config.backup), will that be removed by the package manager? In Windows the occasional left over file can be easily spotted and deleted because the vast majority of an apps files are in one folder in one place...and you delete it if it's left over after an uninstall. It seems as though while Windows is going to leak ram and cpu cycles over time with a million tiny loose ends, Linux is going to eat up my hd over time with a million tiny loose ends. Rational fear? Or confused newbie?

4# - And - don't hate me for this one! Is there a way to make Linux's directory structure less transparent? Is there a package available that will make it appear that ALL of my applications are in one directory, with their configuration and support files in close proximity like Windows or Mac?

Thank you for reading and helping.
[bunnyfly]

---

### Post by Inxsible on 2007-07-30
1) The only bin directory that I have ever had to worry about is the /usr/bin where all the program executables are stored by default (forgive me for the wording there) but what I mean is that when you need an application to start, thats where you look for it. You can simply choose to ignore the rest. just like I am sure you dont worry too much as to what goes into your System and System32 folders under the Windows folder.

2) You forget, that when you say /home you are including the root folder (denoted by /).
So everything is under root (/) unless you have created separate partitions for home under which case it is simply accessing a different drive/partition.

3) If you manually create a .backup file, I dont think it will remove that on uninstall. In Windows too, if i copy a file to another location, it wont remove it when I remove the application. But the fact that you are creating a backup means that you intentionally want another copy, lest something happen to the original one, so you can revert back.

---

### Post by aysiu on 2007-07-30
These links should help:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://www.gobolinux.org/](http://www.gobolinux.org/)

As for the devices, they usually get mounted within the /media directory. In Mac, they get mounted to /Volumes. Windows is the only major desktop OS that decides to assign a different letter drive to each drive (C:\, D:\, E:\, etc.).

---

### Post by Toet on 2007-07-30
[http://www.faqs.org/docs/linux_admin/dir-tree-overview.html](http://www.faqs.org/docs/linux_admin/dir-tree-overview.html)

---

### Post by Nekiruhs on 2007-07-30
/media and /mnt are for non essential media. Meaning if you make a seperate partition for /home, it would still be .home not /hdb2/home. /media and /mnt are for storage media. All configuration files are under ~/ (your home folder). If you use synaptic to remove a program you can mark to completely remove it and that removes unnessecary dependencies and config files.  When you enter a command in the terminal, notice how it just "knows" where the program is? Thats because the program is in the PATH setting. Thats what all those bin folders are for (bin = binary = executable). If you want to see all of them, type in a terminal echo $PATH . /etc is for Editable Text Configuration (Thats for OS wide configuration, like xorg etc). USR = Unix System Resources. You get used to the file system eventually, but if it really gets on your nerves, try Gobo Linux, it has a more OSX like FS.

EDIT: .... Too slow again.

---

### Post by asmoore82 on 2007-07-30
> **bunnyfly said:**
> Is there truly no consistency to where a program will sprawl its files out across my hard drive like a drunkard on a couch, or is there a magical formula that I don't know?

:D Yes.

But seriously, here is a quick list of that those directories are intended for...

/ - the 'root' filesystem; it is a LAW of UNIX machines that no files exist outside of the root filesystem, even if they are physically located on other partitions/drives/media;
hence the ability to attach or **mount** other filesystems *anywhere* **under** the root filesystem.

/bin - all the foundation programs of the os are here, things that most users don't even realize
are separate programs; one to copy a file, another to move a file, yet another to delete a file.

/boot - the the data needed to boot the system; it was common in the old days for this to actually be a small (50~100 MB) partition at the beginning of the hard drive to workaround
BIOS problems. (old BIOSes couldn't read beyond 1024 cylinders and the problem woudn't
manifest itself until after a major system upgrade placed the kernel and other boot files
beyond that barrier.

/etc - system settings - the place for a lot of tweaking and/or breaking; home of
everyone's favorite file xorg.conf :evil:

/dev - all the 'device' files belong here; it is a LAW of UNIX that all Input/Ouput be handled as
files to make programmers lives easier. all the files in /dev correspond to devices but the programmers just have to read/write these files to manipulate the devices.

/home - place for users's personal data

/lib - the shared code for the foundation programs in /bin and /sbin. lots of files ending in '.so'
roughly equivalent to dlls on windoze ( DLL="Dynamic Link Library", SO="Shared Object" )
either way they are common pieces of other user programs.

/media - the new, 'user-friendly' /mnt; (same stuff, different name :))

/mnt - the old '/media' :P - even though foreign filesystems *can* be attached or **mounted** anywhere; this is the politically correct place for them.

/opt - the non-UNIX style software directory - if an application demands that all of it's program files be in one place Windoze style, this is where it should be installed; very few Linux programs are like this, so the intended purpose of /opt has faded into obscurity*

/proc - files in here don't really exist :shock: - it is a mountpoint for the procfilesystem, a window into the Matrix, a place to directly communicate with your running Linux kernel.
type 'cat /proc/cpuinfo' in a terminal to see what Linux thinks of your processing power.

/root - root's home directory - off limits to everyone but me :ninja:

/sbin - like /bin but specifically for lowlevel system administration. most programs in here aren't very usefull without root permission.

/sys - i'm not sure - sort of like an uber-modern /dev and window to the Matrix.

/tmp - short term environment data - the place for volitile information**, writable to everyone.

/var - long term environment data - a place for programs to store misc. stuff; but a lot less
volitile - programs can and do rely on this info still being there after a reboot. If you nuke
all the stuff in here the Linux kernel will still run like a dream, but the rest of the software
that makes up your Desktop OS will flop around like a wounded animal.

/usr - I saved this for last - the "second level" of the OS. All programs that have a GUI will be in here. this folder mimics the contents of the root folder....
/usr/bin - like /bin but with pretty graphics.
/usr/lib - like /lib but with pretty graphics.
/usr/sbin - like /sbin but with pretty graphics.
/usr/src - the place for SOURCE CODE; the DNA of all Free and Open Source Software
/usr/share - the place for fun stuff like system-wide sound effects/icons/documentation
/usr/local - a whole other beast - the place for machine dependent data - custom compiled stuff that can't be reliably transplanted to another computer even with the same Linux distro.

------------------------------
whew - all who have read this far now know too much and must break off
all further communication with Micro$oft Corporation.

anyways, there are many reasons that a single application's files
will be spread across multiple directories like /usr/lib and /usr/bin ...
I will try to name a few most important ones:

1. it is much more important and coherent to place individual files by their individual
purpose and not by which App Package they "belong" to - you would think micro$oft
would have developed a deeper appreciation for this since their OSes are so easily
fooled by changing extensions.
2. beyond the shallow reason in #1, it is very important for all binaries (or executables) to be in a
central location so that we can give the end-user a PATH - more on this later
3. beyond the shallow reason in # 1, it is very important for all runtime library data (or shared ojbects) to be in a central location so that everyone can access it. Open Source is all about Sharing.


I can't type anymore at one time.....

-------------------------
* archlinux is a modern Linux distro that makes use of '/opt' - such as
/opt/mozilla for firefox
/opt/gnome for GNOME/gdm
/opt/openoffice for OpenOffice.org
/opt/bin for linking to various apps in /opt

and this is where PATH comes in to play

Micro$oft tries to create a coherent user environment by letting programs
install in their own little folders scattered all over creation but placing shortcuts
to various programs in the Start Menu. the "coherence" of the UI breaks down as
soon as you open 'CMD' - there is no real User Environment underneath it all

Linux users can open a terminal and run any program on their system by simply
typing the name of its binary/executable/frontend ... the user need not know where it is
this is because of the PATH environment variable which on my Ubuntu 7.04 is ...
```
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

archlinux is a slick distro but you have to update your PATH when you install new apps
in /opt if you want to be able to run them from terminals in the future.

so the answer to original question #4 is that the Command Line User Environment is a 'catch-all'
i.e. to see every single binary that is available to normal users, log in as a normal user,
open a terminal, and hit [Tab] a few times.

**on some distros, including archlinux, /tmp is a mounted tmpfs filesystem for performance.
I.E. these files only exist in RAM and will never be written to Disk.
So you can be sure that these files will be long gone after a reboot.

---

### Post by asmoore82 on 2007-07-30
:popcorn: bump

---

### Post by bunnyfly on 2007-07-30
Wow - thank you for all of your generous replies. More than I expected!

Inxible, I'll try to take your advice and look to /usr/bin first...asmoore82's advice seems to confirm this - since most gui apps should be here?

Nekiruhs, thanks for the acronyms - I assumed etc and usr were etcetera and user...makes a bit more sense now. I'm going to try to learn it. Why switch to Linux if I'm just going to get it to run like another OS?...I'm sure eventually I'll understand...or at least learn what masses of tangles to ignore and what bits of Linux to focus on.

asmoore82, wow - more than I bargained for. Much of the "directory list" I'd already seen - but your definitions made more practical sense...it seems then that basically - command line tools are in /bin, gui apps are in /usr/bin? And I can ignore the dozens of 'sbin's and /usr/local/ mazes.

It did impress me that I never have to navigate to a program's path to run it - that I suppose is one good thing about it. I remember whenever I'd jump out of Windows 3.11 and I'd spend hours trying to cd my way through DOS. Although - it seems as though DOS and Windows are more friendly in differentiating between a directory and a file!

I don't think I'd leave Ubuntu for another distro just because of the file system (especially considering this hodge podgery is almost universal in the Linux world, I might as well learn it)...but your replies do make things seem a little less messy. I think I might try to go into Nautilus and set up sidebar shortcuts to some directories and decryptify the names with all of your help. Thanks,
[bunnyfly]

---

### Post by lisati on 2007-07-30
> **bunnyfly said:**
> 
#1 - Why are there so many "bin" directories and what determines where a program will install? In Windows and from what I've seen of Mac (I know I know it uses Unix underneath, but they do a commendable job of hiding it.) all of the applications get their own directory and all of those directories are in one place. In Linux, it seems as though I have programs scattered all over the place in various bins that have no correlation to where their configuration files are. I'm constantly frustrated trying to find configuration or readme files because once I've found which bin a program is in by editing the Gnome menu and peeking at an apps' properties and command line, then I have to spend 10 minutes rooting (hehe) through the directories trying to find their files. I tried doing a Nautilus search...but sometimes the files just don't pop up because they're named differently. So now, the most reliable (although pathetically tedious) way I've found is to go into Symantics and look through all of the files that a package installed.

Is there truly no consistency to where a program will sprawl its files out across my hard drive like a drunkard on a couch, or is there a magical formula that I don't know?



 Where a particular file goes depends on the particular program's needs and the way the installer was designed.

My own preference is for each program having its own folder, in some ways similar to /usr/bin on Linux and "Program files" on Windoze, and not touching the OS's system folders if I can possibly avoid it. This can help heaps when tidying up if you change your mind about having a program on your system - in the unlikely event the need for a brute force "delete entire directory, files and all" arises to remove a program it saves having to wade through several folders trying to work out which files you can safely delete and which you need to keep.

---

### Post by lisati on 2007-07-30
> **lisati said:**
> Where a particular file goes depends on the particular program's needs and the way the installer was designed.

My own preference is for each program having its own folder, in some ways similar to /usr/bin on Linux and "Program files" on Windoze, and not touching the OS's system folders if I can possibly avoid it. This can help heaps when tidying up if you change your mind about having a program on your system - in the unlikely event the need for a brute force "delete entire directory, files and all" arises to remove a program it saves having to wade through several folders trying to work out which files you can safely delete and which you need to keep.

p.s. good observations by others about the need to have files in a place that you (and your choice of OS) can find them

---

### Post by aysiu on 2007-07-30
> **bunnyfly said:**
> 
It did impress me that I never have to navigate to a program's path to run it - that I suppose is one good thing about it. I remember whenever I'd jump out of Windows 3.11 and I'd spend hours trying to cd my way through DOS. Although - it seems as though DOS and Windows are more friendly in differentiating between a directory and a file! In all fairness, this can be done in Windows XP as well. Press Win+R and type the name of the program you want to run--you don't need the path. You can do ```
firefox
``` instead of ```
C:\Program Files\Mozilla Firefox\firefox.exe
```

---

### Post by asmoore82 on 2007-07-31
> **aysiu said:**
> In all fairness, this can be done in Windows XP as well. Press Win+R and type the name of the program you want to run--you don't need the path. You can do ```
firefox
``` instead of ```
C:\Program Files\Mozilla Firefox\firefox.exe
```

this is exactly the type of inconsistency I was talking about ...

"Run" :>firefox works but makes firefox's **current working directory** your Desktop.

but "$HOME" :> firefox in CMD causes ...
> 'firefox' is not recognized as an internal or external command,
operable progam or batch file.

running firefox in all Linux terminal's works AND sets firefox's **CWD** appropriately.

(the GIMP behaves much nicer when it's **CWD** is your pictures folder :))

---

### Post by LaRoza on 2007-07-31
As to the different file system, you get used to it, I am most displeased with the Windows way, because I am used to Linux, and Windows, but Linux is easier for me.

---

### Post by capink on 2007-07-31
> Is there truly no consistency to where a program will sprawl its files out across my hard drive like a drunkard on a couch, or is there a magical formula that I don't know?

an easy way to know where all the files belonging to a certain package are located is to type the following command at the terminal:

```
dpkg --listfiles packagename
```

---

