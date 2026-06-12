---
title: "Beginner's questions (Plain English Please) Long Read Ahead"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by testbenchdude on 2006-12-02
Pre-post: Meh. I can't believe I spelled Beginer's wrong. It's write their at the top of teh page! *whacks self with a herring*
Pre-post #2: Sorry for the double post. I hit submit instead of preview. Here is the complete text. Sorry!
Hello all,

Every couple of years I try out a few flavors of Linux to see how the open source OS community is progressing. Ultimately I'd like to ditch Windows and be able to tailor-fit an OS to do exactly what I want it to, but that's a long ways off for me. For starters I'm learning how to do the most basic of things that as a Windows user I have taken for granted. For instance, I am already comfortable with installing most flavors of linux and setting up the options that I want (mostly default). The GUI for Ubuntu is especially nice, and I am comfortable with surfing the web (I already use Firefox) and using the included multimedia apps and office suite. I know how to log into a terminal window as su and I can browse the shared folders on my windows network. Pretty simple stuff, that--and for someone like my girlfriend who only does email and internet and office stuff and music, Ubuntu is perfect for her out-of-the-box. I'm a little harder to please I'm afraid...

So let's kick this off, shall we?

Stumbling block #1. Search. How the heck do you use this feature? For instance, I downloaded Wine and installed it, and then I installed a game with it, but I can't for the life of me find the game directory. When I try the search from the GUI, it is absolutely no help. Where did it go!? ("Oh how I miss you, Hello Kitty Island Adventure!")

Just kidding. No, really, I play Quake and stuff. I'm leet and I will pwnzorz j00. Srsly. ..Just let me boot back into windows first...

Back on topic now. Here's an example--go ahead and try this. Make a text file on your desktop, call it test. Now let's say you suddenly forgot where you put this Very Important File. (Ignore it winking at you from the desktop--cover it with a terminal window or something. Now... where did that little file go...)

Open your search from the GUI, browse to the root directory (the one that has your /usr /etc /var /home folders etc.), type test in the search box, hit enter.

Nothing. Intuitively, a search program should do just that--search. What's the point of searching for a file if I already know where it is? ("Ok, let's see. Yup, it's still there. Boy do I like to be sure. Thanks, Search!") Is there some syntax I'm missing? I've tried all sorts of tricks, like *s and "s and some others, but to no avail.

Stumbling block #2. Permissions. I recognize the value of restricting access to files and folders that contain system critical information. I also know that you can use chmod in a terminal to change these permissions. That's all well and good, but let's say I want to edit a configuration file in my /home directory using the GUI. I browse to it from Places, and double-click the file. It opens in an editor, but if I try to save it I'm told I don't have the right permissions. How can you change permissions on the fly, so to speak, from the GUI? It's a real PITA to have to do everything in the terminal window when you've got all those pretty icons that should be user accessable at the merest click of a mouse. What's the point in having a GUI if you have to do all the hard stuff in a terminal? I know there's got to be a better answer than logging into your GUI as root.

Stumbling block #3. Understanding the file structure. This one is something that I'm actively researching right now because I'm used to this scenario:

Download a program from the net. Create a folder and put it there. Uncompress if needed. Double-click the setup or install executable. Follow the on-screen directions (if any). Select where the program is installed, if and where you want icons, etc. Let it do its thing.

Now, when the program is installed, I know exactly where the main files are located. I can search the Windows registry for values if I need to tweak and change them. I can choose to delete or uninstall if necessary. I can edit the shortcut and config files to include certain perameters if I wish. I can apply patches at will. Best of all, I can do this without having to log in as administrator or browse to all of these separate places in a terminal window.

In Linux--eh, not so much. People that have been using it for years undoubtably have this sort of thing ingrained in their DNA for future generations to be able to do instinctively, but alas--my parents did not come from that side of the pool so I'm stuck with "generic PC user" genes... Anyway, as such, it might be just as hard for a Linux user to explain their file structure to a windows junkie as it is to explain sight to a blind person... but don't let that stop you. Please try.

I am also at a complete loss when it comes to "compiling" or doing anything that has the word "kernel" in the instructions somewhere. I know that the kernel is sort of like the "core" of Linux--sort of like its engine or brain. Beyond that...pfft. Nothing. I can blindly follow directions posted to the internet on how to compile a specific piece of software, cutting and pasting snippets of command code, but I actually have no idea what it's doing while I'm sitting back and watching all that text scroll up. (I see blondes, brunettes... well not yet, but maybe soon thanks to you all  )

Actually that's sort of a lie. I know that a compiler takes code that humans can recognize and turns it, or "compiles" it (natch) into code that the computer can use, or "machine code". That's a rather generic statement though and doesn't really do a good job of explaining how it works. Maybe that's too in depth for a newbie such as myself, and I should just smile and nod while it does its thing for now. I'm ok with that actually. I just want to know where the darn thing "compiles" to.

So, the grand finale. My three questions:

Search
Permissions
File Structure
(and my bonus question, compiling).

If anyone here would be so kind as to explain or point me to a good explaination any or all of these things, I'm more than willing to listen and apply. These things are very important to me and would go a very long way towards my whole-hearted adoption of Linux as my main OS. So thank you for reading my Very Long Post, and I look forward to becoming a contributing member of this community in the future.

Cheers!

p.s.: Obligatory Comic Book Guy reference thrown in for no reason whatsoever:

"Oh. My. God. He doesn't even know how to grep? What a luser. Get out of my store."

---

### Post by Shatrat on 2006-12-02
For #1.  Wine has its own simulated windows directory hidden in .wine in your home directory.  If you want to search for things in general, there is a command line utilty called slocate which I use sometimes.  For example, if you're looking for your biology report and you can't find it you could type 'slocate biologyreport.pdf' and it lists locations of all files that match it.  As for a gui search utility, I dont lose things that often adn when I do slocate usually hooks me right up.  Maybe someone else has some recommendations.

#2  permissions are stored in 9 bits which are expressed as rwxrwxrwx or in octal 777 where each digit sums the 3 bits each of Owner, Group, Others.  If youre not a fan of that (which I figure you aren't) you can right click on files in the file manager and change permissions that way.  There is a permissions tab in properties.  I don't know what config file in your own home that you wouldn't be able to write to by default, but you definitely aren't going to be able to edit things like /etc/fstab (filesystem table) or /etc/hosts (special hostname-IP adress pairs) as anything less than super user.

#3 As for file structure, there is one tree in unix and everything branches out from /
The different directories there have different purposes which arent immediately obvious, /etc has a lot of config stuff, /dev is devices, et cetera.  All a normal user cares about is /home/normaluser.  If you install something as root it will generall install somewhere in /usr and be accessible to all. If you install as a user the files end up in some directory in your own home and only you see them.  As far as compiling stuff, if you ever need to install from a tarball there are a series of scripts inside a standard tarball of source code which can handle compiling, if you have the compiler and all the dependencies installed.  There will always be a README in the tarball, if you ever want to do this.

---

### Post by Bachstelze on 2006-12-02
1) I never do :p

2) Well, if a file is owned by root, only root can change its perms. And the only proper way to do stuff as root is from the terminal.

3) I don't really understand what's bothering you here. In Linux, just like in Windows, the installer - whatever it is - will just copy all the files needed by the program in their right place.

---

### Post by lamego on 2006-12-02
**Stumbling block #1**
Wine software gets installed into ~/.wine which is a hidden directoy, try using the search on hidden files when doing the search...

**Stumbling block #2.**
I am not sure you quite understood the real purpose of permissions on the first place, when you open a read-only file it means you are attempting to edit a file that you your are not authorized to do so. And yes file permissions can be managed by the GUI (nautilus) as long you are the owner as expected.


**Stumbling block #3. Understanding the file structure**
If you keep using the official process to install software using there is nothing to care about, you can just go to the package manager and list the files installed by every package.
Once you get familiar with the Unix file structure you will understand that it makes more sense than having all files packed per application, a lot of times duplicating files and problems.

---

### Post by IYY on 2006-12-02
> Just kidding. No, really, I play Quake and stuff. I'm leet and I will pwnzorz j00. Srsly.

You know, Quake, Unreal and Doom all work natively under Linux, no need for Wine.

When using the Nautilus search (the regular GUI search, that is), specify the location to your home folder. It should find it fairly quickly. 

A terminal command for search is `locate'. Used like this:

```
locate somefilename
```

A much more powerful graphical search is **beagle**, but I never use it.

> Stumbling block #2. Permissions.

If the file is indeed in your home directory and is owned by you, you can change its permissions by right clicking on it and selecting `properties'. There is a permission tab in that window where you can adjust everything graphically.

If the file in question is owned by root, you shouldn't be able to change its permissions as a user anyway. To launch nautilus as superuser, just run
```

gksudo nautilus
```

and you will have the power to graphically change the permissions, and edit all files on your filesystem.

> Stumbling block #3. Understanding the file structure. 

You shouldn't worry too much about the file structure when installing programs. Most of your programs will already be installed in the correct directory when you download them in deb form, or install from Synaptic. Even if you compile your applications from source, they will be placed in the correct location.

Usually, the program will have configuration files in the /etc directory, as well as a local hidden configuration file in your home directory. The executable file usually resides in /usr/bin.

If you are genuinely curious about the file structure, read one of many explanations on the topic. For example, here's the first hit from Google on Linux Filesystem: [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

> Actually that's sort of a lie. I know that a compiler takes code that humans can recognize and turns it, or "compiles" it (natch) into code that the computer can use, or "machine code". That's a reather generic statement though and doesn't really do a good job of explaining how it works. Maybe that's too in depth for a newbie such as my self, and I should just smile and nod while it does its thing for now. I'm ok with that actually.

I think it's a perfect description of compiling and this is exactly what happens. Inside the source code directory you download, there is a subdirectory containing all the code, in C, C++, Python or some other language, and a Makefile that specifies what things you must have installed on your system in order to compile, as well as the instructions for compiling. If everything goes nicely, after running the commands specified in the readme, your program will be translated to code the computer can understand, and all executable files and configuration data will be moved to the correct place on your filesystem (that's what **make install** does).

Don't worry about not understanding the details of every single thing you do at this point. It's impossible to understand all of Linux in one day. The more programs you install, the more problems you fix, the more programs you configure, the better you will understand what's going on and what the logic behind it is.

---

### Post by Delkster on 2006-12-02
> **testbenchdude said:**
> Search. How the heck do you use this feature? For instance, I downloaded Wine and installed it, and then I installed a game with it, but I can't for the life of me find the game directory.

As you may have found out already, in Unix/Linux per-user settings are usually saved in configuration files (sometimes organized into directories), and because most of the time the user has no need to see those files and they'd just be in the way, they're hidden (actually, the file names just begin with a dot, which causes most file managers and command line shells to hide them by default).

The search also ignores dotted files and directories by default. You probably wouln't want to get your results garbled by all kinds of configuration files that just happen to match your search if you weren't specifically looking for a configuration file. Granted, that may cause problems when you *are* looking for one if there isn't an option to also show dotted files.

By default, Wine happens to place almost everything, including its "fake Windows drive", within the same directory tree where it also stores its configuration which, as such, is -- as you probably guessed already -- a hidden one. To be more specific, it's ~/.wine, where ~ denotes your home folder.

> Back on topic now. Here's an example--go ahead and try this. Make a text file on your desktop, call it **test** ... Open your **search** from the GUI, browse to the root directory (the one that has your /usr /etc /var /home folders etc.), type **test** in the search box, hit enter.

Nothing. Intuitively, a search program should do just that. What's the point of searching for a file if I already know where it is?

There's a package called locate (its more secure cousin is called 'slocate'). It contains a script which is run periodically and maintains an index of locations of files in the system, and a 'locate' command allowing searching for files in that index. That allows for very fast search on the name of the file. I think the traditional Gnome search feature also uses locate if it's available to speed up searching.

Unfortunately, the downside is that the index isn't automatically updated when you create a new file, and thus the information isn't up-to-date. If you don't like that (and don't need the extra-fast searching), you can find the 'slocate' package in Synaptic and remove it (doing a full remove, including the configuration, may be an even safer bet).

Some of the more modern desktop indexing and searching services (such as Beagle) may also do a better job since they often monitor for changes in the filesystem and may thus keep their index up-to-date in real time. At least Beagle may have some of its own problems, though...

> **Stumbling block #2. Permissions. **How can you change permissions on the fly, so to speak, from the GUI? It's a real PITA to have to do everything in the terminal window when you've got all those pretty icons that should be user accessable at the merest click of a mouse.

If you often need to edit configuration files that only root has access to, you may find something to help you on the [RootSudo page](https://help.ubuntu.com/community/RootSudo#head-c863a1b669260ba6af02fa652d7f8fe5e6828042) in the wiki.

> **Stumbling block #3. Understanding the file structure.**

There are pretty thorough descriptions of the purposes of various directories in the [Filesystem Hierarchy Standard specification](http://www.pathname.com/fhs/pub/fhs-2.3.html).

If you just need to know what files a package has installed and where, you can check it out in the properties of that particular package in Synaptic (assuming that the package is currently installed, since that information is only stored locally for installed packages). If you use the GDebi installer for installing third-party deb packages, it also shows you the files that package will install.

---

### Post by testbenchdude on 2006-12-02
See, now these are the sort of things I need clarification on.

IYY writes: [I]You know, Quake, Unreal and Doom all work natively under Linux, no need for Wine.

When using the Nautilus search (the regular GUI search, that is), specify the location to your home folder. It should find it fairly quickly. 

A terminal command for search is `locate'.[/I]

My point was, what if I didn't know the file was in my home directory. The search does little good if you have to steer it to exactly where the file is. Anyway, I can't wait to install those games. :)

[I]If the file is indeed in your home directory and is owned by you, you can change its permissions by right clicking on it and selecting `properties'. There is a permission tab in that window where you can adjust everything graphically.

If the file in question is owned by root, you shouldn't be able to change its permissions as a user anyway.[/I]

Forgive any percieved fecitiousness, but don't I already "own" everything on my computer? I'm pretty sure I'm not understanding this the way you are. You might have to spell it out for me...

Shatrat writes: *#2 permissions are stored in 9 bits which are expressed as rwxrwxrwx or in octal 777 where each digit sums the 3 bits each of Owner, Group, Others. If youre not a fan of that (which I figure you aren't) you can right click on files in the file manager and change permissions that way. There is a permissions tab in properties. I don't know what config file in your own home that you wouldn't be able to write to by default, but you definitely aren't going to be able to edit things like /etc/fstab (filesystem table) or /etc/hosts (special hostname-IP adress pairs) as anything less than super user.*

I actually do like that explaination--I'm familiar with binary, hex, and octal (electronics background) and that's the first time I've every heard it explained that way. Thank you.

That said, thank you all for your responses, I'm checking out that file structure link right now. Also, I'm sorry I posted accidentally before I was done fixed upon edit). I hit the post button instead of preview button by mistake but it was too late to stop it, hence the double post.

---

### Post by IYY on 2006-12-02
> My point was, what if I didn't know the file was in my home directory. The search does little good if you have to steer it to exactly where the file is. Anyway, I can't wait to install those games.

Your home directory is where all of your files will be stored. A user should not really own any file outside of his own home directory (except for /tmp). So, if this file you are looking for is something you have write permissions for, it will surely be somewhere in your home directory.

Otherwise, use 'locate' or 'beagle', as suggested.

> Forgive any perceived fecitiousness, but don't I already "own" everything on my computer? I'm pretty sure I'm not understanding this the way you are. You might have to spell it out for me...

Strictly speaking, no. There are many users on your machine: you the user is one, your brother, mother and girlfriend are examples of other users. There are some users that never graphically log in at all: for example, "gdm", "ftp" and "dhcp". They do system stuff and you shouldn't worry about them. A special user is called "root", and this user has access to every single file on your computer. 

On some distributions (you could say Windows XP does this), you can actually graphically log in as root. This is very insecure, for many reasons. Ubuntu (and Windows Vista) does something different: certain users on the system have the power to execute commands as root from their own accounts, buy supplying their own login password. This is what the command 'sudo' means: super user do.

So, no, *you* do not own the file /etc/X11/xorg.conf, the X11 configuration file, for example. It is owned by root, for security purposes.

To see all the users on your sysytem (and this may confuse you, because there are many), just look at the file /etc/passwd. You will find 'root' on there, as well as your own username. You may also look at the file /etc/group which specifies the members of each group on your machine. 'admin' is the group of users who can execute sudo commands.

---

### Post by testbenchdude on 2006-12-02
> **IYY said:**
> Your home directory is where all of your files will be stored. A user should not really own any file outside of his own home directory (except for /tmp). So, if this file you are looking for is something you have write permissions for, it will surely be somewhere in your home directory.

Otherwise, use 'locate' or 'beagle', as suggested.

Strictly speaking, no. There are many users on your machine: you the user is one, your brother, mother and girlfriend are examples of other users. There are some users that never graphically log in at all: for example, "gdm", "ftp" and "dhcp". They do system stuff and you shouldn't worry about them. A special user is called "root", and this user has access to every single file on your computer. 

On some distributions (you could say Windows XP does this), you can actually graphically log in as root. This is very insecure, for many reasons. Ubuntu (and Windows Vista) does something different: certain users on the system have the power to execute commands as root from their own accounts, buy supplying their own login password. This is what the command 'sudo' means: super user do.

So, no, *you* do not own the file /etc/X11/xorg.conf, the X11 configuration file, for example. It is owned by root, for security purposes.

To see all the users on your sysytem (and this may confuse you, because there are many), just look at the file /etc/passwd. You will find 'root' on there, as well as your own username. You may also look at the file /etc/group which specifies the members of each group on your machine. 'admin' is the group of users who can execute sudo commands.

Ok, I understand about the users thing. But are you saying that the only directories that I'll ever have any access to or need to mess with are in my /home? That doesn't seem right to me. And why are the files that Wine put in there hidden by default? This has mystified me to no end any other time I've tried to crack the Linux code. I'll install a file, and the poof! Where did it go, how can I run it, etc.

Are all the program I install going to put themselves in their own hidden folders in the /home directory?

Thanks for being patient with me. See I told you, it really is like explaining sight to a blind guy. ](*,)

---

### Post by IYY on 2006-12-02
> Ok, I understand about the users thing. But are you saying that the only directories that I'll ever have any access to or need to mess with are in my /home? That doesn't seem right to me. 

You might need to make some changes outside of your home directory, but it certainly is not something you do on a daily basis, and when doing it you usually will be in the terminal anyway, so you can use the locate command.

> Are all the program I install going to put themselves in their own hidden folders in the /home directory?

The programs themselves are usually installed all over your filesystem, with configuration files in /etc, executable files in /usr/bin and so on. However, it's very common for programs to have a hidden configuration file in each user's home directory. The hidden configuration data can either be a single ASCII text file, or an entire directory of settings. Just type 

```
ls -a
```

in the terminal while in your home directory. You will see a whole bunch of configuration files you can edit. 

> And why are the files that Wine put in there hidden by default? This has mystified me to no end any other time I've tried to crack the Linux code. I'll install a file, and the poof! Where did it go, how can I run it, etc.

This is just to make your home directory less cluttered. If you automatically saw every single configuration file, it would look incredibly messy and will be hard to work with. This way, you only need to look at the configuration files when you really want to change something, but they don't interrupt your daily flow of work.

> Thanks for being patient with me. See I told you, it really is like explaining sight to a blind guy.

Understanding Linux is all about being able to change your way of thinking about things, being open minded and patient. You seem to be doing everything right, so I have no doubt you'll become a true guru in no time. 

Some users come to the forums and ask the same kinds of questions as you, but when given the answers they simply say `but in Windows, this was so easy and I knew how to do everything. Clearly this is a worse system.'

---

### Post by Delkster on 2006-12-02
> **testbenchdude said:**
> But are you saying that the only directories that I'll ever have any access to or need to mess with are in my /home? That doesn't seem right to me.

Is there a particular reason why you'd need to place your personal files somewhere else? (They're what's usually edited directly by the user -- the optimal solution for configuration, for example, would obviously be to have user interfaces for setting commonly-used options rather than forcing the user to edit them by hand, while more obscure options can be hidden from view, but then, in those rare cases where they're needed, I guess it isn't such a big struggle to use sudo by hand as well).

> And why are the files that Wine put in there hidden by default? This has mystified me to no end any other time I've tried to crack the Linux code. I'll install a file, and the poof! Where did it go, how can I run it, etc.

Again, the optimal thing would again be to have Wine put an icon for you somewhere for launching the program. Unfortunately, I guess part of the problem is that Windows applications usually don't honour the exact categories that Linux desktops usually have in their menus (or, indeed, any sensible categories at all), so there'd be the problem of icon placement. I certainly wouldn't want the Windows applications to clutter my menu the way they do in Windows either.

I guess there are also several ways a Windows application can place an icon on the Windows desktop or in the menus and I guess not all of those are very easy for Wine to integrate with the Linux desktop. For example, if the Windows application installer just places the icons as files somewhere, how is Wine to automagically integrate that with the Gnome desktop and menus which reside elsewhere?

There's clearly a problem here but it isn't easy to solve.

As for Wine placing the fake Windows directory within the hidden configuration directory by default, I don't know. I guess it could also keep that part on its own outside the configuration directory (which, in my opinion, *should* be hidden by default, as it is).

> Are all the program I install going to put themselves in their own hidden folders in the /home directory?
Native Unix/Linux applications don't. Windows applications you install in Wine do. Native applications normally place only your per-user settings (and things comparable to those, such as web browser caches) in dotted files within your home directory.

Windows applications expect a certain kind of directory hierarchy that doesn't normally exist in Unix/Linux, and that's one reason why Wine keeps Windows applications in their specific directory tree rather than placing them all around the standard Unix directory hierarchy.

Again, I guess that "sandbox" directory Wine uses for Windows applications could probably be placed somewhere else than within the hidden configuration directory by default.

---

### Post by Shatrat on 2006-12-02
> are you saying that the only directories that I'll ever have any access to or need to mess with are in my /home?
You still have read access to most of the stuff outside of your home but for the most part thats absolutely right.  Normal user activities just work in the home.  That way if a user is deleted, all their files and settings are deleted.  Keep in mind this system is designed so that if you wanted to you could have thousands of users and add and remove many of them per day.
Only the administrator needs to mess with stuff outside of /home.

Im not sure why wine hides its windows directory, transgamings cedega is pretty much the same thing but it has its visible as the transgaming_drive or something.  You could make a link to .wine that is visible if you wanted to easily.  Just ln -s /home/foo/.wine/drive_c cdrivewine or something like that.  As for installed files going poof, well it does the same thing in windows doesnt it?  If you install something as root it probably is gonna put a link to the executable in /usr/bin or /usr/local/bin or something.  If you install as user it will make a folker, like /home/foo/enemy-territory and install in there.  If you install using apt it will generally be kind enough to go ahead and add a link to the program in your applications menu.  If you install from source or something it only takes seconds to create your own link.  Just because its not in C:\\Program Files doesnt mean its lost forever.

Also, hidden files are easy to see if you want.  I believe ctrl H in nautilus will toggle to show them. Hidden files are simply ones prefixed with a . to tell applications not to display them unless you specifically want to see them.  If this wasnt done there would be a lot of clutter of configs and user data in your home folder that would get very annoying to look at.  Most of these files you never have to look at or edit unless there is a problem.

> See I told you, it really is like explaining sight to a blind guy. 
Is that anything like explaining sex to a nun? In detail?

---

### Post by Delkster on 2006-12-02
> **IYY said:**
> However, it's very common for programs to have a hidden configuration file in each user's home directory. The hidden configuration data can either be a single ASCII text file, or an entire directory of settings. Just type 

```
ls -a
```

in the terminal while in your home directory. You will see a whole bunch of configuration files you can edit. 

... or enable "Show hidden files" in the file manager, probably in the View menu. (Can't check right now, I'm on Windows)

---

### Post by aysiu on 2006-12-02
I don't know why your search isn't working. Mine is.

You may also want to read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by testbenchdude on 2006-12-02
Ok, that helps some. Thanks again.

> **IYY said:**
> Some users come to the forums and ask the same kinds of questions as you, but when given the answers they simply say `but in Windows, this was so easy and I knew how to do everything. Clearly this is a worse system.'

Yeah, I saw one of those posts the other day and it made me laugh because it mirrored my frustrations in no small amount. ;) 

Linux still has a long way to go until it becomes a viable replacement for Windows though--maybe not to this community, but to the teeming hordes of regular windows users. I'm a tinkerer by nature though, so I'm willing to go the extra mile when others might simply give up in frustration. And even I can see how much improvemnent has been made in the way of making Linux more approachable over the years.

It's not a worse system, it's just different. I'd also like to prophesize that you guys will probably see a big surge in newbies like myself as Vista comes to market. (I know I'm not planning on using it anytime in the near future, but that's a subject for another thread ;) .) This can only have good consequences as more developers start to take notice as to how many more users are clammoring for support for their linux distros.

Well, it's almost time to go home from work. I'm sure I'll be back here several more times before this night is done. 8) 

Cheers!

*"In Soviet Russia, open source code compiles YOU!"*

---

### Post by 3rdalbum on 2006-12-02
GRAPHICAL SEARCH:

I use kfind. It requires the KDE libraries, but these will pull themselves in when you install the program from Synaptic.

EDITING FILES:

With Windows, viruses can edit the system files because your own user account always has write access to the system files. This is a security risk, so on Linux by default a normal user won't have write access to the system files.

When you need to make modifications to a system file, go to the terminal and type:

```
gksudo nautilus
```

You will now get a file manager window which lets you open any file on your system as writable. Be careful what you do within this window!

(Tip: Put this command in a launcher on one of your Gnome panels, or in your Applications menu)

FINDING PROGRAM FILES

Preferences files for programs are typically stored in ~/.*programname* (i.e. if my username was chris, and the program was Gaim, it would be /home/chris/.gaim. In Nautilus, if you press Control-H, you can see the hidden files and folders.

If you want to find out where an installed program has put all its *system-wide* files (like manuals, read-mes, plugins, resources etc), go into Synaptic and do a search for the name of the program. Right-click its entry and go to Properties. Click the Installed Files tab, and this will show you all the files that were installed.

I think that takes care of your questions... don't worry, Linux is a much different system to Windows, you'll understand Linux before long.

---

### Post by K.Mandla on 2006-12-02
> **testbenchdude said:**
> Pre-post: Meh. I can't believe I spelled Beginer's wrong. It's write their at the top of teh page! *whacks self with a herring*
(No need for herring-whackings, friend. And welcome to the forums. ;) )

---

### Post by testbenchdude on 2006-12-02
Dude. Thanks. All of you, for taking the time to write all of that. 

Somehow I corrupted my xserver, and because of that and everything else I screwed around with last night, I'm installing Ubuntu Edgy fresh right now.

I'm bookmarking this thread :)

Cheers!

---

### Post by testbenchdude on 2006-12-03
Quick question. I installed Wine via Automatix2 and now I don't know how to access it to configure it.

locate wine gives a bunch of files in /usr/shaer/app-install/desktop. I can't find anything in my /home folder...

Help please?

EDIT*

NM, I openned the Automatix log and saw that it wants me to run winecfg in a terminal window. So I did, and apparently it created a configuration directory in /root/.wine so yay! Ok, on to more stuff. Wish me luck!

EDIT2*

I still can't access Wine. I went to my /home and typed ls /.wine but there is "no such file or directory". What am I missing?

EDIT3*

I typed cd ~/.wine and all of a sudden I'm there. Hmm... I'm still struggling with this, thanks for bearing with me :) What does the ~ actually mean?

---

### Post by aysiu on 2006-12-03
~/ means /home/*username*

Read more about Wine basic use here:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by JBull on 2006-12-03
These are great questions about searching, installing and accessing files.  I've been using Linux for a while now and these are still annoyances for me.  

To say that you should be using only files in your home directiry is insane.  I work with files and apps in /usr/local or other location about 75% of the time I'm at my computer - Installing and configuring software, setting up Apache2, writing html for my web pages, etc.  It gets real old typing sudo before evrything.  

For finding files I use 
$find / -name netcdf.h
to find the location of netcdf.h, for example.  Oops, I forgot to type sudo.
$sudo find / -name netcdf.h

OK, that worked.  Why did I search for netcdf.h? Because I installed an app that has netcdf.h and I have no idea where the installer put it.  I need to find it becasue I'm installing another app that needs it and I must tell the new app the location so it can include it during make.  This happens daily and I hate it.

And I agree with you , I should own every file on my system.  I am the only user of this computer and will be the only user forever.  If someone else (my sister, for example) logs on then she can temporarily own all my files, I'm perfectly fine with that, but Linux is not. There is a way to set up Ubuntu so you can log in as root and therefore bypass the permissions annoyance.  I'm not big on security, but Linux is very secure so I deal with it.

These are common annoyances when migrating from Windows to Ubuntu.  My biggest annoyance is the filesystem structure.  New software will be looking for some library and it won;t be in the "standard" place.  That's a problem with Linux, there is no "standard" place.  Ubuntu puts things in different places compared to other Linux distros.  For example  /usr/lib/X11R6/lib is now in /usr/lib.  And yes it is true that none of that is in your home directory so you won't be able to easily fix the problems.  You'll be sudo and chmodding and possibly simlinking things, if you are able to locate them.

There's my rant on this topic.  But don't get the wrong impression: I love Ubuntu.  I use it more than Windows now as I learn more and get used these things.

---

### Post by steve.horsley on 2006-12-03
I'm surprised that nobody else has confirmed that search in nautilus is broken. As far as I can tell, it has never worked, and it may be that it never will. Attached is a screenshot of nautilus failing to find a file in my home directory. Utterly useless. 

If you use **locate** to find files, that works nice and fast but only find files that were there last time the scanner ran (it caches a list of all files on the system, I think).

**find** is the origingal file finding utility, and works pretty-much as you would expect.

---

### Post by aysiu on 2006-12-03
That's weird. So does Nautilus' search use something different from *gnome-search-tool*?

---

### Post by steve.horsley on 2006-12-03
Clearly it does. gnome-search-tool finds that file no problem. I didn't know about that tool. Thanks.

The interesting thing with nautilus is that if you specify to search Filesystem, it says 0 files found so fast that I don't think it's looking at all.

---

### Post by aysiu on 2006-12-03
Sounds like a bug report in the making.

While we're at it, what's with Nautilus search going straight to your home directory instead of... whatever directory you happen to be looking at?

---

### Post by Delkster on 2006-12-05
> **JBull said:**
> To say that you should be using only files in your home directiry is insane.  I work with files and apps in /usr/local or other location about 75% of the time I'm at my computer - Installing and configuring software, setting up Apache2, writing html for my web pages, etc.
Call me old-fashioned but if you run a web server, you really should be knowledgeable enough to be able to use the command line. Although handling files outside of typical desktop applications (of which server configuration isn't one, and neither is compiling software from source code etc.) tend to be tedious to do with GUI tools, they can be quite nicely done on the command line, and yes, this is one of those cases where it isn't inappropriate to say that.

> It gets real old typing sudo before evrything.
If you want a root shell, you can use:
```
sudo -s
```
Tada, the benefits of having root.


There are usability problems with regard to permissions etc. but I fail to see the big deal in this case. I agree that it may be a good idea to have some kind of an easy way to open a file as root in a GUI, mostly for purposes of editing configuration files, although clearly the correct solution would be to have GUIs for commonly needed settings (and using the command line or something else for those uncommon ones shouldn't be as big a deal as it clearly is for frequently needed ones). Sometimes you have to have something between the two extremes as a temporary solution until a real one can be developed.

I for one am very glad that we do have the culture of privilege separation. If Linux gets more market share also among the 'normal' desktop users and comes into the radar of malware writers, having a strict separation of privileges should at least help a little.

---

### Post by Delkster on 2006-12-05
> **steve.horsley said:**
> I'm surprised that nobody else has confirmed that search in nautilus is broken. As far as I can tell, it has never worked, and it may be that it never will. Attached is a screenshot of nautilus failing to find a file in my home directory. Utterly useless.

Do you happen to have Beagle installed? I don't know much about it and haven't investigated further but in my experience Beagle (or at least its GUI) doesn't seem to search based on file name at all.

If you don't have Beagle installed, the search in Nautilus probably uses something more traditional and straightforward. I'd be surprised if that wouldn't work.

---

