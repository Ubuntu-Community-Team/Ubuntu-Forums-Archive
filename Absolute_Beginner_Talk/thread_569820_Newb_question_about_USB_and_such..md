---
title: "Newb question about USB and such."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by buba447 on 2007-10-07
Hello all,
I am a week-old linux user, so i apologize if this doesnt make much sense.
I am using Ubuntu-Server
I am trying to setup a tcpip connection between my palm pilot and my server, using usb.
I have gotten the connection to work. My problem is that i want to automate this, so i can just connect my palm pilot and hit connect.
Right now i have to mount all of my usb drivers, plug my palm pilot in, wait for the usb to become active, then start the ppp daemon. If i try starting the ppp daemon before plugging the palm pilot i get and error saying that ttyUSB1 does not exist.
I haven't made any alterations to the basic ubuntu setup, nor have i made any kernel changes. (i wouldnt even know how)
Ive read some things about compiling kernels or adding kernel modules, neither of which i know anything about...
Seems to me that i need to find some way to get ttyUSB1 to be always on, in order for my ppp daemon to actively search for a connection. But i dunno how :-(

Thanks in advance.

---

### Post by jpkotta on 2007-10-07
Is this just on boot-up?  In that case, all you have to do is add your USB drivers to /etc/modules.

```
sudo -i
echo name_of_the_first_usb_module >> /etc/modules
echo name_of_the_second_usb_module >> /etc/modules
echo name_of_the_Nth_usb_module >> /etc/modules
exit
```

Then start pppd at boot.  If it is sane, it came with an init script to do this properly.  This will be located in /etc/init.d.  In that case, you can just use something like BUM, sysvconfig, sysv-rc-conf, ksysv, etc.  Or you can add whatever command you use to start pppd to /etc/rc.local.

---

### Post by buba447 on 2007-10-07
Hello again.
What exactly are the usb modules?
I still cant seem to get the /deb/ttyUSB1 to exist without my palm being plugged in.

---

### Post by buba447 on 2007-10-07
Nix that, i've got the usb module to load properly...
Now i just gotta figure out how to get the ppp daemon to constantly look for a connection....
Anyone have any ideas?
Sorry for being so vague...

---

### Post by buba447 on 2007-10-07
Ok, i cant seem to get the /dev/ttyUSB1 to stay...
As soon as i disconnect my palm i get this error message
'Failed to open /dev/ttyUSB1: No such device'

Then if i turn my palm back on, i cannot reconnect...
What am i doing wrong?

---

### Post by jpkotta on 2007-10-07
I see what you're getting at now.  The modules are already loaded.  There is a thing called udev that watches for new devices (usually USB) and automatically creates a device node in /dev/ for them.  Otherwise you would need to create the node by hand.  This is a possible solution.  When /dev/ttyUSB1 gets created, run this command on it:
```
ls -l /dev/ttyUSB1
```
and make a note of the very first character (probably a "c") and the two comma-separated numbers between the group (probably "root") and the date.  Then unplug the palm and manually create the device node.
```
sudo mknod /dev/ttyUSB1 <type> <major> <minor>
```
where <type> is the very first character from above, <major> is the first number, and <minor> is the second number.  Hopefully this node will persist and stay associated with the palm and all will be right with the world.

If udev gets too clever and deletes the node, or the kernel assigns the device to another node, you'll have to modify udev's configuration.  I don't know how to do this.

---

### Post by jpkotta on 2007-10-07
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Palm](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Palm)

---

