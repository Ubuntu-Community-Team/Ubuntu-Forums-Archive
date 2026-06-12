---
title: "One person's Synopsis for MBA ...."
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-05
Hi, I pretty much have my MBA (macbook air) going to my satisfaction. So I thought it might help to put all of my findings into one post.

-First, Install [rEFit]("http://refit.sourceforge.net"), AND after doing that, run the standard MAC Software update because there is a rEFit software update that your Mac will run there.   

-I'm dual booting; I got started here: [https://help.ubuntu.com/community/Macbook_Air?highlight=(Air)|(Macbook](https://help.ubuntu.com/community/Macbook_Air?highlight=(Air)|(Macbook)) This helps you get the wireless and the sound going as well.

- After installing rEFit, doing your partitions and installing Ubuntu, one still has to 'Syncronize your partitions'. Otherwise Ubuntu might not boot correctly from the rEFit menu, even though everything looks right. This is done right at the rEFit menu with the Partition Editor. Just click the partition editor and it should by default ask you if you'd like to sync your partitions. Just type 'y' for yes and that's all. 

- I've had NO Problems with the MBA Superdrive, even after just installing Ubuntu and rebooting, it worked fine;

- I don't know yet if the touchpad works with all its features, BUT, and this is a real plus for me, there seem to be NO Problems typing  - that is, there is no jumpy cursor like I've encountered in Ubuntu on other laptops that have a touchpad. (now that I think about it, all the other laptops were windows-based)

- As the tutorial above mentions, iSight works right out of the box. Download the program 'Cheese' using Add/Remove. 

-Bluetooth works right out of the box.I had to right-click the Bluetooth icon on the top task bar, choose Preferences and choose 'Visible and Connectable for other devices'. It actually detected my white Apple mouse. 

This is all I can think of for now. Hopefully this will help some folks...Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-05
> **Brightbelt said:**
> - I don't know yet if the touchpad works with all its features, BUT, and this is a real plus for me, there seem to be NO Problems typing  - that is, there is no jumpy cursor like I've encountered in Ubuntu on other laptops that have a touchpad. (now that I think about it, all the other laptops were windows-based)It doesn't see here for a utility to get things working better:
[http://tannewt.org/touch/](http://tannewt.org/touch/)

> **Brightbelt said:**
>  - As the tutorial above mentions, iSight works right out of the box. Download the program 'Cheese' using Add/Remove.This is very interesting... most of us have to load firmware. Can you post the output of lsusb?

---

### Post by Brightbelt on 2008-05-05
Thanks for the reality-check Cyber. For me on the Cheese program, the program gets a very good iSight video preview; so with that, plus the Community-based tutorial, I assumed the issue was solved.

But as you said, it's not so true...I recorded a video and then played it. It seemed to record ok, but it played back very, very fast AND with No sound at all. (I have run the sound thing already in the terminal, so I do have sound in general).

Also I want to qualify my experience of Bluetooth. It seems to work after I tweak the Preferences, but it's not clear to me anyway that one setting consistently works. It seems to get activated by me changing something in there just in general. So with apologies about being vague here, I'll back away from my full endorsement that Bluetooth flies well right out of the box. 

Cyber, if you have a link for the iSight fix, I'd appreciate it.
No wait, I got it. No problem....The lsusb code is coming up.


Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-05
Oh and here's the lsusb for you:

```
Bus 007 Device 003: ID 05ac:8505 Apple Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 05ac:0223 Apple Computer, Inc. 
Bus 005 Device 002: ID 05ac:8242 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 010: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 007: ID 05ac:820b Apple Computer, Inc. 
Bus 003 Device 006: ID 05ac:820a Apple Computer, Inc. 
Bus 003 Device 005: ID 05ac:8210 Apple Computer, Inc. 
Bus 003 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by cyberdork33 on 2008-05-05
I think you misunderstood. If you can see an image from your iSight, your camera is 100% completely working correctly. I would guess that the recording error is likely a bug in cheese or gstreamer. I would check the cheese homepage, and maybe contact the devs or file a bug. [http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)

I was only interested in the lsusb output because it DOES work without firmware loading... I can see that it is a new hardware ID... I think I know which one is your iSight anyway... Can you give some more details? This is just for reference purposes.... Make sure you are in your home directory in the terminal:
```
cd
```
then run
```
sudo lsusb -d 05ac:8505 > iSightDetails.txt
```

You should then have a file in your home directory called "iSightDetails.txt" that you can upload as an attachment.

---

### Post by Brightbelt on 2008-05-05
Thanks, Cyber. Here's the attachment....Thanks, Frank B.

---

### Post by poisonfist on 2008-05-05
Hi, I also have installed Hardy on my MacBook Air and seemed like most of the important stuff working.  I followed the same instructions you did.  It seems the microphone is not working though, I tried a skype session with my mother (in Japan) and got the video going but although her voice came through fine, she did not hear anything from us.  When I try skype booting into Leopard, it everything works fine (as it should) so there definitely is a problem with the mic.

---

### Post by cyberdork33 on 2008-05-05
> **Brightbelt said:**
> Thanks, Cyber. Here's the attachment....Thanks, Frank B.

Sorry, I forgot something... I need the verbose output, try this one.
```
sudo lsusb -d -vv 05ac:8505 > iSightDetails.txt
```

---

### Post by Brightbelt on 2008-05-05
Ok, Cyber,...is this it?

```
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program

```

I hope that's what you wanted. I'll attached the txt file again just in case....Frank B.

Well, I can't get the txt to upload. Let me know if you need that again.

---

### Post by Brightbelt on 2008-05-05
Yes, Poisonfist, the audio does not work with my iSight either; I should repeat, however, that as far as my regular laptop audio goes, I did get that working successfully by following the community tutorial.

...Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-05
no, sorry, I don't have access to a Linux machine to test this out. you should get something similar to the first output, but with a lot of other detailed information related to the device as well.

and on the mic, you might need to enable a "capture" channel and increase it's level to get the mic to work. run 'alsamixer' to adjust all the available channels.

---

