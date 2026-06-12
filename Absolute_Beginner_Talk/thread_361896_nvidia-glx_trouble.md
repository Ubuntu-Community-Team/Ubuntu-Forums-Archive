---
title: "nvidia-glx trouble"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Bayushi Red on 2007-02-14
I have an Nvidia Geforce4 TI4200.  As far as I can tell from synaptic, nvidia-glx is properly installed, yet when I go to the terminal, this is what I get:

bayushired@bayushired-desktop:~$ sudo nvidia-glx-config enable
Password:
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

What's wrong?

Edit:
nvidia-kernel-common also appears to be properly installed.

---

### Post by chuckyp on 2007-02-15
You also need the linux-restricted-modules-2.6*****  package.  Replace 2.6**** with whatever kernel you are currently running.   You can find out by using uname -r in terminal.

---

### Post by Bayushi Red on 2007-02-15
My kernel is v 2.6.17.11 , and I've installed everything that matches that version name.  I get the same result when I try to set up my video card drivers.

---

### Post by Patrick K on 2007-02-15
Have you been to the Multimedia & Video forum? In the top section are several "how to's" on installing nvidia drivers. I used the Envy script and had them installed and fully functional in a few minutes.

---

### Post by FyreBrand on 2007-02-15
What version of Ubuntu are you using?  By the kernel version I'm guessing Edgy.  If you haven't read this guide I would highly recommend it.  It's great and leads you step by step through the install process.  It also has a troubleshooting section.

I'm not too familiar with the Ti4xxx series but there are special instructions there for Geforce 4 420/440 cards.

Here is the link to the HowTo (by tseliot): [**Latest Nvidia Edgy**]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy").

Good luck.

---

### Post by Tahir on 2007-03-04
Hello Bayushi Red,

I had your problems too.  All I did to sort it out was download envy from this page:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

here is the direct link:

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

save it to your desktop.  double click it and install it.  Then open a command line and type "sudo envy".

Select the first option to remove the drivers. (IF THE SCREEN GOES BLANK THEN PRESS ALT +F1). Once you do that then select the second option to install the driver.  It may ask you to enter your ubuntu CD.  It should really install flawlessly.  Mad props to the author of the script.

-Tahir

---

### Post by Repent on 2007-03-04
This is a really easy way to install the proper drivers and it to uses Envy it just does it in a easier way.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by Tahir on 2007-03-05
> **Repent said:**
> This is a really easy way to install the proper drivers and it to uses Envy it just does it in a easier way.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

But I am sure it also configures your driver settings too.  Because I installed the nvidia GPU myself once and the frame rate was very bad.  Once I uninstalled the driver using this script and then installed (the same) driver somehow the framerate was brilliant. BTW I have a nvidia geforce4 ti4200 graphics card.

---

