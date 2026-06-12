---
title: "Bluetooth wireless keyboard fails to connect (Gutsy Gibbon)"
date: 2007-11-01
forum: Apple Intel Users
---

### Post by billy420 on 2007-11-01
Im trying to connect an [apple bluetooth keyboard]("http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=MB167LL/A"),  When I use the default bluetooth manager, it finds and identifies my device as an Apple Wireless Keyboard, but when I try to connect it, I get the following error: 
```

"obex://[00:1b:63:fb:fd:bb]" is not a valid location.

Please check the spelling and try again.

```

I found a thread in this subforum that reccomended installing gnome-bluetooth, which I did.  when I scan for my device  (sudo hidd --search), it too finds my device but then fails to connect with this error :
```

:~$ sudo hidd --search
Searching ...
        Connecting to device 00:1B:63:FB:FD:BB
Can't create HID control channel: Connection timed out

```
I've searched through this forum, and looked at the seemingly outdated ubuntu bluetooth guide, but I haven't gotten anywhere.
 Can I get this keyboard working with ubuntu? If so, how?

thanks.

---

### Post by nicfagn on 2007-11-06
I had to change 

```
HIDD_ENABLED=0
```

to

```
HIDD_ENABLED=1
```

in /etc/default/bluetooth and to switch the keybord off and then on when issuing:

```
sudo hidd --search
```

to put it in discovery mode.

Hope it helps.

---

### Post by jslmg on 2007-11-09
That did it! Thank you! I'd been searching for days for this.

Will this setting remain when I reboot, or will have to open terminal and do this everytime? If not, is there a way to make HIDD see the keyboard at boot?

Oh, and what the wireless mouse? Same method?

---

### Post by jslmg on 2007-11-09
I just tried the hidd --search command to see if it would see my wireless mouse. It saw it, alright, but then said "HID create error 13 (Permission denied)."

---

### Post by nicfagn on 2007-11-09
Did you use sudo before hidd --search? You have to switch off and on the mouse too.
After reboot the paired devices should be remembered.

---

### Post by jslmg on 2007-11-15
Thanks, nacfagn. This thread has done more than any other to get this bluetooth keyboard and mouse running. I'm still struggling with two issues, though, and I'm wondering if you have experience with these:

(1) Signals for both fade fast, then drop out. Could this be an intrinsic weakness of the bluetooth drivers that come with Ubuntu 7.10? Is there a remedy for it?

(2) Getting Ubuntu to search for the devices at boot. So far, this hasn't happened on my computer. What are the configs I need to check to make it so? I see in the /etc/default/bluetooth an option to make bluetooth always search for the same interfaces:

```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect aa:bb:cc:dd:ee:ff --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
``` 

And it seems that the setting I have in there would already make it search for the devices at boot:

```
# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1
```

Is this where it's done?

Happily, tonight, btw, the signals for both the mouse and keyboard are holding up better than before. I'll try a reboot later...

---

### Post by cyberdork33 on 2007-11-15
The method in the FAQ is what worked for me to connect on startup in Fiesty and it worked great. I could use the bluetooth keyboard in rEFIt, Grub, and to login:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I haven't been using my Bluetooth keyboard anymore because of the connection issues that you seem to be experiencing as well. I would be typing along and letters would be skipped over and such. I became too irritated by it and finally just switched back to USB.

---

### Post by jslmg on 2007-11-15
> **cyberdork33 said:**
> The method in the FAQ is what worked for me to connect on startup in Fiesty and it worked great. I could use the bluetooth keyboard in rEFIt, Grub, and to login:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I haven't been using my Bluetooth keyboard anymore because of the connection issues that you seem to be experiencing as well. I would be typing along and letters would be skipped over and such. I became too irritated by it and finally just switched back to USB.

I'll take a look at that FAQ later, if, after a reboot, I don't get bluetooth. 

So strange that I've been using my bluetooth keyboard and mouse solidly for over two hours now! I swear that a week ago, I couldn't stay connected.

Must be something in the ionosphere :rolleyes:

---

### Post by jslmg on 2007-11-15
There was a whole bunch of gnome updates today. I wonder if any of those might have fixed the connectivity problem...

---

### Post by cyberdork33 on 2007-11-15
> **jslmg said:**
> There was a whole bunch of gnome updates today. I wonder if any of those might have fixed the connectivity problem...
I guess I will have to try again...

---

### Post by dishkuvek on 2007-11-29
So what do you guys think? Mine is working a little better than before (I think), but I am still suffering the same type of problems.  Dropping signal up and down so fast that in a sentence of 50 words, 3-4 letters might be missing. :(

---

### Post by jslmg on 2007-11-29
I've about decided the problems with wireless in Ubuntu are due to the driver itself, and there's nothing to do except keep reporting progress or bugs, then wait. I noticed a significant improvement in wireless performance after some updates a couple of weeks ago, but it's still unstable.

Any one else noticing improvement? Would you agree with my idea that the problem is in the Bluetooth software on Ubuntu?

---

### Post by cyberdork33 on 2007-11-29
Actually, I saw the opposite. After my last post here, I got my Keyboard working great again, but after some other updates, I now have a hard time getting the keyboard to connect in the first place. I have to restart bluetooth using ```
sudo /etc/init.d/bluetooth restart
``` for the keyboard to be recognized. 

The weird thing is that is shows up in the bluetooth utility icon as connected, but typing does nothing.

I have again placed my wireless keyboard aside.

The good thing about it was that when it WAS working, I could navigate in Grub and other bootloaders with the keyboard which I had not been able to do with my USB keyboard.

---

### Post by dishkuvek on 2007-11-29
I've found that I can get along ok with using just the mightymouse, and a regular usb keyboard.  Still, that sucks as I would really like to use my apple keyboard.

Is there a bug filed about this?  I could not find one.  If not, I will file one.

---

### Post by cyberdork33 on 2007-11-29
> **dishkuvek said:**
> I've found that I can get along ok with using just the mightymouse, and a regular usb keyboard.  Still, that sucks as I would really like to use my apple keyboard.

Is there a bug filed about this?  I could not find one.  If not, I will file one.
Post back with what you find, so we can add more information.

---

### Post by dishkuvek on 2007-11-29
This is what I have found in launchpad so far:

[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

General:
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bugs](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bugs)

I am going to try compiling a few different vanilla kernels and see what happens, I'll let you guys know, till then, good luck!

---

### Post by dishkuvek on 2007-11-29
Ok so, I don't want to jinx myself here, but I made two small changes to two different bluetooth config files, and now both my apple keyboard and mouse are working PERFECTLY together.

Here is what I did...
```

$ sudo gedit /etc/bluetooth/hcid.conf

change

lm accept;

to

lm master;

```

then I did this...
```

$ sudo gedit /etc/default/bluetooth

HIDD_OPTIONS="--master --connect 00:14:51:D1:0D:5B --connect 00:0A:95:50:15:62 --server

```

Obviously, you will want to change those two addresses to the addresses of your keyboard and/or mouse, the difference was that before I had the two --connects and the --server, but I had left out --master

So after those two changes, I restarted bluetooth in init.d and now both devices work perfectly.  I've been typing with 0 lost keys for over two hours.  YAY!

---

### Post by cyberdork33 on 2007-11-30
yes it is noted in the [Bluetooth Wiki]("https://help.ubuntu.com/community/BluetoothSetup") (Linked in the FAQ) that the master line can be bad or good.

---

### Post by jslmg on 2007-12-01
dishkuvek,

Is your bluetooth loading at startup now? That has been an ongoing problem, too--BT not loading at start-up, or being unrecognized when the GDM started. In my case, sometimes it would, but usually it wouldn't.

Did you have to make any changes to the startup configs?

---

### Post by dishkuvek on 2007-12-01
> **jslmg said:**
> dishkuvek,

Is your bluetooth loading at startup now? That has been an ongoing problem, too--BT not loading at start-up, or being unrecognized when the GDM started. In my case, sometimes it would, but usually it wouldn't.

Did you have to make any changes to the startup configs?

That's a good question.  Honestly, since getting my keyboard and mouse working, I haven't even logged out.

I will try a reboot and report back.

---

### Post by jslmg on 2008-01-03
Diskuvek, I just now--four weeks later--tested your settings. They worked! BT now starts at boot-up. Reliable too.

Thanks, dishkuvek!


> **dishkuvek said:**
> Ok so, I don't want to jinx myself here, but I made two small changes to two different bluetooth config files, and now both my apple keyboard and mouse are working PERFECTLY together.

Here is what I did...
```

$ sudo gedit /etc/bluetooth/hcid.conf

change

lm accept;

to

lm master;

```

then I did this...
```

$ sudo gedit /etc/default/bluetooth

HIDD_OPTIONS="--master --connect 00:14:51:D1:0D:5B --connect 00:0A:95:50:15:62 --server

```

Obviously, you will want to change those two addresses to the addresses of your keyboard and/or mouse, the difference was that before I had the two --connects and the --server, but I had left out --master

So after those two changes, I restarted bluetooth in init.d and now both devices work perfectly.  I've been typing with 0 lost keys for over two hours.  YAY!

---

### Post by neatokino on 2008-02-14
I've tried everything, and so far no luck at all with my apple bluetooth keyboard.  My Logitech LV270 Mouse works just fine, however.   Any relief in sight for the keyboard problems???

---

### Post by george.talusan on 2008-02-17
I've followed the suggestions here and still have a non-functional wireless apple aluminum keyboard.

Any ideas?

---

### Post by george.talusan on 2008-02-19
Nix that.  Got it working with by entering typing the password on the keyboard and hitting return before the pairing process began.  The keyboard works great with the exception that the special function keys (display dim, etc) don't work.

---

### Post by nicfagn on 2008-02-21
> **george.talusan said:**
> The keyboard works great with the exception that the special function keys (display dim, etc) don't work.

The same for me, but if I switch off and then on the keyboard they work as expected.

---

