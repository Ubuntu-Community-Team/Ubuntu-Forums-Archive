---
title: "Apple keyboard acts like Windows keyboard"
date: 2010-02-13
forum: Apple Hardware Users
---

### Post by Zomaian on 2010-02-13
So this is the first time installing Ubuntu on my iMac which is maybe from 2004 or something meaning it has the old (wireless) Apple mouse and keyboard. The installation went fine which I installed with a Windows (Dell) keyboard and mouse connected via USB.

Once I got Ubuntu installed I tried adding the Apple mouse and keyboard via Bluetooth which failed first. I installed a application called bluez which was able to connect to my Apple mouse but not the Apple keyboard. Than I unistalled Bluez and tried Blueman which seemed to regonize the Apple keyboard but failed to connect to it. I than installed gnome-bluetooth back and now I got gnome-bluetooth and Blueman installed which when both installed seem to be able to connect to my Apple keyboard and mouse.

Now that I got those two working with a bit of trouble I stumbled on two new problems:

1) My Apple keyboard acts like a Windows one meaning Ctrl+C instead of Home+C. Now I could care less about that but than I realized that my Apple mouse might be a bit pointless without the Control key meaning I am not not able to left click with my Apple Mouse and Keyboard. I already set my Keyboard layout to USA Macintosh but sometimes it gives me an "error activating xkb configuration" error is probably the problem. So how do I get my Apple keyboard functions to work?

2) During removing and installing all those bluetooth files like gnome-bluetooth, Blueman, and Bluez I seemed to uninstalled the Network application because the little network icon disappeared in my bar and System -> Preferences meaning I got no control over my cable/wireless internet settings or connections but somehow I am still connected. So how do I install that pack, whats the name of it in the Package Manager?

Thanks a lot & Cheers,
Bob

---

### Post by linuxopjemac on 2010-02-14
ad 2:
sudo apt-get install networkmanager

ad 1:
[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

---

### Post by Zomaian on 2010-02-14
> **linuxopjemac said:**
> ad 2:
sudo apt-get install networkmanager

ad 1:
[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

I got an error when installing the networkmanager but than I installed network-manager-gnome in the Synaptic Package Manager which seems to be working now, atleast I can connect to Wireless Internet smoothly.

Now the main problem is not solved yet since I do not understand what that article you gave me wants me to do. It more explains some stuff in my opionion but does not clearly give me a fix. Any ideas on how I can get my Apple Mouse to click left with the help of with Apple keyboard? The Apple keyboard works smoothly and good except it acts like a Windows keyboard :/.

Thanks,
Bob.

Edit:

I fixed the other problem by following this guide: [http://linuxbasement.com/content/enable-right-apple-button-macbook-right-click-button](http://linuxbasement.com/content/enable-right-apple-button-macbook-right-click-button) which basically installs this addon that allows me to use the F12 key to right click. Now I followed the guide to change the F12 key to the Mac (Home) key but now when I click the left Home key nothing happens but the right one does work. How can I make it so when you press the Left Mac Home key the right click menu pops up?

```

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default.
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 0 126"        # Right Apple Key with no modifier
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypresss

```When I have the file like that the F12 key acts like the right click menu but when I do this:
```

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
RIGHT_CLICK="-right 0 126"        # Right Apple Key with no modifier
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypresss

```The right Mac Home key acts like the right click menu, as you see the only thing I removed was the "#". Now how can I change this to the left? I already tried changing the "right" to "left" but it doesn't do anything. Any help?

---

### Post by linuxopjemac on 2010-02-14
I found this in my mouseemu conf file

#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click

So I guess what you want then is the following:

```
RIGHT_CLICK="-right 0 125"        # Left Apple Key with no modifier
```

What I don't understand is that with xev, I get completely different codes for those keys

Left Apple key in xev is 133
Right Apple key in xev is 134

I don't understand the key codes of mouseemu....

---

### Post by Zomaian on 2010-02-15
> **linuxopjemac said:**
> I found this in my mouseemu conf file

#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click

So I guess what you want then is the following:

```
RIGHT_CLICK="-right 0 125"        # Left Apple Key with no modifier
```What I don't understand is that with xev, I get completely different codes for those keys

Left Apple key in xev is 133
Right Apple key in xev is 134

I don't understand the key codes of mouseemu....
Thanks it worked! Now I can use the left Home key ;). But yea I agree with you its a bit complex also whats the point of the whole "#" since that also effects the key location and numbering.

---

