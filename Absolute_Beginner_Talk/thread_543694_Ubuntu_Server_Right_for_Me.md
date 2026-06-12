---
title: "Ubuntu Server: Right for Me?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-05
I'd like to set up my own E-mail domain address and Web Server for my family
example:  [email]Bob@MyFamilyName.com[/email]

I understand 1st I must get a domain name in which
I may or may not be able to get. I could get this from Godaddy.com
Example: MyFamilyName.com

I will more than likely use Gallery for the Website
( Just a Photo Site ) for everyone to exchange Photos
Easier. 

I have a SmoothWall in Which I will connect my Server to
the Orange Nic.

Would Ubuntu Server be right for me?
Are Linux Servers easiser and more secure
to use then a Windows Server.

New to this so I just would like some Help and opinions.  :KS

---

### Post by splintercellguy on 2007-09-05
Probably, there should be a guide to setting up a mail server somewhere.

---

### Post by cmnorton on 2007-09-05
You have asked a question about creating an email domain, and I am interested in the answer. 

As to whether or not you should use Ubuntu, are you talking about the Ubuntu server distribution? If you are and you do not mind working in text only mode, then my experience is a Linux (Ubuntu) server is going to be far more reliable and cost you less than a Windows server. 

You might want to consider installing regular Ubuntu with its graphical interface; configuring your system with the daemons (services) to support your email domain; and when you feel you want to button the server up (you can live without the graphical interface), you can run the server without the X interface. 

I have heard from experts that if the system is not going to be used as a workstation/desktop, then running with X turned is a good thing to do, because your server's cycles are spent running your application, and not running X.  I don't subscribe to that way of thinking especially with today's hardware targeted at high-end desktops and workstations, let alone servers.

You will perhaps need to read more than on a Windows server, but you will know a lot more when you are done, and you won't be paying Windows server costs. I do not know if you can run an email system on the Windows workstation distributions. Look at open source email systems for Windows. Mercury may be one of them.

---

### Post by Nythain on 2007-09-05
i know ill probably get flamed from hell for saying this but...
honestly, if you arent running a major server (wich from the looks of things you arent) i would suggest just installing regular ol' ubuntu. The only advantage you are going to gain from the server version is it comes with the most common server daemons (mysql, apache, i forget the ftp and mail ones) already installed and will ask you a MINIMAL amount of questions during installation to set them up. You will more than likely STILL end up havening to configure them greater after the installation anyways.

With the ubuntu desktop install, you will have to go and install the server's you want to run (wich can almost be considered a plus since you get to choose what you want to install and set up), and a lot of them now adays have GTK front ends for configuring them (will make things a little easier for someone new to the linux end of things)

And as mentioned above, with current hardware your loss of perfomance running X shouldnt be to big of an issue... now if you were running a file server, or a high bandwidth corporate webserver then my views would change, but thats where i stand.

---

### Post by dca on 2007-09-05
You can find some good Ubuntu set-up info here:
 
[http://www.howtoforge.net/taxonomy_menu/1/1/50](http://www.howtoforge.net/taxonomy_menu/1/1/50)
 
Just be sure you unblock certain ports on your router:  80 for HTTP and others for sendmail, etc...

---

### Post by irish_flu on 2007-09-05
My Ubuntu Mail Server uses "Zimbra".  It's a pretty cool web/POP/IMAP mail server frontend (Apache and Postfix in the backend); I'm running it on top of Ubuntu Dapper, and couldn't be happier.

So, yes I think Ubuntu is an excellent choice. The others are right when they say that you'll do just fine if you use the Desktop Edition and add whatever services you want.  Of course, you can just as easily install the "server edition" and add the familiar GUI if you want.  AFAIK the main difference between the two is *default* packages installed.

Here are a couple of things to think about (just in case you haven't already):
If you're considering buying a domain, this will need a public IP address to point to; this address needs to be "static", not the DHCP addresses (which change periodically) commonly offered by ISPs.

Also, somebody needs to host the DNS "A Record" (the authoritative domain pointer) and "mx record" (mail exchange) for this domain on their nameservers.  Some Registrars (I don't know about GoDaddy) wil offer this for a fee.  You might also consider "OpenDNS", which might even be free.

---

### Post by ZenMasta on 2007-09-05
Unless you mostly want this for learning experience it seems like it would be easier to sign up for one of the 5 dollar a month hostnig companies that does it all for you. That way when your ISP is down mail isn't getting bounced. 


Plus lots of hosts these days have auto install for things like joomla and gallery.

---

### Post by irish_flu on 2007-09-05
I gotta go with Zen on that one.

The other thing is that if you're using a "typical" (here in the 'States anyway) home connection, your "upload" speed is very limited (compared to your download speed) and folks using your pages might see very slow load times for images and such.

---

### Post by rsambuca on 2007-09-05
For a server of this size, I would go with the straight server edition of (ubuntu, debian, etc.).  The advantage of this is that for your needs, your server will run perfectly with an old pIII, which you can pick up for $50 somewhere.  Running on a fancy new setup is just a waste of money.

There, now you have pretty much every different option covered!

---

### Post by daveshields on 2007-09-05
I agree about using a hosting service. They are cheap. I use Bluehost.com. They run Linux and you can get direct access via ssh if you need it, though you can install many common packages using Fantastico.

---

### Post by Orbital75 on 2007-09-05
Well, If I do decide to run the Server from home, it will be on an old PC which has
been laying around.  This PC is a 400mhz AMD Chip with 192meg of ram (Maxed out).
At one time I had it set up with Windows 2000 Pro and Gallery install on it.  I use No-ip.com 
to resolve my Home IP address and keep it on another network (Orange) with my SmoothWall. 
This way, it keep bad guys off my local LAN (Green) network
The bad thing was that I didn't have my own Domain and I had to use something
with the no-ip.org ending.   

If I install Ubuntu or Ubuntu Server and want to run Gallery, I will need CSS, PHP, MySQL, and Apache installed
on the machine. They worked fine on the 2000 Machine but I always worried about attack with a Internet facing
windows machine.  I've never ran a Mail Server before so I don't know what I would
use for that.   SendMail ?

---

### Post by irish_flu on 2007-09-06
Lots of people use Sendmail and say good things about it.  Also, lots of people use Postfix and say good things about it.

---

### Post by mlentink on 2007-09-06
It depends a bit on how well versed you are with protocols and a bit of security.For many years I've run the mail server for my SOHO-domain( I run a small consulting business) on Windows. With Postmaster (regrettably it doesn't exist anymore)  server. Rock solid. From a windows perspective, that is.
Since a little over a year, it's Ubuntu 6.06 with  Postfix and Dovecot. It was a bit of a learning curve getting it installed and configured. But basically I haven't touched that box since October 2006. Rock Solid has been redefined for me. Gradually, I am moving the web-stuff over form a provider to my box.

Tune in, turn on, drop out.
Join the rebellion, you will be rewarded

---

### Post by reckless2k2 on 2007-09-06
well if you are going to do it then you need to buy the FQDN and have DDNS service. Go with no-ip.com for the one stop feature. you can get it from dyndns too. i think the prices are the same. then because of your resources you are looking at a lot of command line fun. hopefully it won't turn you off. zimbra won't really work on that config so you'll have to do postfix and squirrelmail for a frontend which is probably best. some would argue. if you don't need webmail, you can just pull it down to any normal desktop with outlook or thunderbird..yadda...you get the idea. webserver with apache...again have fun at the commandline. all can be done on ubuntu but you will be getting REAL comfortable with the commandline.

---

### Post by mlentink on 2007-09-06
Ain't nothin' wrong with that,  man...
(oops or: woman)

---

### Post by cmnorton on 2007-09-08
[QUOTE=Orbital75;3315422]Well, If I do decide to run the Server from home, it will be on an old PC which has
been laying around.  This PC is a 400mhz AMD Chip with 192meg of ram (Maxed out).
At one time I had it set up with Windows 2000 Pro and Gallery install on it.  I use No-ip.com ...

192 MB RAM seems a little too lean for a server, and maybe even for a client. I am running 6.06 LTS on an Acer TravelMate 630 that came through new with 250MB RAM. I just upgraded it with a second SODIMM (500MB) chip, because the response was a little pokey.

---

### Post by Orbital75 on 2007-10-11
Looks like I'm going to dive deep into the command line but that's a good thing.
I've wanted to learn it better anyways so here's my chance.   :popcorn:

---

### Post by HermanAB on 2007-10-11
Two things:
a. If you wish to run a server at home, install Xubuntu, so that you get a minimalist GUI.
b. If you have never set up an email system before, then I suggest that you install something that is really easy to set up: [http://www.citadel.org](http://www.citadel.org) is the best in this regard thanks to the Easy Install script.  Getting a full fledged, fast and secure system up takes only about 20 minutes.

Cheers,

herman

---

