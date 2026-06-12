---
title: "No Network connection......tried everything!!!"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by skopas on 2006-02-08
Hey gang,   
         Need some assistance here.  I installed ubuntu as a virtual OS.  Everything is fine, only that i cant get online.  I tried to ping a few names not ip's adresse's  and get a window cant find whatever!!  Now, I run a ipconfig on my legit os windows xp and it shows my ip address ,gateway and so on.  Down below it also show's the virtual ip address assigned to ubuntu.  My networked is bridged over,,,if that makes sense. 

I go over to ubuntu/preferences/network,  and checked to see if anything is out of the ordinary..and I cant really tell.  :???:  I have a ETHO there which i believe  is the virtual nic and i configure it with addresse from ipconfig info.....still nothing...no connection.    sorrry..im new to the linux world

But, im not  giving up:KS      ANY suggestions, would be more than helpful.

BTW..im using a Motorola sb5100 surfboard modem.  No router.  Cable/modem/pc.;) ;)

---

### Post by davmac on 2006-02-08
In Ubuntu, if you open up a terminal and type "ifstatus eth0" and "ifconfig eth0" what output do you get?

Dave Mac

---

### Post by TrendyDark on 2006-02-08
if you get a negative-looking response on those tests you can always try "sudo ifup eth0" to see if that will configure your network interface, if not, goto **System --> Administration --> Networking**

---

### Post by kenweill on 2006-02-08
Assign a static ip address for Ubuntu. Use the same subnet mask in your ubuntu and windows. It works for me. It could work for you too.

Example:
If your Windows XP have an ip address of 192.168.0.1 and subnetmask of 255.255.255.0 ....
Then you have to assign a static address of your ubuntu with something like 192.168.0.x(any number other than 1 and 255), and the same subnet mask with your windows station.

---

### Post by skopas on 2006-02-08
Thanks everyone for value input.  I'll try, and post the results.:) :)

---

### Post by skopas on 2006-02-09
WOW!....still having problems...:confused: 

OK, I ran sudo ifup eth0  and it stated already configured.

I tried to reassign a new IP address.....to no avail.

I ran ifstatus eth0........that said BASH!...no valid command.

I ran ifconfig eth0......that pulled a nice window with all sorts of info, but since I'm a windows user, the linux window looked a little greek to me.:confused:  Im not sure what to look for....sorry.   I'm really trying  here...;) 

Any more ideas.......???

---

### Post by davmac on 2006-02-09
Try running the "ifconfig eth0" command and then copy/paste the message text back into this thread. It should give people something to go on.

Regards,

Dave Mac

---

### Post by skopas on 2006-02-09
OK, Dave Mac
                   Here goes nothing.  I couldnt copy/paste from the terminal, because im running a virtual machine.  I did a screenshot, and just hosted it.
Thanks in advance for helping.:) :) 



[[IMG]http://img339.imageshack.us/img339/8371/untitled4pu1.png[/IMG]]("[URL=http://imageshack.us)"][[IMG]http://img339.imageshack.us/img339/8371/untitled4pu1.png[/IMG]](http://imageshack.us)[/URL]

---

### Post by GopherPrime on 2007-09-26
I had this same problem but to fix it was strangely simple. When you login, click on the network icon near the top right and select wired network. I have to do this every time I login but it seems to work fine after that.

---

