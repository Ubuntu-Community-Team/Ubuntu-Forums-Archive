---
title: "Help Install Nvidia 6150"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Rainier on 2007-02-20
Good Morning, I have reach a level of :confused: .  I have tried several methods to install a driver for a GeForce 6150 Driver on my Compaq Presario V6030US Laptop.  I've tried using the instructions for GLX but all I get is a black screen of death.  I've tried the Legacy Driver and all I come up with after start-up is a black screen with Text prompt.

Please could someone help me correctly install a Nvidia GeForce 6150 Driver?

---

### Post by Bachstelze on 2007-02-20
Which Ubuntu are you using ? Are you sure you followed the instructions from the Wiki czrefully ?

---

### Post by arochester on 2007-02-20
You may have fallen between two problems. 

There has been a recent kernel update and this has given many people problems. The new kernel and the X-Server need to be configured together first. There are various ways of doing this, but one of the simplest, is to input at the prompt:> sudo dpkg-reconfigure xserver-xorg This will start a text-based wizard. Answer the questions as best you can and if you don't know the answer to any then go with the default suggested answer. If at first you don't succeed, in restarting the GUI, then try again and specify VESA.

Then when the GUI is up and running you need to install the Nvidia Driver. One simple way is to use the script "Envy" which is at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) This checks what card is installed and downloads and installs the correct driver. It appears that it does not work for 100% of people - but give it a try.

---

### Post by Rainier on 2007-02-20
I running Edgy 6.10  AMD64 with a kernel 2.6.17-11 generic.  I've enable linux-restrcted-modules; added the restricted repositories.  I have followed Binary Driver How To Nvidia Community Ubuntu Documentations   I've even tried the above link.   Which Nvidia Driver should I use for Geforce 6150 the Nvidia-GLX or Nvidia-Legacy?  I've tried the 1-2-3 method.  I'm at my ends with this.  When I was using SUSE this issue was resolved during the installation.  I guess; I need a walk through with good instructions to install the driver.  Anyone that has install a GeForce 6150?  Help.    Thank You!

---

### Post by brandoncolorado on 2007-02-20
Hey man!

Tricky stuff.  I am running the GeForce Go 6100.

Envy script worked like a charm for me.  Maybe it will work for you too.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Let me know if you have any questions about how to use it, it worked great.

---

### Post by brandoncolorado on 2007-02-20
By the way, you can run envy from the text prompt, so even if you have a driver problem, potentially you can fix it.

---

### Post by Rainier on 2007-02-20
I install Envy and ran it.  This is what happen:  I run the auto config to set-up the driver.  However before running Envy a message came up saying driver was not supported would you like to continue with the installation.  While I ran it and the result was the x server was not config correctly at the end on a reboot a funny  message appear saying your x server is not correct would you like to review yes or no.   Should I run Envy in a manually installation.  If so what would be my config settings?

---

### Post by Rainier on 2007-02-21
I would like to say Thank you for your help and support...However after long consideration I have decide to re-install SuSe.  SuSe right out of the box it install my Nvidia Driver and acpi.  I really like Ubuntu API is; but I feel Ubuntu is still very rough around the edges for laptop use.  If the developers of Ubuntu are listening please focus on ACPI and Autodetect Graphic card detection.  Once again Thank You for your support and time.   Sincerely Rainier

---

