---
title: "Logging in as Admin"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by rosco99 on 2007-06-09
I have just installed Kubuntu v 6.10 as I understand this supports the BigPond USB Desk top modem. (Maxon BP-3).
I have been using Suse 10.2 but recently upgraded from Telstra ISDN to Wireless Next G, and have not been able to get it operational. In Quozl's article on the Maxon BP-3 he shows how to set it up in Kubuntu.
My problem is I can not get Admin privileges to insmod "usbserial.ko".
In Suse you set the Admin password during installation as well as user password. In Kubuntu I am only able to set my user Password and when I try to set su from Konsole I have to submit an unknown password.
Can someone please hold my hand through this please.
I am having to use Windows to access this Forum until I can operate the wireless modem from Kubuntu.

---

### Post by Catsworth on 2007-06-09
The password that you're being asked for when you're using su (or sudo, or gksu, or gksudo) is *your* password, the one that you logged in with.

If this doesn't work then you may need to ensure that your current user account is listed in sudoers (a quick forum search should get you instructions on doing that) - it should be by default, but for some reason I sometimes find that my account hasn't been added to that list when I do a clean install.

---

### Post by LollYouSuckZor on 2007-06-09
Type in the console.

```


sudo su


```

it will then ask for your password, enter it, and walla. ;]

---

### Post by rosco99 on 2007-06-09
> **LollYouSuckZor said:**
> Type in the console.
it will then ask for your password, enter it, and walla. ;]
Thank you,
That worked.
However,I am trying to do this-
insmod /lib/modules/2.6.18.2-34-default /kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280

I get an error "file not found"
I have also gone to the location of usbserial.ko and tried to open with insmod and get an error-Action not allowed.

Any ideas?

---

### Post by Catsworth on 2007-06-09
Sorry, don't even know what insmod does.

Did you try:

```


sudo insmod <yourfilenamehere>


```

?

---

### Post by rosco99 on 2007-06-09
> **Catsworth said:**
> Sorry, don't even know what insmod does.

Did you try:

```


sudo insmod <yourfilenamehere>


```

?
I am trying to do this 
ask the usbserial module to adopt the device, for example:

insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280
---
This is directly from an article on [http://quozl.linux.org.au/bp3-usb/](http://quozl.linux.org.au/bp3-usb/) ---
Which is illustrated to make the Maxon modem work on Kubuntu Edgy 6.10

I naively thought I could just follow the instructions and make it work.

---

### Post by steve.horsley on 2007-06-09
For a start, I woulud be inclined to do it all on one line, in case newlines are causing issues:
> insmod /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280

For a second, file not found is quite fundamental. It seems that you are not entering the text from the web site properly. Try copy/paste from the quote above. If that says file not found, you may have version mismatch problems - try this command:
> echo /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko
and see where the printed path differs from the path of the file you actually have.

---

### Post by rosco99 on 2007-06-11
Thank you, I have tried everything. Even went to file and copied location from the media line and still no good. The modem is not showing up in the lsusb -v as in Quozl's article. I had to add a USB pci card to this computer as the on board usb port died. I wonder if this is causing the problem.  I am going to try on my HTPC, which is the computer I want to use ultimately with linux. I was trying to get the modem working beforeworhing on the htpc.

---

