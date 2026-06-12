---
title: "Cannot connect to Bluetooth devices"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-02-21
I can turn my bluetooth adapter on and off but I cannot connect to any devices when ever I try to connect to a device I get the following message:
obex://[00:16:cb:1c:cc:10] is not a valid location, please check the spelling and try again.



Any help?

---

### Post by linuxwizard on 2008-02-21
Look at bottom of this page for > Troubleshooting > should help you.

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by neurostu on 2008-02-21
I ran the following code like the troubleshooting said:

```
 sudo apt-get install gnome-vfs-obexftp
```

Now I get the following error:

Couldn't display "obex://[00:02:76:00:4f:dc]". Check if the service is available.

---

### Post by dcstar on 2008-02-21
> **neurostu said:**
> I ran the following code like the troubleshooting said:

```
 sudo apt-get install gnome-vfs-obexftp
```

Now I get the following error:

Couldn't display "obex://[00:02:76:00:4f:dc]". Check if the service is available.

I have the exact same issue with connecting to my LG mobile phone (which connects fine using a Windows VM under Linux and the BlueSoleil software), and I believe it is because the phone doesn't support the basic OBEX protocol and needs some specialist software which doesn't seem to be available in Linux (at least, I haven't been able to find it).

The basic Bluetooth connection works in Ubuntu, just accessing the device in a useful manner don't!

If someone comes up with a fix, then I will be interested to see it.

---

### Post by neurostu on 2008-02-21
I'm not sure how much more difficult it is to connect a cell phone over bluetooth but i am just trying to connect a bluetooth mouse

---

### Post by dcstar on 2008-02-21
> **neurostu said:**
> I'm not sure how much more difficult it is to connect a cell phone over bluetooth but i am just trying to connect a bluetooth mouse

Then that is why you are getting that error - AFAIK the OBEX protocol is for File Transfers.

The mouse should be recognised as an "Input" device (I believe), you may have to check your Bluetooth preferences to make sure you have all the services enabled.

---

### Post by steveneddy on 2008-02-21
[Here]("http://ubuntuforums.org/showthread.php?t=586105") is my How To on bluetooth.

Bluetooth isn't hard, you just have to set it up correctly.

---

### Post by neurostu on 2008-02-22
So I already had all the services enabled and I ran 
```
 sudo apt-get upgrade bluez-utils 
```
as I already had them installed.

Whenever i try to connect it still says that the service is unavailable...

---

### Post by neurostu on 2008-02-23
*bump

---

### Post by jroq on 2008-02-24
I'm having the exact same problem. I've installed all the bluetooth utilities/applications available through add/remove. It gives the me error:

"obex://[00:17:fa:87:0e:44]" is not a valid location.

Any ideas?

I'm windows literate and i've had ubuntu for a bit since my IT friend introduced me to it, but i'm new to the advanced workings of the OS (ubuntu).

---

