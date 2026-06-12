---
title: "Camera mounting issues..."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by dwdude on 2007-07-31
I have an Olympus D-435 digital camera that isn't mounting correctly...

I plug the camera into the usb cord, then on the camera, I select "PC" which puts it into usb mode.

gThumb pops up and it tries to detect a camera, but it always detects the Olympus C-370Z. Also, when I have photos on the camera, gThumb says it doesn't (which would make sense, considering it's detecting the wrong camera)

I clicked on the camera icon so I could look at the catalog, choosing my own camera to use, but my camera wasn't on the list!! Which is really strange because it was working once before...

My iPod mounts just fine, it's on the desktop and working.

I had it working ONCE. The camera popped up on the desktop and it was mounted, but then I (stupid new linux user) just unplugged the camera from the cord, not unmounting it first.

I've tried remounting it, but, to be honest, am sooo lost.

```
$ lsusb
Bus 004 Device 002: ID 05ac:1209 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 07b4:0109 Olympus Optical Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 054c:0154 Sony Corp. 
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

If you need any other info, just ask.

But be a little specific as to what you want...

I've had Ubuntu (Feisty Fawn btw) for like.. 2 weeks? So I'm sorta a noob to it. Although I did get the eyetoy working nicely... :D

Anyways, help please?

---

### Post by Pragmatist on 2007-07-31
install **gphoto2** (it is in the repositories, if you use synaptic, just use its search feature and type gphoto2 as the keyword)

Then, in a terminal, with the camera plugged in and turned on,  type this:

```
gphoto2 --list-ports
```

Post  the output here.

---

### Post by dwdude on 2007-08-02
```
$ gphoto2 --list-ports
Devices found: 10                                                              
Path                             Description
--------------------------------------------------------------
disk:/media/DAVID                Media 'DAVID'                   
disk:/                           Media 'Volume (ext3)'           
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:                             Universal Serial Bus            
usb:004,009                      Universal Serial Bus            
usb:003,005                      Universal Serial Bus 

```

Media 'DAVID' is my iPod.

A pop up came up, saying "Unable to mount device." When I plugged in my camera and put into USB mode.

I clicked on details and it said something about... "/sdc1 does not exist."

---

### Post by Pragmatist on 2007-08-02
edit: see next post

---

### Post by Pragmatist on 2007-08-02
With the camera plugged in and turned on, type this:
```
**gphoto2  --list-folders  --port usb:**  
```

---

### Post by dwdude on 2007-08-02
```
$ gphoto2  --list-folders  --port usb:
                                                                               
*** Error ***              
An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x7b4, product 0x109). Make sure this device is connected to the computer.
*** Error (-2: 'Bad parameters') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --list-folders --port "usb:"

Please make sure there is sufficient quoting around the arguments.

```

---

### Post by Pragmatist on 2007-08-02
Your camera is definitely not being recognized (your probably saying, "duh, I know that already", but I want to be sure :) )

What is "usb mode"?  I just turn my camera on.

---

### Post by dwdude on 2007-08-02
Well, I have the camera off, right?

Then I plug it in, and it turns itself on.

A menu pops up, and I click on "PC" 
It has another option which is "print" 

PC mode (on windows) attached the camera automatically as an external drive, allowing me to browse the folders to find the pictures. 

Print would automatically print the pictures on the camera out...

*gets an idea*

Haven't tried the "print" option before..

EDIT: For some VERY odd reason, the "print" option allows me to view the photos on the camera and import them... Still detecting itself as a different camera... Same popup, except it shows the pictures... Weird? I agree.

---

### Post by Pragmatist on 2007-08-02
> **dwdude said:**
> Well, I have the camera off, right?
....
A menu pops up, and I click on "PC" 
It has another option which is "print" 
....

What happens if you don't select anything.  Just plug it in, and then run the last command I gave you (it probably won't matter, why not try it?)

---

### Post by Pragmatist on 2007-08-02
> **dwdude said:**
> 
EDIT: For some VERY odd reason, **the "print" option allows me to view the photos on the camera and import them...** Still detecting itself as a different camera... Same popup, except it shows the pictures... Weird? I agree.

Does this mean your problem is solved?

---

### Post by dwdude on 2007-08-02
Well, this way works... But mounting it would be a lot better.

The computer detects it, but it's not being detected as a camera or something that is mountable.

The command that you told me shows the same thing, but lsusb shows:

```

$ lsusb
Bus 004 Device 012: ID 05ac:1209 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
**Bus 003 Device 041: ID 07b4:0109 Olympus Optical Co., Ltd **
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by Pragmatist on 2007-08-02
> **dwdude said:**
> Well, this way works....
Please explain to me exactly what "this way" is.  What program are you using to import the photos?

---

### Post by dwdude on 2007-08-02
Well, when I use the "Print" option, gThumb pops up and shows pictures on the camera (although being detected as a different camera)
That is "this way" and it works..

Using the "PC" option, gThumb pops up, but it says there aren't any photos on the camera when there really is.

gphoto2 isn't doing anything.

The first time I plugged it in, I used the "PC" option (which I always used), pictures were found (don't remember if it was the right camera detected or not), I was able to import them, and there was a drive on the desktop, allowing me to browse the camera.
**This is what I'm trying to achieve.**

But I didn't safely disconnect the camera, so now nothing comes up on the desktop.

---

### Post by Pragmatist on 2007-08-02
Try this:

1.) Turn off and unplug the camera.

2.) Type this in a terminal:
```
tail -f /var/log/messages
```

3.) Plug in the camera and set to "print mode"

4.) Look at the terminal for messages.

5.) Post the messages here.

---

### Post by dwdude on 2007-08-02
By the way, I have to thank you for all your help so far :D

```
Aug  1 23:34:41 david kernel: [111439.374240] usb 3-2: USB disconnect, address 41
Aug  1 23:47:38 david kernel: [112214.566056] usb 3-1: new full speed USB device using uhci_hcd and address 42
Aug  1 23:47:38 david kernel: [112214.763754] usb 3-1: configuration #1 chosen from 1 choice

```

---

### Post by Pragmatist on 2007-08-02
Now that we know that "print mode" works, I want to try gphoto2 again to find the port:
Again, turn off, unplug, plug in, turn to "print mode" and then type:
```
gphoto2 --list-ports
```

Also, how many USB devices to you have attached to your system right now?  What are they?

---

### Post by dwdude on 2007-08-02
```
$ gphoto2 --list-ports
Devices found: 10                                                              
Path                             Description
--------------------------------------------------------------
disk:/media/DAVID                Media 'DAVID'                   
disk:/                           Media 'Volume (ext3)'           
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:                             Universal Serial Bus            
usb:004,012                      Universal Serial Bus            
usb:003,042                      Universal Serial Bus

```

I have my iPod, mouse, and camera plugged into usb. Keyboard is usb as well, but it's using an adapter allowing it to plug into a serial port...

[http://www.coolgear.com/images/364966pro.jpg](http://www.coolgear.com/images/364966pro.jpg) Almost like that, but it is much smaller and only plugs into the mouse part (green)
EDIT: It's the opposite of that.. Male into mouse part, female usb.. Understand?

---

### Post by Pragmatist on 2007-08-02
Please post the result of this:
```
ps -ef |grep gnome-volume-manager
```

This next command will bring up a window.  Tell me what you see under the "cameras" tab:
```
gnome-volume-properties
```

---

### Post by dwdude on 2007-08-02
```
$ ps -ef |grep gnome-volume-manager
david     5583     1  0 Jul31 ?        00:00:00 gnome-volume-manager --sm-client-id default4

```


It has Import digital photos when connected checked and for command, it shows:
```
gnome-volume-manager-gthumb %h
```

---

### Post by Pragmatist on 2007-08-02
Next, type this:
```
gconf-editor
```

Once the window opens, go to Edit-->Find
Under "search for" type "camera"
Make sure both boxes are checked ("search also in key names", "search also in key values")

You'll see the results of your search in the bottom of the window.  Ignore entries that contain the word "schemas".  You should get two lines that look like this (bear in mind that, although these look like paths to files, they are not.  It is just a hierarchy that gconf uses)  We are not going to change anything yet.  We just are looking for information:
[B]/desktop/gnome/volume-manager/prompts/camera_import_photos
/apps/gthumb/dialogs/photo_importer/delete_from_camera

[/B]Click on this one and tell me about any entries that do not have a "0":
**/desktop/gnome/volume-manager/prompts/camera_import_photos**

Click on this one, and tell me the model and port
**/apps/gthumb/dialogs/photo_importer/delete_from_camera**

---

### Post by dwdude on 2007-08-02
**/desktop/gnome/volume_manager/prompts/camera_import_photos** key has this:

camera_import_photos and the value is: 6    

Model is **Olympus C-310Z** and the port is **usb:**

---

### Post by Pragmatist on 2007-08-02
I just read an old bug report (pre-dapper) where some people had the same problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/37694](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/37694)

The above references this guide, and I think you should follow its suggestions and tell us your results:

[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

---

