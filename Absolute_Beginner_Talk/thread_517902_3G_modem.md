---
title: "3G modem"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Ginoxy on 2007-08-05
Hello i am trying to install a 3G modem to my Ubuntu but each time i got this error 

wvdial:
–> WvDial: Internet dialer version 1.56
–> Cannot get information for serial port.
–> Initializing modem.
–> Sending: ATZ
–> Sending: ATQ0
–> Re-Sending: ATZ
–> Modem not responding.


Any idea how to fix it ?

Thanks.

---

### Post by apswartz on 2007-08-05
See if one of these articles will help you...
[http://www.tectonic.co.za/view.php?src=rss&id=1596](http://www.tectonic.co.za/view.php?src=rss&id=1596)
[http://www.marotori.com/blog/?p=17](http://www.marotori.com/blog/?p=17)

---

### Post by feistyfirsttimer on 2007-08-05
>Hello i am trying to install a 3G modem to my Ubuntu but each time i got this error
>
>wvdial:
>&#8211;> WvDial: Internet dialer version 1.56
>&#8211;> Cannot get information for serial port.
>&#8211;> Initializing modem.
>&#8211;> Sending: ATZ
>&#8211;> Sending: ATQ0
>&#8211;> Re-Sending: ATZ
>&#8211;> Modem not responding.
>
>
>Any idea how to fix it ?

I use wvdial to use my mobile phone as a modem.  The USB/Serial lead I use to connect the phone to my pc is a bit dodgy, and sometimes I get that message.  It means the pc can't make contact with the modem.  In my case it's cos the dodgy lead's disconnected, and I have to plug it back in.

Alternatively, are you sure you set wvdial to listen to the correct port (in /etc/wvdial.conf)?

---

### Post by Ginoxy on 2007-08-07
what do you mean ?

the wvdial.conf is not in the etc its in diff. folder

---

### Post by apswartz on 2007-08-07
Try looking here...
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

---

