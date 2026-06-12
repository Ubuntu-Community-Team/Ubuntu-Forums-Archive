---
title: "internet problem"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by freduard0 4 on 2008-02-20
Hi,
I just downloaded ubuntu 7.10 yesterday on my computer. I installed it and my internet would not work. I looked for a wireless adapter that worked "out of the box" with ubuntu and I found one. The linksys WUSB54GC model. The internet does work, but it works very slow, almost too slow to function. But recently I have not even been able to connect. I am not very smart with this stuff so can you please be specific.
:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by divindavid on 2008-02-20
can u tell me what u get with "iwconfig" in the terminal

---

### Post by freduard0 4 on 2008-02-20
Now, when I connect, the wireless signal works for a few seconds, then doesnt work again, 
Please help
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-20
I've Tried multiple USB ports

---

### Post by freduard0 4 on 2008-02-20
This Is what my computer specs are: a compaq presario.20gig HDD 1.20 GHz intel celeron 512 mb RAM
Could it be a bad computer, because it is my old one
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-20
Can someone please help
:popcorn::popcorn::popcorn::popcorn::popcorn:
 Spanks, 
  Freduardo

---

### Post by freduard0 4 on 2008-02-20
I really need help with this guys
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-20
n::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by ispy on 2008-02-20
why don't you start by posting the output of 
```

iwconfig
```

once you've done that, maybe we can help.

---

### Post by jcitguy78 on 2008-02-20
i know some people in this forum are good but without the 'iwconfig' output don't know where to start or what advice to give

---

### Post by freduard0 4 on 2008-02-21
'iwconfig'
Wlan:0     IEEE 802.11g   ESSID: "Hance Network"
                Mode: Managed   Frequency: 2.422 GHz   Access Point: 00:1B:11:62:AB:44
                Retry Min Limit: 7   RTS thr: off   Fragment thr= 2346 B
                Link Quality:0   Signal level:0   Noise Level:0
                Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
                Tx exessive retries:0   invalid misc:0   Missed beacon:0

Thanks
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by divindavid on 2008-02-21
when you connect can you go to a web page or send an IM

---

### Post by divindavid on 2008-02-22
the same thing hallened to me but it fixed itself after i upgraded to 7.10 but i see you already are

---

### Post by divindavid on 2008-02-22
hey freddie what if you put your linux computer ware you other computer is just unitll you get the problem fixed so do a wired connection to it and then it will be easer to show the terminal results

---

### Post by freduard0 4 on 2008-02-22
I cannot go to any web page or send an IM, it wont even let me sign onto aim

When You said to put it on my other computer, do you mean just with the CD, or actually install it

:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by divindavid on 2008-02-22
no freddie just move the computer in the paino room so you can get on the internet using a wired connection

---

### Post by freduard0 4 on 2008-02-22
no
Can't I just get the wireless connection? It said the wireless thing workd out of the box
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by divindavid on 2008-02-22
i dono freddie go to my post where i had problems and see if any of those things helped


[http://ubuntuforums.org/showthread.php?t=694742&page=1](http://ubuntuforums.org/showthread.php?t=694742&page=1)

---

### Post by freduard0 4 on 2008-02-23
What is the problem with the wireless internet? Everything else in my house connects, but this will only connect for a few seconds, then I cannot even find the network.
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-23
I am getting very mad at this point with the internet, it said the wireless adapter worked "out of the box" and it didn't. Now all I want is just to have the internet, maybe I should download the 8.04 or something, because I really need the internet, and I don't care about bugs at this time. Any help that will let me keep the 7.10 and not move my computer to wired internet would be greatly appreciated.
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-23
what are you specs?

---

### Post by freduard0 4 on 2008-02-23
As stated earlier, a compaq presario.20gig HDD 1.20 GHz intel celeron 512 mb RAM

---

### Post by divindavid on 2008-02-23
sorry i forgot 

with the internet problem "pashents young grasshoppa"

---

### Post by freduard0 4 on 2008-02-23
It's okay, but do you have any ideas on how to help with the internet (and with your spelling) 

BTW it's patience
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-23
Any help would be very helpful at this time
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-23
I don't think I could really help you on this one, sorry, any one else got anything?

---

### Post by richaoj on 2008-02-23
Despite the fact that you are being somewhat impatient and a little rude with your spelling comment, I will give you a little help . . . . . 

I have recently (within the last couple of months) had problems with the default network-manager daemon in ubuntu.  It seems to drop wireless connection occasionally for me too.  What i have done is switch over to wicd--another wireless manager that -- for me at least-- seems to work better and more consistently.  You can install it by following these directions:
Installing Wicd in Ubuntu

(from [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php))
_____________________________________________________________________
Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras 

where feisty is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".
_________________________________________________________________________

occasionally the tray icon will not pop up from me, but you can always find wicd under your menu in the internet section.

Good luck, and if you temper your attitude a bit, i suspect you will receive more help here on the forums

---

### Post by divindavid on 2008-02-24
how is he going to install it if he does not have internet

about the spelling me and freddie are friends in real life it was kinda a joke

---

### Post by divindavid on 2008-02-24
and hes running gutsy not feisty (i installed it on his computer)

---

### Post by freduard0 4 on 2008-02-24
Yeah, it wouldn't let me download it, but thanks for the help, and I apologize for not being patient, but my dad is getting mad at me for not being able to get on the internet on that computer.
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by divindavid on 2008-02-24
so would 8.04 be good for him so i am told it is better for drivers and what not

---

### Post by richaoj on 2008-02-24
I really don't think that it is a driver issue.  I use gutsy as well, on several different machines (I support a little local ubuntu community of my friends and colleagues around me.) and it seems that there was an update to network-manager maybe about 4 months ago that screwed up the wireless on several of those machines and would cause them to drop wireless connections after a while, or not show wireless essid that I knew to be there etc and some other strange behavior.  I don't know if this was a local problem -- i didn't go searching for it in launchpad or anything, but i do remember reading something about it.  

Is there a hard-wire option that you could connect to to try wicd?  
also, if you have a friend that has ubuntu on a laptop with working wireless, you could always download the .deb and put it on a flash drive or something.

good luck with the problem, and sorry if i missed some inside humor or was short b4.

---

### Post by timbounceback on 2008-02-24
no, I wouldn't recommend using 8.04 just yet. So what does the icon with the signal strength (nm-applet) look like right now? Have you actually connected but it won't load anything, or are you not even connected. You need to be more specific

---

### Post by freduard0 4 on 2008-02-24
What happens is that I see the essid, and it shows the signal strength and everything, I try to connect, and that's when the problem occurs. Sometimes I connect for less than a minute, then it just loses connection, but other times it won't even connect. When I do connect it's not long enough to do anything with the internet. Thanks for all the help guys.
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by freduard0 4 on 2008-02-24
I'm getting my flash drive back tomorrow (my friend stole it for a S.S. project), so i'll try the wicd then. 
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

---

### Post by divindavid on 2008-02-24
freddie i can come over and i can bring my laptop and my thumb drive

---

### Post by divindavid on 2008-02-24
> **freduard0 4 said:**
> I'm getting my flash drive back tomorrow (my friend stole it for a S.S. project), so i'll try the wicd then. 
:popcorn::popcorn::popcorn::popcorn::popcorn:
   Freduardo

freddie you cant download a linux file in windows and then put it on a flash drive

---

### Post by uberlube on 2008-02-24
Why not? Linux reads and writes to NTFS

---

### Post by divindavid on 2008-02-25
how would he/I download a linux file in windows

---

### Post by divindavid on 2008-02-25
i reason why i sayed he/i is because chances are i will be doing this for him with my laptop

---

### Post by incen on 2008-02-25
You may need to go to
Applications -> Accessories -> Terminal
And then type
```
iwconfig
```
as everyone mentioned above.

Then, post the result. :)

---

### Post by freduard0 4 on 2008-02-25
'iwconfig'
Wlan:0 IEEE 802.11g ESSID: "Hance Network"
Mode: Managed Frequency: 2.422 GHz Access Point: 00:1B:11:62:AB:44
Retry Min Limit: 7 RTS thr: off Fragment thr= 2346 B
Link Quality:0 Signal level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx exessive retries:0 invalid misc:0 Missed beacon:0
:popcorn::popcorn::popcorn::popcorn::popcorn:
freduardo

---

### Post by freduard0 4 on 2008-02-25
How do I download wicd through windows?
:popcorn::popcorn::popcorn::popcorn::popcorn:
  Freduardo

---

### Post by divindavid on 2008-02-26
i dono if you cant i will bring my laptop to ur house freddie

---

### Post by freduard0 4 on 2008-02-26
Ok cool
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-27
yep freddie

---

### Post by richaoj on 2008-02-27
you can download a linux file in windows just like you can download a .exe in linux.  It just won't run in windows, but what you are downloading is a series of 1's and 0's.  Just download wicd, and put it on a flash drive, plug it into the other system and double click on the package file.  Here is a link to exactly what you should download:

[http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0)

Specific instructions:

1. Remove network-manager ("sudo apt-get remove --purge network-manager")
2. Double click the wicd .deb package on your flash drive - click ok to install
3. Under internet in your menu, you should find wicd.
4. To auto-startup wicd under Preferences -> Sessions in the Startup tab click the "New". the command is "/opt/wicd/tray.py".

---

### Post by richaoj on 2008-02-27
p.s. when you remove network manager, it may say something about removing ubuntu-desktop.  DON't freak out, this is ok as ubuntu-desktop is just a meta-package of all of the packages for ubuntu desktop.  you aren't actually removing ubuntu.  it'll be ok, i promise =)

---

### Post by freduard0 4 on 2008-02-28
It wouldn't let me do it, it said i had an error, I will post the output when I get home
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-28
sweet i did it on my computer and it worked now to see if freddies works
if so many people have seccuss with this program why isnt it preinstalled in ubuntu

---

### Post by timbounceback on 2008-02-28
> **divindavid said:**
> if so many people have seccuss with this program why isnt it preinstalled in ubuntu
actually, other than you, only one other person has said it has worked for them. after all, network-manager has a larger, stronger community base, is more widely used, and is probably updated more frequently.

---

### Post by freduard0 4 on 2008-02-28
This Is what came back when I put in "sudo apt-get remove --purge network-manager":

freddie@freddie-desktop:~$ sudo apt-get remove --purge network-manager 
[sudo] password for freddie: 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following extra packages will be installed: 
  libpango1.0-0 libpango1.0-common 
Suggested packages: 
  ttf-thryomanes ttf-baekmuk ttf-arphic-gkai00mp ttf-arphic-bkai00mp 
The following packages will be REMOVED: 
  network-manager* network-manager-gnome* 
The following packages will be upgraded: 
  libpango1.0-0 libpango1.0-common 
2 upgraded, 0 newly installed, 2 to remove and 196 not upgraded. 
Need to get 357kB of archives. 
After unpacking 2470kB disk space will be freed. 
Do you want to continue [Y/n]? y 
WARNING: The following packages cannot be authenticated! 
  libpango1.0-common libpango1.0-0 
Install these packages without verification [y/N]? y 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libpango1.0-common 1.18.3-0ubuntu1 
  Could not resolve 'archive.ubuntu.com' 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main libpango1.0-0 1.18.3-0ubuntu1 
  Could not resolve 'archive.ubuntu.com' 
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb)  Could not resolve 'archive.ubuntu.com' 
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb)  Could not resolve 'archive.ubuntu.com' 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
freddie@freddie-desktop:~$  
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by freduard0 4 on 2008-02-28
lalala!!!!

---

### Post by divindavid on 2008-02-28
freddie does it work

---

### Post by richaoj on 2008-02-28
from what i can see, the errors come from your computer trying to download two packages - libpango1.0-0 and libpango1.0-common.  These packages are not required to install wicd.  The dependencies that it needs should be already on your system . . . 

good luck!?

ps.  in response to timbounceback:
[http://ubuntuforums.org/showthread.php?t=587010&highlight=wicd](http://ubuntuforums.org/showthread.php?t=587010&highlight=wicd)

network-manager is truly broken /crippled on many laptops with wifi.  the reason i use linux is because of the truly vast amounts of choices i have to get my system working exactly the way i want it too.  wicd works for me.  network-manager may work for you.  it's ok for us both to enjoy our computing experience.

pps - if you are missing any dependencies - the installer will tell you - (i don't think you will be) but just in case - you can always pull packages you need off packages.ubuntu.com

---

### Post by freduard0 4 on 2008-02-29
Why doesn't the WICD install right?
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-29
more info?

---

### Post by divindavid on 2008-02-29
did u uninstall network manager do u have the network sysemble on the top right?

---

### Post by freduard0 4 on 2008-02-29
OMG!!! I connected to the internet for a minute, but it was just enough time to install the packages, which let me uninstall network manager, so I just installed WICD... hopefully it works

---

### Post by freduard0 4 on 2008-02-29
Ok... so now I can connect, but there is a new problem. It is very slow. I have a linksys WUSB54GC model wireless adapter. I also have an 802.11n D-link router, which I know works, everything in my house can connect. I'm just wondering why the internet is so slow.
Thanks
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-29
is it faster that it was when u first got it
do a speed test
internetfrog.com

---

### Post by freduard0 4 on 2008-02-29
I dont hav the patience to wait for internetfrog, but i guess i'll put it up and wait:(
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by divindavid on 2008-02-29
it is that slow is ur internet adapter in the  "high speed usb 2.0 slot"

---

### Post by divindavid on 2008-02-29
does wicd alaways go slow

---

### Post by divindavid on 2008-03-01
so freddie can wicd connect to your network and do stuff on your network

---

### Post by freduard0 4 on 2008-03-05
It can download some of the updates, but pidgin doesn't work. I haven't waited long enough to see if firefox works, so I don't really know.
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by freduard0 4 on 2008-03-07
should I run some sort of code or sumthing? Or should i bring back the wireless adapter? 
Thanks
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

### Post by freduard0 4 on 2008-03-09
Alright, this is really weird, but last night, I decided to try to connect to the internet with ubuntu, I actually got connected, and it worked fine. So I thought, why not post it on here, so I try to post something, and then I can't connect again. It makes no sense. I'm gonna see if I can get on to do the internetfrog thing.
:popcorn::popcorn::popcorn::popcorn::popcorn:
Freduardo

---

