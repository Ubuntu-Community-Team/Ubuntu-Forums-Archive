---
title: "[SOLVED] Newbie - Please help, so close"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-07-31
Hello, I am a newbie at setting up ubuntu, server adn all of that. I have messed with apache in the past and I am somewhat familiar with it. Ok this is the point I am at and I am totaly stuck.

I have set up ubuntu with gnome gui. It works.
I have installed Apache2, php5, mysql and phpmyadim.
All work by going to local host.

Now i want to set my domain [www.kennyn.info](www.kennyn.info) which I have purchased through godaddy.com to point to that box at home.

There is only one problem. My internet service provider uses dynamic IP address. 

I signed up for name servers, at zoneedit.com

I am also behind a netgear router. 
I have also already made sure that the mac address of my machine will allways stay to the 192.168.0.7 IP address that my router gives it.

Now what do I do. I have pointed the domain to the name servers that I was given by zoneedit, but of course the IP address' are not correct in the zoneedit settings, mainly because I am lost on where to get the correct IP address and what to do.

I feel as if I am so close to get this working, just dont know where to go from here. Please can someone advise me on where to go from here. If you would like to see some of my settings, please let me know and I can send them. 

Thank you and have a great day.

---

### Post by MikeEvans on 2007-07-31
You need a dynamic DNS client running on your computer to tell Zone Edit what your IP address is.  There is information about it on the Zone Edit FAQ.  You also need to set port forwarding on your router for the port your serving on (usually 80).  

There are some Dynamic DNS update clients in add/remove programs but I don't know if they work with zone edit.  I use one with DynDns.org.

---

### Post by kennyn on 2007-07-31
Ok so now the stupid question. I am pretty sure that I already installed DynDNS on my machine, if so, do you know how I can figure out where it is and if it is installed.

---

### Post by MikeEvans on 2007-07-31
Well if you installed it with add/remove programs it will be easy to find.  First check your menus under applications -> internet to see if its there.  If not open up add/remove and query DNS and see if anything that comes up is installed.

If you used Synaptic then there should still be an entry in your menu's.  If not open synaptic and search installed applications for it.

If you compiled from source you should always hold onto the source files.  You could also check /etc for a configuration folder or just search your file system for "DNS".

---

### Post by kennyn on 2007-07-31
Thanks, greatly appriciated. I will check when I get home tonight and then post back what I find. Thanks again.

---

### Post by MikeEvans on 2007-07-31
Also,  synaptic logs everything you install.  Open it up and choose history from the file menu.

---

### Post by kennyn on 2007-07-31
Ok evidently I do not have dyndns installed on my machine. Any instructions on how and what to install to get the dns working with zoneedit????

---

### Post by Cybergod on 2007-08-01
Check the below link out.  It should provide all the info you need.

[http://www.zoneedit.com/doc/dynamic.html?AdRefer=http%3A%2F%2Fwww.google.com%2Fsearch%3Fq%3Dzoneedit%26ie%3Dutf-8%26oe%3Dutf-8%26aq%3Dt%26rls%3Dcom.ubuntu%3Aen-US%3Aofficial%26client%3Dfirefox-a]("http://www.zoneedit.com/doc/dynamic.html?AdRefer=http%3A%2F%2Fwww.google.com%2Fsearch%3Fq%3Dzoneedit%26ie%3Dutf-8%26oe%3Dutf-8%26aq%3Dt%26rls%3Dcom.ubuntu%3Aen-US%3Aofficial%26client%3Dfirefox-a")

---

### Post by MikeEvans on 2007-08-01
Here is a linux client that says its compatible with ZoneEdit

[http://encodable.com/eponym/]("http://encodable.com/eponym/")

---

### Post by kennyn on 2007-08-01
Thanks, Going to go with Eponym. Will install it tonight and reply back once it is set up. Thanks again for all of the help!!

---

### Post by asmoore82 on 2007-08-01
> **kennyn said:**
> I am also behind a netgear router. .

All home routers have the best type of Firewall - NAT.

you need to get into your router's settings and either
1. enable a Virtual Server on port 80
-OR-
2. enable Static NAT (DMZ) to your computer

I highly recommend option 1  over option 2 ...
mainly because Static NAT on some routers is known
to break the bittorrent checksum, always on the very last piece of the download ...
the "Stuck at 99.9% Complete" symptom :D

---

### Post by kennyn on 2007-08-01
Just purchased eponym. Will hopefully succesfully set it up tonight and post back. 

I have another quick question thou. When i was initially setting this box up I was using the domain kennyn.com. But now I have changed my mind. I want to use

kennynproductions.com 

I hope that this wont mess me up to much. Do i have to change any setting within apache2 or anywheres else for this all to take place without much problems.

Thanks.

---

### Post by kennyn on 2007-08-03
Ok, I have installed eponym finally, I think, I looked at eponym-current-state.txt and this is what I get, Now What. I looked at the Zoneedit under my domain and it still says the original ips. What do i do now. This is what that file said.


-----------------------------------------------------------------------------------------


You are 24.252.65.214, saith [www.ipaddressworld.com/](www.ipaddressworld.com/).
You are 24.252.65.214, saith [www.edpsciences.org/htbin/ipaddress](www.edpsciences.org/htbin/ipaddress).
You are 24.252.65.214, saith [www.selfseo.com/what_is_my_ip.php](www.selfseo.com/what_is_my_ip.php).

20070803-2000: Detected your IP successfully.

/eponym/eponym.pl: $mime_msg->send failed: SMTP MAIL command failed: 
... temporary failure

 at /eponym/eponym.pl line 1139

Attempting to continue since email-related problems do not affect Eponym's core functionality; however you should look into this problem.
There was a problem detecting one of these IP addresses:
kennynproductions.com: unknown
your IP: 24.252.65.214

Update skipped.  Eponym will continue to run because this might be a
temporary network outage; however if you get this message lots of times
there is probably a problem.

/eponym/eponym.pl: $mime_msg->send failed: SMTP MAIL command failed: 
... temporary failure

 at /eponym/eponym.pl line 1068

Attempting to continue since email-related problems do not affect Eponym's core functionality; however you should look into this problem.
/eponym/eponym.pl: $mime_msg->send failed: SMTP MAIL command failed: 
... temporary failure

 at /eponym/eponym.pl line 1068

Attempting to continue since email-related problems do not affect Eponym's core functionality; however you should look into this problem.

Exiting.

---

### Post by kennyn on 2007-08-05
OK Scratch, the last thing I wrote. Eponym is working. 

If I go to [http://www.kennynproductions.com](http://www.kennynproductions.com) within my network, it pulls up fine. But anyone else i ask to test it, cannot see it. I have my router port forwaded to port 80.

I am pretty sure that my ISP blocks port 80 from the outside. 

I tryed changing the port forwarding to 443 and then nothing pulls up even in network.

I am so close I can taste it. Can anyone else please help me. I have a netgear router. Dont know where else to go from here.

---

### Post by Cybergod on 2007-08-05
You might want to use port 8080 and make sure you specify port 8080 in your router settings for port forwarding.  Once this is setup the your site should be accessible by [http://www.kennynproductions.com:8080](http://www.kennynproductions.com:8080)

---

### Post by MikeEvans on 2007-08-06
You are close  :)  You may be right about your ISP blocking port 80 but I have yet to encounter one that does.  Be sure to check:
[LIST]
[*]Your router may have a web interface that listens to port 80, which will interfere.  Check it out.
[*]Firewalls,  if your using any type of firewall you may want to open it up for testing.
[/LIST]
Also, if you are changing ports you need to tell apache to listen on that alternative port.  If you using virtual hosts you may need to specify it within the VH header.

---

### Post by Dr Small on 2007-08-06
Open port 80 on your firewall to allow incoming connections.

---

### Post by kennyn on 2007-08-08
Ok, let just say I am there but just frustrated. I finally got my server to work. The downfall is my ISP blocks port 80, so I had to set my port to 81.

So if you go to: [http://www.kennynproductions.com:81](http://www.kennynproductions.com:81) you should get my website.

This is really agrivating, I dont want to have to put in :81 after it. Does anyone know how to disguise this or fix this without having to get a new domain and mask it to that address??

Thanks.

Also one more question, my current full time job blocks anything on 80, 81 etc. I know that they do not block 443. Any way of getting around this so that i can pull my website up here from work as well as everyone else in the real world still being able to see it??

---

### Post by por100pre1 on 2007-08-08
Try to check if your DNS service can be configured to use IP number with port, like xxx.xxx.xxx.xxx:81 instead of just your IP number.

---

