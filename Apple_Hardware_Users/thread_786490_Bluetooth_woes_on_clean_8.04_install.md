---
title: "Bluetooth woes on clean 8.04 install"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by sunbird on 2008-05-08
Hi all, I did a clean install of 8.04 and most everything is working great, but I can't get bluetooth to work.

I tried reinstalling bluetooth and bluez-utils, but still not there. Also, no panel applet.

```

 * Starting bluetooth                                    [ OK ] 
Searching ...
	No devices in range or visible

```

This is what /var/log/daemon.log has to say:

```

May  8 15:04:48 NetworkManager: <debug> [1210241088.226409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_76167a114'). 
May  8 15:04:48 hidd[9025]: Rejected connection from unknown device xxxxx
May  8 15:04:49 hidd[9025]: Rejected connection from unknown device xxxxx
May  8 15:04:54 NetworkManager: <debug> [1210241094.988125] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_76167a114'). 
May  8 15:05:10 NetworkManager: <debug> [1210241110.244737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_76167a114'). 
May  8 15:05:10 hidd[9025]: Rejected connection from unknown device xxxxx

```

I'd really like to get my mouse working. Any help?

**Edit:** Might as well post my hcid.conf:

```

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
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1357";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

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
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
device xxxxxx {
    name "Apple Wireless Keyboard";
    auth enable;
    encrypt enable;
}

device xxxxxxx {
    name "mouse";
    auth enable;
    encrypt enable;
}

device xxxxx {
    name "phone";
    auth enable;
    encrypt enable;
}

```

And my /etc/default/bluetooth (only changes from default is to change HIDD_ENABLED to 1):

```

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HID2HCI_ENABLED=1

############ HIDD
#
# HID daemon
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
# in later versions of pand it used to execute /etc/bluetooth/pan/dev-up
# automatically, now you will need to use the --devup/--devdown options. See
# the pand manpage for more informations
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""

```

---

### Post by emmeelle on 2008-05-08
Mee too have a problem with bluetooth.

I can't use it.

This is hcitool scan output:

hcitool scan
Scanning ...
Inquiry failed: Connection timed out

---

### Post by sunbird on 2008-05-10
*Bump*

Any help on this? Obviously, everyone isn't having this trouble, so I'm sure there's a way to get it working.

---

### Post by cyberdork33 on 2008-05-10
> **sunbird said:**
> Any help on this? Obviously, everyone isn't having this trouble, so I'm sure there's a way to get it working.
Yes, but bluetooth should "just work" there is no configuration required... (not supposed to be anyway).

---

### Post by sunbird on 2008-05-10
Hurm.... well, it doesn't "just work," unfortuantely, and I'm at a loss for how to proceed. Should I do an apt-get remove --purge bluetooth bluez-utils and then apt-get install bluetooth bluez-utils to get back to the default config and try over? 

Bluetooth sees my devices:

```

$ hcitool scan
Scanning ...
	xxxxxxxxxxxxxxxxx	keyboard
	xxxxxxxxxxxxxxxxx	mouse

```

But when I try to connect to my keyboard I get an input/output error after entering the password defined in /etc/bluetooth/hcid.conf:

```

$ sudo hcitool cc xxxxxxxxxxxxxxx
Can't create connection: Input/output error

```

The command appears to run successfully for my mouse, but the mouse doesn't work and bluetooth shows no active connections:

```

$ sudo hcitool cc xxxxxxxxxxxxxxxx
$ hcitool con
Connections:
$ 

```

Should I file a bug report on launchpad? Again, this is a clean install, so I'm at a loss for the cause of the problem. All these devices worked fine in 7.10.

---

### Post by cyberdork33 on 2008-05-10
well if you can scan and see devices then your bluetooth is "just working" you just cannot connect to devices. You are not supposed to edit those files anymore, just use the bluetooth applet to connect to devices... I cannot get it to work with my Apple keyboard either. There were several bugs found in the new bluetooth system in the Hardy betas but they didn't get fixed.

There is a lot of info in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/191704](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/191704)

---

### Post by sunbird on 2008-05-11
Hmmm... well, I think your definition of working is different than mine. ;) 

But thanks for the link to the bug report, downgrading to gutsy's bluez-utils, connecting my mouse there, and then upgrading back to the current version fixed my problem (more detailed description [here]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/191704/comments/50"). I didn't try it with the keyboard, but I mostly use the mouse anyway.

This can be marked solved.

---

### Post by russo.mic on 2008-05-11
guys,  with kubuntu I found that i have to use this command

sudo hidd scan

That finds my mouse, and connects.  What is wierd is that without doing that, the bluetooth daemon just keeps on popping up with it's connected message over and over again.  Once I run that command ONCE, it works fine forever. I think what is happening is that the daemon's permissions aren't setup correctly, and it can't write to some conf. file it needs to...just a guess.

Russo

---

### Post by russo.mic on 2008-05-11
guys,  with kubuntu I found that i have to use this command

sudo hidd scan

That finds my mouse, and connects.  What is wierd is that without doing that, the bluetooth daemon just keeps on popping up with it's connected message over and over again, with the mouse not working.  Once I run that command ONCE, it works fine forever. I think what is happening is that the daemon's permissions aren't setup correctly, and it can't write to some conf. file it needs to...just a guess.

Russo

---

### Post by russo.mic on 2008-05-11
sorry for the double post, not quite sure how i did that!

Russo

---

### Post by cyberdork33 on 2008-05-11
> **sunbird said:**
> Hmmm... well, I think your definition of working is different than mine. ;) 
You made it sound like you bluetooth radio in your machine did not work at all... this wasn't the case. you had a problem connecting to devices.

---

### Post by jca96328 on 2008-06-02
Try [http://blueman.tuxfamily.org](http://blueman.tuxfamily.org)

Works fine for me if only I could get the keyboard to automatically pair.

---

### Post by cyberdork33 on 2008-06-02
> **jca96328 said:**
> Try [http://blueman.tuxfamily.org](http://blueman.tuxfamily.org)

Works fine for me if only I could get the keyboard to automatically pair.
Cool! I will have to check this out.

---

### Post by matthewcraig on 2008-06-26
These two threads may be of assistance to you:
[http://ubuntuforums.org/showthread.php?t=830383](http://ubuntuforums.org/showthread.php?t=830383)
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

---

### Post by bailewen on 2008-08-12
Been fighting with this thing for months. 

It's the one reason I have never been able to switch completely to linux. No bluetooth. Doesn't matter how cool this os is, no bluetooth is a dealbreaker for me. That means no wireless stereo headset, no skype without sitting at my desk. Lots of general suckiness that forces me to keep windows on a separate partition more than half the time.

I tried the blueman thing. Nothing.
I tried the various utilities on this thread. Nothing.

It only finds my bluetooth dongle but is not able to find any devices...at all. The command lines posted on this thread just time out without finding my headset and the blueman utility says simply "failed to start inquiry".

This thing is seriously annoying.

---

### Post by cyberdork33 on 2008-08-12
> **bailewen said:**
> Been fighting with this thing for months. 

It's the one reason I have never been able to switch completely to linux. No bluetooth. Doesn't matter how cool this os is, no bluetooth is a dealbreaker for me. That means no wireless stereo headset, no skype without sitting at my desk. Lots of general suckiness that forces me to keep windows on a separate partition more than half the time.

I tried the blueman thing. Nothing.
I tried the various utilities on this thread. Nothing.

It only finds my bluetooth dongle but is not able to find any devices...at all. The command lines posted on this thread just time out without finding my headset and the blueman utility says simply "failed to start inquiry".

This thing is seriously annoying.
if your dongle is recognized, then, when you put your headset into discover mode, then you should see the device with "hidd --search". If you cannot get that to find your device, then it is likely not in the correct mode.

---

### Post by bailewen on 2008-08-13
"hcitool dev"  yields the following output:  hci0	00:0A:3A:82:40:11

So that, I assume, is my dongle. When I try to search for my headset via blueman it tells me: "device or resource busy". If I try using the command prompt by typing, "sudo hcitool scan" it says "scanning..." for a while and then says, "Inquiry failed: Connection timed out"

The headset is not new to me. I have been using it smoothly on 3 different cell phones so far and *drum roll*....WINDOWS XP, without incident. You turn it on, listen for the tell tale beeping pattern and look at the pretty blue light that indicates it is in pairing mode. So far, Linux is the only software that has not seen it. I have tried paring my cell phone to my laptop as well but the thing just wont search at all in blueman and in the command prompt it acts like its searching but never finds anything. 

Listening to music and making VOIP phone calls probably make up nearly half of all that I use my laptop for. They are a BIG deal to me. I was really hoping that with the latest Ubuntu, Hardy, the bluetooth issue would have finally been solved. Its the only thing left for me that really doesn't work. Sadly, it's just a hair less important than Linux recognizing my mouse and being able to connect to wireless networks relatively easily.

---

### Post by cyberdork33 on 2008-08-13
> **bailewen said:**
> Listening to music and making VOIP phone calls probably make up nearly half of all that I use my laptop for. They are a BIG deal to me. I was really hoping that with the latest Ubuntu, Hardy, the bluetooth issue would have finally been solved. Its the only thing left for me that really doesn't work. Sadly, it's just a hair less important than Linux recognizing my mouse and being able to connect to wireless networks relatively easily.Well, since it sounds like you definitely know what you are doing, you might try something like this:
[http://ubuntuforums.org/showthread.php?p=4486290](http://ubuntuforums.org/showthread.php?p=4486290)

I had big issues with hardy. It actually seemed to break bluetooth more than help it. My wireless keyboard still doesn't work right, and this bug is still not addressed either. Good luck.

---

### Post by bailewen on 2008-08-13
heh....

So does blueman seem to work better on Gutsy? It's a big enough problem that I would totally consider going back. It would be the first time I have ever gone back to an older version of Ubuntu. In every other aspect the OS has gotten better, more stable and requiring less tweaking as new editions come out. In 6.x I never did get wireless working. In Hardy it lights right up (with some very minor bugs not worth going into here) The media players all handle 100G databases better than before and combining Beryl, which is what really sold me on Ubuntu, into Compiz, well that made it stable and FAR easier to install. 

This bluetooth thing is really vexing me. Thanks for the new lead on how to fix it. I haven't read the new thread yet but at least it explains why all the other howto's I had found didn't seem to help.

---

### Post by cyberdork33 on 2008-08-13
> **bailewen said:**
> So does blueman seem to work better on Gutsy?I didn't even know about it when I was on Gutsy... 

> **bailewen said:**
> In every other aspect the OS has gotten better, more stable and requiring less tweaking as new editions come out.You are just scraping the surface. What is available in Hardy is the result of a LOT of people complaining about bluetooth during testing. It is better than their original intent... they were going to just leave out the hidd binary completely and the directions they gave to connect a mouse was "move it around a little, and it will connect". Great...

---

### Post by bailewen on 2008-08-14
&#65293;never mind- just more griping in that post anyways.

---

### Post by bailewen on 2008-08-15
....so I had been trying desparately to avoid getting down and dirty in command prompt but after googling around a bit I decided to try and do it the old fasioned way. I had installed all the various bluetooth utilities through Synaptec before but now I get these stupid tarballs to wrestle with but, of course, I learned something.

When running "./configure" while in the folder for the /bluez-gnome-0 folder it tells me, after a long readout of junk I can't understand:

checking for update-desktop-database... /usr/bin/update-desktop-database
checking for update-mime-database... /usr/bin/update-mime-database
checking for gtk-update-icon-cache... /usr/bin/gtk-update-icon-cache
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DBUS... yes
checking for HAL... no
checking for GTK... no
configure: error: gtk+ >= 2.10 is required

How can I install GTK. Searching Synaptec is too vague. There's 100's of packages with "GTK" in their name. What am I supposed to install?

---

### Post by cyberdork33 on 2008-08-15
> **bailewen said:**
> How can I install GTK. Searching Synaptec is too vague. There's 100's of packages with "GTK" in their name. What am I supposed to install?

I guess you are trying to compile a newer version of bluez-gnome than is in Ubuntu? Anyway, you compile, you must have all the -dev packages (header files) for the libraries that what you are trying to compile depends on. so you can search through synaptic for each one.... or you can use:
```
sudo apt-get build-dep bluez-gnome
```That should install all the dependencies for bluez-gnome. (At least the version in the Ubuntu repos). If it requires a library that is newer than what is in the repos, well, then it's another story. You will also want to make sure that you install the 'build-essential' package before compiling anything.

---

### Post by bailewen on 2008-08-15
No. I'm just trying to get my bluetooth headset paired up. So far (spent at least a dozen entire evenings struggling with this one) no luck. 

After running the ./configure file in the latest bluez utilities tarball it says:

> configure: error: gtk+ >= 2.10 is required

See my previous post. I could care less what sort of GTK is in my box. I am just trying every damn way I can to get the thing to recognize, well...any bluetooth device at all. hcitools scan just times out. It doesn't see my cell phone or my headset. Nothing, nada. Bupkis. 

This thing sucks. Doesn't "just work" at all. Doesn't even work after spending countless hours on the web researching, online trying different packages, using blueman, kbluetooth or any other gui I have been able to find. I don't want to deal with command prompt at all. I'm just desparate to get my linux box working.

---

### Post by cyberdork33 on 2008-08-15
> **bailewen said:**
> No. I'm just trying to get my bluetooth headset paired up. So far (spent at least a dozen entire evenings struggling with this one) no luck. 

After running the ./configure file in the latest bluez utilities tarball it says:



See my previous post. I could care less what sort of GTK is in my box. I am just trying every damn way I can to get the thing to recognize, well...any bluetooth device at all. hcitools scan just times out. It doesn't see my cell phone or my headset. Nothing, nada. Bupkis. 

This thing sucks. Doesn't "just work" at all. Doesn't even work after spending countless hours on the web researching, online trying different packages, using blueman, kbluetooth or any other gui I have been able to find. I don't want to deal with command prompt at all. I'm just desparate to get my linux box working.for some reason that is not coming up in build-dep... I think the package you need is libgtk2.0-dev:
```
sudo apt-get install libgtk2.0-dev
```
You probably still need to get other dpendencies as well, so make sure to do
```
sudo apt-get build-dep bluez-utils
```
Are you on a Mac? (This is an Apple forum... If not on a Mac, you might want to try a different forum.)

---

### Post by bailewen on 2008-08-15
Oh...yeah. I'm not on a Mac. I got to this thread by searching "bluetooth". I've been on at least 3 or 4 bluetooth related threads so far. 

Trying to get help any way I can. Been trying to get bluetooth sound to work through 2 different distrubutions of an on over the past couple years. I work on it a few weeks. Give up. Go back to windows and then come back and try again when the next distro comes out. This time I am giving Linux another try because blueman looked like maybe the issue had finally been solved. The screenshots look pretty comparable to bluesoleil and having installed and run it, it looks like kind of the same sort of thing except...

it doesn't work. :(

---

### Post by cyberdork33 on 2008-08-15
> **bailewen said:**
> it doesn't work. :(
Unfortunately, in your case it sounds more like an actual hardware (dongle) incompatibility... You should probably file a bug report.

---

### Post by goodluckguys on 2008-08-15
MOVING? ivansmoving.narod.ru LOW PRICES!!!

---

### Post by mabovo on 2008-08-16
Ok, not to want spam this thread, but I am trying to connect with a smartphone Samsung SGH-i710 that uses ActiveSync to connect in Windows but in Linux using Bluethooth I get 

> mabovo@macbook:~$ hcitool scan
Scanning ...
	00:17:D5:6D:F1:86	Pocket_PC
mabovo@macbook:~$ dbus-send --system --type=method_call --print-reply --dest=org.bluez /org/bluez org.bluez.Manager.ActivateService string:input
method return sender=:1.32 -> dest=:1.38 reply_serial=2
   string ":1.34"
mabovo@macbook:~$ dbus-send --system --type=method_call --print-reply --dest=":1.34" /org/bluez/input org.bluez.input.Manager.CreateDevice string:00:17:D5:6D:F1:86
Error org.bluez.Error.NotSupported: Not supported
mabovo@macbook:~$ 


I just got it from tech assist reparing with update in windows mobile and the firmware.

It is just the device that doesn't connect or something with Linux ?

Thanks for any help.

---

### Post by cyberdork33 on 2008-08-16
> **mabovo said:**
> Ok, not to want spam this thread, but I am trying to connect with a smartphone Samsung SGH-i710 that uses ActiveSync to connect in Windows but in Linux using Bluethooth I get 

I just got it from tech assist reparing with update in windows mobile and the firmware.

It is just the device that doesn't connect or something with Linux ?

Thanks for any help.
If you are following the commands in that thread I posted, those are really specifically for input devices. I got all that info off of wiki.bluez.org. Have you just tried using "Browse Device..." from the applet?

[http://wiki.bluez.org/wiki/HOWTO](http://wiki.bluez.org/wiki/HOWTO)

---

### Post by mabovo on 2008-08-16
> **cyberdork33 said:**
> If you are following the commands in that thread I posted, those are really specifically for input devices. I got all that info off of wiki.bluez.org. Have you just tried using "Browse Device..." from the applet?

[http://wiki.bluez.org/wiki/HOWTO](http://wiki.bluez.org/wiki/HOWTO)

Using Blueman I got it inquired as Pocket PC and could send some files.
It was my misunderstood trying to connect it to access internet as a modem.

---

### Post by bailewen on 2008-08-17
Bought another dongle yesterday. Voicestar at Radio Shak. Problem solved . . . finally. 


See. It's a Mac user thread but the answer was still here. I'm only a little dissaopointed because:

1. I had to spend another 40 bucks to get a more mainstream dongle.

2. The original dongle I had was really tiny. It only stuck out about a 1/3 of an inch from the USB port and that is a really good feature when you are on a laptop and always afraid you are going to snap the damn thing off. 

Still though, with bluetooth music (haven't tested skype yet) I think I really have no reasons left to go back to windows this time. Yipee!

---

### Post by cyberdork33 on 2008-08-17
> **bailewen said:**
> Bought another dongle yesterday. Voicestar at Radio Shak. Problem solved . . . finally. 


See. It's a Mac user thread but the answer was still here. I'm only a little dissaopointed because:

1. I had to spend another 40 bucks to get a more mainstream dongle.

2. The original dongle I had was really tiny. It only stuck out about a 1/3 of an inch from the USB port and that is a really good feature when you are on a laptop and always afraid you are going to snap the damn thing off. 

Still though, with bluetooth music (haven't tested skype yet) I think I really have no reasons left to go back to windows this time. Yipee!

Apparently your old dongle is not woorking with bluetooth now. I would file a bug with details about the hardware, and hopefully someone can help support it in the future!

---

### Post by bailewen on 2008-08-20
How do I do that? The other dongle is both cheaper and better. I don't know about the range on it but a dongle that doesn't stick out from the side of the laptop is a big benifit to me. 

I noticed that under "device info" in the bluez utilities, on the non-compatable dongle, there is a whole lot of nothing. How do I try and find usefull info for eager programmers to work into bluez and where do I post it / report a bug?

---

### Post by cyberdork33 on 2008-08-20
> **bailewen said:**
> How do I do that? The other dongle is both cheaper and better. I don't know about the range on it but a dongle that doesn't stick out from the side of the laptop is a big benifit to me. 

I noticed that under "device info" in the bluez utilities, on the non-compatable dongle, there is a whole lot of nothing. How do I try and find usefull info for eager programmers to work into bluez and where do I post it / report a bug?

After plugging the device, you can find the hardware info with 'lsusb'. You will probabaly want to get a verbose output (lsusb -v) and try to get it for your specific device. You can read the options under 'lsusb --help' to figure that out.

Ubuntu bugs can be filed in launchpad (launchpad.net). Create an account, make sure to choose the Ubuntu project (there are others too) and file the bug. try to provide a lot of info about your system, and describe the issue you are having. You will also have to choose a package that the bug affects. You might try 'linux' and 'bluez-gnome'.

---

### Post by bailewen on 2008-08-21
Thanks. I'l check it out.

---

### Post by jbor7755 on 2008-08-24
Russo knows what's what!

sudo hidd scan

worked for me too (again using Kubuntu 8.04 (64bit)).

DONE!

---

### Post by sayad on 2008-08-24
oh man forget it , blutooth devices are scrap.
I aint used blutooth for ubuntu but still you see ,, i have changed around 5 blutooth devices using them on the pc.
it is surely problme with your blutooth device.

---

### Post by Chucklz15 on 2008-08-26
Hi all, I'm having the exact same problem but I don't understand what you guys are saying (I'm still windows savy). could you describe it in words I can understand?

---

### Post by cyberdork33 on 2008-08-26
> **Chucklz15 said:**
> Hi all, I'm having the exact same problem but I don't understand what you guys are saying (I'm still windows savy). could you describe it in words I can understand?
since you are on ppc (if i remember correctly), you may be in a slightly different boat. I would also start a different thread and be sure to state what you are trying to do (exactly), what you have tried, and what hardware you have.

---

