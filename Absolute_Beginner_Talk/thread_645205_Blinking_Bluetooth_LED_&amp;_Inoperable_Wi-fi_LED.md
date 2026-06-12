---
title: "Blinking Bluetooth LED &amp; Inoperable Wi-fi LED"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Firi on 2007-12-19
While using the Ubuntu 7.10 i386 Live CD on a Dell XPS M140 notebook, the Bluetooth LED constantly blinks and the wi-fi LED does not seem to work at all.  The only way that I have found to stop this is to hit "Fn + F2" which stops all outgoing signals, including wi-fi.  Obviously, I'd like to have wi-fi connectivity without the Bluetooth LED constantly blinking.  Perhaps there is a way to turn Bluetooth off when I'm not using it?  In fact, I am having the same problem as this person (same notebook and everything):

[http://ubuntuforums.org/showthread.php?t=467118](http://ubuntuforums.org/showthread.php?t=467118)

And my case is similar to this:

[http://ubuntuforums.org/showthread.php?t=599246](http://ubuntuforums.org/showthread.php?t=599246)

But none of these people seemed to get much help.  I don't really care about the wi-fi LED, because I can get wi-fi to work without any problems (other than the LED, of course).  Bluetooth, while I haven't tested to see if it actually works, should not be constantly (and rhythmically, I might add) blinking.

The thing is, when I restarted my computer from Ubuntu Live CD to Windows XP Professional, the Bluetooth LED continued to blink the entire time.  When I then restarted from Windows XP Professional back to Windows XP Professional, the Bluetooth LED continued to blink the entire time.  Only when I completely shut down my computer from Windows XP Professional and restarted to Windows XP Professional did the Bluetooth LED stop blinking.

So, any ideas on what the issue might be?

How can I stop the Bluetooth LED from blinking when using Ubuntu?  What about the wi-fi LED?

---

### Post by Firi on 2007-12-20
All right, I found out how to turn off the blinking Bluetooth LED here:

[http://ubuntuforums.org/showthread.php?t=361802](http://ubuntuforums.org/showthread.php?t=361802)

"If you want to shut down the bluetooth just enter:
sudo hciconfig hci0 down
sudo rmmod hci_usb
and it will switch off. If you want it back on just turn it on the usual way (Fn+F2)..."

This thread also has a fix for the wi-fi led, but I don't think that I can test it because it requires saving and restarting and I'm still using the Live CD.

The only thing I'm worried about is having to enter the "stop Bluetooth and its LED" command everytime I boot Ubuntu.  I'm assuming that the blinking Bluetooth LED will return each session.

I've yet to see if Bluetooth actually works or not.

Also, unrelated, I'm trying to find out how to remotely print to a Lexmark Z515 printer.  I basically need drivers, but I'm unsure where to get them for Linux (or if they even exist).  Any ideas?

---

