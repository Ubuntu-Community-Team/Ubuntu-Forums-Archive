---
title: "Connecting to the internet"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by sharong on 2006-12-18
I have a laptop (DELL Inspiron, if that makes any difference) and I've installed Ubuntu.  I can't get connected to the internet.
First I tried to get the winmodem to work, but I just couldn't follow the instructions so I gave up and bought a serial modem.
Now I've no idea what to do.  Someone said 'plug it in and it will work', so i plugged it in, double-clicked on Firefox and tried to load up a web page.... but that didn't work.

I've read some of the help pages, but didn't really get anywhere.  So far I think I've established that there are 2 bits to this - setting up the network, and then actually dialling up and getting online.  I don't know how to do either.

So, can someone help me?

Thanks!!

---

### Post by Sef on 2006-12-18
Have you checked out [linmodems]("http://linmodems.org")?

---

### Post by Bartender on 2006-12-18
Well, it's not quite as simple as "plug it in & it will work".  With the serial modem plugged in and turned on try restarting your lappy.  It seems to work better if the devices are energized & detected by Ubuntu during startup.  
Then go into System>Administration>Networking and see if Ubuntu shows a new modem device.  It should.
Right-click on it, go to Properties, General tab, you'll need to enter the phone number you dial (be sure you get this right - the phone number in the first line and any prefixes, such as *70 to disable call-waiting in the second line) your full username including everything after the "@", and your password.

Under the "Modem" tab, Dapper has a neat "auto-detect" feature so that you don't have to guess whether the device is on tty0 or tty1 or whatever.  Xubuntu and Edgy did not seem to have this.  Your dial type is probly "Tones" and for now at least you'll want to set the volume to "Medium" or "Low" instead of "Off".  At least until we know it's working.

Under the "Options" tab I checked the first 2 options to "On" but that's your call.  I'm not sure about what the checkboxes do but that's working for me.

Another thing that may be hanging you up - on my old eBay-acquired USR 5686 external there's a bank of little tiny switches that must be set up correctly.
What's the brand of your modem, and does it have a bunch of switches on it somewhere?

If you can get to this point (modem is on, Ubuntu detected it correctly, etc) right-click on your upper panel and go to the "Add" window.  Drag or add Modem Monitor to the upper panel.  If I remember correctly Modem Monitor is also missing from Xubuntu and Edgy, so Ubuntu Dapper is probly the best choice for those of us stuck with modems.  Not sure about Kubuntu Dapper.  
Right-click on Modem Monitor and "Activate" the modem.  Check to see if the lights start blinking and you get any sounds from it.  If you hear a taped operator message you know you didn't get the phone number or prefix right.

---

### Post by ieee488 on 2006-12-18
You'll need to get your username and password for your ISP.

I have AT&T Worldnet, and in Windows, I really didn't have to worry about what they
are exactly. I put in the installation CD and pretty much got every up and working
without much work on my part. With Linux, that isn't possible. Since you bought a serial
modem - not USB - it won't be that hard to get online.

I'm using Dapper and I love it. For what I want to do which is go online, it is great!

---

### Post by tf37 on 2007-01-19
Thanks again Bartender, once again you hit the nail on the head:) 
I was missing the silly setup under system - admin, etc...
Did go to the terminal and did a wvdialconf, but had to change the config file to rw rw rw...pain
But done, now to test
Thanks again
Terry:cool:

---

