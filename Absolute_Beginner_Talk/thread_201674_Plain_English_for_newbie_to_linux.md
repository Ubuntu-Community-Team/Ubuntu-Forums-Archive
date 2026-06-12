---
title: "Plain English for newbie to linux"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by zorro26 on 2006-06-22
Finaly i manage to install ubuntu..... and thats its.... i want to learn linux and ubuntu step by step... and for my first step i want to learn how to set up my Speedtouch 330 modem, so when ever i need help i can search online.. i use my system (windows) to watch and download movies & music, play games and browse net. So that what i want to do with ubunto. Reading loads and loads of thread, that dosnt sound to hard..but am too stupid to understand (well am not)..;) i have tried this [COLOR="RoyalBlue"]http://www.linux-usb.org/SpeedTouch/ubuntu/index.html[/COLOR] [COLOR="Black"]but some of stuff doesnt make any sense to me like [/COLOR]**First, unzip the firmware and use the firmware-extractor to split it into two parts, speedtch-1.bin and speedtch-2.bin** or in one of the thread i found this
unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012
sudo cp speedtch* /lib/firmware/2.6.15-25-686
sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets 
sudo install -m 600 speedtch /etc/ppp/peers 
sudo install -m 744 dial /etc/init.d &&
sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
sudo ln -sf ppp/resolv.conf /etc/resolv.conf 

i am new to linux and have no exp of programing that dosnt make any sense to me.

so please lets start this in simple and plain english...
i have download SpeedTouch330_firmware_3012.zip and when i unzip it it just extracts one file "KQD6_3.012" extracting it againg it gave me "ZZZL_3.012". i tried some comands in terminal but all in vain they dont work and i dont know why cause i dont undestand all this. SO PLEASE HELP...

---

### Post by keith whitehouse on 2006-06-22
hi zorro26,

if you go to search, towards the top right hand corner of the screen and type in "speedtouch "you will find that this subject has been covered many times and I am sure that the answer you seek is there already.

I am newish to Linux, and the first thing that I did when I found this beginers page was to go back and read the last 100 pages. Anything that I thought would be helpful I saved to my computer, other bits and pieces I printed out and filed for future use.

I am not being critical, as I have had to use this forum myself and many times it has recued me from serious trouble, but it appears that everyone is trying hard to run before they can walk. Virtually everything that is seen as a problem has already been covered, it is just a matter of digging a bit. You can also use "Google" to search up problems.

best regards keith

---

### Post by mips on 2006-06-22
[http://www.ubuntuforums.org/showthread.php?t=128875](http://www.ubuntuforums.org/showthread.php?t=128875)
[http://www.ubuntuforums.org/showthread.php?t=44763](http://www.ubuntuforums.org/showthread.php?t=44763)
[http://ubuntuforums.org/showthread.php?t=190359](http://ubuntuforums.org/showthread.php?t=190359)
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

If you do a search for "Speedtouch" you will find lots of posts.

---

### Post by hotbrainz on 2006-06-22
Hello,
I agree absolutely with Keith. Anyway I did the search and got these links for you. 
[http://www.ubuntuforums.org/showthread.php?t=128875&highlight=speedtouch+modem]("http://www.ubuntuforums.org/showthread.php?t=128875&highlight=speedtouch+modem")

[http://www.ubuntuforums.org/showthread.php?t=186233&highlight=speedtouch+modem]("http://www.ubuntuforums.org/showthread.php?t=186233&highlight=speedtouch+modem")

Hope these help. If there are any specific queries then ask. People here have helped me a lot and thats the spirit of Ubuntu :)

Have some coffee

---

### Post by zorro26 on 2006-06-22
I dont know what i am doing wrong, i have already put those links in my previous msg. i have searched, saved and copied it on a cd so that i can check instructions while i am using ubuntu. as i explained earlier i dont get what the instructions tells me that i will . am sure its me not the links or instructions. i just want some simple and plain intrustions. i have decided that i will use ubuntu, i dont care how long it takes me to learn but i will, i am not giving up...so ill take hotbrainz idea, ill have some coffee at night and give it another go again, and let you guys know what happen.ohhhh i remeber am going out tonight, ill be too drunk to do this tonight, so ill try it tomorrow. i dont want to find a formatted pc when i get up next morning..;) lol. thanks for the replies....

---

### Post by Beej on 2006-06-22
zorro, i do not have your modem, so I can't help with instructions but I can help you understand a little the instructions given. 

these instructions have to be entered in the terminal. They are not "programming" as such as you said, but a non graphical method of communicating with your pc. 

Terminal can be found in Applications > Accessories > terminal

looks like the first thing you need to do is download a file called  SpeedTouch330_firmware_3012.zip. Down load this to your home directory.

Open a terminal window. The terminal automatically opens in your home folder. 

The commands should be copied a line at a time hitting return after each one is entered.

unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012

This is three seperate commands the double ampersand makes the commands run one after another. the first unzips the file SpeedTouch330_firmware_3012.zip which you down loaded to your home folder. The second changes the properties of the extracted file firmware-extractor so that it can be executed. the third step executes the file firmware-extractor

I'm unsure what the other comands do from here, but copying and pasting them should work. I would suggeest reading up on terminal commands elsewhere in the forums or the wiki to get a better understanding.

try 

[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by zorro26 on 2006-06-23
Thanks BEEJ, that realy make more sense and this is what i mean by plain english... i have tried that and it unziped both file but than it says to install **libatm1_2.4.1-17_i386.deb** in the insturtionsis this needs to be downloaded or is it in Synaptic manager, if it is where and how can i find it, thanks for everyones help again

---

### Post by Beej on 2006-06-23
I dont know if this in the repos or not. You could try searching in synaptic, 

system > administration > synaptic package manager

search for libatm using the search function and see if that or a newer version is available. If it is right click on the package and select install, then tick the big apply box at the top.

Synaptic is your freind!! If you need an application you can search and install it 90% of the time from here with little fuss.


If the file is not there you will need to find it on the interweb and download it to your home folder. Then type the following command in the terminal to install it

sudo dpkg -i libatm1_2.4.1-17_i386.deb

sudo is as explained before. dpkg means depakage and -i means install. So the comand says depakage and install libatm1_2.4.1-17_i386.deb.

.deb is the extension for debian packages, as far i as ican tell they are like zip files of programs, with instructioons as to where the files contained need to go etc to make them work, and instructions as to what other deb files are needed.

Hope this helps. Keep me updated as to how your getting on and I'll do what I can to help. Don't give up!! stick with ubuntu, it's worth it I  promise.

---

### Post by zorro26 on 2006-06-23
i searched every where its not in pakage manage or internet, its a pakage in 6-06 drapper version and i got 5.05 something which is breezy. infact i want to update it to draper cause most of the instruction i find are for draper. how can i update it to drapper, keep it mind that i dont have access to internet throught ubuntu, so i have to download it on windows. can i download draper and burn cd and boot my system from that cd, would it be a new instalation or would it just update breezy version. thanks

---

### Post by e_james on 2006-06-23
Just a word of caution. If you download 6.06 (Dapper Drake) for dual boot, get the Alternate CD. The Live / Install CD is likely to wipe existing partitions (including Windows).

---

### Post by zorro26 on 2006-06-23
so if i download drapper alternate CD, how can i go about updating ubuntu breezy?

---

### Post by Beej on 2006-06-23
without internet i don't know how to do this.

I have found a debian deb which may do the trick, although I can't promise it will work. get it here - 

[http://ftp.sk.debian.org/debian/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb](http://ftp.sk.debian.org/debian/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb)

tr if you manage to get on line I'll talk you through the upgrade to dapper which is relatively simple when online, unless anyone knows how to do this offline from a cd for example?

---

### Post by zorro26 on 2006-06-23
does that mean if i download alternate CD i can just update breezy version rather than a new instalation

---

### Post by zorro26 on 2006-06-23
thanks beej, ill try to connect through ubuntu this time,fingers cross ...

---

### Post by zorro26 on 2006-06-23
[QUOTE=zorro26]thanks beej, ill try to connect through ubuntu this time,fingers cross ...[/QUOTE]
following are the instruction i am following:

 [COLOR="Red"][B]SpeedTouch USB ADSL Modem HowTo for Ubuntu 5.10 Breezy Badger (UK) 

--------------------------------------------------------------------

Requirements for the U.K. only!

NOTE: 

Print a copy of this HowTo or have it visible on another machine that doesn't require an internet connection. Else save it and transfer it onto your ubuntu machine.

If you're a newbie, it would also be a good idea to print a copy of basic questions and commands (if you don't have a book) that will speed up your development. These are general to most linux distro's (distributions) and are available from - Download: [http://www.linuxhelp.net/newbies/newbies-print.php](http://www.linuxhelp.net/newbies/newbies-print.php)

0 - SpeedTouch ADSL version 4 modem (Thomson / Alcatel)

1 - libatm1_2.4.1-17_i386.deb 

('libatm' is already packaged with Breezy Badger but you should re-install it to prevent any further frustrations. Newer versions will possibly supercede this, but this works) Download: [http://packages.ubuntu.com/hoary/libs/libatm1](http://packages.ubuntu.com/hoary/libs/libatm1)

2 - speedtouch-firmware_0.3012k_all.deb 

(Modem firmware that ensures your modem runs everytime you plug it in, switch your computer on or click to browse the internet.) Download: [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb)

3 - speedtch.txt

(This script is necessary for hotplugging the modem ie: connecting / disconnecting when the usb plug to the modem is inserted / pulled out of the usb port [PlugandPlay]. Many thanks to Darrell - ubuntu forum member)


Copy and save in Notepad everything between the lines as "speedtch.txt"

-------------------------------------------------------------------------------------

#!/bin/sh



# Script based on /etc/hotplug/usb/speedtouch from the speedtouch debian package.

# This package is not required with kernel 2.6.10, but without this little bit 

# of its functionality, we would lose automatic connection on hotplugging the 

# speedtouch modem (and immediate killing of the pppd on disconnection). 


PATH=/sbin:/bin:/usr/sbin:/usr/bin

export PATH



# ignore device events

#[ "$PRODUCT" ] || exit 0



# a PPP peer to call

PPPD_PEER="adslscript" # the name of a connection script in /etc/ppp/peers



# start the pppd process

pppd call $PPPD_PEER




#This will make sure that the pppd process is killed immediately if the  

# modem is unplugged, thereby making everything ready for immediate reconnection

[ "$REMOVER" ] || exit 0

  {
  echo "#!/bin/sh"

  [ "$PPPD_PEER" ] && printf "poff $PPPD_PEER\nsleep 5\n"

  } >> $REMOVER

  chmod +x $REMOVER

exit 0



-------------------------------------------------------------------------------------


MAKE SURE YOU HAVE EVERYTHING PRINTED OR SAVED IN YOUR HOME DIRECTORY IN UBUNTU THAT YOU REQUIRE! IT IS SOMETIMES BETTER IF YOU HAVE THE HOWTO LOADED ON THE SAME SYSTEM SO YOU CAN JUST COPY AND PAST.

FINALLY MAKE SURE YOU HAVE AN INTERNET CONNECTION BUT DON'T PLUG YOUR USB MODEM IN JUST YET. YOU WILL BE PROMPTED TO DO THIS LATER.

Assuming you're already in Ubuntu - OPEN A TERMINAL (Application -> Accessories -> Terminal)

STEP 1: install the package 'libatm1_2.4.1-17_i386.deb'

CODE TO TYPE: 
sudo su <ENTER> (this will require your root password and give you something like this 'root@your username:/home/yourusername#')
dpkg -i libatm1_2.4.1-17_i386.deb <ENTER>

Step 2: install the modem firmware package 'speedtouch-firmware_0.3012k_all.deb'

CODE TO TYPE:
dpkg -i speedtouch-firmware_0.3012k_all.deb <ENTER> (you must still be in root - This will install the firmware files to your computer.)

Step 3: configure the software

You are now going to load the pppoatm module, and set up your machine so the pppoatm module is loaded at every boot - before you do this type 'exit' to get out of root ie: root@your username:/home/yourusername# exit <ENTER>
This will leave you with: your username@your username:~$

CODE TO TYPE:
sudo modprobe pppoatm <ENTER> (note: whenever you're not in root and you type 'sudo' at the start of a command, you will be prompted for your root password)
sudo gedit /etc/modules <ENTER> (this will open up gedit word editor - in the editor window, add the word - pppoatm - at the bottom of the list, save and exit.

Now we're going to create a pppd connection script to control logging on to your ISP:

CODE TO TYPE:
sudo cp /usr/share/doc/ppp/examples/peers-pppoe /etc/ppp/peers/adslscript <ENTER>
sudo gedit /etc/ppp/peers/adslscript <ENTER> (this will open up gedit word editor - in the editor window, change the line - 
# user "myusername@myprovider.com"

to

user "your-own-isp-username"

below this you are going to replace a few lines (remember to include the blank line, up to eth0), which are:

# Load the pppoe plugin. 
plugin rp-pppoe.so

.........ethernet interface...........
eth0

and replace with

CODE TO TYPE:
# These options configure pppd to talk with the kernelspace speedtch driver.
# Don't forget to adapt the VP.VC pair to your ISP/country settings.
# (see [http://www.linux-usb.org/SpeedTouch/faq/index.html#q12](http://www.linux-usb.org/SpeedTouch/faq/index.html#q12))
plugin pppoatm.so
0.38 #UK

After this you should have the following:

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

If you have the above, then there's nothing else to do here except save and exit the editor.

But, if you have the following towards the bottom, comment out (ie put a # at the beginning of the line):

noaccomp

and

default-asyncmap

After you have commented out the above lines, save and exit the editor.

Now you are going to set up your isp password:

CODE TO TYPE:
sudo gedit /etc/ppp/chap-secrets <ENTER> (In the editor window, add the following line)

your-isp-username * your-isp-password * (Note: there is a space between username, *, password and *)

Save file and close the editor.

CODE TO TYPE:
sudo gedit /etc/ppp/pap-secrets <ENTER> (In the editor window, add the identical line to that just added to the chap secrets file. Don't forget the spaces.)

Save file and close the editor. (Only one of these two files that you have just edited will be used by your ISP to connect, it just depends on the authentication method used by your ISP.)

Finally, setup the hotplug system to automatically connect when the modem is plugged in and at boot time:

CODE TO TYPE:
sudo cp /your/path/to/speedtch.txt /etc/hotplug/usb/speedtch <ENTER> (/your/path/to must be replaced with the location of the speedtch.txt file)

Now we are going to turn this script into an executable file 

CODE TO TYPE:
sudo chmod +x /etc/hotplug/usb/speedtch <ENTER>

CODE TO TYPE:
tail -f /var/log/messages <ENTER> (NOW IS THE TIME TO: Plug in your modem and watch it connect. You should see in the messages displayed with a month, date, time and localhost format with the more important stuff at the end, which will read something like this: 

usbcore: registered new driver speedtch
speedtch: loaded successfully
Plugin pppoatm.so loaded
pppd 2.4.3 started...
found stage 2 firmware...
Exit
Exit
Using interface ppp0
Connect: ppp0 <--> 0.38
ADSL line is synchronising
CHAP authentication succeeded
PPP...registered
PPP...registered
local IP address ......
remote IP address ......
primary DNS address ........
secondary DNS address .......
ADSL line is up (2272 Kib/s down ¦ 288 Kib/s up)

CODE TO TYPE:
ctrl-c (to get out of the scrolling messages display).

You should now be connected to the internet.

NOTE: In other countries using PPPoA should work by changing the VPI/VCI numbers. To check what your VPI/VCI numbers are look at [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html).[/B][/COLOR]

everythin goes ok except following two things, 
[COLOR="Purple"]1)[/COLOR] when i try to install speedtouch-firmware, i get following msg:
[COLOR="Blue"]khalid@ubuntu:~$ sudo su
root@ubuntu:/home/khalid# dpkg -i speedtouch-firmware_0.3012k_all.deb
dpkg: error processing speedtouch-firmware_0.3012k_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 speedtouch-firmware_0.3012k_all.deb
root@ubuntu:/home/khalid#[/COLOR]

[COLOR="Black"]just to let you know that i already have KQD6_3.012 & ZZZL_3.012 in my home folder..[/COLOR]

[COLOR="purple"]2)[/COLOR][COLOR="black"]and after all the steps i get following msg:[/COLOR]

[COLOR="RoyalBlue"]khalid@ubuntu:~$ tail -f /var/log/messages
Jun 23 20:08:43 localhost gconfd (root-8617): Resolved address "xml:readonly:/us r/share/gconf/local.defaults" to a read-only configuration source at position 4
Jun 23 20:08:43 localhost gconfd (root-8617): Resolved address "xml:readonly:/us r/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jun 23 20:08:43 localhost gconfd (root-8617): Resolved address "xml:readonly:/us r/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jun 23 20:08:43 localhost gconfd (root-8617): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 7
Jun 23 20:11:13 localhost gconfd (root-8617): GConf server is not in use, shutti ng down.
Jun 23 20:11:13 localhost gconfd (root-8617): Exiting
Jun 23 20:16:27 localhost kernel: [4296363.367000] usb 3-2: new full speed USB d evice using ohci_hcd and address 2
Jun 23 20:16:27 localhost usb.agent[8880]:      speedtch: already loaded
Jun 23 20:16:28 localhost usb.agent[8922]:      speedtch: already loaded
Jun 23 20:16:28 localhost usb.agent[8931]:      speedtch: already loaded
Jun 23 20:19:56 localhost kernel: [4296364.141000] usb 3-2: no stage 1 firmware found!UDF-fs: No VRS found[/COLOR]

[COLOR="Black"]at this point i have to mention that both green lights on when i turn my pc on through ubuntu and after following all the above steps the lights are on again as soon as i plug the modem through usb, but its not connected as i cant browse. sorry if this is too much details, but i want to learn more and more.... thanks to beej i understand comands and terminal relationship now.... what should i do now?[/COLOR]

---

### Post by bruce89 on 2006-06-23
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) got this working for me when I used this exact modem.

---

### Post by zorro26 on 2006-06-23
thanks bruce89, i have already been given that link... but itss too hard for me to follow for example [COLOR="YellowGreen"]You'll need to prepare the firmware with a copy of the firmware extractor. You can get a precompiled binary or you can get the source and compile it yourself (but you'll need to install gcc for that). [/COLOR] mmmmmmmm makes no real sense to me.

and where it says after extracting the files i should have a speedtch-1.bin and speedtch-2.bin in my home folder, i dont get that.... so i am realy stuck at the first step, cant go any further...

---

### Post by Beej on 2006-06-23
Zorro, 
      If bruce has had success you may want to follow his instructions.

    with regards to this,
"You'll need to prepare the firmware with a copy of the firmware extractor. You can get a precompiled binary or you can get the source and compile it yourself (but you'll need to install gcc for that)"

allthat this means is to download this file

[http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor) 

to your home folder. Then you need to do the following. go to your home folder and check that the file is actually called 

"firmware-extractor"

If not rename it so it is, for example I had ago at downloading it and it became "firmware-extractor.html"

then follow the instructions. Make sure you follow the** pre** dapper instructions and the correct ones for your firmware.

---

### Post by Jagot on 2006-06-23
[QUOTE=e_james]Just a word of caution. If you download 6.06 (Dapper Drake) for dual boot, get the Alternate CD. The Live / Install CD is likely to wipe existing partitions (including Windows).[/QUOTE]

Sorry, know it's not relevant to the main question in the thread but I thought i'd just point out that this is incorrect for any other people reading his.  Live/Desktop CD sets up dual boot with Windows fine providing, as with the Alternate Install CD, that you pay attention at the partitioning stage.

---

### Post by zorro26 on 2006-06-23
i worked on it all day but no luck, am still not givin up..... i want it more and more now.... how sad is that lol...

i followed all the instructions three times now, still not working.. there are two things i want to mention :
first ::: where it says [COLOR="Red"]"If that went OK you should now have a speedtch-1.bin and speedtch-2.bin in your home folder. Ubuntu used to keep firmware in /lib/hotplug/firmware but with Dapper Drake Ubuntu has moved into line with everyone else and now stores firmware in /lib/firmware. So, if you're using an older (pre Dapper) version use these commands"[/COLOR]
[COLOR="Black"]i dont get speedtch-1.bin and speedtch-2.bin in my home folder, 
but yea i have used pre dapper commands.[/COLOR]

secoundly ::: right at the end its says "[COLOR="red"]If not, is the firmware is loading OK? Once the kernel has loaded the speedtch module the left LED should stay green while the right LED flashes eight or nine times (and then stays green).

If the firmware loads but ppp can't connect with your ISP check the details you put in /etc/ppp/*-secrets and /etc/ppp/peers/speedtch. Also try adding the option 'debug' to /etc/ppp/peers/speedtch"[/COLOR]

[COLOR="black"]my modems both green light turns on sametime and stay still after reboot. and how can i check if my firmware loading ok..... is that when ubuntu in loading???[/COLOR]

sorry to be pain in the back side guys.... but i have one more question... when i read a README file in firmware-extractor its says [COLOR="Red"]"If you have a revision 0 or revision 2 SpeedTouch copy the KQD6_3.012 file into this folder and rename it mgmt.o, if you have a revision four modem, use the ZZZL_3.012 file 
instead."[/COLOR] 
[COLOR="Black"]now mine revision 4 does that means i have to rename ZZZL_3.012 to mgmt.o or is it just for KQD6_3.012, and which folder is it asking to copy it in is it firmware-extractor folder or ????[/COLOR]


thanks again guys

---

### Post by zorro26 on 2006-06-24
anyone online to reply to my question, i am up early.... and want to give it a go again???

---

### Post by richbarna on 2006-06-24
Hi zorro26,

Wow, lots of fun with the USB modem, no?

A few years back I had the same problems that you are having now. One of my friends said "USB modems suck, get a cheap router".

I followed his advice, I checked which router my ISP normally supplies, and I bought a second-hand one for &#8364;30. I downloaded their "install router software" from their web site and set it up from Windows Xp. 

I don't use Windows anymore now, but I can run ANY linux Distro through my router without having to ever configure anything.

I don't know if you have enough money to buy a cheap router, and I know that people have actually got a USB modem to work, but this option saved me a whole lot of hassle.

Sorry I can't help with your modem, I just thought I would give you an alternative.

By the way, your mentality is great !!, keep reading, keep trying, and if all else
fails come to this forum and we will all try to help :)

---

### Post by Apple 101 on 2006-06-24
Good idea richbarna.  I was going to suggest that too.

zorro26:  Do you have to connect via USB?  Does the modem come with a LAN port?

---

### Post by richbarna on 2006-06-24
[QUOTE=Apple 101]Good idea richbarna.  I was going to suggest that too.

zorro26:  Do you have to connect via USB?  Does the modem come with a LAN port?[/QUOTE]

Hey apple 101

I see you haven't got anything in your signature space, why no chuck in a few links ?
They are great for the new users :)
|
|
v

---

### Post by Apple 101 on 2006-06-24
[QUOTE=richbarna]Hey apple 101

I see you haven't got anything in your signature space, why no chuck in a few links ?
They are great for the new users :)
|
|
v[/QUOTE]
I don't understand what you mean richbarna (sorry).

zorro26:  Is the USB modem detected?

---

### Post by zorro26 on 2006-06-24
i am no expert, i dont know what you mean by does a usb modem comes with lan port.... all i know its speedtouch 330 usb modem....
thanks for the advice richbarna but i think i need to learn bit more before i start using router, but yea i have been consedering that option.. thanks

but at the moment am still stuck with usb modem which i cant install... any one who can help ... please read my previous posts... thanks

---

### Post by sam hassell on 2006-06-24
zorro, i can't really help you. I just wanted to say "stick at it", it took me a half dozen installs before I worked out what I was doing. Now I have a system that works beautifully.

edit: what he means by LAN port is, is there a connection on the back of the modem that you can connect a network cable to. I don't think there would be.

I tried a long time to get a PCI card modem working with linux, and in the end I just got a dsl router - it was automatically detected and I have not had to deal with the problem since.

So keep trying, and maybe you can help me in the future :)

---

### Post by zorro26 on 2006-06-24
anyone here to help me with my previous post....

i worked on it all day but no luck, am still not givin up..... i want it more and more now.... how sad is that lol...

i followed all the instructions three times now, still not working.. there are two things i want to mention :
first ::: where it says "If that went OK you should now have a speedtch-1.bin and speedtch-2.bin in your home folder. Ubuntu used to keep firmware in /lib/hotplug/firmware but with Dapper Drake Ubuntu has moved into line with everyone else and now stores firmware in /lib/firmware. So, if you're using an older (pre Dapper) version use these commands"
i dont get speedtch-1.bin and speedtch-2.bin in my home folder, 
but yea i have used pre dapper commands.

secoundly ::: right at the end its says "If not, is the firmware is loading OK? Once the kernel has loaded the speedtch module the left LED should stay green while the right LED flashes eight or nine times (and then stays green).

If the firmware loads but ppp can't connect with your ISP check the details you put in /etc/ppp/*-secrets and /etc/ppp/peers/speedtch. Also try adding the option 'debug' to /etc/ppp/peers/speedtch"

my modems both green light turns on sametime and stay still after reboot. and how can i check if my firmware loading ok..... is that when ubuntu in loading???

sorry to be pain in the back side guys.... but i have one more question... when i read a README file in firmware-extractor its says "If you have a revision 0 or revision 2 SpeedTouch copy the KQD6_3.012 file into this folder and rename it mgmt.o, if you have a revision four modem, use the ZZZL_3.012 file 
instead." 
now mine revision 4 does that means i have to rename ZZZL_3.012 to mgmt.o or is it just for KQD6_3.012, and which folder is it asking to copy it in is it firmware-extractor folder or ????

---

### Post by richbarna on 2006-06-24
[QUOTE=Apple 101]I don't understand what you mean richbarna (sorry).

zorro26:  Is the USB modem detected?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=200626]("http://www.ubuntuforums.org/showthread.php?t=200626")

---

### Post by richbarna on 2006-06-24
[QUOTE=zorro26]

sorry to be pain in the back side guys.... but i have one more question... when i read a README file in firmware-extractor its says "If you have a revision 0 or revision 2 SpeedTouch copy the KQD6_3.012 file into this folder and rename it mgmt.o, if you have a revision four modem, use the ZZZL_3.012 file 
instead." 
now mine revision 4 does that means i have to rename ZZZL_3.012 to mgmt.o or is it just for KQD6_3.012, and which folder is it asking to copy it in is it firmware-extractor folder or ????[/QUOTE]

Revision 4 is the ZZZL_3.012. change it to mgmt.o

---

### Post by zorro26 on 2006-06-24
thanks richbarna, but i still want to know 
1)what should i do after i change it to mgmt.o, which folder is it going in?
2) why am not getting speedtch-1.bin and speedtch-2.bin in my home folder after i install speedtouch firmware?
3) on the instruction page it says right at the end that "[COLOR="Red"]If the firmware is loading OK.. Once the kernel has loaded the speedtch module the left LED should stay green while the right LED flashes eight or nine times (and then stays green)".[/COLOR] my modems both green light turns on sametime and stay still after reboot. and how can i check if my firmware loading ok..... is that when ubuntu in loading???
if i am not making sense please refer to my previous posts.... i need help.. i have waited all today, i havnt tried anything today ... and i wanted it to be working today....

---

### Post by richbarna on 2006-06-24
Ok, you have got ALL of these in your "home" folder ?:-

> 0 - SpeedTouch ADSL version 4 modem (Thomson / Alcatel)

1 - libatm1_2.4.1-17_i386.deb

('libatm' is already packaged with Breezy Badger but you should re-install it to prevent any further frustrations. Newer versions will possibly supercede this, but this works) Download: [http://packages.ubuntu.com/hoary/libs/libatm1](http://packages.ubuntu.com/hoary/libs/libatm1)

2 - speedtouch-firmware_0.3012k_all.deb

(Modem firmware that ensures your modem runs everytime you plug it in, switch your computer on or click to browse the internet.) Download: [http://ftp.linux.it/pub/People/md/wa....3012k_all.deb](http://ftp.linux.it/pub/People/md/wa....3012k_all.deb)

3 - speedtch.txt

(This script is necessary for hotplugging the modem ie: connecting / disconnecting when the usb plug to the modem is inserted / pulled out of the usb port [PlugandPlay]. Many thanks to Darrell - ubuntu forum member)


Copy and save in Notepad everything between the lines as "speedtch.txt"

And you didn't plug in the modem until you were TOLD to ?

2. why am i not getting the firmware bins 1 and 2 in the home folder ?
Open your terminal and type this :-
> unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012
And post exactly what happens.

Also go to the "/lib/hotplug/firmware" folder and see if you have the two files there. If you have, copy and paste them into the "home" folder.

---

### Post by zorro26 on 2006-06-24
yes i have checked averything...this is what u get:

[COLOR="Blue"]khalid@ubuntu:~$ unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012
  inflating: ZZZL_3.012
chmod: cannot access `firmware-extractor': No such file or directory
khalid@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/khalid# unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012
Archive:  SpeedTouch330_firmware_3012.zip
replace KQD6_3.012? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: KQD6_3.012
replace ZZZL_3.012? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: ZZZL_3.012
chmod: cannot access `firmware-extractor': No such file or directory

root@ubuntu:/home/khalid# unzip SpeedTouch330_firmware_3012.zip && chmod +x /home/khalid/firmware-extractor.tar.gz && /home/khalid/firmware-extractor.tar.gz ZZZL_3.012
Archive:  SpeedTouch330_firmware_3012.zip
replace KQD6_3.012? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: KQD6_3.012
replace ZZZL_3.012? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: ZZZL_3.012
bash: /home/khalid/firmware-extractor.tar.gz: cannot execute binary file[/COLOR]

i have checked /lib/hotplug/firmware there no firmware bins 1 and 2 in that folder..
i am trying to attach screen shot of my home folder, donw know if it works,,,,,help anyone

---

### Post by zorro26 on 2006-06-25
hi richbarna, have you checked my previos post... please tell me what i am doing wrong?

---

### Post by richbarna on 2006-06-25
[QUOTE=zorro26]hi richbarna, have you checked my previos post... please tell me what i am doing wrong?[/QUOTE]

I think it's this line :-

unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012

Theres no .tar.gz AFTER firmware extractor eg :-

unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor.tar.gz && ./firmware-extractor ZZZL_3.012

you can also do them one by one and then continue with the other instructions, eg

unzip SpeedTouch330_firmware_3012.zip

chmod +x firmware-extractor.tar.gz

./firmware-extractor ZZZL_3.012

---

### Post by zorro26 on 2006-06-25
i did exactly "unzip SpeedTouch330_firmware_3012.zip && chmod +x firmware-extractor && ./firmware-extractor ZZZL_3.012" but it gave me a msg that cant find firmware-extractor, that when i tried ti move the file in terminal... if you look at the terminal report that i put in blue in my previous post right at at top you will notice i have put exact commands

---

### Post by keith whitehouse on 2006-06-25
hi zorro26

go to this site

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

I do not understand why you are unable to get a speedtch-1.bin and a speedtch-2.bin  into your home folder. I have just downloaded a file from the link on the page "this zip file", I then downloaded the "precompiled binary" and the "br2684ctl". Make sure that ALL of these 3 files are in your home page, and make sure that they are all named correctly, and then reboot.

Open "terminal" and copy and paste the lines

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012

and press return

In your home folder you will now have speedtch-1.bin and speedtch-2.bin

I have just done this to confirm that it works and it does


best regards keith

---

### Post by richbarna on 2006-06-25
I got the same thing :confused:
[ATTACH]11732[/ATTACH]

When asked to replace the different files, I tried Yes, No, All etc. "no go"
It couldn't find ./firmware- extractor, so I created a file in the root folder and the home folder, "no go"
No matter what I did, there are no .bin files (1 or 2) to be seen.

Sorry Zorro26, I don't know what to suggest.

---

### Post by richbarna on 2006-06-25
[QUOTE=keith whitehouse]hi zorro26

go to this site

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

I do not understand why you are unable to get a speedtch-1.bin and a speedtch-2.bin  into your home folder. I have just downloaded a file from the link on the page "this zip file", I then downloaded the "precompiled binary" and the "br2684ctl". Make sure that ALL of these 3 files are in your home page, and make sure that they are all named correctly, and then reboot.

Open "terminal" and copy and paste the lines

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012

and press return

In your home folder you will now have speedtch-1.bin and speedtch-2.bin

I have just done this to confirm that it works and it does


best regards keith[/QUOTE]


Hi Keith,
I'm not sure what's going on here?
I did the same as you, and I got the same result as Zorro26 :confused: 

Can you think of anything different on your setup ?
Are you running as root ?
KDE or GNOME ?
Anything that might help, I just want to try and help Zorro26.
I use a router myself, no drivers no firmware and no hassle :rolleyes:

---

### Post by stephen_lau on 2006-06-25
[QUOTE=richbarna]
It couldn't find ./firmware- extractor
[/QUOTE]

To Zorro26 and richbarna:
You've downloaded the **tar.gz (source code)** for the firmware-extractor. **You need the precompiled binary - [http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor))**. Place that in the same directory as where you downloaded the firmware ZIP file (in my screenshot below, I've put both firmware-extractor and SpeedTouch330_firmware_3012.zip in /home/steve/speedtouch):

[IMG]http://members.optusnet.com.au/stephen_lau/images/speedtouch.jpg[/IMG]

For convenience's sake, let's put those two files in your **home directory**
After putting both the firmware-extractor and ZIP file in the same directory, open up console, and type:
```
ls
```
This lists all the (non-hidden) files in the current directory. You should see 
**firmware-extractor** and **SpeedTouch330_firmware_3012.zip** there (like my screenshot).

Now using your mouse, highlight the following code:
```
unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012
```
Go back to console, and click the MIDDLE mouse button. This is a fast way to copy and paste text. Press enter, and you should see output similar to mine.

Type
```
ls
```
and you should see the extracted files (including speedtch-1.bin and speedtch-2.bin there) :-D

(also, don't miss the other file - [http://www.linux-usb.org/SpeedTouch/mandrake/br2684ctl](http://www.linux-usb.org/SpeedTouch/mandrake/br2684ctl) - you need it if your ISP uses PPPoE)
It's great to see you having such enthusiasm and perserverence Zorro26! Keep it up!


edit: 
I think it's good that I should explain some of the commands used here for Zorro26:

[LIST]
[*]The use of ```
unzip
``` should be pretty straightforward - you use it to unzip ZIP files (other compressed files like TAR and RAR uses other programs).
[*]The ```
&&
``` is used so you can link separate commands together without waiting for the first command to finish. Using &&, the second command is initiated if and only if the first command is finished without any errors.
[*]```
chmod +x
``` means you want to change the file permission such that it can be executed (hence, the +x). 
[*]In ```
./firmware-extractor
```, since firmware-extractor is a binary file (ie. it's compiled from code already into something that is run-able), the command ./ is basically executing/running the binary file.
[/LIST]

Long post, but hope this helps you in your journey into Ubuntu :-)

---

### Post by zorro26 on 2006-06-25
ok heres my screenshot.... home screen shot is for my home folder and terminal is for terminal.... just check all the comands and results i have been trying in terminal... and let me know  what i am doing wrong... thankyou

---

### Post by zorro26 on 2006-06-25
sorry missed attachments

---

### Post by mips on 2006-06-25
zorro26,

You are using the wrong file !

You need these two files:
[http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip](http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip)
[http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor)

You already have the first one but not the second one seeing you downloaded the source code. Delete the firmware-extractor.tar.gz file as you don't need it.

I just tried the above and it works fine:
```

reon@obelix:~/tmp$ ls
firmware-extractor  SpeedTouch330_firmware_3012.zip
reon@obelix:~/tmp$ unzip SpeedTouch330_firmware_3012.zip
Archive:  SpeedTouch330_firmware_3012.zip
  inflating: KQD6_3.012
  inflating: ZZZL_3.012
reon@obelix:~/tmp$ ls
firmware-extractor  SpeedTouch330_firmware_3012.zip  ZZZL_3.012
KQD6_3.012          swiftfox
reon@obelix:~/tmp$ ls -l
total 2276
-rw-------  1 reon reon  11901 2006-06-25 17:09 firmware-extractor
-rw-rw-rw-  1 reon reon 763677 2004-03-05 12:03 KQD6_3.012
-rw-------  1 reon reon 769125 2006-06-25 17:09 SpeedTouch330_firmware_3012.zip
-rw-rw-rw-  1 reon reon 776512 2004-03-05 12:03 ZZZL_3.012
reon@obelix:~/tmp$ chmod +x firmware-extractor
reon@obelix:~/tmp$ ./firmware-extractor KQD6_3.012
** Boot block from KQD6_3.012:
   CRC: 0xd80bf9f7
   Length: 991
** Firmware block from KQD6_3.012:
   CRC: 0x78039fed
   Length: 762650
reon@obelix:~/tmp$ ./firmware-extractor ZZZL_3.012
** Boot block from ZZZL_3.012:
   CRC: 0x69636579
   Length: 935
** Firmware block from ZZZL_3.012:
   CRC: 0x41d4143c
   Length: 775545
reon@obelix:~/tmp$
```

---

### Post by stephen_lau on 2006-06-25
Yes I did highlight you needed the binary file, not the tar.gz file in **bold** in my post =/

[QUOTE=zorro26]sorry missed attachments[/QUOTE]
Use the edit button at the bottom of the post next time so you don't have to create a new post

---

### Post by zorro26 on 2006-06-25
thanks mips and stephen, but when i click the secound link "http://www.linux-usb.org/SpeedTouch/...ware-extractor" its opens a txt file with some wierd stuff in it... and when i try to download it just downloads tar.gz file??? what should i do

---

### Post by keith whitehouse on 2006-06-25
hi zorro26,

I have just clicked on the second link in mips post and it downloads the "Firmware-Extractor" to my desktop. The file is type executable and has a size of 11.6 kb.

best regards keith

---

### Post by keith whitehouse on 2006-06-25
hi zorro26

it was only after I sent the message that it dawned on me what you could possibly be  doing.

When you click on the second link in mips reply you immediatly get a dialogue box pop up in the middle of your screen. It has 2 options, open with archive manager and save. You must save it to where all your other speedtouch files are. If you elect to open it with archive manager you may well think that you are seeing a .txt file.

best regards keith

---

### Post by zorro26 on 2006-06-25
right i tried something different this time...

[COLOR="DarkSlateBlue"]khalid@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/khalid# dpkg -i libatm1_2.4.1-17_i386.deb
(Reading database ... 56925 files and directories currently installed.)
Preparing to replace libatm1 2.4.1-17 (using libatm1_2.4.1-17_i386.deb) ...
Unpacking replacement libatm1 ...
Setting up libatm1 (2.4.1-17) ...

root@ubuntu:/home/khalid# pkg -i speedtouch-firmware_0.3012k_all.deb
bash: pkg: command not found
root@ubuntu:/home/khalid# dpkg -i speedtouch-firmware_0.3012k_all.deb
dpkg: error processing speedtouch-firmware_0.3012k_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 speedtouch-firmware_0.3012k_all.deb
root@ubuntu:/home/khalid# exit
exit
khalid@ubuntu:~$ sudo modprobe pppoatm
khalid@ubuntu:~$ sudo gedit /etc/modules
khalid@ubuntu:~$ sudo cp /usr/share/doc/ppp/examples/peers-pppoe /etc/ppp/peers/ adslscript
khalid@ubuntu:~$ sudo gedit /etc/ppp/peers/adslscript
khalid@ubuntu:~$ sudo gedit /etc/ppp/peers/adslscript
khalid@ubuntu:~$ sudo gedit /etc/ppp/chap-secrets
khalid@ubuntu:~$ sudo gedit /etc/ppp/pap-secrets
khalid@ubuntu:~$ udo cp /your/path/to/speedtch.txt /etc/hotplug/usb/speedtch
bash: udo: command not found
khalid@ubuntu:~$ sudo cp /home/khalid/speedtch.txt /etc/hotplug/usb/speedtch
khalid@ubuntu:~$ sudo chmod +x /etc/hotplug/usb/speedtch
khalid@ubuntu:~$ tail -f /var/log/messages
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/us r/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readwrite:/r oot/.gconf" to a writable configuration source at position 2
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/us r/share/gconf/local.defaults" to a read-only configuration source at position 4
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/us r/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/us r/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jun 25 21:15:34 localhost gconfd (root-9715): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 7
Jun 25 21:17:04 localhost gconfd (root-9715): GConf server is not in use, shutti ng down.
Jun 25 21:17:04 localhost gconfd (root-9715): Exiting
Jun 25 21:18:58 localhost kernel: [4296186.793000] usb 3-2: new full speed USB d evice using ohci_hcd and address 3
Jun 25 21:18:58 localhost usb.agent[9836]:      speedtch: already loaded
Jun 25 21:18:59 localhost usb.agent[9878]:      speedtch: already loaded
Jun 25 21:18:59 localhost usb.agent[9914]:      speedtch: already loaded
Jun 25 21:18:59 localhost kernel: [4296187.608000] usb 3-2: found stage 1 firmwa re speedtch-1.bin
Jun 25 21:18:59 localhost kernel: [4296187.785000] usb 3-2: found stage 2 firmwa re speedtch-2.bin
Jun 25 21:19:04 localhost kernel: [4296192.659000] ADSL line is synchronising
Jun 25 21:19:19 localhost kernel: [4296207.659000] ADSL line is up (1152 Kib/s d own | 288 Kib/s up)
Jun 25 21:19:43 localhost gconfd (root-10153): starting (version 2.12.0), pid 10 153 user 'root'
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/e tc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/u sr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readwrite:/ root/.gconf" to a writable configuration source at position 2
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/e tc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/u sr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/u sr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/u sr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jun 25 21:19:43 localhost gconfd (root-10153): Resolved address "xml:readonly:/v ar/lib/gconf/defaults" to a read-only configuration source at position 7
Jun 25 21:22:43 localhost gconfd (root-10153): GConf server is not in use, shutting down.
Jun 25 21:22:43 localhost gconfd (root-10153): Exiting[/COLOR]

and yes its working now............. woooooohoooooooooo.....

---

### Post by richbarna on 2006-06-25
Well Done !!! :)

---

### Post by Beej on 2006-06-26
I didn't dissapear, I have been keeping an eye on this thread, it makes me feel warm inside when the community helps itself out like this...

A true baptism of fire for zorro26 too. Welcome dude!

---

### Post by zorro26 on 2006-06-28
thanks for eveyone help, but guess what.........:(
i found the command to update ubuntu, which i did but when i reboot... it wasnt working. just gave me option for ubuntu mmm68 something... any way i download new ubuntu 6.06 version(draper one). but its said amd64 and that my processor so i download it. but after installing i relized that it never picked up my ATI video card, any way i tried to install my modem... and tried same things what i did before.. and formatted my pc after failing... m very upste. can anyone tell me what ubuntu version should i download for my AMD64 3700mhz. thanks

---

### Post by loserboy on 2006-06-28
I am using the 64 version of dapper on my amd64 3700+ and everything has been great.  but i have seen lots of people having problems,   try using the PC (Intel x86) version, from what i hear it works perfectly with amd64, only a few people said some performance loss.

I dont think thats going to help with your video card though.


Edit: somone please correct me if i'm wrong

---

### Post by zorro26 on 2006-06-29
can anyine else help please

---

### Post by Beej on 2006-06-29
Hi Zorro, me again! What exactly is your problem?  Are you saying you updated from breezy, and now your graphics card isn't working. Can you explain a bit more?

---

### Post by zorro26 on 2006-07-01
Anyone whos online, pls help me with this...i updated my breezy ubuntu online, and after restarting it it gave me just one boot option which was something like ubuntu mm68, and that was only a blue screen with different configration options (like bios setup). i formated my pc installed windows and downloaded DRAPER AMD64 version. i tried everything all over again but it never let me install my modem (ofcourse i was using DRAPER commands). Another odd thing was that it never picked my ATI RADEON x300/x550 series VGA card. i have bought D-LINK 4PORT ETHERNET BROADBAND ROUTER, i have also checked my VGA card drivers CD and it got drivers for linux. my first question is that is it right if i use DRAPER AMD64 for my AMD64 3700 mhz pc, secoundly can i install VGA drivers for linux onto Draper and last question is that can i use that router (i am totaly virgin with routers and installation even in windows).i only have windows on PC now. i have a ubuntu breezy and ubuntu Draper cd.

hmm i have just checked i think i got wrong router its the one where you still need a DSL modem with wan port and connect other pc to broadband..... is that true?

---

### Post by zorro26 on 2006-07-02
right i have just installed Draper again. samething happed. VGA card not been installed no sound and cant install modem....... helpppp

OK i have sorted my VGA, but that it. have just spend another few hours trying to reinstall my modem but no luck. i havnt tried to sort my sound system yet

---

### Post by zorro26 on 2006-07-03
Hello, where all the nice people gone???? i have sorted my VGA card. but i have noticed another thing. there no sound coming through main speakers but when i plug headphones to front of my CPU, there is sound through headphones. thats very strange. Can anyone help ,e with this please???

---

### Post by keith whitehouse on 2006-07-03
hi zorro26,

this thread started out by you asking about a Speedtouch modem. I think that it would be sensible for you to start a new thread.

best regards keith

---

