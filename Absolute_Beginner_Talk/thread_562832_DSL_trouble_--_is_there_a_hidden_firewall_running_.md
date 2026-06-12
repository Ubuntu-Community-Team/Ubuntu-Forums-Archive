---
title: "DSL trouble -- is there a hidden firewall running on Ubuntu?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by buzznot1012 on 2007-09-29
I'm running Fesity Fawn on a Dell Dimension 2400 with a wired DSL connection going through a D-Link router.  I can connect to the Internet, but only intermittently.  It seems like some unseen firewall is running that is hampering my connection, though I have not yet installed a firewall.  I'm confused because I installed Feisty Fawn on an older machine a month ago as a trial run.  Everything worked perfectly.  I connected to the Internet once, and I was on my way.  Now, I have to go into the terminal and type in pon dsl-provider every time I want to view a new Web page.  It sticks and faulters, but eventually I can force my way through.

There has to be a better way.

I've searched these forums since Tuesday and haven't found anything that really applies to my situation.

Many thanks in advance for any advice you can pass along!

---

### Post by Sef on 2007-09-29
Yes there is.  Iptables is installed by default.

I suspect that the problem is either hardware related or a bad install since

---

### Post by mendingo84 on 2007-09-29
i suspect there are some messed up setings on the router. since you are connected to a router than the router should perform the dialing up. check your router and try to determine how often it changes you IP address ( that goes in the DHCP interface, i assume you have DHCP turned on and not static IP addresses )

---

### Post by tgalati4 on 2007-09-29
Do other machines have problems?  It could be a faulty router.

---

### Post by jon zendatta on 2007-09-29
check your router settings.
address  10.1.1.1
username   admin
password    admin

---

### Post by buzznot1012 on 2007-09-29
Thanks for the replies!!

It's strange that my Dell desktop would have this problem when I'm literally using the same jack to connect to the Internet that I used on my other computer.

Anyhow, I'm new to using Linux commands, so when I type "address 10.1.1.1" in my terminal, it tells me "command not found".  When I just type that number into the terminal. It gives me the same thing.  What exactly should I be typing in the terminal?

I only have a Dell Inspiron laptop and the desktop using the router.  They are not networked together.  The laptop's Internet connection is perfect, as was the desktop's when I was using Windows.  I'll keep at it.

Again, thanks for the input!

---

### Post by sasquatch74 on 2007-09-29
Type 10.1.1.1 into the address bar of your web browser.  Hopefully you have the router manual which will have the default admin and password needed to get access.  That should get you into the router's setup page.

---

### Post by buzznot1012 on 2007-09-29
Awesome!  Thanks.

---

### Post by dberg on 2007-09-29
I have been having a problem that sounds similar.  My connection will work great for a while but then once every day or two I start having trouble connecting to most websites (though a select few will still connect). If I turn off my DSL modem and router and turn them back on the problem is usually fixed for another day or two.

The windows machine plugged into the same router has no trouble at all. Needless to say it is really annoying to have to do this all the time.

EDIT: Forgot to say that my router is a Linksys.

---

### Post by buzznot1012 on 2007-09-29
Yes, I definitely have to work on the router.  I do reinstalls so seldom, I completely forgot that I had to reconfigure that. I do appreciate the replies here -- and throughout the forums.  All extremely helpful.

---

### Post by dberg on 2007-09-29
So what router settings should be checked and/or changed?

---

