---
title: "Firefox java and Logmein"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-06-21
I can use logmein from XP, but not from Ubuntu (it used to work).  Here is the message I receive after I login, click on the remote computer, then, click Go on the remote control aplet:

java.security.accesscontrolexception: access denied (java.net.socketpermission mycomputername-ziglgoaxlu.app12.logmein.com:443 connect,resolve)

What does this mean, how can I fix it?

Thanks in advance for any help you can offer.

Caruso

---

### Post by santy_kushwaha on 2007-06-21
ya man 

i use logmein but it don't work for me in linux i fing that it is bcoz it tried to go throught HTTP and java don't get the permission to enter from there

---

### Post by carusoswi on 2007-06-21
> **santy_kushwaha said:**
> ya man 

i use logmein but it don't work for me in linux i fing that it is bcoz it tried to go throught HTTP and java don't get the permission to enter from there

Exactly.
So, what to do.  I want to use it in Ubuntu.
Caruso

---

### Post by lazyart on 2007-06-21
Try Hamachi (owned by logmein), create a virtual network and vnc/remote desktop to it.

---

### Post by paulstanding on 2007-06-26
> **carusoswi said:**
> I can use logmein from XP, but not from Ubuntu (it used to work).  Here is the message I receive after I login, click on the remote computer, then, click Go on the remote control aplet:

java.security.accesscontrolexception: access denied (java.net.socketpermission mycomputername-ziglgoaxlu.app12.logmein.com:443 connect,resolve)

What does this mean, how can I fix it?

Thanks in advance for any help you can offer.

Caruso

I have exactly the same problem. It used to work for me too - using Dapper. I now use Fiesty. Ther must be an answer. I know about hamachi and for some purposes it is better, but I also want to use LogMeIn.

---

### Post by 1oki on 2007-06-26
no no no no virtual network, no VNC, No remote desktop sessions... It does work with just java and firefox... I know this because I had it working under fistey. Don't ask me how, I just did. Someone at my office accidentally deleted my initd and i had to reinstall the system... Now when I try to use logmein it wont work. I did every step that I took in the previous installation of java (automatix2 install JRE for Firefox) and it wont work... 

So I tried it through apt:

sudo apt-get install sun-java6-plugin sun-java6-fonts


go to logmein and now its says "Loading Java Applet Failed..." and there is a little box in the upper left hand corner of the logmein window with an "X" through it. When I right click on the logmein window (java frame) I get the java options... so i know it is working. Maybe a reboot....


also, when i went to Suns installation check 
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)
it says:
> Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer.  
Clearly its not... I am thinking that java is throwing a wrong code somewhere causing JRE apps to think it wont run.

---

### Post by 1oki on 2007-06-26
I figured out what it is... Logmein does not like java 6... 
here are the steps i took to get it working..

Close all firefox sessions.

Go into synaptic and do a search for java... select "completely remove" java common (and its ok to 
remove all the other things that it wants to automatically) 

before you click apply, do another search for java 5

select sun-java5-fonts, and sun-java5-plugin there will be a bunch of prerequisites that are needed for install (jre, etc.)

Click apply..... let it install.

open firefox, sign into logmein... BAM, it works.

---

### Post by carusoswi on 2007-06-30
Thank you, thank you!  I didn't achieve the switch back to java5 exactly as you described, but, however I did it, I managed to uninstall java6 and install java5 with the appropriate pluggins.  All is sweet with the world, now.
Thanks.

Caruso

> **1oki said:**
> I figured out what it is... Logmein does not like java 6... 
here are the steps i took to get it working..

Close all firefox sessions.

Go into synaptic and do a search for java... select "completely remove" java common (and its ok to 
remove all the other things that it wants to automatically) 

before you click apply, do another search for java 5

select sun-java5-fonts, and sun-java5-plugin there will be a bunch of prerequisites that are needed for install (jre, etc.)

Click apply..... let it install.

open firefox, sign into logmein... BAM, it works.

---

### Post by augustosamame on 2007-12-05
I have been going crazy with a different issue for days. I just couldn't open the [www.logmein.com](www.logmein.com) page (or secure.logmein.com for that matter). I only got a "Connection Reset" error.

I found the answer, of all places, on a MAC Safari forum.

[http://discussions.apple.com/thread.jspa?messageID=6017681](http://discussions.apple.com/thread.jspa?messageID=6017681)

The problem seems to be Gutsy's default MTU network setting, which is 1500. You will have to change this to 1472, or you won't be able to access the secure logmein page. The MTU value determines the max packet size in TCP/IP networks.

The simplest (and temporary until the next reboot) way to change this value is to enter the following command in terminal (this assumes you use eth0 to connect to the Internet, otherwise edit accordingly)

"sudo ifconfig eth0 mtu 1472"

If you can access the logmein page after changing this setting, then you can attempt (it's a bit complex depending on user/configuration) to make the change permanent.

This method worked for me:

"sudo gedit /etc/network/interfaces"

add the following line to the eth0 configuration info

"MTU 1472"

reboot or restart network services using

"sudo /etc/init.d/networking restart"


I use a static IP address. I have heard of this simple method not working when using DHCP so you could do some research here

[http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size](http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size)

to see which method will work for you.

Hope this helps.

---

