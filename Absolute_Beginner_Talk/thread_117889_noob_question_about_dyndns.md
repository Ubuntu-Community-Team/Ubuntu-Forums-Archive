---
title: "noob question about dyndns"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by oxboy on 2006-01-15
hi all,

I'm was trying to set up an ftp server, and after reading a bunch of threads about it, I decided register a domain at dyndns because of my dynamic ip.  I got an account and name set up.

I was being curious, and decided to type in the host name into my web browser to see what would happen.  A login for my router appeared :confused:  Is that supposed to happen?  or rather, is that safe?  Am I doing something wrong that I could fix so that this doesn't happen, and for me to still have the host name?  

Thanks a lot!

---

### Post by Mr_Grieves on 2006-01-15
No, it's not the way it's supposed to be. Immediatly deactivate remoting handling of your router. You're at risk of getting it hacked.

Read your routers manual, it's all there. Or post the routers make here, and some kind soul can find it for you.

---

### Post by ptmurphy on 2006-01-15
[QUOTE=oxboy]hi all,

I'm was trying to set up an ftp server, and after reading a bunch of threads about it, I decided register a domain at dyndns because of my dynamic ip.  I got an account and name set up.

I was being curious, and decided to type in the host name into my web browser to see what would happen.  A login for my router appeared :confused:  Is that supposed to happen?  or rather, is that safe?  Am I doing something wrong that I could fix so that this doesn't happen, and for me to still have the host name?  

Thanks a lot![/QUOTE]

Well, normal if you have not completed your setup.  Getting the DynDNS account setup and seeing your ip address is halpf the equation (maybe 2/3).

In your router, you need to tell it to forward traffic on port 80 (default for http traffic) to the computer running the web server.  This is what happened when you entered it in your web browser, it defaulted to port 80 and found the web interface to your router.

So, if you want http traffic and/or FTP traffic to be routed to a computer on your network, you must setup what most routers call "Port Forwarding".  You tell the router than any traffic on the http port (80) forward to and internal computer running a web server (192.168.0.2, for example).  Same with FTP.  Just forward that port to the computer running your FTP server.

Make sure you secure your FTP and HTTP servers.

---

### Post by Mr_Grieves on 2006-01-15
You should only forward port 80 if you are running a webserver. In any case, you need to shut off remote management on the router!

---

### Post by oxboy on 2006-01-15
Ahhh!  I don't want to be hacked!  Ok so I looked looked at my router and it says that remote management *is* disabled =/.  Does this mean I'll have to set up an http server too if I only want to have an ftp server so that other people can't get into my router?

For now, I just forwarded  port 80 anyway so that if i just enter the host name on my browser i don't get the login but an error that says connection refused.  I don't know if thats any better, but I checked again and it does say remote management is disabled, so I'm not sure if its still safe.  I'm following the How-to's posted for the ftp server, so i'm guessing its secure?  Don't really know how to check...

Anyway thanks so much for your help.  Any more advice would be greatly appreciated.  Thanks again!

---

### Post by hen3rz on 2006-01-15
Well as long as your router login page doesnt display anymore and all traffic on port 80 is forwarded somewhere else you should be reasonably safe.

Just a small note. It isnt very hard to set up a http server with Ubuntu its as simple as typing 2 lines of code into the terminal:
```
sudo apt-get update
sudo apt-get install apache2
```
(I would recommend the apache http server as it has a large ubundance of support)

Once Apache is installed simply open up /var/www/ and save a .html page as index.html this page will be displayed when your visitors go to [http://you.dyndns.org](http://you.dyndns.org)

If you cant be botherd making a web page you can always just leave index.html blank.

---

### Post by oxboy on 2006-01-15
ah i'm so stupid!  I think the reason why I got the prompt was because I was typing in the hostname from within the lan. =/ sorry about all the trouble...

---

### Post by hen3rz on 2006-01-15
> ah i'm so stupid! I think the reason why I got the prompt was because I was typing in the hostname from within the lan. =/ sorry about all the trouble...

lol its all good we all make mistakes.

---

### Post by ptmurphy on 2006-01-16
[QUOTE=oxboy]Does this mean I'll have to set up an http server too if I only want to have an ftp server so that other people can't get into my router?
[/QUOTE]

No, just setup the FTP port to forward if you do not have a web server.

FTP defaults to ports 20 and 21.

---

