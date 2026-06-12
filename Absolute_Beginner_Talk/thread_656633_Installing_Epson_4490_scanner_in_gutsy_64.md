---
title: "Installing Epson 4490 scanner in gutsy 64"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Michaelg14 on 2008-01-02
The title says it all.  I got the iscan packages but when I try to run alien on them I get errors:

Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `iscan-2.10.0': File exists
unable to mkdir iscan-2.10.0:  at /usr/share/perl5/Alien/Package.pm line 257.

The first time a ran it I got different errors one of which said something about not supporting 64 bit systems.

Any Ideas on how to get this scanner working?

Mike

---

### Post by Mikes80 on 2008-01-17
Hey Michael.

First of all I  don't use iscan to get my Epson DX4000 to work with Ubuntu. Perhaps you are using this for personal preference. If so I may not be able to help :(.

I need a bit more info to help. 

[LIST=1]
[*]Does the scanner use a usb connection?
[*]Have you tried using it with Xsane? (this is what I use)
[*]If you have, what where the results?
[/LIST]

---

### Post by Michaelg14 on 2008-01-17
Hi Mike

Yes, it is USB.  When I use Xsane it fails to locate the scanner.  I am using Windows XP in Virtualbox and it works fine so I know it works and is connected correctly.

doing a lsusb gives me

Bus 005 Device 011: ID 04b8:0119 Seiko Epson Corp. 

But still it is not recognized by any Ubuntu software.

Mike

---

### Post by Mikes80 on 2008-01-17
Try this to get it running with Xsane.

Open the file /etc/udev/rules.d/45-libsane.rules with a text editor.

Find the Epson section, it's about half way down.

Copy one of the Epson rules lines. It doesn't matter which one. Paste it on a seperate, new line.
For clarity the line will look like (or at least similar too) this;

```
# Epson Perfection 636U
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0101", MODE="664", GROUP="scanner"

```

Now change the idProduct number so it matches yours. It will now look something like this. (Changes highlighted)

```
# Epson Perfection
SYSFS{idVendor}=="04b8", ***SYSFS{idProduct}=="0119"***, MODE="664", GROUP="scanner"
```

Save the file. The on to part 2 :)

Using a text editor open the file /etc/sane.d/epson.conf add the following to the bottom of the file
```

usb 0x04b8 0x0119
```

save the file.

Add yourself to the scanner group, in a terminal;

```
sudo usermod -aG scanner* yourusername*
```

Now reboot your computer to allow the changes to take effect.

Now try Xsane. Does it work? I hope so! :)

---

### Post by Michaelg14 on 2008-01-17
That was a definite help, at least Xsane starts now.  When I try to scan I get:

"Failed to start scanner: Invalid argument

Mike

---

### Post by Mikes80 on 2008-01-18
That's disappointing. :(

I've had a look on google and provided a link which sheds some light on the situation. Though no solution I'm afraid.

From the Sane website:
[http://www.xs4all.nl/~ljm/SANE-faq.html#49](http://www.xs4all.nl/~ljm/SANE-faq.html#49)

There could be any number of reasons why it doesn't work. From what I've read it may be necessary to go down the iscan route. Which brings us back to your original problem. I've not much experience with Alien so can't help in that regard. I recommend opening another thread in the x86_64 forum to see if anyone has experience with alien in 64 bit.

I'll keep my eye on this thread and do a bit more research, if I find anything I'll let you know. Keep me posted on your progress. :)

Sorry I couldn't be more help at this time.

---

### Post by Michaelg14 on 2008-01-18
Thanks Mike, you got me further along.  Someday I will get it to work.  In the meantime it works under Windows in Virtualbox just fine.

Mike

---

### Post by luca.mg on 2008-02-23
try [http://ubuntuforums.org/showthread.php?p=4389626#post4389626](http://ubuntuforums.org/showthread.php?p=4389626#post4389626) 

ciao luca

---

### Post by Michaelg14 on 2008-02-25
Thank you for that information.  As I use Virtualbox for other things I just installed the Windows software that came with the scanner and it works fine.  Granted, that may not be a solution that appeals to the die-hard Linux users but it has the advantage of working without jumping through hoops.

---

### Post by Thing0ne on 2008-04-04
So, after messing around with this same problem for a few days, trying to compile from tarball and a few other avenues, I was able to get iscan to work.  I dl'ed the rpms from Epson, then rather than trying to install, I opened them with file roller and manually copied the files out the the appropriate directories.  Odd, that that should work but it does.  At least for iscan.  scanimage -L and xsane still can't see anything, but at least iscan does.  I'll keep plugging away to see if I can get the rest to work.

---

### Post by dryder on 2008-04-15
Please let us know how you go ... :)

David

---

