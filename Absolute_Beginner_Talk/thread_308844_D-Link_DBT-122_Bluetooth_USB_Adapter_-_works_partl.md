---
title: "D-Link DBT-122 Bluetooth USB Adapter - works partly with my Ubuntu?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-28
Hello all!

Today I am trying another Bluetooth Device.

The _Model_ is: **D-Link DBT-122 Bluetooth USB Adapter**

I am trying to make it work in my Ubuntu v6.10.

I followed the instructions on the following link:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

And got the following results:

**1.** I verified that the package "**bluez-utils**" is installed on my Ubuntu.

**2.** I restarted the Bluetooth services by doing:


> root@dimitris-desktop:/# **sudo /etc/init.d/bluetooth restart**
* Restarting Bluetooth services [ ok ]


**3.** Verified whether my bluetooth device has been detected & the appropriate modules loaded by viewing the "**lsusb**" output (in case of usb device) output:

> root@dimitris-desktop:/# lsusb
Bus 005 Device 005: ID 0a48:3240 I/O Interconnect 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 2001:f111 D-Link Corp. [hex] 
Bus 002 Device 003: ID 0df7:0620 Mobile Action Technology, Inc. MA-620 Infrared Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

Things seem to be better this time, I identified the Bluetooth Device - it's:

> Bus 002 Device 004: ID 2001:f111 D-Link Corp. [hex]


**4.** I viewed the output of the command "**hcitool dev**" which gave me a listing of bluetooth devices on my computer:

> root@dimitris-desktop:/# hcitool dev
Devices:
        hci0    00:15:E9:F5:6C:0A

_Note_:
Since I am not getting "all zeros", I do NOT need to restart the "bluez-utils" service & try again.

**5.** Now I need to connect to my Bluetooth device & I need to find the address of my device.

> Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual)...

_Note_:
Unfortunately there is no Keyboard button labeled "Connect", NOR is there a such a button on my Mouse...

...And then I performed a search for the device, with this command:

> root@dimitris-desktop:/# **sudo hidd --search**
Searching ...
root@dimitris-desktop:/#

_Note_:
This D-Link's Bluetooth has 2 LEDs:

a. A Green Power LED (labeled: PWR), which is ON at all times.

b. A Green Link LED (labeled: LNK), which is ON at all times.

While the process was under "Searching...", I noticed that NO Lights were blinking!

_Note_:
A diff result, from the one I experienced with the Trust's BT-2210Tp Bluetooth USB Adapter, whose blue light started blinking for about 20 times!
And then it got back to previous state (stopped blinking & turned ON again) & I got NO output!

Is there some other output, I should have got here?

OR

Hopefully the Green LEDs would be blinking too?

**6.** Then, I tried to temporarily connect to my device, and used the following command:

> root@dimitris-desktop:/# **sudo hidd --connect 00:15:E9:F5:6C:0A**
Can't get device information: No route to host
root@dimitris-desktop:/#

_Note_:
The "00:0B:0D:4C:3A:16", is the address of the device, I am trying to connect to (An address I got from the output of Step4 above).

In this step, my Bluetooth device should have connected for the current session...

If I had got a "Can't create HID control channel: Connection refused" error message, most likely the discovery period for the device would have timed out.
And I would have made the device discoverable & enter the above command again, but more quickly!

But I am getting a different message:

> **Can't get device information: No route to host**

_Note_:
The above message is the SAME message I experienced when trying to connect the Trust's BT-2210Tp Bluetooth USB Adapter.

Also, according to feedback from this thread:

[http://ubuntuforums.org/showthread.php?t=304992](http://ubuntuforums.org/showthread.php?t=304992)

... Ubuntu user "Zalbor" experienced the SAME thing!!!

> **Zalbor]Following that guide, I have the same problem with "hidd --search".
Nothing is found (I'm looking for my mobile, which is easily found by other mobiles and in windows).
As for the next, the reason it doesn't work is that you should try to connect to the device, whose number you're supposed to get by searching...[/quote]


What is wrong with the Ubuntu instructions posted here:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I think these instructions need a fix/correction at this point, because it seems that with 3 Bluetooth adaptors tested, WE get NO results!!!

What are we doing wrong?

**7.** I then followed user's "Zalbor" idea, which he was very kind to provide on the above thread...

So, I Edited the "**/etc/bluetooth/hcid.conf**" file, so that it says:

a. **security auto said:**
> If you send a file from the Mobile Phone device, it will be automatically saved on the Desktop.

So, from my Mobile Phone, I perform the following:

a. I select a nice picture.

b. I select "send", to send the picture.

c. I select "Via Bluetooth", to send the picture to my Ubuntu.

d. Under "Detected Bluetooth Devices", I select "dimitris-desktop-0" (My Ubuntu).

And I get the _same_ result:

> **Bluetooth Connection Failed**

Any ideas?

What am I doing wrong?

Things are much better compared with the other Bluetooth USB Adapter's connection's results!!!
At least now, my Mobile phone can SEE my Ubuntu!

What is wrong?

**9.** Now I will try to send a file _from_ **Ubuntu PC** _to_ my **Nokia Mobile Phone**.
I decided to follow what user "Zalbor" suggested:

[quote=Zalbor]Now, sending a file to the other device is harder.
Find the file on your drive, right-click & select "send to".
The other device won't be in the list at first, but if you try to use it to connect to your PC a few times (even if it fails) it will appear, so you can send a file from the PC...[/quote]

So, I performed the following steps:

a. I selected a picture on my Desktop.

b. I right-clicked on it & select "Send to...".

c. From the window that opens, under "Send as:", I select "Bluetooth"

d. From the "Send to:" section, NO Device seemed to be listed...

_UNTIL_:

d1. Suddenly, my Nokia Phone is found & listed - Yupiii!!!

d2. So, I select it from the list!

e. I then, click on the button named "Send".

f. On my Mobile Phone's side, I get the message: "Receive Data from: dimitris-desktop-0"?

g. I select "Accept".

h. On the Ubuntu side, a screen comes up on the screen saying "Sending File" with a progress bar on it.

i. Yes!!! Yes!!! The file has been received on my Nokia Mobile Phone!!!

_Note_:
To set above step #s f&g on your Nokia Mobile Phone, to auto-connect to Ubuntu's Bluetooth Device, there is a setting in your Nokia's Mobile Phone Menu, saying "Auto-Connection without Confirmation?"...
...if you change it to "YES", the step #s f&g above will NOT be required!

_Conclusion_:
I CAN send files _from_ my **Ubuntu PC** _to_ my **Nokia Mobile Phone**, but I can NOT do the opposite:

> I can NOT send files _from_ my **Nokia Mobile Phone** _to_ my **Ubuntu PC**!

I get the following error:

**Bluetooth Connection Failed**

What do I do?

Any Ideas?

Thanks.

---

### Post by dvarsam on 2006-11-30
I finally managed to achieve a connection in both directions!

So, I am very happy about it!!!

Thanks.

---

### Post by timmahhny on 2006-12-01
I also had a problem with connecting my Motorola Razor to my PC using the D-Link DBT-122. I followed every post with no results, but yours helped me out. I can now transfer files from my Ubuntu to my cell phone, and from my cell phone to my box.
 Thanks for the great information
Timmahhny

---

### Post by dvarsam on 2006-12-01
Dear "timmahhny",

Thanks for your reply!

> **timmahhny said:**
> 
I also had a problem with connecting my Motorola Razor to my PC using the D-Link DBT-122. I followed every post with no results, but yours helped me out. I can now transfer files from my Ubuntu to my cell phone, and from my cell phone to my box.
 Thanks for the great information
Timmahhny

I am very happy that things worked for you too!

**Message to users trying to Set up their Bluetooth:**

The instructions on the following link are NOT very helpful:

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

In fact, they are confusing & some parts of it do NOT work!!!

Please follow this post's directions:

[https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter](https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter)

The above instructions were created _after_ I had my Ubuntu v6.10 _cleanly_ installed!

So, there shouldn't be any differences between my Ubuntu and yours...
(e.g. in packages that **I** have installed, but **you** are missing...)

**Also**:

> It would be nice when you are adding Hardware on the wiki.ubuntu.com, to **mention** the date you purchased the specific Hardware & a picture of the product you are talking about...

This would help users, **know** whether they could search & find that product on their nearest computer store/shop.

Thanks.

---

### Post by malmjako on 2008-03-16
> **dvarsam said:**
> I finally managed to achieve a connection in both directions!

So, I am very happy about it!!!

Thanks.

Exactly what did you do to get the sending from phone working? I have a Samsung SGH-z240, and I can send stuff TO the phone, but not FROM the phone. (On Ubuntu 7.10, Gutsy Gibbon)

---

