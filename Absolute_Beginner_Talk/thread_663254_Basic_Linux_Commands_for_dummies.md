---
title: "Basic Linux Commands for dummies"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-09
Let me start by saying that I have no command liine exp. in Linux and very little in windows. 

I was wondering if there is a site that can teach me basic navigation skills in the command line for Linux.
Basic stuff like opening folders and view files in the terminal. I will gain more knowledge as I go on.

---

### Post by LaRoza on 2008-01-09
See my wiki, [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

Use googe too, you'll get a lot of hits.

---

### Post by twin_57103 on 2008-01-09
Here's a quick start for file navigation:

"cd" is the same as in Windows/DOS: change directory.  Use "cd .." to move up a directory or cd [directory name] to move down a directory

"ls" stands for list - the same as "dir" in DOS (dir also works) - it lists the files in a folder.

"cp" is for copy - cp [original file name] [new file name]

"rm" is for remove/delete - this does not go to a recycle bin - use with caution!  rm [file name]

"rmdir" is for deleting a folder - it will also delete anything in the folder - use with extreme caution!!

"mkdir" will create a folder - mkdir [folder name]

"gedit" is a good viewer for simple files (text, configuration files, program code) - "gedit [file name]"

 For help with a specific  command, type "man [command]" - this will access the manual (same as [command] /? in Windows/DOS)

See [https://help.ubuntu.com/7.10/basic-commands/C/]("https://help.ubuntu.com/7.10/basic-commands/C/") for a more complete guide.

You can also search for terminal commands - that's what the command line is called in Linux.

---

### Post by moebob24 on 2008-01-09
I know you get a lot of hits but idk if all are reliable. thanks for this link tho.

---

### Post by LaRoza on 2008-01-09
> **moebob24 said:**
> I know you get a lot of hits but idk if all are reliable. thanks for this link tho.

That is my wiki, usually reliable.

---

### Post by frup on 2008-01-09
> **twin_57103 said:**
> 
"gedit" is a good viewer for simple files (text, configuration files, program code) - "gedit [file name]"


In command line terms it is probably more important to know about nano. Nano is easy to use but you have to understand it. Lucking most of the commands are listed at it bottom.

---

### Post by twin_57103 on 2008-01-09
> **frup said:**
> In command line terms it is probably more important to know about nano. Nano is easy to use but you have to understand it. Lucking most of the commands are listed at it bottom.

There are almost always multiple options.  I like gedit because it is pretty straightforward and because I have used it for programming - personal taste.

---

### Post by LaRoza on 2008-01-09
Vi(m) would be better, as it is universally present in *nix systems. It may take a little longer to learn, but it will be there...

---

### Post by mrphud on 2008-01-09
yes If you would like to learn a bit about linux and about some basic commands I recommend

[www.linux.org](www.linux.org)

There is a tab that says courses and you can ambulate through the beginners course. Also what helped me for the command line shell is to inform yourself about the bash shell. In fact you should look a bit at the history of linux and how it works, like kernels/ shells/ for some background knowledge. It will just take a little patience and time like it did with windows. Commands are easily learned. Also learn how to access the manual for the bash shell if you would like information and options on bash commands.

```
man (any bash command)
```

Hope this helps 

Good Luck

---

### Post by frup on 2008-01-09
> **twin_57103 said:**
> There are almost always multiple options.  I like gedit because it is pretty straightforward and because I have used it for programming - personal taste.

Yeah that's fine but strictly speaking gedit is not a command line program, you are merely using it to call gedit. In a command line situation, which can be scary for some users if it is by accident you can't use gedit. 

Another good program to know about for recovery is Lynx. That's the command line web browser.

---

### Post by Mike'sHardLinux on 2008-01-09
> **twin_57103 said:**
> There are almost always multiple options.  I like gedit because it is pretty straightforward and because I have used it for programming - personal taste.

The thing is, gedit is **not** a commandline tool. Sure you can start it from the commandline, but it is a gui app. Nano is a true commandline app.

---

### Post by akiratheoni on 2008-01-09
This was on Digg several days ago (I think it's still on there, too).

[http://www.linuxguide.it/linux_commands_line_en.htm](http://www.linuxguide.it/linux_commands_line_en.htm)

---

### Post by azimuth on 2008-01-10
Why just go for commands for dummies. Take the command line by the horns and let full  tutorials like [http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php) lead you to where you really want to be.

---

### Post by Paulmd on 2008-01-10
> **moebob24 said:**
> Let me start by saying that I have no command liine exp. in Linux and very little in windows. 

I was wondering if there is a site that can teach me basic navigation skills in the command line for Linux.
Basic stuff like opening folders and view files in the terminal. I will gain more knowledge as I go on.

First, you need not use the command line unless something breaks, badly enough that X doesn't work. Or need features not accessible in gnome. Depending on your prejudices, you can interpreet this as "the linux command line is incredibly rich" or "the developers of gnome need to do a much better job of implementing a complete feature set."


Since the most basic ones have already been posted, I will only add a few.

sudo (gives root permissions to a command) 
pico (command line text editor), which is useful for editing config files.

apt-get (for adding and removing packages) (synaptic is clunkier, than it should be)
man (for accessing manuals)

---

### Post by erginemr on 2008-01-10
> **moebob24 said:**
> Let me start by saying that I have no command liine exp. in Linux and very little in windows. 

I was wondering if there is a site that can teach me basic navigation skills in the command line for Linux.
Basic stuff like opening folders and view files in the terminal. I will gain more knowledge as I go on.

Here is another one with a light-hearted read and top-notch jokes inside, which I highly recommend for any Linux newbie:

[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

---

### Post by philinux on 2008-01-10
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

Plenty of info to keep you going there. :)

---

### Post by bbqsandwich on 2008-01-10
As a linux newbie myself, I recommend [www.linuxcommand.org](www.linuxcommand.org). I like the way it walks you through things and is not just a dry list of commands.

Edit: Oops! azimuth already recommended this one. I must have glanced over it, sorry. But I will keep my post as a second endorsement. :)

---

### Post by ghostdog74 on 2008-01-10
> **moebob24 said:**
> Let me start by saying that I have no command liine exp. in Linux and very little in windows. 

I was wondering if there is a site that can teach me basic navigation skills in the command line for Linux.
Basic stuff like opening folders and view files in the terminal. I will gain more knowledge as I go on.

some common commands and tools you can use while playing with linux

Navigation/Files:/Permissions:
--------------------------------------------
"pwd" : print working directory. See where you are now
"cd" : change directory
"ls" : list files and directories
"rmdir" : remove directory.
"rm" : remove files / directory
"cp" : copy files
"mv" : move files
"find" : find files based on criteria. 
"locate" : same as find
"chown" : change file ownership
"chmod" : change permissions
"|" : pipe, chaining of commands , eg ps -ef|grep "some process"
">"  and ">>" :  output redirection, create/append files
"<" : input redirection, read a file


Accounts:
------------------------------
"userdel" : delete a user
"usermod" : change properties of a user
"passwd" change your password and more


Shells:
--------------------
"bash" : the bash shell.
"ksh" : korn shell
"csh" : C shell


System
------------------
"who" : see who's logged on
"ps" : see currents processes in your system
"top" : see current processes and more
"init 0" : shutdown the machine
"shutdown" : same as above
"init 6" : reboot
"mount" : mount partitions, portable HDD etc
"ntfs-3g" : if you want to mount NTFS partition


Text file searching & manipulation:
---------------------------------------
"paste": merge lines of files
"join" : join lines of files
"cut" : remove sections from each line
"tr" : translate or delete characters
"sed" : stream editor text filtering/manipulation
"awk" : as above, and more
"vi" : command line editor. comes with most systems.
"grep" : search for patterns
"comm": compare 2 sorted files line by line

Help:
-----------------
"man" :  the manual pages. Do a man <command> to see the manual page for that command
"apropos: search the man page 

Networking
-------------------------
"telnet" : you can connect to other telnet servers
"ftp " : file transfer 
"ssh" : secure shell, sftp for secured file transfer, scp secured copy
"ifconfig" : set your network settings.
"lynx" : text web browser
"tcpdump" : packet sniffer
"nc" : netcat

Of course,there are many others.. you can check you /usr/bin and /usr/sbin directories for more.

---

### Post by Niniel on 2008-01-10
> **LaRoza said:**
> Vi(m) would be better, as it is universally present in *nix systems. It may take a little longer to learn, but it will be there...

vi may have been great when people didn't know better... Seriously, it may be the most feature-rich application ever, but it the "interface" is just awful.

Personally, I'm partial to Pico/Nano. I loved Pine when I used it back in the day, so yes, since that's what I know, these editors must be best. :)

---

