---
title: "No Internet"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by arden13 on 2007-06-01
I have installed both kubuntu and xubuntu on my computer (different partitions) and I need help. I'm trying to install a D-link DFE-530TX+ PCI ehternet adapter, and it comes with the driver. The problem is, I don't know what to do after I Un-Tar it. In the .txt file it says to "compile it" but I don't know how to do that. It comes with a Makefile, but I'm not sure what to do with it. HELP!!!

---

### Post by Sparkster185 on 2007-06-01
Traditionally you go to the folder where you extracted the tarball.  Then you type "./configure", wait until it's done, type "./make" then "sudo make install".  That should cover it.

Perhaps the README has more information?

---

### Post by Rui Pais on 2007-06-01
And before that to compile you need a compiler :)

Get it with:
```
sudo apt-get install build-essential
```

But you should read anyway the README file to know what to do to load it.

---

### Post by arden13 on 2007-06-01
it said it didn't find build essentials

---

### Post by Dougie187 on 2007-06-01
Look for it in your synaptic package manager. You probably just typed in the name wrong.

Go to System->Administratoion->Synaptic Package Manager

Then Click on one of the packages and type in build. Hit Esc and look for your build-essential package. Check it for install and hit apply.

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> it said it didn't find build essentials

have you copied the line from my post? is **build-essential**
no space but a minus sign and without a final "s"

---

### Post by bobplano on 2007-06-01
build-essential is on the cd if you don't have internet. just run
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by arden13 on 2007-06-01
pais, yes i typed it in EXACTLY as you said.  Dougie,  it wasn't there.   am i just screwed?

P.S.  i'm using a DIFFERENT computer to get on the internet.  thats my main issue here.

---

### Post by arden13 on 2007-06-01
> **bobplano said:**
> build-essential is on the cd if you don't have internet. just run
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

I love you. (in a non-gay way)

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> pais, yes i typed it in EXACTLY as you said.  Dougie,  it wasn't there.   am i just screwed?

P.S.  i'm using a DIFFERENT computer to get on the internet.  thats my main issue here.

Ok. i feel idiot, of course you don't have a connection... ](*,)

do what bobplano suggested or get the deb from here (with the computer with connection):
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all)

and instll it with:
```
sudo dpkg -i build-essential*.deb
```


edit: Ah you did it faster then my typing :)

---

### Post by arden13 on 2007-06-01
okay, now the make and ./configure stuff isn't working
 


it doesn't recognize ./configure

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> okay, now the make and ./configure stuff isn't working
 


it doesn't recognize ./configure

what are the error? do you previously moved to the untared(decompressed) folder?

---

### Post by bobplano on 2007-06-01
so these commands don't work once your in the untared directory?:
```
sudo make uninstall
make 
sudo make install
```

---

### Post by arden13 on 2007-06-01
I'm in the Un-Tared directory, and the 'sudo make uninstall' works.  the other two don't

and when you type in ./configure   it says file directory not found (or something very similar)

---

### Post by Dougie187 on 2007-06-01
what does ./configure return?

Edit:
To Kind of explain what you are doing... You have the source code for pidgin. And you need to compile it.
Before you compile it you need to configure the scripts to install correctly for your system, so the kinda people who made the program (this is usual) wrote a script called configure that configures the rest of the files to install correctly for you. So you run this with ./configure. After this runs (successfully) you can compile the program.

In the same directory there is what is called a make file. This gives the computer the commands to compile the program for you. So you just type make to initially compile the program, and then there are different parameters you can give the makefile like, make install, make clean, and make uninstall. Make install (has to be run as root) will install the program on your system. Make uninstall (has to be run as root) will uninstall the program for you so it might be handy to keep the source around if you need to uninstall it later. Make clean will clean the compiliation so you can recompile the source for you.

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> I'm in the Un-Tared directory, and the 'sudo make uninstall' works.  the other two don't

sudo make install probabilly will only work if you run fits ./configure and make. You don't compiled yet so you don't have nothing to install.

Search for a file README or INSTALL. Usually they have precious information on how to do this...

What happen is console when you type 
```
./configure
```  ?

---

### Post by arden13 on 2007-06-01
Dougie, it says 'file directory not found'  or something similar

---

### Post by Rui Pais on 2007-06-01
btw, i check they site and on [this link]("http://support.dlink.com/products/view.asp?productid=DFE%2D530TX%2B#") they say that drivers are only need when there isn't  r8139 available which you have available with the generic module..

> ¤ Use for 2.2.x or if your version of Linux does not have the RTL8139 module built-in.

---

### Post by arden13 on 2007-06-01
then why isn't it recognizing the hardware???  just please help me through the driver install.

---

### Post by Dougie187 on 2007-06-01
Can you post the last couple of lines from ./configure

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> then why isn't it recognizing the hardware???  just please help me through the driver install.

do you mind to post the output of:
```
lsmod |grep r8
```

and whats the output of 
```
ls
```
when you are inside the untarred folder

---

### Post by arden13 on 2007-06-01
DOUGIE:

it says  IN ONE LINE

file or directory not found

THATS IT

---

### Post by arden13 on 2007-06-01
Rui, I don't have time right now to post the file names because i have to go to work, but please keep helping with this.

---

### Post by Rui Pais on 2007-06-01
> **arden13 said:**
> Rui, I don't have time right now to post the file names because i have to go to work, but please keep helping with this.

Ok, good work. 
we all be around when you post again :)

---

### Post by Dougie187 on 2007-06-01
You probably dont compile it using configure then...

---

### Post by arden13 on 2007-06-01
okay, i'm back from work, and i found a link to the exact driver stuff that they give me, (even though its in a .zip format) except that I only get the installation part of the .txt  oh well, have at it.

---

### Post by arden13 on 2007-06-01
*bump*

---

### Post by arden13 on 2007-06-01
can nobody help?

---

### Post by Dougie187 on 2007-06-02
Can you print the output of this command when inside the unzipped folder?

```
ls
```

Also it might help if I could get the link to the file you downloaded.

---

### Post by Rui Pais on 2007-06-02
> **arden13 said:**
> okay, i'm back from work, and i found a link to the exact driver stuff that they give me, (even though its in a .zip format) except that I only get the installation part of the .txt  oh well, have at it.

Are you sure you have a *nix driver? usually they don't appear as zips (but bz2/gz)... 
The only thing i got from D-link site that is for linux (as a said before) is a link for a c file thats is the code for the rlt8139 and the info that it's only needed if your linux don't have it (they all have but...)  

D-link software are GPL so you can attach the compressed file or give us a link to, so we can see what can be done.

But my advice is to try simply use the r8139 and see if it work:
Check if its loaded:
```
lsmod |grep r8
```
if output is an empty line, you need to loaded:
```
sudo modprobe r8139
``` 
should load the module.

And whats the output of:
```
lspci
```

i realize you are not in your linux box... you can send those outputs to txt file or images and save them on a pen to add it here from your connected computer. To save to a text do:
```
lspci > lspci.txt
```
or:
```
cd *my_untarred_code_folder*
ls > ls.txt
```



edit:
meanwhile i found this [page here]("http://www.scrounge.org/linux/nics.htm"), that mention your card. Again they refer it uses the r8139 and some users report working better with the r8139too module (bottom of page). 
You should at least try both of them before going to compile anything, imho.

---

### Post by Dougie187 on 2007-06-02
Well since you have at least access to a windows driver, you might consider using Ndiswrapper to use that driver in you linux installation.

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

### Post by arden13 on 2007-06-04
okay, i'm back, but i have some news.  I gave up on the D-Link, but the new card is asking for the same thing.  rtl8139   the problem is, its not loaded, and when i use the user guide, it says to go to this link:

[http://www.scyld.com/network/rtl8139.html](http://www.scyld.com/network/rtl8139.html)    but it takes me to the main page of beowulf, which doesn't help.

---

### Post by arden13 on 2007-06-04
bumpage

---

### Post by Rui Pais on 2007-06-04
If the module is not loaded you need to load it (that was deep!).

There are 2 version:
r8139too and r8139cp which one you need... you have to try. Load it with:
```
sudo modprobe r8139too
```

check with:
```
lsmod | grep r8
```
and 
```
dmesg
```

For more info check the output of:
```
lspci
``` 
and 
```
sudo lshw -C network
```


If it fails redo everything with the r8139cp one.

---

### Post by arden13 on 2007-06-04
okay, please for a second, imagine i am a TOTAL linux n00b.  please make a step by step thing for me to do including downloading the file (i only need step by step in linux, but include websites that are necesary)  otherwise, i am totally screwed.

---

### Post by Rui Pais on 2007-06-04
ok, i'll try to make it the simpler as possible and explain as better i can.

First, it's simpler then you imagine. You are thinking as a Windows user... somewhere there is a place on net with a precious driver - probably the hardware maker - where you download and somehow install (even compile)...

No, thats not exactly the way on Linux. That only happens for some bizarre hardware or for some specific close source drivers (the ones that makers don't give technical specification and nobody had yet make one freely).

Drivers under linux are named modules and with the kernel (the heart of a GNU/Linux operating system) there are always dozens of modules for a lot of hardware. Networks (wired internal cards specially) are very well supported under Linux, realtelk one of the most commons. So you are lucky.

Drivers/modules can be loaded during run time (when system is running) with the modprobe command.

Autodetection usually detects all hardware and net cards are usually well detected... thats why i suspect you may have already the module loaded.

So, open a terminal (is in menus, or press Alt+F2 and type gnome-terminal)
and type:
```
lsmod | grep r8
```
(If you can't copy+past text ,you can use autocompletion feature. Type just **lsm** and press Tab key on your keyboard, it would complete the word, avoiding typing errors :) the **|grep r8** is to show only modules which name started with **r8** )

Now there are 2 possibilities. 
Or it returns nothing on the line command and you need to load it:
```
sudo modprobe r8139too
```
you can type **modp** (press Tab key 1 or 2 times) till you got the full word, type r8 (press Tab again) go get the available modules started with r8. sudo is to give you as user administrative powers, it will ask you a password.

Or it's loaded and you can go on to the next level on actions.

Start by doing this and post what happens (or any doubts).

---

### Post by arden13 on 2007-06-04
ok the command 

Code:

lsmod | grep r8

returned nothing

but when you type in 
lsmod
you get all the modules, and one of them is 8139cp

i then did sudo modprobe 8139cp
it returned back to the #

I also loaded mii which said it was used by 8139cp


what next?

---

### Post by Rui Pais on 2007-06-04
ok, i'm using a self compiled stripped kernel, i don't build modules except the ones i need so i cant check the names, but if you have a 8139cp thats the one (i have a rlt8169 and the module is called r8169, thats why i supposed they have a 'r' in front of the name :( ) 
So you don't have to do nothing after all, autodetection had already load the module for you :)

now you simply run:
```
gksudo network-admin
```
select Wired connection and click on 'Properties' button.

Ensures that it says 'Automatic configuration (DHCP)'  on Configuration. If not choose that Option from the combo.
Close and on a Terminal type:
```
sudo ifup eth0 
```

that should bring your network up.

---

### Post by arden13 on 2007-06-04
it WORKED.  but, if i want to reconfigure it, how do i do so??  (if i retyp the command it says its already configured)

---

### Post by arden13 on 2007-06-04
actually, i figured it out.  Thanks a bunch Rui Pais.  (This is me typing from my linux comp. :)

where did you learn all your linux stuff by the way?

---

### Post by Rui Pais on 2007-06-05
hi again,
sorry it was late here and i was off to bed (good morning ;))

glad you managed to get it.
Note that nothing was wrong in fact. Autodetection had already detect correctly and loaded the needed module and dhcp assign IP is the default so it should had been set too. 
The only thing need was to make you stop thinking like a Windows user and start to think like a Linux user :)
Its very common on first times on a new OS, keep around and soon you'll feel at home.


I get a little of Unix at university (we had some old Unix machines, very unfriendly, with a desktop that was only a grey background... hard to find even a terminal) but we learn only basic line commands, the rest of the course was focus on coding. I really learn (the little i know) by get in trouble...

I installed later a Linux myself (a RedHat 8, i think) and got a terrible USB adsl modem (they stamp on the box 'Work on Linux'... but they forget to inform they didn't offer support for it - smart guys). 
So i learn like most of the people. That way -> : ](*,) Read dozens of how-tos, trying endless variations. Hardly something worked, but i learn always a little with any of them. When i finally got it to work i wanted to auto start at boot, so i check scripts (bash is easy to read) of boot processes and manage to get it... and learn a little about boot precess. So i was a lucky guy till that module starts to get trouble to Fedora guys (i had meanwhile upgrade and move to that). They didn't seem to find a solution, so they simply remove it from they kernel... Ok, i need it, so i had to learn how to compile the kernel (easy after some few trials). And so on...

For me one of the great advantages of Linux is every time you got a problem you end up learn a little. (you didn't needed but you learn something about compiling, that in ubuntu you need build-essential, how to check modules, how to load modules in run time, how to check/set network with dhcp... see) Linux can have less things work out-of-box, but you learn more, you can see how things are done. 
Even helping people around and you are constantly learning, and sometimes on things that one had though that knew a lot about. 

Hope you stay around and enjoy it. 
Have fun :D

---

### Post by romihim on 2007-07-03
hii
i have just installed fiesty ,but it is not detecting my network card.Actually my problem is almost the same as of the guy who started the post ,but a bit more complicated .I dont have .tar.gz file of my driver of rtl8139.I have its .c file(Plus some more files which i got in cd). Readme tells to compile it and save the output as a module . but it is not getting compiled .It says config.h not found . 
I m uploading the files i got in the driver cd .
[http://www.4shared.com/dir/3151078/d76f155b/rtl8139_driver.html](http://www.4shared.com/dir/3151078/d76f155b/rtl8139_driver.html)
Plz try this at ur linux and if it gets compiled plz tell the procedure and upload the output file in the same folder of the link.
my ubuntu does not have rtl8139 module loaded 


plz help me its urgent .

without net ubuntu would be very useless for me

---

### Post by romihim on 2007-07-03
And one more thing 
on using make command it gives error config.h not found

---

### Post by Rui Pais on 2007-07-03
> **romihim said:**
> hii
i have just installed fiesty ,but it is not detecting my network card.Actually my problem is almost the same as of the guy who started the post ,but a bit more complicated .I dont have .tar.gz file of my driver of rtl8139.I have its .c file(Plus some more files which i got in cd). Readme tells to compile it and save the output as a module . but it is not getting compiled .It says config.h not found . 
I m uploading the files i got in the driver cd .
[http://www.4shared.com/dir/3151078/d76f155b/rtl8139_driver.html](http://www.4shared.com/dir/3151078/d76f155b/rtl8139_driver.html)
Plz try this at ur linux and if it gets compiled plz tell the procedure and upload the output file in the same folder of the link.
my ubuntu does not have rtl8139 module loaded 


plz help me its urgent .

without net ubuntu would be very useless for me

Hi.
(You have a very confusing typing...)

Calm. Compiling modules with code from the net should be the last option.
If your net card is a realtek 8139 and you are using a standard Ubuntu module you must have that one.

Do you mind to boot to your Ubuntu, and type the following on a terminal:
```
lshw -C net > lshw.txt
```
```
lsmod |grep 81 > lsmod.txt
```

then use a pen or a floppy and copy the files lswh.txt and lsmod.txt (they must be on your home folder) to the floppy  or pen and post them here, please.

---

### Post by romihim on 2007-07-04
@Rui Pais 

Thank You for the Reply . I have resolved my problem and now my internet is working very fine .
Actually my lan card was of  Hangzhou Silan Microelectronics Co. They supplied it with driver named scl92031 for kernel version 2.4 and 2.5.  This card will be supported in kernel version 2.6.21 . 
i have found a modified of scl92031 for kernel 2.6 . 
link is :-
[http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/)

[http://ubuntuforums.org/showthread.php?t=478063](http://ubuntuforums.org/showthread.php?t=478063)

Thank You

---

