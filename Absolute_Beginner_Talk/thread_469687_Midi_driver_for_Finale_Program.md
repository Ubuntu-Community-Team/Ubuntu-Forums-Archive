---
title: "Midi driver for Finale Program"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-10
Hi,
I am venturing out into the unknown - I have actually successfully (so far) installed Finale 2007 (Music notation program) using wine. (FYI, CrossOver wouldn't install it - there wasn't the right Windows version or Windows reference there.) 

What I would normally do in Windows now is install an M-Audio Midi driver that allows me to hook my keyboard up via usb and "punch" notes into the Finale program to make a music chart. 

I know that there are many Midi programs (eg, Ubuntu Studio has tons, like Rosegarden) in Linux. But is there a chance someone might know the type of midi I'm wanting to employ here and could anyone suggest the Right Midi program? 

For instance, I'm Not wanting to do Midi Sequencing here... that's a whole 'nother area in Midi. I simply want a Midi In/Midi Out type scenario where my keyboard will be recognized as midi by the computer and by Finale.

I really appreciate any help or pointers.  Many Thanks, Frank B.

---

### Post by coffeecat on 2007-06-10
I don't really have much of an answer, but I thought I would respond with a few thoughts, some of which might be useful.

First of all. I bow to your patience and tenacity in being able to get Finale to work at all. I tried it once a few years ago. :evil: Never again. Never again. :(

I use Capella in Windows but it won't play ball with wine and this app is about the only reason I still keep Windoesn't going. And to interface my music keyboard with the computer, I have a choice of a midi > usb and midi > serial cables both of which came with Windows drivers only. No doubt someone could get these drivers working with something like ndiswrapper, but I'm not even going to try. Life is too short. :wink:

Just recently I bought a cheap pci soundcard that came with a joystick port. Joystick > midi cables are easy to find but I don't know whether the Linux kernel driver for the soundcard will recognise midi signals coming in from the joystick port. I haven't had time to try it yet.

Again, recently, someone I know bought themselves a (dumb) music controller keyboard which has a usb connector instead of a midi one. That might be worth trying if you can borrow one.

Lastly - if you don't get any other responses, may I suggest you try a new thread without the word 'Finale' in it. It will be an unknown for the majority of people here I should think, and might put some people off from even reading your post.

Good luck!

---

### Post by Brightbelt on 2007-06-10
Thanks Coffeecat for your response. And yes, life is too short...I won't spend an inordinate amount of time on this. 

Btw, I may not have been clear but that's exactly what I have: a simple keyboard controller that goes in USB. But it still requires some sort of a driver I would imagine for it to be recognized by Finale.

However, I will try plugging it in and seeing if anything happens. If you have any additional ideas, I'm game. 

Many Thanks, Frank B.

---

### Post by christhemonkey on 2007-06-10
What i would do:

Load the kernel module for midi processing:
```
sudo modprobe snd-seq 
```

Then install aconnectgui to conect together the ports:
```
sudo apt-get install aconnectgui 
```

Go into winecfg and select the ALSA drivers only:
```
winecfg 
```

Then if you have a usb midi thingy it should be auto detected when you plug it in.

Run aconnectgui from a terminal:
```
acconectgui 
```

And see if there are ports for your Maudio usb midi thing. (and if there are you should connect them to the wine ports.

Then on passing midi data from your maudio midi it should go through into finale.

---

### Post by coffeecat on 2007-06-10
That's useful information, **christhemonkey**. I'll bookmark it for myself if I ever bestir myself sufficiently to get midi working in Linux. A point of information. 'lsmod | grep snd' shows me that the snd_seq module (and snd_seq_midi among others) is already in memory). Perhaps that's because of my CMedia sound card with a gameport, possibly?

---

### Post by Brightbelt on 2007-06-10
Thanks Christhemonkey,
Everything worked except for the last part. When I plugped my radium keyboard in usb, it got no detection and I tried  'acconectgui' in the terminal but it said 'command not found' (even using sudo). 

Now I have another problem. I swear initially it looked like I was going to be able to go into Finale smoothly, but ever since then, every time, it freezes going into the program. 

This is rather disconcerting because 2007 has a feature I was really counting on, called 'Deactivate Finale', which allows me to switch systems or uninstall the program, reinstall it,  and not have to grovel for an activation over the phone. 

How can I update wine from the terminal? Sometimes having the latest version makes a difference.

Many Thanks, Frank B.

---

### Post by christhemonkey on 2007-06-10
Maybe they are loaded automatically these days, i dont know.

Also on a slightly related not, for usb audio equipment, if it goes to the specification, then it should *just work* with linux using the snd-usb-audio.
But then again thats not really to do with usb midi. Which uses snd-seq-midi which again depends on standards compliant hardware.

---

### Post by christhemonkey on 2007-06-10
**@Brightbelt**
My bad i meant:
```
aconnectgui 
```
Which you should have installed already with:
```
sudo apt-get install aconnectgui 
```

May i suggest musescore or noteedit as linux native alternatives?
```
sudo apt-get install noteedit 
```
Or for mscore see here:
[http://mggmail.blogspot.com/2007/05/mscore-package-for-musix-debianstable.html](http://mggmail.blogspot.com/2007/05/mscore-package-for-musix-debianstable.html) (this might not work im afraid)
or install it from source from here:
[http://mscore.sourceforge.net/](http://mscore.sourceforge.net/)

```
sudo apt-get upgrade 
```
Should update everything to the latest version.

---

### Post by Brightbelt on 2007-06-10
Ok,
Christhemonkey, I installed Noteedit -- and it shows that it is installed in the Synaptic package Manager,...but I can't find it on any menu or access it anywhere!! I've tried restarting several times, but nada. 

Also, to update you on other parts of this: aconnectgui is installed and when I run 'aconnectgui' in the terminal, it brings up a small ALSA Sequencer window, but it still doesn't recognize my keyboard. I can click anywhere within the sequencer but nothing responds.

Many Thanks for any followup,...Frank B.

---

### Post by christhemonkey on 2007-06-10
Go to a terminal and type (you guessed it):
```
noteedit 
```

That should launch the program.
Also if you feel like being helpful file a bug against that package on launchpad.

For aconnectgui,
To connect ports (think like physically connecting with a midi cable) first click on the little cable icon, on the right of the scisorrs, then drag between an "Out" and an "in" arrow next to the individual clients.

Are there ports listed there for your midi device?

---

### Post by Brightbelt on 2007-06-10
Sorry, I was out for the afternoon a bit...
As far as I know there are no ports that show for my keyboard or for any midi device.

I'll have to try that thing with the sequencer, but it's just that window there, so it'll seem like I'm plugging something into itself, ....if that makes sense.

Many Thanks, Frank B.

---

### Post by christhemonkey on 2007-06-10
Iv attached a screenshot of what mine looks like.

Where the system devices are well, the internal midi clock etc.
Midi through is, well, the midi through...
CmediaPCI is my sound cards midi.
MPU401 is the gameport on motherboard.
Client 129 is noteedit.

And noteedit has made some connections by itself on startup.
To all 3 other non-system devices.

---

### Post by Brightbelt on 2007-06-10
Wow, That shows a lot more than mine. So I've taken a window screenshot of what mine looks like, even while my keyboard is plugged in. 

It's all that I'm getting,....Frank B.

---

### Post by christhemonkey on 2007-06-11
Ok, what exactly is your usb midi?

You said it was a m audio?

Is it a m audio 4x4, 2x2, 1x1, or uno?
Or is it a usb keyboard like the m audio Radium?



When you plug it in, what is the output of this command:
```
dmesg | tail 
```

---

### Post by Brightbelt on 2007-06-11
Thanks for keeping up, Christhemonkey....I have a radium m-audio usb keyboard. It's a Radium midiman keyboard.

Here's what I got when I ran your code:

brightbelt@brightbelt-desktop:~$ dmesg | tail
[   54.992000] NTFS-fs warning (device sdc5): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   55.148000] NTFS volume version 3.1.
[   55.428000] NTFS-fs warning (device sdd1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   55.544000] NTFS volume version 3.1.
[   67.768000] SoftMAC: Open Authentication completed with 00:13:10:b0:dc:bb
[   67.808000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   68.908000] ieee80211_crypt: registered algorithm 'TKIP'
[   87.796000] eth1: no IPv6 routers present
[  257.672000] usb 2-5: new full speed USB device using ohci_hcd and address 4
[  257.876000] usb 2-5: configuration #1 chosen from 1 choice
brightbelt@brightbelt-desktop:~$ 

Thanks for following up with me!! I appreciate it,....Frank B.

---

### Post by christhemonkey on 2007-06-12
Ok i think you just need to do:
```
sudo apt-get install midisport-firmware 
```

(make sure you have the multiverse repository enabled otherwise apt wont find it!)

Then plug in your radium and check the dmesg output again.

---

### Post by Brightbelt on 2007-06-12
OK, The midisport firmware did install and I think that was a really good idea, but I'm still getting nothing from the keyboard.

Is there a way to install the m-audio usb midi driver in Linux ? I can't say exactly what it'd be called, but I do have the CD driver for windows. 

Thank you for sticking with me, Christhemonkey,...Frank B.

---

### Post by Brightbelt on 2007-06-12
Christhemonkey, I found this comment from another M-Audio post:

""....
Hi,
Feisty has built-in support for the new Keystation es models. Plug in your USB port, open a terminal and type "lsusb" you should see a list of USB devices and the Keystation will appear as "evolution" (I can't remember the exact name). Then you need to download qjackctl from the repositories and use it as an interface to whatever software you are using, I use my Keystation with Qsynth and it works very well.
...."

I'll give this a try as well and let you know,....Frank B.

---

### Post by Brightbelt on 2007-06-12
Well, it seems that whenever I sync things up -using Qjackctl with the Alsa driver along with wine - Finale freezes upon opening. 

Setting QJackctl to use the Freebob driver works better with Finale, but then QJackctl says it cannot connect with the server. 

I'll keep looking, Frank B.

---

### Post by christhemonkey on 2007-06-12
If you want to use the JACK audio server with wine you will need to install libjack0.100.0-dev. 
```
sudo apt-get install libjack0.100.0-dev 
```

The launch winecfg:
```
winecfg 
```

Go to the audio tab and select JACK as well as ALSA.


Then start qjackctl and start the server;
(btw dont use the freebob backend unless your using a firewire card for audio which you dont seem to be...) 

Connect the wine audio ports to alsa_pcm and then look on the midi tab, hopefully wine and your radium will have ports that you can connect and then BANG magic, it should *just work.*

---

### Post by christhemonkey on 2007-06-12
Also please post the output of lsusb so we can see exactly what make and model your Radium is.


Also if it is a Radium, then it wont be Keystation es which doesnt require firmware.

---

### Post by Brightbelt on 2007-06-12
OK, Christhemonkey, how exactly do I do this???

"....Connect the wine audio ports to alsa_pcm and then look on the midi tab, hopefully wine and your radium will have ports that you can connect ...."

What does" alsa_pcm" mean or stand for? Where are the wine audio parts? Also, still with everything set to alsa, Finale still freezes. Who knows. 

When I run lsusb, I get this:

brightbelt@brightbelt-desktop:~$ lsusb
Bus 002 Device 004: ID 0763:1014 Midiman 
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d49:7110 Maxtor 
Bus 001 Device 006: ID 03f0:070c Hewlett-Packard 
Bus 001 Device 002: ID 04b8:0827 Seiko Epson Corp. 
Bus 001 Device 005: ID 0424:2504 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000  

I see it says "midiman", so that may be different. Right?

Thanks for hanging in with me, Frank B.

---

### Post by christhemonkey on 2007-06-12
Ok maybe we should start by getting your Maudio midi working then you we can worry about getting Finale to recieve the midi events :)

What is the output of 'dmesg | tail' when you replug your keyboard in, now that you have midisport-firmware installed?
(you might need to restart your pc before it starts to load the usb firmware)

And the output of:
```
aconnect -o 
```

---

### Post by Brightbelt on 2007-06-12
Ok, for the first command, the 'dmesg | tail' one, I get this:

brightbelt@brightbelt-desktop:~$ dmesg | tail
[   53.796000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   55.780000] NTFS-fs warning (device sdd1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   55.892000] NTFS volume version 3.1.
[   55.916000] NTFS-fs warning (device sdc5): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[   56.092000] NTFS volume version 3.1.
[   59.608000] SoftMAC: Open Authentication completed with 00:13:10:b0:dc:bb
[   59.624000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   60.752000] ieee80211_crypt: registered algorithm 'TKIP'
[   69.656000] eth1: no IPv6 routers present
[   81.968000] eth1: no IPv6 routers present
brightbelt@brightbelt-desktop:~$ 

And for the 'aconnect -o' command, I get: 

brightbelt@brightbelt-desktop:~$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
brightbelt@brightbelt-desktop:~$ 

Thanks, I hope these help you (and me) out,....Frank B.

---

### Post by christhemonkey on 2007-06-12
Is this after plugging your midi device in?


Or if you put it in at boot what is the output of this command:
```
dmesg | grep usb 
```

---

### Post by Brightbelt on 2007-06-12
Yes, I restarted the computer like you suggested and then ran the commands. And I restarted again here with my keyboard already plugged in for the 'dmesg | grep' command which brought this:

brightbelt@brightbelt-desktop:~$ dmesg | grep usb
[    3.384000] usbcore: registered new interface driver usbfs
[    3.384000] usbcore: registered new interface driver hub
[    3.384000] usbcore: registered new device driver usb
[    6.252000] usb usb1: configuration #1 chosen from 1 choice
[    6.600000] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.744000] usb 1-1: configuration #1 chosen from 1 choice
[    6.944000] usb usb2: configuration #1 chosen from 1 choice
[    6.996000] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    7.136000] usb 1-2: configuration #1 chosen from 1 choice
[    7.564000] usb 1-4: new high speed USB device using ehci_hcd and address 5
[    7.704000] usb 1-4: configuration #1 chosen from 1 choice
[    8.236000] usb 1-7: new high speed USB device using ehci_hcd and address 7
[    8.392000] usb 1-7: configuration #1 chosen from 1 choice
[    8.884000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    9.112000] usb 2-3: configuration #1 chosen from 1 choice
[    9.420000] usb 2-5: new full speed USB device using ohci_hcd and address 3
[    9.616000] usb 2-5: configuration #1 chosen from 1 choice
[    9.924000] usb 2-8: new full speed USB device using ohci_hcd and address 4
[   10.132000] usb 2-8: configuration #1 chosen from 1 choice
[   10.184000] usbcore: registered new interface driver libusual
[   10.520000] usb-storage: device found at 2
[   10.520000] usb-storage: waiting for device to settle before scanning
[   10.520000] usb-storage: device found at 3
[   10.520000] usb-storage: waiting for device to settle before scanning
[   10.520000] usb-storage: device found at 7
[   10.520000] usb-storage: waiting for device to settle before scanning
[   10.520000] usb-storage: device found at 4
[   10.520000] usb-storage: waiting for device to settle before scanning
[   10.520000] usbcore: registered new interface driver usb-storage
[   15.520000] usb-storage: device scan complete
[   15.524000] usb-storage: device scan complete
[   15.524000] usb-storage: device scan complete
[   15.524000] usb-storage: device scan complete
[   18.260000] usbcore: registered new interface driver hiddev
[   18.328000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-3
[   18.328000] usbcore: registered new interface driver usbhid
[   18.328000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.396000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0827
[   18.396000] usbcore: registered new interface driver usblp
[   18.396000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   18.520000] usbcore: registered new interface driver lmpcm_usb
[   18.520000] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver

Thanks, Frank B.

---

### Post by christhemonkey on 2007-06-12
Try this:

Boot up without your usb midi inserted then type this command:
```
tail -f /var/log/messages 
```

Then insert your usb midi and paste the output here :D
(as well as lsub again, just for the heck of it :D)

---

### Post by Brightbelt on 2007-06-12
Ok, first one:

brightbelt@brightbelt-desktop:~$ tail -f /var/log/messages
Jun 12 18:22:05 brightbelt-desktop kernel: [   47.048000] lo: Disabled Privacy Extensions
Jun 12 18:22:05 brightbelt-desktop kernel: [   47.048000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 12 18:22:05 brightbelt-desktop kernel: [   47.048000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 12 18:22:10 brightbelt-desktop gconfd (brightbelt-6049): Resolved address "xml:readwrite:/home/brightbelt/.gconf" to a writable configuration source at position 0
Jun 12 18:22:10 brightbelt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun 12 18:22:11 brightbelt-desktop kernel: [   52.636000] SoftMAC: Open Authentication completed with 00:13:10:b0:dc:bb
Jun 12 18:22:11 brightbelt-desktop kernel: [   52.652000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 12 18:22:21 brightbelt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Jun 12 18:22:21 brightbelt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jun 12 18:22:21 brightbelt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jun 12 18:23:30 brightbelt-desktop kernel: [  131.940000] usb 1-5: new full speed USB device using ohci_hcd and address 5
Jun 12 18:23:30 brightbelt-desktop kernel: [  132.144000] usb 1-5: configuration #1 chosen from 1 choice

lsusb
 

And as you see, I couldn't run lsusb there. I couldn't get my command prompt back even. So I closed the terminal - reopened it, and ran lsusb:

brightbelt@brightbelt-desktop:~$ lsusb
Bus 002 Device 002: ID 04b8:0827 Seiko Epson Corp. 
Bus 002 Device 006: ID 03f0:070c Hewlett-Packard 
Bus 002 Device 003: ID 0d49:7110 Maxtor 
Bus 002 Device 005: ID 0424:2504 Standard Microsystems Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0763:1014 Midiman 
Bus 001 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000  
brightbelt@brightbelt-desktop:~$ 

I hope this is helping,....Thanks, Frank B.

---

### Post by Brightbelt on 2007-06-12
Christhemonkey, in the first sequence from the "tail..." command, it was the last line OR 2 that appeared when I plugged the keyboard in.  In other words, most of it came when I ran the command after the reboot, but before plugging in the keyboard. Then when I plugged in the keyboard, I got the last line or so of that sequence. 

 I hope that makes sense. I'm trying to follow your directions exactly. 

Thanks, Frank B.

---

### Post by loell on 2007-06-13
hi, i was wondering about this particular software too, actually sibelius and finale.

how about making the timidity as a server? 

it worked as a playback for noteworthy composer  on me, i just thought maybe we can do the same with finale :)

---

### Post by Brightbelt on 2007-06-13
Ok, Loell, it's worth a try. I assume it's available in Add/Remove. 

Thanks for the tip; I'll let you know what happens and you do the same. Thanks, ;) Frank B.

---

### Post by loell on 2007-06-13
or you can just invoke the command in the command line to install
```
sudo apt-get install timidity
```

and to launch timdity as a midi server, just invoke the command

```
timidity -iA -B2,8 -Os
```

i'm having trouble downloading the trial version of finale notepad. but when i get it, i'll try this too.

---

### Post by loell on 2007-06-13
oh my bad, i have now read the whole thread,
but i was thinking that you just want midi playback for finale, i guess my suggestion was of no use :(

---

### Post by christhemonkey on 2007-06-14
Thanks Frank B for following the instructions so well :)

Ok, i think we need to actually insert the firmware from your cd.
Try doing this:
[http://demudi.agnula.info/wiki/DocumentsTipsMAudio?format=txt](http://demudi.agnula.info/wiki/DocumentsTipsMAudio?format=txt)

---

### Post by Brightbelt on 2007-06-14
Jose, those instructions speak more of going into windows which I'll try later on etc.  I already tried installing the tar.gz file in Ubuntu last night, but I tried again here so I could show you what's generated. (First I tried an uninstall to clear the system because I tried this same install last night....) and this is what I got:

```
brightbelt@brightbelt-desktop:~$ cd Desktop
brightbelt@brightbelt-desktop:~/Desktop$ cd midisport-firmware-1.2
brightbelt@brightbelt-desktop:~/Desktop/midisport-firmware-1.2$ sudo make uninstall
Password:
make: *** No rule to make target `uninstall'.  Stop.
brightbelt@brightbelt-desktop:~/Desktop/midisport-firmware-1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for fxload... /sbin/fxload
checking for udev version... 108
checking for /etc/udev/udev.conf... yes
checking for udev rules directory... not found; assuming /etc/udev/rules.d
configure: creating ./config.status
config.status: creating Makefile
brightbelt@brightbelt-desktop:~/Desktop/midisport-firmware-1.2$ make
rm -f 42-midisport-firmware.rules 42-midisport-firmware.rules.tmp
sed -e 's,@firmwaredir\@,/usr/local/share/usb/maudio,g' \
                -e 's,@fxload\@,/sbin/fxload,g' \
                ./42-midisport-firmware.rules.in > 42-midisport-firmware.rules.tmp
mv 42-midisport-firmware.rules.tmp 42-midisport-firmware.rules
rm -f files.list
for i in 42-midisport-firmware.rules; do \
                echo "/etc/udev/rules.d/$i"; \
        done >> files.list
for i in MidiSportLoader.ihx MidiSport2x2.ihx MidiSport1x1.ihx MidiSportKS.ihx MidiSport4x4.ihx MidiSport8x8-2.10.ihx MidiSport8x8-2.21.ihx; do \
                echo "/usr/local/share/usb/maudio/$i"; \
        done >> files.list
brightbelt@brightbelt-desktop:~/Desktop/midisport-firmware-1.2$ sudo make install
make[1]: Entering directory `/home/brightbelt/Desktop/midisport-firmware-1.2'
make[1]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/usb/maudio" || mkdir -p -- . "/usr/local/share/usb/maudio"
 /usr/bin/install -c -m 644 'MidiSportLoader.ihx' '/usr/local/share/usb/maudio/MidiSportLoader.ihx'
 /usr/bin/install -c -m 644 'MidiSport2x2.ihx' '/usr/local/share/usb/maudio/MidiSport2x2.ihx'
 /usr/bin/install -c -m 644 'MidiSport1x1.ihx' '/usr/local/share/usb/maudio/MidiSport1x1.ihx'
 /usr/bin/install -c -m 644 'MidiSportKS.ihx' '/usr/local/share/usb/maudio/MidiSportKS.ihx'
 /usr/bin/install -c -m 644 'MidiSport4x4.ihx' '/usr/local/share/usb/maudio/MidiSport4x4.ihx'
 /usr/bin/install -c -m 644 'MidiSport8x8-2.10.ihx' '/usr/local/share/usb/maudio/MidiSport8x8-2.10.ihx'
 /usr/bin/install -c -m 644 'MidiSport8x8-2.21.ihx' '/usr/local/share/usb/maudio/MidiSport8x8-2.21.ihx'
test -z "/etc/udev/rules.d" || mkdir -p -- . "/etc/udev/rules.d"
 /usr/bin/install -c -m 644 '42-midisport-firmware.rules' '/etc/udev/rules.d/42-midisport-firmware.rules'
make[1]: Leaving directory `/home/brightbelt/Desktop/midisport-firmware-1.2'
brightbelt@brightbelt-desktop:~/Desktop/midisport-firmware-1.2$ 


```

Still no recognition of the keyboard, even with jackctr going. I have yet to follow those instructions of actually going into windows, doing the partial install and bringing it back to Linux. I'll have to wait a day or two when I have time.

Thanks for sticking with me on this,.....Frank B.

---

### Post by christhemonkey on 2007-06-15
Ok you do need to do the bit about loading the actual device firmware cos thats kinda the point :)


Let us know how it goes and if you get any problems!

---

### Post by shanepardue on 2007-07-14
I'm having the same problem with my Radium midi controller...it shows up in lsusb and dmesg, but it isn't being recognized by jack-control or rosegarden.

I'm not able to find much info on this elsewhere either.

---

