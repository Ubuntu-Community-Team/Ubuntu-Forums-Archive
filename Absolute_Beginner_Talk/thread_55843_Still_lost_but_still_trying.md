---
title: "Still lost but still trying"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by kairos911 on 2005-08-10
Okay, I don't want to go long, but I want to give enough detail that someone can get help.  I am working with tar.gz .  This is the first program I have tried to install.  I created "Sword" and that is where I unzipped the program.

I then read the Install file.  It states the following:

>  INSTALLATION NOTES


QUICKSTART

Try:

	./usrinst.sh
	make
	su
	make install

If you have never installed sword before and/or are happy with a default
configuration, you may wish to type:

    make install_config

for a basic configuration.  WARNING: THIS WILL OVERWRITE AN EXISTING
CONFIGURATION.  It is OK to rerun this if you have not changed any
parameters in /etc/sword.conf

If the above steps do not work, or if you're particular about your
configuration, please read on.


BUILD CONFIGURATION

What most people consider 'normal' user install options are saved in
a script 'usrinst.sh', which you may run with the command './usrinst.sh'.
You may want to have a look at the configuration options by typing
./configure --help and also looking at what we consider 'normal'
usage parameters by looking inside usrinst.sh
to be sure everything is being built the way that you would like.

 ](*,) Here's where I start to bang my head against the wall.  I open a terminal.  I cd to Sword and try to follow the instructions above.  Here's what I get:
```

kairos911@ubuntu2:~/Sword$ ls
gnomesword2-2.0.0  sword-1.5.8
kairos911@ubuntu2:~/Sword$ cd sword-1.5.8
kairos911@ubuntu2:~/Sword/sword-1.5.8$ make install_config
make: *** No rule to make target `install_config'.  Stop.
kairos911@ubuntu2:~/Sword/sword-1.5.8$ cd usrinst.sh
bash: cd: usrinst.sh: Not a directory
kairos911@ubuntu2:~/Sword/sword-1.5.8$ ./usrinst.sh
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

And the program still won't run.

Sorry for the length of this and thanks in advance for the help.

---

### Post by tonysathre on 2005-08-10
[QUOTE=kairos911]Okay, I don't want to go long, but I want to give enough detail that someone can get help.  I am working with tar.gz .  This is the first program I have tried to install.  I created "Sword" and that is where I unzipped the program.

I then read the Install file.  It states the following:



 ](*,) Here's where I start to bang my head against the wall.  I open a terminal.  I cd to Sword and try to follow the instructions above.  Here's what I get:
```

kairos911@ubuntu2:~/Sword$ ls
gnomesword2-2.0.0  sword-1.5.8
kairos911@ubuntu2:~/Sword$ cd sword-1.5.8
kairos911@ubuntu2:~/Sword/sword-1.5.8$ make install_config
make: *** No rule to make target `install_config'.  Stop.
kairos911@ubuntu2:~/Sword/sword-1.5.8$ cd usrinst.sh
bash: cd: usrinst.sh: Not a directory
kairos911@ubuntu2:~/Sword/sword-1.5.8$ ./usrinst.sh
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

And the program still won't run.

Sorry for the length of this and thanks in advance for the help.[/QUOTE]
 u need gcc and cpp and c++ ....just search synaptic for them...also get gawk

---

### Post by dcraven on 2005-08-10
sudo apt-get install build-essential

Cheers,
~djc

---

### Post by pmjdebruijn on 2005-08-10
Hi,

Is SWORD a bible study program?

Anyway try 'gnomesword', note that you need to add the universe repository...

Regards,
Pascal de Bruijn

---

### Post by KingBahamut on 2005-08-10
apt-get install gnomesword bible-kjv bible-kjv-txt gnomequran perspic-texts 

for the full experience.

---

### Post by kairos911 on 2005-08-10
\\:D/ Thanks for the help so far.  Still no "solution" but I am getting closer.  The machine finally ran a whole bunch of code.  Took it at least 5 minutes to complete.  This is after I installed several things like c++ as recommended.

Yes, Sword is a bible study program.  The idea is to immediately upgrade to SwordGnome.  However, the documentation says that I need Sword 1.5.6 first.

Anyway, on to the current situation.

In installing Sword I finally got to the point at the end that my terminal read:
```

collect2: ld returned 1 exit status
make[1]: *** [buildtest] Error 1
make[1]: Leaving directory `/home/kairos911/Sword/sword-1.5.8'
make: *** [install-recursive] Error 1
root@ubuntu2:/home/kairos911/Sword/sword-1.5.8 # ./apps
bash: ./apps: No such file or directory
root@ubuntu2:/home/kairos911/Sword/sword-1.5.8 # make install_config
/bin/sh: /usr/local/etc/sword.conf: No such file or directory
make: *** [install_config] Error 1
root@ubuntu2:/home/kairos911/Sword/sword-1.5.8 #
```

[buildbest] Error 1 is now where I am stuck

The instructions say to run ./apps but you can also see that gets me nowhere.

Again, I thank all for the help!  This rookie is learning and it is finally becoming fun.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=KingBahamut]apt-get install gnomesword bible-kjv bible-kjv-txt gnomequran perspic-texts 

for the full experience.[/QUOTE]

You mean "put this in a  regular terminal:"

> sudo apt-get install gnomesword bible-kjv bible-kjv-txt gnomequran perspic-texts 

---

### Post by kairos911 on 2005-08-11
Thanks for pulling a rookie along this far!  I used
```
 sudo apt-get install gnomesword bible-kjv bible-kjv-txt gnomequran perspic-texts
```
That was in a regular terminal and not root.

GnomeSword installed.

Now I am trying to install modules.  I downloaded the raw files through Windows and burned them on a CD.  Linux recognizes the files when I view them.

However, I now can't find a location into which they can be unzipped.

when I open a root terminal and type
```
root@ubuntu2:/home/kairos911 # cd /usr
root@ubuntu2:/usr # cd local
root@ubuntu2:/usr/local # cd share
root@ubuntu2:/usr/local/share # cd sword
bash: cd: sword: No such file or directory
root@ubuntu2:/usr/local/share # ls
fonts  games  man  sgml  xml
root@ubuntu2:/usr/local/share #
```

when I open a regular terminal and type
```
kairos911@ubuntu2:~$ cd /usr
kairos911@ubuntu2:/usr$ cd loca
bash: cd: loca: No such file or directory
kairos911@ubuntu2:/usr$ ls
bin  doc  games  include  info  lib  local  sbin  share  src  X11R6
kairos911@ubuntu2:/usr$ cd local
kairos911@ubuntu2:/usr/local$ cd share
kairos911@ubuntu2:/usr/local/share$ cd sword
bash: cd: sword: No such file or directory
kairos911@ubuntu2:/usr/local/share$ ls
fonts  games  man  sgml  xml
kairos911@ubuntu2:/usr/local/share$
```

If I go to
```
/etc/sword.conf
```

Then it tells me that sword.conf is not a directory.  Sword.conf is listed in under "etc" but it is grey instead of blue.

The patience of this group has been remarkable so far!

THANK YOU!!!!!

---

### Post by mrgigabyte on 2007-11-29
What specific modules are you trying to install?

Anyhow, after a base install with gnomesword in ubuntu (Im using gutsy with gnomesword 2.2.3):

Open up Gnomesword
Click " Edit ->Module Manager "
A window with "Module Manager" caption should come up.

Click "Configure"
I use "Remote" because I live in the US but it should show "Local" "CD Rom" if thats what you desire to use.
**But you can click "Sources" then add wherever the module files are located inthere.

If you use remote  Click the "refresh" button.
Then click on the "install" selection.
Select your module(s) and click the "install" button.

Hope this helps,

Gig

---

### Post by eldepeche on 2007-11-29
If you're still looking at the documentation you downloaded, it will be telling you the "wrong" place. Software you compile by hand gets installed into /usr/local , and architecture-independent data would go into /usr/local/share .

Since you installed via the package manager (apt), the program is installed using Ubuntu's normal paths, and so the modules would go into /usr/share .

Also, /etc/sword.conf is probably a regular file, so you should open it with a text editor. Since you don't own it (it's outside your home directory), you need to use sudo:

```
gksudo gedit /etc/sword.conf
```

gksudo is a version of sudo that should be used to start graphical programs, and gedit is the Gnome default text editor.

---

### Post by aonegodman on 2007-12-16
Hey there I'm in the same boat with trying to add raw modules to Gnomesword.

I've located the directories they are supposed to go in and have tried to just "pull and paste" to transfer like in Windows, but get "you don't have permission to use that function" error. Obviously it requires some syntax to use in the Terminal program using "sudo".

Can someone give me the command structure(code) to transfer files from one directory to another as sudo.

gnomesword files are located under  ***/usr/share/sword***

modules need to be placed under this directory in the following two folders located here:

 */usr/share/sword/mods.d*   and  */usr/share/sword/modules*


I obtained the additional modules from the Sword Project modules database and they are RAW files in .ZIP format.

I was able to unzip them to a seperate folder. Each module contains two files in the .zip which are a *mods.d* folder and a *modules* folder. Upon examining gnomesword file structure I find these two folders is where it keeps its added text modules.

If someone knows how to automate this process so I can install the added modules I would be most appreciative. But I'm willing to do it manually with command structure guidance. Thanks.

---

### Post by aonegodman on 2007-12-16
):P Hold everything -- Stop the presses!!! Just figured it out.

I was going about it the hard way and then I read again above and found mentioned about the ***Module Manager***. Some times we can't see for the trees.

I used the MM to add all the extra modules I wanted(from the Internet via Crosswire.org) to the program. \\:D/

Thanks

---

