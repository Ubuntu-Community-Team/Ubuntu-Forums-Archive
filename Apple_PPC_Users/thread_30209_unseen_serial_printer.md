---
title: "unseen serial printer"
date: 2005-04-27
forum: Apple PPC Users
---

### Post by tonyB on 2005-04-27
Well, I mis-posted this into the warty forum.  <shakes head>  I'll try again:

I am running hoary on a 7300 w/ G3 upgrade card.  I recently was gifted an HP LaserJet 5MP.  I d/l the mac os driver from HP, and it performs fine under the mac os.  When I try to install it using the gnome administration printing utility, it says it does not see any local printer.  On previous Linux distributions I was able to access the printer by sending a file to /dev/ttyS0 or /dev/ttyS1 using cat.  Nothing happens when I do that in Hoary, so obviously the printer is indeed not there.  Anyone using a serial printer under Hoary?  Hints?  Suggestions?  Thank you in advance for any assistance.

tony

---

### Post by albertkain on 2005-07-22
I'm not an expert in Ubuntu or security issues but if just want to get your serial printer working under Hoary, below are the setups:

chmod a+rw /dev/ttyS0  (so that you don't get permission denied when trying to print)
chmod +x /usr/lib/cups/backend/serial  (so that serial ports appear Printer Admin)

Printer Admin don't allow you to change the queue name, if you want to do so:
vi /etc/cups/printers.conf and change <Printer XXX> to <Printer YourQueueName>

restart cupsys:
/etc/init.d/cupsys restart

Now your serial printer is working....

---

### Post by tonyB on 2005-07-27
[QUOTE=albertkain]I'm not an expert in Ubuntu or security issues but if just want to get your serial printer working under Hoary, below are the setups:

chmod a+rw /dev/ttyS0  (so that you don't get permission denied when trying to print)
chmod +x /usr/lib/cups/backend/serial  (so that serial ports appear Printer Admin)

Printer Admin don't allow you to change the queue name, if you want to do so:
vi /etc/cups/printers.conf and change <Printer XXX> to <Printer YourQueueName>

restart cupsys:
/etc/init.d/cupsys restart

Now your serial printer is working....[/QUOTE]


Thank you for this, Albert.  I had about given up trying to make this work.

I tried all the stuff you listed, and that did indeed make the printer show up in the Printer Admin app, and allowed me to create a print queue.  Since I was not sure which port corresponded to /dev/ttyS0 and /dev/ttyS1, I created a queue for both ports.  Although everything looks fine, when I try to print to either queue I get no output.  The job shows up in the queue and stays there for what appears like an appropriate amount of time to be processing the file, but no output.  I also tried to cat a file to /dev/ttyS[01] and that did not produce anything either.

Any suggestions on how to proceed from here?

Thanks again,
tony

---

### Post by chascon on 2005-07-29
I've never had to change permissions to get a printer to show up in the printer utility.  To get it to show, I've turned the printer on and left it on while I rebooted the computer.  Then run gnome-cups-manager and it'll show up.  Then configure.  You might have to try different drivers.  Try them all and keep notes on the ones that work.  When one driver refuses to work, try another driver (from your working list).  The other thing you can try is running '/etc/init.d//cupsys/ restart' (also ' .... stop', then ' ... start', perhaps as #) if cups server has crashed.  Use this ONLY as a last resort as I've never had to do this on ubuntu.

Lastly, your problem rings of problems I have when I print to a printer that is powered off.  The print job gets queued but stalls (because my printer was off when I evoked the print job) thus not letting any other further print jobs to print.  Powering the printer on immediately on AFTER evoking the print job doesn't work.  This scenario looks as if cupsys has crashed but it hasn't.  The solution for me is to delete that print job using the appropiate gnome utility and then powercycling the printer.  But when powering the printer up, power it up withOUT the usb cable inserted, count to 5, then insert the USB cable, count to 5.  Then try to print.

Indeed, have your printer powered on when initiating a print job.   If you do and it doesn't work, then try the power cycling solution before anything else.

---

### Post by tonyB on 2005-08-15
thanks chascon for the suggestions, and my apologies for the very slow reply.

i was only able to get the printer admin to see my printer by following albertkain's suggestions. <shrug> But, even though I could now setup the printqueue, and everything *appeared* to be working, I could never get any output on the printer.  I tried using different drivers as you suggested, but still no joy.

I've been poking at it from time to time, but i suspect it is not going to work until my next install -- or reinstall.

thanks again for your help.

tony

I meant to mention that i get a message for ttyS[01] when booting saying they have an illegal UART type unknown.  I installed setserial and tried to change the type for them, but it wouldn't do it.  (don't recall the message.)  this leads me to suspect something didn't get setup during the inital install of ubuntu.

---

### Post by albertkain on 2005-08-18
[QUOTE=tonyB]Thank you for this, Albert.  I had about given up trying to make this work.

I tried all the stuff you listed, and that did indeed make the printer show up in the Printer Admin app, and allowed me to create a print queue.  Since I was not sure which port corresponded to /dev/ttyS0 and /dev/ttyS1, I created a queue for both ports.  Although everything looks fine, when I try to print to either queue I get no output.  The job shows up in the queue and stays there for what appears like an appropriate amount of time to be processing the file, but no output.  I also tried to cat a file to /dev/ttyS[01] and that did not produce anything either.

Any suggestions on how to proceed from here?

Thanks again,
tony[/QUOTE]

If you cannot cat a file to /dev/ttyS0 or /dev/ttyS1, most probably you're not referencing the serial port correctly.  Maybe you have more than 2 serial ports and thus you should try to cat to /dev/ttyS2 to see if it works?  Or maybe the serial port is no good???

---

### Post by tonyB on 2005-08-25
[QUOTE=albertkain]If you cannot cat a file to /dev/ttyS0 or /dev/ttyS1, most probably you're not referencing the serial port correctly.  Maybe you have more than 2 serial ports and thus you should try to cat to /dev/ttyS2 to see if it works?  Or maybe the serial port is no good???[/QUOTE]

ls /dev/*S* only lists ttyS0 and ttyS1.  And the physical port must be ok because it works fine under Mac OS.  I suspect a re-install might fix this -- just a gut feeling -- but I use this system every day for doing "actual stuff" :) and I don't want to go through re-creating everything.  I'll try it a little later in the fall when I have a bit more time or when Breezy comes out.  Thank you again for your help and suggestions.

Regards,
tony

---

### Post by cory lee on 2006-02-15
i have a similar problem
i do not have /usr/lib/cups/backend/serial
file

can anyone help me.
printer is connected to the computer directly
can cat filename > /dev/ttyS0
also need port for ttyUSB0 usb to serial
also can cat filename > /dev/ttyUSB0

everything prints but serial and ttyUSB does not show up
lpinfo -v only show usb and parallel port
any one have an answer this problem???

---

### Post by Tommy on 2007-01-09
I'm adding a comment here (and taking a discussion from the Xubuntu mailing list to here).

If after upgrading from an older version of ubuntu you find that your oldworld serial ports no longer exist, it's because the newer kernels don't load the serial module. Fortunately it's still there, so all you have to do to re-enable your serial ports (this works in Ubuntu 6.06; can't say about others) -- add this line to /etc/modules 

```
pmac_zilog
```

Then after the next boot you should be able to see the serial ports. You can install the minicom program to twiddle with the modem or whatever, and (I hope) they will also be visible to cupsys (the CUPS daemon).


On 1/6/07, Frarquit wrote:
> 1) When I examine the dmesg output I get these lines:
> 
> [   76.648788] pmac_zilog: 0.6 (Benjamin Herrenschmidt
> <benh@kernel.crashing.org>)
> [   76.661021] ttyS0 at MMIO 0xf3013020 (irq = 15) is a Z85c30 ESCC -
> Serial port
> [   76.673774] ttyS1 at MMIO 0xf3013000 (irq = 16) is a Z85c30 ESCC -
> Serial port
> 
> 2) when I try configure the printer (Epson Stylus Color 1520) by the
> configure system> printers>add new printer> the option for serial local
> printer is not available (!)
> 
> 2a) I`ve tried serial:/dev/ttyS0, serial:///dev/ttyS0 and only
> /dev/ttyS0 but it does not work.
> 
> 2b) I think the printer`drive is not a problem. There are four drivers
> for Epson Stylus Color 1520.


I just did a few Google searches, and found that others have reported trouble using serial printers in later versions of Ubuntu. So we can also look at a few of the things they are doing.

A) Check Permissions -- see [https://launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/29050](https://launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/29050) (despite the title, troubles adding USB and Serial printers have been combined with that bug).  As described there, you might check to be sure the permissions are compatible -- what group do the serial ports get assigned to? On my system they're in the dialout group, so I suspect the cupsys user needs to be in the dialout group. (If on your box your /dev/ttyS* ports got assigned to another group, you'll want to add the cupsys user to the same group.)

B) If the serial port appears but you cannot connect to the printer, you may need to manually update the serial settings -- see [http://www.linuxquestions.org/questions/showthread.php?t=308086](http://www.linuxquestions.org/questions/showthread.php?t=308086)  as an example of a more elaborate serial definition. I think in many cases having just the port in printers.conf may work, such as:

```
DeviceURI serial:/dev/ttyS1
```
but you may need to override the defaults to match the speed, bits, parity and flow control your printer expects (or change it using switches or software) and make the CUPS configuration match.

The example at linuxquestions uses this setting:
```
DeviceURI serial:/dev/ttyS1?baud=1200+bits=8+parity=none+flow=none

```
which is a VERY slow printer port and having no flow control. I think it's unlikely yours will be that slow, and hopefully another form of flow control works (they probably had to slow the printer to 1200 because they couldn't get flow control working). I haven't yet looked for the syntax of the serial interface in the cupsys backend, so hopefully the permissions (item A above) will be all you need to update.

---

### Post by Tommy on 2007-01-25
I'm adding one more note here -- it may already have been mentioned in this thread, but I was just working with an Ubuntu 6.10 system and when I was having some CUPS problems I tried ```
sudo dpkg-reconfigure cupsys
``` and I noticed that the serial backend is not activated by default. You might want to check to see that it is. 

After you invoke that command, dpkg will shut down CUPS and then display some configuration screens (blue background). On the third screen it will list the CUPS backends -- scroll down using your arrow keys and look for the serial selection. Turn the selection on or off using the space bar. 

Be careful -- the setup screens noted that you would NOT want to activate the Parallel backend on a PowerPC because it might lock up the system.

I wasn't absolutely sure of some of the other configuration screens but in most cases I just pressed return for the default. 

Once you have activated the serial backend, the serial option should appear when you are configuring a new printer in CUPS.

---

### Post by carlosman on 2007-04-09
Thank you, Tommy!!!

Your advice made it for me. I have not used Ubuntu in a while, and you just saved my life.

> ```
sudo dpkg-reconfigure cupsys
```

---

