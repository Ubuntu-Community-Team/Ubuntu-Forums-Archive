---
title: "Background color change?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by rwhillman on 2007-02-06
Is there a way to change the basic window background color (white) to something else? Some  applications allow but I am looking for a universal change to something less glaring (probably light gray).

---

### Post by ComplexNumber on 2007-02-06
> **rwhillman said:**
> Is there a way to change the basic window background color (white) to something else? Some  applications allow but I am looking for a universal change to something less glaring (probably light gray).
right click on the desktop and select 'change desktop background'. you can select the colour there.

---

### Post by jordanmthomas on 2007-02-06
These will probably be your best bet unless you want to learn how to edit GTK themes:
[http://art.gnome.org/themes/gtk2/](http://art.gnome.org/themes/gtk2/)

---

### Post by wildseven on 2007-02-06
i think he is talking about the terminal. it's ugly white ahah. 

If you are talking about the terminal go to
edit > current profile > colors tab.

you can change there color here and the effects tab can do cool stuff too like transparency.
hope this helps.


-seven

---

### Post by ComplexNumber on 2007-02-06
ahhh yes, i see now. 
**rwhillman**
i guess you're talking about application background rather than desktop background. in that case, i would recommend an application called gnome-color-chooser [here]("http://gnome-look.org/content/show.php?content=47349"). it allows you to change lots of colour aspects of the applications and desktop etc, irrespective of what theme is installed. the screenshots will show what i mean with before and after shots.

---

### Post by wildseven on 2007-02-06
awww i strike out again! i thought i solved his problems! oh well, i can't compete with a master roaster! hahaha. i wish i had more than a carafe of ubuntu! haha. perhaps a surplus of ubuntu ^^:lolflag:

---

### Post by rwhillman on 2007-02-06
Let me clarify.  It is not the desktop background, which is easy to change.  It is the white background in every window.  In Windows, there is an option to change the background to any color.  It looks like the gnome-color-chooser may address this, but I am a little worried at installation being over my head.

---

### Post by ComplexNumber on 2007-02-06
> **rwhillman said:**
> Let me clarify.  It is not the desktop background, which is easy to change.  It is the white background in every window.  In Windows, there is an option to change the background to any color.  It looks like the gnome-color-chooser may address this, but I am a little worried at installation being over my head.
-download the file to your home directory. then right click on the file, select 'extract here'. then fire up the terminal and go into where you extracted the file. for example, if your username is rwhillman and the file extracted to /home/rwhillman, creating a directory called gnome-color-chooser-0.1.3, then fire up the terminal and type in the following:
**cd /home/rwhillman****/gnome-color-chooser-0.1.3**

then type in **./configure**. wait for it to finish.
then type in **make**. again, wait for that to finish. then type in **sudo make install**

---

### Post by jordanmthomas on 2007-02-06
You wouldn't be able to install it that way on a vanilla installation.
```
sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev
```
You'll need these to build gnome-color-chooser.
Also, instead of make install you *may* need to use **sudo** make install

---

### Post by ComplexNumber on 2007-02-06
> **jordanmthomas said:**
> You wouldn't be able to install it that way on a vanilla installation.
```
sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev
```You'll need these to build gnome-color-chooser.
Also, instead of make install you *may* need to use **sudo** make install
ahhh heck! yes, you're correct. i forgot. i'll edit my post.

---

### Post by rwhillman on 2007-02-06
I much appreciate the help.  But I have install trouble.  Here is what I get --

bob@ubuntu:~$ cd /home/bob/Color/gnome-color-chooser-0.1.3
bob@ubuntu:~/Color/gnome-color-chooser-0.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by ComplexNumber on 2007-02-06
as jordanmthemeas has suggested, the following need to be installed:
[FONT=monospace]build-essentials 
libgtkmm-dev
libglademm-2.4-dev
libxml2-dev

install them wither by using synaptic or by typeing the following on the commandline:
[B]sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev


[/B]then run the configure script again.


[/FONT]

---

### Post by rwhillman on 2007-02-06
Thanks again.  Install seemed to go OK with exception that Bug Buddy popped up.  Now I am trying to figure out out to open the program.

---

### Post by rwhillman on 2007-02-06
Got it!.  Thanks.  This is exactly what I was looking for.

---

### Post by rgd55 on 2007-03-28
I am having trouble getting this program to configure.
I was able to complete the
sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev,
but for some reason I can't seem to get the program to load.
This is what I typed in my terminal,
rgd@linux07:~$ cd: /home/rgd/gnome-color-chooser-0.1.3./configure
bash: cd:: command not found
:confused:

---

### Post by ComplexNumber on 2007-03-28
> **rgd55 said:**
> I am having trouble getting this program to configure.
I was able to complete the
sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev,
but for some reason I can't seem to get the program to load.
This is what I typed in my terminal,
rgd@linux07:~$ cd: /home/rgd/gnome-color-chooser-0.1.3./configure
bash: cd:: command not found
:confused:
fire up the terminal and type in the following:
[B]cd[COLOR=White]...[/COLOR]~/gnome-color-chooser-0.1.3

[/B]NOTE: the tilde(ie '~') is merely a shorthand for your home directory. it saves on typing :p.

then type in the folliowing:
**./configure **

---

### Post by rgd55 on 2007-03-28
ok gave it a try
rgd@linux07:/$ cd ~gnome-color-chooser-0.1.3./configure
bash: cd: ~gnome-color-chooser-0.1.3./configure: No such file or directory

---

### Post by ComplexNumber on 2007-03-28
> **rgd55 said:**
> ok gave it a try
rgd@linux07:/$ cd ~gnome-color-chooser-0.1.3./configure
bash: cd: ~gnome-color-chooser-0.1.3./configure: No such file or directory
please type it in _EXACTLY_  like i've shown.

copy and paste it if necessary.


NOTE: also, i hope you've extracted the contents of the tarball beforehand.

---

### Post by rgd55 on 2007-03-29
Thanks for the help.I am still have difficulty getting this to work.I have copyed
and pasted your script text into my terminal,here is the results.

rgd@linux07:~$ cd...~/gnome-color-chooser-0.1.3./configure
bash: cd...~/gnome-color-chooser-0.1.3./configure: No such file or directory

You noted,"i hope you've extracted the contents of the tarball beforehand."
My reply is that I have followed this thread and used this script,
sudo apt-get install build-essential libgtkmm-dev libglademm-2.4-dev libxml2-dev
This script compleated without errors as far as I could tell.

---

### Post by ComplexNumber on 2007-03-29
```
cd...~/gnome-color-chooser-0.1.3./configure
```its not working because you're  not writing it exactly as i've said (note: those dots inbetween the "cd " and the "~/gnome-color-chooser-0.1.3" shouldn't be there. i just put them in white so as to make it omre readable to you by spacing everything out).
lets start again...


copy and paste the following in the terminal
[B]cd ~/gnome-color-chooser-0.1.3

[/B]now press the RETURN key

type in the following:
[B]./configure

[/B]now press the RETURN key and wait for the configure script to complete.

the last 5 or so lines of the configure script should give you an indication of if there are any errors or not. errors may be where it is saying that 1 or more packages can't be found. 

if it completed without any  errors, then type in the following:
**make**

now press the RETURN key and wait for the script to complete.

if there don't appear to be any errors, type in the following:
**sudo make install**

---

### Post by rgd55 on 2007-03-29
I appreciate your patience and help.I am at work now will give this a try
in a few hours.I'll post an update then.

---

### Post by rgd55 on 2007-03-29
ComplexNumber,
   
You asked me to
[B]copy and paste the following in the terminal
cd ~/gnome-color-chooser-0.1.3[/B]





I seem to be stuck at this command.Here is a cut/paste of my terminals results.
[B]rgd@linux07:~$ cd ~/gnome-color-chooser-0.1.3
bash: cd: /home/rgd/gnome-color-chooser-0.1.3: No such file or directory
[/B]

---

### Post by ComplexNumber on 2007-03-29
gnome-color-chooser came in a package which had the extension "tar.gz" or "tar.bz2" didn't it? well, you haven't unzipped it have you? :p.

ok, right click on the package and select 'extract here'. assuming it extracts to a directory called gnome-color-chooser, you need to go inside that directory with the terminal. you will see a lot of files, one of them is called "configure". thats the file that you run when you execute the command "./configure".

---

### Post by rgd55 on 2007-03-29
I need a your help extracting the file.I have it located in /home/rgd and when I right click I several options.I don't know how to extract to a directory called gnome-color-chooser.

---

### Post by rgd55 on 2007-03-29
I also see it here
[B]rgd@linux07:~$ ls
47349-gnome-color-chooser-0.1.3.tar.bz2  fs-manual.pdf         System Utils
Desktop                                  Personal              System Utils~
Examples                                 RealPlayer10GOLD.bin
[/B]

---

### Post by Drakkor on 2007-03-29
I think my install was correct, now how do I open the program ??

---

### Post by ComplexNumber on 2007-03-29
> **Drakkor said:**
> I think my install was correct, now how do I open the program ??
i don't quite understand. it should be in the menu under main menu -> system -> preferences.



ok, guys, [here]("http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/gnome-color-chooser_0.1.3-3v1ubuntu0_i386.deb") is a deb file. hopefully that will make things easier. to install it, fire up the terminal and go to the directory where you've downloaded it to. then type the following into the terminal:
[B]sudo dpkg -i gnome-color*

[/B]also, ensure that you have the dependencies listed in post 12(and beforehand) of this thread before you install it. install the dependencies, then try installing gnome-color-chooser again[B].
[/B]

---

### Post by Drakkor on 2007-03-29
Cool, thx ComplexNumber   the .deb file did the trick, and now it's in System>Preferences :)

---

### Post by rgd55 on 2007-03-29
Well.I still have a problem.I wonder if I need to reinstall the dependencies.
My terminal readings:
[B]rgd@linux07:~$ sudo dpkg -i gnome-color*
Password:
dpkg-split: error reading gnome-color-choser: Is a directory
dpkg: error processing gnome-color-choser (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 gnome-color-choser
[/B]rgd@linux07:~$ sudo dpkg -i gnome-color*
Password:
dpkg-split: error reading gnome-color-choser: Is a directory
dpkg: error processing gnome-color-choser (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 gnome-color-choser

---

### Post by Drakkor on 2007-03-29
Try just double clicking the .deb file, that should start up the package manager and install it with no problems !

---

### Post by rgd55 on 2007-03-29
ok,I'll try that.

---

### Post by rgd55 on 2007-03-29
Ok,I have it now:) 
Hopefully one day I'll learn to do the installs from the terminal.
Thanks ComplexNumber and Drakkor

---

### Post by rgd55 on 2007-03-29
One last question,can the /home/rgd/47349-gnome-color-chooser-0.1.3.tar.bz2
file now be deleated?

---

### Post by jordanmthomas on 2007-03-29
Yes.

---

### Post by rgd55 on 2007-03-29
Thanks
:)

---

