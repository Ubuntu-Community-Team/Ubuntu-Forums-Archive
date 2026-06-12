---
title: "Wireless card not recognized"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by sine1757 on 2007-05-06
I have just loaded Ubuntu onto my computer and it doesn't recognize my wireless card. It is a Linksys 2.4 GHz Wireless-B PCI adapter. In the help file it said to download NDISwrapper. Of course I can't download it 'cause I can't connect to the internet! So I've downloaded it my husband's computer, have transferred the file to mine but now I don't know how to install it. I've followed the installation instructions by opening Terminal and typing "sudo apt-get install ndiswrapper" but I get the error message, "couldn't find package ndiswrapper".  I'm using Ubuntu version 7.04.

Please help. I don't know what to do.
Sheena

---

### Post by robbie carrobie on 2007-05-07
hi i had same problem and just managed to fix it, do you know what type of card you got in your machine that runs your wireless

---

### Post by robbie carrobie on 2007-05-07
sorry just re read your post, will try and search for driver for this card.

---

### Post by scrooge_74 on 2007-05-07
if you downloaded the deb package for ndiswrapper you can installed from inside synaptic

---

### Post by robbie carrobie on 2007-05-07
hi what i did is went to the help part on unbuntu, internet, wireless network, found my card and followed the instructions, if all else fails you its a last option, wish i could help you more- robert.

---

### Post by sine1757 on 2007-05-07
Hi Scrooge,

You wrote: if you downloaded the deb package for ndiswrapper you can installed from inside synaptic

Where do I find the "deb package" and is "synaptic" part of Ubuntu??

---

### Post by GSF1200S on 2007-05-07
> **sine1757 said:**
> Hi Scrooge,

You wrote: if you downloaded the deb package for ndiswrapper you can installed from inside synaptic

Where do I find the "deb package" and is "synaptic" part of Ubuntu??

Synaptic is a package manager- its a database of programs, drivers, and libraries needed for different things in Ubuntu. You can find it by going to System -> Administration -> Synaptic Package Manager.

A .deb package is designed to be like installing something on windows.,, double click it and it installs. Im not too familar with Ndiswrapper itself, other than what it does.

To use Ndiswrapper, youll need a windows driver for your wireless card, and youll need the ndiswrapper program installed. Think of ndiswrapper as a program that fools your wireless card into thinking Windows is using it.

---

### Post by sine1757 on 2007-05-07
Okay, I'll see if I can find the .deb package and the synaptic package manager.  Thanks

---

### Post by sine1757 on 2007-05-07
:confused:

---

### Post by Bachstelze on 2007-05-07
You must download the DEB files fom [http://packages.ubuntu.com](http://packages.ubuntu.com)

You install them with the command

```
sudo dpkg -i file.deb
```

---

### Post by sine1757 on 2007-05-07
> **HymnToLife said:**
> You must download the DEB files fom [http://packages.ubuntu.com](http://packages.ubuntu.com)

You install them with the command

```
sudo dpkg -i file.deb
```

Thanks HymnToLife.  If have used the link you provided and put ndiswrapper in the search but now have 3 choices:
Package ndiswrapper-common
Package ndiswrapper-source
Package ndiswrapper-utils-1.9

I'm so lost now I don't know which one to choose.  I've seen reference to "common" and "utils".

? 
Sheena

---

### Post by Bachstelze on 2007-05-07
You just need -common and -utils, -source is used if you want to compile ndiswrapper yourself. Also, you'll need the Windows drivers for your card.

---

### Post by GSF1200S on 2007-05-07
> **sine1757 said:**
> I have just loaded Ubuntu onto my computer and it doesn't recognize my wireless card. It is a Linksys 2.4 GHz Wireless-B PCI adapter. In the help file it said to download NDISwrapper. Of course I can't download it 'cause I can't connect to the internet! So I've downloaded it my husband's computer, have transferred the file to mine but now I don't know how to install it. I've followed the installation instructions by opening Terminal and typing "sudo apt-get install ndiswrapper" but I get the error message, "couldn't find package ndiswrapper".  I'm using Ubuntu version 7.04.

Please help. I don't know what to do.
Sheena

I just reread this..

The reason youre getting an error message is because you dont have an internet connection. 

sudo apt-get install filename

attempts to download the file from an online source. So, no connection = error message. So...

**IF ITS A .DEB PACKAGE, THEN DO THIS**
If the ndiswrapper file you have is a .deb package, double click on it and ndiswrapper will be installed. If its a tar.gz or tar.bz2 package, you must install it manually. 


**IF ITS A TAR.GZ OR TAR.BZ2, THEN DO THIS**
Move the tar.gz or tar.bz2 to your /home folder (you can find this Places -> Home folder). Then, right click on the tar.gz package and go to extract. Extract it in your home folder. Now, open a terminal and change the directory to the folder you extracted. For example, if the folder you extracted is named           ndiswrapper9.2             you would type the following in a terminal:

cd ndiswrapper9.2

then type the following three commands hitting enter after each one:

sudo make
sudo make install
sudo make clean

Hope this helps...

Ha! Seems the situation was somewhat resolved by the time I posted this.. hopefully it will help someone in the future...

---

### Post by sine1757 on 2007-05-07
Okay, I admit I am way over my head on all this but I am fairly smart and I should be able to make all this work.  I have downloaded ndiswrapper-1.38, ndiswrapper deb packages -common and -utils.  I typed the command you suggested "sudo dpkg -i file.deb and got the following error:

error processing ndiswrapper-common_1.38_lubuntul_all.deb (--install): cannot access archieve: No such file or directory
Errors were encountered while processing: ndiswrapper-common_1.38_lubuntul_all.deb

I'm trying not to sound stupid or extremely frustrated but I feel like both!  What am I doing wrong?  

Sheena
Ps
You have been great and your answers are very easy to follow.

---

### Post by Bachstelze on 2007-05-07
Where did you copy the DEBs on your Ubuntu system ? You need to be in the same directory when running the command, or type the patth to the files.

---

### Post by sine1757 on 2007-05-07
> **HymnToLife said:**
> Where did you copy the DEBs on your Ubuntu system ? You need to be in the same directory when running the command, or type the patth to the files.

I copied the DEBs from my USB memory stick to Desktop. When I open Terminal is says sheena@sheena-desktop:

Should I be somewhere else?  Some of this is finally starting to make a little sense.  I'm going back in time to my first computers and DOS.  Similar but different.  Hard to get out of "Windows" mode but I'm trying.

S

---

### Post by Bachstelze on 2007-05-07
When you open a terminal, you're in your home directory. If you copied a file on your desktop, it's in the Desktop subirectory. So to instal your debs, you can either do

```
sudo dpkg -i Desktop/*.deb
```

or

```
cd Desktop
sudo dpkg -i *.deb
```

---

### Post by srt4play on 2007-05-07
Just double-click on the file on your desktop.  It can't get any easier than that.  If it tells you there is a dependency problem, then double-click on the one it's complaining about not having, first.

Why is she being told to do this through the terminal when it is so much easier for a new user to just double-click the thing??? The ease of use is there, why not take advantage of it??

---

### Post by sine1757 on 2007-05-07
Thanks.  I have to run to work for a couple of hours but will try this when I get back and let you know how I get on.  Thank you so much for your patience.  It is much appreciated.  To put this in perspective, the computer I'm on the forums on is in my basement.  The computer I'm trying to get connected to internet is on the upper floor of the house so I am running up and down two flights of stairs each time I try something and then have to come back for more help!

Thanks again,
Sheena

---

### Post by Bachstelze on 2007-05-07
*You* think it's simpler. *I* don't.

---

### Post by srt4play on 2007-05-07
Notice I didn't say simpler for *me*, but for a *new user*.  I think for some things it is simpler for them to copy and paste commands, but jeez she already had the files on her desktop.  To open a terminal and figure out how to use it are needless extra steps when all she is trying to do is install a couple of .debs.

---

### Post by Bachstelze on 2007-05-07
The sooner one learns how to use the terminal, the better it will be for him/her in the long run.

---

### Post by sine1757 on 2007-05-07
Thank you.  That seems to have worked.  Now I just need to find the proper driver to download.

---

### Post by TransplantedCanuck on 2007-05-07
Hi,

This is the far-removed son of sine1757... trying to help her through it over the phone, but its hard cause I have more computer knowledge, but the same amount of Linux/ubuntu knowledge.

Anyway, googled around for stuff related to the card. So we got ndiswrapper working, and we installed the .inf files for the card. 

At first it wouldn't take just LSIPNDS.inf as an ok solution... but I found that we're supposed to install all 3 .inf files in order to get it to accept LSIPNDS.inf.

Except now when we do a     sudo ndiswrapper -l    it says the driver is installed, but it says nothing about the hardware, and according to Ubuntu... there is no hardware.

We ran these commands, which I found in another thread.

> 
sudo ndiswrapper -i LSIPNDS.inf
sudo ndiswrapper -l 
sudo modprobe ndiswrapper
sudo ndiswrapper -m 

Linksys and microsoft, both are bloody annoying. Anyway... further help for us would be lovely. Thanks again for helping my Mom and I out.

---

### Post by sine1757 on 2007-05-07
If anyone is able to help with this it is really appreciated.  Seems like i have the driver loaded and is recognized by Ubuntu but it doesn't recognize the hardware?

What do I do now?

Thanks,
Sheena

---

### Post by Bachstelze on 2007-05-07
What have you done so far ?

---

### Post by TransplantedCanuck on 2007-05-07
See my post. :)

---

### Post by Bachstelze on 2007-05-07
Hmm, then what did *ndiswrapper -l* output ?

---

### Post by TransplantedCanuck on 2007-05-07
To the best of my memory and translated into speakable things over the phone

edit: phoned her.

LSBCMNDS : driver installed
LSIPNDS : invalid driver!
WMP11NDS : invalid driver!


edit2: also...  on the NDISwrapper website it says:
> 
 You must install all three inf files from the driver zip file (I had to force NDIS to load all three drivers for the one card with the -d option on each inf). 

might that be part of it?

---

### Post by Bachstelze on 2007-05-07
Then possibly the installed driver was not the correct one. It would help if we could have the output of *lspci*.

---

### Post by sine1757 on 2007-05-07
> **HymnToLife said:**
> Then possibly the installed driver was not the correct one. It would help if we could have the output of *lspci*.

okay was having trouble getting results of lspci command from one computer to the next. Hoping you can open this file.

---

### Post by sine1757 on 2007-05-08
Then possibly the installed driver was not the correct one. It would help if we could have the output of lspci.

Attached output of Ispci in previous post - anyone able to help??

---

### Post by Bachstelze on 2007-05-08
Ok so now we're off for another command :p The output shouldn't be hard to copy though, it's only 8 characters.

```
lspci -n | grep 00:07.0 | awk '{print $3}'
```

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> Ok so now we're off for another command :p The output shouldn't be hard to copy though, it's only 8 characters.

```
lspci -n | grep 00:07.0 | awk '{print $3}'
```

right so response is

17fe:2120

---

### Post by Bachstelze on 2007-05-08
That's weird. On the ndiswrapper Wiki, people reported success with LSIPNDS.inf, which failed for you... Try using those drivers :

[http://www.truckstop.net/support/C130-Driver.zip](http://www.truckstop.net/support/C130-Driver.zip)

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> That's weird. On the ndiswrapper Wiki, people reported success with LSIPNDS.inf, which failed for you... Try using those drivers :

[http://www.truckstop.net/support/C130-Driver.zip](http://www.truckstop.net/support/C130-Driver.zip)

Okay.  So I've downloaded but get two files 
C130-Driver.zip.part       and        C130-Driver.zip

Which one do I use?  My son talked me through opening the other driver files today but I didn't write down his instructions and he'll be asleep now.  

Sorry to be a bother.

---

### Post by Bachstelze on 2007-05-08
The *.part file means that Firefox has not finished downloading the file. Give it a few moments ;)

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> The *.part file means that Firefox has not finished downloading the file. Give it a few moments ;)

Doh!! Okay off upstairs to try this one.

---

### Post by sine1757 on 2007-05-08
extracted the file and installed it.  typed Code: ndiswrapper -l  

lsbcmnds : driver installed
lsipnds : invalid driver!
wmp11nds : invalid driver!

Still doesn't seem to recognize the hardware and when I go to System>Administration>Networking it still doesn't show a Wireless Connection.

Sheena

---

### Post by Bachstelze on 2007-05-08
First, remove all those useless drivers :

```
sudo ndiswrapper -r lsbcmnds
sudo ndiswrapper -r lsipnds
sudo ndiswrapper -r wmp11nds
```

Then, where did you save that ZIP file (on your Ubuntu system) ?

---

### Post by sine1757 on 2007-05-08
It is on the desktop on my Ubuntu system and on my USB memory stick

---

### Post by Bachstelze on 2007-05-08
OK, so do this and be sure to not make typing mistakes ! :

```

cd
mkdir drivers
mv Desktop/C130-Driver.zip drivers
cd drivers
unzip *.zip
cp */DRIVERS/WinXP/* .
rm -rf T*
sudo ndiswrapper -i NETI2120.INF
ndiswrapper -l
```

What does the last one tell you ?

---

### Post by sine1757 on 2007-05-08
removed other drivers.  Followed Code from help file to install new driver.
sudo ndiswrapper -i ~/Desktop/driver.inf

typed in code  ndiswrapper -l but nothing gets listed.

I'm installing the driver from the WinXP folder in Truckstop folder

---

### Post by sine1757 on 2007-05-08
Sorry didn't see your post.  Will follow your instructions.  BRB

---

### Post by Bachstelze on 2007-05-08
EDIT : Never mind, good luck with that ;)

---

### Post by sine1757 on 2007-05-08
:(  After code:

sudo ndiswrapper -i NET12120.INF    get the following:

installing net12120 ...
couldn't open NET12120.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

---

### Post by Bachstelze on 2007-05-08
Hmm, that's even more weird, I have no problem installing it here. I'm using the lastest ndiswrapper built from source though... I think you made a mistake in typing what I told you, what does this output ?

```
ls ~/drivers
```

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> Hmm, that's even more weird, I have no problem installing it here. I'm using the lastest ndiswrapper built from source though... I think you made a mistake in typing what I told you, what does this output ?

```
ls ~/drivers
```


Result:

C130-Driver.zip     IPN2120.CAT  IPN2120.SYS  NET12120.INF  NET12120.INF.bak

(the C130-Driver.zip) is in bright green.

Also when I typed the unzip code, I can see the NET12120.INF file in the listing

---

### Post by Bachstelze on 2007-05-08
Oh, then I think it's just Ubuntu's ndiswrapper being stupid... Try this

```
cd ~/drivers
cp NET2120.INF net2120.inf
sudo ndiswrapper-1.9 -i net2120.inf
```

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> Oh, then I think it's just Ubuntu's ndiswrapper being stupid... Try this

```
cd ~/drivers
cp NET2120.INF net2120.inf
sudo ndiswrapper-1.9 -i net2120.inf
```

after Code: cp NET12120.INF net12120.inf    result:

cp: cannot stat 'NET12120.INF': No such file or directory

typed last line of code anyway       result:

driver already installed

typed Code: ndiswrapper -l         result:

net12120: invalid driver!

Think I need to get some sleep now.  Will try again in the morning.  Thanks again for persevering with me.

---

### Post by Bachstelze on 2007-05-08
Hmm no, actually, it's me being stupid...

```

cd ~/drivers
sudo ndiswrapper-1.9 -i *.INF
ndiswrapper-1.9 -l
```

That should work ;)

---

### Post by sine1757 on 2007-05-08
Anyone have any other suggestions?  What is my next step??

Thanks

---

### Post by sine1757 on 2007-05-08
Sorry again - didn't realize there was another [I]page[I] of messages!

So followed those new instructions
Result:
net12120  : invalid driver!
neti210     : driver installed
device (17FE:2120) present

What is the next step?

If I go to System>Administrator>Networking   it still does not show a Wireless Connectcion.  So am i right to assume I now have a driver for the wireless card but Ubuntu is still not recognizing the hardware?

---

### Post by sine1757 on 2007-05-08
HymnToLife,

Thanks so much for all of your help.  Did I say I was smart??? - duh, decided to restart and see what happened - gee, I now show a wireless connection in Network.  Yipee!!!!!!!!!

So guess I now need to chane my title as it should be "how do I get my wireless connection to work.

Thank you so much again for putting up with such a newbie.

Sheena

---

### Post by Bachstelze on 2007-05-08
```
sudo iwconfig
```

Does it show the wireless connection there, too ?

---

### Post by sine1757 on 2007-05-08
> **HymnToLife said:**
> ```
sudo iwconfig
```

Does it show the wireless connection there, too ?

Result:
lo          no wireless extensions

etho0   no wireless extensions

wlan0   IEEE 802.11b      ESSID: off/any
            Mode: Managed Frequency : 2.432 GHz     Access Point: Not Associated
            Bit Rate=1 Mb/s     Tx-Power: 17 dBm
            RTS thr = 2347 B     Fragment thr=2346 B
            Encryption key : off
            Power Management : off
            Link Quality : 0     Signal Level : 0     Noise Level : 0
            Rx invalid nwid : 0     Rx invalid crypt : 0     Rx invalid frag : 0
            Tx excessive retries : 0     Invalid misc : 0     Missed beacon : 0

So is this good news?  :)

---

### Post by Bachstelze on 2007-05-08
Yes :) What kind of encryption does your wireless network use (WEP, WPA, ...) ?

---

### Post by sine1757 on 2007-05-08
Oh crap - I have absolutely no idea and number one smart son is at work!  Is there somewhere on husbands windows computer that I could find that?  Or woudld it be on the router?  We are usuing high speed cable internet if that means anything.

:(

---

### Post by Bachstelze on 2007-05-08
Then just run

```
sudo iwlist wlan0 scan
```

the info will be in there.

---

### Post by sine1757 on 2007-05-08
Results:

wlan0     Sacn completed:
Cell 01 - Address: 00:13:10:0C:B3:7A
ESSID: "Cook"
Protocol: IEEE 802.11b
Mode: managed
Frequency: 2.437 GHz (Channel 6)
Quality: 59/100  Signal level: -58 dBm  Noise level: -96 dBm
Encryption key: off
Bit rates: 1 Mb/s; 2 Mb/s: 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
Extra:atim=0

---

### Post by Bachstelze on 2007-05-08
```
sudo iwconfig wlan0 essid Cook
sudo dhclient wlan0
```

Open Firefox and voilà :p

---

### Post by sine1757 on 2007-05-08
Hmmm, hold the voila for now.  Did that, opened Firefox but can't open any websites.  This is the results of what you asked me to input:

Internet Systems Consortium DHCP Client V3.0.4
Copy right 2004-2006 Internet Systems Consortium.
All rights reserved.
Fro info, please visit [http://www.isc.org/sw/dhcp](http://www.isc.org/sw/dhcp)

Listening on  LPF/wlan0/00:13:10:37:4f:55
Sending on   LPF/wlan0/00:13:10:37:4f:55
Sending on   socket/fall back
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received
No working leases in persistent database - sleeping

:confused:

---

### Post by Bachstelze on 2007-05-08
Your network is not using DHCP, you'll have to get the correct IP parameters. On that other Windows machine, do Start > Run. In the dialog box, type

```
cmd /k ipconfig /all
```

and paste what you get. The Windows command-line won't let you copy text "on the fly", you'll need to use the system menu, like [this](http://www.pcentraide.com/tutoriel/adresse-ip/connaitre-son-ip.png) (it's in French but you get the idea).

---

### Post by sine1757 on 2007-05-08
Thank goodness for 4 years of High School French!  :-)  Where do I paste it?  (i.e. how do I get it from windows machine to my Ubuntu machine).

S

---

### Post by Bachstelze on 2007-05-08
Just paste it here :)

---

### Post by sine1757 on 2007-05-08
Haha  Okay here it is.


Windows IP Configuration
 
        Host Name . . . . . . . . . . . . : ASDF
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
 
Ethernet adapter Wireless Network Connection:
 
        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Wireless-B PCI Adapter
        Physical Address. . . . . . . . . : 00-12-17-0D-35-08
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.52
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 64.59.160.13
                                            64.59.160.15
 
C:\Documents and Settings\Sheena Cook>

---

### Post by Bachstelze on 2007-05-08
okey dokey, do this :

```
sudo ifconfig wlan0 inet 192.168.1.53 netmask 255.255.255.0
sudo route add default gw 192.168.1.1
echo "nameserver 64.59.160.13" | sudo tee /etc/resolv.conf
```

Then try to browse the net again.

---

### Post by sine1757 on 2007-05-08
Still no luck  Here are results:

Code: sudo route add default gw 192.168.1.1

Usage:   route [-nNvee] [-FC] [<AF>] List kernal routing tables
 route [-v] [-FC] {add|del|flush}... modify routing table for AF.

route {-hl|--help} [<AF>] Detailed usage syntax for specified AF.
route {-V|--version}  Display version/author and exit.

-v, --verbose   be verbose
-n, --numeric  don't resolve names
-e, --extend  display other/more information
-F, --fib  display Forwarding Information Base (default)
-C, --cache  display routing cache instead of FIB

<AF>=Use '-A<af>' or '--<af>' ; default: inet
List of possible address families (which support routing):
inet (DARPA Internet) inet6 (IPV6) ax25 (AMPR AX.25)
netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP)
x25 (CCITT X.25)

Code: echo "nameserver 64.59.160.13" |sudo tee /etc/resolve.conf

name server 64.59.160.13

---

### Post by Bachstelze on 2007-05-08
Double-check commands before typing them. You made at least two mistakes and I'm pretty sure you made others too...

---

### Post by sine1757 on 2007-05-08
Sorry, I have to write down what you tell me, run upstairs and type it in, write down response and then come back and type again.  I have double checked the command code that I wrote down first.  I think mistakes are in last reply - I see that I put an 'e' in resolv that is not what I typed upstairs. and missed a space.  I'll double check upstairs.

Found one error there.  So after all three lines of code response is :

nameserver 64.59.160.13

Still can't connect online though.  Says "Firefox can't find the server at www.ubuntu.com."

---

### Post by Bachstelze on 2007-05-08
That's weird, the *route* command does not throw that error here... I guess you could just use the Networg GUI-thingie to configure your interface

Address : 192.168.1.53
Subnet : 255.255.255.0
Gateway : 192.168.1.1
Name server : 64.59.160.13

---

### Post by sine1757 on 2007-05-08
okay so where do I find the Networg GUI thingey?

---

### Post by Bachstelze on 2007-05-08
This is what I don't know, as you could see, I'm command-line all the way...

---

### Post by sine1757 on 2007-05-08
Should I try to type the command codes one more time??

---

### Post by Bachstelze on 2007-05-08
It wouldn't hurt, and maske youre you don't do any typing mistake ! Maybe it's just *route* behaving differently in Ubuntu though, I'll install one in vmware and check this out.

---

### Post by sine1757 on 2007-05-08
Do I also need to Restart after I do these things?

---

### Post by sine1757 on 2007-05-08
So retyped all three lines of code again and after last line response is: name server 64.59.160.13

Still can't connect to internet.  Thought we almost had it there!

---

### Post by Bachstelze on 2007-05-08
This is normal. The problem is the error you get when you type the *route* command, it should not be there...

---

### Post by sine1757 on 2007-05-08
which error?  Once I fixed my typo after each line of code it goes back to sheena@sheena-desktop~$

---

### Post by Bachstelze on 2007-05-08
Oh, that's different then. And still no net ? What do these do ?

```
ping 192.168.1.1
ping 209.85.135.103
ping www.google.com
```

No need to copy the whole output, I just need to know if the connection works or not.

---

### Post by TransplantedCanuck on 2007-05-08
Just got home and checked the thread.

HymnToLife.... you are amazing. Thank you!! =D> =D> 


Ironically, the first thing popped in my head was "ping the gateway".... guess all that cisco brain beating paid off. :P

We can't reach the gateway, so the connection still isn't up... whats the command to see if the interface is up?

---

### Post by sine1757 on 2007-05-08
ping 192.168.1.1
Connect: Network is unreachable

ping 209.85.135.103
connect: Network is unreachable

ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by Bachstelze on 2007-05-08
*smacks forehead*

```
sudo ifconfig wlan0 up
```

---

### Post by TransplantedCanuck on 2007-05-08
hahaha...

CCNP troubleshooting ftw...

1. plugged in?
1. ping gateway.
2. interface up?

---

### Post by TransplantedCanuck on 2007-05-08
it's still saying the destination host is unreachable when we try and ping the gateway

---

### Post by sine1757 on 2007-05-08
I'M ON THE NET!!!!!!!!!!1:) 

I'M IN THE FORUMS!!!!!!!!!!!!!!!!!

HymnToLife - you are the absolute best!!!!!!!!!!!!!!!!!!!

email me privately [email]rastacu@shaw.ca[/email]  I'd like to send you a proper thank you!!

Sheena & Andrew (alias Transplanted Canuck)

---

### Post by sine1757 on 2007-05-08
Okay so HymnToLife you might want to run and hide - next is getting  my printer to run.

---

### Post by Bachstelze on 2007-05-08
Putting your email address on a public from is not a wise thing to do unless you have a very good antispam... My email is the same I use for MSN so just click on the MSN icon to get it if you want to email me :)

And no, I can't help you with your printer, sorry ;)

---

