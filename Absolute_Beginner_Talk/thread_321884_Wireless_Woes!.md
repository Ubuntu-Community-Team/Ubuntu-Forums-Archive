---
title: "Wireless Woes!"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Vyper06 on 2006-12-19
I just converted to ubuntu today (wahey!), good install, everything works fine but i have a big prblem in that I only connect to the internet through wireless, to my belkin router, as the computer is in a different room to the telephone socket. I have set up the IP adress, and have no WEP key, but even though i activated the connection i cannot get on the internet. 
Pinging results were fine, 0% package loss, however when i look arund 60000 packets have been sent yet none recieved. I have a RaLink usb device which came with the Philips computer, which needs to connect to a Belkiin router. Any help would be much appreciated. Thankyou!

---

### Post by Kobalt on 2006-12-19
You should search the forum with the exact model name of your usb wifi device, to learn how to get it working on Ubuntu...

---

### Post by Vyper06 on 2006-12-19
well i should have checked but the thing is the card seems to work it is recognised and sends 'packets' thanks newy

---

### Post by Kobalt on 2006-12-19
Do you have the Wifi level in the connection properties of the Gnome panel  (top right corner of the  screen) ?

---

### Post by CoolHand on 2006-12-19
You really haven't given us enough information to help.  From your post it sounds like you are running with a static IP.  Is there a reason you don't run DHCP on your router?  Since you set the IP static, did you also set up your nameservers?  Check /etc/resolv.conf to see if it is in there.  Also do you have default route (gateway) set?  Use the route command to check for the address of your router.  Also you say you are pinging that is why I assume you are associated with your AP but have you run iwconfig to verify that you are associated with your wireless router?  Some of these answers and more information in your post would probably help.

---

### Post by Vyper06 on 2006-12-19
woah thats a lot of info needed :p but ill see, as for the wifi bar in the corner no i dont have it,  just the clock. i will try to find these answers tomoro as i am on my winddows laptop curently.   and it is half 10pm here in uk. Thanks anyway i will be sure to check this information...and i thought ubuntu was sposed to be easy to use:p

---

