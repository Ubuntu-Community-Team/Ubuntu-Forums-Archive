---
title: "usb port #"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-03-06
How can I tell what my usb port # is? which would be top and which would be bottom? Thanks Dan

---

### Post by {BzF}~JOKesTER on 2008-03-06
If I'm Getting What Your Asking

Plug In Your Keyboard In To Whatever Port You'd Like To Find Is Which.

And In The Terminal Type lsusb

Than Look For Your Keyboard On The List {I.E. Logitech USB Keyboard}

Hope This Helps.

---

### Post by maineman2 on 2008-03-06
Hi I need to find out which usb port my printer is plugged into. isusb command not found. Thanks Dan

---

### Post by {BzF}~JOKesTER on 2008-03-06
Ok So Type lsusb In The Console

And Find Out Which Port Number It Is Example...


root@THE-ILLUSION:/home/jokester# lsusb         #Here I Type lsusb
Bus 003 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi  #Here Is My Netgear Wireless Card
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub #My Keyboard
Bus 002 Device 005: ID 03f0:020c Hewlett-Packard Multimedia Keyboard #My Keyboards USB Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button) # My Mouse
Bus 001 Device 001: ID 0000:0000  


Ok So Find One That Looks Like It Whould Be The Printer Like Maybe:

Bus 003 Device 002: ID 0846:6a00 HP Printer Model 6372

Or Something Like That - Depending On What Printer You Have..

Hope This Helps

---

### Post by maineman2 on 2008-03-06
I type into the terminal Isusb command not found Dan

---

### Post by {BzF}~JOKesTER on 2008-03-06
> **maineman2 said:**
> Hi I need to find out which usb port my printer is plugged into. isusb command not found. Thanks Dan


Its Not isusb

It's LSUSB {Without The Caps Though}

Just Copy And Paste This

lsusb

---

### Post by maineman2 on 2008-03-06
That did work. I found out my usb port #. I installed QInk last night and it cant detect my printer even while I was printing. The program says try chmod 666/dev/usblpx X being my usb port # In the terminal. I tried that and it did not detect my printer. Any help would be appreciated Dan

---

### Post by {BzF}~JOKesTER on 2008-03-06
i whould reccomend re-installing Qink Using A Purge Command

apt-get remove qink --purge

I Hope This Works Out For You - Keep Me Updated Thanks

:):):)

---

### Post by maineman2 on 2008-03-06
medan@medan-laptop:~$ apt-get remove qink --purge
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
medan@medan-laptop:~$ 

Thanks Dan

---

### Post by {BzF}~JOKesTER on 2008-03-06
sorry use sudo:

sudo apt-get remove qink --purge

And Type Your Root Password

And Unninstall

:popcorn:

---

### Post by maineman2 on 2008-03-06
Thanks for your help. I removed and reinstalled with synaptic package manager and nothing. I removed with the code you gave me and then reinstalled. And it still wont detect my printer Thanks Dan

---

### Post by Albinodrew on 2008-05-07
> **maineman2 said:**
> That did work. I found out my usb port #. I installed QInk last night and it cant detect my printer even while I was printing. The program says try chmod 666/dev/usblpx X being my usb port # In the terminal. I tried that and it did not detect my printer. Any help would be appreciated Dan

I've just try that command, and it work just fine for me, I believe you might have forgot to put a space between 666 and /dev/usblpx.
mine is /dev/usblp0

So for those who read this post and are new to linux, to change permission you must be root (administrator) so after opening a terminal, the command should be enter like this

sudo chmod 666 /dev/usblp0

then when ask, enter your password

Et Voila.

Hope this help everyone.

---

