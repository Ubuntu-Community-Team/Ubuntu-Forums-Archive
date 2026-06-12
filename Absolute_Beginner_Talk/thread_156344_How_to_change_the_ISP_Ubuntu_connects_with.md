---
title: "How to change the ISP Ubuntu connects with?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by ntu on 2006-04-06
Greetings.

I have changed my dialup ISP in Windows 98se. Now, how to do this change in Ubuntu 5.04?

Advice appreciated.

---

### Post by lupine_nickt on 2006-04-06
You need to modify your PPP (point-to-point protocol) settings. In 5.10, I know, this can be done via. the Network Tools (binary: network-admin) utility... that should be present on 5.04. Assuming it is, try loading it up (It's in Settings->Network Tools for me), selecting "Modem Configuration", hit "Properties", change phone number, username and password... and you're done.

If it's not present, then you'll need to edit your ppp config files, which - IIRC - are to be found in /etc/ppp/peers

I've been on BB so long, though, that my memory on how to do it is a bit rusty. Google should give you some info, though...

xF,

...Nick

---

### Post by ntu on 2006-04-06
Thanks for your informative reply Nick.

I have found the network-admin in the GUI and opened Network Settings.

Now, you say in Properties to change phone no, uname and pw. Is that all?... No DNS sever 'numbers' or Hosts IP Addresses or Aliases?

Grateful for your help, no matter how rusty :)

---

### Post by lupine_nickt on 2006-04-06
Generally speaking, it'll pull all that extra info through the PPP link when it first starts up. I've certainly never needed to add it.

The last time I set up a PPP link, it was using my mobile phone as the modem. Even that was a year ago. So it is poretty rusty, yes :). 

Glad I could help.

xF,

...Nick

---

### Post by ntu on 2006-04-07
Thanks Nick. Online with Ubuntu machine and new ISP now :)

I remembered a very helpful post:

For those  who are looking to change ISP I used the last part - see below - of the excellent first post on this thread: [http://www.ubuntuforums.org/showthread.php?t=37465&highlight=536ep](http://www.ubuntuforums.org/showthread.php?t=37465&highlight=536ep) (Many thanks Zerksis. I wouldn't have got online in the first place - some months ago - without this post).


 1.) Right click on the top toolbar, (or the bottom toolbar if you prefer the modem icon à la Windows) & left click "+ Add toPanel..."

2.) Scroll down to a red telephone icon, double click it.
The icon will now appear on the top toolbar. 

3.) Right click on the toolbar/panel icon, & left click "Properties" in the drop down menu. Enter your user password.

4.) Check the "This device is configured" box, - now fill in
Phone number (ISP dial-in No.)
Dial prefix can be left blank
Your ISP dial-in Username
Your ISP dial-in Password

5.) On the Modem tab, in Modem port: type /dev/536ep0 
(don't even think about Autodetect!) and that last character above is a zero.
Under "Volume" select Medium, from the drop down menu, if you want to listen to the modem dialing out.

6.) Under the Options tab make sure that the "Set modem as default route to internet" is ticked.

Click on OK

Check that the modem phone line is connected - right click on the telephone icon, click Activate, enter PW.

---

