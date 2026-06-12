---
title: "Apple BT Keyboard Fn Key ModMap"
date: 2011-11-29
forum: Apple Hardware Users
---

### Post by Finog on 2011-11-29
I'm connecting an Apple Bluetooth Aluminum keyboard ([http://www.apple.com/keyboard/](http://www.apple.com/keyboard/)) to my Lubuntu setup using the blueman applet.

The keyboard connects fine and most of the keys do what I expect. However, the fn key does not seem to function. I cannot use it to change screen brightness or volume. Nor can I figure out how to use it in combination to do page-up (fn+ctrl+down), page-down (fn+ctrl+up), et cetera.

When I use xev, I don't see anything happen when I press fn.

Do I need to configure blueman's "Input Service" setting somehow to indicate the type of keyboard I'm using? (It's not obvious how to do this.)

Is xev just not showing the fn key?

Is there some xmodmap black magic I should apply?

Where in this stack of software do I need to make a change to achieve the desired behaviour?

Thanks!

---

### Post by ChilledWort on 2011-12-30
Is your keyboard a new Lion model?  I have a new usb model apple aluminum keyboard and have the same problem.  No fn key period.

---

### Post by ubix on 2011-12-31
Does the following command when entered in your terminal display number one **»1«** on the terminal? 
```
cat /sys/module/hid_apple/parameters/fnmode
```
If it does, do **»sudo gedit /etc/rc.local«** and insert the following line before last line which should be **»exit 0«**.

```
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

Make sure you inserted the above line before the line that contains **exit 0**. After rebooting your function keys in Ubuntu should work without **»fn«** key. 

Please tell me if this helped?

---

