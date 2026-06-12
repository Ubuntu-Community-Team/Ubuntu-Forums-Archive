---
title: "Help required: ADSL Modem Speedtouch 330"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2006-11-19
I would be greatful if someone could assist me with this  problem. (I need a  *beginning to end*, step-by-step IDIOT GUIDE ](*,)  )

I have been trying to connect my THOMSON
SPEEDTOUCH 330 (a spare good one as previously used on the iMac when it ran OS9.2)
I have read about the difficulties of this task on the **Ubuntu Wiki **site and have managed to download the software to varying degrees of success
The 'Guidence notes' start to get a bit 'tricky' to say the least for a 'Plug&Play' man like myself, so if you could possibly guide me though some of the more 'text-driven' areas I would be greatful.

I have both KQD6_3.012 and ZZL_3.012 files in the Home folder on Ubunto *neither *of which want to do anything! and the screen message is something along the lines of '[COLOR="Red"]Could not display KQD6_3.012[/COLOR]' (they do appear as 'program' files in the home folder)
I am then **completely **overwhelmed by all the following instructions although I have all the required information regarding my ISP from when I set up my X86 and OS9.2 computers
(windows style)  I just cannot fathem out HOW to i/put the information.
If anyone can help at all please get back to me. I'm enjoying Ubuntu and just desperate to get on the Web using it.
 
Cheers, Radiolad.     :( :(

---

### Post by Blondie on 2006-11-19
Could you post a link to the wiki you're using? I've never done what you are doing but I might be able to translate it into newbie-ese for you.

---

### Post by Radiolad on 2006-11-19
Hi, Thanks for your response. (My ISP is Tiscali which uses PPPoA) I'll try for the link:-
 
  
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28adsl%29]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28adsl%29") 

I hope this gets you to the right place :???: :???: 
This makes me feel like a complete 'plonker':redface:   

The VCP is 0 (zero)
The VCI is 38
Authentication type PAP
I Think the Version number for the 330 modem is 0 or 2 but I'm not sure as even this part of the instructions did not seem to work!

Thanks in advance,   Cheers,  Radiolad.

---

### Post by xpod on 2006-11-19
I actually had some problems yesterday with the same modem on my mother in laws xp after tiscali sent her a new one....

Turned out to be a dodgy cd they sent her but i got the drivers online ok.
Only to then discovered there as nothing wrong with her old one so god knows how her and tiscali ever came to the conclusion that a new one was required.:confused: 

Anyway ive actually got her as far as "considering" ubuntu so at least i`ll know where to come when she eventually gets sick of windows:D

---

### Post by polly1 on 2006-11-20
Hi

You may find this link of some additional help, if you have still not been able to connect to the Internet.

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

Just remember that when using the command to split the speedtouch file into the 2 bin files  you must ensure that the SpeedTouch name  is the same as on this downloaded file, otherwise it will throw up an error. ie In small case or capital letters as necessary.

I suggest you burn all the Speedtouch/ Index files from your home folder to a cd,for future reference. It saves a lot of bother when doing a reinstall.

---

### Post by Radiolad on 2006-11-20
Hiya, Thanks for your reply. 
The link you gave me is the one I have been attempting to download from. Unfortunately I'm still having difficulty. There must be someone on the forum who is running an iMac with a Speedtouch 330 :confused: ..especially as the software is freely available for this modem. I feel I'm so close yet so far away from the fix :-k 
I have checked the 'name' compatability  as you suggested and everything appears to match ...but still no joy :-? 

Thanks again...and here's hoping. Kind regards  Radiolad

---

### Post by Radiolad on 2006-11-20
On going to the Speedtouch problem: when trying to run  speedtouch_1.3.1-2_powerpc.deb  I am getting an error which says "**Dependency is not satisfiable:hotplug**"   Can anyone explain what this means?
   Cheers, Radiolad

---

### Post by polly1 on 2006-11-21
Hi

You could try [http://www.linux-usb.org/SpeedTouch/index.ht](http://www.linux-usb.org/SpeedTouch/index.ht) email list of problems with speedtouch, or perhaps email them to see if they have a solution to your query.

---

### Post by fishpie on 2006-11-22
Hi Radiolad,
I think I can help you I have managed to get my speedtouch modem to work with both Dapper and Edgy.In order to help need to know three things. First, what colour is your modem? Second, are yo  using Dapper drake? And thirdly are you using the i386(i.e. 32 bit pc) architecture?

---

### Post by orko3001 on 2006-11-23
> Hi Radiolad,
I think I can help you I have managed to get my speedtouch modem to work with both Dapper and Edgy.In order to help need to know three things. First, what colour is your modem? Second, are yo using Dapper drake? And thirdly are you using the i386(i.e. 32 bit pc) architecture?

I could do with some help aswell :) I have downloaded and installed the latest Ubuntu off the live cd which I think is Edgy.

My modem is Revision 4.00 and black.

I have followed this and am fairly convinced that everything has been done: 
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

But no connection. I get the green lights on the modem that flash on boot and set after login.

I am using Tiscali and VPI/VCI numbers are 0.38. My username and password is correct in all files... But no connection.

Syslog says:

Nov 23 11:03:21 usr1-desktop kernel: [17179590.792000] speedtch 1-4:1.0: found stage 1 firmware speedtch-1.bin
Nov 23 11:03:21 usr1-desktop kernel: [17179590.920000] speedtch 1-4:1.0: found stage 2 firmware speedtch-2.bin
Nov 23 11:03:21 usr1-desktop kernel: [17179590.992000] lp0: using parport0 (interrupt-driven).
Nov 23 11:03:21 usr1-desktop kernel: [17179591.012000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Nov 23 11:03:21 usr1-desktop kernel: [17179591.012000] ieee1394: sbp2: Try serialize_io=0 for better performance

Messages says:

Nov 23 11:03:21 usr1-desktop kernel: [17179590.740000] usbcore: registered new driver libusual
Nov 23 11:03:21 usr1-desktop kernel: [17179590.740000] usbcore: registered new driver speedtch
Nov 23 11:03:21 usr1-desktop kernel: [17179590.748000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x018E
Nov 23 11:03:21 usr1-desktop kernel: [17179590.748000] usbcore: registered new driver usblp
Nov 23 11:03:21 usr1-desktop kernel: [17179590.748000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Nov 23 11:03:21 usr1-desktop kernel: [17179590.756000] Initializing USB Mass Storage driver...
Nov 23 11:03:21 usr1-desktop kernel: [17179590.756000] scsi4 : SCSI emulation for USB Mass Storage devices
Nov 23 11:03:21 usr1-desktop kernel: [17179590.756000] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 23 11:03:21 usr1-desktop kernel: [17179590.756000] usbcore: registered new driver usb-storage
Nov 23 11:03:21 usr1-desktop kernel: [17179590.756000] USB Mass Storage support registered.
Nov 23 11:03:21 usr1-desktop kernel: [17179590.792000] speedtch 1-4:1.0: found stage 1 firmware speedtch-1.bin
Nov 23 11:03:21 usr1-desktop kernel: [17179590.920000] speedtch 1-4:1.0: found stage 2 firmware speedtch-2.bin
Nov 23 11:03:21 usr1-desktop kernel: [17179590.992000] lp0: using parport0 (interrupt-driven).
Nov 23 11:03:21 usr1-desktop kernel: [17179591.012000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Nov 23 11:03:21 usr1-desktop kernel: [17179591.012000] ieee1394: sbp2: Try serialize_io=0 for better performance

So something is happening. Please help :)

---

### Post by fishpie on 2006-11-23
Hi orko3001,

Ubuntu seems to be finding the firmware, so your problem probably lies in dialing the internet. To diagnose your problem, you should try and run the dial script from the command line and post the result here. To run the dial script:
> sudo /etc/rc.d/dial

---

### Post by orko3001 on 2006-11-23
> Ubuntu seems to be finding the firmware, so your problem probably lies in dialing the internet. To diagnose your problem, you should try and run the dial script from the command line and post the result here. To run the dial script:

Quote:
sudo /etc/rc.d/dial  


Hi Fishpie,

This is what happened:

I put this in
root@usr1-desktop:~# sudo /etc/rc.d/dial 

and got this 
sudo: /etc/rc.d/dial: command not found

I realises it is in rc2.d and checked that it was there. I then put this in
root@usr1-desktop:~# sudo /etc/rc2.d/dial 

and got this
sudo: /etc/rc2.d/dial: command not found

If i reinstall:
root@usr1-desktop:~# sudo install -m 744 dial /etc/init.d &&
> 
> sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
> 
> sudo ln -sf ppp/resolv.conf /etc/resolv.conf

I get this
ln: creating symbolic link `/etc/rc2.d/S95dial' to `../init.d/dial': File exists

but still get 'command not found'

:S

---

### Post by fishpie on 2006-11-23
Sorry orko3001 I got the command wrong. You should type this
> sudo /etc/init.d/dial

---

### Post by orko3001 on 2006-11-23
> 
Sorry orko3001 I got the command wrong. You should type this
Quote:
sudo /etc/init.d/dial  


Did this
sudo /etc/init.d/dial

Got this
sudo: unable to execute /etc/init.d/dial: No such file or directory

It is there as I checked several times. :s

---

### Post by orko3001 on 2006-11-23
Sorry but I am new to Ubuntu and Linux. This issue isn't being caused by me being logged into root is it?

Probably not but thought I would ask.

Thankyou for your advice :)

---

### Post by fishpie on 2006-11-23
orko3001, it looks like you have a problem with your  /etc/init.d/dial file. I need to know the details about the file. Type the following and post the result

```
ls -l /etc/init.d/dial 
```

---

### Post by orko3001 on 2006-11-23
> orko3001, it looks like you have a problem with your /etc/init.d/dial file. I need to know the details about the file. Type the following and post the result
Code:
ls -l /etc/init.d/dial


Did this:
ls -l /etc/init.d/dial

Got this:
-rwxr--r-- 1 root root 275 2006-11-23 14:13 [COLOR="Lime"]/etc/init.d/dial[/COLOR]

Please note that '/etc/init.d/dial' was green.

Thankyou :mrgreen:

---

### Post by Radiolad on 2006-11-23
> **fishpie said:**
> Hi Radiolad,
I think I can help you I have managed to get my speedtouch modem to work with both Dapper and Edgy.In order to help need to know three things. First, what colour is your modem? Second, are yo  using Dapper drake? And thirdly are you using the i386(i.e. 32 bit pc) architecture?

Hi Fishpie, The information you asked for is:-
1. Modem Speedtouch330 SILVER
2. Ubuntu 6.06.1 Dapper (loaded from LiveCD and no longer using Mac OS 9.22 which I chose to delete on loading Ubuntu)
3. Using Windows98se for accessing the web and downloads on seperate PC.

Additional info:- PPC requiring to connect:- iMac Graphite G3 400Mhz. 512 Meg of Ram.

I have searched the Ubuntu forums and the Speedtouch ADSL site in attempting to load the correct Firmware for the ST330 from:- [http://downloads.sourceforge.net/speedtouch/speedtouch_1.3.1-2_powerpc.deb](http://downloads.sourceforge.net/speedtouch/speedtouch_1.3.1-2_powerpc.deb)

**ERROR **messages are:- "Could not display KQD6_3.012", (or ZZL_3.012);   "Dependency is not satisfiable: hotplug".
 
  N.B. the iMac does '**see**' the modem on its USB 'devices' but (strangely) BOTH green lights are on even though the telephone cord is NOT connected (so one light should be red  or at least a flashing green!!) I assume this is due to the need for providing the correct firmware??
An Ubuntu forum member (LINEAR) thinks that possibly the FIRMWARE-EXTRACTOR is for X386 PCs and therefore not compatible with Mac/Linux when attempting to 'split' the file in the two components:-  speedtch-1.bin & speedtch-2.bin  
I hope there is sufficient info here. I am looking forward to accessing the web using Ubuntu.

  Thanks in advance, regards  Radiolad :-?

---

### Post by fishpie on 2006-11-23
orko3001,
Your /etc/init.d/dial appears to be OK it is present and is executable. I'm confused by your problem, please humour me and try running the script again using:

```
sudo /etc/init.d/dial
```

---

### Post by fishpie on 2006-11-23
Radiolad,
> 1. Modem Speedtouch330 SILVER
This is a revision 4 modem, which means that you will need the ZZZL_3.012 firmware
> 2. Ubuntu 6.06.1 Dapper
Good choice
> 
Additional info:- PPC requiring to connect:- iMac Graphite G3 400Mhz. 512 Meg of Ram.

PPC complicates matters slightly, but should still be workable

There are two different drivers available for dapper the usermode driver and the kernel driver. Both will work with Dapper. However, the usermode driver doesn't work with newer kernels so will break when/if you upgrade to edgy or likely future versions of ubuntu. Thhe instructions at
[https://help.ubuntu.com/community/Us...ght=%28adsl%29](https://help.ubuntu.com/community/Us...ght=%28adsl%29) are for the kernel driver. However, they will not work on PPC. since the involve downloading and running an i386 binary of the firmware extractor.
I think that your best option is to download already extracted firmware from [http://speedtouchconf.sourceforge.net/rev4fw.zip]("http://speedtouchconf.sourceforge.net/rev4fw.zip")
You will need to create 3 further files using notepad on your PC and then you should copy them to your home directory along with the rev4.zip firmware file. The first file to create is a file called secrets it should contain just one line
> "username@isp" "*" "password"
Type the details that you use to connect to your ISP from windows Rather that literally typing "username@isp" and "password". The second file that you need to create should be called speedtch and should look like this
>  noipdefault
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin pppoatm.so
0.38

### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd
Again, replace username@isp with your actual ISP details. The third file that you should create is a bootscript it should be called dial and it should contain the following
> #!/bin/bash
modprobe ppp_generic
modprobe pppoatm
count=0
while [[ $((count++)) -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    pppd call speedtch
    exit 0
  fi
  sleep 1
done
echo "The SpeedTouch firmware did not load"```

```

Copy all 4 files to your home directory

 Next some terminal work Applications->Accessories->Termninal should start the terminal now you need the following command to unzip the firmware
```
sudo unzip rev4fw.zip  
```
now you will have to copy the two extracted files to the appropriate place. Using the following two commands. You will be prompted for your login password, just type it when prompted
```
sudo cp ZZZLP1.eni /lib/firmware/speedtch-1.bin
sudo cp ZZZLP2.eni /lib/firmware/speedtch-2.bin
```

Next you have to configure pppd, by issuing the following commands

> sudo install -m 600 secrets /etc/ppp/pap-secrets
sudo install -m 600 speedtch /etc/ppp/peers 
sudo ln -sf /etc/ppp/resolv.conf /etc/resolv.conf

Finally you have to install the boot script using
> sudo install -m 744 dial /etc/init.d
sudo ln -s /etc/init.d/dial /etc/rc2.d/S95dial
I hope the terminal stuff isn't too intimidating. Just type in the commands EXACTLY one line at a time and press enter at the end of each line. You may wish to save these instructions to a file and copy and paste them into the terminal.

---

### Post by orko3001 on 2006-11-24
> orko3001,
Your /etc/init.d/dial appears to be OK it is present and is executable. I'm confused by your problem, please humour me and try running the script again using:
Code:
sudo /etc/init.d/dial

Did this:
sudo /etc/init.d/dial

Got this:
sudo: unable to execute /etc/init.d/dial: No such file or directory

Wierd :-k 

I wonder if this is just a dodge version of Ubuntu. I installed this off the live cd. Is there somewhere better I could install it off? On a seperate point Openoffice and a couple of other programmes don't start. The loading bar on OpenOffice gets about half way then the splash screen disappears and nothing else happens. It was the same on the live cd. I thought I would get online and download a new version and install that. I'd be lucky. :D

Thanks for your help :)

---

### Post by Radiolad on 2006-11-24
Hiya Fishpie,
I'll give it a try, One question regarding the following:-
 (in red)
noipdefault
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin pppoatm.so
0.38

[COLOR="Red"]### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd[/COLOR]

[COLOR="Black"][/COLOR] Do I type this in, or is it an instrution to ME ? (sorry to be so thick!!)

   Cheers, Radiolad

---

### Post by orko3001 on 2006-11-24
> Do I type this in, or is it an instrution to ME ? (sorry to be so thick!!)
Cheers, Radiolad



Text after # are comments. It is information for you. You put it with the rest of the code but the computer is told to ignor text in a line after #

In this exaple on this page:

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

There is this statement:

'Also try adding the option 'debug' to /etc/ppp/peers/speedtch, it will then be more verbose in the system log (/var/log/syslog).'

Which means delete the # before # debug to allow debug to work. 

Hope this isn't too garbled. :-D

---

### Post by Radiolad on 2006-11-24
Thanks, Now an even 'Thicker' question !.. Where IS 'notepad' on Ubuntu ???
Cheers Radiolad

---

### Post by fishpie on 2006-11-24
Radiolad, the lines that begin with a # are comments i.e. entries in a configuration file or computer program that are their to make the file more understandable to humans and are ignored by the computer. So you can leave them out if you like. To run "notepad" Applications->accessories->Text Editor

---

### Post by fishpie on 2006-11-24
orko3001,```


```
You could try ```
sudo pppd call speedtch
```
this should connect you to the internet without using the dial script. I think that the error message that you have been getting can be caused by trying to run a binary compiled for another platform. However, dial is a shell script and so should run on all platforms. You could try:
```
md5sum /etc/init.d/dial
```
if this doesn't produce
> c4b6dd0d627903b1601d2f49ee1f6978  /etc/init.d/dial
then there is probably a problem with the file if so post the contents of /etc/init.d.dial here. You could also try launching openoffice from the command line this might produce a useful error message.

---

### Post by orko3001 on 2006-11-25
> You could try
Code:
sudo pppd call speedtch


That worked and I am now writing to you from Ubuntu :mrgreen: 

But how do I create a button to connect to the internet rather than typing that code all the time. Also how do I start Openoffice from command line?

Here is my dial script with colours:

[COLOR="Blue"]#!/bin/bash[/COLOR]
[COLOR="Lime"]modprobe[/COLOR] ppp_generic
[COLOR="Lime"]modprobe[/COLOR] pppoatm
[COLOR="Cyan"]count[/COLOR]=0
[COLOR="Sienna"]while [[[/COLOR] $[COLOR="Lime"](([/COLOR]count++[COLOR="Lime"]))[/COLOR] [COLOR="Cyan"]-lt[/COLOR] 40 [COLOR="Sienna"]]][/COLOR]
[COLOR="Sienna"]do[/COLOR]
  [COLOR="Cyan"]sync=[/COLOR]$[COLOR="Lime"]([/COLOR]dmesg [COLOR="Lime"]| grep[/COLOR] [COLOR="Red"]'[/COLOR][COLOR="Magenta"]ADSL line is up[/COLOR][COLOR="Red"]'[/COLOR][COLOR="Lime"])[/COLOR]
  [COLOR="Sienna"]if [ ![/COLOR] [COLOR="Cyan"]-z[/COLOR] [COLOR="Magenta"]"$sync"[/COLOR] [COLOR="Sienna"]][/COLOR]
  [COLOR="Sienna"]then[/COLOR]
    pppd call speedtch
    [COLOR="Sienna"]exit[/COLOR] 0
  [COLOR="Sienna"]fi[/COLOR]
  [COLOR="Lime"]sleep[/COLOR] 1
[COLOR="Sienna"]done[/COLOR]
[COLOR="Sienna"]echo[/COLOR] [COLOR="Magenta"]"The SpeedTouch firmware did not load"[/COLOR]


What do the colours mean?

Thankyou for all your help :D

---

### Post by OLD WaterRat on 2006-12-16
:D :D  [FONT="Arial Black"][SIZE="5"][COLOR="Blue"][/COLOR][/SIZE][/FONT]THANK YOU THANK YOU fishpie

[FONT="Arial"][SIZE="3"][COLOR="Black"][/COLOR][/SIZE][/FONT]After reading this thread and following your instruction including the " sudo pppd call speedtch" bit like orko3001 I`m writing from Ubuntu.

You should add the "sudo pppd call speedtch" to the bottom of your original instruction and see if the MODS on this forum can make it a stickie. It was brill

Old WaterRat

---

### Post by GrahamPR on 2006-12-29
[QUOTE=orko3001;1804596]
But how do I create a button to connect to the internet rather than typing that code all the time. /QUOTE]

Woohoo! I am now too connected to the web, many many thanks to "fishpies" directions at bottom of page two. got very confused with the unpacking and command lines (even for an old DOS man), and found those instructions to be reasonably easy. easier than running up and downstairs between computers anyway. :D 

Orko, for the moment, I have simply edited the "secrets" file. I put an # infront of the current texts and put the sudo pppd call speedtch line in. ;)

I have a few more questions, I'll search first though. :D

edit: sorry, can I also delete the extractor and other miscellaneous file from my desktop now all the firmware etc is installed? needs a bit of a tidy up :O

---

