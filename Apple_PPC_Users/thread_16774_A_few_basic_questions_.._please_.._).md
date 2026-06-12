---
title: "A few basic questions .. please .. :)"
date: 2005-02-23
forum: Apple PPC Users
---

### Post by playahater on 2005-02-23
iBook .. 500Mhz CPU .. 256Mb Ram ... 10Gb Hdd .. Ubuntu PPC

problem 1 - I have downloaded a lot of packages in ".deb" format but .. how da hell should I install them  :razz: .. what is console command  :-? 
problem 2 -  Have enabled 3D acceleration but i can`t install Q3 .. have linux version and have succesfully installed it on Suse 9.2 Pro and it worked fine .. ????  :-? 
problem 3 -  Have configured modem ( /dev/ttyS0 ) or something like that .. and because I do not have any dialer at the moment .. I have tried to dial from console .. with wvdial .. ofcourse i have configure it before starting and it sais NO DIAL TONE ... where to turn it of .. can I put another string in wvdial.conf .. something like .. NoDialTone = 1 ????
problem 4 -  In order to watch DivX .. do I need to install win32 condecs and Mplayer or just Mplayer ???

Thanx in advance  :smile:

---

### Post by betterok5 on 2005-02-23
I am so new to Ubuntu that I have yet to get it running but it is a Debian
type of distro so you should be able to use dselect from a console.  Know 
where our files are and use access > mounted >whatever directory your files
are in.  You should go to select and be able to locate them with </> and choose to install 
them with <+> and <enter>.  You will probably be presented with dependancy
suggestions/requirements.  Use <space> to get back to the screen.  Hit <enter>
to accept the defaults.  Hit enter once more when finished selecting and go through
the rest of the steps. Hope this is of some use.
KK

---

### Post by bored2k on 2005-02-23
[QUOTE=playahater]iBook .. 500Mhz CPU .. 256Mb Ram ... 10Gb Hdd .. Ubuntu PPC

problem 1 - I have downloaded a lot of packages in ".deb" format but .. how da hell should I install them  :razz: .. what is console command  :-? 
problem 2 -  Have enabled 3D acceleration but i can`t install Q3 .. have linux version and have succesfully installed it on Suse 9.2 Pro and it worked fine .. ????  :-? 
problem 3 -  Have configured modem ( /dev/ttyS0 ) or something like that .. and because I do not have any dialer at the moment .. I have tried to dial from console .. with wvdial .. ofcourse i have configure it before starting and it sais NO DIAL TONE ... where to turn it of .. can I put another string in wvdial.conf .. something like .. NoDialTone = 1 ????
problem 4 -  In order to watch DivX .. do I need to install win32 condecs and Mplayer or just Mplayer ???

Thanx in advance  :smile:[/QUOTE]

1. In COMPUTER > SYS CONFIGURATION there is SYNAPTIC, wich is a Graphical INterface [gui] to install applications .

for command line and installation of dl .debs there are other gui but i do them in terminal by typing
#dpkg -i application.deb     [-i for installation btw,]
u need to be root , if u dont know these, ubuntu doesnt use root by default, so that would be sudo dpkg -i application.deb , inputting ur passwd when asked to .

--i suggest u stick with ubuntu broad sources bcuz ull hav no dependency problems. in synaptic clic on repositories and clic them all on for the full ubuntu files [at least, "universe" , ull need input for "multiverse"]

2. i dont do gaming on linux, someone here will help

3. neither deal with modems on debian, but u can click COMPUTER > SYS CONFIG > NETWORKING and maybe that gui will help !!

4. u need only w32codecs and no u dont need mplayer, personally i like totem or vlc .

vlc easily plays anything mostly w/o dependencies.
xine is very good also

u can get marillats w32codecs for debian [or..ubuntu] from google or some happy poster other than me

---

### Post by DirtDawg on 2005-02-23
[QUOTE=playahater]
problem 1 - I have downloaded a lot of packages in ".deb" format but .. how da hell should I install them  :razz: .. what is console command  :-? [/QUOTE]

While in the terminal, change directories to the one that contains the deb package, then type "sudo dpkg -i packagename.deb". The computer will ask for your password then, if all goes well and yer not missing any libraries, yer finished!

Of course as bored2k suggests, using Synaptic I think is the easiest way to go (assuming your linux box is hooked to the net). 

Good luck

---

### Post by playahater on 2005-02-23
Thanx for fast reply ...
thanx for that installation tip ..  ;-) 
I try to configure modem from GUI but I couldn`t find anywhere the nodialtone thing .. it is configured from dialer .. since I have only non-graphical dialer .. I`m stuck .. 
and I can`t get any of graphical dialers or any more packages until I make that modem work .. 

SO .. if anyone knows how to set no dial tone to 1 for wvdial ... shout ..  :smile:  ;-) 

Thanx in advance

---

### Post by toojays on 2005-02-24
Quake 3 on Linux only runs on x86. This will change sometime after iD GPLs it, but that might be a while.

---

### Post by playahater on 2005-02-24
[QUOTE=toojays]Quake 3 on Linux only runs on x86. This will change sometime after iD GPLs it, but that might be a while.[/QUOTE]

Which linux games I can play on ppc ???
Q1,Q2 ... ???

---

### Post by gruepig on 2005-02-24
[QUOTE=playahater]

SO .. if anyone knows how to set no dial tone to 1 for wvdial ... shout ..  :smile:  ;-) 

[/QUOTE]

According to the man page for wvdial.conf, the default is "abort on no dial tone".  Try disabling this in wvdial.conf (maybe set it to 0?) or in /etc/ppp/options.  I'm not sure if this will help; I haven't gotten the hcsfusbmodem module for my modem to load, so you're ahead of me.

---

### Post by landotter on 2005-02-24
I can help with the modem: open a terminal and run "sudo pppconfig" and answer the questions. You should then be able to start and stop your modem using "pon providername" and "poff providername". I highly recommend adding "modem-lights" to your panel and telling it to use those commands. You may have to add yourself to the "modem" group in the user configurator.

---

### Post by playahater on 2005-02-25
Thanx for help guys .. 
I`ll try to fiux it 
The thing is that I do not have no such string in wvdialconf as nodialtone .. that`s why I asked to add it .. 
I`ll try to fix it with "sudo pppconfig" and then we`ll see .. 

I`ll post result ... 

Greetings  :neutral:  :neutral:

---

### Post by adrian440 on 2005-02-25
I once had a NO DIALTONE message that would pop up no matter what OS I was running, and by adding an X3 to the init string, the modem would ignore the dialtone, (the problem was that that particular modem had trouble recognising the dial tone in my country).

---

### Post by playahater on 2005-02-25
I still have trouble to setup the fu***  :^o modem ... ](*,) 
Is there any chance that someone post his wvdialconf .. so I can compare and maybe use some of it ?? :roll: 
And another question .. how do I enable click on touchpad?? .. 
 
Thanx in advance  \\:D/ 

I`m maybe borring but I really need to understand this thing ..

---

### Post by stereo on 2005-02-26
yes quake2 is running fine in ubuntu/ppc.. it's under the gpl and available in the repositories. i guess in universe. so just click'n'run, but you'll need the originial *.wadfile or better a complete baseq2-folder to play.
I live in a four persons living-community with (dunno why *g*) 4 different plattforms. quake2 seems to be the only solution, if we want to frag us ;o)

---

### Post by playahater on 2005-02-27
Is there any chanse to post download link for quake for ppc ??

---

### Post by playahater on 2005-02-28
OK .. me again ..  :lol: 

I haven`t managed to disable dial tone yet .. here is my wvdial.conf and wvdial "error" from terminal and if someone knows a solution ..  ;) 

wvdial.conf

Phone = **********
Username = **********
Password = **********
[Dialer ppp0]
Init2 = ATM0
Password = **********
Stupid mode = 1
Init1 = ATZ
Phone = *********
Username = *********
[Dialer Defaults]
 Init2 = ATM0
Password = **********
Stupid mode = 1
Init1 = ATZ
Phone = *********
Username = *********


and here is the terminal

root@debian:/home/playahater # wvdial
--> Wvdial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending ATZ
ATZ
OK
--> Sending ATM0
ATM0
OK
--> Modem initialized
--> Sending ATDT042110770
--> Waiting for carrier.
 ATDT042110770
NO DIALTONE
--> No dial tone.
--> Disconnecting at Tue Mar 1 08:58:13 2005


Where to put no dial tone in wvdial config ??

I have tried to insert it as "No dial tone = 1" and I got nothing.

Thanx in advance

---

### Post by playahater on 2005-03-01
I made it work .. all I had to do is to put ATX3 instead of ATZ .. 

Thanx to all of you
 :-|

---

### Post by F_Athens on 2005-03-02
I'v put instructions for Q2 on the unnofficial ppc wiki

[http://ubuntuppc.webplazahosting.com/index.php?Quake%20II](http://ubuntuppc.webplazahosting.com/index.php?Quake%20II)

hope this helps

F

---

