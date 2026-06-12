---
title: "[SOLVED] Can't connect Apple Wireless Keyboard on Ubuntu 8.10"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by 74141 on 2008-10-30
Ok, I am doing a little testing right now with the new Ubuntu 8.10 on my Macbook 3.1, the external monitor can now configure it perfectly, the sound works out of the box, and the same thing with my wireless mighty mouse.

But I can't connect my Apple wireless keyboard! :(

I try using the bluetooth configuration by "Setup new device" and it find my keyboard, but if I try to connect it with my machine it give me this message: Pairing with Apple Wireless Keyboard failed!

I was using hidd with ubuntu hardy to connect my keyboard, but it seems the developer remove it from this version of ubuntu, so I try with hcitool without any success :confused:

Any advice??

Before I forget, I try this tutorials before without any good results :(
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)
[http://ubuntuforums.org/showthread.php?p=4486290](http://ubuntuforums.org/showthread.php?p=4486290)

Thanks..

---

### Post by cyberdork33 on 2008-10-30
> **74141 said:**
> Ok, I am doing a little testing right now with the new Ubuntu 8.10 on my Macbook 3.1, the external monitor can now configure it perfectly, the sound works out of the box, and the same thing with my wireless mighty mouse.

But I can't connect my Apple wireless keyboard! :(

I try using the bluetooth configuration by "Setup new device" and it find my keyboard, but if I try to connect it with my machine it give me this message: Pairing with Apple Wireless Keyboard failed!

I was using hidd with ubuntu hardy to connect my keyboard, but it seems the developer remove it from this version of ubuntu, so I try with hcitool without any success :confused:

Any advice??

Before I forget, I try this tutorials before without any good results :(
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)
[http://ubuntuforums.org/showthread.php?p=4486290](http://ubuntuforums.org/showthread.php?p=4486290)

Thanks..
Known bug. hidd is in bluez-compat package now
[https://bugs.launchpad.net/bugs/281580](https://bugs.launchpad.net/bugs/281580)

---

### Post by jdong on 2008-10-30
I spent about a week investigating this:

Bottom line was, Ubuntu **CAN** connect to these keyboards without hidd (which is recommended as the BlueZ input service is to replace hidd altogether), **but** you need to first tell OS X to forget the association. It seems like OS X sets up some sort of pairing at the pre-boot (NVRAM? PRAM? BT controller?) level that will cause Bluetooth Wizard to fail.

If you go to OS X's bluetooth pref pane and remove the keyboard, reboot into Ubuntu, put the keyboard into Pairing mode and use the BT wizard, you'll get the "enter pin xxxx" instead of "pairing failed" message. Note that it may take one or two tries to get this working.


I don't know how to go about this if you don't have OS X at all. I suspect a PRAM reset will get the same effect but that's unconfirmed.

---

### Post by cyberdork33 on 2008-10-30
> **jdong said:**
> If you go to OS X's bluetooth pref pane and remove the keyboard, reboot into Ubuntu, put the keyboard into Pairing mode and use the BT wizard, you'll get the "enter pin xxxx" instead of "pairing failed" message. Note that it may take one or two tries to get this working.
Nope. I stopped using my wireless keyboard in OSX before I even filed the bug report to get hidd back. hidd is not working correctly now either for me.

Are you using the white keyboard or the Aluminum one?

---

### Post by jdong on 2008-10-30
This is the aluminum one. It will not pair once OS X has paired with the keyboard at least once, until you tell OS X to remove the pairing (removing OS X or disconnecting the keyboard via the BT applet doesn't do this)

There's some sort of nonvolatile memory effect going on. Once I pair it iwht Ubuntu, if I boot into OS X and pair it there, then boot back into Ubuntu, I can still use an existing pairing, but if I remove and re-try to pair it fails.

---

### Post by cyberdork33 on 2008-10-30
I am using a white, older style. I can double-check, but I removed it awhile ago from OSX. It was working just fine in both without issue for long time with hide. (The blues applet has never, ever worked.)

---

### Post by trouble1313 on 2008-10-30
I was able to get one of the white ones to pair from the command line(pairing failed through the applet) but it doesn't live through a reboot. A generic BT mouse paired through the applet and came back. It's tough to enter your login credentials with no keyboard! I'd love to know the trick to getting this to work.
-Trouble

---

### Post by cyberdork33 on 2008-10-30
how did you do it from the commandline? What commands?

---

### Post by 74141 on 2008-10-31
> **jdong said:**
> I spent about a week investigating this:

Bottom line was, Ubuntu **CAN** connect to these keyboards without hidd (which is recommended as the BlueZ input service is to replace hidd altogether), **but** you need to first tell OS X to forget the association. It seems like OS X sets up some sort of pairing at the pre-boot (NVRAM? PRAM? BT controller?) level that will cause Bluetooth Wizard to fail.

If you go to OS X's bluetooth pref pane and remove the keyboard, reboot into Ubuntu, put the keyboard into Pairing mode and use the BT wizard, you'll get the "enter pin xxxx" instead of "pairing failed" message. Note that it may take one or two tries to get this working.


I don't know how to go about this if you don't have OS X at all. I suspect a PRAM reset will get the same effect but that's unconfirmed.

Thanks for your advice, it works with me right now, but the FN keys doesn't working :( And I need to patching "hidp" to make it works.

By the way, I am using two language layout on my system, English and my mother language, and I make a short cut for Layout switching, and every time I wake up my machine, or reboot it I lost this configuration and I must do it again!! :confused:

Is this a BUG in gnome-keyboard-properties? and there is any one know how to fix it?

Big thanks to all of you :)

---

### Post by jdong on 2008-10-31
> **74141 said:**
> Thanks for your advice, it works with me right now, but the FN keys doesn't working :( And I need to patching "hidp" to make it works.


This workaround is a little bit disgusting, but there's some sort of kernel-level bug that prevents the input service from correctly detecting the model of the keyboard. To work around, edit your /var/lib/bluetooth/(mac address)/did file.

It should have a line like:
```

00:1E:52:XX:XX:XX FFFF 0000 0000 0000

```


Change it to read
```

00:1E:52:XX:XX:XX FFFF 05AC 022C 0000

```

0x05ac:0x022c is the device ID for the US aluminum Apple keyboard.

Then, reboot to apply these changes. Note that if you have a mighty mouse, you don't need to set its device ID (in fact doing so may cause the horizontal wheel to work incorrectly)

---

### Post by deltaiscain on 2008-10-31
> **jdong said:**
> This workaround is a little bit disgusting, but there's some sort of kernel-level bug that prevents the input service from correctly detecting the model of the keyboard. To work around, edit your /var/lib/bluetooth/(mac address)/did file.

It should have a line like:
```

00:1E:52:XX:XX:XX FFFF 0000 0000 0000

```


Change it to read
```

00:1E:52:XX:XX:XX FFFF 05AC 022C 0000

```

0x05ac:0x022c is the device ID for the US aluminum Apple keyboard.

Then, reboot to apply these changes. Note that if you have a mighty mouse, you don't need to set its device ID (in fact doing so may cause the horizontal wheel to work incorrectly)

Noob here, when i try to save the file, i get an error that my permissions are incorrect. How do you change them?

Thanks a million!

---

### Post by jdong on 2008-10-31
You need to use a administrator privilege editor, such as "gksu gedit"

---

### Post by 74141 on 2008-10-31
A new problem with Apple Keyboard and FN keys!
```
$ hidd
00:1E:52:xx:xx:xx apple keyboard [**0000:0000**] connected 
00:1F:5B:xx:xx:xx apple mouse [**0000:0000**] connected 

```

I think there seems to be some problem with bluez, it doesn't fetching the id.
So I can't make it know the fn map key because of that :confused:

---

### Post by jdong on 2008-10-31
> **74141 said:**
> A new problem with Apple Keyboard and FN keys!
```
$ hidd
00:1E:52:xx:xx:xx apple keyboard [**0000:0000**] connected 
00:1F:5B:xx:xx:xx apple mouse [**0000:0000**] connected 

```

I think there seems to be some problem with bluez, it doesn't fetching the id.
So I can't make it know the fn map key because of that :confused:

This is what my workaround in post #10 addresses. After that, the product ID will be correct and fn key will be mapped. I don't know why the ID isn't picked up correctly, but I will research into it.

---

### Post by 74141 on 2008-11-01
> **jdong said:**
> This is what my workaround in post #10 addresses. After that, the product ID will be correct and fn key will be mapped. I don't know why the ID isn't picked up correctly, but I will research into it.

> **jdong said:**
> This workaround is a little bit disgusting, but there's some sort of kernel-level bug that prevents the input service from correctly detecting the model of the keyboard. To work around, edit your /var/lib/bluetooth/(mac address)/did file.

It should have a line like:
```

00:1E:52:XX:XX:XX FFFF 0000 0000 0000

```


Change it to read
```

00:1E:52:XX:XX:XX FFFF 05AC 022C 0000

```

0x05ac:0x022c is the device ID for the US aluminum Apple keyboard.

Then, reboot to apply these changes. Note that if you have a mighty mouse, you don't need to set its device ID (in fact doing so may cause the horizontal wheel to work incorrectly)

Sorry I wasn't read your post before..

Actually the ID of my keyboard is 0x05ac:0x022d, so I was need to do a little patching for hid.ko module to make it works perfectly on Hardy or openSUSE.. etc, and right now I test your advice with this ID, but it doesn't work with me.

So I decide to test it with the ID for the US aluminum Apple keyboard (0x05ac:0x022c) and it works very nice, this trick is so easy without doing any patching for hid.ko and losing time :)

Do you thing if there any fix for this bug in the future I will lost this ID with a default ID of my keyboard?



Thank you so much for this helpful post :)

---

### Post by jdong on 2008-11-01
Well, I am prepping a patch to (1) remove the horizontal mousewhele quirk ((2) add the ISO and JIS variants of the Apple keyboard (22D and 22E respectively)


I still don't know why BlueZ doesn't get the ID of the keyboard correctly.

---

### Post by popformula on 2008-11-03
My keyboard won't connect and I guess it's the same reason - it's physically paired somehow. This is evidenced by the fact I can use it with the bootloader before OS X even starts.

I've now got no access to my OS X partition (it's corrupt) any ideas how to unpair my keyboard from within Ubuntu or some other way..?

---

### Post by jdong on 2008-11-03
Wild guess, but perhaps try resetting the PRAM/NVRAM? super-P-R on bootup with a wired keyboard (NOTE: volumes will all reset too)

Otherwise, boot up onto an OS X installer CD, pair your keyboard then unpair it.

---

### Post by kmand on 2008-11-03
I just upgraded from 8.04 to 8.10 on a Mac Mini, and went from working bluetooth keyboard and mouse, to non working ones.

I took the suggestion in the thread and booted OS X and deleted both. I then boot Ubuntu 8.10 and try to add them with bluetooth device setup.
Both are seen by setup and identified with the same names they had before (and in OS X).

When I try to add the mouse, it says pairing succeeded but the mouse keeps blinking and does't move the cursor.

When I try and add the keyboard, I just get pairing failed. I don't get an  enter pin prompt. The apple keyboard I have is about a year old is white and has a clear plastic bottom.

Any ideas?

---

### Post by cyberdork33 on 2008-11-04
> **jdong said:**
> Wild guess, but perhaps try resetting the PRAM/NVRAM? super-P-R on bootup with a wired keyboard (NOTE: volumes will all reset too)

Otherwise, boot up onto an OS X installer CD, pair your keyboard then unpair it.
I still have no luck with my older white keyboard either.

---

### Post by jdong on 2008-11-04
Hmm,  maybe my procedure works with the new aluminum ones only :(

---

### Post by cyberdork33 on 2008-11-04
> **jdong said:**
> Hmm,  maybe my procedure works with the new aluminum ones only :(
Unfortunately, the old way I used to get it to work (with hidd) doesn't work anymore either.

---

### Post by calebio on 2008-11-06
> **cyberdork33 said:**
> Unfortunately, the old way I used to get it to work (with hidd) doesn't work anymore either.

I have been able to connect my white Apple wireless keyboard and mighty mouse (on my white iMac) using '**sudo hidd --connect aa:bb:cc:dd:ee:ff**' where the MAC address corresponds to '**hcitool scan**' (when either device is in discoverable mode).

Steps to make this work:
[LIST=1]
[*]install **bluez-compat** to enable **hidd** tool
[*]run **hcitool scan** with your keyboard/mouse in discoverable mode to get their MAC addresses
[*]edit **/etc/default/bluetooth** to include the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS=" --server --connect 00:aa:bb:cc:dd:ee --connect aa:bb:cc:dd:ee:ff"

```
where the first is your keyboard, the second your mouse MAC address
[/LIST]

Hope this helps. Please let me know if clarification is needed. One note: trackball scrolling on the mouse does not work with this setup.

---

### Post by cyberdork33 on 2008-11-07
> **calebio said:**
> I have been able to connect my white Apple wireless keyboard and mighty mouse (on my white iMac) using '**sudo hidd --connect aa:bb:cc:dd:ee:ff**' where the MAC address corresponds to '**hcitool scan**' (when either device is in discoverable mode).

Steps to make this work:
[LIST=1]
[*]install **bluez-compat** to enable **hidd** tool
[*]run **hcitool scan** with your keyboard/mouse in discoverable mode to get their MAC addresses
[*]edit **/etc/default/bluetooth** to include the lines ```
HIDD_ENABLED=1
HIDD_OPTIONS=" --server --connect 00:aa:bb:cc:dd:ee --connect aa:bb:cc:dd:ee:ff"

```where the first is your keyboard, the second your mouse MAC address
[/LIST]

Hope this helps. Please let me know if clarification is needed. One note: trackball scrolling on the mouse does not work with this setup.
Can you post your entire/etc/default/bluetooth file? There are some other options in there that can be key to making this work or not.

I can try this again, but ever since the bluetooth updates that were done at the last minute when I was testing Intrepid, nothing seems to work correctly anymore.

Also, for the mighty mouse "advanced" funtions, you have to switch the Blueeooth hardware into HCI mode. You can do this with the command :
```
sudo hciconfig hci0 reset
```

If everything works OK with that, you can add
```
options hci reset=1
```
to your /etc/modprobe.d/local file

---

### Post by calebio on 2008-11-07
> **cyberdork33 said:**
> Can you post your entire/etc/default/bluetooth file? There are some other options in there that can be key to making this work or not.

My entire **/etc/defaults/bluetooth** reads
```
# Defaults for bluez
# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HIDD_ENABLED=1
HID2HCI_ENABLED=0
#HID2HCI_UNDO=1
HIDD_OPTIONS=" --server --connect 00:14:51:c0:14:58 --connect 00:0A:95:49:B0:B2"
```

> Also, for the mighty mouse "advanced" funtions, you have to switch the Blueeooth hardware into HCI mode. You can do this with the command :
```
sudo hciconfig hci0 reset
```

This does nothing for me, perhaps because of my **HID2HCI_ENABLED=0** line?

---

### Post by cyberdork33 on 2008-11-07
> **calebio said:**
> This does nothing for me, perhaps because of my **HID2HCI_ENABLED=0** line?
no. That option determines if the system tries to use the hid2hci utility to change from hid mode to hci mode, but this has not worked in previous releases (that is what the command I posted does).

I think you have to connect the mouse after you have reset, and you have to do some additional setup to get all the functions working (scrolling, etc)

See this article that explains a bit better than me.
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

EDIT: Still no luck. Applet simply says "failed" and using hidd returns "Can't get device information: Function not implemented"

---

### Post by calebio on 2008-11-08
> **cyberdork33 said:**
> I think you have to connect the mouse after you have reset, and you have to do some additional setup to get all the functions working (scrolling, etc)

See this article that explains a bit better than me.
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

Yeah, no. I have no luck with the advanced setup (the 'red pill' in that blog post). The instructions in the link don't work for me.

---

### Post by cyberdork33 on 2008-11-08
> **calebio said:**
> Yeah, no. I have no luck with the advanced setup (the 'red pill' in that blog post). The instructions in the link don't work for me.
me either since the upgrade, but I was really referring to the underlying problem with HID vs HCI. You have to get the hardware into HCI mode for the advanced functions to work.

---

### Post by kmand on 2008-11-08
I've also tried all the suggestions with no luck.

Worked fine under heron and no go with intrepid. I have a Mac Mini with original white keyboard and mouse (not super).

Looking for debug suggestions.

---

### Post by calebio on 2008-11-08
> **kmand said:**
> Worked fine under heron and no go with intrepid. I have a Mac Mini with original white keyboard and mouse (not super).

Not super!? Mine is 'mighty'. :P

Higher OS versions generally add and expand functionality, not destroy it. Why does this happen in Ubuntu? The change/transition management process needs some work.... This sort of issue has been a deal-breaker with Ubuntu for me in the past. Audio not working (even in Ubuntu Studio) is really the main one. Oh well.

---

### Post by cyberdork33 on 2008-11-08
> **calebio said:**
> Higher OS versions generally add and expand functionality, not destroy it. Why does this happen in Ubuntu? The change/transition management process needs some work.... This sort of issue has been a deal-breaker with Ubuntu for me in the past. Audio not working (even in Ubuntu Studio) is really the main one. Oh well.
I have mentioned this everytime they change the Bluetooth stack. They did a big change right before final release this time, and they did the same for Hardy.

---

### Post by jdong on 2008-11-08
From what I understand, the old stack played so poorly with the new kernel-level bluetooth drivers that there was no choice but to make this migration. It wasn't an easy decision -- all of KDE was left in the dust too.

---

