---
title: "Got it working...except for wireless network adapter"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by escapee from Winhell on 2006-06-05
Thanks guys..i re-installed...apparently the LVM partioning worked..I didn't use the LVM in the first install...now everything seems to be working properly..well ...


with the exception of my networking...still working on that one...if you all can help here's the the scenario

....Belkin USB wireless adapter...Belkin Wireless Router ....Direcway DW6000...

other computers on router are XP systems... wireless adapter is recognized by Ubuntu however i still can't connect with it....

Thanks for the help everyone!!!

---

### Post by Jagot on 2006-06-05
This might help:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

---

### Post by escapee from Winhell on 2006-06-06
thanks jagot....sorry for the delayed response..I'm exhausted...i tried the instructions mentioned above...however...i changed it up a bit...i copy/pasted inf and sys files for the driver to a folder on the Desktop..and got'm installed from there...however..(seems to be used alot by me lately...haha)...drivers installed...hardware detected....but no connection...

I'm a complete Newb when it comes to setting up proxy settings and what not...though i've tried every possible thing i could try...and then un-tried'm as to not make any permanent mistakes...now the question is....withthe hardware and drivers detected...is there something else that anyone can help me with...that could get me online....walkin back and forth from my ubuntu machine to this one for net access is killing my legs...haha

I'd be a great Ubuntu charity case if anyone wants to adopt me...I WANNA LEARN!!!!!!!!!...Thanks you guys...

             signed.......Newb w/ phone..will call.......wants to learn.......

---

### Post by n00bWillingToLearn on 2006-06-06
Are you using breezy or Dapper Drake?

---

### Post by n00bWillingToLearn on 2006-06-06
Please post output of 
```
cat /etc/network/interfaces
```

---

### Post by escapee from Winhell on 2006-06-06
noob..i'm using breezy for now..have dapper on the way...ordered disk rather than d/l'ing for hopes that I could learn a bit b4 it got here...as for out put...here's what i'm getting on "cat /etc/network/interfaces"...

mapping hotplug
            script grep
            map eth0
iface wlan0 inet dhcp
auto wlan0

I didn't configure eth0 b/c i wasn't using ethernet cable..(using USB)...figuring that shouldn't effect me..
I'm made another try at installing drivers and everything went well till time to run ifup wlan0 command...i got an Internet Systems Consortium DHCP client v3.0.2..then the ISC copyright stuff...then...sit0: hardware address 776

if that helps any.........

---

### Post by n00bWillingToLearn on 2006-06-06
What exactly, other than the tutorial posted above, have you tried to do to get your card working already?

Did Ubuntu recognise your card at all before you installed NDIS wrapper?

Does your ethernet work? ( you need some form of internet to follow the instructions posted above )

Sorry to be asking more questions than giving answers but I am trying to figure out what exactly is wrong and to be perfectly honest I am also fairly new to Ubuntu myself.

---

### Post by escapee from Winhell on 2006-06-06
my ethernet works...though it's not connected..i connected today and downloaded the rt73 drivers from ralink which are required for the rt73 chip set of the 7050 model that i have...howeer the directions for install i have noticed requires me to be online to gather more apps/info....

i've tried using the windows drivers..(inf and sys files) through the ndiswrapper...that didn't work...the adapter was recognized from clean install however in wouldn't work...thus causing me to search for methods to install

if you're in the states and don't mind me calling i can call and sit in front of Ubuntu system and read what it says....as of now I've done another clean install...just assure that i'd undone all I'd attempted...as of now i have the ralink drivers on desktop..and still searching for methods...i have to my kids and need to spend some time with them..but i'll be able to get back online in about an hour..oh and i wasn't connected to the internet when i tried the easy-peasy method earlier...everything appeared to work without error except for getting the adapter to turn on and connect...it said drivers present, hardware present but nothing showng on the adapter end that it was working..and no connection thanks for the help...

as for asking questions...no worries...i know detailed info is often needed for the correct help...thanks again...

---

### Post by uzi09 on 2006-06-06
perhaps you might want to try this:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
and it's wiki...
[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)

i got it working no problem...hmm...seems to be idiot proof :-k

---

### Post by ramcosca on 2006-06-06
[QUOTE=Jagot]This might help:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)[/QUOTE]
I tried doing this, but my CD is lost. I downloaded the drivers off the Belkin webpage, it opened with WINE, unzipped... but... uh... where are the files? I'm stuck there.
Please help. :)

---

### Post by escapee from Winhell on 2006-06-06
uzi...i have a question....my version of the 7050 requires the lsusb driver from prism54 which you have to build and i have no idea how to do so..or it requires the Ralink rt73 driver...being that the windows driver was the rt73...the link you offered doesn't have either of the two..can you point me in the right direction...obviously i'm a bigger idiot than this was tested on...thanks for any and all replies you guys..

---

### Post by escapee from Winhell on 2006-06-06
K...here's an update...I have another method to add to my madness..so i'm going to try it...it as well requires internet connectivity so i'm going to bring the ox out here and connect through the ethernet...try an option that i found in an earlier post...the easy-peasy one didn't really work for me...may try it again to being that it was a rather simple method...i'll be back in about an hour and let you all know how it turns out...if you have any info in the meantime by all means post'm...lord knows i'm liable to screw this up too...haha...anyway...wish me luck see you in a bit...and thanks again everyone....

---

### Post by n00bWillingToLearn on 2006-06-06
I am asking this to someone smarter than me for escapee from Winhell.

Do USB wireless cards need firmware from the computer like PCMCIA cards do?
I thought that if Ubuntu recognised the card and displayed it that it had the drivers for it and if it didn't work it might be that for legal reasons they are not allowed to distribute the firmware with Ubuntu but using fwcutter you could extract just the firmware from a windows driver instead of using NDIS wrapper. I have tried to setup wireless cards with NDIS wrapper and it has been hit or miss weras avery time a card has been recognised I have been able to set it up successfully with fwcutter.I have never set up a USB wireless card. Am I understanding this correctly, and does this apply for USB cards also. If so, than should escapee from Winhell try using fwcutter instead of NDIS wrapper?

---

### Post by escapee from Winhell on 2006-06-06
noob...I'm not sure if this answers your question or not....though you seem to make a valid point..i just don't know enough to say either way..However, it's my understanding that the drivers for the Belkin f5d7050..v.3000 which is rt73 is not supported...however ralink has made a package that you have to build for the rt73. I've just set my pc up next to me here so that i can try and build it..may take me a while being as I have no clue what i'm doing really other than following directions..some of which are slightly confusing to me, not having any experience with any linux/unix systems....though i'll be checking posts regularly while trying to work this thing out...

but if anyone can answer noobs question above please lemme know...I've gotten the re-install process down so i have no prob with doing that to make sure everything is right..haha...i've reformatted /re-installed Ubuntu 4 times now...just to make sure i undo everything that didn't work the try before....haha..thanks guys

---

### Post by n00bWillingToLearn on 2006-06-06
[QUOTE=escapee from Winhell]...i've reformatted /re-installed Ubuntu 4 times now...just to make sure i undo everything that didn't work the try before....haha..thanks guys[/QUOTE]

My record is 5 times in one day trying to get XGL to work. Thank god Dapper installs in ~20 min:)

---

### Post by uzi09 on 2006-06-06
sorry haven't gotten a chance to check up on the thread again.
@ escapee from winhell:
hmm, if it doesn't support your adapter, i'd recommend letting them know about it first of all at their site, and second, i don't know of any other way around except building it. if you'd like, please post the instructions here and let us know where you're having problems, if any of us understand, we'd be more than happy to help

@n00b willing to learn:
geez! wow - i guess i got off easy! seemed to work the first time around for me, without any hassles :S
what set of instructions were u using???

---

### Post by escapee from Winhell on 2006-06-06
ok..i used the easy peasy method again..and got an unknown device address 776 response...and tried to start the same method over..and got the same thing...........so i started on the other method i have for building the ralink rt73 driver and don't believe that's gonna work for me either...it says to use./makefile command..and either i'm using it wrong or it's just not working.....so i got up to get a smoke and my son decided to have a go at it...he's 10..needless to say i'm doing another install...

---

### Post by escapee from Winhell on 2006-06-06
uzi09:..this is a link to one of the sets of instructions i've used...the one that gave me the result in my last post [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux") here is another set i've tried..but this one confuses me....i'd like to discuss this method in detail with someone b/c i'm almost positive i'm doing it wrong..so if any of you can take a look at [http://www.linuxquestions.org/questions/showthread.php?p=2265682]("http://www.linuxquestions.org/questions/showthread.php?p=2265682") and let me know if you feel you can help me to understand what i'm doing wrong...(my problem starts with the makefile part..so..rather early in this build)...thanks you guys for all ya support

---

### Post by uzi09 on 2006-06-06
[QUOTE=ramcosca]I tried doing this, but my CD is lost. I downloaded the drivers off the Belkin webpage, it opened with WINE, unzipped... but... uh... where are the files? I'm stuck there.
Please help. :)[/QUOTE]

umm, there is a unzipping utility for linux too :D you don't need wine for it. and it's probably in
 ~/.wine/drive_c/
directory

if you could gimme a lil while, i'm just going to see what he's talking about. IMO, the how-to @ linuxquestions.org is a lousy how-to

EDIT: k, so the instructions at easy-peasy seem pretty straight forward. k, you said you got some unknown device error. when was it that you hit this error??

EDIT2: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) which one did you download at this site?
EDIT2a: nvm, i believe you used the rt73 one because of this line:
supplied driver on the disk was rt73 which is how I knew to download the ralink rt73 driver from:

---

### Post by n00bWillingToLearn on 2006-06-06
[QUOTE=uzi09]
@n00b willing to learn:
geez! wow - i guess i got off easy! seemed to work the first time around for me, without any hassles :S
what set of instructions were u using???[/QUOTE]

I am on a powerbook g4 ie no proprietary nVidia drivers :(

---

### Post by escapee from Winhell on 2006-06-06
Uzi...on the easy-peasy set i made it all the way through to the ifup wlan0 command at the end of the instructions....

I liked the idea of using these instructs. b/c they were rather simple to follow..but with the end result i'm getting i'm wondering if I'm having some kind of conflict with my usb 2.0 ports..though during boot and in device manager the usb ports show (boot)..Belkin USB wireless adapter shows in usb root hub in device manager..so that may not be my issue... I am just popping off whatever ideas come to mind...maybe one of you will have some better ideas...obviously mine aren't working..haha...thanks guys

---

### Post by escapee from Winhell on 2006-06-06
hey noob........have you tried easyubuntu?...it's supposed to have ati and nvidia drivers...and a bunch of other stuff in it....it's at [www.easyubuntu.com(or](www.easyubuntu.com(or) .org..not sure which)...i d/l'd it earlier and it was a very simple click and go type interface...tabs for each of the diferent elements...multimedia..system..and a few others...check it out..not sure if it works on laptops or not...don't know what the differences are when it comes to setting them up...

---

### Post by escapee from Winhell on 2006-06-06
hey noob........have you tried easyubuntu?...it's supposed to have ati and nvidia drivers...and a bunch of other stuff in it....it's at [www.easyubuntu.com(or](www.easyubuntu.com(or) .org..not sure which)...i d/l'd it earlier and it was a very simple click and go type interface...tabs for each of the diferent elements...multimedia..system..and a few others...check it out..not sure if it works on laptops or not...don't know what the differences are when it comes to setting them up...

---

### Post by uzi09 on 2006-06-06
@n00b
figures :P

@ escapee
man, i'm stumped. it'd help if you could copy paste the exact output into a post here. in the mean time, i went to google for the answer and came across this thread:
[http://ubuntuforums.org/showthread.php?p=618981&highlight=unknown+hardware+address+type+776#post618981](http://ubuntuforums.org/showthread.php?p=618981&highlight=unknown+hardware+address+type+776#post618981)
his solution:
[http://ubuntuforums.org/showpost.php?p=642983&postcount=39](http://ubuntuforums.org/showpost.php?p=642983&postcount=39)
he's been having a similar issue, but this seems to be in regards to something else entirely. i'll keep searching and let you know, hopefully someone else more experienced may come along...

---

### Post by escapee from Winhell on 2006-06-06
thanks bro..as for copy and paste..not available..hastily did another install to make a new attempt...i'm going to try the build again for the ralink rt73 driver if it doesn't work i'll go back and try the easy-peasy meth and get the output for you...thanks for ya help bro...

---

### Post by ramcosca on 2006-06-06
[QUOTE=uzi09]umm, there is a unzipping utility for linux too :D you don't need wine for it. and it's probably in
 ~/.wine/drive_c/
directory[/QUOTE]
I thought I needed WINE for .exe files... :confused: 
Also, I cannot find my /.wine folder thing ](*,)

---

### Post by uzi09 on 2006-06-06
[QUOTE=ramcosca]I thought I needed WINE for .exe files... :confused: 
Also, I cannot find my /.wine folder thing ](*,)[/QUOTE]

for .EXE yes, for .zip - no.

```

sudo aptitude install unzip

```
that's how you install the unziping utility, then to unzip:

```

unzip file.zip

```

your .wine folder is in your home directory. the ~ is a shortcut to represent your home directory.


@escapee

oh yeah, forgot that you'd need to be on the internet to post the output :S.
if you can perhaps find some other way, it'd be quite helpful.

---

### Post by uzi09 on 2006-06-06
[QUOTE=escapee from Winhell]thanks bro..as for copy and paste..not available..hastily did another install to make a new attempt...i'm going to try the build again for the ralink rt73 driver if it doesn't work i'll go back and try the easy-peasy meth and get the output for you...thanks for ya help bro...[/QUOTE]

sorry to double post, but...

for this, with the makefile part. the author of the how-to is a bit vague in which directory he's talking about. i'm thinking that it may, in fact, not be that big of a deal where you copy MakeFile.6

from the README file under RT73 > Modules
```

Build Instructions:
====================
1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]

3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code

5> $cp rt73.bin /etc/Wireless/RT73STA/      # copy firmware

6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat
    # !!!check if it is a binary file before loading !!!

7> $load
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

```

perhaps we should try to do it using this...although this is relatively new to me, lemme see if i can figure out what they mean by any of this. 

again, get back to you soon...


EDIT: k, so i decided to try out *some* of these commands (geez, i hope this doesn't screw up my system, lol jk ;)), and it seems to work....i think:
From this directory:
RT73_Linux_STA_Drv1.0.3.0/Module
type this:
```

sudo cp Makefile.6 ./Makefile

```
the reason i used sudo here is because (for me) it's asking to confirm overwrite (i guess the file already exists), but when i hit yes, it didn't allow me to. said permission denied. i think we'll just force it :D

then type this:

```

chmod 755 Configure

```

then:
```

make config

```
k, so i kind of got stuck here with this error:
[email]uzi@mybochs:~/.down[/email]loads/RT73_Linux_STA_Drv1.0.3.0/Module$ make config
make: *** No rule to make target `config'.  Stop.

i think the reason for this is that there is no 'config' file. usually when you compile from source, you run these 3 commands:
./configure
make
make install

and usually that does the trick. but here...this is just retarded (for lack of a better word) :S

---

### Post by escapee from Winhell on 2006-06-06
lmmfao..you're gonna love this...i'm such a nut....i forgot to save the driverfiles to disk..haha..so now i'm downloading them...i have msn on other computer and added you so if you turn it on you should have invite...thanks bro..bear with me...as soon as i get the files down again.. i'll be at it again...

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=escapee from Winhell]hey noob........have you tried easyubuntu?...it's supposed to have ati and nvidia drivers...and a bunch of other stuff in it....it's at [www.easyubuntu.com(or](www.easyubuntu.com(or) .org..not sure which)...i d/l'd it earlier and it was a very simple click and go type interface...tabs for each of the diferent elements...multimedia..system..and a few others...check it out..not sure if it works on laptops or not...don't know what the differences are when it comes to setting them up...[/QUOTE]
I actually have used easyubuntu, great program BTW, but nVidia doesn't distibute PPC (mac) binaries and since they are proprietary I can't even compile them myself. There simply seems to be no way to get XGL working on a powerbook:(

---

### Post by uzi09 on 2006-06-07
[QUOTE=n00bWillingToLearn]I actually have used easyubuntu, great program BTW, but nVidia doesn't distibute PPC (mac) binaries and since they are proprietary I can't even compile them myself. There simply seems to be no way to get XGL working on a powerbook:([/QUOTE]

that may be true, but you may want to double check by taking a look at the ***ultimate*** XGL/AIGLX/Compiz thread ([http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+thread+rule](http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+compiz+thread+rule))

---

### Post by escapee from Winhell on 2006-06-09
hey guys thanks for all the help but after all the reading and picking at the scabs of my Belkin wound i'm finally online with it..........as i posted in another thread it took 3 commands in terminal to get me online..now i just gotta go back and set it to automatically come on when i boot...(don't know if that's gonna happen yet, guess we'll see when i reboot in a bit...lol)...anyway..in case anyone wants to know...i took the .sys file and the .inf off the setup disc that came with my Belkin adapter put'm in a file on Desktop..opened terminal........navigated to the directory of that folder...(i named my folder Belkin..)
so in the command line i typed   
cd Desktop/Belkin          that put me in that directory  and i typed 
sudo ndiswrapper -i rt73.inf ----------------------rt73.inf was my driver file
sudomodprobe ndiswrapper
sudo ifup wlan0-----------------------------wasn't sure if i needed "sudo" or not

but that's it...i then went to System at the top of the screen..went to administration then to netwworking deactivate eth0 and configured wireless to DHCP  (that's how my router's set up) and i'm online.....................thanks guys.......for all the help and head-banging you helped me to endure....hope this helps someone in the future...

---

