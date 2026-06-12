---
title: "Need Help Learning The Linux File System"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-03
Ok, so after something like 20 years of Windows experience, I am taking the Linux plunge.

So far, I have found Ubuntu a pleasure to work with. Very simple and intuitive interface, and much quicker and easier on my hardware than that huge cow of an OS, named Vista. (No insult intended to cows.)

I started getting kinda twitchy when my new laptop seemed to be ready to blow a circuit board trying to run Microsoft's newest memory hog. :D

However, I am experiencing one area where the learning curve seems to be kicking my ***: The file system.

I am not really sure where to go, or what to do, when I need to locate a file. 

I am so used to the old C: > Program Files > JoeBob Software > ShotgunShanty.exe

Anyone have a good website that can teach me to make this transition?

Any help, hints, tips, tricks, etc. for a Linux newb would be greatly appreciated. 

Thanks!

---

### Post by Inxsible on 2007-07-03
In Ubuntu, some applications will create the menu list for you under Applications. 
An example of this is the NTFS Configuration Tool when installed from Add/Remove, or EasyTag, Exaile etc etc.
 
Yet others will not, and so you will have to manually create them. An example of this is the Eclipse IDE when installed NOT from the reps but from eclipse.org itself. 
 
Then there are some applications that do not really make sense opening up by themselves, and so sometimes its difficult to create the menu items for them. An example of this could be any codecs that you need to install for mp3 and/or video files to work, like GStreamer plugins etc.

---

### Post by yagood on 2007-07-03
Sure! For starters it's always a good idea to type something in Google. "linux file system" in this case gives us this nice article:

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

It explains file system layout, which directory is for what files etc.

Another quick tutorial:

[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

Here's a good one, altohugh a bit more "technical" - "Why doesn't Linux need defragmenting?":

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Also if you have any specific questions / doubts regarding file system navigating, maintenance etc. don't hesitate to ask here!

EDIT:

Oh, and remember, in Linux, everything is a file! Even hardware devices (check /dev/)!

---

### Post by cairnsww on 2007-07-03
I found this diagram very helpful - I have printed it out and keep it next to my computer!

[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

---

### Post by TheBlackWizard on 2007-07-03
Thanks for that center link, Ya...

That is a true blessing....

Cause I was sitting here looking at all these directories, thinking "What the hell is this?"

:D

---

### Post by hyper_ch on 2007-07-03
Basically when you install some program it will put itself in the according dirs which are also in your path environment variable.

This means if you install a programme called "xyz" then you run it by issuing "xyz" ;)

---

### Post by TheBlackWizard on 2007-07-03
Congrats!

You just confused the hell out of a newbie!

:KS

That star is just for you!

Issue command? Huh? Path Variable? WTF?

---

### Post by yagood on 2007-07-03
> **TheBlackWizard said:**
> Congrats!

You just confused the hell out of a newbie!

:KS

That star is just for you!

Issue command? Huh? Path Variable? WTF?

Start the terminal and type:

```
echo $PATH
```

PATH is a name of environmental variable - variable that always lives in your system after you login.

This echo command above will display list of directories separated by ":". Most notably there are "bin" directories there. This means that if you type (=issue :)) some command in the terminal, for example...

```
firefox
```

...the system will search for firefox executable file in those directories. Firefox is "in your path" (that's a shortcut for saying "Firefox exectuable is in the directory that is listed in PATH env variable") so Linux is going to find it and run it. Most of the programs install themselves in those "PATH directories" so that you don't have to run them by entering full path (/usr/bin/firefox is not needed for that reason).

Now bonus! Type in the terminal:

```
which firefox
```

It'll display full path of the executable which is run after you type simply "firefox".

PS. Can I get that star too? :-)

---

### Post by Praill on 2007-07-03
> **hyper_ch said:**
> Basically when you install some program it will put itself in the according dirs which are also in your path environment variable.

This means if you install a programme called "xyz" then you run it by issuing "xyz" ;)
Ya.. this approach has always confused me. Maybe someone can explain to me why it's like this?
Say I decide to make a program called gencat (just checked my /usr/bin for a random executable) and release a deb on my website unwittingly. A equally unwitting person might download my program and overwrite their already existing gencat executable. PLUS some programs will write to /bin or /usr/bin or /usr/local/bin leaving the user to a heap of guesswork when trying to locate it. Furthermore, the modules will be installed in /usr/lib, the config files in /etc, the manual for the command in /usr/man, the help files somewhere else, etc, etc. Then I have to trust that all these random files in random locations are getting properly removed. 

It seems much smarter to me to install ALL program files in a centralized area like windows does. I have always hated and not understood the way linux does this.

---

### Post by yagood on 2007-07-03
> **Praill said:**
> Then I have to trust that all these random files in random locations are getting properly removed. 

It seems much smarter to me to install ALL program files in a centralized area like windows does. I have always hated and not understood the way linux does this.

I think package managers are doing great job in this area. In Synaptic you can easily check package's installed files in properties - there you always have executable, configuration files, documentation etc.

---

### Post by phizikal on 2007-07-03
[IMG]http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.0/userguide-9.0/verzeichnisse_baum.png[/IMG]

---

### Post by Bd0g on 2007-07-03
The linux file tree is indeed a scary place if your new and are used to windows way of managing some stuff.

It's like landing in a very unfriendly and unrecogniseable territory where logic is missing. 
The only safe haven you have from the start is your "home" folder and that one looks like it landed right into the system32 folder in windows at first sight ;)

Windows has a giant score in this issue when it comes to make it friendly for newcomers. Looks mean so much if you are thinking about moving over. Coming from "Program Files" to sbin,bin,opt and so on... is ... like holding something soft and trading it for a rough branch with  sharp pointy sticks.

You get the feeling that you wont comprehend much from the system right away and think: 
- Hmm, maybe they're right, linux is not friendly.. and I still have all my stuff working in my other OS...

That's just my initial thoughts and feelings on what makes it hard for some to transition.

---

### Post by yagood on 2007-07-03
I guess it comes from the fact that most people just doesn't know anything besides Windows and are extremely used to Microsoft way. It takes a little curiosity and open-mindedness to learn the Linux / Unix way, which starts to make sense after a while.

---

### Post by zodmaner on 2007-07-03
Hi 

If you're completely new to Linux then I suggest you read this guide:
**[Introduction to Linux]("http://tldp.org/LDP/intro-linux/html/intro-linux.html")**

Which is a very informative guide for anyone getting started with Linux. It describes various fundamental concepts of Linux system in a non-technical way and also included a short description of Linux file system.

To locate a file, one of the options is to use **locate** command.

For example: type *locate xorg.conf* in a terminal to search for xorg.conf file.
> 
smith@smith-desktop:~$ locate xorg.conf
/etc/X11/xorg.conf
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.roster
/var/lib/x11/xorg.conf.md5sum
smith@smith-desktop:~$ 

Type *man locate* in terminal to learn more about advance function of the command.

Oh, and welcome to Linux (and Ubuntu). :)

---

### Post by hyper_ch on 2007-07-03
> **Praill said:**
> It seems much smarter to me to install ALL program files in a centralized area like windows does. I have always hated and not understood the way linux does this.

Windows doesn't install all program files in a centralized area ;)

you got c:\windows or c:\winnt and you got c:\Program Files
All of those locations containt program files ;)

and actually I find the unix/linux way meanwhile much smarter than the windows one. It offers a lot more flexibility.

---

### Post by Benoone on 2007-07-03
I just couldn't let this one go....

I may be a real n00b with Linux but about Windoz, I sure do know a thing or two.

I just un-installed CorelDraw13 and when it was finished it left 522 entries in that undocumented thingy they call THE REGISTRY!

Then, there were all those nasty files left over in the program files/common folder plus files in the temp folders  plus a few .dll's that failed to un-register.  

It took me a good hour to find all the left over crap and an audit still shows the serial number is still registered somewhere in the registry which I can't seem to remove.  I'm no expert with Linux but it sure seems that *locate* and *whereis* are tools that will at least tell you where the stuff is. 

IMHO, it sure seems that everything about Windows is a big secret and if you happen to stumble on one of it's secrets then Billy Gates and his legal slime-balls want to sue the living daylights out of you and drag you into the dust as they are now trying to do with RedHat. 

Sorry for the rant but Vista is still the best thing that has ever happened to Linux.

Just my two cents so take what you like and ignore the rest.

To all the above posters, thank you for your fine and helpful input.  Maybe someday I'll be able to know one half as much as you do.

Regards

Benoone

---

### Post by hyper_ch on 2007-07-04
> **Benoone said:**
> 
Maybe someday I'll be able to know one half as much as you do.

This day comes sooner than you may think :)

---

### Post by Bd0g on 2007-07-06
> **Benoone said:**
> 
Sorry for the rant but Vista is still the best thing that has ever happened to Linux.

Agreed ;)

---

### Post by tbresson on 2007-07-06
I share your confusion on the filesystem but I've worked with Ubuntu for a while now and it's not that often you need to know so much about it. Most programs install themselves anyway, and as one user wrote you can always search / locate the stuff you need (there's a gui search also besides the locate command).

Since it's confusing I suggest you start with adding programs via the Add/Remove feature and/or the Synaptec interface. The only bad thing about Synaptec is while it helps adding all the extra stuff you need when installing e.g. a webserver it doesn't do a very good job removing those things again. There are alternatives to Synaptec but it will do for most).

The last suggestion is that you roam around your home dir, when installing don't be affraid that it not the "correct" way to do it, install programs on your Desktop if you like ;-) (Just wait until you get to file permissions .. you won't get anything done if you want everything to be just right).

You get to learn linux / Ubuntu pretty fast by trying out new stuff and unlike Windows it doesn't take that long to install if you mess up.

Ohh. I might aswell add this: You should check out the Virtualbox program. It's easy to install and I'll let you install any OS on top of your Ubuntu. You can even install the same Ubuntu inside VirtualBox. Then you can always try stuff out before you mess anything up (just remember to take snapshots of you OS each time).

Welcome to Ubuntu :)

---

