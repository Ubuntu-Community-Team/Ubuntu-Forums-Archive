---
title: "setup an ubuntu web server"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-03-24
ok, so i want to set up a web server on my desktop (running kubuntu).  while doing some searching for similar posts, i found:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=8776]("http://ubuntuforums.org/showthread.php?t=8776")
[*][http://ubuntuforums.org/showthread.php?t=347005]("http://ubuntuforums.org/showthread.php?t=347005")
[*][http://ubuntuforums.org/showthread.php?t=83220]("http://ubuntuforums.org/showthread.php?t=83220")
[*][http://www.cjfay.com/lamp.html]("http://www.cjfay.com/lamp.html")
[*][http://sheeped.com/2007/01/29/set-up-ubuntu-linux-lamp-server-in-minutes/]("http://sheeped.com/2007/01/29/set-up-ubuntu-linux-lamp-server-in-minutes/")
[/LIST]

but what i am basically looking for is a server that can be used to display web pages.  now most of the time i dont have physical access to my desktop so i read in one of the posts that i might be able to set up FTP access to upload files.  but upon further reading, i saw that ssh would be better for "security" reasons.

so i think i would go into synaptic and install "apache2" and "ssh", and possibly "php4" (with that lib-php-something-or-other-module).  i do have some experience with apache, although limited.

i guess my question is **how would i make it so that the "rest of the world" can view the website?** even though i'll probably be the only one accessing it and using it as file storage.  i'm behind a router and i included a screen shot of the router port forwarding page which i think i might have to add something (there are free slots when i scroll to the way bottom).  **what would i add so that the server would be accessible from outside the home network?**

if i enter an entry, i'm guessing that i would do something like:
[LIST=1]
[*]enabled == checked
[*]some description
[*]inbound port == 80 (i think)
[*]not sure what to put in after the dash
[*]type == TCP (the only other option is UDP)
[*]private IP address would be my desktops ip address.... maybe, i think?
[*]private port == no idea :confused: 
[/LIST]

is that all i have to do? set up the apache with ssh, and modify the routers port forwarding?  also, how would people connect to the server? would it be something like [ [http://ipaddress/](http://ipaddress/) ], or could i set up apache to have an actual name?


thanks for any help

---

### Post by schwascore on 2007-03-24
Apache listens to port 80 by default.  This means that as long as you have your router forwarding all port 80 traffic to your computer, Apache will respond.  If you are a home internet user, you probably have a dynamic ip address.  In this case, you can use tools like [http://www.dyndns.com/](http://www.dyndns.com/) to create a dynamic domain name.  In combination with the ddclient tool.  See this post:

[http://ubuntu.wordpress.com/2005/09/08/updating-dynamic-ip-address-automatically/](http://ubuntu.wordpress.com/2005/09/08/updating-dynamic-ip-address-automatically/)

Once you have this set up, people can just go to your domain name.  You can use a free one from dyndns that will look similar to this: username.dnsalias.org, or for a price you can have a top level domain name point to your server.

I have used ddclient and dyndns with great success for the past two years.  Good luck, keep us posted.

---

### Post by rmadhu on 2007-03-26
> **rbprogrammer said:**
> 

i guess my question is **how would i make it so that the "rest of the world" can view the website?** even though i'll probably be the only one accessing it and using it as file storage.  i'm behind a router and i included a screen shot of the router port forwarding page which i think i might have to add something (there are free slots when i scroll to the way bottom).  **what would i add so that the server would be accessible from outside the home network?**


thanks for any help

I am able to open up the port for the rest of the world . 
Here are my details 
1) I have my apache running 
2) I have done the port forwarding in the router .
 But when i type the ip address my ISP is providing , I am unable to reach my side . meaning 
[http://111.222.333.444](http://111.222.333.444) shows the page is inaccessible. 
But [http://localhost](http://localhost) shows my pages .

The same thing works fine with my windows boot.  Meaning my router config is fine. Is there any firewall thats blocking my ubuntu ? or am i missing something in Apache config.

TIA

---

### Post by rbprogrammer on 2007-03-31
> **rmadhu said:**
> 
The same thing works fine with my windows boot. 

TIA

i didnt get my problems completely solved, but for your problem, do you mean that you have one computer and you log off of ubuntu and then log into windows?  b/c if you do that then you will be shutting down your apache server on ubuntu.  as for your problem when in ubuntu, sorry, i'm not up to that part yet.....

---

### Post by schwascore on 2007-03-31
rmadhu:

You should double check that both Windows and Ubuntu have the same IP address when running.  Depending on your setup, DHCP will sometimes release an address and assign a new one between boots.  Other potential problems are if one OS has a static IP set and the other doesn't, or if both have static IPs set and they are different.

Double checking those settings would be a good place to start.

---

### Post by rbprogrammer on 2007-04-02
ok, so i thought i had everything working...  i was on my desktop at home and i installed ddclient, apache2, php, yada yada yada... so i can access my website from inside my network, but when i try to access the site from outside my network, i get a "The Connection has Timed Out."  this happens when i try to connect to the dyndns.org name ( [http://rbprogrammer.is-a-geek.net/](http://rbprogrammer.is-a-geek.net/) ).  i can get to the site with that URL, but once i leave my network (ie go to the college campus), i cant get access.

i'm not sure exactly what to post to better explain the problem.

---

### Post by punx45 on 2007-04-02
your home ISP might not allow incoming port 80 requests to your computer.

---

### Post by rbprogrammer on 2007-04-02
but then how do you explain my computer connecting to the dyndns.org site? :confused:

so then could i just use a different port and put something like: [http://rbprogrammer.is-a-geek.net:####/](http://rbprogrammer.is-a-geek.net:####/)

where #### is just some unused port on my router?

---

### Post by Dual Cortex on 2007-04-02
Can you connect to your computer using your IP?
[http://www.whatismyip.org/](http://www.whatismyip.org/)

Does your routher have a DMZ option? A bit less of a margin error if you could add your PC in the DMZ and see if accessing the PC through your external IP address works.

---

### Post by schwascore on 2007-04-03
Short answer:  Yes, you can re-route port 80 traffic over a different port.

Long answer: Depending on your ISP, that could be a problem.  I'd get in touch with tech support from your ISP and see what they can tell you before you spend any more time banging your head against the monitor on this one!

---

