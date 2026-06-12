---
title: "What Linux Users Should Memorize"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-12
**Objectives of this thread**
1. To let users (especially the new ones) know what the most essential things about Linux they should keep in their minds are
2. To let users (especially the new ones) memorize what the basic things that they should memorize by simply reading posts on this thread
[B]
What is Going On[/B]
There are many basic things that every Linux user has to know in order for him/her to do basic operations with the OS, but many new users (even some old ones maybe) tend not to know them or take them for granted. Some of those things are essential command-line codes and the meanings of directories under the root (/) directory.

**Nature of Posts this Thread is Designed For**
This thread is intended for posts regarding on what Linux users have to have on the back of their minds.
[B]
Notes[/B]
**1. Please try to make your posts comprehensive enough for the NEW USER**
2. Please avoid to be off topic
3. Please try not to post information that has been posted already

:guitar:

---

### Post by wersdaluv on 2007-02-12
The directories under the root (/) directory are important yet, new users could be unfamiliar with it. 

Here is a copy of what is posted on [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/directories-file-systems.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/directories-file-systems.html)



    *

      /bin - important binary applications
    *

      /boot - files that are required to boot the computer
    *

      /dev - the device files
    *

      /etc - configuration files, startup scripts, etc...
    *

      /home - local users' home directories
    *

      /lib - system libraries
    *

      /lost+found - provides a lost+found system for files that exist under the root (/) directory
    *

      /media - mounted (loaded) removable media such as CDs, digital cameras, etc...
    *

      /mnt - mounted filesystems
    *

      /opt - provides a location for optional applications to be installed
    *

      /proc - special dynamic directory that maintains information about the state of the system, including currently running processes
    *

      /root - root user home directory, pronounced 'slash-root'
    *

      /sbin - important system binaries
    *

      /sys - contains information about the system
    *

      /tmp - temporary files
    *

      /usr - applications and files that are mostly available for all users to access
    *

      /var - variable files such as logs and databases

---

### Post by an.echte.trilingue on 2007-02-12
the command no ubuntu user should be without (still not GUI equivalent):

```
sudo dpkg-reconfigure xserver-xorg
```

it also amazes me how many people forget to do this before trying to install stuff or do upgrades:
```
sudo aptitude update
```

Also, I think that the synaptic, although very nice, is no replacement for learning how to use apt-get, aptitude, and dpkg.

/usr means "user", but I like to think of it as Unix System Resources; lots of binaries are stored there

/bin is short for Binaries, but they are often in other places, such as /usr/bin or /usr/sbin

/etc is where the configuration files for pretty much everything are.

---

### Post by Jamface on 2007-02-12
sudo dpkg-reconfigure xserver-xorg
sudo aptitude update

Very happy to learn these codes but what do they mean and do? 
Hope this question is 'on thread'. :)

---

### Post by Bachstelze on 2007-02-12
The first one is used to reconfigure your X server (which is the part of your system who deals with most graphics) and should be used only if you have problems with it. I personally never use it, as I prefer editing the X configuration file manually.

The second one download a list of all available packages in the sources you have enabled, to let the system know what the latest version of eveything is.

---

### Post by ghandi69_ on 2007-02-12
Some important locations.

etc/apt/sources.list

Must change that file to include more sources if you want to get all the cool apps.

type in "Getting Started with ubuntu" into google, and the first link will be a link to the ubuntu guide.  It has a good list of sources you can copy into your source list.

etc/X11/xorg.conf

location of xorg.conf file... good to know for configuring video card drivers.

I will provide some information while also requesting some.... I know that files that start with a period ".config" for example, are hidden.... how do you view these in the terminal?

Thanks!!

---

### Post by tommy1987 on 2007-02-12
To view hidden files in the terminal do 'ls -a',

this views all files, (even hidden ones)

To get more information about ls do 'man ls' in terminal

---

### Post by wersdaluv on 2007-02-12
I copied the following from [http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal](http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal)...
> 
**Navigating the terminal**

The standard terminal on Ubuntu is Gnome Terminal which can be found in Applications &#8594; Accessories &#8594; Terminal. A terminal is in a way very similar to a file manager in that it's always inside a specific folder and is able to navigate to other folders and do regular file management. By default it will be inside your home folder when you run it. To confirm that your terminal is indeed browsing your home folder, type pwd ending with a press on enter. The pwd command will output the path to the current folder.

To see a list of files and directories inside the current directory, run the command ls. If you want to navigate up the directory tree run cd ... If you want to navigate down the directory tree run cd NAME where NAME is the name of the folder you want to navigate to. Example: if Tom is inside his home folder and there's a directory called test inside it, he will run cd test to change directory. If he wants to go back he can run cd ... I he ever gets lost he can run cd by itself; this will take him back to his home folder.

Also, whenever typing directory names with spaces, put the name inside quotation marks.
Example of changing to a directory with spaces---> cd "/home/user/Extracted Files"

---

### Post by Zuuswa on 2007-02-12
When your system seems to 'hang' or 'crash', first try control+alt+backspace.  This will restart the xsession, and log out from the current user.  It will restart the xsession and bring you back to the log in screen (gdm, kdm, etc.) without having to reboot the computer or force a shutdown.

If you need to reboot the computer, but only have access to a terminal:
```
sudo shutdown -r now
```

if you just want to shutdown (and not reboot), then leave the '-r' out.

Most programs, when being run by entering their name in a terminal, will display some usefull information (i.e. arguements) if you append '--help' after the program name.  Even more information will be displayed if you type 'man' before the command.

Example:
```
gedit --help
man gedit
```

---

### Post by usererror on 2007-02-12
Wow, **wersdaluv** that is the post i have wanted all of my linux life!!!

So if i'm installing my own programs I currently put them in /usr/local/bin/ is that a good place or not?

I still do not fully understand the logic of the linux directory structure.

---

### Post by louieb on 2007-02-12
[http://www.google.com/linux](http://www.google.com/linux)

---

### Post by confused57 on 2007-02-12
I have this thread bookmarked:
[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

My memory fails me on occasion, so I have cheatsheet next to my keyboard that I use for important commands or configuration files...when I'm reading through the forum, if I see something I might need, I write it down.

---

### Post by Maestro23 on 2007-02-12
> **confused57 said:**
> I have this thread bookmarked:
[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

My memory fails me on occasion, so I have cheatsheet next to my keyboard that I use for important commands or configuration files...when I'm reading through the forum, if I see something I might need, I write it down.

I do the same thing man.  Keep an OpenOffice doc minimized that I add stuff to that I find on the forums or other linux sites. Put links in there as well.

---

### Post by kittyhawk63 on 2007-02-12
Confused57 and Maestro23...great suggestion. :)

---

### Post by sunexplodes on 2007-02-12
I made a little reference guide quite a while back, and i was going to post some stuff from it, but almost everything's outdated now. 

But yeah, the best thing a novice linux user can do for themselves is take notes ON PAPER, so they don't lose them if they screw something up or have to reinstall. I've got a little notebook in my desk drawer for that kind of thing.

---

### Post by ndefontenay on 2007-02-12
for me /bin are Linux binaries such as all the commands we can type in the shell.
It's not a place to install new applications.

I would install my new stuff to /usr/local/ instead.

I suppose it's still ok to install application in the user home but I think it's messy.

Concerning the notes, I would write it down on a paper too. I used to write it in an Open Office document available on my desktop, but it serves no purpose when I loose X!
It can still be usefull if it's a text document... It's still okay to use VI or cat to view it.

Writing the important command lines on paper is a betters solution I think.

The command line to reconfigure X is a must have!

---

### Post by Maestro23 on 2007-02-12
> **kittyhawk63 said:**
> Confused57 and Maestro23...great suggestion. :)

Another thing I do, (because we do it at work) is keep a changelog. Document any changes I make to the system and mark it with a date.  Anything I install, change, etc... Supply links to the help threads or type out the commands I used.  Also have a handy notebook in the desk drawer as well, as other have suggested.

---

### Post by confused57 on 2007-02-12
> **ndefontenay said:**
> for me /bin are Linux binaries such as all the commands we can type in the shell.
It's not a place to install new applications.

I would install my new stuff to /usr/local/ instead.

I suppose it's still ok to install application in the user home but I think it's messy.

Concerning the notes, I would write it down on a paper too. I used to write it in an Open Office document available on my desktop, but it serves no purpose when I loose X!
It can still be usefull if it's a text document... It's still okay to use VI or cat to view it.

Writing the important command lines on paper is a betters solution I think.

The command line to reconfigure X is a must have!

A text file would probably be useful, put in a "keyword" & use grep to locate entries...it's not something I devised, but see Herman's reply(#5, I think) in this thread:
[http://www.ubuntuforums.org/showthread.php?t=352484](http://www.ubuntuforums.org/showthread.php?t=352484)

---

### Post by sunexplodes on 2007-02-12
this thread inspired me to update my little cheat sheet. 

[http://ubuntuforums.org/showthread.php?t=302475](http://ubuntuforums.org/showthread.php?t=302475)

---

### Post by wersdaluv on 2007-02-14
> **usererror said:**
> Wow, **wersdaluv** that is the post i have wanted all of my linux life!!!

So if i'm installing my own programs I currently put them in /usr/local/bin/ is that a good place or not?

I still do not fully understand the logic of the linux directory structure.

I would love to answer that but I too do not understand the directory structure. I hope someone explains those things here. ;)

---

### Post by Maestro23 on 2007-02-14
> **wersdaluv said:**
> I would love to answer that but I too do not understand the directory structure. I hope someone explains those things here. ;)

Great site for people new to linux: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by sunexplodes on 2007-02-28
I'm just giving this a little bump to see if anybody has anything new to add.

---

### Post by nickoli_02 on 2007-02-28
[QUOTE=
Also, whenever typing directory names with spaces, put the name inside quotation marks.
Example of changing to a directory with spaces---> cd "/home/user/Extracted Files"[/QUOTE]

You can also use a \ escape character as well:

```
cd /home/user/Extracted\ Files
```

---

### Post by Skidpad on 2007-02-28
I like this link a lot...it is the "How to Help Yourself" thread: [http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)
A great resource tool for n00bs like me.  :guitar:

---

### Post by wersdaluv on 2007-04-12
A very good place to store your cheatsheet on is [BasKet]("http://basket.kde.org/").

---

### Post by Gallardo Spyder on 2007-04-12
A little more advance tip - but has saved my bacon a number of times...

I do a full image copy of my ubuntu installation - somewhat frequently. But specifically before I mess with anything with updating the Kernal, Xserver, Beryl, etc.  That way if anything goes wrong - in 15 minutes restoring my latest image - I am back to where I started.

I have used this numerous times - since I like to try new things, latest alpha and beta software (specifically with Beryl and other potential system effecting things.)

I use Partimage from the System Rescue Distro - takes about 15 minutes to do a full partimage and 15 minutes to restore back to the working system if needed.

It also servers as a nice full backup to the entire OS - stored on an external drive, you always have a DR if your main drive goes bad, corruption or other...

Here is a very easy Howto on doing this:

[http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition](http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition)

Gspyder

---

### Post by nsleiman on 2007-04-12
since i am using gmail i used always (and still) to mail myself any new note or command i didn't know,
Hint: i have a label there called "linuxnotes" and whenever i want to save something i do email it to the following email: xxxxxx+linuxnotes@gmail.com (the xxxxx is my username :) ) the filter will catch the appended extras "+linuxnotes" and will be moved directly to the folder without appearing in my inbox :) 

i hate writing on paper since i always forget where i put em.

as for the important commands i suggest following:

rm -rf foder/files/people   for  deleting 
cp /etc/X11/xorg.conf .  (for backuping the xorg configuration file)
shutdown -r now
kill -9  and  killall
top
uptime
free -h
ps aux | grep xxxxxx

and most important is to search the forum before asking anything :guitar:

---

### Post by Nythain on 2007-04-12
BACK UP important config files regularly... so when if something jacks up you arent spending two days trying to get a freaking samba share to work like i am

---

### Post by wersdaluv on 2007-05-18
[The Ultimate Linux Reference Guide for Newbies]("http://blog.lxpages.com/ultimate_linux.html")

---

