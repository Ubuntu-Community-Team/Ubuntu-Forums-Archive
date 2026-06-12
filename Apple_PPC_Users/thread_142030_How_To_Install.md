---
title: "How To Install"
date: 2006-03-09
forum: Apple PPC Users
---

### Post by E.M.P99 on 2006-03-09
hi i just installed kubuntu and i'm very confused:confused:  over how to install apps. the way i see it there r 2 ways to install apps. 1 to compile the source code (sounds very hard) . 2 some how edit the source.list in ext/apt so u can download pak's thru some kind of download manger.

i also saw some app mentioned at linuxqwuestions fourm that installs thing for u

i'm just a noob look'in for help:-k :-k

---

### Post by Princey on 2006-03-09
What kind of applications are you looking for? It's not as hard as it sounds. Most 3rd party programs comes with the directions, and hey, there's a wealth of information out there to help. Editing your sources.list isn't that difficult. In fact, if you search through the threads here, you'll find lots of help. Most times, I just copy and paste the commands from the posts and advice given and it works. Give it a go, you won't know until you reach there. We're here to learn from each other. That's how the Linux community grows. Good luck.:)

---

### Post by sarcasticfrench on 2006-03-09
Usually you won't need to edit your sources.list file unless you can't find what your looking for in Adept. Adept is the package manager for Kubuntu. In case you don't know, a package manager is an application that bundles the download and install steps into one, so that you simply hit "install package" and then "commit changes" and it does the rest on it's own. To get into adept, either go into the K menu and go into the "system" section, or hit alt-space and then type Adept, then hit enter. It will then ask for your password, and after you enter it the program will appear. I hope this answers your question!!

---

### Post by Sutekh on 2006-03-09
[QUOTE=E.M.P99]
i'm just a noob look'in for help:-k :-k[/QUOTE]

This is the link for you

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

That link will show you the many ways to install software in Ubuntu.  **Synaptic** is the package manager in question.  It is a very easy way to install new packages.  Other methods are also shown, including compiling source code, which can be hard indeed.

There are other helpful links there including enabling repositories.

---

### Post by ronrafajko on 2006-03-10
Is there a way to use Synaptic Package Manager (SPM?) to install a .deb file I downloaded? 

I did not see a way to use it other than searching for a program on a site listed in the 
/etc/apt/sources.list file.

THANKS!

~ron in american fork, utah

---

### Post by RJMacReady on 2006-03-10
In a terminal, change to where you saved the file, and type: ```
sudo dpkg -i thepackagename.deb
```

The **-i** option is install. Use **-r** to remove.

You could just right click the .deb and open it with Debian Package Manager. But meh, thats too easy! :)

---

### Post by ronrafajko on 2006-03-11
I origionally tried to open the package in SPM, but saw no options built in.
I right click on the file and I have the options to open it with "Archive Manager", or to "gksudo", or Open with other Application... .  

I selected the latter and of course the only applications that come up are the simple menu items, no SPM.  I browse to SPM in /usr/sbin/synaptic and it says that it needs to be launched as root.  I logout and try to login as root and it says root can not log in from this screen.  :( 

I go back and right click on the file and I now see Synaptic as an option, but it still needs to run as root user.  I check the properties of the SPM icon on my tool bar and the path is listed as gksudo /usr/sbin/synaptic (whatever gksudo is?).  I put that in the path for Open other application and it asks me to log in (why does it ask for my password and not root's password?).  SPM comes up but I see no xxx.deb file listed, the one I right clicked on.  :cry: 

Maybe I will try the command line with: sudo dpkg -i thepackagename.deb.  I don't mind using it, I just don't know if there is a problem mixing the two.

THANKS!

~ron in american fork, utah

---

### Post by Sutekh on 2006-03-11
[QUOTE=ronrafajko]Is there a way to use Synaptic Package Manager (SPM?) to install a .deb file I downloaded? [/QUOTE]Not that I know of.  If you download a .deb the best way to install is as RJMacReady suggested.

[QUOTE=ronrafajko]I selected the latter and of course the only applications that come up are the simple menu items, no SPM. I browse to SPM in /usr/sbin/synaptic and it says that it needs to be launched as root. I logout and try to login as root and it says root can not log in from this screen.[/QUOTE] By default the root account in Ubuntu is disabled.  Ubuntu uses the command **sudo** to temporarily run something "as root".

[Ubuntu Wiki - RootSudo](wiki.ubuntu.com/RootSudo) explains how it all works.

[QUOTE=ronrafajko]
I go back and right click on the file and I now see Synaptic as an option, but it still needs to run as root user. I check the properties of the SPM icon on my tool bar and the path is listed as gksudo /usr/sbin/synaptic (whatever gksudo is?).[/QUOTE]**gksudo** works the same way as sudo.  The only difference being is that it is used when launching graphical applications rather than from a command line.

So an example is **gksudo synaptic**  (the /usr/sbin is not required)

[QUOTE=ronrafajko]I put that in the path for Open other application and it asks me to log in (why does it ask for my password and not root's password?). [/QUOTE]The first user of an Ubuntu system (by default) is given the right to use **sudo**, but requires entering your user's password to use sudo.

All this stuff is covered in the Wiki link, and its one of the most asked question on the forum too, so there are plenty of threads covering the use of sudo.

[QUOTE=ronrafajko]SPM comes up but I see no xxx.deb file listed, the one I right clicked on.

Maybe I will try the command line with: sudo dpkg -i thepackagename.deb. I don't mind using it, I just don't know if there is a problem mixing the two.[/QUOTE]
There shouldn't be a problem mixing the two.  

The only problem I can think of is that the .deb should have been specifically created for Ubuntu.  I would be careful installing a .deb created for Debian, etc.

---

