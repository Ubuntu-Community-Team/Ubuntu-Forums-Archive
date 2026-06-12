---
title: "How do I install Power Tab Tools?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Noodels on 2007-08-06
Okay, hi everyone... again, installing programs on windows was easy enough for me, I did it all the time, the step by step guide went something like this:
1) Double click install file.
2) Answer some questions.
3) Wait.
But since I got ubuntu I've had difficulty installing programs that I've downloaded. In this case I've downloaded a file from this link : [http://linux.softpedia.com/get/Multimedia/Audio/PowerTab-Tools-5532.shtml](http://linux.softpedia.com/get/Multimedia/Audio/PowerTab-Tools-5532.shtml)

Downloaded it fine, and from previous builds where I've been guided through, I remembered something about using the configure file, so I double clicked the configure file and all the texts went by without any apparent error messages and the folder filled up with oddly named files that I dare not touch, but I've forgotten what I'm meant to do next, can anyone help me?

---

### Post by Inxsible on 2007-08-06
What kind of file is it?

Ubuntu is Debian based, so it can only install .deb files with point and click.
If you want to install other files for eg. .rpm then you need to use alien to convert it to a .deb first.

Other ways to install software are
1) Synaptic Package Manager

2) Applications --> Add/Remove

3) ```
sudo aptitude install <program-name>
```

4) oh and of course, compiling the software from source, yourself

---

### Post by reckless2k2 on 2007-08-06
you use add/remove programs in your menu list to add programs or synaptic. other than that, you can install from the source compiling a program from a tar file or installing using dpkg with a .deb file. what it sounds like by your post, you should be looking at synaptic or add/remove programs menu.

---

### Post by steveneddy on 2007-08-06
did you read the read me file? or the install file?

---

### Post by Noodels on 2007-08-06
What I am trying to do is install a program that doesn't show up in synaptic or add/remove programs, I mentioned the link earlier, it gives me a .tar.gz file and in it I get lots of files, so maybe I need to compile it from source. You can get it from the link only about 100/150 kilobytes. You can look over it from there, I think this is probably meant to be compiled, if only I knew how.

---

### Post by Noodels on 2007-08-06
> **steveneddy said:**
> did you read the read me file? or the install file?

Yeah, they didn't really help me out much.

---

### Post by silent1643 on 2007-08-06
> **Noodels said:**
> Okay, hi everyone... again, installing programs on windows was easy enough for me, I did it all the time, the step by step guide went something like this:
1) Double click install file.
2) Answer some questions.
3) Wait.
But since I got ubuntu I've had difficulty installing programs that I've downloaded. In this case I've downloaded a file from this link : [http://linux.softpedia.com/get/Multimedia/Audio/PowerTab-Tools-5532.shtml](http://linux.softpedia.com/get/Multimedia/Audio/PowerTab-Tools-5532.shtml)

here's a good source - i would add to your bookmarks
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Noodels on 2007-08-06
> **silent1643 said:**
> here's a good source - i would add to your bookmarks
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Thanks, this helps a lot, only should I be worrying about the following?

```
noodels@noodels-desktop:~/Programs/ptabtools-0.4.3$ make
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb.c -o ptb.po
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:516: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:517: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:518: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:519: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:520: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:522: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:523: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:671: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:672: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:673: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:674: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:675: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:891: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c gp.c -o gp.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb-tuning.c -o ptb-tuning.po
gcc -Wl,-soname,libptb.so.0 -shared -g -O2 -g -Wall  -DHAVE_CONFIG_H= -o libptb.so.0.4.3 ptb.po gp.po ptb-tuning.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb.c 
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:516: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:517: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:518: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:519: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:520: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:522: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:523: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:671: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:672: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:673: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:674: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:675: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:891: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c gp.c 
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb-tuning.c 
ar rs libptb.a ptb.o gp.o ptb-tuning.o
ar: creating libptb.a
noodels@noodels-desktop:~/Programs/ptabtools-0.4.3$ sudo make install
/usr/bin/install -c -d /usr/local/bin
test -z "" || /usr/bin/install -c  /usr/local/bin
/usr/bin/install -c -d /usr/local/share/man/man1
/usr/bin/install -c -m 644  /usr/local/share/man/man1
/usr/bin/install: missing destination file operand after `/usr/local/share/man/man1'
Try `/usr/bin/install --help' for more information.
make: *** [install] Error 1
noodels@noodels-desktop:~/Programs/ptabtools-0.4.3$ 

```

---

### Post by reckless2k2 on 2007-08-06
tar files are a little more detailed to install. you have to use the 5 step extract and build method. the tr file is kind of from the "source" if you will. follow this all from the terminal and make sure the tar file is in you home directory:

step 1 - tar zxvf <the full name of the tar file>

(this will extract it to a directory. it's like unzipping a file that creates a folder.)

step 2 - cd <the name of the extracted directory>

(if the file was extracted in your home directory, you can view the name by opening the home directory.)

step 3 - ./configure

(this will run a bunch of initial setups.)

step 4 - make

(this will kinda start the process for install prep.)

step 5 - sudo make install

(this will install the program.)

In some cases you may need to restart your desktop to see the icons in your menus.

---

### Post by jd65pl on 2007-08-06
See [these videos]("http://jamie.dumbill.googlepages.com/l_how_to_vids.html") on how to install software hopefully they will explain

---

### Post by Noodels on 2007-08-06
> **reckless2k2 said:**
> tar files are a little more detailed to install. you have to use the 5 step extract and build method. the tr file is kind of from the "source" if you will. follow this all from the terminal and make sure the tar file is in you home directory:

step 1 - tar zxvf <the full name of the tar file>

(this will extract it to a directory. it's like unzipping a file that creates a folder.)

step 2 - cd <the name of the extracted directory>

(if the file was extracted in your home directory, you can view the name by opening the home directory.)

step 3 - ./configure

(this will run a bunch of initial setups.)

step 4 - make

(this will kinda start the process for install prep.)

step 5 - sudo make install

(this will install the program.)

In some cases you may need to restart your desktop to see the icons in your menus.

Okay, when I do step 4, the following occurs:

```
noodels@noodels-desktop:~/Programs/ptabtools-0.4.3$ make
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb.c -o ptb.po
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:516: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:517: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:518: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:519: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:520: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:522: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:523: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:671: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:672: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:673: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:674: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:675: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:891: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c gp.c -o gp.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -fPIC -c ptb-tuning.c -o ptb-tuning.po
gcc -Wl,-soname,libptb.so.0 -shared -g -O2 -g -Wall  -DHAVE_CONFIG_H= -o libptb.so.0.4.3 ptb.po gp.po ptb-tuning.po
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb.c 
ptb.c: In function ‘ptb_data_instrument’:
ptb.c:516: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:517: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:518: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:519: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:520: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:522: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:523: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CSection’:
ptb.c:671: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:672: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:673: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:674: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c:675: warning: dereferencing type-punned pointer will break strict-aliasing rules
ptb.c: In function ‘handle_CPosition’:
ptb.c:891: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c gp.c 
gcc -g -O2 -g -Wall  -DHAVE_CONFIG_H= -c ptb-tuning.c 
ar rs libptb.a ptb.o gp.o ptb-tuning.o
ar: creating libptb.a
noodels@noodels-desktop:~/Programs/ptabtools-0.4.3$ 

```

Will this have a negative effect on step 5?

---

### Post by Noodels on 2007-08-06
> **jd65pl said:**
> See [these videos]("http://jamie.dumbill.googlepages.com/l_how_to_vids.html") on how to install software hopefully they will explain

What I am trying to do is compile a tar.gz source file thingamy, so these aren't really options.

---

### Post by aysiu on 2007-08-06
Try pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ptabtools
``` Haven't tried it myself yet, but I'm basing it on the fact that theoretically repositories exist for this package:
[http://jelmer.vernstok.nl/oss/ptabtool/](http://jelmer.vernstok.nl/oss/ptabtool/)

By the way, I've retitled your thread so that people don't keep telling you that you can install through Synaptic or *apt-get* or Add/Remove. Clearly you already know about those methods, which don't really help for this particular program.

---

### Post by Noodels on 2007-08-06
> **aysiu said:**
> Try pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install ptabtools
``` Haven't tried it myself yet, but I'm basing it on the fact that theoretically repositories exist for this package:
[http://jelmer.vernstok.nl/oss/ptabtool/](http://jelmer.vernstok.nl/oss/ptabtool/)

By the way, I've retitled your thread so that people don't keep telling you that you can install through Synaptic or *apt-get* or Add/Remove. Clearly you already know about those methods, which don't really help for this particular program.

Okay, thanks for renaming it, I'm not exactly sure what's happened here. This is the first terminal:
```
noodels@noodels-desktop:~$ echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
Password:
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
noodels@noodels-desktop:~$ echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
noodels@noodels-desktop:~$ sudo apt-get update
Get: 1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB          
Get: 2 http://gb.archive.ubuntu.com feisty Release.gpg [191B]                  
Get: 3 http://gb.archive.ubuntu.com feisty/main Translation-en_GB [4827B]      
Err http://autobuild.vernstok.nl ./ Release.gpg                                
  Could not resolve ‘autobuild.vernstok.nl’
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB           
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB             
Get: 4 http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB [1573B]
Get: 5 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB   
Err http://autobuild.vernstok.nl ./ Translation-en_GB                          
  Could not resolve ‘autobuild.vernstok.nl’
Hit http://gb.archive.ubuntu.com feisty Release                                
Get: 6 http://ubuntu.beryl-project.org feisty Release.gpg [191B]               
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Hit http://gb.archive.ubuntu.com feisty-updates Release                        
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_GB              
Err http://autobuild.vernstok.nl ./ Translation-en_GB                          
  Could not resolve ‘autobuild.vernstok.nl’
Hit http://ubuntu.beryl-project.org feisty Release                             
Ign http://autobuild.vernstok.nl ./ Release                                    
Ign http://autobuild.vernstok.nl ./ Packages                                   
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Ign http://autobuild.vernstok.nl ./ Packages                                   
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://security.ubuntu.com feisty-security/main Sources         
Hit http://gb.archive.ubuntu.com feisty/main Packages                          
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://gb.archive.ubuntu.com feisty/restricted Packages                    
Hit http://gb.archive.ubuntu.com feisty/restricted Sources                     
Hit http://gb.archive.ubuntu.com feisty/main Sources                           
Err http://autobuild.vernstok.nl ./ Packages                                   
  Could not resolve ‘autobuild.vernstok.nl’
Hit http://gb.archive.ubuntu.com feisty/multiverse Sources     
Hit http://gb.archive.ubuntu.com feisty/universe Sources
Hit http://gb.archive.ubuntu.com feisty/universe Packages
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://gb.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Sources             
Hit http://ubuntu.beryl-project.org feisty/main Packages                       
Err http://autobuild.vernstok.nl ./ Packages                   
  Could not resolve ‘autobuild.vernstok.nl’
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Hit http://ubuntu.beryl-project.org feisty/main Packages
Hit http://ubuntu.beryl-project.org feisty/main Sources
Fetched 6594B in 1s (4885B/s)
Failed to fetch http://autobuild.vernstok.nl/snapshots/ptabtools/debian/./Release.gpg  Could not resolve ‘autobuild.vernstok.nl’
Failed to fetch http://autobuild.vernstok.nl/snapshots/ptabtools/debian/./en_GB.bz2  Could not resolve ‘autobuild.vernstok.nl’
Failed to fetch http://autobuild.vernstok.nl/snapshots/ptabtools/debian/./en_GB.bz2  Could not resolve ‘autobuild.vernstok.nl’
Failed to fetch http://autobuild.vernstok.nl/snapshots/ptabtools/debian/./Packages.gz  Could not resolve ‘autobuild.vernstok.nl’
Failed to fetch http://autobuild.vernstok.nl/snapshots/ptabtools/debian/./Packages.gz  Could not resolve ‘autobuild.vernstok.nl’
Reading package lists... Done
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ubuntu.beryl-project.org feisty/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
noodels@noodels-desktop:~$ sudo apt-get install ptabtools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ptabtools
noodels@noodels-desktop:~$ sudo tee -a /etc/apt/sources.list

sudo apt-get install ptabtools







noodels@noodels-desktop:~$ 

```
And this is the second terminal:
```
noodels@noodels-desktop:~$ echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
Password:
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
noodels@noodels-desktop:~$ echo "deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./" | sudo tee -a /etc/apt/sources.list
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
noodels@noodels-desktop:~$ sudo apt-get update
E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
noodels@noodels-desktop:~$ sudo apt-get install ptabtools
E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
noodels@noodels-desktop:~$ 

```

I'm not really sure what's happened, it doesn't appear to have worked, no new icons or anything.

---

### Post by atomkarinca on 2007-08-06
it's gonna be a little off topic(?) but you say you want install power tab tools, why don't you try tuxguitar?

---

### Post by Noodels on 2007-08-06
> **atomkarinca said:**
> it's gonna be a little off topic(?) but you say you want install power tab tools, why don't you try tuxguitar?

I could do, I tried Kguitar but that didn't work. I'll have a look now.

---

### Post by aysiu on 2007-08-06
It looks as if you have some problems with your sources.list. Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Noodels on 2007-08-06
> **aysiu said:**
> It looks as if you have some problems with your sources.list. Can you post the output of this command? ```
cat /etc/apt/sources.list
```

Hmm, it seems like it yes, the following comes up:
```
noodels@noodels-desktop:~/Programs/TuxGuitar-0.9.1-src$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
sudo apt-get install ptabtools



deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./
deb http://autobuild.vernstok.nl/snapshots/ptabtools/debian ./


noodels@noodels-desktop:~/Programs/TuxGuitar-0.9.1-src$ 

```

HOWEVER, somehow, synaptic is broken. When I try to open it I get this error message :
```
E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.
```
Synaptic then closes when I hit the close button, has this happened from all the root things I've been doing in the terminal to get Power Tab working?

---

### Post by jd65pl on 2007-08-06
Do
```

gksudo gedit /etc/apt/sources.list
```

The when the file opens remove the line:

"sudo apt-get install ptabtools"

Once removed save and close

This file contains a list of software sources and this line is not valid in the file.

---

### Post by Noodels on 2007-08-06
> **jd65pl said:**
> Do
```

gksudo gedit /etc/apt/sources.list
```

The when the file opens remove the line:

"sudo apt-get install ptabtools"

Once removed save and close

This file contains a list of software sources and this line is not valid in the file.

Okay, the error message is now this :
```
E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.
```

I'm gonna try getting rid of that other line, sudo apt-get update or something and see what happens.

---

### Post by Noodels on 2007-08-06
I got rid of the other line and it's spaces and synaptic works again, thanks for that.

---

### Post by jd65pl on 2007-08-06
The uncommented lines in this file (the ones which don't start with a "#" should really start "deb" followed by other data. comment out all line which do not follow this trend then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Noodels on 2007-08-06
> **jd65pl said:**
> The uncommented lines in this file (the ones which don't start with a "#" should really start "deb" followed by other data. comment out all line which do not follow this trend then run

```
sudo aptitude update
sudo aptitude upgrade
```

Upgrade ran just fine, towards the end of update the following showed up : 
```
Hit http://ubuntu.beryl-project.org feisty/main Sources
Ign http://autobuild.vernstok.nl ./ Packages
Ign http://autobuild.vernstok.nl ./ Packages
Ign http://autobuild.vernstok.nl ./ Packages
Err http://autobuild.vernstok.nl ./ Packages
  Could not resolve ‘autobuild.vernstok.nl’
Err http://autobuild.vernstok.nl ./ Packages
  Could not resolve ‘autobuild.vernstok.nl’
Err http://autobuild.vernstok.nl ./ Packages
  Could not resolve ‘autobuild.vernstok.nl’
Err http://autobuild.vernstok.nl ./ Packages
  Could not resolve ‘autobuild.vernstok.nl’
Fetched 194B in 2s (76B/s)               
Reading package lists... Done
noodels@noodels-desktop:~/Programs/TuxGuitar-0.9.1-src$
```

But everything seems to work.

---

### Post by nichipet on 2007-08-06
autobuild.vernstok.nl is not coming up as a valid site. vernstok.nl comes up, though. Looks like the owner took autobuild down, hence the Could not resolve error.

---

### Post by gabrielr on 2008-06-19
Hate to dig up an old thread, but you can get the current sources list, as well as the key from 

[http://samba.org/~jelmer/debian/](http://samba.org/~jelmer/debian/)

---

