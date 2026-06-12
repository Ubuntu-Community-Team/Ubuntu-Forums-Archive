---
title: "pda synching, is it possible?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Xiequn on 2007-05-22
Good evening, I've just this afternoon installed feisty on my dell inspiron 630m laptop.
Mostly good, although some trouble with my printer and my HP 6515 pda.
As I use these 2 things everyday because I need them.
The pda/pilot daemon takes me thru 'device settings' so I choose usb, leave all the others as is, next is > yes to > has this device been synched before because I've done this every day, but is that what the question means?
the reason I doubt is because the very next screen says;
> initial sync
about to retrieve owner name and ID from the PDA
please put PDA in cradle (dev/pilot) and press HotSync button

Well, to my knowledge I don't have a hot-sync button.

Nothing further happens as the daemon waits for my button press which is never coming.
How very circular.
I assume I need to download/install something?
I'd really rather not have to return to XP (shudder)
Any ideas? Please
expectantly hopeful.

---

### Post by bcw on 2007-05-22
> **Xiequn said:**
> my HP 6515 pda

Hello,

I believe that device runs some form of Windows, and you want to look into 'synce' or some similar name.  The 'pilot' device and kpilot work with Palm OS PDAs, like the Palm, Handspring Visor, Sony Clie (my device), etc.

Search on something like 'Linux WinCE' or 'linux Windows Mobile' or whatever your device calls it's operating system.

Cheers,
Bret

---

### Post by Xiequn on 2007-05-22
Hi Bret, thanks for your help. that link was quite  complicated but it gave me ideas and I looked in this;[HTML]http://doc.gwos.org/index.php/Pocket_PC_Evolution[/HTML] and it went well......up to a point.
> dmesg shows my pda as > attached to ttyUSB0 
but the terminal gives me this;
> xiequn@pearlgardens:~$ sudo synce-serial-config ttyUSB0

ERROR:

synce-serial-config was unable to find a character device named "ttyUSB0"

Run "synce-serial-config --help" to get help. and then this
> xiequn@pearlgardens:~$ sudo synce-serial-config --help

Syntax for synce-serial-config:

  synce-serial-config serial-device [local-ip-address:remote-ip_address [DNS-server-name]]

  The serial-device specifies the name of your serial port device.

  These are the port names on Linux:

    ttyS0  The first serial port
    ttyS1  The second serial port
    ...

  You can also connect via an infrared connection (IrDA). This requires
  that you already have irattach running.

    ircomm0  The first IrDA communication port

  Please send corrections and updates to the above information to the
  SynCE development mailing list: [email]synce-devel@lists.sourceforge.net[/email]

  If you do not provide the local_ip_address:remote_ip_address parameter,
  synce-serial-config will use 192.168.131.102:192.168.131.201.

  If you want to specify these addresses yourself, you may want to read
  about the same option on the man page for pppd. 
so I tried ttys0 but without success, ditto for ttys1, in that it runs and finishes and says its waiting for the device but nothing happens.
followed this with;
> xiequn@pearlgardens:~$ sudo synce-serial-config ttys0

You can now run synce-serial-start to start a serial connection.

xiequn@pearlgardens:~$ sudo synce-serial-start

synce-serial-start is now waiting for your device to connect

xiequn@pearlgardens:~$ synce-pstatus
synce-pstatus: Could not find configuration at path '(Default)'

so i ran this;
> xiequn@pearlgardens:~$ synce-matchmaker create INDEX
[synce_info_from_file:51] unable to open file: /home/xiequn/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI
just to see what would happen. the file can't be opened because it doesn't exist. I looked for it.
well, I reckon I'm closer but now I don't know the next step.

---

### Post by Inxsible on 2007-05-22
Since you tried with Evolution, try these links, these worked for my W810i
 
I know your phone is different and everything...but mebbe you might get a few pointers in the right direction
 
[http://ubuntuforums.org/showthread.php?t=438896&highlight=w810i](http://ubuntuforums.org/showthread.php?t=438896&highlight=w810i)
 
[http://ubuntuforums.org/showthread.php?t=376709&highlight=w810i](http://ubuntuforums.org/showthread.php?t=376709&highlight=w810i)
 
[http://ubuntuforums.org/showthread.php?t=242932&highlight=wammu](http://ubuntuforums.org/showthread.php?t=242932&highlight=wammu)
 
[http://ubuntuforums.org/showthread.php?t=366877&highlight=w810i](http://ubuntuforums.org/showthread.php?t=366877&highlight=w810i)
 
I hope that helps !

---

### Post by bcw on 2007-05-25
Hi,

```
xiequn@pearlgardens:~$ sudo synce-serial-config ttyUSB0
```

You almost certainly want:
```
xiequn@pearlgardens:~$ sudo synce-serial-config /dev/ttyUSB0
```

or perhaps /dev/ttyUSB1

All devices are found under '/dev'.  It's sloppy of the coder not to make that obvious in the help messages.

I'm curious that dmesg offered 'ttyUSB0' without the /dev part of the path - is there another message line nearby in the output with the full path?

In any case, give that a try.

Cheers,
Bret

---

### Post by Xiequn on 2007-05-29
Hi Bret, sorry to take so long but Ive been flat out like a lizard drinking.
I tried the new code but got the same error.
here's part of dmesg
[ 1534.564000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 1534.728000] usb 4-1: configuration #1 chosen from 1 choice
[ 1535.104000] usbcore: registered new interface driver usbserial
[ 1535.104000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1535.104000] usbcore: registered new interface driver usbserial_generic
[ 1535.104000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 1535.116000] drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
[ 1535.116000] drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
[ 1535.116000] ipaq 4-1:1.0: PocketPC PDA converter detected
[ 1535.120000] usb 4-1: PocketPC PDA converter now attached to ttyUSB0
[ 1535.120000] usbcore: registered new interface driver ipaq
[ 1552.976000] usb 4-1: USB disconnect, address 2
[ 1552.976000] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 1552.976000] ipaq 4-1:1.0: device disconnected
and then it says
[ 1558.032000] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 1560.956000] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 1563.872000] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 1566.792000] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 1569.828000] usb 4-1: new full speed USB device using uhci_hcd and address 7
[ 1572.748000] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 1575.820000] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 1578.740000] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 1581.808000] usb 4-1: new full speed USB device using uhci_hcd and address 11
[ 1584.696000] usb 4-1: new full speed USB device using uhci_hcd and address 12
[ 1587.764000] usb 4-1: new full speed USB device using uhci_hcd and address 13
[ 1590.684000] usb 4-1: new full speed USB device using uhci_hcd and address 14
[ 1593.756000] usb 4-1: new full speed USB device using uhci_hcd and address 15
[ 1596.640000] usb 4-1: new full speed USB device using uhci_hcd and address 16
[ 1599.712000] usb 4-1: new full speed USB device using uhci_hcd and address 17
[ 1602.632000] usb 4-1: new full speed USB device using uhci_hcd and address 18
[ 1605.704000] usb 4-1: new full speed USB device using uhci_hcd and address 19
[ 1608.592000] usb 4-1: new full speed USB device using uhci_hcd and address 20
[ 1611.664000] usb 4-1: new full speed USB device using uhci_hcd and address 21
[ 1614.584000] usb 4-1: new full speed USB device using uhci_hcd and address 22
[ 1617.652000] usb 4-1: new full speed USB device using uhci_hcd and address 23
[ 1620.572000] usb 4-1: new full speed USB device using uhci_hcd and address 24
[ 1623.608000] usb 4-1: new full speed USB device using uhci_hcd and address 25
[ 1626.528000] usb 4-1: new full speed USB device using uhci_hcd and address 26
[ 1629.444000] usb 4-1: new full speed USB device using uhci_hcd and address 27
[ 1632.516000] usb 4-1: new full speed USB device using uhci_hcd and address 28
[ 1635.552000] usb 4-1: new full speed USB device using uhci_hcd and address 29
[ 1638.472000] usb 4-1: new full speed USB device using uhci_hcd and address 30
[ 1641.388000] usb 4-1: new full speed USB device using uhci_hcd and address 31
[ 1644.460000] usb 4-1: new full speed USB device using uhci_hcd and address 32
[ 1647.344000] usb 4-1: new full speed USB device using uhci_hcd and address 33
[ 1650.416000] usb 4-1: new full speed USB device using uhci_hcd and address 34
[ 1653.336000] usb 4-1: new full speed USB device using uhci_hcd and address 35
[ 1656.404000] usb 4-1: new full speed USB device using uhci_hcd and address 36
[ 1659.324000] usb 4-1: new full speed USB device using uhci_hcd and address 37
xiequn@pearlgardens:~$ 
It doesn't mean much to me.
Thanks for your help.
Jen

---

### Post by Xiequn on 2007-05-30
I've been going thru the synce site instructions, from scratch, and got to this part;
 > Find out USB information about your device

Make sure your device is not connected to your computer before following these steps:

   1. Save a list of the devices currently on USB by running the command:

          cat /proc/bus/usb/devices > /tmp/before

   2. Connect your device to your computer.
   3. Save the updated list to a new file:

          cat /proc/bus/usb/devices > /tmp/after

   4. Disconnect your device.
   5. Compare the two lists by running the command:

          diff /tmp/before /tmp/after

You should get an output like the following:

23a24,31
> T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 10 Spd=12  MxCh= 0
> D:  Ver= 1.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS= 8 #Cfgs=  1
> P:  Vendor=049f ProdID=0003 Rev= 0.00
> C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
> I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ipaq
> E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
> E:  Ad=82(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms
>

Important parts of the text have been highlighted in red. 

I got nothing from this, no output, nada. 
So I looked in /proc/bus/usb/devices and found nothing. Devices says it has zero bytes, I opened it and yes its empty.
So, where is the information kept now? I have a printer on usb, always, so that at least should show, shouldn't it?
this is very confusing:(
Thanks, Jen

---

