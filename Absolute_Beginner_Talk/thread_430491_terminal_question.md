---
title: "terminal question"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-05-02
This is probably going to be easy to answer for most of you, but I was wondering if the install code works the same in every Ubuntu version like if I wanted to get wine could I type the same code in the terminal to get and install it in any version of Ubuntu?  Kinda random, just wondering because I put Ubuntu 6.04 on my laptop to replace windowsXp and I've been messing with that and some things don't seem to install the same way as they do in feisty.

---

### Post by quark_77 on 2007-05-02
I think this is what you are looking for. The following:

```
sudo apt-get install wine
```

should work on all versions of ubuntu as they are all apt-based package systems. Kubuntu I think uses adept instead.

Quark_77

---

### Post by doomster on 2007-05-02
yeah. apt-get ,and aptitude works on all versions of ubuntu, if you mean installing from repositories:)

sudo apt-get install  wine <-- installs wine through  apt-get
sudo apt-cache search wine <--- searches the repositories for "wine" string

sudo aptitude install wine <--- installs wine through aptitude
sudo aptitude search wine <---- searches repositores for "wine " string through aptitude

---

### Post by riminicat on 2007-05-02
Yeah that is the code, the terminal just can't seem to find it

---

### Post by riminicat on 2007-05-02
Heres the message I get

> riminicat@riminicat-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


---

### Post by Pobega on 2007-05-02
Use aptitude search to find wine. So **aptitude search wine** will show you all of the packages with Wine it the name.

> pobega@vader:~$ aptitude search wine
p   libwine                         - Windows API Implementation (Library)      
p   libwine-alsa                    - Windows API Implementation (ALSA Sound Mod
p   libwine-arts                    - Windows API Implementation (aRts Sound Mod
p   libwine-capi                    - Windows API Implementation (ISDN Module)  
p   libwine-cms                     - Windows API Implementation (Color Manageme
p   libwine-dev                     - Windows API Implementation (Development fi
p   libwine-esd                     - Windows API Implementation (EsounD Sound M
p   libwine-gl                      - Windows API Implementation (OpenGL Module)
p   libwine-gphoto2                 - Windows API Implementation (Camera Module)
p   libwine-jack                    - Windows API Implementation (JACK Sound Mod
p   libwine-ldap                    - Windows API Implementation (LDAP Module)  
p   libwine-nas                     - Windows API Implementation (NAS Sound Modu
p   libwine-print                   - Windows API Implementation (Printing Modul
p   libwine-sane                    - Windows API Implementation (Scanner Module
p   libwine-twain                   - Windows API Implementation (empty transiti
p   wine                            - Windows API Implementation (Binary Loader)
p   wine-doc                        - Windows Emulator (Documentation)          
p   wine-utils                      - Windows API Implementation (Utilities)    
p   xwine                           - graphical user interface for the WINE emul

Now if you want to install Wine using aptitude, run **sudo aptitude install wine xwine** (Or just wine for me)

> pobega@vader:~$ sudo aptitude install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Reading task descriptions... Done         
Building tag database... Done    
The following NEW packages will be automatically installed:
  libwine libwine-gl libwine-print wine-utils 
The following packages have been kept back:
  policycoreutils 
The following NEW packages will be installed:
  libwine libwine-gl libwine-print wine wine-utils 
0 packages upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.0MB of archives. After unpacking 43.6MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://ftp.debian.org](http://ftp.debian.org) sid/main libwine 0.9.31-1 [7566kB]
Get:2 [http://ftp.debian.org](http://ftp.debian.org) sid/main libwine-gl 0.9.31-1 [898kB]                
Get:3 [http://ftp.debian.org](http://ftp.debian.org) sid/main libwine-print 0.9.31-1 [606kB]             
Get:4 [http://ftp.debian.org](http://ftp.debian.org) sid/main wine 0.9.31-1 [861kB]                      
Get:5 [http://ftp.debian.org](http://ftp.debian.org) sid/main wine-utils 0.9.31-1 [1083kB]               
Fetched 11.0MB in 32s (339kB/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package libwine.
(Reading database ... 74762 files and directories currently installed.)
Unpacking libwine (from .../libwine_0.9.31-1_i386.deb) ...
Selecting previously deselected package libwine-gl.
Unpacking libwine-gl (from .../libwine-gl_0.9.31-1_i386.deb) ...
Selecting previously deselected package libwine-print.
Unpacking libwine-print (from .../libwine-print_0.9.31-1_i386.deb) ...
Selecting previously deselected package wine.
Unpacking wine (from .../wine_0.9.31-1_i386.deb) ...
Selecting previously deselected package wine-utils.
Unpacking wine-utils (from .../wine-utils_0.9.31-1_i386.deb) ...
Setting up libwine (0.9.31-1) ...

Setting up libwine-gl (0.9.31-1) ...
Setting up libwine-print (0.9.31-1) ...
Setting up wine (0.9.31-1) ...

Setting up wine-utils (0.9.31-1) ...

And there you go. If you install xwine it is a graphical interface to Wine, which is more user friendly but too much overhead in my opinion. I don't like GUIs!

---

### Post by doomster on 2007-05-02
get to the system options and  select software sources from Administration panel . 
there you must have selected main/universe/restricted/multiverse sources,in order
 for apt-get to use all your available repositories. this might solve your problem.
then try to search for the wine to see how is it refered in the rep- list using 
apt-cache search wine command

---

### Post by riminicat on 2007-05-02
Hey guys thanks for the help, it's so weird switching between distros to test things, I used to be able to type the name of a program in and it would say something like "to install this program enter sudo apt-get install "program name", any idea why that stopped?

---

### Post by riminicat on 2007-05-02
Hey thanks Doomster

---

### Post by riminicat on 2007-05-02
I updated and changed the options and it all works

---

### Post by doomster on 2007-05-02
np :) 
 
thread close plz:)

---

