---
title: "Doesn't Ubuntu support serial ports?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-05-23
Good day to all....
I was brousing through the OS tonight, thinking about my next thing to tackle...and I noticed in Applications>System Tools>System Information (Hardinfo)  there is no mention of any serial ports...it does strike me as being odd...

See, I have a digital camera (Epson Photo PC 550) that connects thru the 9 pin serial port...It's one of my last few MS barriers...BESIDES needing a new camera (one in the 21st century would be grand) , I'm curious why there are no serial ports configured on my 'puter. If there is a way to get one detected or install one, I'd appreciate the help. 

My hope is to access the flash card on the camera as one would access a flash disk or a USB device, as the software that came with the camera is worthless without the 'ol MS.

---

### Post by Sef on 2006-05-23
> I'm curious why there are no serial ports configured on my 'puter. If there is a way to get one detected or install one,.... 

Serial ports are yesterday's technology, so they are fading out like PS/2 ports and floppy disks.

> I'd appreciate the help. 

What happens if anything when you hook up your camera?

> My hope is to access the flash card on the camera as one would access a flash disk or a USB device,

Why not get a flashcard reader?

---

### Post by djsroknrol on 2006-05-23
Hi Sef...

Please don't take offence of my responses here....

1)
> Serial ports are yesterday's technology, so they are fading out like PS/2 ports and floppy disks.
Understandable..;), but it doesn't answer my question...

2)
> What happens if anything when you hook up your camera?
Nothin, my friend...that's why I'm asking the question here...

3)
> Why not get a flashcard reader?
I think, unless there IS serial support in Ubuntu, a reader would be in line for purchace...

---

### Post by argie on 2006-05-23
I think Ubuntu does recognize serial ports. 

If it's those COM1, COM2, etc... they're on /dev/ttyS0 /dev/ttyS1 etc...
or something like that.

I got my old modem running (partially), and that modem connects on a serial port (COM1 to be exact, and it was recognised on /dev/ttyS0 by gnome-ppp)

So some sort of support does exist. About your digicam issue I really don't know sorry :(

---

### Post by dmizer on 2006-05-23
here's some information i found with google on your camera that will likely be of interest to you: [http://www.lightner.net/lightner/bruce/ppc_use.html](http://www.lightner.net/lightner/bruce/ppc_use.html)

---

### Post by Sef on 2006-05-23
> here's some information i found with google on your camera that will likely be of interest to you: [http://www.lightner.net/lightner/bru...e/ppc_use.html](http://www.lightner.net/lightner/bru...e/ppc_use.html)

The url is not working.  Getting a 404 message.

---

### Post by Ramses on 2006-05-23
[Here's]("http://www.lightner.net/lightner/bruce/ppc_use.html") dmizer's link hopefully working. 

[Here's]("http://packages.ubuntulinux.org/warty/graphics/photopc") ubuntu photopc package. If you have universe in your repository sources then just: ```
sudo apt-get install photopc
```

---

### Post by Sef on 2006-05-23
Ramses, thank you. It works

---

### Post by dmizer on 2006-05-23
[QUOTE=Sef]The url is not working.  Getting a 404 message.[/QUOTE]
fixed my post ... musta clicked the mouse one too many times.

---

### Post by djsroknrol on 2006-05-23
Thanks Sef....

The link does work, and it's more than I hoped for (I keep saying Ubuntu rocks!!). Now, if I could only get the port working...How can I get   "/dev/ttyS0"  working?...anyone?

---

### Post by pbaehr on 2006-05-23
Just to give you a heads up, I use a serial port for my X10 lighting controls and for some reason my serial ports are assigned to /dev/ttyS15 and /dev/ttyS14 or something like that. I don't remember exactly because they changed recently when I reinstalled Dapper. I'm not sure why it picks these seemingly random numbers but I figured I should tell you that in my experience you will not always find what you are looking for on ttyS0 or ttyS1.

---

### Post by djsroknrol on 2006-05-23
Sorry for the bump folks...

I'm so close, I can see my camera snapping pics again in Ubuntu...anyone have any idea how to enable my ttyS0 ?

---

### Post by Jussi Kukkonen on 2006-05-23
[QUOTE=djsroknrol]Good day to all....
I was brousing through the OS tonight, thinking about my next thing to tackle...and I noticed in Applications>System Tools>System Information (Hardinfo)  there is no mention of any serial ports...it does strike me as being odd...
[/QUOTE]

Look at System --> Administration --> Device Manager.

You should find your COM ports on the root level -- mine says "16650A-compatible COM port", and seems to have device file "/dev/ttyS0".

---

### Post by az on 2006-05-23
If your camera is supported by libgphoto2, it will work fine.  Many older camers which are supported by gphoto2 are serial-only.

---

### Post by az on 2006-05-23
[QUOTE=djsroknrol]anyone have any idea how to enable my ttyS0 ?[/QUOTE]


[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Your camera is on the list.  If you plug it in, open up the image viewer and click on "connect to camera" (or something like that, I am not in front of an ubuntu box right now) you should see your stuff.

If your serial port is really not working, it's probably dissabled in the bios.  There are no serial port chipsets that have no linux support.  But I suspect that nothing is showing up in the device manager because nothing is hooked up to the ports at the time.

---

### Post by djsroknrol on 2006-05-23
Hi again gang,

Well gthumb has the camera in the list alright...there are untold tty's in the drop down list. The problem still is the port IMO...it times out making a connection with the camera...I have another cable and both work in MS. Is there a way to test the port thru terminal possibly?

BTW, it shows up in device manager....

---

### Post by djsroknrol on 2006-06-24
Well...I got back on this serial port thing again (bored, curious,etc). I left it alone for awhile, but it's bugging me...here is a little more snooping:

```
bob@server:~$ sudo setserial -g /dev/ttyS0
Password:
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4

```

the strange thing is this one:

```
ob@server:~$ cat /proc/interrupts
           CPU0
  0:    2320742          XT-PIC  timer
  1:        740          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:          0          XT-PIC  uhci_hcd:usb2
  5:          0          XT-PIC  ehci_hcd:usb4
  7:          1          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:          0          XT-PIC  acpi
 10:       2086          XT-PIC  uhci_hcd:usb3, VIA8233
 11:     137870          XT-PIC  uhci_hcd:usb1, eth0, radeon@pci:0000:01:00.0
 12:      63827          XT-PIC  i8042
 14:      16269          XT-PIC  ide0
 15:      41562          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0
bob@server:~$

```

anyone have any ideas on this one? Why doesn't it show up even after a reboot? I've changed permissions for ttyS0 as root.

Any help would be appreciated.

---

### Post by djsroknrol on 2006-06-25
One last bump...things just fly by and disappear in these forums lately....

---

### Post by djsroknrol on 2006-06-25
And....one last image to show that it is trying to communicate with the program....

Someone must have an idea...I think it might be a speed issue, but I wouldn't know where to set it....

---

### Post by fenian on 2006-08-17
Try this
open terminal and type

sudo chmod a+rw /dev/ttyS0

I need to do this to get mythtv talking to my sat. box through serial connection.

---

### Post by djsroknrol on 2006-08-17
> **fenian said:**
> Try this
open terminal and type

sudo chmod a+rw /dev/ttyS0

I need to do this to get mythtv talking to my sat. box through serial connection.

Thanks fenian...I had given up on getting my camera to work and purchaced a card reader...I didn't think about trying chmod, but I will tonight....

---

### Post by djsroknrol on 2006-08-17
Well fenian...I got a little closerthis time...I got communication with the camera, but it only lasted a few seconds on the camera control screen...and then I got this:

Anyone else have any ideas before I give up again?

---

