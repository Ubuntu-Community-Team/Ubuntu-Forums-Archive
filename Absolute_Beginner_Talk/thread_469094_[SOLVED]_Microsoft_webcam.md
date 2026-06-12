---
title: "[SOLVED] Microsoft webcam"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-06-09
Hello,

Is there any way to use my Microsoft webcam to chat online? The model is VX-6000.

Thanks for your help!

---

### Post by hartz on 2007-06-09
See whether your webcam is supported by Linux.

You can search the web for Linux hardware compatibility <cameramodel>

or better, enter the command lsusb into a terminal, find the ID strings, it looks like thjs:
```
Bus 002 Device 003: ID 1307:0163 
```

So then search for [COLOR="Red"]Linux Webcam 1307:0163 support[/COLOR], Though you should use your own ID strings.

---

### Post by djmaxmalta on 2007-06-09
> **hartz said:**
> See whether your webcam is supported by Linux.

You can search the web for Linux hardware compatibility <cameramodel>

or better, enter the command lsusb into a terminal, find the ID strings, it looks like thjs:
```
Bus 002 Device 003: ID 1307:0163 
```

So then search for [COLOR="Red"]Linux Webcam 1307:0163 support[/COLOR], Though you should use your own ID strings.
erm can u explain it in a simple way for us linux learner or beginners???

my creative cam didn't work on ubuntu

but my cheaper and less resoluted cam from sweex workes on a program but not on amsn cos of firewall or reuter probs but hey atleast i cam on and had some color issues come on a blue hulk
???

---

### Post by the8thstar on 2007-06-14
> See whether your webcam is supported by Linux.

You can search the web for Linux hardware compatibility <cameramodel>

or better, enter the command lsusb into a terminal, find the ID strings, it looks like thjs:
Code:

Bus 002 Device 003: ID 1307:0163

So then search for Linux Webcam 1307:0163 support, Though you should use your own ID strings.

I'm sorry, I don't speak that language. I have no clue what "Linux Webcam 1307:0163" support is. Mine shows Microsoft Corp.

---

### Post by w4ett on 2007-06-14
In your terminal type the command:   lsusb    and copy and paste the results (output)  of the command.  this will show if your camera is being recognized by Ubuntu......if it is we can probably get it working.

---

### Post by hartz on 2007-06-15
> **the8thstar said:**
> I'm sorry, I don't speak that language. I have no clue what "Linux Webcam 1307:0163" support is. Mine shows Microsoft Corp.

Sometimes it is hard to establish from someone's question how much Linux knowledge they have.  In these cases you make a guess about how much information to give.

I will try again, this time much more verbose, hopefully much simpler, so here goes.

Webcam support under Linux is a regular frustration for many users.  This is because there are so many webcams which are not well supported by Linux, but it also means that the topic is much discussed and as a result much information exists on the Web about it.  It is highly unlikely that you are the first person trying to get your specific camera to work, so you need to find other posts, questions or information pages about your camera and its support on Linux.

To do this you need to find a piece of information about your specific camera.  This is not printed on the box or in the manual, but Linux can extract it from the camera.

First, some background information: When a USB device is plugged into a computer port, it gets registered and is given an address on the USB bus, and it also identifies itself to the host.  (A host in this sense is the Controller chip in the computer which understands the USB protocol.  It is responsible for negotiating addresses, connect-disconnect state maintenance, taking care of power consumption on the BUS, etc.)

The way in which USB devices identify themselves is by means of a Vendor and Device ID pair.  The vendor IDs are issued by an authority, might be the IETF but I forgot now.  The result is that every vendor has got one or more unique "USB Vendor ID" numbers.

These USB vendors however are are the people making the chips inside USB devices.  Microsoft doesn't make chips, it buys them from a chip manufacturer, like Microdia.  The vendor also assigns a device ID to every device they make, and is responsible for making sure that these are unique.

Therefore the Vendor-ID and Device-ID pair uniquely identifies the chip inside the device.  It doesn't matter whether it has got a Logitech, A4, Genius or Microsoft label painted on the casing, the device driver needs to work with the chip inside the device.

For you to find out whether the chip inside YOUR Microsoft webcam is supported, you need to find out what chip is inside it.  If you buy five boxes of the same make/model on the same day you are likely to get all devices with the same chip, but if you buy them months apart, they are less likely to be identical inside - it just depends on who is providing chips cheapest to the OEM manufacturer that specific week.

How to find out the vendor-id and device-id?

You need to open a terminal, this is found under the main Ubuntu menu under Application->Accessories->Terminal.

In the window that appears, enter the command lsusb

This will print information about the all currently connected USB devices, including the Vendor and device ID pairs for each device, one device per line.  (In case you're interested, the command is derived from ls for LIST and usb for the USB bus; thus "list the USB bus devices")

If you don't know which line identifies your camera (the description fields are often non-obvious), maybe you have many USB devices connected, simply re-run the command after disconnecting the camera, and look for a change.

The vendorID:deviceID string looks something like this: ```
1307:0163
``` - Two four-digit hexadecimal numbers.

(Note: Sometimes the numbers are written as 0x1307:0x0163.)

Once you got the string, you can search for it, both here on the Ubuntu forums, and also on the greater internet.

My suggestion was to search for the strings, together wit some other keywords, Linux and webcam and support.  This should give google a good idea of what you're looking for.

Try to find your device string, give it a whirl through Google, and post back on your findings here in this discussion, both to help others searching for the same thing and to let us know what you found.

---

### Post by willylindsay@yahoo.co.uk on 2008-01-03
Just to put this out there - I have a Microsoft WEbcam with ID string 045e:00f7 and googled for support as suggested with no luck.  If you have had any luck with this please post it.  Oh, I am on Gutsy Gibbon (obviously ?!).

Thanks

---

### Post by vivalant on 2008-01-05
willy, it seems your  webcam is supported by the SN9CXXX driver a [http://www.linux-projects.org](http://www.linux-projects.org) . Give it a try.

---

### Post by the8thstar on 2008-04-13
It is supported indeed. Thanks alot **vivalant**!

---

### Post by the8thstar on 2008-04-19
Ouch, now that I upgraded to Hardy, I've got to wait until Luca updates the driver... argh!

---

