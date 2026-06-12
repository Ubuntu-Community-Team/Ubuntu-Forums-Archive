---
title: "bluetooth problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-23
i installed kdebluetooth .. i can connect my bluetooth adapter.. when i do search from my cell phone.. i can find it too but when i try to connect it. i cant.. i tried all kind of pin but .. without even trying both my cell and kdebluetooth says "unable to pair/connect"
what can i do to fix this ?

---

### Post by HunkieChan on 2007-03-23
anyone please ? btw.. when does the final version of feity fawn and beryl comes out ?

---

### Post by mbv93 on 2007-03-23
The Final Version of Feisty is coming on april... and i think beryl is stable :)

---

### Post by HunkieChan on 2007-03-23
whats the new feature in feisty ? do you know a link where the have all of em in brief

what about my problem ? :(

---

### Post by HunkieChan on 2007-03-23
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=howto+bluetooth](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=howto+bluetooth)

okay i follow his instruction .. BUT...



1. Install bluez-utils
2. Install kdebluetooth (gnome bluetooth is not as far developed as kde I think), libopenobex, qobex
3. Install konqueror
4. Check /etc/bluetooth/hcid.conf:
security should be user
pairing should be multi
**pin_helper should be /usr/bluez-pin**

i dont have that part in my file.. whats the problem ?

---

### Post by HunkieChan on 2007-03-23
can anyone please help me ? please ?

---

### Post by flangemonkey on 2007-04-05
my hciconf file 

backup yours and plonk this into your /etc/bluetooth directory

```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security user;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /usr/bluez-pin;
        # or you can use /usr/bin/pinwrapper;

        # D-Bus PIN helper
        #dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption (Security Mode 3)
        #auth enable;
        #encrypt enable;
}


```

hth

Phill

---

