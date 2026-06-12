---
title: "Complete Newbie (i Need Step By Step Walk Throughs)"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by piNNoy on 2007-05-01
i read the faq i read alot on this forumn but i still cant do it........i just downloaded/installed ubuntu 7.04 last night. took me like 4 hours to get it totally installed. (had probs with partitions,bad disk ect.) 

(STILL NEED HELP WITH WIRELESS details on last page) *******************

problem 1:   right now im loaded up in the os...i connected my network cable to laptop, it says its connected i try to connect to the web (via firefox the normal webbrowser) and it wont detect anything. also i have a couple open wireless networds by me and it wont connect. (on my windows os it connects fine)

(SOLVED)         problem 2: **most important shoulda been problem 1**cant get my CUBE to work,    i downloaded this prog for the effects.. after  watching a video ([http://youtube.com/watch?v=_kHdSYLrmNw](http://youtube.com/watch?v=_kHdSYLrmNw))  i found out i want this on my new laptop from school. its 1.66ghz 502 mb ram ....  i enabled it on system > prefrences > desktop effects. and tried to use alt+crtl + left mouse button to move the cube but nothing happend.

(SOLVED)         problem 3: where do i get the simplest install of berly and HOW do i install it. (what programs do i need and such to install it on my ubuntu 7.04.

I basicly wanna do everything that guy did in that video above. I go to class in 3 hours and 30 minutes id like to try to get ALL of this fixed before i go to class n show it off! 

Sorry for being a COMPLETE AND TOTALY NEWBIE'R     but im in need.

---

### Post by jpatton on 2007-05-01
i guess make sure you're video card is beefy enough to support this stuff then i'd say

sudo apt-get install beryl

i think there are some other components that go along with that, can't remember, may be better to do 

sudo aptitude

and search for beryl

---

### Post by dfreer on 2007-05-01
First, read this post. 
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

Now, do you have your video card drivers correctly installed? And Direct Rendering is enabled?
The eaisest way I found is to do this (once the above is taken care of):
```
sudo apt-get install beryl beryl-manager emerald-themes
```
start beryl-manager and reload the window decorator and window theme and enjoy.

4 hours to install ubuntu?? that's very odd, I think I've spent at most 1-2 hours on most of my installs.

---

### Post by jpatton on 2007-05-01
> **dfreer said:**
> First, read this post. 
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

Now, do you have your video card drivers correctly installed? And Direct Rendering is enabled?
The eaisest way I found is to do this (once the above is taken care of):
```
sudo apt-get install beryl beryl-manager emerald-themes
```
start beryl-manager and reload the window decorator and window theme and enjoy.

4 hours to install ubuntu?? that's very odd, I think I've spent at most 1-2 hours on most of my installs.

i knew there was other junk than just beryl ;)

---

### Post by piNNoy on 2007-05-01
> **dfreer said:**
> First, read this post. 
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

Now, do you have your video card drivers correctly installed? And Direct Rendering is enabled?
The eaisest way I found is to do this (once the above is taken care of):
```
sudo apt-get install beryl beryl-manager emerald-themes
```
start beryl-manager and reload the window decorator and window theme and enjoy.

4 hours to install ubuntu?? that's very odd, I think I've spent at most 1-2 hours on most of my installs.

yep i read that site before twice lol i still want it..


hey i told ya i was newbie ... where do i type in "sudo apt-get install beryl beryl-manager emerald-themes" 

and my video card i couldnt find 'Direct Rendering' but i seen a couple other options that were turned off and i turned em on ...





hmm i just noticed something i hold crtl and alt and press esc nothing happens?? shouldnt it switch windows?? i checkd my keyboard config all looked fine

---

### Post by teddybairs1 on 2007-05-01
In order to run any command go to Applications --> Accessories --> Terminal and click it. At the command prompt either type out the commands or cut and paste them from where you got them.

In general, I find the easiest way to add the programs you want is to open up Synaptic, this is found in System --> Administration It will ask you for your password and then send you in.

Once there, just do a search for the package name(s) that you want, in this case I recommend searching for "Beryl", it should pull up all relevant packages. Mark the little boxes for installation by clicking on them and selecting mark for installation. Then when you are done, hit apply.

However, none of this is worth anything if you can't connect to the web. What are your hardware specs? What kind of Wifi card do you have? What kind of wired network card do you have? What kind of graphics card do you have? For example, I'm running a Dell which uses an Intel 915 graphics card with 128MB of shared video memory, it uses Broadcom network cards for both the wire and the wifi.

Let us know what you're running. Don't know if we can sort it out in a couple of hours but we can try.

---

### Post by piNNoy on 2007-05-01
> **teddybairs1 said:**
> In order to run any command go to Applications --> Accessories --> Terminal and click it. At the command prompt either type out the commands or cut and paste them from where you got them.

In general, I find the easiest way to add the programs you want is to open up Synaptic, this is found in System --> Administration It will ask you for your password and then send you in.

Once there, just do a search for the package name(s) that you want, in this case I recommend searching for "Beryl", it should pull up all relevant packages. Mark the little boxes for installation by clicking on them and selecting mark for installation. Then when you are done, hit apply.

However, none of this is worth anything if you can't connect to the web. What are your hardware specs? What kind of Wifi card do you have? What kind of wired network card do you have? What kind of graphics card do you have? For example, I'm running a Dell which uses an Intel 915 graphics card with 128MB of shared video memory, it uses Broadcom network cards for both the wire and the wifi.

Let us know what you're running. Don't know if we can sort it out in a couple of hours but we can try.



GREAT INFORMATION !! A+++ would buy from again! lol 

my specs are 
IBM ThinkPad R60 (lenovo)
Processor Speed: Genuine Intel)R_ CPU T2300 @ 1662 MHZ
Processor: x86 family 6 model 14 stepping 8   (LOL WTF)
Mininum graphics memory 8 mb 
Maximum graphics memory 224 mb         
Mobile Intel(R) 945GM Express chipset family  
pysical memory: 502 mb
direct x versoin 9.0

sry if i added to much tried not to leave anything out 
if i did leave anything out lemme know what

oh and i have windows on c drive 30 gb 
and ubuntu on another drive ext3 or something 29 gb


crap network card sec..
11a/b/g/ Wireless LAN Mini PCI Express Adapter
Broadcom NetXtreme Gigabit Ethernet

---

### Post by teddybairs1 on 2007-05-01
Ok, to my knowledge, which is limited to be sure, your Graphics card should have no problems running beryl. Just use synaptic and install all packages relevant to beryl. Read through the descriptions if you're not sure. Beryl itself is still a beta, so don't expect it to work all the time. It's basically a toy. I've got it, and I use it on occasion, but it also does mess up some times and I have to revert to metacity (the gnome window manager).

What we need to know is the network card specs. It's odd that Ubuntu isn't recognizing your wired network card. Wifi card support is notorious for problems in Linux (although it is definitely getting better), but network cards generally work out of the box. You said that you weren't getting any kind of a connection on your wired card, is that correct? How are you going online to the forum? On a separate system?

Ok, I just caught the network card. Is this your wifi or your wired or both? If it's your wifi and it's a broadcom, you may need either the firmware, or use ndiswrapper to work in the windows drivers. There are different posts on this forum which provide excellent guides for both. just do the search for your hardware, for ndiswrapper, etc. and you should turn up something. This is something which may take a few days to get straightened out. WiFi cards are a pain under Linux. They're a hundred times better under Feisty, but Broadcom in general is a pain because they're stingy with their drivers.

---

### Post by piNNoy on 2007-05-01
> **teddybairs1 said:**
> Ok, to my knowledge, which is limited to be sure, your Graphics card should have no problems running beryl. Just use synaptic and install all packages relevant to beryl. Read through the descriptions if you're not sure. Beryl itself is still a beta, so don't expect it to work all the time. It's basically a toy. I've got it, and I use it on occasion, but it also does mess up some times and I have to revert to metacity (the gnome window manager).

What we need to know is the network card specs. It's odd that Ubuntu isn't recognizing your wired network card. Wifi card support is notorious for problems in Linux (although it is definitely getting better), but network cards generally work out of the box. You said that you weren't getting any kind of a connection on your wired card, is that correct? How are you going online to the forum? On a separate system?

Ok, I just caught the network card. Is this your wifi or your wired or both? If it's your wifi and it's a broadcom, you may need either the firmware, or use ndiswrapper to work in the windows drivers. There are different posts on this forum which provide excellent guides for both. just do the search for your hardware, for ndiswrapper, etc. and you should turn up something. This is something which may take a few days to get straightened out. WiFi cards are a pain under Linux. They're a hundred times better under Feisty, but Broadcom in general is a pain because they're stingy with their drivers.



ok ill try these things,, another thing since berly is so buggy ... what would you recommend that is similair to that ?? i mostly want the clear cube thats about it

---

### Post by teddybairs1 on 2007-05-01
Both Beryl and Compiz have bugs. These are pretty much your options. this being said, it's not that they're unusable. It's just they have problems every once in a while. I got everything running, started playing with the 3-d cube, the fire effects, etc. and loved it. But I also found that after a while it just becomes routine and a toy to play with that I pull out every once and a while. Beryl is probably a better choice and more stable than Compiz.

---

### Post by piNNoy on 2007-05-01
ok i dled  wlassistant-0.5.7.tar.bz2  and ndiswrapper-1.43.tar.gz  

how do i unzip or install them? 

what do i type in terminal 

gz and bz2  files do you have to un zip them? or just install?

---

### Post by teddybairs1 on 2007-05-01
Ok, wlassistant is going to be worthless to you at the moment, and has to do with detecting and connecting to wireless networks. As I said before, we need to get your wireless card working before we can use it.

You downloaded what looks like source packages. Unless you are familiar with compiling and packaging, these will also be worthless to you. In order to install a program by hand (hereafter referred to as manually) you need to get the .deb file from the ubuntu repos. This is found at:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

At the top of the web page you will find a set of tabs which correspond to each Ubuntu distribution. Click on the one which matches your distribution. This will put you into a page which lists a number of categories. You can select packages by categories.

the other option is, on the initial screen for packages.ubuntu.com there is a search feature. You enter your search criteria (i.e. name of the package you want, or a one word description of what you're looking for), and mark which version of ubuntu you want the engine to look in for your package.

In this case you want to look for "ndiswrapper". This should bring up any package which has to do with ndiswrapper. In order to search for wlassistant do the same.

Now, as it comes up with a list of packages which match your search, you will want to locate the package which matches what you want. Click on it. From here you will get a description of the package, and it's list of dependencies. This is where it get's tricky, and why Synaptic is such a godsend because it does all this for you.

In order to install a package, you must have all of it's dependencies satisfied. Where ndiswrapper is concerned, a part of it is already pre-installed into Ubuntu proper if I remember right.

The packages you want are ndiswrapper-common (should already be in feisty, check with Synaptic), and ndiswrapper-utils-1.9 They have their own dependencies. Check with Synaptic to ensure that each dependency is satisfied. The packages you want to look for (its dependencies) are "perl" and "ndiswrapper-common". Search for them in Synaptic and make sure they're there. (You're going to see libc6 pop up a lot as a dependency. Don't worry about this one, it's a core component of the OS and is already there)

Assuming that all dependencies are met, install the ndiswrapper packages by right clicking on the downloaded package and selecting GDebi package manager. Enter your password and let it do it's thing. When it's satisfied, hit install and let it work.

Now, once you have Ndiswrapper installed, now what?

You need the windows drivers for your wireless card. Go to Broadcom's website and see if you can't find them. Elsewise, do a search online. Somebody has to have them. Specifically you are looking for a .inf file and a .sys file.

I'm not an expert on ndiswrapper, but there are excellent guides here on the forum. Just do a search for ndiswrapper and you'll turn one up. There are also wikis online about this piece of software which provide good instructions. Do a google search for it.

Unfortunately doing a manual install of a .deb package can be a bit of a pain, but it's not impossible; it's just not as easy as going through synaptic or add/remove and hitting "apply".

What about your wired card? Is it a total no-go or what?

---

### Post by piNNoy on 2007-05-02
somehow ..... my wired card worked PERFECT when i was at school.but when i got home .. it says its connected but i cant get on the internet ...... i installed 1 app and updated the OS (at school connected wired.) (was amazing =p ) app i installed was kde networking managering thing that didnt fix my problem 1 bit =[ 

as for my wireless........still reading up on it.......

---

### Post by teddybairs1 on 2007-05-02
What's the difference between your hi-speed connection at home and at school? It may have nothing to do with your network card at all, but with your service. What's your hi speed service at home, router, hardware, etc; and the same at school? Chance are if it worked once at school on the wire, it'll work all the time on the wire.

---

### Post by piNNoy on 2007-05-04
ok so i installed the madwifi drivers and my wifi still dosent work =[ helps 

from [http://www.thinkwiki.org/wiki/Madwifi](http://www.thinkwiki.org/wiki/Madwifi)

screenshots - 

[IMG]http://i71.photobucket.com/albums/i152/piNNoy/poopu/nnhelpnshot.png[/IMG]

[IMG]http://i71.photobucket.com/albums/i152/piNNoy/poopu/help.png[/IMG]

what am i doing wrong? or what else do i need to do

---

### Post by teddybairs1 on 2007-05-04
Ok, first... You don't need to use the command line to install a package. use Synaptic under System-->Administration. Just type in the name of the package you want and it will find it for you. For a complete newbie, I would recommend not setting foot in the command line unless you absolutely have to. It's a lot more user friendly and you don't have to worry about the frustration of putting one letter or character out of line in a long command sentence.

Second, what are the specs of your wifi card? MADWiFi is for Atheros cards I believe. Mine is a Broadcom 4318. Find out what kind of a wifi card you have and then do two things, reply to this post, and then do a search on this forum for your wifi make and model and see what other people have said about it.

---

### Post by piNNoy on 2007-05-04
> **teddybairs1 said:**
> Ok, first... You don't need to use the command line to install a package. use Synaptic under System-->Administration. Just type in the name of the package you want and it will find it for you. For a complete newbie, I would recommend not setting foot in the command line unless you absolutely have to. It's a lot more user friendly and you don't have to worry about the frustration of putting one letter or character out of line in a long command sentence.

Second, what are the specs of your wifi card? MADWiFi is for Atheros cards I believe. Mine is a Broadcom 4318. Find out what kind of a wifi card you have and then do two things, reply to this post, and then do a search on this forum for your wifi make and model and see what other people have said about it.

wifi card specs: AR5212 802.11abg NIC 

searching now sir

---

### Post by teddybairs1 on 2007-05-04
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=429537](http://ubuntuforums.org/showthread.php?t=429537)

It may help.

---

### Post by piNNoy on 2007-05-05
getting closer.....ithink

on 'step 0' from 
[https://help.ubuntu.com/community/WifiDocs/WiFiWithSomeoneElsesRouter](https://help.ubuntu.com/community/WifiDocs/WiFiWithSomeoneElsesRouter)

typed in modprobe -l ath*
that command is invalid....

also on the channel 
i type iwlist scan and see its Cell 04

how do i get on that channel? 

Example: iwconfig ath0 channel 4??????????

---

### Post by dfreer on 2007-05-05
wait... post your results from these commands:
```
iwconfig
```
```
iwlist scan
```


I'm thinking scanning doesn't work unless your wireless card is working...

---

### Post by piNNoy on 2007-05-08
> **dfreer said:**
> wait... post your results from these commands:
```
iwconfig
```
```
iwlist scan
```


I'm thinking scanning doesn't work unless your wireless card is working...



im at school right now but its the same thing with diff routers



pinnoy@pinnoy:~$ iwconfi
bash: iwconfi: command not found
pinnoy@pinnoy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Free Wireless"  Nickname:"Free Wireless"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:10257  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pinnoy@pinnoy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:40:96:5C:4D:69
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 9E:7B:E4:E8:B0:45
                    ESSID:"Free Public WiFi"
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/94  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

---

### Post by dfreer on 2007-05-08
sure looks like your wireless is working to me.
try finding a router that has no security enabled (no encryption, public AP), or set your home router that way. Then connect manually to the router (in this example the router has an essid of your_essid_here)
```
sudo iwconfig ath0 essid "your_essid_here"
sudo dhclient ath0
ping www.google.com
```

EDIT: those quotes are necessary in the first line. just change the actual name of the essid itself. for example, most linksys routers ship with the essid of *linksys*, so you would connect using *sudo iwconfig ath0 essid "linksys"*

---

