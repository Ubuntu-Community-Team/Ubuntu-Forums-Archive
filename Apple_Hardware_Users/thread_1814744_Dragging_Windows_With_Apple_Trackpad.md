---
title: "Dragging Windows With Apple Trackpad"
date: 2011-07-30
forum: Apple Hardware Users
---

### Post by ryanclancy000 on 2011-07-30
Hey guys,

I'm currently using my Macbook Pro 7,1 with Ubuntu 11.04. After switching recently from Lion, I've realised that I can't click and drag windows around or resize things like categories, etc. I have installed GPointing Devices which made it so I can 2 finger scroll again, but still no click and drag. Any insight?

~Ryan

---

### Post by Allsixcolours on 2011-07-30
Unfortunately, Ubuntu does not support full multi-touch without some additional drivers. There are a few programs in the software center that claim to add support for multi-touch gestures, but they really don't help much. The most helpful solution I have found so far is in this thread:

[http://ubuntuforums.org/showthread.php?t=1730361](http://ubuntuforums.org/showthread.php?t=1730361)

I'd give you the exact page, but it will be more helpful to you if you act least scan a few of the pages to learn more about it. It is actually a different version of another, original driver, but I have tried both and prefer this one. You should know that there are multiple sets of instructions in the thread, and the ones towards the back are the most up to date. I'm using it as we speak and it works great once adjusted. Hope this helps.

---

### Post by ryanclancy000 on 2011-07-30
@Allsixcolours

After looking through that thread, I am still having some issues figuring out what to do. I am fairly new at Ubuntu. Could you point my to the right post?

~Ryan

---

### Post by Allsixcolours on 2011-07-30
> **unagimiyagi said:**
> This is what I see.  It's in a file called Readme.md
I clicked on it and got what's below.

Xorg Multitouch Trackpad Driver
* Install the Debian package
* Configure xorg.conf
* Restart X

When I am saying that I (and likely other newbies) do not understand how to install this, is that I would like more info about each of these three steps.

In case you are interested in the points that a newbie used to the windows world would find unclear, it's:

Where is the debian package?  I assume that it's the binary for Ubuntu that I installed already from the ftp site dated April 28, 2011.

How do I configure xorg.conf?  Do I search for it somewhere in my file system and then add some lines to it?

I assume I restart X (I think that's the windowing system name in Ubuntu) by rebooting the computer?


Here is some additional detail for total newbies that I added to another post made earlier from Helios (thanks, Helios!)


If you have ubuntu, go to this link and download the file that applies to your version of linux that you are running:

[http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/](http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/)

I grabbed this one:  
[xserver-xorg-input-mtrack_0.1.1_natty_i386.deb]("http://www.dev.fatalmachine.org/packages/xf86-input-mtrack/ubuntu/xserver-xorg-input-mtrack_0.1.1_natty_i386.deb")  because I have Ubuntu 11.04 natty, the 32-bit version.

double click on this and Ubuntu software center will open.  Install it by following the onscreen directions. FYI: You do not need to download the tar file and extract it, compile it with "make install" or anything like that. 
If the right .deb is not in the link to the ftp site above, you'll have to compile this yourself before proceeding to any further steps.  No directions are being included for that.

OK, now you've just installed the new driver, but it's not activated yet.

To do that, you need to find and edit a file called xorg.conf.

The place (path) where this file is located on your computer is: /etc/X11/xorg.conf

You need to open this file.  If you use Nautilus, the windows explorer-type graphical file browser, you can navigate to and open this file.
Or you can use nano or vim or gedit (all text editors) to open this file.  To open this file, you need to become the superuser with the command sudo.
So, to use the built-in text editor to modify xorg.conf, type in the following at the command line (open a terminal window):
     
     ```

     sudo gedit /etc/X11/xorg.conf 

``` Type in the following bit of code at the end of the file
```

Section "InputClass"
        MatchIsTouchpad "on"
        Identifier "Touchpads"
        Driver "mtrack"
EndSection


```When you are done, your xorg.conf should look like this:

```

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
        MatchIsTouchpad "on"
        Identifier "Touchpads"
        Driver "mtrack"
EndSection




```Bookmark this page and Reboot your computer. (yes, you must do this or the new driver won't work).  If you don't wish to reboot, you can just restart the X windowing system if you know how to do that.

To tweak the options for the driver (sensitivity, pressure sensing, tap  to click enable/disable, thumb width, etc) follow the list of options in  the configuration section of the readme here:

[https://github.com/BlueDragonX/xf86-...ster/README.md]("https://github.com/BlueDragonX/xf86-input-mtrack/blob/master/README.md")

You insert the options you want to tweak in your xorg.conf file in between "Driver "mtrack"" and "EndSection"


Thanks for the great program!

That is a pretty good outline, I think. I'm pretty new to it myself, you'll get used to it pretty quickly. Feel free to ask questions about all that, but it is essentially all the steps you need to get it working. You wont need to make specific options in order for the dragging to work, that works by itself just by installing the driver.

---

### Post by ryanclancy000 on 2011-07-30
@Allsixcolours

Thank you very much, this is exactly what i was looking for

---

### Post by Allsixcolours on 2011-07-30
not a problem, I was very frustrated with it when I first switched. I'm assuming your thanks means you got it installed, but if you haven't, don't hesitate to ask for more help. You might want to look into customization, too, you can do some pretty cool things and almost get all of the functionality back from what you had in OS X. There are a few examples of setups people have in that thread that you could experiment with. I'd give you some tips, but I'm just figuring it out myself. Glad I could help, and welcome to the forums.

---

