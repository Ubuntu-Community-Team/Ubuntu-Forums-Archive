---
title: "Cannot recognize external firewire hard drive"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-03-20
Hi:

I have a PCI firewire card in my Breezy computer and it is recognized. However, in attempting to connect an external firewire hard drive . . . I cannot find the drive in /media or . . . anywhere else. Perhaps the external firewire device is not compatible with Breeze but . . . how/what do I check or how do I go about formatting and mounting an external firewire drive?

Thanks.

---

### Post by Pragmatist on 2006-03-20
Type this command in a terminal when the drive is unplugged.
```
tail -f /var/log/messages
```

Now, plug in the drive and watch for any messages to show up in the terminal.  Post them here.

---

### Post by GMachine_24 on 2006-03-20
Ok, I typed in the command you said to in a terminal window with the firewire drive disconnected and got this:

user@ubuntu1:~$ tail -f /var/log/messages
Mar 20 13:24:04 localhost gconfd (root-8036): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 7
Mar 20 13:24:07 localhost kernel: [ 1599.983167] Warning: /proc/ide/hd?/settings  interface is obsolete, and will be removed soon!
Mar 20 13:24:34 localhost gconfd (root-8036): GConf server is not in use, shutti ng down.
Mar 20 13:24:34 localhost gconfd (root-8036): Exiting
Mar 20 13:38:43 localhost -- MARK --
Mar 20 13:58:43 localhost -- MARK --
Mar 20 14:18:43 localhost -- MARK --
Mar 20 14:38:43 localhost -- MARK --
Mar 20 14:58:44 localhost -- MARK --
Mar 20 15:18:44 localhost -- MARK --

Then I plugged the drive back in and watched, and nothing happened. No messages.

GM

---

### Post by Pragmatist on 2006-03-20
What is the make and model number of your devices (firewire card, and drive)?  Also, please give output of:
```
lspci |grep [F,f]ire
```

---

### Post by GMachine_24 on 2006-03-20
Hi:

The firewire card is a Via Technologies (see below)

user@ubuntu1:~$ lspci |grep [F,f]ire
0000:00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

the firewire is a do-it-yourself with a Western Digital 120GB hard drive and a firewire case with a chipset which I cannot read and which only shows up on my Windows machine as a 'generic' IEEEE 1394 drive.

So, I'm assuming an incompatibility between the firewire drive/chip and Ubuntu. I just wondered if there was something I was doing wrong before springing for a new external firewire drive.

---

### Post by GMachine_24 on 2006-03-20
/
The PCI firewire card Via chipset is VT6306.

Model: A-1394/6306

---

### Post by Pragmatist on 2006-03-20
So we've got three components:

1.) PCI Firewire (IEEE 1394)Card:  
       (a) Brand = Via Technologies
       (b) Model = A-1394/6306
       (c) Chipset = VT6306

2.) Firewire case:
       (a) Brand = ?
       (b) Model = ?
       (c) Chipset = ?

3.) Hard Drive
       (a) Brand = Western Digital
       (b) Model = probably not necessary

Probably nothing is physically wrong with the PCI card or the case, since windows can at least detect the drive (can you use the drive on windows??)

So the key information we need is about this firewire case.  While a chipset is best, the brand/model will help get us there--there is alot of info on the web :)

---

### Post by GMachine_24 on 2006-03-20
Hi:

Well, the firewire case came in a generic-looking box with no brand name or make/model numbers on it. However, the wholesaler I bought them from listed the model number as

CSE-PENR-525FW

with the "525FW" obviously referring to the fact that the case is a 5.25" firewire case . . . 

The chipset is an SBP2-compliant 1394 Oxford 911 (perhaps this number means something:the details under 'device manager' in Windows XP Home version with SP2 are 

1394\Oxford______&911\580831EE2E03000

)

I find references on the Net to Oxford 911 firewire chipsets and "bridge boards" working with Linux.....and I doubt it's the hard drive but the WD model number is 

WD1200JB-00EVA0


Yes, the case works with Windows XP (the only version of Windows I have attempted it with).

---

### Post by Pragmatist on 2006-03-20
Try this:
```
sudo insmode sbp2 serialize_io=1
```

---

### Post by GMachine_24 on 2006-03-21
Hi:

Thanks for your continued help. Here is the result of the command you specified:

user@ubuntu1:~$ sudo insmode sbp2 serialize_io=1
Password:
sudo: insmode: command not found
user@ubuntu1:~$

So I tried it again without sudo (since I'd already given my password) and I got

user@ubuntu1:~$ insmode sbp2 serialize_io=1
bash: insmode: command not found
user@ubuntu1:~$

Then I tried it as "root"

user@ubuntu1:~$ su -
Password:
root@ubuntu1:~# insmode sbp2 serialize_io=1
-su: insmode: command not found
root@ubuntu1:~#


That's it.

---

### Post by Pragmatist on 2006-03-21
sorry, spelling mistake, I added an 'e' at the end by mistake.:oops: It is **insmod** not insmode

---

### Post by GMachine_24 on 2006-03-21
This is the result:

user@ubunt1:~$ insmod sbp2 serialize_io=1
insmod: can't read 'sbp2': No such file or directory

---

### Post by Pragmatist on 2006-03-21
Ok, these are my errors in syntax.  What happend was that I read around and saw a few people had success with the sbp2 module with the serialize option.  Today we usually use modprobe instead of insmod, but since that was the syntax on the sites I saw, I went with that.  Regardless, it should have worked except the sites I saw weren't precise.  Here is the authority on the subject:

[http://www.linux1394.org/sbp2.php](http://www.linux1394.org/sbp2.php)

From this I gather the right invocation is:

```
sudo modprobe sbp2 sbp2_serialize_io=1
```

What your doing is loading the sbp2 kernel module which will, hopefully, allow you to use your firewire case.  the "sbp2_serialize_io" is just an option.

You should have the sbp2.ko module here:
 /lib/modules/2.6.12-10-386/kernel/drivers/ieee1394/sbp2.ko

Naturally, if your kernel isn't exactly 2.6.12-10-386 then the corresponding directory under /lib/modules will be slightly different.

The easiest way to check that you have the sbp2.ko module is like this:
```
sudo updatedb
```
Wait until that finishes and then type this:
```
locate sbp2
```

---

### Post by GMachine_24 on 2006-03-21
Hi:

Actually, attempting to run 

sudo modprobe sbp2 sbp2_serialize_io=1

produced an error message that suggested I read "dmesg" from which I gathered "sbp2_serialize_io=1" is not the proper style.

So I ran

sudo modprobe sbp2

and there were no error messages. But I also could not read/find my firewire drive. (I do have  /lib/modules/2.6.12-10-386/kernel/drivers/ieee1394/sbp2.ko)

Reading

[http://www.linux1394.org/sbp2.php](http://www.linux1394.org/sbp2.php)

I found that with Linux kernel 2.6 the second "sbp2" (i.e. the one directly preceding "_serialize") is not needed, i.e. causes an error message if one tries

sudo modprobe sbp2 sbp2_serialize_io=1

so I tried

sudo modprobe sbp2 serialize_io=1

without receiving an error or any other type of message. But, once again, I cannot find my firewire drive.

I also did:

user@ubuntu1:~$ sudo updatedb
user@ubuntu1:~$ locate sbp2
/lib/modules/2.6.12-9-386/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.12-10-386/kernel/drivers/ieee1394/sbp2.ko


I read the remainder of sbp2.php to no avail. I am completely lost.

---

### Post by Pragmatist on 2006-03-21
Ok, lets go step-by-step.  Did the module load?  Do this to find out:
```
lsmod
```

---

### Post by Pragmatist on 2006-03-21
Try this:
```
sudo gedit /etc/modprobe.d/1394_drive
```
then type this line and save the file (you can call it anything you want, not just 1394_drive):
```
options sbp2 serialize_io=1
```

Now type:
```
sudo modprobe sbp2
```

Let us know what happens.  This should at least load the module with the option.

---

### Post by GMachine_24 on 2006-03-22
Hi again:

This is a response to Post #15 as I believe the module in question loaded - at least once.

Upon running

lsmod | more

I found (among numerous other processes of course)

ohci1394               30644  0
ieee1394               90936  2 sbp2,ohci1394


Ok, I thought sbp2 was mentioned more than once but I guess not. I am assuming this means the module loaded?

GM

P.S. Thank you for all the time you have put into this.

---

### Post by Pragmatist on 2006-03-22
Does it work yet!

---

### Post by GMachine_24 on 2006-03-22
Oh yeah, duh.

No, I cannot find the firewire drive - but at this point I'm not sure if I'd know where to look. I checked /media and it is not there. Perhaps I should try another hard drive or look elsewhere?

---

### Post by Pragmatist on 2006-03-22
Let's see what these produce:
```
mount
```
Do you see something looking like your drive in this output?

If not, then with the drive unplugged, check again, now that it is unplugged ,that the modules are still loaded (they should be) by typing **lsmod |grep sbp2**  Then type this in a terminal followed by plugging in the device.  Look for new messages to appear on your screen.
```
tail -f /var/log/messages
```

Did you do these yet?
>  	
```
sudo gedit /etc/modprobe.d/1394_drive
```

then type this line and save the file (you can call it anything you want, not just 1394_drive):
```
options sbp2 serialize_io=1
```

Now type:
```
sudo modprobe sbp2
```


---

### Post by GMachine_24 on 2006-03-22
Hello:

user@ubuntu1:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hdd1 on /data1A type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

Nothing that looks like a firewire hard drive - all the hdx drives are accounted for.

After disconnecting the firewire drive, the sbp2 / firewire mod(s) is/are still running.

user@ubuntu1:~$ tail -f /var/log/messages
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6Mar 22 18:06:35 localhost gconfd (root-8872): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Mar 22 18:07:35 localhost gconfd (root-8872): GConf server is not in use, shutting down.
Mar 22 18:07:35 localhost gconfd (root-8872): Exiting

... and nothing more after plugging in the firewire drive.

I did this

sudo gedit /etc/modprobe.d/1394_drive

added

options sbp2 serialize_io=1

to the blank page and saved it and then ran

sudo modprobe sbp2

which just got me another command line. Since the sbp2 module was already running

lsmod | more

yielded the same results as prior to creation of this file, etc.

I also:

1. Brought another, identical, firewire drive (this one with a DVD player) that is normally connected to one of my Windows XP machines over and connected that - ran through all the same commands as above where applicable and . . . nothing.

2. Changed hard drives to a Maxtor 4D080H4 drive which tested good two days ago on a Windows machine (i.e. the computer recognized the drive and I could do whatever, partition, format, etc.) and then wiped it blank. Ran all the commands - again, nothing.

At this point if there was an emoticon of a little yellow head waving a white flag, I'd enter it here: <white flag>.

I have a RAID PCI card connected to this computer so I can add three more drives as needed. Perhaps I will check the Linux/Ubuntu hard drive compatibility list and try another make/model of firewire drive.

I thank you for all your help - but really, life is too short.

GM

---

### Post by Pragmatist on 2006-03-22
> Originally Posted by: **GMachine_24**
*At this point if there was an emoticon of a little yellow head waving a white flag, I'd enter it here....I thank you for all your help - but really, life is too short.*

LOL, they should make such an icon! :)  It is understandable if you want to quit.  Please realize, however, that this is no reflection on you or even the supposed difficulty of the task we worked on.  It really is my ineptness at this particular problem.  I haven't had to do it before and so it is taking much longer than if you got instructions from someone who knew exactly what they were doing.

If you still want to try, I definitely believe there are good chances that it will work.  I just found this site, which has some excellent advice.  There aren't that many steps, so if you go very carefully through these, you might have your drive working in no time.

---

### Post by GMachine_24 on 2006-03-22
. . . . and ..... I suppose... I am to find the url for this new Web site you mention . . . telepathically? ;) I'm kidding - but I do think you forgot to include the address for the Web site you mentioned.

I, generally, can make anything work and can, with help and diligence, solve almost any computer problem I've encountered. This one just wore me down because I also screwed up an install -- trying to get "HandBrake" installed and working - now that is a true disaster I am going to have to unravel.

It wasn't but 10 minutes after my last post that I was over at another computer  researching the Oxford 911, Linux etc. - found the home page for Oxford Semi and got a stat sheet off of that - I didn't realize that the Oxford 911 was at one time thought of as the premiere firewire chipset.

I also read some posts in various forums from other people who either got their firewire device up and running only after many many hours of trial and error and I also didn't know - and I still don't know much about this - but there seems to be some sort of connection between SCSI and firewire - which makes sense because they are both tempermental and seem to come and go as they please - at least on a Windows machine.

So . . . if you would be so kind as to post the link to the Web page you mention I will take a look at it. Also, please tell me the route to where I will most likely find my firewire drive once it is working . . . e.g. will it be in /dev or somewhere else?

And, lastly, along with the white flag emoticon I think there should be a similar one for throwing in the towel. I guess that's the same thing. :confused:

---

### Post by Pragmatist on 2006-03-22
Whoops!  Wow! The only two obvious blunders I've made are in this thread!! :oops: maybe I should call it quits :rolleyes:  
Here it is:
[http://www.strange-phenomenom.de/pmwiki-0.4.25/index.php/Linux/ExternalFireWireHardDrive](http://www.strange-phenomenom.de/pmwiki-0.4.25/index.php/Linux/ExternalFireWireHardDrive)

---

### Post by GMachine_24 on 2006-03-22
Uhm... ok... it looks complicated enough that it might work... I d/l the script for scanning for scsi drives... but... I really do not know what to do with this

perl #!/bin/sh case "$1" in start) echo "Starting firewire harddisk..." modprobe -k ieee1394 modprobe -k ohci1394 modprobe -k sbp2 modprobe -k sd_mod modprobe -k sg ./rescan-scsi-bus.sh mount /firewire ;; stop) echo "Shutting down firewire harddisk..." fuser -m /firewire umount /firewire modprobe -r sbp2 modprobe -r ohci1394 modprobe -r sg modprobe -r sd_mod ;; *) echo "Usage: $0 [start|stop]" ;; esac

Is it run all at once? Do I break it into separate commands? If so, where? Do I create a script? If so, how?

---

### Post by Pragmatist on 2006-03-22
Here are the scripts.  You can rename the one called "load.txt" to whatever you want, but leave off the .txt extension.  The one called "rescan" rename to **rescan-scsi-bus.sh**  This name must be exact.  Make sure they are executable by doing this to each file:
```
chmod +x filename
```
Then, you do this to execute:
```
./load start
```

Three  points:  
1.You run that last command inside the directory where the script (I'm calling it "load") resides.
2.) You preface the script name with ./  Thus ./load

3.) You put the word "start" at the end of ./load   This tells the script you want to install the modules and so on.  If you put stop instead, it would remove the modules....etc...

---

### Post by GMachine_24 on 2006-03-22
Ok, did as you said and got this output:


<code>
user@ubuntu1:~$ ./load start
Starting firewire harddisk...
./rescan-scsi-bus.sh: line 31: [: too many arguments
Host adapter * (device_info) found.
Scanning hosts  * channels 0 for
 SCSI target IDs  0 1 2 3 4 5 6 7 , LUNs  0
Scanning for device amsn 0 0 0 ...
Scanning for device amsn 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device amsn_received 0 0 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 1 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 2 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 3 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 4 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 5 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 6 0 ...csi/scsi: Permission denied
Scanning for device amsn_received 0 7 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 0 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 1 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 2 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 3 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 4 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 5 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 6 0 ...csi/scsi: Permission denied
Scanning for device automatix.log 0 7 0 ...csi/scsi: Permission denied
Scanning for device Azureus 0 0 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 1 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 2 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 3 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 4 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 5 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 6 0 ...proc/scsi/scsi: Permission denied
Scanning for device Azureus 0 7 0 ...proc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 0 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 1 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 2 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 3 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 4 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 5 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 6 0 ...oc/scsi/scsi: Permission denied
Scanning for device crazy.odt 0 7 0 ...oc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 0 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 1 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 2 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 3 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 4 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 5 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 6 0 ...proc/scsi/scsi: Permission denied
Scanning for device CUPSPDF 0 7 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 0 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 1 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 2 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 3 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 4 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 5 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 6 0 ...proc/scsi/scsi: Permission denied
Scanning for device Desktop 0 7 0 ...proc/scsi/scsi: Permission denied
Scanning for device firewirescript 0 0 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 1 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 2 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 3 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 4 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 5 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 6 0 ...si/scsi: Permission denied
Scanning for device firewirescript 0 7 0 ...si/scsi: Permission denied
Scanning for device fontcache 0 0 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 1 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 2 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 3 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 4 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 5 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 6 0 ...oc/scsi/scsi: Permission denied
Scanning for device fontcache 0 7 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 0 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 1 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 2 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 3 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 4 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 5 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 6 0 ...oc/scsi/scsi: Permission denied
Scanning for device Handbrake 0 7 0 ...oc/scsi/scsi: Permission denied
Scanning for device HandbrakeLite 0 0 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 1 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 2 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 3 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 4 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 5 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 6 0 ...csi/scsi: Permission denied
Scanning for device HandbrakeLite 0 7 0 ...csi/scsi: Permission denied
Scanning for device hdb2 0 0 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device hdb2 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 0 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 1 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 2 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 3 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 4 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 5 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 6 0 ...scsi: Permission denied
Scanning for device Howl-Ginsberg.odt 0 7 0 ...scsi: Permission denied
Scanning for device iPodderData 0 0 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 1 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 2 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 3 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 4 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 5 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 6 0 .../scsi/scsi: Permission denied
Scanning for device iPodderData 0 7 0 .../scsi/scsi: Permission denied
Scanning for device java 0 0 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device java 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 0 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device Kino 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device lisamdj2000.png 0 0 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 1 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 2 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 3 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 4 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 5 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 6 0 ...i/scsi: Permission denied
Scanning for device lisamdj2000.png 0 7 0 ...i/scsi: Permission denied
Scanning for device load 0 0 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device load 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device mozilla_backup 0 0 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 1 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 2 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 3 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 4 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 5 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 6 0 ...si/scsi: Permission denied
Scanning for device mozilla_backup 0 7 0 ...si/scsi: Permission denied
Scanning for device New Database.lck 0 0 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 1 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 2 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 3 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 4 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 5 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 6 0 .../scsi: Permission denied
Scanning for device New Database.lck 0 7 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 0 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 1 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 2 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 3 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 4 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 5 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 6 0 .../scsi: Permission denied
Scanning for device New Database.odb 0 7 0 .../scsi: Permission denied
Scanning for device nvu 0 0 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 1 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 2 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 3 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 4 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 5 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 6 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device nvu 0 7 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 0 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 1 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 2 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 3 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 4 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 5 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 6 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device PDF 0 7 0 ...0: /proc/scsi/scsi: Permission denied
Scanning for device podcast 0 0 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 1 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 2 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 3 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 4 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 5 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 6 0 ...proc/scsi/scsi: Permission denied
Scanning for device podcast 0 7 0 ...proc/scsi/scsi: Permission denied
Scanning for device python2.4 0 0 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 1 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 2 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 3 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 4 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 5 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 6 0 ...oc/scsi/scsi: Permission denied
Scanning for device python2.4 0 7 0 ...oc/scsi/scsi: Permission denied
Scanning for device real 0 0 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 1 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 2 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 3 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 4 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 5 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 6 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device real 0 7 0 ...: /proc/scsi/scsi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 0 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 1 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 2 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 3 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 4 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 5 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 6 0 ...csi: Permission denied
Scanning for device rescan-scsi-bus.sh 0 7 0 ...csi: Permission denied
Scanning for device Skype1 0 0 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 1 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 2 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 3 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 4 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 5 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 6 0 .../proc/scsi/scsi: Permission denied
Scanning for device Skype1 0 7 0 .../proc/scsi/scsi: Permission denied
Scanning for device Slim_Server 0 0 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 1 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 2 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 3 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 4 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 5 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 6 0 .../scsi/scsi: Permission denied
Scanning for device Slim_Server 0 7 0 .../scsi/scsi: Permission denied
Scanning for device Various 0 0 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 1 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 2 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 3 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 4 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 5 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 6 0 ...proc/scsi/scsi: Permission denied
Scanning for device Various 0 7 0 ...proc/scsi/scsi: Permission denied
Scanning for device YahooMessenger 0 0 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 1 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 2 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 3 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 4 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 5 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 6 0 ...si/scsi: Permission denied
Scanning for device YahooMessenger 0 7 0 ...si/scsi: Permission denied
0 new device(s) found.               proc/scsi/scsi: Permission denied
0 device(s) removed.
mount: can't find /firewire in /etc/fstab or /etc/mtab
user@ubuntu1:~$

</code>

There seems to be an error in line 31 of the rescan-scsi file . . . but I can't tell what it is.

It seems at the beginning of the output that there is an indication that something was found - host adapter, etc.

I will try again tomorrow. Thanks for all your help.

---

### Post by Pragmatist on 2006-03-23
You just need to run the program as root. So preface the command with **sudo**
```
**sudo** ./load start
```

---

### Post by GMachine_24 on 2006-03-23
Yes, I ran it in sudo also and got the same result.

I also ran it logged in as root as in 

su -
password

My question now is whether I have SCSI support in my kernel. The SCSI rescan keeps searching for a file/location called /proc/scsi/scsi which does not exist on my computer and I have seen how SCSI devices are often listed in this location . . . so .... ???

How can I check whether I have SCSI support in my kernel?

---

### Post by Pragmatist on 2006-03-23
> Originally Posted by: **GMachine_24**
Yes, I ran it in sudo also and got the same result.
That is very strange.  You shouldn't have got all the "permission denied" messages.  I got those when I did it without sudo and they went away when I did it with sudo.

Please give me a long listing of both files:
```
ls -l file1 file2
```

---

### Post by GMachine_24 on 2006-03-23
[QUOTE=Pragmatist]That is very strange.  You shouldn't have got all the "permission denied" messages.  I got those when I did it without sudo and they went away when I did it with sudo.
[/QUOTE]


Just wanted to be sure you saw my updated post - the one previous to this one.

There is no /proc/scsi/scsi location on my computer. There is no /proc/scsi location on my computer. So again I'm asking if SCSI support is enabled in the kernel or what.... because when I searched the Net the /proc/scsi/scsi was a basic file which lists SCSI drives, as I'm sure you know, and is often invoked in association with the "cat" command.

Anyway your lists coming up in a moment.

---

### Post by GMachine_24 on 2006-03-23
[QUOTE=Pragmatist]
Please give me a long listing of both files:
```
ls -l file1 file2
```[/QUOTE]


Ok . . . . lol, which files do you want? Please remember to keep things very basic because I do not know what you want.

Thanks.

---

### Post by Pragmatist on 2006-03-23
> **Originally Posted by GMachine_24**
*There is no /proc/scsi/scsi location on my computer. There is no /proc/scsi location on my computer. So again I'm asking if SCSI support is enabled in the kernel or what.... because when I searched the Net the /proc/scsi/scsi was a basic file which lists SCSI drives, as I'm sure you know, and is often invoked in association with the "cat" command.*

You know me too well by now :)  Yeah, I missed this as I was in such awe of the continued 'permission denied' messages

Unless you did something really radical, like download an old kernel, tweak its options to remove scsi support, and recompile, you have scsi support.  It isn't that suprising to me that the file is missing.  Mine, for instance, only has these entries:
```
mnaus@ubuntu:~ $ cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: Apacer   Model: Embedded Reader  Rev: 3.02
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HP       Model: Photosmart 7400  Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 01
  Vendor: Apacer   Model: Embedded Reader  Rev: 3.02
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 02
  Vendor: Apacer   Model: Embedded Reader  Rev: 3.02
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 03
  Vendor: Apacer   Model: Embedded Reader  Rev: 3.02
  Type:   Direct-Access                    ANSI SCSI revision: 02

```
These represent the different slots on my media reader.  I'm sure if I plugged in my palm pilot, or ipod, or any other device that would be treated as a SCSI device, that new entries would be made.  So, perhaps, if you don't have any SCSI devices plugged in, it doesn't have the file?  Do you have a /proc/scsi directory?

---

### Post by Pragmatist on 2006-03-23
Sorry, the files I called load.txt and rescan.txt  The two files you downloaded from my earlier post.

---

### Post by GMachine_24 on 2006-03-23
Well, right, except the firewire drive is obviously supposed to register in that file and perhaps it is created when one FINALLY gets their SCSI/firewire device connected/recognized . . . but I have been unable to find an explanation of when the file is created in my searches.

Anyway, the output from the two files was rather dull:

<code>
user@ubuntu1:~$ ls -l load
-rwxr-xr-x  1 user user 434 2006-03-22 23:00 load
user@ubuntu1:~$ ls -l rescan-scsi-bus.sh
-rwxr-xr-x  1 root root 5523 2006-03-22 23:18 rescan-scsi-bus.sh
user@ubuntu1:~$
</code>

That's it.

Oh, and there is no /proc/scsi file.

---

### Post by Pragmatist on 2006-03-23
If you want to know more about what kernel options, related to SCSI, are loaded, then do this:
```
KERNAME=`uname -r`
```
Note: the little backward slashes(`) are essential. This is not the single-quote mark(') that is found about the regular quote (").  The backward slash(`)  can be found typically below the tilde (~) on the key next to the 1 (one) key.  Next do this:
```
cat /boot/config-$KERNAME | grep SCSI
```

---

### Post by Pragmatist on 2006-03-23
I'm doing some searches in the forums in general about external firewire drives.  Here is a listing of threads I get when using these as keywords:
**firewire external drive case**
[http://www.ubuntuforums.org/search.php?searchid=4460237](http://www.ubuntuforums.org/search.php?searchid=4460237)

I didn't read them all, but I found this one interesting:
[http://www.ubuntuforums.org/showthread.php?t=42516&highlight=firewire+external+drive+case](http://www.ubuntuforums.org/showthread.php?t=42516&highlight=firewire+external+drive+case)

---

### Post by GMachine_24 on 2006-03-23
Hi:

Here are the results:

</code>
user@ubuntu1:~$ KERNAME=`uname -r`
user@ubuntu1:~$ cat /boot/config-$KERNAME | grep SCSI
CONFIG_CISS_SCSI_TAPE=y
CONFIG_BLK_DEV_IDESCSI=m
# SCSI device support
CONFIG_SCSI=m
CONFIG_SCSI_PROC_FS=y
# SCSI support type (disk, tape, CD-ROM)
# Some SCSI devices (e.g. CD jukebox) support multiple LUNs
CONFIG_SCSI_MULTI_LUN=y
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
# SCSI Transport Attributes
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_ISCSI_ATTRS=m
# SCSI low-level drivers
CONFIG_SCSI_3W_9XXX=m
CONFIG_SCSI_7000FASST=m
CONFIG_SCSI_ACARD=m
CONFIG_SCSI_AHA152X=m
CONFIG_SCSI_AHA1542=m
CONFIG_SCSI_AHA1740=m
CONFIG_SCSI_AACRAID=m
CONFIG_SCSI_AIC7XXX=m
CONFIG_SCSI_AIC7XXX_OLD=m
CONFIG_SCSI_AIC79XX=m
CONFIG_SCSI_DPT_I2O=m
CONFIG_SCSI_ADVANSYS=m
CONFIG_SCSI_IN2000=m
CONFIG_SCSI_SATA=y
CONFIG_SCSI_SATA_AHCI=m
CONFIG_SCSI_SATA_SVW=m
CONFIG_SCSI_ATA_PIIX=m
CONFIG_SCSI_SATA_NV=m
CONFIG_SCSI_SATA_PROMISE=m
CONFIG_SCSI_SATA_QSTOR=m
CONFIG_SCSI_SATA_SX4=m
CONFIG_SCSI_SATA_SIL=m
CONFIG_SCSI_SATA_SIS=m
CONFIG_SCSI_SATA_ULI=m
CONFIG_SCSI_SATA_VIA=m
CONFIG_SCSI_SATA_VITESSE=m
CONFIG_SCSI_BUSLOGIC=m
# CONFIG_SCSI_OMIT_FLASHPOINT is not set
# CONFIG_SCSI_CPQFCTS is not set
CONFIG_SCSI_DMX3191D=m
CONFIG_SCSI_DTC3280=m
CONFIG_SCSI_EATA=m
CONFIG_SCSI_EATA_TAGGED_QUEUE=y
CONFIG_SCSI_EATA_LINKED_COMMANDS=y
CONFIG_SCSI_EATA_MAX_TAGS=16
CONFIG_SCSI_EATA_PIO=m
CONFIG_SCSI_FUTURE_DOMAIN=m
CONFIG_SCSI_FD_MCS=m
CONFIG_SCSI_GDTH=m
CONFIG_SCSI_GENERIC_NCR5380=m
CONFIG_SCSI_GENERIC_NCR5380_MMIO=m
CONFIG_SCSI_GENERIC_NCR53C400=y
CONFIG_SCSI_IBMMCA=m
CONFIG_IBMMCA_SCSI_ORDER_STANDARD=y
# CONFIG_IBMMCA_SCSI_DEV_RESET is not set
CONFIG_SCSI_IPS=m
CONFIG_SCSI_INITIO=m
# CONFIG_SCSI_INIA100 is not set
CONFIG_SCSI_PPA=m
CONFIG_SCSI_IMM=m
# CONFIG_SCSI_IZIP_EPP16 is not set
# CONFIG_SCSI_IZIP_SLOW_CTR is not set
CONFIG_SCSI_NCR53C406A=m
CONFIG_SCSI_NCR_D700=m
CONFIG_SCSI_SYM53C8XX_2=m
CONFIG_SCSI_SYM53C8XX_DMA_ADDRESSING_MODE=1
CONFIG_SCSI_SYM53C8XX_DEFAULT_TAGS=16
CONFIG_SCSI_SYM53C8XX_MAX_TAGS=64
# CONFIG_SCSI_SYM53C8XX_IOMAPPED is not set
CONFIG_SCSI_IPR=m
# CONFIG_SCSI_IPR_TRACE is not set
# CONFIG_SCSI_IPR_DUMP is not set
CONFIG_SCSI_NCR_Q720=m
CONFIG_SCSI_NCR53C8XX_DEFAULT_TAGS=8
CONFIG_SCSI_NCR53C8XX_MAX_TAGS=4
CONFIG_SCSI_NCR53C8XX_SYNC=5
# CONFIG_SCSI_NCR53C8XX_PROFILE is not set
CONFIG_SCSI_MCA_53C9X=m
CONFIG_SCSI_PAS16=m
# CONFIG_SCSI_PCI2000 is not set
# CONFIG_SCSI_PCI2220I is not set
CONFIG_SCSI_PSI240I=m
CONFIG_SCSI_QLOGIC_FAS=m
CONFIG_SCSI_QLOGIC_ISP=m
CONFIG_SCSI_QLOGIC_FC=m
CONFIG_SCSI_QLOGIC_FC_FIRMWARE=y
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLOGIC_1280_1040=y
CONFIG_SCSI_QLA2XXX=m
CONFIG_SCSI_QLA21XX=m
CONFIG_SCSI_QLA22XX=m
CONFIG_SCSI_QLA2300=m
CONFIG_SCSI_QLA2322=m
CONFIG_SCSI_QLA6312=m
CONFIG_SCSI_LPFC=m
# CONFIG_SCSI_SEAGATE is not set
CONFIG_SCSI_SIM710=m
CONFIG_SCSI_SYM53C416=m
CONFIG_SCSI_DC395x=m
CONFIG_SCSI_DC390T=m
CONFIG_SCSI_T128=m
CONFIG_SCSI_U14_34F=m
CONFIG_SCSI_U14_34F_TAGGED_QUEUE=y
CONFIG_SCSI_U14_34F_LINKED_COMMANDS=y
CONFIG_SCSI_U14_34F_MAX_TAGS=8
CONFIG_SCSI_ULTRASTOR=m
CONFIG_SCSI_NSP32=m
CONFIG_SCSI_DEBUG=m
# PCMCIA SCSI adapter support
CONFIG_PCMCIA_NINJA_SCSI=m
# Old CD-ROM drivers (not SCSI, not IDE)
CONFIG_CD_NO_IDESCSI=y
CONFIG_I2O_SCSI=m
# NOTE: USB_STORAGE enables SCSI, and 'SCSI disk support' may also be needed; see USB_STORAGE Help for more information
user@ubuntu1:~$
</code>

So, the only thing I wonder about is the note that says

USB_STORAGE enables SCSI

and

'SCSI disk support' may also be needed; see USB_Storage Help for more information.

---

### Post by Pragmatist on 2006-03-23
Back in the days of the 2.4 kernel (approx. spring '04 and before), there was this annoyance called **scsi emulation**.  Doing things like burning a CD were a major pain if you didn't understand what scsi emulation was.  2004 isn't THAT long ago! :), however, so we still see all sorts of posts, websites, howtos, etc... that are addressing people with the 2.4 kernel.  Further, Debian makes "stability" its prime focus, so typically it doesn't upgrade to the new kernels right away.  They want to give time to improve and develop and eliminate unknown bugs.  While Ubuntu is Debian based, we don't wait as long to upgrade a kernel. We try to stay as current as possible because we want people to be able to use new devices with ease and to use all sorts of multimedia devices, applications, etc..  
Why do I mention this?  Because we might run across advice from somebody who runs Debian and think we are close to what we need (since we are debian-based).  Yet, because they are using a much earlier kernel (2.4 or even 2.2 series kernels) the advice isn't applicable to us. 

Check this out:
[https://wiki.ubuntu.com/HowToEnableSCSIEmulationWithHoaryKernel26?highlight=%28scsi%29](https://wiki.ubuntu.com/HowToEnableSCSIEmulationWithHoaryKernel26?highlight=%28scsi%29)

Bottom line: I don't think the problem is with USB_STORAGE

---

### Post by GMachine_24 on 2006-03-23
Ok. I just was pointing out the only things that looked promising.

I pulled a list of CONFIG commands from a posting on another forum site - the person who posted these said he had a very difficult time getting his firewire to work under 2.4 and that he hadn't tried under 2.6. However, a user was attempting to get firewire running under 2.6 so this person posted all the processes he enabled to get firewire running under 2.4. I put them here just for "historical value" - if there is any. I did run each command and then the rescan-scsi and ended up with the same results we are getting after running the "load" script.

Here they are:

[KEEP IN MIND LINUX 2.4]
<code>
CONFIG_SCSI=m
CONFIG_SCSI_PROC_FC=y
CONFIG_BLK_DEV_SD=m
CONFIG_CHR_DEV_SG=m
CONFIG_SCSI_MULTI_LUN=m
CONFIG_IEEE1394=m
CONFIG_IEEE1394_PCILYNX=m
CONFIG_IEEE1394_OHCI1394=m
CONFIG_IEEE1394_VIDEO1394=m
CONFIG_IEEE1394_SBP2=m
CONFIG_IEEE1394_SBP2_PHYS_DMA=y
</code>

Anyway, I continue my quest. Thanks again for all your help. I do understand about Debian and Ubuntu releases and at least some of the differences. I'm, at this point, just brainstorming and not ruling anything out because usually anything that takes this long to fix . . . usually has a very simple solution. That's my experience, anyway.

Take care.

GM

---

### Post by GMachine_24 on 2006-03-23
Believe it or not..... the, er, 'darn' thing works. I am not sure I want to confess what I did but I was playing around with some commands and then I unplugged and then reconnected the firewire cable and . . . there was a box on my monitor labeled "WD 120GB FIRE" and I can read the files (even though the drive is an NFTS format drive).

I cannot believe it!!! <Sigh.>

Thank you for ALL YOUR HELP.

I WILL post the "what I did" to get it running as soon as I can replicate the procedure . . . and speaking of which . . . do I need to add a line to /etc/fstab so the drive is mounted on boot?

God, I just cannot believe this finally works!!

GM

I thought I should post this as my flag of victory:

<code>
user@ubuntu1:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: WDC WD12 Model: 00JB-00EVA0      Rev: 0.01
  Type:   Direct-Access                    ANSI SCSI revision: 02
user@ubunt1:~$
</code>


Success!!

---

### Post by Pragmatist on 2006-03-23
A  W  E  S  O  M  E  !  !  !  :) :)  I can't even believe it myself.  I feel like we won the superbowl or something :p 

Sometimes unplugging and then replugging works...I guess.  Yeah it would be nice if we could re-engineer what exactly happened.

As for how to handle the drive in general, yes I think making an entry to /etc/fstab is a good idea.  Read the man page:
```
man fstab
```

There might be some other things needed for a permanent setup just the way you want. (like udev hal, etc...)

Congratulations!

---

### Post by GMachine_24 on 2006-03-23
Ok, I am going to attach two text files. One is more-or-less a step-by-step of what I did . . . let's say just prior to the computer recognizing the firewire drive.

The second file is the command line printout. It begins after I ran the command you gave me to check on what SCSI components are installed in my kernel.

You can read the commands I used - and judge for yourself whether you think they enabled the drive.

Again, thanks for all your help. Right now, I am just enjoying the fact that I can see and read from the firewire drive. I think I will see about reformatting it, etc., tomorrow.

Cheers.

---

