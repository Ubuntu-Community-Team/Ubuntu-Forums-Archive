---
title: "Win to Ubuntu -&gt; Filesystem tutorial"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Garyu on 2006-09-16
When I first tried out Ubuntu I found the file system very confusing. I had been using Windows (and DOS) for about 15 years and also used to work as a programmer, so I was very familiar with the windows directory structure. In Ubuntu, however, I felt totally lost and I couldn't find anything I wanted to find. Now that I have progressed somewhat I figured that a tutorial for new users might be handy.

While I am using windows directories as comparison, you don't need to know anything about windows to understand the unix/linux/ubuntu filesystem. The comparisons are just there to make it even easier for windows-users to understand the differences.

**/**
In Ubuntu the top-level directory is called "root" (the same name is used for top-level user as well). In windows you often refer to physical drives as "C:" or "A:" and if you connect to a network drive it also gets a letter like "X:". In Ubuntu there are no drives in this sense, everything is incorporated in the same directory structure. You may think of the root directory kind of like "My Computer" in Windows XP. It is the top of the pyramid, the root of the tree.

**/bin**
This is the place for basic system binaries. Binaries are programs/applications. You will for example find basic terminal commands like "cp" (copy), "rm" (delete), "ls" (list) and so on. It is similar to the "c:\command.com" in DOS and Windows environment.

**/boot**
Ubuntu comes installed with GRUB which is a boot loader that lets you select which OS (like win or ubuntu) you want to start when powering on your computer. Settings for GRUB are stored in /boot/grub/menu.lst which is kind of similar to autoexec.bat in DOS or old Windows. When you select your kernel to start it is loaded from the vmlinuz.img and other files located in /boot which then proceeds to load the system from /usr.

**/dev**
Devices in Ubuntu exist here as files. For example, the hard drive is a device stored in /dev/hda with the first partition at /dev/hda1 (on some systems /dev/hda is cd-rom and /dev/hdb is hard drive, an added physical drive would be /dev/hdc and so on). /dev/tty is what is displayed on screen (or in a terminal). Sound device will be in /dev/snd/.

**/etc**
This is where all configuration files should go. For instance, /etc/fstab is where the file system is configured, which drives are mounted where. In Windows this can be compared to .ini-files or maybe the windows registry (or the regedit and sysedit commands in windows). The configuration for X (the window manager) is located in /etc/X11.

**/home**
Home of all user directories, which in turn hold the home for each user. This is kind of similar to "My Documents" in Windows, but it also contains user-specific settings (like what theme you like, what icons to use, e-mail settings, and so on). To avoid clutter, all of the files and folders in your home (/home/username) that deal with settings have names that start with a dot (i.e. ".face"). The dot as a first character in the filename makes it hidden, so you have to choose to display hidden files in Nautilus if you want to see them. If you use wine to install windows-programs they will end up in /home/username/.wine/drive_c/ which is interpreted as "C:" by windows software. The home directory may also be referenced as ~ (the tilde sign), i.e. "~/.wine/drive_c".

**/lib**
Shared libraries. In Windows these are DLL-files (.dll) but in unix/linux/Ubuntu they are called libraries. For example, this is where you will find drivers for graphics cards and such things.

**/media**
This is the mounting point for removable devices such as floppies and cd-roms. In Windows you might have always had floppies at "A:" and cd's/dvd's at "D:" but in Ubuntu you will find the floppy at "/media/floppy" and the cd at "/media/cd-rom".

**/mnt**
This is the mounting point for filesystems, i.e. if you use smbfs to mount a network share on a windows computer (i.e. "/mnt/laptop"). In Windows this would be a drive letter like "X:".

**/opt**
Opt is a public place to put application software. Applications that are installed here may be shared with other computers on a network. This is kind of similar to "C:\Program Files\" in Windows.

**/root**
This is just an empty directory in Ubuntu. Actually it is the root user home, instead of "/home/root", but the root user is not active in Ubuntu, we use "sudo" with our own username instead.

**/sbin**
System binaries. Kind of similar to "C:\Windows\System" or "C:\MSDOS" in older versions of Microsoft OS's. This is the place for commands that deal with network configuration, hard disk partitioning or other a little more advanced system tasks.

**/srv**
Services. This one is usually empty in Ubuntu.

**/tmp**
Temporary files. This is for example where Firefox will put pdf-files when you view them from the internet.

**/usr**
Unix System Resources (USR is not "user"). This is where software/applications are installed by default for use by all users on the computer. Some programs (like the game Americas Army) will assume that you are the only user when installed so they will install in your home directory instead of here. The /usr directory could be compared to the "C:\Program Files\" but it also includes "C:\Windows" as the X window server is installed in "/usr/X11R6". In "/usr/src" and "/usr/local/src" and "/usr/include" you will find source files for building/compiling the linux kernel and other software (if installed). "/usr/bin" will contain most terminal commands/applications so this directory is actually the one most similar to "C:\Program Files" in Windows. If you look through "/usr/share" you will find icons, wallpapers and other static data used by applications.

**/var**
Variable files like game scores, system log files, samba passwords... Basically information files that are read by applications.


More information can be found at the homepage of the File Hierarchy Standard: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)


If you find it difficult to find something, you are probably stuck in your old windows-way of thinking. 

In Windows, if you installed a piece of software you would most often find it in "C:\Program Files\Appname", and in this single directory you would find all of the files associated with this piece of software.

In Ubuntu/linux, if you insall "Appname" you will have the executables/binaries in "/usr/bin" (or "/usr/games" if it is a game). Then you will have the application settings in "/etc/appname". Then you will have the application data, such as game scores or whatever in "/var/games" (if it is a game). Also, there might be some user-specific settings for your application stored in your home directory as "/home/username/.appname"

And, to make it even more confusing for a new user, some apps will just install in your home directory (/home/username). Where did that windows-application install that you can't seem to find? Try to look for */home/username/.wine/drive_c/Program\ Files/appname*

***Usually ***though, the only directory you will use is your **/home/username**. Sometimes you might want to change something in **/etc** or maybe **/usr** and maybe you will have some media or disk mounted at **/media** or **/mnt**, but other than that you will probably never look at the other directories, they are simply there for the system.

I hope this helps to clear things up for some of you. :cool:

---

### Post by Lord Illidan on 2006-09-16
A correction, if I may..

/home/username is the home directory for the specific user.. /home is the overall directory...

like.. /home is Documents and Settings
/home/illidan is Illidan / My Documents..

Otherwise, very clear tutorial.=D>

---

### Post by Anonii on 2006-09-16
Something trickier <:
Whats /proc? 
(I'd like to ask some more questions like the difference between /dev/null and /dev/zero, but this will only confuse things up.)

---

### Post by Lord Illidan on 2006-09-16
> **Anonii said:**
> Something trickier <:
Whats /proc? 
(I'd like to ask some more questions like the difference between /dev/null and /dev/zero, but this will only confuse things up.)

Good question.
[http://en.wikipedia.org/wiki//proc](http://en.wikipedia.org/wiki//proc)

*On [Unix]("http://en.wikipedia.org/wiki/Unix")-like computer systems, **procfs**, short for [process]("http://en.wikipedia.org/wiki/Process_%28computing%29") [filesystem]("http://en.wikipedia.org/wiki/Filesystem"), is a pseudo-filesystem used to access process information from the [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29"). The filesystem is often mounted as a /proc [directory]("http://en.wikipedia.org/wiki/Directory_%28file_systems%29"). Because /proc is not a real file system, it consumes no storage space and only a limited amount of memory.*
 *procfs is supported under [Solaris]("http://en.wikipedia.org/wiki/Solaris_Operating_Environment"), [BSD]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution") and [Linux]("http://en.wikipedia.org/wiki/Linux"); the latter also extends it to non-process-related data.*


*Under Linux, /proc provides information on any running process at /proc/PID, but in addition to that it also includes:*
 [LIST]
[*]*A symbolic link to the current (traversing) process at /proc/self*
[*]*Information on hardware, kernel, and module configuration*
[*]*Access to dynamically-configurable kernel options under /proc/sys*
[*]*Information about the system as a whole, such as [/proc/meminfo]("http://en.wikipedia.org/wiki//proc/meminfo"), which provides memory statistics.*[/LIST] *The basic utilities that use /proc under Linux are in the [procps]("http://en.wikipedia.org/w/index.php?title=Procps&action=edit") package, and they require that /proc is mounted in order to function.*
 *The procfs plays an important role in moving functionality from [kernel mode]("http://en.wikipedia.org/wiki/Kernel_mode") to [user mode]("http://en.wikipedia.org/wiki/User_mode"). For example the [GNU]("http://en.wikipedia.org/wiki/GNU") version of [ps]("http://en.wikipedia.org/wiki/Ps_%28Unix%29") operates entirely in user mode, using the procfs to obtain its data.*
 *In [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") 2.6, much of the non-process related files under /proc were moved to a separate pseudo-filesystem called **[sysfs]("http://en.wikipedia.org/wiki/Sysfs") (mounted under /sys).*


[http://en.wikipedia.org/wiki/Dev/null](http://en.wikipedia.org/wiki/Dev/null)

is very different from

[http://en.wikipedia.org/wiki//dev/zero](http://en.wikipedia.org/wiki//dev/zero)

---

### Post by xpod on 2006-09-16
> If you find it difficult to find something, you are probably stuck in your old windows-way of thinking. 

Good stuff..
I only used windows for a few months before destiny brought me here but i did learn all about those DLL`s......I had enough of the bloody things "missing or corrupt" everytime i run "sfc /scannow":biggrin: 

good guide though

---

### Post by xyz on 2006-09-16
Thanks [b]  	
Garyu[/b]
Regarless of the Linux/Windows comparison, your descriptions/explanations help me get a clearer picture of 'the tree'.

---

### Post by snakyjake on 2006-09-16
This is awesome work!  Thank you for doing this.  I have a few places that might be a bit confusing with the wording.  They both say "system binaries".  Maybe /bin is really like "system commands"?

> 
/bin
This is the place for system binaries.

/sbin
System binaries.

---

### Post by Garyu on 2006-09-17
> **snakyjake said:**
> This is awesome work!  Thank you for doing this.  I have a few places that might be a bit confusing with the wording.  They both say "system binaries".  Maybe /bin is really like "system commands"?

Actually, they are both for system binaries, but on different levels. /bin is more basic commands used by shells and so on, like ls, cd, mkdir. /sbin is more advanced commands such as ifconfig (for network), commands for resizing filesystems, alsactl for sound, and so on.

I will try to make this more clear later when I am not too busy which I am right now.

---

### Post by Pumm4 on 2006-09-17
Very nice tutorial **Garyu**. New Linux users need more guides like this.

---

### Post by buffy^ on 2006-09-17
I have to say reading that all I keep saying was "ahhhhhhhhhhhhhh" as I had one reverlation after another, thats very much for taking the time to clear alot of things up for me. I feel I had a basic knowledge of the tree, but you clear so much unknow ground for me there.

---

### Post by Garyu on 2006-09-25
*bump* (just checking if someone missed this)

---

### Post by bodhi.zazen on 2006-09-25
[O'Reilly Online Guide - Debian](http://oreilly.com/catalog/debian/chapter/book/)

[Linux Directory Tree](http://oreilly.com/catalog/debian/chapter/book/appa_01.html)

:cool:

---

### Post by xpod on 2006-09-25
Spoilsport...I quite liked his own guide,NOW you go giving me more to read:D

EDIT...AND i prefer "aptitude":mrgreen:

---

### Post by bodhi.zazen on 2006-09-25
> **xpod said:**
> Spoilsport...I quite liked his own guide,NOW you go giving me more to read:D

EDIT...AND i prefer "aptitude":mrgreen:

That's what ya get for bumping ya own. :-({|= :)

---

### Post by xpod on 2006-09-25
OK OK..Your forgiven:mrgreen:

---

### Post by Garyu on 2006-09-25
> **bodhi.zazen said:**
> That's what ya get for bumping ya own. :-({|= :)

Just trying to help you know. Let me know if I should stop doing this. :cool:

---

### Post by xpod on 2006-09-25
> Just trying to help you know. Let me know if I should stop doing this. 

KEEP UP THE GOOD WORK!!:mrgreen:

---

### Post by bodhi.zazen on 2006-09-25
> **Garyu said:**
> Just trying to help you know. Let me know if I should stop doing this. :cool:

LOL Garyu :lol:

You wrote a nice guide and I book marked it :)

Beyond that xpod and I are just hav'in some fun (I'm afraid it is an inside kind of thing, no offense to you !).

If you would be so kind as to:[list=a][*]Keep teaching, lord knows I need it !
[*]Laugh, that's the point. :p[/list]

---

### Post by xpod on 2006-09-25
to be sure to be sure!

EDIT:....Whats a community without laughter after all:mrgreen:

---

### Post by xpod on 2006-09-25
Did you know i got my first post "jailed" today.......A bad joke in the bad joke thread of all places(backyard)..

Hows THAT for irony...LOLOLOLOLOLOLOL

---

### Post by xmastree on 2006-09-25
I can't help thinking that /bin isn't like command.com but more like c:\windows\command 
A directory where windows keeps its executable files like edit or scandisk.
AIUI, **ls** and **cp** are bash *commands* like **dir** or **copy**, which are contained within command.com

---

### Post by xmastree on 2006-09-25
> **xpod said:**
> Did you know i got my first post "jailed" today.......A bad joke in the bad joke thread of all places(backyard)..ooh... 
<fx>checks jail</fx>
Hmm... not surprising really...

what's the difference between a woman and a computer?


(pm me for the answer... LOL)


Whoops, mustn't derail this thread...

---

### Post by Lord Illidan on 2006-09-25
> **xmastree said:**
> I can't help thinking that /bin isn't like command.com but more like c:\windows\command 
A directory where windows keeps its executable files like edit or scandisk.
AIUI, **ls** and **cp** are bash *commands* like **dir** or **copy**, which are contained within command.com

seems you are right.
command.com is a shell, like bash, in which dir and copy are stored, among others [http://en.wikipedia.org/wiki/Command.com](http://en.wikipedia.org/wiki/Command.com)

---

### Post by Garyu on 2006-09-25
> **xmastree said:**
> I can't help thinking that /bin isn't like command.com but more like c:\windows\command 
A directory where windows keeps its executable files like edit or scandisk.
AIUI, **ls** and **cp** are bash *commands* like **dir** or **copy**, which are contained within command.com

I might be a little rusty on my microsoft knowledge, but dir, copy, move, rename, delete, and several other commands basic to the DOS shell resides in command.com (at least used to be like this in DOS). Other commands like fdisk, attrib, format, edit, scandisk, and so on resided as .com or .exe (binaries) in the "\MSDOS" directory. As I understood things the "\MSDOS" simply was moved to "\Windows\System" from Win95 and on. But then there was winNT and then winXP which is built on NT (rather than DOS). 

In winXP/NT I have hardly used anything but the GUI so maybe things have changed since my days on the microsoft command line. In that case, maybe you could suggest a better translation of the directory structure than the one I provided here?

I am trying to keep things as simple as possible though. No use in complicating things by explaining the differences in microsoft OS's on top of trying to explain the unix file system hierarchy...

---

### Post by Garyu on 2006-09-25
> **Lord Illidan said:**
> seems you are right.
command.com is a shell, like bash, in which dir and copy are stored, among others [http://en.wikipedia.org/wiki/Command.com](http://en.wikipedia.org/wiki/Command.com)

Are you guys saying that "ls" and "cp" would reside in the binary "bash"? Then why do I find them in /bin ? 

I wrote this guide because I saw a need and tried to fill it, not because I am some kind of expert, so if there are mistakes in here please help me correct them to something better. :)

---

### Post by Lord Illidan on 2006-09-25
> **Garyu said:**
> Are you guys saying that "ls" and "cp" would reside in the binary "bash"? Then why do I find them in /bin ? 

I wrote this guide because I saw a need and tried to fill it, not because I am some kind of expert, so if there are mistakes in here please help me correct them to something better. :)

ls and cp are common to all UNIX shells, so they reside in /bin.
On the other hand, dir and copy are found only in command.com, because that's the way windows was coded...and it had only 1 shell to begin with anyway.

I like your guide, mate. Don't be discouraged.

---

### Post by Whhpssh on 2006-09-27
Great post, Gary.  Thank you very much.

If there's one thing I've noticed since starting to use Ubuntu, it's that this community has already answered every question I've had.  :D

---

