---
title: "Configuring wireless network"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by pallukucchu on 2007-04-02
I am using intel wireless 3945ABG for a dell notebook.
The system is able to detect wireless and shows the connections.However, when i use automatic dhcp configuration, it says connection failed. I dont what dhcp means. 

I am able to configure wired connection with automatic dhcp.Is there any driver to be installed for this particular configuration.I used ubuntu edge efty edition.

:guitar: :confused:

---

### Post by ajmorris on 2007-04-02
DHCP is what your router uses to issue you an I.P address. There are linux drivers for that card 
here : [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) also have you tried typing from a shell ```
sudo dhclient
```?

But the drivers should not be needed, that card should work on edgy straight out of the box.

Try sudo dhclient first.

---

### Post by pallukucchu on 2007-04-03
I can go the site.
the install document is little bit complex.

It say download packages and install from terminal window. 
when i type 
$ make install
make: *** No rule to make target `compatible/iwlwifi.ko', needed by `install'.  Stop.
:guitar: :confused: :guitar: :confused:

---

