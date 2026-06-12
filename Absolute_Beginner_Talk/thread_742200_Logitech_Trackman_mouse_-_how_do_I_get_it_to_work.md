---
title: "Logitech Trackman mouse - how do I get it to work?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by t0p on 2008-04-01
Last night I discovered a Logitech Trackman mouse in my collection of hardware.  It doesn't have the same kind of plug as my Microsoft PS/2-style mouse - the Logitech Trackman has a plug that goes into a 9-pin socket.

I plugged the Trackman into the only socket on the back of my computer that it can fit into... and it doesn't work.  And it doesn't show up under **System > Preferences > Hardware Information**.  *It doesn't work, dammit!!!*  :(

So:  does anyone know how I can get the Trackman to work?  Eh?  Anyone??

---

### Post by artfwo on 2008-04-02
I presume, the 9-pin socket is the serial port, right? In that case, to make X work with your Trackman, you'll have to manually edit your xorg.conf. To open the file, run the following command in Terminal:
```
sudo gedit /etc/X11/xorg.conf
```

And create a section like this there (just below your regular mouse section):
```
Section "InputDevice"
    Identifier "Logitech Trackman"
    Driver "mouse"
    #Option "CorePointer" # <-- uncomment if you want it to be the primary pointer
    Option "Device" "/dev/ttyS0" # <-- if that does not work, try ttyS1 for COM2
    Option "Protocol" "auto"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
EndSection

```
I also think setting the protocol to "ExplorerPS/2" is okay. Hope this helps :)

---

