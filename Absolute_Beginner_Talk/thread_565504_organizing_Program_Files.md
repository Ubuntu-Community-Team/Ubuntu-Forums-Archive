---
title: "organizing Program Files"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by anna611 on 2007-10-02
Hello all

I switched from Windows to Ubuntu.

One thing is unclear:
in Windows all programs / applications are installed in "Program Files".

How does it work in Ubuntu?

Googled around, but just found that in the ~ (/home/user/) -folder are just the conf-files.

If I install JDK for example, it automatically installs in ~-folder. Same for NETBEANS.
Is this wrong? In which directory should it be installed?

Thank you in advance
Anna

---

### Post by Anzan on 2007-10-02
/bin (binaries)

---

### Post by hyper_ch on 2007-10-02
and /usr

---

### Post by Tomosaur on 2007-10-02
This is one of the biggest differences between Linux and Windows - so it's no surprise if it confuses you - so don't worry :)

Linux uses a Unix type directory structure, which means **everything** is seen as a sub-directory of / (which we call the root directory). When you install a program, it normally gets spread out over a few directories. Anzan is incorrect when he said '/bin' - that is where **system** binaries go. For user installed programs, the binary files go in /usr/bin, while shared stuff - images, documentation etc, go into /usr/share. Here's a typical run-down of what goes where:

Software binaries (the equivalent to .exe files in Windows) go into /usr/bin/

Software documentation goes into /usr/share/doc/program_name/

Software libraries (the equivalent to Windows' .dll files) go into /usr/lib/

Software data files (images, sounds etc) go into /usr/share/program_name/



Many newcomers think this is just overly confusing, but there is some method to the madness - admittedly the main benefits are for system administrators who need to remember lots of different things, not just the program name. It also allows programs to share stuff more easily between each other.

---

### Post by anna611 on 2007-10-02
@Tomosaur: Thank you for your explanation.

When installing Netbeans it suggest installing in the home-directory. So this means they are wrong?

Another question: When installing Netbeans, I installed it in the home-folder. As I understand, the installation automatically puts the files in their belonging directory, like /usr/share/doc/netbeans etc. When checking this, I don't see it in that directory.

Does this mean I always should start installing a program from /usr/bin?

One more question: all files and folders do start with small capital letters. Is that better then like in Windows, where everything starts with big capital letters?

---

### Post by steve.horsley on 2007-10-02
Firstly, you should **always** check Synaptic (System->Administation->Synaptic) for software before looking round he web for downloads. If it's in the repos, it's pre-built for Ubuntu, easier to install, and it's a safer source than ad-hoc web sites.

Secondly, when installing software outside of your home folder, you need root permission. The easiest way to get this is with the command 
**sudo -i**
which gives you a root permissions prompt ubtil you exit it. Beware, it starts in roots home directory.

Thirdly, not all files start with lower case, but most do, because it saves using the shift key. Be aware that on Unix, file names are case sensitive. The files a.txt and A.txt are different, and can both exist in the same directory at the same time.

---

### Post by evets on 2007-10-05
Nice thread. More questions. :)

How does a former windows user know which icon to click on to start an app? What would the extension be that executes it?

I thought if it was in the /usr/bin folder it was an executable, but I'm wrong. I have apps installed that I can't find and/or can't execute if/when I do find them. It's driving me nuts because it's so hit and miss. 

Thanks for any direction you can give.

---

### Post by hyper_ch on 2007-10-06
whether a file is executable doesn't depend on the file extension... I still wonder why M$ does that... but it depends on the permissions on the file.

---

### Post by Soarer on 2007-10-06
If applications are correctly installed (from the repositories) they will normally appear in the menus, or can be started by typing their name in a terminal.

So you don't need to know where they are at all.

Try not to download applications from the Internet & install them. This is the Windows way, and you can nearly always find an equivalent in the repositories which will just work (and will be free). If you *have* to download something, the developer *should* provide documentation (perhaps a read.me) which will tell you what to do. If not, don't install it.

---

### Post by evets on 2007-10-06
So, what you're saying is, it's impossible to tell by looking at a filename, whether or not it's an executable? And, in order to know which file will execute an application, I would have to right click it, and select "Properties" and then tab to "permissions"?

I'm not sure I understand that. LOL 

> **hyper_ch said:**
> whether a file is executable doesn't depend on the file extension... I still wonder why M$ does that... but it depends on the permissions on the file.

---

### Post by Fixman on 2007-10-06
Yes, there is a way:

go to properties of the files, on permissions tab, and see if the "allow executing this file" tick is on.

EDIT: What program is that you want to know how to execute it? maybe we could help with that.

---

### Post by HermanAB on 2007-10-06
If you really want to 'organize' things the way you like it, edit the desktop system menu.  Don't ever move a binary file.  On Linux, the system is extremely modular.  There are thousands of executables in /bin, /sbin and /usr/bin.  

These utilities are highly interdependent and many programs simply assume that a certain utility exists.  (There is something called the Linux Standards Base - LSB, so it not quite anarchy.) The important point is that if you delete one little program, then it can break lots of things.  

Ferinstance, delete /bin/bash and your system is totally fsck'ed...
;)

---

### Post by Soarer on 2007-10-06
> **evets said:**
> So, what you're saying is, it's impossible to tell by looking at a filename, whether or not it's an executable?


Correct. This is not Windows, remember. Sometimes there are better ways than the MS way...

> **evets said:**
> 
 And, in order to know which file will execute an application, I would have to right click it, and select "Properties" and then tab to "permissions"?

I'm not sure I understand that. LOL

No. Usually, you just find it in the menus, just like in Windows. If its not in the menus, it's easy to put it in. If neither of those suit you, just open a terminal and type it's name.

---

### Post by evets on 2007-10-06
Thanks for the reply. I've had several I wanted to run, but, for the sake of learning, I'd like to know how to id files.

Some day, I want to graduate from n00bness. :lolflag:



> **Fixman said:**
> Yes, there is a way:

go to properties of the files, on permissions tab, and see if the "allow executing this file" tick is on.

EDIT: What program is that you want to know how to execute it? maybe we could help with that.

---

### Post by evets on 2007-10-06
To begin with, Yes, I am very familiar with windows, but, I don't care about windows or how windows does things. I just want to learn Linux/Ubuntu.


> **Soarer said:**
> Correct. This is not Windows, remember. Sometimes there are better ways than the MS way...


If I can't identify which file should be placed in the menu...:)?

No. Usually, you just find it in the menus, just like in Windows. If its not in the menus, it's easy to put it in. If neither of those suit you, just open a terminal and type it's name.


Not for us noobs, it ain't! :(

> it's easy to put it in


BTW, do you guys use top or bottom posting to quotes here?

---

### Post by Soarer on 2007-10-06
If you install a program from the repositories, usually it will put itself in the menus.

If not, right click on the top left of the screen, and 'edit menus'. You can put programs on menus which are not already there, or create a launcher for items you have found.

We would really like to know what sort of programs you are talking about - for me, either they appear in the menus or run from a terminal, but the latter only usually for utilities.

---

### Post by evets on 2007-10-06
gfreqlet was one, and it took me two days to get Advanced Desktop Effects Settings on the menu. A non repo one was Claws-Slypheed mail.

Sometimes, I find that an app is already installed, but I can't find the correct file to associate with a launcher for the menu. 

BTW, can you help me in getting flash for Opera installed? :) Flash works for everything else...FF, Konq., etc. I have d/l'd install_flash_player_9_linux.tar.gz , tried to install it, but no success.

Thanks for all your help.




> **Soarer said:**
> If you install a program from the repositories, usually it will put itself in the menus.

If not, right click on the top left of the screen, and 'edit menus'. You can put programs on menus which are not already there, or create a launcher for items you have found.

We would really like to know what sort of programs you are talking about - for me, either they appear in the menus or run from a terminal, but the latter only usually for utilities.

---

### Post by olejorgen on 2007-10-06
> **evets said:**
> Nice thread. More questions. :)

How does a former windows user know which icon to click on to start an app? What would the extension be that executes it?

I thought if it was in the /usr/bin folder it was an executable, but I'm wrong. I have apps installed that I can't find and/or can't execute if/when I do find them. It's driving me nuts because it's so hit and miss. 

Thanks for any direction you can give.
Most likely these executables expect to run from a terminal. They have no gui, so if you simply dobble click it you won't see anything happen. (I think nautilus should give you a choice to "run in terminal" though)

---

