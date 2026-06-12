---
title: "Wireless Problem"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by mjhasbach on 2007-04-01
Hello, I am having a few wireless problems with Ubuntu version 6.10 that I am hoping someone can help me with. I installed Ubuntu today, and everything seems to be working fine...besides wireless. This is something I have always had trouble with...regardless of the build.

I have read through many posts, and set up everything as per what I have read...to no/little avail. My wireless card is the "PRO/Wireless 2100 (Centrino)" and it is supported according to [THIS]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") page. I have enabled use of the Wireless card in Ubuntu and I have set it up correctly to match my connection in Windows XP. When I open up the monitoring window it says that packets are being sent and recieved, and that I have a good signal strength. When I open up firefox, it brings me to my home page, google.com, which gives me the wonderful page can not be dispayed error. Also, internet applications such as GAIM are not working...etc. The wierd thing is, I can type in the IP for my router, login, and change settings. But as far as I know, playing with the router on my own network is the only thing that I can do, and I can't access the outside world.

Any suggestions would be greatly appreciated, TIA.

---

### Post by Dual Cortex on 2007-04-01
This is something I've experiend too with a different network adapter, and I don't really know a fix for it but I believe if you wait a bit, everything works (can't exactly remember how it finally worked out, and I might just be telling you to waste your time).

Actually try this:
[http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

I think I just learned a new thing, great! Never really researched my problem since I never again experienced it.

---

### Post by ac7ss on 2007-04-01
the results of the commands 

iwconfig
ifconfig

would help considerably. 

also, try pinging 72.14.253.147 (google.) this will test your dns settings. 
Are you running dhclient after connecting?

---

### Post by ac7ss on 2007-04-01
With the wait for it theory it sounds like the dhclient needs to be kicked.

I have a little script I use for connecting:
```
#! /bin/sh
# New and improved WiFi scan and connect

ctf=/tmp/connect.$$

trap "exit 1"   HUP INT PIPE QUIT TERM
trap "rm -f $ctf" exit

echo '\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n'
        clear
        echo "Utility for connecting to wifi networks.\nWritten by Glenn Brockett\n"
if [ $1 ] ;then

#       Command line may accept an interface name, otherwise it will scan for an active interface.

        interf="$1"
else

#       This will set it up with the installed IEEE 802.11 device. 

        interf=`iwconfig 2> /dev/null | grep "IEEE 802.11" | sed 's/ *IEEE.*//'`

fi

#       Display interface.

printf "Active interface: -%s-\n\n" "$interf"

#       If there is an interface present:

if [ "$interf" ]; then

#       List available networks into file for a menu

        iwlist $interf scan | grep 'Cell\|Mode:\|ESSID\|key:off\|Signal'|tac |sed -n '/Encry/,+4 p' |tac | sed 's/ - Addr.*//;s/.*Cell/Cell/; s/.*ESSID/ID/; s/.*Sig/Sig/; s/.*Mode:/Mode:/; s/\/153.*level:/\//; s/\/153//' |grep 'Cell\|ID\|Mode:\|Signal' >$ctf

#       Re-Format menu for ease of reading.

        cat $ctf |sed   '/Cell/N; s/\n/\t/' |sed   '/Cell/N; s/\n/\t/' |sed  '/Cell/N; s/\n/\t/; s/ID://; s/Signal level/SNR/' >$ctf

#       Display menu:

        cat $ctf

        echo '\nCurrent:'

#       Show current configuration
#       First the wireless portion

        iwconfig $interf|sed -n 's/.*ESSID/ ID/; s/Nickname:.*//;s/.*Link/ Link/; s/Signal.*//; /ID\|Link/ p '|sed -n '/ID/ h;/92/ H ;x ;s/\n/\t/;/\/92/p'

#       Then the IP

        ifconfig $interf| sed -n 's/.*inet addr/ IP/;s/Bcast.*//;/IP/ p'

#       Query for selection

        echo '\nEnter Cell # (both digits) Return to exit'
        read selection
        echo ""

#       Branch to do nothing unless there is a selection.

        if [ "$selection" ] ; then

#       Check for valid selection

                if grep "Cell $selection" $ctf > /dev/null ; then 

#       Set ESSID

                        iwconfig $interf essid "`grep "Cell $selection" $ctf |sed 's/.*\t\"//1; s/\"\t.*//'`"

#       Set Mode (Managed|Ad-Hoc)

                        iwconfig $interf mode `grep "Cell $selection" $ctf |sed 's/.*Mode://; s/\tSNR.*//; s/Master/Managed/'`

#       Run dhclient

                        dhclient $interf

#       Show off new settings

                        echo '\nNew:'
                        iwconfig $interf| grep 'ESSID\|Link' | sed 's/.*ESSID/ ID/;s/.*Link/ Link/'
                        ifconfig $interf| sed -n 's/.*inet addr/ IP/;s/Bcast.*//;/IP/ p'
                fi
        fi

#       cleanup
        rm $ctf
else
        echo ""

```

which may be a little much for a fixed ESSID, but it works wonderfully.
(Note, this works best either done with sudo or suid bit set on the iwlist, iwconfig, ifconfig, and dhclient executables do this at your own risk.)

---

### Post by mjhasbach on 2007-04-01
Thanks for the replies everyone...You will have to forgive my limited linux knowledge, but:

1. How would I run the commands? through the terminal thing? lol
2. What would I do with the information obtained by running these commands?
3. How do I ping in linux?
4. How do I use the script you provided?

Thankyou very much:)

---

### Post by ac7ss on 2007-04-01
Yes the dreaded terminal thing.  (get used to it, it is easy to write scripts to automate many tasks you will love it later.)

Post the results of the iwconfig and ifconfig commands.

but first of all:

$ping 72.14.253.147

(you don't type the $, that indicates a prompt)

It should say something like 
```
64 bytes from po-in-f147.google.com (72.14.253.147): icmp_seq=1 ttl=240 time=27.4 ms

```
where the important things are:
blah.google.com - the resolved address
TTL - the number of bounces left in that ping (helps prevent loops)
time - the time that the ping took to return.

Ping started out in unix, MS just copied a good thing.

---

### Post by Dual Cortex on 2007-04-01
> **mjhasbach said:**
> Thanks for the replies everyone...You will have to forgive my limited linux knowledge, but:

1. How would I run the commands? through the terminal thing? lol
2. What would I do with the information obtained by running these commands?
3. How do I ping in linux?
4. How do I use the script you provided?

Thankyou very much:)

1- yeah ;), Applications>Accessories>Terminal... or right click Desktop + "Open Terminal."

2- Copy them from the terminal window and paste them here.

3- ping -c [numberOfTimes] [DESTINATION]

---

### Post by ac7ss on 2007-04-01
use a text editor, paste the text from the script into it, save it (I use the filename 'connect')
in the 'dreaded' shell, type
chmod u+x connect

then at the shell prompt type 

sudo ./connect

CAUTION: USE THE SUDO COMMAND WITH CARE. if you don't understand the command, look it up. or some yahoo (like me) could really mess up your system.

you will need several commands in your system to work with this. type 
locate iwconfig
locate iwlist

if it doesn't find them, use a package manager to load them.

---

### Post by mjhasbach on 2007-04-01
Thanks. I'll mess around with the terminal and these commands and post my results =]

---

### Post by mjhasbach on 2007-04-02
Allrighty...I'm going to try to bring this topic back from yesterday and see if I can get this resolved. Here are my results:

I ran iwconfig:

m@m-laptop:~$ locate iwconfig
/sbin/iwconfig
/usr/share/man/cs/man8/iwconfig.8.gz
/usr/share/man/fr/man8/iwconfig.8.gz
/usr/share/man/man8/iwconfig.8.gz
~~~~~~~~~~~~~~~~~~~~~~~~~
I ran iwlist:

m@m-laptop:~$ locate iwlist
/sbin/iwlist
/usr/share/man/cs/man8/iwlist.8.gz
/usr/share/man/fr/man8/iwlist.8.gz
/usr/share/man/man8/iwlist.8.gz
~~~~~~~~~~~~~~~~~~~~~~~~~
I pinged google:

m@m-laptop:~$ ping -c 1 72.14.253.147
PING 72.14.253.147 (72.14.253.147) 56(84) bytes of data.

--- 72.14.253.147 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
and...I ran that script that ac7ss provided:

Utility for connecting to wifi networks.
Written by Glenn Brockett

Active interface: -eth1-

/root/connect: 94: Syntax error: end of file unexpected (expecting "fi")



If anyone can make any sense of this and try to tell me how to fix my wireless internet on Ubuntu that would be great. TIA.

---

### Post by mjhasbach on 2007-04-02
*bump* help please =]

---

### Post by mjhasbach on 2007-04-02
*bump again* XD

---

### Post by mjhasbach on 2007-04-02
A guy in the IRC channel #ubuntu told me to post the results of iwconfig and iwlist without the locate command before them...so here they are:

m@m-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Wireless"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:09:5B:35:59:12   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

m@m-laptop:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

Can anyone make anything of that...?

---

### Post by Liam1964 on 2007-04-02
I am no Ubuntu expert, however I did manage to get my wireless working just fine. I got to exactly the same point as you. All I did was totally shut down my network - router and all. Rebooted everything and it has worked well ever since.

I know it is simple, but it might help.

---

### Post by chili555 on 2007-04-02
We actually want:```
iwlist eth1 scan
```

---

### Post by ac7ss on 2007-04-02
according to the ping, you are getting through to the net.

According to the iwconfig, you are connected to the access point.

Next test would be typing 

```
ifconfig
```

it wouldn't hurt to try

```
sudo dhclient eth1
```
 after that.

---

