---
title: "after complete INSTALLATION"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jaya28inside on 2008-02-05
i dunno
i'm new when USING THIS UBUNTU LINUX
that's why i need help from others users please...


after completing my task here
I already COMPLETED installing the UBUNTU via Alternate mode...

also it's similar with the steps from
> 
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu#Installation_complete.21](http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu#Installation_complete.21)

but then
after i reboot...
It appeared the OS options (it's OK then)
after that Entering The Ubuntu for the First selection right?

then it comes into the Command-Line mode...

log in as my account already and then password
OK then...

after that still on Command-Line mode...
where's the Desktop or something like GUI session????

help!!!

i dunno what to do next...

I REALLY DUNNO WHAT TO DO NEXT...
setting this up is different as Windows experienced-user....

sorry but... need help...!!! please help!!!:popcorn:

---

### Post by jaya28inside on 2008-02-05
help please on my email or this posting ...!!!

someone could please help!!!!!!!!

at least give me a tutorial of it...

coz i was downloading the alternate of UBUNTU... :(

---

### Post by jan quark on 2008-02-05
hmmm

did you enter the grub menu, a menu which shows you the options to boot into normal mode, the recovery mode, and to perform the memtest?


or did ubuntu load on its own, with no error messages and the loading screen was displayed, and you then entered into the command mode?

---

### Post by szymon_g on 2008-02-05
you used an alternate mode... so maybe you just installed a 'pure' system (i.e. without Xserver?) try to type

startx

and look what happend.
if Gui will show that you prabably need to install an application gdm.
if nothing happend, type

sudo aptitude install ubuntu-desktop <<--- it will download and install & preconfigure a 'standard' gnome-based gui... you can choose kubuntu-desktop (for kde) or xubuntu-desktop (for xfce4).


////////////
btw- you should NEVER give your email addres on forum or in other public websites. be prepared for spam, spam, spam, ;p

---

### Post by jaya28inside on 2008-02-08
yes


i download the alternative installation on command line mode

so then there's no GUI...

and please help... i dont have internet connection on my PC

coz this i connect via another places... :(

what's should i do...
coz i just download that alternate CD so then i install it...
but .. how to make it as windows desktop as well...??

it's not just COMMAND LINE right?
none of the Graphical appeared help!!!

---

### Post by jaya28inside on 2008-02-09
i try you tips:

> 
sudo aptitude install ubuntu-desktop 


but then it needs the CD right?

so never mind it's OK

then it's appeared looks like the Safe mode of windows...
like you said before... it's still PURE...

yes still clean so 

what's should i add next... i mean which and what steps again?? plzzzz

---

### Post by Paqman on 2008-02-09
To be honest, i'd go back and reinstall the full desktop version. It's probably quicker than trying to figure out what you do and don't have installed.

---

### Post by jaya28inside on 2008-02-09
wait...hold on about it :|

i found that if firstly installing on the option which is

Text mode
and then Command Line System (which is i choose it)

some user said that Command Line System is just for the moreeeee details 
and need more details... (difficult?)

so the Text mode or the FIRST OPTION is just for the quicker right?
and mostly didnt take any difficult-configuration right?

so then i choose the difficultly way....
......................

next what should i do? plzzz dont make me chose to back installing it again :(

---

### Post by halitech on 2008-02-09
If you did the Alternate Command Line (server) install, you have just the command line version. If you wanted a GUI, you need to install a GUI (IE. Ubuntu-desktop) from the command line or you need to get a version with the gui.

---

### Post by jaya28inside on 2008-02-09
> **halitech said:**
> If you did the Alternate Command Line (server) install, you have just the command line version. If you wanted a GUI, you need to install a GUI (IE. Ubuntu-desktop) from the command line or you need to get a version with the gui.


wait.....so after finishing selecting and completing the installation of ubuntu 
via alternative mode
and choosing the Command Line SYstem
and it's appeared likes DOS

so...then i should install the desktop right? 

similar with the last post command?
or perhaps you could give me a details what to do next...

coz last time i already get it
install apt-get ... something like that... i forgot... ubuntu-desktop

and ok success

i try startx
coming the desktop!!

horrrayy!!!

but then after log-in
there's message user-switch..something like that unexpectedly what/////\\\ dunno
some message appeared like that when i get in to the desktop just in the first of my life...

OMG!!

then...
after restarting... it's normall boot via GRUB
and then
selecting the FIRST option which is LINUX..
but then

the SCREEN going blank....
looks like the RESOLUTION cant be handled

but last time i can go inside...
why??
so i prefer restart it again... and select RECOVERY from GRUB boot
then coming up the Command Line system....

i use startx
and same thing... the screen looks like cant handle the resolution
perhaps it's just limited only 1024 x 768.....

perhaps... 

so then 
i type exit ---still the blank screen 
ENTER

it's comes up the Command Line System again....
and saying that something error or what...dunno mistake like that....
its about the xserver?

whaaaaa..... i need more guidance...plzzz!!!

even i know it's difficult... but i wanna try to get the solution...plzzz 
Linux User... we're all same... need help!! i'm new here...!!

---

