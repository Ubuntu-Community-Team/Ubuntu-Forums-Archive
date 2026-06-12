---
title: "[SOLVED] Remote control"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by e-tip on 2007-11-09
Hi all ,
I've read some howtos finded in this forum on how setup mactel with ubuntu.
After an easy setup i've managed to make work everything... but the remote control shipped with my new imac 24.
i've read that volume control should work out of the box but in my case it isn't true..:(
Like i've said mac is a new Imac 24" (the one with the black frame ) 
Any hint on how to make this work..... (i know this can seem stupid thing but i'd love to use to forward my presentation ;)  )

this is dmesg output
> 
[   35.395580] input: Apple Computer, Inc. IR Receiver as /class/input/input6
[   35.395584] input: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1


lsusb
> 
Bus 001 Device 004: ID 05ac:8206 Apple Computer, Inc. 
Bus 007 Device 005: ID 05ac:0221 Apple Computer, Inc. 
Bus 007 Device 006: ID 05ac:0304 Apple Computer, Inc. 
Bus 007 Device 003: ID 05ac:8502 Apple Computer, Inc. 
Bus 007 Device 002: ID 05ac:1006 Apple Computer, Inc. 
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc.  <-- this should be the ir reciver


cat special device outputs something for the first button pression, after that nothing happens

sudo cat /dev/input/by-id/usb-Apple_Computer__Inc._IR_Receiver-event-ir 
&#1924;4Gn&#65533;  <- this is first button pression output

---

### Post by e-tip on 2007-11-14
Hi all. i've been able to make my remote control work with ubuntu.
the problem was that reciver id was changed and appleir don't recognize it
if you have a new imac and want to use your remote control, you have to recompile appleir source code to do this 
Get the sources
```
apt-get source linux-ubuntu-modules-2.6.22-14-generic
```
this step will download two files in the pwd
```
tar zxvf linux-ubuntu-modules-2.6.22-14-generic.tar.gz 
```
cd into just created directory 
```
cd linux-ubuntu-modules-2.6.22-14-generic
```
Edit the sourcefile
```
gedit ubuntu/mactel/appleir.c
```
and change 
USB_DEVICE_ID_APPLE_IR  0x8240
into
USB_DEVICE_ID_APPLE_IR  0x8242 
Compile the modules and build a debian package
```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
(make sure you have write permission in parent directory)
this will create the new deb in parent directory 
install it 
```
dpkg -i linux-ubuntu-modules-2.6.22.14....deb
```
and then reload drivers
```
rmmod usbhid && modprobe appleir && modprobe usbhid;
```
MAKE ATTENTION TO TYPE THIS COMMANDS IN THE SAME LINE, IF NOT YOUR KEYBOARD AND MOUSE WON'T WORK 'TILL RESTART.

---

### Post by cyberdork33 on 2007-11-14
> **e-tip said:**
> Hi all. i've been able to make my remote control work with ubuntu.
the problem was that reciver id was changed and appleir don't recognize it
if you have a new imac and want to use your remote control, you have to recompile appleir source code to do this 
apt-get source linux-ubuntu-modules-2.6.22-14-generic
this step will download two files in the pwd
untar linux-ubuntu-modules-2.6.22-14-generic.tar.gz 
cd into just created directory and edit ubuntu/mactel/appleir.c
and change 
USB_DEVICE_ID_APPLE_IR  0x8240
into
USB_DEVICE_ID_APPLE_IR  0x8242 
then, in the main modules directory launch
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
(make sure you have write permission in parent directory)
this will create the new deb in parent directory 
install it with dpkg -i or anything you like
type (using root)
rmmod usbhid && modprobe appleir && modprobe usbhid;
MAKE ATTENTION TO TYPE THIS COMMANDS IN THE SAME LINE, IF NOT YOUR KEYBOARD AND MOUSE WON'T WORK 'TILL RESTART.

Please use the code tags:
Get the source
```
apt-get source linux-ubuntu-modules-2.6.22-14-generic
```
Building the new modules
```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
loading new module
```
rmmod usbhid && modprobe appleir && modprobe usbhid
```

---

### Post by jslmg on 2007-11-16
This is not working for me. I just installed Fakeroot in Terminal, cuz when I entered 
```
 AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
I got:
```
The program 'fakeroot' is currently not installed.  You can install it by typing:
sudo apt-get install fakeroot
bash: fakeroot: command not found

```

All appeared normal on installing Fakeroot, but then, when I reran the autobuild, I got:
```
/usr/bin/fakeroot: 166: debian/rules: not found
```

Advice?

---

### Post by jslmg on 2007-11-16
One thing is, I don't have an appleir.c file. Could someone send me one?

I suppose I'd have to use nano, not gedit, to make a new one?

After I have the proper appleir.c file, I may be on a better footing to proceed with this.

---

### Post by e-tip on 2007-11-16
Uhhhmm in wich directory you typed command ?

---

### Post by e-tip on 2007-11-16
supposing you gave command
```
apt-get source linux-ubuntu-modules-2.6.22-14-generic 
```
in your user directory /home/youruser
you have to type 
```
tar zxvf linux-ubuntu-modules-2.6.22-14-generic.tar.gz 
```
this will create a directory called linux-ubuntu-modules-2.6.22-14-generic
in /home/youruser
appleir is in
/home/youruser/linux-ubuntu-modules-2.6.22-14-generic/ubuntu/mactel/
if you need i can send you the precompiled and modifyed pacage...

---

### Post by jslmg on 2007-11-16
Thanks for responding, e-tip. Could you give me some more precise code info on where to go for the appleir.c, and then the autobuild command?

When using codes that posters give in ubuntuforums, my usual practice is just to open a terminal and paste the codes in, making no changes unless told to do so. That practice has worked most of the time. That's what I did in this case, following your instructions. Here is what I put in (I already have all linux-ubuntu modules installed, so I skipped that):

 ```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```

Would I need to CD somewhere first? Could you tell me the cd path? 

Thanks.

---

### Post by jslmg on 2007-11-16
OK, as you were posting your last reply, I was posting mine.

I'll retry the apt-get stuff, then cd to my home directory, and see what happens.

---

### Post by jslmg on 2007-11-16
As I suspected, when I cd to home/my-user-name/linux-ubuntu-modules-2.6.22-14-generic/ubuntu/mactel/, I get "No such file or directory."

I installed the linux-ubuntu modules through synaptic-the whole lot of 'em. They must be somewhere else...

---

### Post by e-tip on 2007-11-16
I've never used synaptic so i don't know if you can just get sources with it... but you don't need to install the package you need to get the source code for that package this is done with
```
apt-get source linux-ubuntu-modules-2.6.22-14-generic 
```

---

### Post by jslmg on 2007-11-16
Well, I found my appleir.c file. It was in the home/user directory after all. The folder is called "linux-ubuntu-modules-2.6.22-2.6.22". Hmmm.

I'll edit that appleir.c, then retry.

I may still have a problem with the AUTOBUILD with fakeroot. Is that still going to be in the home/user directory?

---

### Post by jslmg on 2007-11-16
OK, done up to install. E-tip, you provided:

```
dpkg -i linux-ubuntu-modules-2.6.22.14....deb
```.

Is that the complete code? Thanks again.

---

### Post by e-tip on 2007-11-16
yes but you have to susbstitute che dots with the complete filename
es the filename is 
```
linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_amd64.deb
```
you have to type 
```
dpkg -i linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_amd64.deb
```

and... you have to be in the same directory of the package

---

### Post by jslmg on 2007-11-16
> **e-tip said:**
> yes but you have to susbstitute che dots with the complete filename
es the filename is 
```
linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_amd64.deb
```
you have to type 
```
dpkg -i linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37_amd64.deb
```

and... you have to be in the same directory of the package

Are you running an amd64? Would that filename be the same on a macintel?

---

### Post by cyberdork33 on 2007-11-16
Type the command to the point that you don't know and hit TAB.

Auto complete is your friend:

```
dpkg -i linux-ubuntu-modules-2.6.22.14[TAB]
```

---

### Post by Levo75 on 2007-11-16
Does anyone know where the IR receiver is?

I don't see anything besides the iSight wich might be able to receive the IR signals.

---

### Post by cyberdork33 on 2007-11-17
> **Levo75 said:**
> Does anyone know where the IR receiver is?

I don't see anything besides the iSight wich might be able to receive the IR signals.
On my iMac it is behind the apple.

---

### Post by jslmg on 2007-11-20
Thanks, e-tip and Cyberdork. I'm just now getting back to Ubuntu to work on a few more things in it for the first time since the weekend.

It looks like the install took place fine. Now I'm trying to do rmmod, and I'm getting this message:

```
jslmg@Ubuntu:~$ sudo rmmod usbhid && modprobe appleir && modprobe usbhid
FATAL: Error inserting usbhid (/lib/modules/2.6.22-14-386/kernel/drivers/hid/usbhid/usbhid.ko): Operation not permitted
```

So, what have I missed?

---

### Post by e-tip on 2007-11-20
what does dmesg says ?

---

### Post by njpatel on 2008-02-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/157919](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/157919) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **e-tip said:**
> Hi all. i've been able to make my remote control work with ubuntu.
the problem was that reciver id was changed and appleir don't recognize it
if you have a new imac and want to use your remote control, you have to recompile appleir source code to do this.

Thanks, this worked perfectly for my Macbook Pro (3.1) as well.

Theres also a bug report on Launchpad for this. It'll be cool if we can get some momentum going over their so we don't need to do this on every install :-).

Regards,

Neil

---

### Post by tmas on 2008-02-16
Need some help..

After doing the 
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
in my home dir, it did look like it made the .dep file, but it isnt anywhere to be find!!

I saw that it build the package and everything, but cant find the file... What could I've done wrong?

Thomas

---

### Post by umeboshi on 2008-02-16
Hi all,

I've installed Ubuntu Gutsy 64 Bit edition on my MacBook Pro (Santa Rosa) and I'm trying to get my IR receiver working. I've followed all the steps described by e-tip:
>  
apt-get source linux-ubuntu-modules-2.6.22-14-generic
tar zxvf linux-ubuntu-modules-2.6.22-14-generic.tar.gz
cd linux-ubuntu-modules-2.6.22-2.6.22 
gedit ubuntu/mactel/appleir.c and change USB_DEVICE_ID_APPLE_IR 0x8240 into USB_DEVICE_ID_APPLE_IR 0x8242
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic


During the execution of the last command I get following error message:

make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
dh_testdir
/bin/bash: dh_testdir: command not found
make: *** [install-generic] Error 127

Do you know how to solve this issue? I don't know much about compiling kernel modules so I'm stuck here.

Any tip is much appreciated.

Regards,
umeboshi

---

### Post by cyberdork33 on 2008-02-16
I think you need to install fakeroot still.

---

### Post by umeboshi on 2008-02-17
Hi Cyberdork33,

The package fakeroot was already installed. It was the package debhelper which was missing. After installing it I was able to finish the compilation.
I have now installed the deb file and my  remote control is working now.

Thanks for your help and thanks to e-tip for his work.

Kind regards,
umeboshi

---

### Post by tmas on 2008-02-22
Need to bump this up again...

I dont get this to work at all..
Actually my apple remote dont even work on the volume! lsusb and dmesg finds the remote, but I`m not able to find it when I cat everything in /dev/input ..!
How can I check that ir actually works in ubuntu? It does in mac os.

And of course did I try to change the appleir.c and recompile it all..

---

### Post by ivelasco on 2008-02-26
> **tmas said:**
> Need to bump this up again...

I dont get this to work at all..
Actually my apple remote dont even work on the volume! lsusb and dmesg finds the remote, but I`m not able to find it when I cat everything in /dev/input ..!
How can I check that ir actually works in ubuntu? It does in mac os.

And of course did I try to change the appleir.c and recompile it all..



I have a Macbook Pro santarosa,and I am in the same situation.I also change the appleair.c ,recompile  and modprobe with success,but nothing happens when I press the remote controller buttons,why?The controller is well detected:

```
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x8242 
  bcdDevice            0.16
  iManufacturer           1 Apple Computer, Inc.
  iProduct                2 IR Receiver
  iSerial                 0 
  bNumConfigurations      1

```



My .lircrc is as follows:
```
##################################################
#### Change mode ####
## If anyone can make this work (in example: pressing a button some time please notify us ##
##################################################

#begin
# prog = irexec
# button = KEY_PLAYPAUSE
# mode = amarok
# config = echo "Modo amarok"
#end
#
#begin
# prog = irexec
# button = KEY_NEXTSONG
# mode = kaffeine
# config = echo "Modo kaffeine"
#end
#begin
# prog = irexec
# button = KEY_PREVIOUSSONG
# mode = kaffeine
# config = echo "Modo kaffeine"
#end


#############
#### VLC ####
#############

begin
prog = vlc
button = KEY_PLAYPAUSE
config = key-play-pause
repeat = 0
end

begin
prog = vlc
button = KEY_MENU
config = key-stop
repeat = 0
end

begin
prog = vlc
button = KEY_PREVIOUSSONG
config = key-jump-1min
repeat = 1
end

begin
prog = vlc
button = KEY_NEXTSONG
config = key-jump+short
repeat = 1
end
begin
prog = vlc
button = KEY_VOLUMEUP
config = key-vol-short
repeat = 1
end

begin
prog = vlc
button = KEY_VOLUMEDOWN
config = key-vol-down
repeat = 1
end


#################
#### MPlayer ####
#################

#begin mplayer
begin
prog = mplayer
button = KEY_PLAYPAUSE
config = pause
repeat = 15
end

begin
prog = mplayer
button = KEY_MENU
config = stop
repeat = 15
end

begin
prog = mplayer
button = KEY_PREVIOUSSONG
config = seek -10
repeat = 10
end

begin
prog = mplayer
button = KEY_NEXTSONG
config = seek +10
repeat = 10
end
begin
prog = mplayer
button = KEY_VOLUMEUP
config = volume 1
repeat = 1
end

begin
prog = mplayer
button = KEY_VOLUMEDOWN
config = volume -1
repeat = 1
end
#end mplayer


##################
#### Kaffeine ####
##################

#begin kaffeine
begin
prog = irexec
button =
config = dcop kaffeine MainApplication-Interface
end

begin
prog = irexec
button = KEY_PLAYPAUSE
config = if `dcop kaffeine KaffeineIface isPlaying`; then dcop kaffeine KaffeineIface pause; dcop kaffeine kaffeine_mainview hide; else dcop kaffeine KaffeineIface play; dcop kaffeine kaffeine_mainview hide; fi
end

begin
prog = irexec
button = KEY_MENU
repeat = 1
config = dcop kaffeine KaffeineIface stop
end

begin
prog = irexec
button = KEY_NEXTSONG
repeat = 1
config = dcop kaffeine KaffeineIface posPlus
end

begin
prog = irexec
button = KEY_PREVIOUSSONG
repeat = 1
config = dcop kaffeine KaffeineIface posMinus
end

begin
prog = irexec
button = KEY_VOLUMEUP
repeat = 1
config = dcop kaffeine KaffeineIface volUp
end

begin
prog = irexec
button = KEY_VOLUMEDOWN
repeat = 1
config = dcop kaffeine KaffeineIface volDown
end

#end kaffeine


################
#### Amarok ####
################

#begin amarok
begin
prog = irexec
button = KEY_PLAYPAUSE
config = dcop amarok player playPause
end

begin
prog = irexec
button = KEY_MENU
config = dcop amarok player stop
end

begin
prog = irexec
button = KEY_NEXTSONG
config = dcop amarok player next
end

begin
prog = irexec
button = KEY_PREVIOUSSONG
config = dcop amarok player prev
end

begin
prog = irexec
button = KEY_VOLUMEUP
repeat = 1
config = dcop amarok player volumeUp
end

begin
prog = irexec
button = KEY_VOLUMEDOWN
repeat = 1
config = dcop amarok player volumeDown
end
#end amarok


###############
#### Totem ####
###############

begin
prog = irxevent
button = KEY_PLAYPAUSE
config = Key p Totem
repeat = 0
end

begin
prog = irexec
button = KEY_MENU
config = stop
repeat = 0
end

begin
prog = Totem
button = KEY_NEXTSONG
config = seek_forward
repeat = 0
end

begin
prog = Totem
button = KEY_PREVIOUSSONG
config = seek_backward
repeat = 0
end

begin
prog = irexec
button = KEY_VOLUMEUP
repeat = 10
config =
end

begin
prog = irexec
button = KEY_VOLUMEDOWN
repeat = 10
config =
end



###################
#### Audacious ####
###################

begin
prog = audacious
button = KEY_PLAYPAUSE
config = PAUSE
repeat = 16
end

begin
prog = audacious
button = KEY_MENU
config = STOP
repeat = 0
end

begin
prog = audacious
button = KEY_NEXTSONG
config = NEXT
repeat = 16
end

begin
prog = audacious
button = KEY_PREVIOUSSONG
config = PREV
repeat = 16
end


##############
#### XMMS ####
##############

begin
prog = xmms
button = KEY_PLAYPAUSE
config = pause
end

begin
prog = xmms
button = KEY_MENU
config = stop
end

begin
prog = xmms
button = KEY_NEXTSONG
config = next
repeat = 16
end

begin
prog = xmms
button = KEY_PREVIOUSSONG
config = prev
repeat = 16
end

begin
prog = xmms
button = KEY_VOLUMEUP
config = fwd 5
repeat = 10
end

begin
prog = xmms
button = KEY_VOLUMEDOWN
config = bwd 5
repeat = 10
end


###############
##### XdTV ####
###############

begin
prog = irexec
button = KEY_PLAYPAUSE
config = record
repeat = 0
end

begin
prog = irexec
button = KEY_PREVIOUSSONG
config = setstation prev
repeat = 0
end

begin
prog = irexec
button = KEY_NEXTSONG
config = setstation next
repeat = 0
end

################
#### TVtime ####
################

#begin tvtime

begin
prog = irexec
button = KEY_PLAYPAUSE
config = tvtime-command ENTER
end

begin
prog = irexec
button = KEY_MENU
config = tvtime-command TOGGLE_FULLSCREEN
end

begin
prog = irexec
button = KEY_NEXTSONG
config = tvtime-command UP
repeat = 1
end
begin
prog = irexec
button = KEY_PREVIOUSSONG
config = tvtime-command DOWN
repeat = 1
end
begin
prog = irexec
button = KEY_VOLUMEUP
config = tvtime-command RIGHT
repeat = 2
end
begin
prog = irexec
button = KEY_VOLUMEDOWN
config = tvtime-command LEFT
repeat = 2
end

#begin
# prog = irexec
# button = middle
# config = tvtime-command CHANNEL_JUMP
# repeat = 1
#end

#end tvtime


################################################## ##############################
#### Turn up and down the volume (Working by default on Feisty) ####
################################################## ##############################

#begin
#prog = irexec
#button = KEY_VOLUMEUP
#config = amixer set PCM 9+ & #amixer set PCM 3%+ &
#repeat = 2
#end
#begin
#prog = irexec
#button = KEY_VOLUMEDOWN
#config = amixer set PCM 9- & #amixer set PCM 3%- &
#repeat = 2
#end

##############################################
#### Evince y OpenOffice (Presentations) ####
##############################################

begin
prog = irxevent
button = KEY_PLAYPAUSE
config = Key F11 CurrentWindow
config = Key F5 CurrentWindow
repeat = 0
end

begin
prog = irxevent
button = KEY_MENU
config = Key Escape CurrentWindow
repeat = 0
end

begin
prog = irxevent
button = KEY_PREVIOUSSONG
config = Key Prior CurrentWindow
repeat = 1
end

begin
prog = irxevent
button = KEY_NEXTSONG
config = Key Next CurrentWindow
repeat = 1
end

begin
prog = irxevent
button = KEY_VOLUMEUP
config = Key ctrl-plus CurrentWindow
repeat = 0
end

begin
prog = irxevent
button = KEY_VOLUMEDOWN
config = Key ctrl-minus CurrentWindow
repeat = 0
end

```

as I copy and paste from this forums.

This is my /etc/lirc/hardware.conf:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER="dev/input"
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
#DEVICE="/dev/input/event1"
DEVICE="/dev/input/by-path/pci-0000:00:1d.2-usb-0:1:1.0-event-ir"
MODULES=""

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

And finally the /etc/lirc/lirccd.conf:

```
begin remote

  name  lircd.conf
  bits            8
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   24
  pre_data       0x800100
  gap          132990
  toggle_bit_mask 0x800100A4

      begin codes
          NEXT                     0xA3
          PREV                     0xA5
          PLUS                     0x73
          MINUS                    0x72
          PLAY                     0xA4
          MENU                     0x8B
      end codes

end remote
```


Any help would be apreciated.This is the only one hard piece that doesn't work for me

---

### Post by e-tip on 2008-02-26
> How can I check that ir actually works in ubuntu? It does in mac os.

The only way you can check if the remote works is to cat the corresponding device... 
You can check the associated device with an sudo lsinput and check for an entry like this 
/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x5ac
   product : 0x8242
   version : 273
   name    : "Apple Computer, Inc. IR Receiver"
   phys    : "usb-0000:00:1d.2-1/input0"
   uniq    : ""
   bits ev : EV_SYN

have you loaded the appleir before usbhid module ?

---

### Post by e-tip on 2008-02-26
> **ivelasco said:**
> I have a Macbook Pro santarosa,and I am in the same situation.I also change the appleair.c ,recompile  and modprobe with success,but nothing happens when I press the remote controller buttons,why?The controller is well detected:


I didn't used lirc to use my remote. i've set it in System->preferences->keyboard-shortcuts
if you manage to make lirc work let me know please

---

### Post by robzon on 2008-03-21
If you really don't want to recompile the module you can simply use any hex editor to change the bytes in the appleir.ko module file from::

ac 05 40 82

to

ac 05 42 82

and reload the module (unload usbhid and load appleir and usbhid).
works great for me, I just hope we'll get it fixed in hardy on time.

---

### Post by robzon on 2008-03-22
Oh, and if you accidentaly unload the usbhid module and your mouse and keyboard stop working - don't panic. Just unplug the mouse and plug it in again - the kernel will automatically load the usbhid module back and you'll be able to continue your work without rebooting the machine.

---

### Post by stueng on 2008-05-18
Hey guys,

I've managed to get the remote control working by using the above modules dpkg steps and its working fine for volume and changing songs in Rythmbox and Totem

How do I get it to work in VLC??

Stu

---

### Post by e-tip on 2008-05-19
Well, i didn't manage to....:(
i can use it to raise up volume, i can use it in amarok, 
but in vlc i didn't..
if i can find time i'll take a look at that

---

### Post by stueng on 2008-05-20
ok thanks, keep us posted if you get it working, i'll do the same

---

### Post by e-tip on 2008-05-20
The best thing would be to make it work under lirc, that have the possibility to configure lot of softwares, but i didn't manage to make it work

---

### Post by cyberdork33 on 2008-05-20
If you would like to get more attention on your problem, try posting in the new Apple Forum as this is just an archive.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by heap on 2008-07-01
> **jslmg said:**
> Thanks, e-tip and Cyberdork. I'm just now getting back to Ubuntu to work on a few more things in it for the first time since the weekend.

It looks like the install took place fine. Now I'm trying to do rmmod, and I'm getting this message:

```
jslmg@Ubuntu:~$ sudo rmmod usbhid && modprobe appleir && modprobe usbhid
FATAL: Error inserting usbhid (/lib/modules/2.6.22-14-386/kernel/drivers/hid/usbhid/usbhid.ko): Operation not permitted
```

So, what have I missed?


I guess you've already managed to sort this out, however (for the record) try 

```
 sudo rmmod usbhid && sudo modprobe appleir && sudo modprobe usbhid;
```

---

### Post by stueng on 2008-07-01
the above step doesnt work, for some reason the modprobe part doesnt execute as su; I type sudo -s (which takes you to a root terminal) and then execute the command to get around this problem

Details here: [http://www.lostpeg.co.uk/content/view/37/79/]("http://www.lostpeg.co.uk/content/view/37/79/")

---

