---
title: "[SOLVED] Ubuntu Virus?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by moochtastic on 2007-07-20
Hi, I'm very very new to ubuntu so please be very clear as to what you mean :) thanks.

Hi,

A while ago I had a bit of a problem with my windows XP computer (see this thread: [http://forums.techguy.org/security/5...r-problem.html](http://forums.techguy.org/security/5...r-problem.html)), but that is all fixed now, I got help installing ubuntu on it and it is now virus free, and I have all my files nicely backed up in a fat. Anyway one of the things I had been told to do with my XP hard drive was periodically check that my ports were closed, and I have continued to do the same with my Ubuntu hard drive. I am a little concerned however that I am seeing some ports appear in the scan.

The results are shown here:

[http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm)

And the ports were:
[http://www.ictsc.com/IP_Port25.htm](http://www.ictsc.com/IP_Port25.htm)
[http://www.ictsc.com/IP_Port80.htm](http://www.ictsc.com/IP_Port80.htm)

So does that mean I have another virus? I was told that viruses on Ubuntu were quite rare, and I have only installed software with the tools I am meant to use, I have not downloaded any, also I have used fire fox and not internet explorer (I cant find internet explorer!) and I am told that that is also safer.

So is there a mistake at the port scanner, or is there a problem with my computer again? I still am not sure if this port scanner [http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm) is any good or a scam.

---

### Post by por100pre1 on 2007-07-20
If you are unsure about that port scanner try [ShieldsUP]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by ben::zen on 2007-07-20
Okay, the simple answer is, there's no problem.
More in-depth: if you read the information on ports 25 and 80, you would see SMTP and HTTP respectively. These are basic internet services, those ports need to be open for some systems to work. Mail is often routed out through port 25, and all your web needs go through port 80. So, again, there's no problem at all; everything's just fine.

EDIT: Oh, and as for IE, it's Windows/Mac OS X only, and Firefox is definitely better. Fewer holes, and much more standards-compliant than IE.

---

### Post by bodycoach2 on 2007-07-20
Port 80 is used for Internet, and Port 25 is for mail - particularly with a mail client. On almost all computers, these ports are open, by default. If you use a Web based mail system, like Yahoo, Gmail, Hotmail, you might be able to close Port 25. I wouldn't close Port 80.

You might want to use a Firewall, especially a hardware one. Pretty much any NAT Router will do.

Anyone, if I'm wrong on this, please correct me.

> **moochtastic said:**
> Hi, I'm very very new to ubuntu so please be very clear as to what you mean :) thanks.

Hi,

A while ago I had a bit of a problem with my windows XP computer (see this thread: [http://forums.techguy.org/security/5...r-problem.html](http://forums.techguy.org/security/5...r-problem.html)), but that is all fixed now, I got help installing ubuntu on it and it is now virus free, and I have all my files nicely backed up in a fat. Anyway one of the things I had been told to do with my XP hard drive was periodically check that my ports were closed, and I have continued to do the same with my Ubuntu hard drive. I am a little concerned however that I am seeing some ports appear in the scan.

The results are shown here:

[http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm)

And the ports were:
[http://www.ictsc.com/IP_Port25.htm](http://www.ictsc.com/IP_Port25.htm)
[http://www.ictsc.com/IP_Port80.htm](http://www.ictsc.com/IP_Port80.htm)

So does that mean I have another virus? I was told that viruses on Ubuntu were quite rare, and I have only installed software with the tools I am meant to use, I have not downloaded any, also I have used fire fox and not internet explorer (I cant find internet explorer!) and I am told that that is also safer.

So is there a mistake at the port scanner, or is there a problem with my computer again? I still am not sure if this port scanner [http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm) is any good or a scam.

---

### Post by reckless2k2 on 2007-07-20
port 80 is http...web sits..yadda.
port 25 is smtp..email

linux doesn't get viruses. you can open a port but that doesn't mean you'll get a virus in linux.

---

### Post by meierfra on 2007-07-20
Relax. At the end of  both files it says:

No results found.

---

### Post by por100pre1 on 2007-07-20
Let me make something clear: ports 25 and 80 are for mail and web servers. If your PC is not running neither of them, they should NOT be open!

---

### Post by moochtastic on 2007-07-20
Are they ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) more trustworthy than ([http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm)) the one I am using??

---

### Post by vwbeamer on 2007-07-20
While there has been attempts to launch Linux viruses, at this time there are no known active Linux viruses. All viruses have failed for various reasons.

In order for a Linux virus to work, it would need to work on both Windows and Linux. There are simply not enough Linux compiters for a virus to spread. Add to that, Liniux is much more secure then windows, viruses should be low on your worry list.

---

### Post by por100pre1 on 2007-07-20
> **moochtastic said:**
> Are they ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)) more trustworthy than ([http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm)) the one I am using??

I can't tell... I haven't use the ictsc.com scanner.

---

### Post by meierfra on 2007-07-20
Who says the ports are open? The web pages only lists what kind of warnings  he might get. And then its says : No resuts founds.

---

### Post by moochtastic on 2007-07-20
> **por100pre1 said:**
> Let me make something clear: ports 25 and 80 are for mail and web servers. If your PC is not running neither of them, they should NOT be open!

Does that mean that they shouldn't be open or that they should? and is that port scanner OK or is it a bad one ( I have been trying to find out if its a scam to get you to use their services or something)? I seem to always have open ports when I use it, although I think I had some viruses under P so that's fair.  If they are open and shouldn't be does that mean I have a virus?  It is definatley saying that they are open:

[http://www.ictsc.com/IP_Port25.htm](http://www.ictsc.com/IP_Port25.htm)
[http://www.ictsc.com/IP_Port80.htm](http://www.ictsc.com/IP_Port80.htm)

that other scanner: the one at [http://www.grc.com](http://www.grc.com) is also saying I have port 25 and port 80 open, but I suppose that that ictcs lot and the grc people could be the same, their port scanner looks similar... Any ideas?  

I thought ubuntu was virus resistant, that is the only reason I decided to change over!

---

### Post by moochtastic on 2007-07-20
> **meierfra said:**
> Who says the ports are open? The web pages only lists what kind of warnings  he might get. And then its says : No resuts founds.

I think I gave you the wrong information a bit.  When I go to [http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm) it shows me two red blinking boxes, and then when I click on those and say open in new tab (much better than new window from internet explorer!) it shows me those pages and what those ports are about.  So I think that means I have those ports open as the other boxes are green and dont blink.  If that makes sense.

---

### Post by por100pre1 on 2007-07-20
I think you should read [this]("https://answers.launchpad.net/ubuntu/+question/9712").

---

### Post by DBStevens on 2007-07-20
Did you look at those pages for each port.

You should note that those are possible things that have been found on those ports not what was found on your ports.

The interesting line is the one at the bottom No Results Found.

Shields up will tell you about open ports, in fact you can actually scan your own ports.

~$ nmap 127.0.0.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-20 22:45 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
80/tcp  open  http
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.265 seconds
~$


Which is correct I have a webserver on port 80 and cups is on 631.

From outside in my system would only show port 80 which is the only forwarded port  on my system. firewall and yes I have Apache on that port.

An open port is not a virus by any stretch of the imagination.  Ports need to be open if you are going to use the services that require them.

---

### Post by meierfra on 2007-07-20
Yes,  it does mean that those ports are open.  I justed tested the web site. All my ports are closed, So I didn't get any red dots. I then  opened  port 80 in my firewall and in my router. I still did not get a red dot. Finally I started apache2 (a webserver) and then I got a red dot for port 80. Are your running a web server on your computer? If not there really is no reason for port 80 to be open.

---

### Post by por100pre1 on 2007-07-20
I'm sure about it; port 25 is for SMTP mail servers and port 80 is for Web servers. They should NOT be open if you are not using smtp and mail servers. Check the link I gave you previosly, a legitimate program may be configured to act like a server on those ports (I'm trying to be optimistic about that). If you want to you can use either avast! for Linux or F-Prot with XFPROT. Besides it's not a bad idea to check for rootkits, install chkrootkit and rkhunter:
```


sudo aptitude install chkrootkit

sudo aptitude install rkhunter


```

To use them:

```


sudo chkrootkit

sudo rkhunter --update

sudo rkhunter -c -sk


```

---

### Post by moochtastic on 2007-07-20
> **DBStevens said:**
> Did you look at those pages for each port.

You should note that those are possible things that have been found on those ports not what was found on your ports.

The interesting line is the one at the bottom No Results Found.

Shields up will tell you about open ports, in fact you can actually scan your own ports.

~$ nmap 127.0.0.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-20 22:45 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
80/tcp  open  http
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.265 seconds
~$


Which is correct I have a webserver on port 80 and cups is on 631.

From outside in my system would only show port 80 which is the only forwarded port  on my system. firewall and yes I have Apache on that port.

An open port is not a virus by any stretch of the imagination.  Ports need to be open if you are going to use the services that require them.

OK now I am even more confused, I did that nmap 127.0.0.1 after doing a sudo apt-get install nmap and I get the following:



Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-21 04:03 BST
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp


So I think that means that that portscanner thing at [http://www.ictsc.com/portscanner.htm](http://www.ictsc.com/portscanner.htm) is lying to me as port 25 and port 80 are not shown.  So from that I can assume that I also have that cups thing (what is that anyway?) but no webserver (should I have? I can see the internet.. but no internet explorer, do I have to install a webserver to get internet explorer?). I assume that that probably means that the [www.ictsc.com](www.ictsc.com) people are just saying there are open ports to get you to buy their services, and should probably be named and shamed somewhere for making people worried, its like those pop ups that claim you have won stuf and you never really have!.

Anyway thanks for clearing that up for me.

---

### Post by DBStevens on 2007-07-20
Cups is the common unix printing system.

---

### Post by moochtastic on 2007-07-20
> **DBStevens said:**
> Cups is the common unix printing system.

So would that be open because I have a printer installed? And how do I install an webserver?

---

### Post by DBStevens on 2007-07-20
That portscanner didn't lie to me when I used it through port 100 it showed I had port 80 open.

Now if one really looks at those lines in the individual ports that talk about this and that you'll discover that a lot of them are Windows gremlins that are being talked about.

---

### Post by DBStevens on 2007-07-20
Well using Synaptic locate and install Apache.

You might also have a webserver inside your router/whatever that is visible to the outside world.  It wouldn't be the first time that a router was exposed on the net.

---

### Post by moochtastic on 2007-07-20
I have just sent an email to all of these:

General Enquieries: [email]info@ictsc.com[/email]
ICTSC Sales: [email]sales@ictsc.com[/email]
ICTSC Marketing: [email]marketing@ictsc.com[/email]
Non Urgent Support: [email]support@ictsc.com[/email]
Web Site Administrator: [email]webmaster@ictsc.com[/email]

to complain about their port scanner not telling the truth about what ports are open.  Is there anyone they could be reported too as well to take action?.   I've had a look but there doesn't seem to be anyone who is properly in charge of these things.

---

### Post by Chris S. on 2007-07-20
A webserver is ... well, it's where you would put your website, if you have one.  By going to a website, using the HTTP protocol, you're accessing that site's web server on its port 80.  If you send an email to someone, you usually send it to port 25 on a mail server (though there are more exceptions to this now).

You don't need either port open on your computer, nor do you need a web server or mail server, unless you plan on hosting a web site or running a mail server on your computer.

---

### Post by por100pre1 on 2007-07-20
Keep in mind that it is not dangerous to have some open ports, if they are used by legitimate, and well configured programs. For example, I got port 5060 always open for a SIP hardphone.

---

### Post by meierfra on 2007-07-20
I  don't think portscanner is lying. Are you on a home network? That is, is there anybody else using the same internet connection?

---

### Post by moochtastic on 2007-07-20
> **meierfra said:**
> I  don't think portscanner is lying. Are you on a home network? That is, is there anybody else using the same internet connection?

No my computer is connected by a parallel cable straight to the internet, and no one else uses my computer.

---

### Post by DBStevens on 2007-07-20
meierfra,

It could even be the router itself since there are frequently multiple ways of talking to them, some can even process email.

---

### Post by moochtastic on 2007-07-20
> **DBStevens said:**
> That portscanner didn't lie to me when I used it through port 100 it showed I had port 80 open.

Now if one really looks at those lines in the individual ports that talk about this and that you'll discover that a lot of them are Windows gremlins that are being talked about.

> **meierfra said:**
> I  don't think portscanner is lying. Are you on a home network? That is, is there anybody else using the same internet connection?

Can anyone else confirm that the port scanner is telling the truth? Is there any reason why the port scanner would say one thing any that nmap program would say something else?  Do I need to apologise to the people I aave emailed? (posting stuff on the internet is excluded from libel isnt it??)

---

### Post by DBStevens on 2007-07-20
"Is there any reason why the port scanner would say one thing any that nmap program would say something else?"

Yes I already mentioned one, a router in the path.

That is the reason a nmap on my external ip address returns just the port 80 and not the port 631.

Prior to configuring things it had a webserver, a ssh server, sftp, and telenet server that was net facing.

---

### Post by moochtastic on 2007-07-20
> **DBStevens said:**
> "Is there any reason why the port scanner would say one thing any that nmap program would say something else?"

Yes I already mentioned one, a router in the path.

That is the reason a nmap on my external ip address returns just the port 80 and not the port 631.

Prior to configuring things it had a webserver, a ssh server, sftp, and telenet server that was net facing.


How do I find out my external address? ( I should point out that I didnt set up ubuntu by myself so I am not sure f the results I see are the right ones...)

Edit: Is the address shown in the summary bit on this page [http://www.ictsc.com/visibility.htm](http://www.ictsc.com/visibility.htm)  my external address?

---

### Post by meierfra on 2007-07-20
type 
```

ifconfig
```
in a terminal

---

### Post by meierfra on 2007-07-20
yes, it is. (Actually then I clicked on the  link it showed my  ip-address)

---

### Post by DBStevens on 2007-07-20
The nmap verified that you only had 631 open on your computer system.

You said youhave a direct connection to the net, I'd take that as meaning you don't have a home network.

If that is the case the port 25 and port 80 being open has to come from equipment you are not responsable for.

If you go back to that site that you did that scan on it tells you what your external IP address is.

It is also availible from running 

ifconfig in a terminal.

---

### Post by moochtastic on 2007-07-20
> **DBStevens said:**
> The nmap verified that you only had 631 open on your computer system.

You said youhave a direct connection to the net, I'd take that as meaning you don't have a home network.

If that is the case the port 25 and port 80 being open has to come from equipment you are not responsable for.

If you go back to that site that you did that scan on it tells you what your external IP address is.

It is also availible from running 

ifconfig in a terminal.

OK I feel really really stupid.  If I go to that external IP address in firefox it takes me to a configuration page and asks for a password.  I entered the password I use for everything (and the password I asked the guy who set up my ubuntu and gave me the router box that I have to use with it (my usb router box apparently didnt work with ubutnu??!) to use when he set up my computer) and it let me in showing me a web configuration thing.  It had some settings or "remote administration" and said it used port 80 and a custom port 25. So I think that it is my modem router that is giving me the open ports.  

I know this is off topic now but, do I need to "allow remote administration"? I wouldn't know what to do with it anyway.  Also I should say sorry to the people at [www.ictsc.com](www.ictsc.com) as it looks like their portscanner is OK, and their visibility thing is quite neat!, I think I will write them an email to explain what I thoughtt was going on.

---

### Post by DBStevens on 2007-07-20
Write your email to the portscanner folks, I'll send you a PM tomorrow, I'm heading to get some shut eye.

---

### Post by Chris S. on 2007-07-21
If you're connected through a router, wouldn't ifconfig only show the internal network address, not the external one?  I usually just go to my router's configuration (at [http://192.168.0.1](http://192.168.0.1) for my router, but it's different depending on the manufacturer/model) or go to a website like whatismyip.com to find my address.

And if you suspect you have a router with open ports at 25 and 80 (and it really shouldn't) then go to the router manufacturer's website or call them and look into configuring your router so they are closed to external traffic if possible.  Your computer is not at risk because of your router, but your router is.  It's not a big security issue that your router is exposed unless you do things like port forwarding or use it as a firewall.  The safer the better, but don't worry if you can't close those ports.

You won't need remote administration unless you feel like configuring your router while you are not connected to your home network, which is a bizarre thing to do for most home routers.

---

### Post by moochtastic on 2007-07-21
> **DBStevens said:**
> Write your email to the portscanner folks, I'll send you a PM tomorrow, I'm heading to get some shut eye.

Thanks - Much appreciated - Everyone that is.  

I think I am going to set aside a couple of weekends and start to work out how computers actually work rather than just trying to blindly use them.  

Many thanks to everyone who answered my questions (especially as it turns out it had nothing to do with ubuntu).  Thanks to whoever it is that provides ubuntu free of charge. Many thanks to the folks at [www.ictsc.com](www.ictsc.com) for providing that port scanner and visibility thingy.  Without being confused by what the results of those scans I wouldnt have gotten rid of my previous XP virus, nor would I have found the last virus I had and gotten in XP, and of course I wouldnt have installed ubuntu.  So in short, without those confusing tools at [www.ictsc.com](www.ictsc.com) I would never have had ubuntu installed, and without ubuntu I  would never have experienced all this helpful advice.  You guys have givne me the final push I need to actually get to know my computer so thanks all round.

All in all thanks you wonderful people!!  \\:D/

---

### Post by ebozzz on 2007-07-21
> **Chris S. said:**
> If you're connected through a router, wouldn't ifconfig only show the internal network address, not the external one? [COLOR="Red"] I usually just go to my router's configuration (at [http://192.168.0.1](http://192.168.0.1) for my router, but it's different depending on the manufacturer/model)[/COLOR] or go to a website like whatismyip.com to find my address.


Using Netgear?

---

