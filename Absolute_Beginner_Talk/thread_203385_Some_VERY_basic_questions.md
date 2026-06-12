---
title: "Some VERY basic questions"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-25
Hi,

After having a real hard time yesterday and deciding to remove Ubuntu, this morning I changed my mind and decided I should give it one more try. Guess what, this time I did manage to get one thing working. Well, that's better then nothing, which was yesterday's result.

Anyway, I have some simple questions and I'll use old MS-DOS command examples to make them clear. I hope you remember the old MS-DOS, if you've ever used even.

MS-DOS:

C:\>CD <directory>          - ? Linux equivalent ?
C:\>CLS                         - ? Linux ?
C:\>MD <directory>          - ? Linux ? 
C:\>RD <directory>          - ? Linux ?
C:\>DEL <file>                 - ? Linux ?
C:\>DIR                          - ? Linux ?

I was also thinking to try and fix my ATI Mobility Radeon X700 graphics drivers  and I found this page [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Yet, there are some things noted there which I need to get right first:
*"Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps"*
Q1: Is there some default download directory or do I have to create one?
Q2: How do I enable those "universe" and "multiverse" repositories? I haven't yet looked into the file I'm supposed to edit.
Q3: How do I download something while I'm in text mode? (my graphics does not work at all)

Thanks

---

### Post by tribaal on 2006-06-25
Cd -> cd : "cd Desktop". Remember linux is case sensitive.
Dir -> ls
del -> rm : Be careful with this one :)

A few tips and tricks: if you push the "tab" key while typing a command the system will try to autocomplete it for you, or display a list of possibilities.
Any command has a "--help" flag, and / or a man page. 
So if you don't know how to use a command try "<command> --help", or "man <command>".

Default download drirectory is ~/Desktop for firefox and most of the GUI stuff, and the current active dir for most command line programms (like wget).
Well I'm sure there are plenty of guides to help you with enabling the repos. A google search would have given you[ this link]("http://ubuntuguide.org/wiki/Dapper").
To download something while in text mode you should either use apt-get (to install programms), or "wget" to actually download somthing from an url. You might need to install wget first ("sudo apt-get install wget").

Hope this helps. :)

- trib'

---

### Post by BoneKracker on 2006-06-25
C:\>CD                      cd
C:\>CLS                    clear
C:\>MD                     mkdir
C:\>RD                      rm -r
C:\>DEL                    rm
C:\>DIR                     ls

There is built-in documentation in the terminal.  Type:
man man

You can get help for stuff by typing, for example:
man mkdir
(then q to get out)

If you don't know what to "man" for, use "man -k" and guess, that will suggest man pages.

Also, if you haven't done so (assuming you're using the desktop version of *buntu), go to the menu and explore the help -- there are pointers to some good documentation.

---

### Post by FuturePast on 2006-06-25
Note that Linux is case sensitive for everything.

[QUOTE=ovimunt]C:\>CD <directory>[/QUOTE]          - cd <dir>
[QUOTE=ovimunt]C:\>CLS[/QUOTE]                         - clear
[QUOTE=ovimunt]C:\>MD <directory>[/QUOTE]          - mkdir <dir>
[QUOTE=ovimunt]C:\>RD <directory>[/QUOTE]          - rmdir <dir>
[QUOTE=ovimunt]C:\>DEL <file>[/QUOTE]                 - rm <file>
[QUOTE=ovimunt]C:\>DIR[/QUOTE]                          - ls

For further info on the commands try man <command name>

[QUOTE=ovimunt]Q1: Is there some default download directory or do I have to create one?[/QUOTE]
No, there's no default, just create one in your home directory.
[QUOTE=ovimunt]Q2: How do I enable those "universe" and "multiverse" repositories? I haven't yet looked into the file I'm supposed to edit.[/QUOTE]
It tells you in the sources.list file. Basically you need to uncomment two lines.
(Try the commands "sudo nano <file>" to do this)
[QUOTE=ovimunt]Q3: How do I download something while I'm in text mode? (my graphics does not work at all)[/QUOTE]
Use the command wget <url>

---

### Post by mmcmonster on 2006-06-25
Remember that linux commands are case sensitive:

C:\>CD <directory>          - cd
C:\>CLS                         - clear
C:\>MD <directory>          - mkdir <directory>
C:\>RD <directory>          - rmdir <directory>
C:\>DEL <file>                 - rm <file>
C:\>DIR                          - ls (see below)

For DIR, ls has a couple different options that can be used:

ls -l          <- This one will work for you most of the time.  It wont show you the "hidden" files in a directory
ls -la         <- This one will show you all the files in a directory in a format similar to DIR

ls             <- This will give you a format similar to DIR /W

In general, files in linux (and unix) that start with a "." (period) are considered hidden and not showed.  As a user, you shouldn't be using files that start with a period.  Configuration files for all your applications all start with a period and are stored in your home directory.  That way if you backup your home directory and move it to another computer, you generally keep all your application preferences.

In whichever file manager you use (such as nautilus) files that start with a period are hidden by default, unless you force the file manager to show them (usually something like View -> Hidden files).

---

### Post by gingermark on 2006-06-25
[QUOTE=ovimunt]
Yet, there are some things noted there which I need to get right first:
*"Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps"*
Q1: Is there some default download directory or do I have to create one?
Q2: How do I enable those "universe" and "multiverse" repositories? I haven't yet looked into the file I'm supposed to edit.
Q3: How do I download something while I'm in text mode? (my graphics does not work at all)

Thanks[/QUOTE]
Check out [http://linuxcommand.org](http://linuxcommand.org) for more command line fun,

Q1: In this context the download directory is wherever you downloaded the file. So, if you saved it to your Desktop, then your Desktop would be the download directory.

Q2: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Q3: use the command 'wget' and then specify the url of the file.
OR do the following:
```
sudo apt-get install elinks
```
then enter your password
then when it has downloaded type 'elinks' and use it to browse the web in text mode.

---

### Post by ovimunt on 2006-06-25
Thanks everyone for their quick reply. 

I have to say I have made a huge leap from yesterday's results.

 I managed to access the */etc/X11/xorg.conf* file and edited it. So now I've fixed my display and I've got graphics and I mean proper graphics 1280x800x24bit on an Acer Aspire 5024WLMi with ATI Mobility Radeon X700. Actually I should get on and give the solution to some other people around here who had the same problem. 

Thanks again

P.S. I've got 12 years MS-Dos and WIndows experience and 3 years of technical support in a computer shop (have seen and solved some of the most weird errors/problems ever during this time) so I'm not flippin' giving up on Linux yet! I will crack it, I'm sure. ;)

---

### Post by gingermark on 2006-06-25
[QUOTE=ovimunt]P.S. I've got 12 years MS-Dos and WIndows experience and 3 years of technical support in a computer shop (have seen and solved some of the most weird errors/problems ever during this time) so I'm not flippin' giving up on Linux yet! I will crack it, I'm sure. ;)[/QUOTE]
Lots of things to 'unlearn' then! :)

---

### Post by nkassi on 2006-06-25
Instead of typing clear everytime you want to clear the screen type "ctrl-l" (L) much easier.

Nic

---

