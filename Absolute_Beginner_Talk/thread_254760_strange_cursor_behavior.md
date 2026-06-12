---
title: "strange cursor behavior"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by ryu kun on 2006-09-10
Hi everyone!

I use a HP pavilion dx5158ea laptop. Ubuntu version 6.06.

When I type something in any application, cursor sometimes goes to where my mouse pointer is at that moment. Or sometimes windows can behave strangely, like firefox goes one page past or active window gets minimized although I didn't do anything. It can be very annoying when you type something.

I guess it may be a problem caused by my touchpad. So I tried to add these lines to my */etc/xorg.conf* file to decrease its tapping sensitivity.

```
Option "CircScrollDelta" "0.5"
Option "MaxTapTime" "60"
Option "MaxSpeed" "1"
```

But problem persisted.

Have you got any idea, whan can cause or how to solve this annoying problem?

Thanks in advance.

---

### Post by ryu kun on 2006-10-02
solution: 

```
sudo gedit /etc/X11/xorg.conf
```

add this line below Section "InputDevice" Identifier "Synaptics Touchpad" 
(it will disable the "button" function from the tap-pad)

```

	Option		"TapButton1"		"0"
```

to see your current settings, just type ```
synclient -l
```

[this page]("http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/#comment-9949") helped.

---

