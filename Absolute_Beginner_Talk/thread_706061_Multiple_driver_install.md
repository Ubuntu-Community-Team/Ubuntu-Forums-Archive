---
title: "Multiple driver install"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by rudolphna on 2008-02-24
ok  i just installed linux on a 40GB partition on my hdd.  It is Ubuntu 7.10.  The problem... is drivers.  I use a wireless network  card (WG111T) I tried to follow the tutorial, but it doenst work.  It refuses to install, and now i cant even enter root in terminal, because when i try to type in my password, nothing happens, no characters/numbers appear at all.  ndiswrapper doesnt install no matter what i try to do, and the install guide that downloads with it is as clear as mud.  Oh, and i also need help installing the Nvidia graphics drivers, as they wont install either.  i cant take running in 1024 res anymore, its driving me bananas..  Anyone help please?  (im currently running on my windows xp install to type this =P)
(First i need to get terminal working again though)

---

### Post by oedha on 2008-02-24
for nvidia.....have you install the driver for it ?
in using ndiswrapper...you need the windows installation file of your wireless ?

---

### Post by rudolphna on 2008-02-24
i downloaded the linux 32bit driver from NVIDIAs website, and it is sitting on my desktop. but when i try to run it, it tries to open it in textedit, and says that  "*Could not open the file /home/nick/Desktop/NVIDI…ux-x86-169.09-pkg1(2).run."*   "[I]gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I]
 
im going to try to reinstall it... AGAIN.

---

### Post by oedha on 2008-02-24
go to terminal
you suppose to install it by
sudo sh /home/nick/Desktop/NVIDIA...............run

---

### Post by rudolphna on 2008-02-24
it doesnt work.  i also tried apt-get install nvidia.....  but it stops at saying it cant find that file

---

### Post by rudolphna on 2008-02-24
for now ill focus on the network drivers. here is what i did and got

root@nick-desktop:~# apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.0kB of archives.
After unpacking 102kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main ndiswrapper-common 1.38-1ubuntu1 [18.0kB]
Fetched 18.0kB in 0s (44.2kB/s)           
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 104951 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
root@nick-desktop:~# ndiswrapper
Error: no versions of ndiswrapper found!


im realy new to it so im hoping you can tell me what the problem might be

---

### Post by Awperator on 2008-02-24
> **rudolphna said:**
> it doesnt work.  i also tried apt-get install nvidia.....  but it stops at saying it cant find that file

Lol man, apt-get install Nvidia... if only it were that easy
Try envy to install your nvidia drivers. Worked for me:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by uberlube on 2008-02-24
Have you already tried to install using ENVY?

---

### Post by rudolphna on 2008-02-24
i just did.  it installed fine, but i still cant run at 1280x 1024. oh well.  can you help me sort out the network drivers please?  thanks lol  i know so little about linux its ridiculous. im a computer tech but linux escapes my knowledge

---

### Post by uberlube on 2008-02-24
LoL no prob. What network device are you trying to install?

---

### Post by rudolphna on 2008-02-24
the Netgear WG111T Wireless USB 2.0 adaptor. I have the disk, and it works perfectly in Windows XP, but im clueless as to how to install it here. i tried installing niswrapper but it wont install, i must be doing something wrong.

---

### Post by rudolphna on 2008-02-24
(PS the integrated Yukon Ethernet card works automatically)

---

### Post by uberlube on 2008-02-24
Ok list the files on the driver disk you have

---

### Post by rudolphna on 2008-02-24
ok, but there is alot.

main folder>  ar5523.bin
                          autorun.inf
                          autorun.EXE
                          netwg11t.cat
                          netwg11t.inf
                            TRANSL.TBL
                         WG11TND5.sys

  Utility folder

SETUP.EXE
TRANSL.TBL

NDIS folder

ar5523.bin
netwg11.cat
netwg11t.inf
TRANS.TBL
WG11TND5.sys

---

### Post by uberlube on 2008-02-24
Ok good there is a NDIS folder. So open a root terminal:

sudo su
*password*

then type in these commands:
mkdir /root/wireless_driver
cd /root/wireless_driver/

then copy the NDIS folder into the directory you just made. Then in terminal type:

cd NDIS (remember its case sensitive) 
ndiswrapper -i netwg11t.inf
reboot

Then hopefully it will recognize the card during boot.

---

### Post by rudolphna on 2008-02-24
ok i feel really dumb..  i copied both of those command lines at the same time, and in the terminal it now says [I] root@nick-desktop:~/wireless_driver# 
[/I]
   but now im not sure what to do.... where is the directory located at? (sorry i know nothing about linux =P)

---

### Post by rudolphna on 2008-02-24
i tried copying/pasting the NDIS folder into the terminal, and this what it looks like

root@nick-desktop:~/wireless_driver# /media/cdrom1/ndis5
bash: /media/cdrom1/ndis5: is a directory
root@nick-desktop:~/wireless_driver#

---

### Post by uberlube on 2008-02-24
Your better off using the file manager with root mode to copy the NDIS folder to where its supposed to go.
In terminal type:

sudo nautilus 

This will open the root file manager

---

### Post by rudolphna on 2008-02-24
ok its copied. now for hte last command line, i tried this
root@nick-desktop:/home/nick# cd NDIS ndiswrapper -i netwg11t.inf
bash: cd: NDIS: No such file or directory
root@nick-desktop:/home/nick#

and nothing happened -.-  ugh

---

### Post by uberlube on 2008-02-24
in terminal you should be in this folder:

cd /root/wireless_driver/NDIS/

and then type in:

ndiswrapper -i netwg11t.inf

---

### Post by rudolphna on 2008-02-24
GRAH!!!  How do you get to that folder in Terminal (god now i know how my grandmother felt when i tried to teach her how her car works =P)    here is the last several lines i tried

root@nick-desktop:~/wireless_driver# /media/cdrom1/ndis5
bash: /media/cdrom1/ndis5: is a directory
root@nick-desktop:~/wireless_driver# /NDIS
bash: /NDIS: No such file or directory
root@nick-desktop:~/wireless_driver# /root/wireless_driver/NDIS/ndiswrapper -i netwg11t.inf
bash: /root/wireless_driver/NDIS/ndiswrapper: No such file or directory
root@nick-desktop:~/wireless_driver# ndiswrapper -i netwg11t.inf


im sorry for being such a moron =P

---

### Post by uberlube on 2008-02-24
No problem dude, your still learning:

Lets start from scratch open a fresh terminal and type in these lines individually and press enter:

sudo su
*password*
cd /root
cd /wireless_driver
cd /NDIS

---

### Post by rudolphna on 2008-02-24
after the first command cd/root it says "no such file or directory"  =P

nick@nick-desktop:~$ sudo su
root@nick-desktop:/home/nick# cd/root
bash: cd/root: No such file or directory
root@nick-desktop:/home/nick#

---

### Post by uberlube on 2008-02-24
did you put a space between: cd /root

---

### Post by rudolphna on 2008-02-24
aaahhhh...

---

### Post by rudolphna on 2008-02-24
same thing with the next one, only i used the space

root@nick-desktop:~# cd <space>/wireless_driver
bash: cd: /wireless_driver: No such file or directory

---

### Post by uberlube on 2008-02-24
sorry take out the backslash and try again

cd wirless_driver

---

### Post by uberlube on 2008-02-24
then cd NDIS

---

### Post by rudolphna on 2008-02-24
ok did that and got to the last step, at which...

root@nick-desktop:~# cd wireless_driver
root@nick-desktop:~/wireless_driver# cd NDIS
bash: cd: NDIS: No such file or directory
root@nick-desktop:~/wireless_driver# cd /NDIS
bash: cd: /NDIS: No such file or directory
root@nick-desktop:~/wireless_driver#

---

### Post by rudolphna on 2008-02-24
you know, the sad thing is i installed it because its an open source, i wanted to learn how to program....  and i cant even install a network driver properly =P

---

### Post by uberlube on 2008-02-24
Well this is how we all learn linux, trial and error. OK I believe the problem is that:

a) you didnt copy the NDIS folder to /root/wireless_driver/
b) you did put it in the right directory but NDIS is in lowercase 'ndis' so 'cd ndis' is the proper as the terminal is case sensitive. While in the /root/wirless_driver/ folder in terminal typr in:

ls

to show what is in the directory (ls=LS not iS)
If NDIS isnt in there then we need to put it there. This is dont by opening the nautilus root window manager

sudo nautilus
if not installed then type

sudo apt-get install nautilus

and then 'sudo nautilus' to open

---

### Post by rudolphna on 2008-02-24
here is why i think.. ok now what do i do

root@nick-desktop:~/wireless_driver# ls
ndis5

root@nick-desktop:~/wireless_driver# cd /ndis
bash: cd: /ndis: No such file or directory
root@nick-desktop:~/wireless_driver# ndis5
bash: ndis5: command not found
root@nick-desktop:~/wireless_driver# cd ndis5
root@nick-desktop:~/wireless_driver/ndis5#  (this is open to type in)

---

### Post by uberlube on 2008-02-24
kn now type 'ls' and then enter and tell me what files are in there

---

### Post by rudolphna on 2008-02-24
root@nick-desktop:~/wireless_driver/ndis5# ls
ar5523.bin 
 netwg11t.cat  netwg11t.inf  
TRANS.TBL 
 WG11TND5.sys
root@nick-desktop:~/wireless_driver/ndis5#

---

### Post by uberlube on 2008-02-24
Ok now type in:

ndiswrapper -i netwg11t.inf

and if it works type in reboot. Ill wait until your back online to tell me what happend.

If it doesnt work, post the output.

---

### Post by rudolphna on 2008-02-24
root@nick-desktop:~/wireless_driver/ndis5# ndiswrapper -i netwg11t.inf
Error: no versions of ndiswrapper found!
root@nick-desktop:~/wireless_driver/ndis5# 

didnt work

---

### Post by uberlube on 2008-02-24
lol ok.

sudo apt-get install ndiswrapper

then once installed press the up directional arrow until you get the ndis -i driver command you used before and press enter

---

### Post by rudolphna on 2008-02-24
hey another quick question, using cd (must be a common command) i am trying to add 1280x 1024 resolution, using this thread, but im stuck at
[http://ubuntuforums.org/showthread.php?t=221263](http://ubuntuforums.org/showthread.php?t=221263)


 cd xorg.conf
bash: cd: xorg.conf: Not a directory
root@nick-desktop:/etc/X11#  cd /xorg.conf
bash: cd: /xorg.conf: No such file or directory
root@nick-desktop:/etc/X11#

---

### Post by rudolphna on 2008-02-24
-.- right back where i started in the first place

root@nick-desktop:/home/nick# apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
root@nick-desktop:/home/nick#

---

### Post by uberlube on 2008-02-24
Open up the synaptic package manager and do a search for ndiswrapper. When you see it click the checkbox and go apply to install.

If you used ENVY to install the graphics driver look in your menu for the nvidia tool and choose your resolution in there. If it doesnt list the resolution you want you probobally cant get it. Plus I personally dont like editing .xorg because I suck at it and if you make 1 mistake it messes everything up.

---

### Post by rudolphna on 2008-02-24
(woohoo finally 1280x1024 thanks! =D)   and i think it worked. here is what i got

root@nick-desktop:~/wireless_driver/ndis5#  ndiswrapper -i netwg11t.inf
installing netwg11t ...
root@nick-desktop:~/wireless_driver/ndis5#

---

### Post by rudolphna on 2008-02-24
(i still have a lot more questions so ^^ lol) im in a good mood no errors this time lol  (course it could be from lack of sleep too)

---

### Post by uberlube on 2008-02-24
Insomnia is our friend:lolflag:

ok now type in:

modprobe ndiswrapper

---

### Post by rudolphna on 2008-02-24
ok here we are.

root@nick-desktop:~/wireless_driver/ndis5# modprobe ndiswrapper
root@nick-desktop:~/wireless_driver/ndis5#

---

### Post by uberlube on 2008-02-24
And then:

ndiswrapper -m

---

### Post by rudolphna on 2008-02-24
ok.
root@nick-desktop:~/wireless_driver/ndis5# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
root@nick-desktop:~/wireless_driver/ndis5# 


(do you know of any system monitors (temp etc) for linux?)

---

### Post by uberlube on 2008-02-24
You are talking to the right man my friend, below is a pic of my desktop with a lightweight system monitor called 'conky' Ill help you get that set up after we finish with your wireless driver.

1) Ok so first things first; do you have a light that comes on for your wirless card and did it turn on?

2) type in: 'iwconfig wlan0' and show me the output

3) type in 'iwlist wlan0 scan' and again show the output

---

### Post by uberlube on 2008-02-24
Heres my desktop:

---

### Post by rudolphna on 2008-02-24
sorry about hat, it disconnected from the router.  yeah, it lights up woohoo!!

root@nick-desktop:~/wireless_driver/ndis5# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Stay out"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:97:56:FA   
          Bit Rate=108 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





root@nick-desktop:~/wireless_driver/ndis5# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:F6:E2:A2
                    ESSID:"Rudolph"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:14:6C:97:56:FA
                    ESSID:"Stay out"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@nick-desktop:~/wireless_driver/ndis5#

---

### Post by rudolphna on 2008-02-24
its wierd when i connect the wireless card, it disconnects from the wired network, but when i unplug it, it connects again.

---

### Post by uberlube on 2008-02-24
Right click on your network manager on the topright of the screen and see if it shows any networks.

---

### Post by rudolphna on 2008-02-24
yes it does

---

### Post by uberlube on 2008-02-24
If you havent actually logged into your network yet. Click on yours and if its WEP encrypted make sure you specify what type it is HEX1/2(64bit) or HEX(128bit) or whatever options it gives you. Im assuming that you already know what to do there.

---

### Post by rudolphna on 2008-02-24
OMG YES IT WORKS!!!!!!!  *hallelujia chorus*
THANK YOU SO MUCH!!!

Its connected to our neighbors wireless, because i dont know what the WPA password is on ours, i have to ask my mom to put it in when she wakes up.  should i know anything about how to put it in?

---

### Post by uberlube on 2008-02-24
There you go dude, your well on your way to being a Linux Guru:lolflag:

Also feel free to click the ribbon with the start to say 'thanks':)

So do you have any other questions before we get your system monitor to work?

---

### Post by rudolphna on 2008-02-24
of course, i was looking for that button. i always like when people press it on mine on the other site check out PCHF in my signature, im a tech there by the name of AW_3_3.  ok  now if your not leaving, lol lets move on to the next thing

---

### Post by uberlube on 2008-02-24
Right on I'll check out your other forum later on. So lets get you sert up with conky.

1) Im assuming your not running a dualcore correct?

2) Open up the synaptic package manager again and search for 'conky' and install.

---

### Post by rudolphna on 2008-02-24
technically no. But its a Hyperthreading CPU so the OS sees it as dual cores. Will this make a difference?

---

### Post by rudolphna on 2008-02-24
ok it installed, where is the program shortcut thing in the menu

---

### Post by uberlube on 2008-02-24
Well we will try out the single core methode first and if that doeasnt work ill use my dual core template. OK so while conky is installing, open up a basic text editor in your menu (or in terminal type in 'gedit').

---

### Post by rudolphna on 2008-02-24
ok its open, but the program was installed already

---

### Post by uberlube on 2008-02-24
K installed? Good to go then. Inside your text editor paste this script:

```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

# Update interval in seconds
update_interval 1.0

TEXT
${color blue}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

${color blue}CPU ${hr 1}${color}
${freq} MHz
Load: ${loadavg}   ${alignr}Temp: ${acpitemp}
$cpubar
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color blue}FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
Windows: ${alignr}${fs_used /media/sda3} / ${fs_size /media/sda3}
${fs_bar 4 /}


${color blue}NETWORK ${addr wlan0} ${hr 1}$color

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107 000000 ff0000} ${alignr}${upspeedgraph wlan0 25,107 000000 ff0000}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

```

Also tell me what your partitions look like

---

### Post by rudolphna on 2008-02-24
ok its pasted.  

uhhh... lets see....  (i had difficultry running the partitioner =P)

Harddrive> Western Digital Caviar SE 250GB SATA

Main Partition--- ~190GB NTFS (Windows Partition

Unix Partition--- ~40 GB  ex3 (Linux Ubuntu 7.04)

Swap Partition ~3.3 GB   swap  (Swap Space)

can i shrink the linux partition and add it back to the windows one? (want to get the linux one down to 25 GB)

---

### Post by uberlube on 2008-02-24
Ok your partitions look good for what I have scripted. As for resizing....DONT...this is dangerous territory and you will run a high risk of screwing both partitions. Especially if you havent defragmented your windows partition. Anyhoo, in the text editor go save as .conkyrc and save it to your /home folder. Once that is done press alt+F2 and type in 'conky -a top_right' and enter. Then take a snapshot (Prt Scr) of your desktop and send it to me. You can add it while writing a post by scrolling down near the bottom and go into 'manage attachments' upload it through there.

---

### Post by rudolphna on 2008-02-24
it shows up, but print screen just acts like a right click.  it shows what i need it to show, how do you turn it off?

---

### Post by rudolphna on 2008-02-24
ok now how do you play mp3s in ubuntu?

---

### Post by uberlube on 2008-02-24
if there is no way to exit the print screen press alt+f2 and type in 'xkill'. your mouse will turn into a skull and crossbones and you just click on the offending program. As far as itunes, yes, your in luck. There is a program called rythembox which is designed just for the ipod purpose. If its not preinstalled, get it from the add/remove software botton in your menu or from the synaptic. So do you have a pic of your desktop or no?

---

### Post by uberlube on 2008-02-24
And there are lots of other mp3 players for linux. I think youd like Exaile.

---

### Post by uberlube on 2008-02-24
I almost forgot, we have to activate all restricted media formats so you can watch DVD's and play all sorts of media files, like mp3s

sudo apt-get install ubuntu-restricted-extras

---

### Post by rudolphna on 2008-02-24
sorry about that. i had to move the computer from downstairs to back in my room.  ok so can rythmbox play AAC?

---

### Post by rudolphna on 2008-02-24
installing now, then on to the unlocking of formats

---

### Post by rudolphna on 2008-02-24
everything on my ipod is marked as unplayable o_0

---

### Post by uberlube on 2008-02-24
Thats actually a good question. It may not considering how new of a format it is, but hey if not theres always VLC right :lolflag:

So anyway heres a bunch of sites that I think you will find helpful:

1) Install Anything in Ubuntu
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
2) GetDeb (software for debian based linux, like Ubuntu)
[http://www.getdeb.net/](http://www.getdeb.net/)
3) Automatix (automatically install cool stuff like the ms-core-fonts)
[http://www.getautomatix.com/](http://www.getautomatix.com/)
4) Click n' Run (Same thing)
[http://www.cnr.com/](http://www.cnr.com/)
5) Softpedia
[http://www.softpedia.com/](http://www.softpedia.com/)
6) Sourceforge
[http://sourceforge.net/](http://sourceforge.net/)
7) Ideas for burning movies in linux
[http://ubuntuforums.org/showthread.php?t=383452](http://ubuntuforums.org/showthread.php?t=383452)
8) Linux Mint (my distrobution of choice. made from debian and ubuntu)
[http://www.linuxmint.com/](http://www.linuxmint.com/)
9) Lots and lots for conky mods
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

And thats all i can think of for now lol.

---

### Post by rudolphna on 2008-02-24
well its been a good session. lol  i finished all my initial goals.

a. get wireless network to work (currently running it  =D)
b. install graphics drivers
c. acheive 1280x 1024 resolution
d. find system monitoring program
e. play music files 

lol

---

### Post by rudolphna on 2008-02-24
uh, oops.  

root@nick-desktop:/home/nick# apt-get install ubuntu-restricted-extras
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@nick-desktop:/home/nick#


how do i fix this lol

---

### Post by uberlube on 2008-02-24
Ya I really need to get some sleep. If you need any more help dont hesitate to PM me. Later Dude):P

---

### Post by rudolphna on 2008-02-24
ok see ya later

---

