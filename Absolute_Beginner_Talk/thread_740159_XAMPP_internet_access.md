---
title: "XAMPP internet access"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-30
I followed this tutorial on XAMPP setup and I have it working just fine when I access /localhost/username:
[http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp")


What I don't see/understand is how to be able to access this from the internet.  How can I have a friend access this from his computer via the internet?

---

### Post by cozmicharlie on 2008-03-30
Good you got it set up and working.  Now though the only access you have is on your local network.  To set up so others can access outside of your local network you need to do a bit more.  It's not hard  and you have a couple options.  You can set up virtual hosts or get a DNS account.  The problem is most computers behind a router use dynamic IP address so you need a way to access your address and since it changes you need some way to point people to a permanent address.  There are a few methods to use - you can get a host name that points a url to your dynamic or static IP here [http://www.dyndns.com/services/](http://www.dyndns.com/services/) (it's free).  The site also has lots of good info to help.  You don't have to do it this way though.  You can set up virtual hosts also.  Best to start by doing some reading to find out what works best for you.  These tutorials should help point you in the right direction.  Don't worry, at first it seems daunting but it really isn't.  If you have trouble post back and we can help.  Also, since you are using XAMP make sure you have all the security set up properly otherwise you are very vulnerable.  The apache friends website shows you how.

These should help you get started
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)  (this is a good place to start)
[http://tldp.org/HOWTO/DNS-HOWTO-5.html](http://tldp.org/HOWTO/DNS-HOWTO-5.html)
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Good luck

---

### Post by BlizzofOZ on 2008-03-30
> **cozmicharlie said:**
> Good you got it set up and working.  Now though the only access you have is on your local network.  To set up so others can access outside of your local network you need to do a bit more.  It's not hard  and you have a couple options.  You can set up virtual hosts or get a DNS account.  The problem is most computers behind a router use dynamic IP address so you need a way to access your address and since it changes you need some way to point people to a permanent address.  There are a few methods to use - you can get a host name that points a url to your dynamic or static IP here [http://www.dyndns.com/services/](http://www.dyndns.com/services/) (it's free).  The site also has lots of good info to help.  You don't have to do it this way though.  You can set up virtual hosts also.  Best to start by doing some reading to find out what works best for you.  These tutorials should help point you in the right direction.  Don't worry, at first it seems daunting but it really isn't.  If you have trouble post back and we can help.  Also, since you are using XAMP make sure you have all the security set up properly otherwise you are very vulnerable.  The apache friends website shows you how.

These should help you get started
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)  (this is a good place to start)
[http://tldp.org/HOWTO/DNS-HOWTO-5.html](http://tldp.org/HOWTO/DNS-HOWTO-5.html)
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
[http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

Good luck

Thanks for the reply!

I've already signed up at dyndns and have a hostname... I did this for remote desktop with Putty and VNC.

I had posted another topic on this... more on the port forward side of things.
I'm not sure my roadblock is...

I did issue the security command in the link I provided... is there more that I should do?

---

### Post by cozmicharlie on 2008-03-30
Not sure why it is not working for you.  It was very simple for me.  I set up XAMP as per the instructions at Apache Friends and when I go to the url from DyDNS up comes XAMP sign in screen.  I type in my XAMP username and pw and I'm in.  This may seem silly and don't be offended but a number of times I simply forgot to start XAMP.  When you go to the url given by DyDNS what comes up?

This page also has a couple short tutorials specifically on DyDNS and XAMP [https://www.dyndns.com/support/kb/cat_web_server.html](https://www.dyndns.com/support/kb/cat_web_server.html) - it may help.

---

### Post by BlizzofOZ on 2008-03-31
> **cozmicharlie said:**
> Not sure why it is not working for you.  It was very simple for me.  I set up XAMP as per the instructions at Apache Friends and when I go to the url from DyDNS up comes XAMP sign in screen.  I type in my XAMP username and pw and I'm in.  This may seem silly and don't be offended but a number of times I simply forgot to start XAMP.  When you go to the url given by DyDNS what comes up?

This page also has a couple short tutorials specifically on DyDNS and XAMP [https://www.dyndns.com/support/kb/cat_web_server.html](https://www.dyndns.com/support/kb/cat_web_server.html) - it may help.

Not silly... I'm new to Linux, so not really silly.

But I did find my problem, which had to do with port forwarding.  I went to Apache Friends forum and found the needed setup file to change the port number.

So, I have it working!  Thanks for you time and help!

---

### Post by cozmicharlie on 2008-03-31
Glad to hear it

---

### Post by insub2 on 2008-04-01
> **BlizzofOZ said:**
> Not silly... I'm new to Linux, so not really silly.

But I did find my problem, which had to do with port forwarding.  I went to Apache Friends forum and found the needed setup file to change the port number.

So, I have it working!  Thanks for you time and help!


could you share the solution or give a link.

i'm running into the same thing.

thanks.

---

### Post by BlizzofOZ on 2008-04-01
> **insub2 said:**
> could you share the solution or give a link.

i'm running into the same thing.

thanks.

Check out this link to my question at Apache Friends:
[http://www.apachefriends.org/f/viewtopic.php?t=29109]("http://www.apachefriends.org/f/viewtopic.php?t=29109")

I had to change 2 conf files, changing the LISTEN command from port 80 to the new port.
Files:
/opt/lampp/etc/httpd.conf
/opt/lampp/lampp

Additionally, you need to add the new port in your router setup.  You setup the new port, to port forward to the server IP address.

---

### Post by insub2 on 2008-04-04
> **BlizzofOZ said:**
> Check out this link to my question at Apache Friends:
[http://www.apachefriends.org/f/viewtopic.php?t=29109]("http://www.apachefriends.org/f/viewtopic.php?t=29109")

I had to change 2 conf files, changing the LISTEN command from port 80 to the new port.
Files:
/opt/lampp/etc/httpd.conf
/opt/lampp/lampp

Additionally, you need to add the new port in your router setup.  You setup the new port, to port forward to the server IP address.

ok, thank you!

---

### Post by BlizzofOZ on 2008-04-05
> **insub2 said:**
> ok, thank you!

Did you get it to work?

---

### Post by insub2 on 2008-04-05
> **BlizzofOZ said:**
> Did you get it to work?

I haven't had time to try it out yet.  But I'll let you know.

---

