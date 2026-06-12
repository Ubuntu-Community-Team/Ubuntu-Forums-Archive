---
title: "Mouse click delayed mere milliseconds"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by +peter on 2008-11-13
So this is a problem that I have had with every Ubuntu install, my mouse click is delayed a millisecond or so. This is frustrating when clicking and moving your mouse at the same time, causing you to miss. It is a problem with both my mouse and track pad.

I used to fix this by going into xorg.conf and turning "emulate 3 button mouse" off. However, in Intrepid, this option is no longer there. I understand that the Xorg.conf file has less importance now ... I just need some pointers on how to solve this. Thanks!

---

### Post by stream303 on 2008-11-14
Hmm.. maybe fool with the environment a little here.

Are you using a KVM switch?  Are the mice and trackpad connected directly to the machine and not via something else in between?  Does the mouse work ok without the trackpad or visca versca?

Does forcing it to redetect the mouse by disconnecting and reconnecting it make any difference?

And of course the smarty-pants answer:  have you tried a 3-button mouse?  On my Intrepid ppc box, a microsoft mouse works fine.  However I can understand it if you prefer a one button mouse.

I wish I knew more about how the new Xserver handles mice and keyboards, so I don't know what to say there in regards to xorg.conf...

---

### Post by +peter on 2008-11-15
Thanks for the thoughts! My mouse plugs directly into my USB port and is a Logitech 3 button mouse. 

I have had this problem with every Ubuntu install, and I always solved it by deactivating "emulate 3 button mouse" in Xorg.conf.

Now that Intrepid handles it differently, I am lost. I guess more research is required. If anybody can point me in the correct direction, that would be awesome!

---

### Post by jakon on 2008-12-28
I also see this on a PC with a Logitech 3 button mouse. And it sucks.

I don't have the complete solution, but i do have a pointer:
[https://bugs.launchpad.net/xorg-server/+bug/54191](https://bugs.launchpad.net/xorg-server/+bug/54191)

---

### Post by jakon on 2008-12-28
The workaround for the mouse click delay in Intrepid:

**1.** Execute
```
xinput list --short
``` and note your mouse name. For me, this is "Logitech USB-PS/2 Optical Mouse".

**2.** Create the file /etc/hal/fdi/policy/mouse-3button.fdi , containing (replace the mouse name with yours!):
```
<match key="info.product" string="Logitech USB-PS/2 Optical Mouse">
 <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
</match>
```

**3.** Unplug your mouse and replug it. (This won't suffice if it's a PS/2 mouse i guess. In this case reboot.)

---

### Post by C7M on 2009-03-25
Wow, thanks a lot, this solution worked for me!:D
I've tried a lot of different solutions but none of them worked. 
Changing "emulate3buttons/emulate3mouse/emulatewheel" to "false/no/0" in xorg.conf sections also didn't help. 
Now i can play quake 3 :cool:
PS. USB mouse Genius Ergo 520

---

