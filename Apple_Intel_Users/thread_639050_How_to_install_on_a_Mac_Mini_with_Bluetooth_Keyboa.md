---
title: "How to install on a Mac Mini with Bluetooth Keyboard &amp; Mouse ???"
date: 2007-12-12
forum: Apple Intel Users
---

### Post by membrana on 2007-12-12
hi,
I want to install Ubuntu 7.04 on my Mac Mini Intel. But i **only** have the Apple wireless keyboard and the Apple wireless Mighty Mouse ( both work via bluetooth ).
I made the BOOTCAMP partition of 20GB, then i inserted the liveDVD, and holded the ALT-Option key. I got this start up screen to choose between OSX and "Windows" ( that is how OSX calls Ubuntu ), and then the thing starts to boot OK.
I get the screen where i have to choose to 'start or install', 'install a command line', etc.
I choose the first one, to boot into the liveDVD and install Ubuntu, but when it loads up, my Keyboard and Mouse are dead ( and they have new batteries! :) )

So... my guess, and from which i've read in the forums, is that i cannot install Ubuntu with my current wireless keyboard and mouse... 

Is there some kind of workaround?

I've read something regarding the 'alternate-command-line-cd-install-thingie' but since i really don't understand much, it didn't make much sense...
Also, there is this thing 'http://reconstructor.aperantis.com/' which is supposed to build a custom Ubuntu install... could this be used to build a liveDVD that has the bluetooth compatibility i'm looking for?

Thanks to all!!!

[I]Mac Mini Intel 
1.83 GHz Intel Core Duo
1 GB 667 MHz DDR2 SDRAM
Mac OS X 10.5.1[/I]

---

### Post by tgalati4 on 2007-12-12
Bum a USB keyboard from a neighbor.

---

### Post by membrana on 2007-12-12
well... thats another no-no. here in Argentina, we still have the PS/2 ports as a default for mouses and keyboards... and very very very few people have Apple at all.

pfft... crappy 3rd world... :)

---

### Post by cyberdork33 on 2007-12-12
yea you are going to need a usb keyboard as the wireless ones will not connect by themselves.

---

### Post by nicfagn on 2007-12-13
At the cd menu press F6 to edit the kernel parameters and add the **single** parameter. 
This will make the system start in single user mode, that is a system with minimum functionality (bluetooth service disabled) and using a command line shell as user interface.
Your keyboard and mouse should work since they are supported directly by the kernel in HID mode.
Now you have to disable the bluetooth service issuing the following command:
```
upate-rc.d -f bluetooth remove
```
Then you can continue the normal startup sequence exiting the single user shell, with:
```
exit
```

Bye

---

### Post by membrana on 2007-12-13
wait.. let me get this straight, **nicfagn**.
you are telling me to enter a minimum mode, with bluetooth disabled, and to disable bluetooth service?
and that will make my bluetooth peripherials work?

thats crazy! but when i get home i'll try it right away...
and that will work forever, right?

thank you very much!!!

---

### Post by cyberdork33 on 2007-12-13
yea the first command prevents the bluetooth service from starting automatically.

This is an interesting way to go about things, but if it will work...

---

### Post by membrana on 2007-12-13
well... it worked!
i was able to install Ubuntu flawlessly.
but then... when i rebooted, the bluetooth mouse and keyboard weren't responding again.
should i do the same again?
if so, how do i get to the single user mode now?

if i can't do that again, could i boot up from the liveCD as the first time, and from there set the bluetooth right on the installed OS?

thanks!!!

---

### Post by nicfagn on 2007-12-14
You have to disable bluetooth again choosing recovery mode at the grub menu.

Glad it worked, I've been using this trick since a while :)

You probably will have to repeat this procedure if you install an update to the bluetooth service (eg. via update-manager), since usually this re-enable it.
The best would be to pair your keyboard and mouse with your Mac, but I didn't find a suitable way to do that with my system alone. 
I had to enable the remote desktop on Ubuntu and used another Mac (near mine) to complete the pairing procedure trough VNC.

---

