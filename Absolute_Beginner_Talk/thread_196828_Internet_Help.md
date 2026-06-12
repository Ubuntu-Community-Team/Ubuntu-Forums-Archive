---
title: "Internet Help"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-06-14
I ran Ubuntu 6.06 live cd but the internet was not working....I have cable modem what do I do to get internet working?

---

### Post by David_T on 2006-06-14
First, go to System > Administration > Networking.
Highlight Ethernet Connection and go to properties, then make
sure the box is checked that says "enable this connection" and make
sure the configuration is DHCP.  Click OK on properties, then click Activate
on the previous box.  That should work.

---

### Post by jasrog on 2006-06-14
That did not work please help someone....

---

### Post by David_T on 2006-06-14
OK.  
What happens when you click activate for the Ethernet connection?  
Does it show up in that list as eth0?
When you right-click on the networking icon up by the time and go to properties, does it show you eth0 as an option in the drop-down menu?
When you open firefox to google.com, does the browser hang or does it immediately give you an error?

---

### Post by jasrog on 2006-06-14
immediately an error

---

### Post by jasrog on 2006-06-14
Cannot find server error....my connection works in windows....

---

### Post by drtvasudevan on 2006-06-15
try this:
disable ipv6.
open firefox. type about:config in the url box
type ipv6 in the filter
double click on the first line.
the value should toggle from false to true.
close browser.
restart firefox.

tv

---

