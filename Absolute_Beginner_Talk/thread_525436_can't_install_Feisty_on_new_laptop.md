---
title: "can't install Feisty on new laptop"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by dlaw on 2007-08-14
I just bought a new Toshiba laptop over the weekend and I am trying to install Feisty on it using the CD that Ubuntu sent me.  I try to install using the CD and it seems fine until the end.  It gives me the "Failed X Server" blue screen.  

When I use the command "startx" it gives me the following errors.

(EE) VESA (0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal Server Error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

I've tried "sudo dpkg-reconfigure xserver-xorg" but i im not sure which options to change.

I'm not completely new to Ubuntu, i have it running on my PC but I'm not totally familiar with the "inner workings" of it.  I know there are similar post on here with similar errors but it seems that Ubuntu had already been installed on there computer and i do not.

My Laptop specs:

Toshiba A215-S4697
15.4" screen
AMD Turion 64 X2
ATI Radeon X1200
160 Gb harddrive
1 Gb of ram
Windows Vista

Any help would be greatly appreciated, Thanks

---

### Post by Inxsible on 2007-08-14
Maybe installing Ubuntu with the Alternate CD would work. You can then reconfigure your graphics  drivers after installation.

---

### Post by nvrpunk on 2007-08-14
Things you need to look up on the Manufacturers Website.

Vertical Refresh range

Horizontal Refresh range

No matching modes means it is saying your monitor doesnt support the settings using the Vesa driver, ie vga in the xorg.conf.

---

### Post by dlaw on 2007-08-14
thanks for the response.

nvrpunk: I can't seem to find the refresh rates of the monitor on this laptop.  I've checked the user manual as well as the Toshiba website.

Inxsible: I will try that tonight

---

### Post by eapache on 2007-08-14
Use this link here: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by dlaw on 2007-08-15
hey eapache, i tried the how-to you sent me but it doesn't seem to work.  I was able to install Ubuntu using the alternate CD however when it finishes loading it still gives me the "Failed X server" blue screen.  It then asks me to login with my Username and Password.  This is where i tried to update the packages but nothing happened.

I use the "startx" command to see if anything changed and it is still the same error message.

If any body has any more ideas please let me know.

Thanks

---

### Post by jimrz on 2007-08-15
[[COLOR="Sienna"]**_this_**[/COLOR]]("http://www.bohne-lang.de/spec/linux/modeline/") might, using the vid settings from your windows, help you calculate the values you need

---

### Post by eapache on 2007-08-15
Did you run the updates before or after you logged in? You should log in first with the values you chose during the install, then run the updates afterwards. It doesn't accept commands during the login screen.

If you did try the updates after you logged in, and they still don't work, run```
sudo nano /etc/X11/xorg.conf
```and see if you can find your monitor and graphics card.

---

### Post by dlaw on 2007-08-15
things have gotten worse.  Now that i have installed Ubuntu on the laptop using the alternate CD, Windows Vista can't load at bootup.  Hopefully the Startup Repair will fix this.

eapache: i ran the updates after logging in.  i will try it again as soon as Windows finishes repairing

---

### Post by dlaw on 2007-08-15
OK, Windows finished repairing and it seems to be working fine.

i ran "sudo nano /etc/X11/xorg.conf" and this is what it says for the monitor and graphics card:

Section "Device"
             Identifier    "Generic Video Card"
             Driver         " vesa"
             BusID          "PCI:1:5:0"
EndSection

Section "Monitor"
              Identifier       "Default Screen"
              Device           "Generic Video Card"
              Monitor          "Generic Monitor"
              DefaultDepth     24

               Then it continues with the "display" subsections for Depths of 1, 4, 8, 15, 16, 24 all with modes "1024x768"  "800x600"  "640x480"

---

### Post by eapache on 2007-08-16
OK, for some reason it got a bit messed up. Change it to this:

Section "Device"
Identifier "Generic Video Card"
Driver " vesa"
BusID "PCI:1:5:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24

Then ctrl-o to save, ctrl-x to exit, and then type```
sudo startx
```

---

### Post by dlaw on 2007-08-16
hey eapache, that didn't seem to work.  The "startx" error is still the same as before.

thanks for your continued help

---

### Post by stchman on 2007-08-16
> **dlaw said:**
> I just bought a new Toshiba laptop over the weekend and I am trying to install Feisty on it using the CD that Ubuntu sent me.  I try to install using the CD and it seems fine until the end.  It gives me the "Failed X Server" blue screen.  

When I use the command "startx" it gives me the following errors.

(EE) VESA (0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal Server Error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

I've tried "sudo dpkg-reconfigure xserver-xorg" but i im not sure which options to change.

I'm not completely new to Ubuntu, i have it running on my PC but I'm not totally familiar with the "inner workings" of it.  I know there are similar post on here with similar errors but it seems that Ubuntu had already been installed on there computer and i do not.

My Laptop specs:

Toshiba A215-S4697
15.4" screen
AMD Turion 64 X2
ATI Radeon X1200
160 Gb harddrive
1 Gb of ram
Windows Vista

Any help would be greatly appreciated, Thanks

Did you try the safe graphics mode?

---

### Post by eapache on 2007-08-16
Sorry, go back in and see if the changes were actually saved. I forgot that you have to press enter after ctrl-o to save (ctrl-o just brings up a dialogue). If you did apply the changes, then please post the section of xorg.conf called "serverlayout".

---

### Post by dlaw on 2007-08-20
Hi everyone, Sorry i was MIA for the last few days i had a busy weekend.

eapache: The stuff you told me to change was saved. the "serverlayout" section is:

Section "Serverlayout"
Identifier       "Default Layout"
Screen           "Default Screen"
InputDevice   "Generic Keyboard" 
InputDevice   "Configured Mouse" 
InputDevice   "stylus"    "SendCoreEvents" 
InputDevice   "cursor"    "SendCoreEvents"
InputDevice   "eraser"    "SendCoreEvents"
InputDevice   "Synaptics Touchpad"
EndSection

---

### Post by ghstzr0 on 2007-08-21
I too have a very similar problem, but on an on-board radeon chip on my desktop.  The problem seems to stem from X.org not being able to identify the card.  You'll notice it just says "Generic Video Card" in xorg.conf...

Type in ```
lspci
``` and I bet you'll see an entry similar to: ```
01:05.0 VGA compatible controller: Unknown video device
```

If you try ```
sudo update-pciids
``` this seems to correctly identify the device in lspci, it now says ```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
```

But, to no avail, this still does NOT fix the ```
(EE) No devices found
``` issue.

I have searched far and wide for the solution to this and no one knows it.  MORE PEOPLE HAVE TO HAVE THIS CHIP!!  Help!

---

### Post by dlaw on 2007-08-21
hey ghstzr0 this is what it says for "lspci":

01:05:.0 VGA compatible controller: ATI Technologies Inc Unknow Device 791f

Also, now in my "startx" command there is a new error:

xauth:  erro in locking authority file /home/dlaw/.Xauthority

---

### Post by eapache on 2007-08-21
Dlaw, try changing the driver from vesa to ati. If that doesn't work, I'm afraid there's nothing else I can think of that would be causing this problem. Sorry.

Ghstzr0, can you please post the contents of your xorg.conf file.

---

### Post by mrhirsh on 2007-08-22
I have the exact same laptop and (surprise!) I have the exact same problem.  Have you been able to resolve yours?

What did you finally do?

thanks,

---

### Post by mrhirsh on 2007-08-22
Peapache:

When I attempt to enter the lines you suggest after I do the nano/etc/x11/xorg.conf command, it will not save those changes.

Any other suggestions.
Thanks,

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
sudo nano then all that crap kuzz you need to be root

you also need the refresh rate to properly configure xorg.conf file

---

### Post by eapache on 2007-08-23
The command needs to```
sudo nano /etc/X11/xorg.conf
```Please note the sudo in front.

---

### Post by dlaw on 2007-08-23
hey mrhirsh, i have had no luck at all

not even close to being resolved.

I am now going to try to uninstall Ubuntu until someone can figure this out

---

### Post by dwhitney67 on 2007-08-23
> **dlaw said:**
> things have gotten worse.  Now that i have installed Ubuntu on the laptop using the alternate CD, Windows Vista can't load at bootup.

That's a good thing (that Vista can't load)!  :lolflag:

Back to your problem at hand, it seems typical for those who try to install Ubuntu on system with ATI video cards (chip sets).

Install Ubuntu with the Alternate CD.  I had to do this myself because I have the ATI X1300.

After installation, I followed these [instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") on this page to get the proper video driver (from ATI) to get X-windows running properly.

I had no trouble whatsoever.  I followed the instructions for Ubuntu 7.04 (Feisty) to the letter.  If you deviate from what is specified then your results may vary.

---

### Post by pgar23 on 2007-08-23
> **dlaw said:**
> hey ghstzr0 this is what it says for "lspci":

01:05:.0 VGA compatible controller: ATI Technologies Inc Unknow Device 791f

Also, now in my "startx" command there is a new error:

xauth:  erro in locking authority file /home/dlaw/.Xauthority

This problem might be occuring BECAUSE you are using a ATI RADEON CARD. try checking the sticky at the top of the absolute beginners page. I used to have this problem, followed the directions from the sticky and it worked for me. HOPE IT HELPS.

good luck.

---

### Post by ghstzr0 on 2007-08-24
> Ghstzr0, can you please post the contents of your xorg.conf file.

Sorry, I can't post my xorg.conf file right now, but I assure you that I did nothing to change it.

I do remember that the card was referenced as "Generic Video Device" under the device settings.  My PCI ID is 1:05:0.

> hey ghstzr0 this is what it says for "lspci":

01:05:.0 VGA compatible controller: ATI Technologies Inc Unknow Device 791f

I'm not sure about the "791f", but yes, that looks very familiar!

---

### Post by dlaw on 2007-08-28
to run all these updates and upgrades i need to be online correct? how do i know that i've established a connection since im using a laptop?

---

### Post by eapache on 2007-08-28
Run```
ping http://www.google.com
```in a terminal and see if it returns anything.

---

### Post by mali2297 on 2007-08-28
> **eapache said:**
> Run```
ping http://www.google.com
```in a terminal and see if it returns anything.

That will give
> 
ping: unknown host [http://www.google.com](http://www.google.com)

if there's a connection.

I think it would be more interesting to run
```

ping -c 10 www.google.com

```

---

### Post by dlaw on 2007-08-28
both ping commands give:

ping: unknown host [www.google.com](www.google.com)

i assume that im not getting an internet connection since none of the how-tos have been working for me
 
i've all but given up on installing Ubuntu on my laptop.  Maybe i will just wait for the next release and hope that ATI works with it, unless somebody out there has any more bright ideas.

thanks everyone for getting me this far

---

### Post by dlaw on 2007-09-02
hi everyone,

I am back on campus so I have internet access to my laptop.
The command mali2297 gave me shows that the connection is transferring packages and gives an IP.

I tried following the sticky at top of the "Absolute Beginner" forum but the updates don't seem to be loading.

When I run: "sudo apt-get update" i get

"Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz) 
302 found"

it continues with many variants of this with different sources such as binary and multiverse.

---

### Post by helliewm on 2007-09-02
See this thread I think its your ATI graphics card.

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I have an ATI X1300 graphics card. What I did was installed Drapper and then upgraded to Edgy. This ensured I had working internet connection. I then followed the instructions in the above THREAD [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) to install the fglxr ATI graphics drivers.

Yes time consuming but quite simple and easy. I have Open GL and wobbly windows and etc and everything works.

Helen

---

### Post by dlaw on 2007-09-02
any other advice/opinion on this matter?  I am pretty sure the internet connection to my laptop is working.  It's just that updates won't download from the sources.

---

