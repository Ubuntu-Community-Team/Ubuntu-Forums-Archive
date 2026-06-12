---
title: "Bluetooth and gps"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-02-22
Hi out there, i'm a new to ubuntu and i'm using edgy.  I have a bluetooth dongle and bluetooth gps unit (i.trek M5).  I am trying to hook the two up and and use gpsdrive.  I've installed KDE Bluetooth and the gps device is showing it is connected to the dongle.  I do not know if they are connected correctly and even if gpsdrive can work with this set up.  Below is some information I hope will help  thanks.

endlessurf@endlessurf:~$ sudo hcitool dev
Devices:
        hci0    11:11:11:11:11:11
endlessurf@endlessurf:~$ sudo hidd --search
endlessurf@endlessurf:~$ hcitool scan
Scanning ...
        00:0B:0D:19:2D:7B       BT GPS
Searching ...
        Connecting to device 00:0B:0D:19:2D:7B
Can't open input device: No such file or directory (2)         ---   what does this mean?

I went into the /etc/bluetooth/hcid.conf and changed the passkey to 0000
here is a link to the gps unit with some specs
[http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf](http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf)
any info or links will help thanks

---

### Post by endlessurf on 2007-02-22
Hi out there, i'm new to ubuntu and i'm using edgy.  I have a bluetooth dongle and bluetooth gps unit (i.trek M5).  I am trying to hook the two up and and use gpsdrive.  I've installed KDE Bluetooth and the gps device is showing it is connected to the dongle.  I do not know if they are connected correctly and even if gpsdrive can work with this set up.  Below is some information I hope will help  thanks.

endlessurf@endlessurf:~$ sudo hcitool dev
Devices:
        hci0    11:11:11:11:11:11
endlessurf@endlessurf:~$ sudo hidd --search
endlessurf@endlessurf:~$ hcitool scan
Scanning ...
        00:0B:0D:19:2D:7B       BT GPS
Searching ...
        Connecting to device 00:0B:0D:19:2D:7B
Can't open input device: No such file or directory (2)         ---   what does this mean?

I went into the /etc/bluetooth/hcid.conf and changed the passkey to 0000
here is a link to the gps unit with some specs
[http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf](http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf)
any info or links will help thanks

---

### Post by endlessurf on 2007-02-22
Hi out there, i'm new to ubuntu and i'm using edgy.  I have a bluetooth dongle and bluetooth gps unit (i.trek M5).  I am trying to hook the two up and and use gpsdrive.  I've installed KDE Bluetooth and the gps device is showing it is connected to the dongle.  I do not know if they are connected correctly and even if gpsdrive can work with this set up.  Below is some information I hope will help  thanks.

:~$ sudo hcitool dev
Devices:
        hci0    11:11:11:11:11:11
:~$ hcitool scan
Scanning ...
        00:0B:0D:19:2D:7B       BT GPS
:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0B:0D:19:2D:7B
Can't open input device: No such file or directory (2)         ---   what does this mean?

I went into the /etc/bluetooth/hcid.conf and changed the passkey to 0000
here is a link to the gps unit with some specs
[http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf](http://205.134.232.209/Semsons/i.Trek%20M5%20BT%20GPS%20User%20Manual.pdf)
any info or links will help thanks

---

### Post by endlessurf on 2007-02-23
bumpage

---

### Post by Muzik83 on 2007-02-23
Hey

I have almost the same setup, just different GPS reciever.  Sadly I havent configured or used it in quite a while, so these instructions are going to be bad bad bad!

Did you edit /etc/bluetooth/rfcomm.conf to configure it for your GPS receiver? 
Did you do an rfcomm bind rfcomm0

Try a cat /dev/rfcomm0 and see if you get GPS data ... rfcomm0 may also be in /dev/bluetooth/rfcomm/0

Configure gpsdrive to connect to /dev/rfcomm0 for its information

Hope this points you in somewhat the right direction

---

### Post by endlessurf on 2007-02-23
Thanks for the help.  I have gone into the /etc/bluetooth/rfcomm.conf file and put in the gps information.  I did not change anything else in that file.  I go to bind and this what is said

:~$  hcitool scan
Scanning ...
        00:0B:0D:19:2D:7B       BT GPS
:~$ rfcomm bind 00:0B:0D:19:2D:7B
Can't create device: Operation not permitted

i'm wondering what i'm doing wrong

---

### Post by endlessurf on 2007-02-23
ok so here's an up date, i believe everything is hooked up right.  when i do 
:~$ cat /dev/rfcomm0 it is giving the coordinates from the gps.  My one problem is now when i open up gpsdrive with the terminal open, lots of info pops up on the terminal and nothing pops up on the screen.  When i do not have the gps unit hooked up it goes straight into the program.  Any help will be nice thanks.

blue tooth and gps:
:~$ sudo modprobe l2cap
:~$ sudo modprobe rfcomm
:~$ sudo mknod /dev/rfcomm0 c 216 0
:~$ hcitool scan
Scanning ...
        00:0B:0D:19:2D:7B       BT GPS
:~$ sudo sdptool add --channel=1 OPUSH
OBEX Object Push service registered
:~$ sudo rfcomm bind /dev/rfcomm0 00:0B:0D:19:2D:7B 1
:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0B:0D:19:2D:7B
Can't open input device: No such file or directory (2)
:~$ cat /dev/rfcomm0
$GPGGA,022734.757,3943.3370,N,12149.9922,W,1,05,02.2,61.7,M,-25.4,M,,*65

$GPRMC,022734.757,A,3943.3370,N,12149.9922,W,0.00,302.47,240207,,,A*7D

$GPGGA,022735.757,3943.3370,N,12149.9922,W,1,06,01.3,61.7,M,-25.4,M,,*65

$GPRMC,022735.757,A,3943.3370,N,12149.9922,W,0.00,302.47,240207,,



examples of what pops up after i start gps drive:
Message from syslogd@endlessurf at Fri Feb 23 18:29:36 2007 ...
endlessurf kernel: [17179997.332000] Oops: 0000 [#1]

Message from syslogd@endlessurf at Fri Feb 23 18:29:37 2007 ...
endlessurf kernel: [17179997.332000] esi: 00000000   edi: 00000001   ebp: 00000000   esp: e7bc9db4

Message from syslogd@endlessurf at Fri Feb 23 18:29:37 2007 ...
endlessurf kernel: [17179997.332000] esi: 00000000   edi: 00000001   ebp: 00000000   esp: e7bc9db4

ext.....

thanks again

---

### Post by endlessurf on 2007-02-24
bumpage

---

### Post by endlessurf on 2007-02-24
Anyways I have figured out how to get the blue tooth dongle, blue tooth gps ( i.Trek M5) and gpsdrive to work.  This is a sort of how to but more like a way for me to figure out what i did when i have to do this again.  just remember that i'm a nub and and threw a hole bunch of stuff at this problem until i got it to work.  There is no rhyme or reason why i did what i did but it works and that is all that I care about.

install     ( people with more knowledge please cut this list down if possible)
    gpsdrive
    from synaptic package manager
    bluetooth
    bluez
    kismet
    libpcre3
    gpsd

plug in and turn on

gksudo gedit /etc/bluetooth/hcid.conf
         put in your passkey for your bluetooth gps device
         other options might have to be changed
hcitool scan
        your device should pop up with a 12 digit number
gksudo gedit /etc/bluetooth/rfcomm.conf
         change the 12 numbers next to device to match yours from above
         note you might have to delete some #
         the file should look something like:
  rfcomm0 {
	# Automatically bind the device at startup
	bind no;

	# Bluetooth address of the device
	device 00:0B:0D:19:2D:7B;

	# RFCOMM channel for the connection
	channel	1;

	# Description of the connection
	comment "Example Bluetooth device";
}

some of the below will not show any feed back
sudo /etc/init.d/bluetooth restart
sudo hidd --search
       will connect to your bluetooth

:~$ modprobe l2cap
:~$ sudo modprobe rfcomm
:~$ sudo mknod /dev/rfcomm0 c 216 0
:~$ sdptool add --channel=1 OPUSH
:~$ sudo rfcomm bind /dev/rfcomm0 00:0B:0D:19:2D:7B 1

The line below will show if your gps is talking to your comp you do not have to do this every time but it is nice to see if your stuff is working correctly.

:~$ cat /dev/rfcomm0
$GPGGA,022734.757,3943.3370,N,12149.9922,W,1,05,02.2,61.7,M,-25.4,M,,*65

$GPRMC,022734.757,A,3943.3370,N,12149.9922,W,0.00,302.47,240207,,,A*7D

gpsd -p /dev/rfcomm0

one i think works and the other errors out if i remember and you might have to open another terminal or closed one.

telnet localhost 2947
/etc/init.d/mysql start

So this worked for me and i imagine that i left out some important parts.  Someone with more knowledge that runs across this post should tighten up the post.  thanks

---

### Post by 1952mudflap on 2007-02-26
Hello endless,
I've been trying to do the same thing you've done except in Kubuntu.
You say you're a nub but I'm sure I'm nubier than you!
You used "gedit" and that appears unique to ubuntu cause it is not a valid command in kubuntu, so I'm going to try to figure out what the equivalent is if you don't mind, check back to your thread because I have some other questions once I straighten myself out here.
Thanks in advance..............

I'm back, I did a "sudo nano" to edit the conf files...
Now, when I try to do a "hidd --search"  I get a pop up window that says no can do "LMP timeout" error
When I do a "cat /dev/rfcomm0"  I get "function not implemented"
Should I just give up?

---

### Post by endlessurf on 2007-02-27
naw never give up.  are you using blue tooth or usb

---

### Post by endlessurf on 2007-02-27
if you are using bluetooth, you should start off with installing bluez.  and then get your bluetooth to hook up to the gps provided that your gps is bluetooth

---

### Post by 1952mudflap on 2007-02-27
I have a USB bluetooth dongle.  System recognizes it no problem.
I can "hcitool dev" no problem
I can "hcitool scan" and see my bluetooth gps, pocket pc, and phone, no problem.
Before I read your thread, I had NO contents in my "hcid.conf" file, now It's correct and has my gps address in it. Problem is, when I do a "hidd -search" I get an error 
"ronm@ronm-desktop:~$ hidd --search
Searching ...
        Connecting to device 00:02:5B:00:A5:A5
Can't get device information: Function not implemented"
Also, a window pops up telling me there's an error "LMP response time out"

Could this have something to do with /dev/rfcomm0 ?

I'm stumped.

---

### Post by 1952mudflap on 2007-02-27
I just noticed something, this is my rfcomm file...
#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 00:02:5B:00:A5:A5;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Pharos BT GPS";
#}

Shouldn't some of these #'s be removed (aren't they for "comment" lines?

---

### Post by 1952mudflap on 2007-02-27
I think the answer to my question was an obvious "yes" (to you non-nubies)
So I removed them but I still get the same error.



:confused:

---

### Post by endlessurf on 2007-02-27
yeah you need to back out the #### my file looks

#
# RFCOMM configuration file.
#

rfcomm0 {
	# Automatically bind the device at startup
	bind no;

	# Bluetooth address of the device
	device 00:0B:0D:19:2D:7B;

	# RFCOMM channel for the connection
	channel	1;

	# Description of the connection
	comment "Example Bluetooth device";



}

you need to edit your    /etc/bluetooth/hcid.conf file and put in your passkey. my key is 1234 and 
my file looks like this 
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0000";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm master;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

---

### Post by endlessurf on 2007-02-27
my /etc/bluetooth/hcid.conf set up might work for you or you might have to change some settings.

---

### Post by 1952mudflap on 2007-02-28
I went over both hcid.conf and rfcomm.conf and only had to change 1 item,
the link mode in mine was set to "accept", I changed it to "master" like yours,
Restarted bluetooth, and got the same error.
The error is in "kbluetoothd"

By the way, thanks for all your help, I'm so close and it's so hard to get anyone to respond to posts. I appreciate your willingness to help.
Ron

---

### Post by endlessurf on 2007-02-28
hey when you do a:   

sudo hcitool dev

does it list your bluetooth dongle?

---

### Post by endlessurf on 2007-02-28
you might also want to know that i went into the synaptic package manager and typed in bluetooth.   I then installed and or already had installed:
all of the affix
all of the bluez 
bluetooth
btscanner
gnome-bluetooth
kdebluetooth
libaffix2
libbluetooth2
libbtctl4
libgnomebt0
multisync
nautilus-sendto
gobex

I know that more than likely don't need all of these things but from one nub to another it is what i have on my comp sooo.....
plug in usb dongle and then do
sudo /etc/init.d/bluetooth restart

and 
sudo hcitool dev
to make sure that your usb dongle is hooked up

and....
hcitool scan
make sure that those numbers are in the other files ie .config

I'm sure you've already done this but if you were me i make so many stupid mistake:make sure that you put in the right passkey in  hcid.conf  and putting in the # of the gps in rfcomm.conf.  I'm sure you have already done this but this if for me or anyone else that would make this mistake.
anyone with more knowledge, please feel free to cut down the list from above

Mr. Bill

---

### Post by endlessurf on 2007-02-28
oh and i got:
obexserver
what this relates idk but i installed it in my path trying to get it to work

---

### Post by 1952mudflap on 2007-02-28
Thanks Mr Bill
I went over your list and installed affix, libbtcil4, multisync and obexserver.  Same results.
When I hcitool dev the dongle shows up fine.
When I hcitool scan my gps, pocket pc, and razr all show up no problem.
what doesn't work is
   hidd --search
   cat /dev/rfcomm0 .......
and gps drive

I'm about to throw in the towel

oh and by the way, multisync doesn't do anything that I can tell but that could be my not understanding how to use it, but as for the three above, they just flat out don't work !:confused: :(

---

### Post by 1952mudflap on 2007-02-28
I wish I knew what "LMP response timeout" was all about.
I've searched Ubuntu, Kubuntu, KDE, and found very little and NOTHING useful.

---

### Post by endlessurf on 2007-02-28
try a 

hidd --connect 00:0B:0D:19:2D:7B

but where 00:0B:0D:19:2D:7B is put your gps address.

---

### Post by endlessurf on 2007-02-28
when you try to connect are all the other bluetooth on?  or just the gps.   Try it with just the gps.

---

### Post by endlessurf on 2007-03-01
i found this, this might help
[http://ubuntuforums.org/showthread.php?t=34740](http://ubuntuforums.org/showthread.php?t=34740)

---

### Post by 1952mudflap on 2007-03-01
I tried the "hidd connect" but that was before the latest installs so I will try it when I get home from work.
The version of kbluetoothd that I installed was their latest which I had to compile from source, I think I may have to re-compile it now that you've shown me some of the rfcomm support that I did not have installed.  I'll try that when I ge home as well.

Once again..... thanks for your replys:)

---

### Post by endlessurf on 2007-03-01
i guess this would be a good time to tell you that i didn't have to compile anything.  just installed it from the add/remove or from the synaptic package manager (system>admin>synaptic....).

---

### Post by endlessurf on 2007-03-02
dude where are you at tonight?????????????????????????????????????????????

---

### Post by 1952mudflap on 2007-03-02
Sorry Mr. Bill !  I was working last night and got home late.
The reason I compiled is because one of the Kubuntu forums mentioned that there was a problem with the current version of kbluetoothd and everyone was installing a version that was not in the repositories yet.  So... I did that and it got everything working better but I have the issues I've spoken of. I can browse my pda and my phone so I know most things are working I think my issue is with rfcomm functions.  Because of that, I think my issue is that my version of kbluetoothd (compiled from source) lacks the rfcomm functionality and that's why I think I have to re-compile it.  Does that make any sense?

---

### Post by 1952mudflap on 2007-03-03
Well, for now, I'm giving up.  I can see all my devices, pda, phone, gps, but with the gps, I cannot get information from it. GPSDRIVE doesn't connect to it, and Multisync doesn't connect to my pda or my phone. When I run kbluetoothd by clikcing on the grey bluetooth icon I can see everything and even transfer files from the pda or phone.  Attempting to connect to the gps yields the error "LMP response timeout".

I'm frustrated and until I read some new material I'm not attempting to use the gps.

Sorry for the rant, perhaps I'm a bit too impatient.
:mad:

---

### Post by tgalati4 on 2007-03-29
Do you have gpsd installed and running?

Run xgps from a terminal (installed with gpsd) to see your data.  If you get valid NMEA data strings then gpsdrive should see it.

I'm not sure if gpsdrive can talk directly to a bluetooth device as it can with an old-school serial device (/dev/tty0).

---

