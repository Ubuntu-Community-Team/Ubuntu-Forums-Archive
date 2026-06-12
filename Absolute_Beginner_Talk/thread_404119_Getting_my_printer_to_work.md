---
title: "Getting my printer to work"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-08
I went to System>Administration>Printing and added my printer (DeskJet-932C) and it's not printing. Any ideas?

---

### Post by igknighted on 2007-04-08
> **x-ray vision said:**
> I went to System>Administration>Printing and added my printer (DeskJet-932C) and it's not printing. Any ideas?

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_932C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_932C)

Says your printer should work fine, make sure that it is using the driver recommended and that you have set it as default.

---

### Post by x-ray vision on 2007-04-08
I tried installing the driver using "Download the Self-Extracting Archive With Installer" on  [this](http://hplip.sourceforge.net/downloads.html) page. 

Part two of the directions says:

** Open a console/terminal and cd to the download directory.**

What cd?

---

### Post by jerrynewt on 2007-04-08
cd  means change directory. Open a terminal and type in cd <location you downloaded the installer to> and that should get you started.

---

### Post by x-ray vision on 2007-04-08
It's downloaded to my desktop.

I tried typing cd desktop

cd <desktop>


What exactly am I supposed to type in?

---

### Post by jordanmthomas on 2007-04-08
```
cd ~/Desktop
```
Note the capital D

---

### Post by x-ray vision on 2007-04-08
Okay I typed in 'cd ~/Desktop' and pressed enter, then 'sh hplip-1.7.3.run', and I got the message 'No such file or directory'.

What am I doing wrong?

---

### Post by jordanmthomas on 2007-04-08
What does the output of 
```
ls
``` give you?  (After you have cd'd to your Desktop)

It seems as though the file hplip-1.7.3.run is not on your desktop

**edit**  You'll also need to use sudo when we find out just where the hplip run file is hiding because installing the drivers requires root access.  It'll be something like this:
```
sudo sh ./hplip-1.7.3.run
```

---

### Post by x-ray vision on 2007-04-08
Sorry about that. Yes, it was no longer on my desktop.

I'm trying again and I'm at a point where it says "Please wait, this may take several minutes..." It's been like this for about five minutes; I hope it's not stuck. I'll be patient. :)

---

### Post by amohanty on 2007-04-08
Is ther any reason the hplip that comes with the repos is not working?? I think the package called hpijs is installed by default.

AM

---

### Post by x-ray vision on 2007-04-08
Well, everything went okay until it got to the point to open device. Then it opened the "HP Device Manager - Printer Setup Wizard" and no devices were found. It asked me to make sure my printer is on and connected, which it is (I tested it with Windows XP).

---

### Post by x-ray vision on 2007-04-08
I went to System>Administration>Printing and added my printer (DeskJet-932C) and it wouldn't print.

I then tried to download drivers by going to a terminal and entered "cd ~/Desktop" and then "sh hplip-1.7.3.run".

I got to a point where the result I got back was:  

[b]"Failed to open device 
error: No devices found.Please make sure your printer is properly connected and powered-on.[/b]

From there the HP Device Manager - Printer Setup Wizard popped up and it also said it couldn't find the device.

The printer is correctly connected and powered on and is printing in Windows XP.

Does anyone know what my next step should be?

---

### Post by nudnik on 2007-04-08
> **x-ray vision said:**
> I went to System>Administration>Printing and added my printer (DeskJet-932C) and it wouldn't print.

I then tried to download drivers by going to a terminal and entered "cd ~/Desktop" and then "sh hplip-1.7.3.run".

I got to a point where the result I got back was:  

[b]"Failed to open device 
error: No devices found.Please make sure your printer is properly connected and powered-on.[/b]

From there the HP Device Manager - Printer Setup Wizard popped up and it also said it couldn't find the device.

The printer is correctly connected and powered on and is printing in Windows XP.

Does anyone know what my next step should be?

One thing that comes to mind, but not the only thing; you should check to see if there are drivers already available via the printing setup. I am assuming Ubuntu can see your printer, otherwise you would not have been able to add it.

When you say "download drivers", does this mean you attempted to install a driver you already downloaded to your desktop? If so, are sure the driver was compatible with Debian/Ubuntu? If so, are you attempting to install the correct version, ie, i386/686 for Intel or the 64 bit version for AMD? If that is in order, did you have permissions to install? Were you root in the terminal?

All of this being said, try to install the driver provided by Ubuntu first before proceeding further.

---

### Post by x-ray vision on 2007-04-08
> **nudnik said:**
> All of this being said, try to install the driver provided by Ubuntu first before proceeding further.
How should I go about doing this at this point?

---

### Post by nudnik on 2007-04-08
> **x-ray vision said:**
> How should I go about doing this at this point?

Click on Printing under the System tab. When the window appears, right click on the icon representing your printer and click properties. Yet another window will appear (aint this fun?) click on the driver tab. There you should be able to adjust your selection of driver. 

Remember to see the mascot below. Its not Windows, but if were, someone would be trying to sell your identity to a intimidating fellow named Dimitri right now. :)

---

### Post by x-ray vision on 2007-04-08
What do I do when I get to the screen that says "Select a PPD file"?

---

### Post by nudnik on 2007-04-08
> **x-ray vision said:**
> What do I do when I get to the screen that says "Select a PPD file"?

Its asking you from what location it should install a driver you have downloaded. You can try directing it to the driver you downloaded earlier. If it rejects that one, you must uninstall the printer, and then reinstall it. Once you have done so, you will be able to select from a long list of drivers. Hopefully there will be one for your specific model.

---

### Post by nudnik on 2007-04-08
I have checked for you, and there is indeed a driver for your specific model included with Ubuntu. You should be able to select it from Step 2 of the printer install.

---

### Post by x-ray vision on 2007-04-08
The last one I got was for my specific model. :confused:

---

### Post by nudnik on 2007-04-08
> **x-ray vision said:**
> The last one I got was for my specific model. :confused:

If the correct driver is already installed, then I am at a loss as well. Ubuntu may need some additional instructions in order to communicate with your printer. You'll need someone with a little more experience to provide that. Sorry I couldnt be of more assistance.

---

### Post by x-ray vision on 2007-04-08
Thanks for trying. I'm thinking about reinstalling Ubuntu and starting from scratch.

---

### Post by metroknight on 2007-04-09
I just installed my printer after a clean reinstall.

I went System>Admin>Printing>new printer> followed the rest of the steps.

I didn't choose the PPD because it was showing that it had my drivers already and I just click forward and it installed the printer via cups. The printer is the same as yours (HP Deskjet 932c).

---

### Post by x-ray vision on 2007-04-09
I don't know what I did, but I just re-did the steps I tried a hundred times and it's printing now. :)

---

### Post by metroknight on 2007-04-09
That is wonderful. You could have just misstepped somewhere on the installation path. It happened to me enough times.

---

### Post by 11hjpphty76lkjj on 2007-04-09
Please run:
```

/usr/lib/cups/backend/hp
```

and post the output.

A

---

### Post by Ambimom on 2007-04-09
I have the same printer....Right click on the printer and open properties tab
click on the Driver tab
and select Model deskjet 932C
(at bottom of this window is a tab that says "install driver"
the suggested driver is hplip 097

then go to connection tab
the local printer should be ticked
specify the port (I use parallel) It directed me to select the Epson printer port

Now see at the bottom left of this window "print test page"

It should print...but be warned...it takes at least a minute and half for the page to start...make sure the printer is turned on....because it doesn't come on automatically as it does in windows.

Good luck

---

