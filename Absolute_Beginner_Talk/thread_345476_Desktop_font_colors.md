---
title: "Desktop font colors"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2007-01-24
I've searched through these forums and I've investigated the help mauals.   It appears Ubuntu/Gnome does not allow the user to change desktop font colors via a simple gui interface.

I really don't want to do a hack to system files.  I'd really like to see some simple GUI checkbox, button or toggle switch.

Anyone know if anything like this is available? Maybe a plug-in of some sort?  If not, I'll just have to choose walllpapers with dark backgrounds.

---

### Post by ComplexNumber on 2007-01-24
use [this]("http://gnome-look.org/content/show.php?content=47349"). select the desktop tab. the screenshots show you the before and after of changing the icon colours. you can even apply a wallpaper background to the background of the icon text.

---

### Post by georgetoon on 2007-01-24
Very nice!:)  when I download the source, where do i install (or save to)?  I haven't done much beyond using the Ubuntu add/remove software installation tool.

Many, many thanks for this!:)

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> Very nice!:)  when I download the source, where do i install (or save to)?  I haven't done much beyond using the Ubuntu add/remove software installation tool.

Many, many thanks for this!:)
i unzipped the source and, on the command line,  typed the following: [B]
./configure --prefix=/usr[/B]

then
[B]
make[/B]

then

**make install**.



after its installed, you will find an entry called gnome color chooser in main menu -> system -> preferences.

---

### Post by georgetoon on 2007-01-24
I'm doing al this and it's not working. I keep getting a message saying the command is wrong.

I dunno...I'm still a gui person.

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> I'm doing al this and it's not working. I keep getting a message saying the command is wrong.

I dunno...I'm still a gui person.
do you mean that its not compiling?
if its not compiling, did you have a look at the dependencies? the dependencies are these:
[B] - libgtkmm >= 2.8.0
- libglademm >= 2.6.0
- libxml2 >= 2.6.0[/B]




install them via synaptic or by using apt-get, and tell me if it now configures.


btw one thing i noticed that if it failed in compiling, it was necessary to delete the unzipped source. then unzip the source package again. i don't know why. so keep the source package around until its installed (just in case)

---

### Post by georgetoon on 2007-01-24
Running synaptic and can't find vesion greter than 2.8. Appears I'm runnig 2.4

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> Running synaptic and can't find vesion greter than 2.8. Appears I'm runnig 2.4
yeah, you're right. well, mine still works anyway, so i don't know whats going on there. maybe the person who stated the requirements got something wrong. ok, forget about version numbers, just install those files mentioned irrespective of what version they are.

---

### Post by georgetoon on 2007-01-24
> **ComplexNumber said:**
> yeah, you're right. well, mine still works anyway, so i don't know whats going on there. maybe the person who stated the requirements got something wrong. ok, forget about version numbers, just install those files mentioned irrespective of what version they are.

Again, I'm pretty dense about this.  Am I typing exactly "./configure --prefix=/usr?"

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> Again, I'm pretty dense about this.  Am I typing exactly "./configure --prefix=/usr?"
its ok, don't worry :). 
yes, fire up the terminal and go into the directory where you unzipped gnome-color-chooser. then type in the following at the terminal:
[B]./configure --prefix=/usr


[/B]wait until thats done (about 2-4 minutes). then type in "**make**"(without the quotes). then wait for that to finish (about 5 minutes), then type in "**make install**"(without the quotes)

---

### Post by georgetoon on 2007-01-24
Dang! I exracted this to the desktiop. I'm in the desktop by default when in teminal.  The location is: "myusername@myusername-desktop"~$"

so, this should work, right? the folder is right on the desktop.

I'm not doing something corectly.

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> Dang! I exracted this to the desktiop. I'm in the desktop by default when in teminal.  The location is: "myusername@myusername-desktop"~$"

so, this should work, right? the folder is right on the desktop.

I'm not doing something corectly.
it makes no difference if its on your desktop or not. now just use the "cd"(ie **c**hange **d**irectory) command so that you are in where you extracted the source file. you should see a load of files, one f them being a file caled "configure". now just run the ./configure command.

---

### Post by georgetoon on 2007-01-24
> **ComplexNumber said:**
> it makes no difference if its on your desktop or not. now just use the "cd"(ie **c**hange **d**irectory) command so that you are in where you extracted the source file. you should see a load of files, one f them being a file caled "configure". now just run the ./configure command.

Yes, I understand.:) I'm trying to change to this directory which is a folder on the desktop. the foldr is called "gnome-color-chooser-0.1.3." i nee to get into this folder (directory).I'm typing in "cd/gnome-color-chooser-0.1.3." nothing.

"cd gnome-color-chooser-0.1.3"  nothing.

I'm obviously executing the "cd' command wrong.

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> Yes, I understand.:) I'm trying to change to this directory which is a folder on the desktop. the foldr is called "gnome-color-chooser-0.1.3." i nee to get into this folder (directory).I'm typing in "cd/gnome-color-chooser-0.1.3." nothing.

"cd gnome-color-chooser-0.1.3"  nothing.

I'm obviously executing the "cd' command wrong.
you can use wild cards. i rarely, if ever, type in the whole thing. for example, if the terminal is open at */home/<my-username>/Desktop* and i want to get to  */home/<my-username>/Desktop/gnome-color-chooser-0.1.3, *i will just type in "cd gn*". that assumes that there isn't another file on the desktop that begins with "gn". if there was another directory on the desktop called (for example) "gnomefiles", then i would type in: "cd gnome-*".

---

### Post by georgetoon on 2007-01-24
> **ComplexNumber said:**
> you can use wild cards. i rarely, if ever, type in the whole thing. for example, if the terminal is open at */home/<my-username>/Desktop* and i want to get to  */home/<my-username>/Desktop/gnome-color-chooser-0.1.3, *i will just type in "cd gn*". that assumes that there isn't another file on the desktop that begins with "gn". if there was another directory on the desktop called (for example) "gnomefiles", then i would type in: "cd gnome-*".

thank you somuch.:) You've been really helpful andpateint with me.

EDIT:  wait! I'm not on the dsktop! DUH! Okay, I'm in the directory! Here we go!:)

---

### Post by ComplexNumber on 2007-01-24
well, let me know in a few minutes or so how you get on. it should take about 5 or so minutes in total to configure and make.

---

### Post by georgetoon on 2007-01-24
yikes1 I was wrong. apologies
> 
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtkmm-2.4 >= 2.8.0 libglademm-2.4 >= 2.6.0 libxml-2.0 >= 2.6.0 ) were not met:

No package 'gtkmm-2.4' found
No package 'libglademm-2.4' found
No package 'libxml-2.0' found

i do not havde these packages installed.  Ijust checked to install them,. Only the last one does not come up in synapatic.

---

### Post by ComplexNumber on 2007-01-24
> **georgetoon said:**
> yikes1 I was wrong. apologies


i do not havde these packages installed.  Ijust checked to install them,. Only the last one does not come up in synapatic.
i imagine its because you haven't enabled universe and multiverse repositories.
go into synaptic. then go into 'settings' in the menu, then 'repositories'. then press 'close'. it should ask you to reload the info. reload, then search for those packages.


EDIT: make sure that you have the "dev" packages installed for all of them. eg libglademm-2.4-dev

---

### Post by georgetoon on 2007-01-25
> **ComplexNumber said:**
> i imagine its because you haven't enabled universe and multiverse repositories.
go into synaptic. then go into 'settings' in the menu, then 'repositories'. then press 'close'. it should ask you to reload the info. reload, then search for those packages.


EDIT: make sure that you have the "dev" packages installed for all of them. eg libglademm-2.4-dev

Okay.:) I'll do this tonight.:)  I'm not in front of my Linux computer right now.  I was called away last night so was not able to get back up here.  Apologies.

Really looking forward to gettin ghtis installed.:)  And learning a lot along the way!:)  Again, many thanks!:)

---

### Post by ComplexNumber on 2007-01-25
oklie dolkie. here is another useful tip when you are installing packages from source:

often, it mentions that a package has some extra dependencies. in this case, they are gtkmm-2.4, libglademm-2.4, and libxml-2.0. 
when you are running the configure script, it looks in /usr/lib/pkgconfig and /usr/local/lib/pkgconfig to see if those dependencies are met. in each of those 2 directories, it contains lots of ".pc" files, and each one of those specifies the version of the package thats installed (amongst other info). if the configure script can't find the relevant pc file, it will believe that the package is not installed. 
now, the important point to realise is, the pc files ARE ONLY INSTALLED WITH THE "DEV" PACKAGES, so even if you have gtkmm-2.4 installed, the configure script won't be able to detect that gtkmm-2.4 is installed unless the gtkmm-2.4-**dev** package is installed too.

thats just something to be aware of just in case you disctincly remember installing a package, but the configure script complains that a package isn't installed. its because you haven't got the dev package installed too.

---

### Post by georgetoon on 2007-01-25
Okay, I went into Synpatic, I reloaded the repsositories, everything is checked, everything reloaded and it stil wil not find libxml-2.0. :confused: 

Oh, well.

I appreciate the help, guys.) I've learned a lot.:):D Many, many thanks!:):KS 

I'm just going to wait for some other kind of component for this...maybe Automatix will begin to include something.

Gotta go outside now and see if I have to run the snowblower again.  Possible 1-2 
feet of the white stuff on the way.

---

### Post by ComplexNumber on 2007-01-26
look for libxml2 and try again.

---

### Post by georgetoon on 2007-01-26
> **ComplexNumber said:**
> look for libxml2 and try again.

Yes!:) That worked!:) Thank you!:)

I beleive I have all the files.:) Look how far icame until it stopped.:)

> /Desktop/gnome-color-chooser-0.1.3$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking for style of include used by make... none
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... no
checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by ComplexNumber on 2007-01-28
install gcc (and its dev file)

---

### Post by Xappe on 2007-01-28
install the build-essential package

---

