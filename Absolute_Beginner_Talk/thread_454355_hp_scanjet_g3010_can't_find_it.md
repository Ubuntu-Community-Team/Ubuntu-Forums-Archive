---
title: "hp scanjet g3010 can't find it"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by cbaez55 on 2007-05-25
My nephew just installed linux ubuntu 6.10. I have this new scanner to restore old photos and slides. Will I have to reinstall windows to use it?:(

---

### Post by Pragmatist on 2007-05-25
Have a look at this:
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

What model/make scanner do you have?

---

### Post by cbaez55 on 2007-05-25
> **Pragmatist said:**
> Have a look at this:
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

What model/make scanner do you have?
I have a hp scanjet  G3010 that I just bought this week. The list of scanners on your link doesnt include g3010. thanks anyway.

---

### Post by Pragmatist on 2007-05-25
Sorry, I missed that you included the make/model in the subject line :oops:

Just because your model isn't in the list, which would make sense, by the way, if it is a brand new model, doesn't mean it won't work in Linux.  It looks like it works with MAC OSX which is a good sign that it works with Linux too.

Lets see if Linux recognizes the scanner when you plug it in:

With the scanner NOT plugged in, type this:
```
tail -f /var/log/messages
```


Then plug in the scanner and note any new lines on the screen.  Post those lines here.

---

### Post by cbaez55 on 2007-05-25
May 25 14:35:43 cheryl-desktop gconfd (root-5616): GConf server is not in use, shutting down.
May 25 14:35:43 cheryl-desktop gconfd (root-5616): Exiting
May 25 15:04:53 cheryl-desktop -- MARK --
May 25 15:24:54 cheryl-desktop -- MARK --
May 25 15:44:54 cheryl-desktop -- MARK --
May 25 16:04:54 cheryl-desktop -- MARK --
May 25 16:24:54 cheryl-desktop -- MARK --
May 25 16:44:54 cheryl-desktop -- MARK --
May 25 17:04:54 cheryl-desktop -- MARK --
May 25 17:18:36 cheryl-desktop kernel: [17191226.664000] usb 5-1: USB disconnect, address 3
I dont know what it means, but it's different.

---

### Post by cbaez55 on 2007-05-25
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 03f0:4205 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
cheryl@cheryl-desktop:~$ tail -f /var/log/messages
May 25 15:44:54 cheryl-desktop -- MARK --
May 25 16:04:54 cheryl-desktop -- MARK --
May 25 16:24:54 cheryl-desktop -- MARK --
May 25 16:44:54 cheryl-desktop -- MARK --
May 25 17:04:54 cheryl-desktop -- MARK --
May 25 17:18:36 cheryl-desktop kernel: [17191226.664000] usb 5-1: USB disconnect, address 3
May 25 17:22:44 cheryl-desktop kernel: [17191474.520000] usb 5-1: new full speed USB device using uhci_hcd and address 4
May 25 17:22:44 cheryl-desktop kernel: [17191474.660000] usb 5-1: not running at top speed; connect to a high speed hub
May 25 17:22:44 cheryl-desktop kernel: [17191474.704000] usb 5-1: configuration #1 chosen from 1 choice
May 25 17:22:53 cheryl-desktop kernel: [17191483.856000] usb 5-1: USB disconnect, address 4
I don't know what it means, but it's different

---

### Post by Pragmatist on 2007-05-25
Does this scanner require USB 2.0?  If it does, do you have USB 2.0 ports?

What exactly happens when you try this:
> **Using your scanner**

  Most of the time, Ubuntu will simply detect your scanner and you just be able to use it. To scan a document, you need to follow these steps: 
 [LIST=1]
[*]Place what you want to scan on the scanner 
[*]Go to Applications --> Graphics --> XSane Image Scanner 
[*]Alternately, pressing the scan button on the scanner should also work
[/LIST]

---

### Post by cbaez55 on 2007-05-26
How do I find out if I have 2.0 usb?

---

### Post by Pragmatist on 2007-05-26
> **cbaez55 said:**
> How do I find out if I have 2.0 usb?
What is the output of this:
```
discover usb
```

---

### Post by cbaez55 on 2007-05-26
bash: discover: command not found

---

### Post by Pragmatist on 2007-05-26
Hmmm.  Well, it is in the repositories.  You can install it using Synaptic.  Just do a search using the keyword "discover".  There is more than one package, but use the one with the ubuntu icon next to it (it is called "discover1"

In the meantime, you can also do this:

```
sudo lshw | grep usb
```

You should get output something like this:
> desktop:~$ **sudo lshw |grep usb**
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
        *-usb:0
           *-usbhost
                bus info: usb@1
                logical name: usb1
                **capabilities: usb-1.10**
        *-usb:1
           *-usbhost
                bus info: usb@2
                logical name: usb2
                **capabilities: usb-1.10**
              *-usb
                   bus info: usb@2:2
                   **capabilities: usb-1.10** scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=12.0MB/s
        *-usb:2
           *-usbhost
                bus info: usb@3
                logical name: usb3
                **capabilities: usb-1.10**
        *-usb:3
           *-usbhost
                bus info: usb@4
                logical name: usb4
                _**capabilities: usb-2.00**_
              *-usb
                   bus info: usb@4:3
                   _**capabilities: usb-2.00**_ scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s


I've put the relevant lines in bold.  Notice that I have both types of usb.  If I was using a device that required USB2.0 then I would want to use those USB ports and not the 1.10 ports.

---

### Post by cbaez55 on 2007-05-27
I typed that and I got capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
           *-usb:0
              *-usbhost
                   bus info: usb@5
                   logical name: usb5
                   capabilities: usb-1.10
           *-usb:1
              *-usbhost
                   bus info: usb@4
                   logical name: usb4
                   capabilities: usb-1.10
           *-usb:2
              *-usbhost
                   bus info: usb@3
                   logical name: usb3
                   capabilities: usb-1.10
           *-usb:3
              *-usbhost
                   bus info: usb@6
                   logical name: usb6
                   capabilities: usb-2.00
        *-usb:0
           *-usbhost
                bus info: usb@1
                logical name: usb1
                capabilities: usb-1.10
              *-usb UNCLAIMED
                   bus info: usb@1:2
                   capabilities: usb-2.00
        *-usb:1
           *-usbhost
                bus info: usb@2
                logical name: usb2
                capabilities: usb-1.10
My nephew split my computer 90-10 (windows xp has the 10 until I can use it on this side and get rid of xp. Works fine on xp.

---

### Post by Pragmatist on 2007-05-27
Great! You have USB 2.0 and USB 1.10  This can improve your speed if you plug the scanner into the USB 2.0 ports.  However, this was only the small part of the question I asked Back in post #7  of this thread.  More importantly, I asked what happens when you try this:

> **Using your scanner**

 Most of the time, Ubuntu will simply detect your scanner and you just be able to use it. To scan a document, you need to follow these steps: [LIST=1]
[*]Place what you want to scan on the scanner
[*]Go to Applications --> Graphics --> XSane Image Scanner
[*]Alternately, pressing the scan button on the scanner should also work[/LIST]

Did you try XSane yet?  If not, try it.  If you did, what exactly happens?

---

### Post by cbaez55 on 2007-05-27
I tried zane and " no device is available"  was the message I got.  I tried applications, , graphics,  xzane image  and I got " no device available"  while pushing buttons or not pushing them.

---

### Post by Pragmatist on 2007-05-28
After examining the SANE website, I found this entry on your scanner!

[http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=scanjet+3010&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=scanjet+3010&bus=any&v=&p=)

> ScanJet G3010 USB 0x03f0/0x4205  [COLOR=#ff9000]basic[/COLOR]   Not tested yet. Seems to be equal to hp scanjet 4370

The HP scanjet 4370 uses the hp3900 backend.  I did a search for hp3900 in Synaptic and found this package:  **libsane-extras**

So there is good news and bad news.  Good news is your scanner probably works with Linux.  Bad news is it hasn't been tested yet.  However, it doesn't cost you anything to install the above package (libsane-extras).  And, if it works, you can update the SANE database to help others who have your same device!

---

### Post by Malta paul on 2007-05-28
Just for info.
I have a HP jetscan 3500c scanner. It did work with xsane, the text was OK but the photo scan was very dark. I reinstalled windows 2000 on a 10GB fat32 partition and installed the HP windows drivers.
So now I scan in windows then reboot into Ubuntu and copy my files there. ;)

---

### Post by cbaez55 on 2007-05-29
I went to the link you supplied and found the 3900 download. I downloaded, installed and rebooted.   Unfortunately, it still says "no device found".  You also answered my question that I didn't ask yet.  I wondered if I could scan in windows and move item to ubuntu. With the 90-10 split my nephew installed, I can do that. I will keep trying to make the scanner work on ubuntu so I can toss Windows all together. Thank you.[http://ubuntuforums.org/images/icons/icon7.gif:D](http://ubuntuforums.org/images/icons/icon7.gif:D)

---

### Post by erikringmar on 2007-12-20
I too have been scratching my head over this one.  Now however it seems SANE supports the ScanJet G3010 scanner (except that I haven't managed to get the slide scanner operational yet).  Download this package -- [http://sourceforge.net/project/downloading.php?group_id=150599&use_mirror=jaist&filename=hp3900-series_0.10.tar.gz&42681600](http://sourceforge.net/project/downloading.php?group_id=150599&use_mirror=jaist&filename=hp3900-series_0.10.tar.gz&42681600) --  and install according to instructions.

yours,

Erik

---

### Post by bimargulies on 2007-12-25
To use the 3900 backend, you have to edit hp3900.conf to include the USB device ID of the G3010, or it won't be recognized.

When I did this, sadly, the result was scans of 100% black pixels.

---

### Post by bimargulies on 2007-12-25
Aha! If you download from the link, you get a working version. The hp3900 that is part of the current gutsy / universe stream isn't good enough.

---

### Post by walard on 2008-01-27
I install now scanjet G3010. I installed libsane and libsane-extras. Then i dowlanded  th last patch 
hp3900-series 0.11 from: [http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)
and i aplied patch.  Then this scanner is functional.  	:)

---

### Post by Fechter on 2008-02-01
Last month I wrote to HP in order to ask them if ther were any drivers released for linux, but their resonse was that still  hey have not released drivers for linux; I tried with HPLIP, but did not suceed-
HP said sth like they were looking forward to releasing drivers this year/2008/... check if XSane are testing any, time will show.
By the way I tried using the windows drivers in the one cd on linux with Wine, but, as I expected,
no good result. I will follow the advice given, lets see...

---

### Post by John_T on 2008-02-02
This *almost* worked for me.  Then I got a "Failed to open device" error message.

A little more searching dug up **[this thread]("http://ubuntuforums.org/showpost.php?p=1657133&postcount=5")**, with great advice from **DingDong** about changing the permissions for the USB device.

See the thread for details, but essentially you have to:

```
sudo chmod a+w /dev/bus/usb/xxx/yyy
```

where:
xxx is the USB bus number
yyy is the USB device number

Now my G3010 is working just fine under Ubuntu 7.10 !

---

