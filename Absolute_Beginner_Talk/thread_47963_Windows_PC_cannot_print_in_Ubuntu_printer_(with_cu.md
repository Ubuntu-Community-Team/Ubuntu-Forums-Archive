---
title: "Windows PC cannot print in Ubuntu printer (with cups)"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by camara on 2005-07-10
Hi all,

I'm setting up my home network. There is something wrong with my cups config I'm sure...
My samba is up and running wonderfully, but there's no sign of my deskjet printer... Any hints?

Thanks a lot (by the way, this community is a great excuse to turn to Ubuntu! ;)

---

### Post by ubuntu_demon on 2005-07-13
I've never done network printing. But since no one has answered I give it a shot.

I think you need to config the printer in linux first ( I know that part)

Go here :
[http://www.linuxprinting.org](http://www.linuxprinting.org)

This will recommend what driver to use. Do 
$ apt-cache search drivername

then install the driver (For HP printers this is most likely the driver hpijs)

$sudo apt-get install driver

after this just go to system->administration->printing and add your printer (select the recommended driver)

So tell me if you can print in Ubuntu. If you can we'll look into samba / cups.

---

### Post by skirkpatrick on 2005-07-13
Are the Windows machines XP or 98?  I have found that 98's response to my Ubuntu printer is better using Samba and my XP's response is better using Cups via IPP.

---

### Post by Mr. Electric Wizard on 2005-07-13
Here is what I did.
On my XP box, I simply right clicked the printer, and shared it.
Then in Ubuntu, I went to Printing (under Administration I believe), then clicked New Printer.
When the next dialog came up, it asked me for the host name, share, etc.
After this was all set up, Ubuntu asked me what type of printer it was, etc.
That was basically it.
The whole process took approx. 2 minutes.

---

### Post by Mr. Electric Wizard on 2005-07-13
Wait, am I backwards on this?
Is your printer hooked up to the Windows box, or the Ubuntu box?

---

### Post by camara on 2005-07-13
Well. Thanks for the suggestions, but I guess I should have described the situation better:
1 -  I have the printer already up and running in Ubuntu. It was easy... :D
2 - I am using XP on the laptop. 
3 - I can see everything from my laptop, but the "Printers and Faxes" folder is plain empty...
4 - In cups, I tried to share it but nothing... There's where I just get lost!...

Cheers
   Francisco

---

### Post by skirkpatrick on 2005-07-13
Ok, lets see if I remember everything I did:

1) Edit /etc/cups/cupsd.conf.

2) Search for "Port 631".  It should be uncommented (no "#" at the beginning of the line).  This means Cups will listen on port 631.

3) This one is important.  Search for "<Location />".  You will need to allow your network address to access Cups.  My network addresses range from 192.168.0.1 to 192.168.0.255 so my "<Location />" section looks like this:
> 
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>


4) Save the file and restart Cups:
> 
sudo /etc/init.d/cupsys restart

Cups should now accept all requests in your subnet.


In XP, when you add a printer, follow these steps:

1) Select "A network printer..." instead of "Local printer...".

2) Click the radio button for "Connect to a printer on the Internet...".

3) In the URL field, enter "http://serverip:631/printers/printername" where "serverip" is the IP of your Ubuntu machine and "printername" is the Cups name for the printer.  If you have DNS setup for your network (unlikely) or you have Samba working on your Ubuntu machine so your XP machines can access it by name, you can use the Ubuntu machine's name instead of it's IP address.

4) You will probably have to tell XP to load the printer driver from its CD as it will not be able to download it from your Ubuntu machine.


Let me know how this goes  :grin:

---

### Post by camara on 2005-07-15
Well. I did the changes to cupsd.conf. Then the cupsys restart gives:
# /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 98!


It seems not to have restarted... any hint?

Thanks

---

### Post by skirkpatrick on 2005-07-16
you can try "/etc/init.d/cupsys stop" then "/etc/init.d/cupsys start" and see if that helps.

---

