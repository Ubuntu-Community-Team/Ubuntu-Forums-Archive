---
title: "Macbook + sysrq key"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by bluefish86 on 2008-04-22
Obviously, my macbook keyboard has no sysrq key.  Is there an equivalent key combination I can press instead?  If not, is there any way I can remap sys rq to some other key combination that goes unused, like Fn+eject?

---

### Post by flaggh on 2008-05-09
bump

---

### Post by neunon on 2008-05-15
bump. need an answer.

---

### Post by flaggh on 2008-08-27
bumpity bump bump

---

### Post by user12021 on 2008-12-03
I hate to do this, but
bump.

Since the sysrq key commands are part of the kernel, would that mean one would have to change the source code to use them on a computer without a sysrq key?

---

### Post by andrei_m on 2009-02-20
It seems that SysRq is broken in gnome on Intrepid.
Works only in console. SO, the prescription below will only
help  if you are able to go to console (Ctrl-Alt-Fn)
after gnome freezes. It is not always possible.

The solution requires installing the keyfuzz program.


The keycodes are in 
/usr/include/linux/input.h

The input devices are in /proc/bus/input/devices
for example:
I: Bus=0003 Vendor=05ac Product=0204 Version=0110
N: Name="Mitsumi Electric Apple Extended USB Keyboard"
P: Phys=usb-0000:00:1d.7-5.3.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb5/5-5/5-5.3/5-5.3.1/5-5.3.1:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
etc.


decimal for 0x00070068    is 458856
 
See the word "event3" in line H? This is system dependent.
Use in argument of keyfuzz:

sudo su
echo "458856 99" | keyfuzz -s -d/dev/input/event3

This maps F13 to PrintScreen, and Alt-F13 will REISUB
Here 458856 stands for F13, and 99 stands for Print/SysRq

But on Intrepid gnome this only works in console. 
Somehow gnome intercepts SysRq. This is a separate problem.

---

### Post by flaggh on 2009-02-21
Unfortunatley Macbooks lack a SysRq key as well as an F13 key.  Thanks for the post though.

---

### Post by cyberdork33 on 2009-02-21
> **flaggh said:**
> Unfortunatley Macbooks lack a SysRq key as well as an F13 key.  Thanks for the post though.
I have an F13, F14, F15, F16, F17, F18, F19 key on my Mac. I think that the process could be applied to another key though since the macbooks do not have such a large keyboard.

---

### Post by flaggh on 2009-02-21
I see, so he's remapping the SysRq to F13.  So using this method, we should be able to map the key to any key we like?

---

### Post by cyberdork33 on 2009-02-22
> **flaggh said:**
> I see, so he's remapping the SysRq to F13.  So using this method, we should be able to map the key to any key we like?
yep, you just have to replace the 458856 code with the keycode for the key you want. This is just a guess as I have never used this, but from the format of the command, and the other information given, that is all you have to do.

---

### Post by flaggh on 2009-02-22
I thought that the SysRq implementation was embedded into the kernel at such a low level that remapping wouldn't work.

---

### Post by cyberdork33 on 2009-02-23
> **flaggh said:**
> I thought that the SysRq implementation was embedded into the kernel at such a low level that remapping wouldn't work.
the keyfuzz app seems to change the keycode at the dev interface level rather than in xorg, thus the system would see SysRq as the actual key that was pressed.

Again, I have not tried this, and this is all based on one user's post above. I suggest that you try the implementation stated and see if it actually works.

---

### Post by flaggh on 2009-02-25
> **andrei_m said:**
> 
decimal for 0x00070068    is 458856


I'm a little confused, where did you get 0x00070068?

If I look in /usr/include/linux/input.h all the values don't look anything close to that.

Also, any idea why I have two entries for my keyboard here:

```
$ cat /proc/bus/input/devices

<snip>

I: Bus=0003 Vendor=05ac Product=021a Version=0111
N: Name="Apple Computer Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=e10000 0 0 0 7b00000000 10c4000000 e0aeffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05ac Product=021a Version=0111
N: Name="Apple Computer Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1d.0-2/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.2/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=13
B: KEY=200000000 0 0
B: MSC=10

<snip>

```
Do I use event7 or event8?

Thanks!

---

### Post by cyberdork33 on 2009-02-25
i think that one is the trackpad, the other is the keyboard. not sure how to tell the difference. You could do an lsusb maybe and figure out the correct device IDs.

This may also help:
[http://0pointer.de/lennart/projects/keyfuzz/#documentation](http://0pointer.de/lennart/projects/keyfuzz/#documentation)

---

### Post by flaggh on 2009-03-01
So I've been playing around with this for a while and haven't gotten it to work yet.  Here's what I've tried, maybe someone can tell me where I've gone wrong.

I'm trying to remap alt-F12 as SysRq.  According to showkey and input.h, the decimal value for F12 is 88.  0d88 = 0x58 and for some reason you need to add 0x070000 to this because it is a USB keyboard which gives you 0x070058 = 0d458840.

I have noticed that after every reboot, the event id changes.  Sometimes the keyboard might be event1 and sometimes it can be something completely different.  For this reason I've chosed to use ```
/dev/input/by-id/usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-kbd
``` to guarantee that I'm using the correct input device.

the last bit of info needed is the SysRq keycode which is 99.

```
 echo "458840 99" | sudo keyfuzz -s -d /dev/input/by-id/usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-kbd
```

This doesn't seem to work for me.  I believe I should be able to recall the assignment using the following command but nothing appears to have changed:
```
sudo keyfuzz --get -d /dev/input/by-id/usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-kbd 
### evdev 1.0.0., driver 'Apple Computer Apple Internal Keyboard / Trackpad'
0x000	0x01d
### EOF

```

Any ideas?

---

### Post by pjjjv on 2012-09-02
Best way to go currently is to install (manually compile) the keyfuzz program and put

echo "786616 99" | keyfuzz -s -d /dev/input/by-id/usb-Apple_Inc._Apple_Internal_Keyboard___Trackpad-event-kbd

in your /etc/profile for instance. This maps Alt-Eject on a typical Apple Macbook Pro (mine is mid-2010, 6,2), to the Alt-SysRq combination.

Hardest was discovering 786616, which is 0xc00b8. For the "consumer" part of the USB HID codes one apparently does not add 0x70000 but 0xc0000. I found the code via the little program getscancodes (again, compile yourself).

For F12 it would have been 458821.

Goodluck!

---

