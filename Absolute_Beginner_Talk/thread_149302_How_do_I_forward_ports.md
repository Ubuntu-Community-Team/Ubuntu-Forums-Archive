---
title: "How do I forward ports?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by nickle on 2006-03-23
I would like to set up a public Netpanzer server. However, I have never done anything like this before. My machine is linked up to the internet via a cable router.

In the netpanzer FAQ it says:
"If you want to open a server, then you have to 		forward port 3030 TCP+UDP to your machine".

What does this mean exactly and how do I do this? 

I would be greatful for some simple advice...

---

### Post by echo $USER on 2006-03-23
You need to log into your router and forward all requests on port 3030 to the ip address of your server.

---

### Post by krusbjorn on 2006-03-23
[Portforward.com]("http://portforward.com/english/routers/port_forwarding/routerindex.htm") has great descriptions of how to forward ports for a lot of different routers.

---

### Post by IYY on 2006-03-23
By default, the router usually is at 192.168.0.1. Try going there in your browser to find the setting you need to change.

---

### Post by nickle on 2006-03-23
Thanks for the quick replies...

I have carried the instructions for my router correctly I think. Now how can I test whether it is working or not?

---

### Post by Azrael on 2006-03-23
[quote=nickle]Thanks for the quick replies...

I have carried the instructions for my router correctly I think. Now how can I test whether it is working or not?[/quote]
You could capture packets with ethereal and see if there is any traffic with destination port 3030 passing through, for example.

Note that when you configure your routing, you often need to configure both NAT and Firewall options.

---

### Post by dvarsam on 2006-03-23
[QUOTE=echo $user]

You need to log into your router and forward all requests on port 3030 to the ip address of your server.

[/QUOTE]

So, in my case (I want to setup an Apache Web Server)...
...I need to Forward my Router's:

Port 3030 -> Port 80

...for the Apache Web Server (to work)?

Does ALL Incoming internet trafic pass from Port 3030?

Thanks.

---

### Post by Azrael on 2006-03-23
[quote=dvarsam]So, in my case (I want to setup an Apache Web Server)...
...I need to Forward my Router's:

Port 3030 -> Port 80

...for the Apache Web Server (to work)?

Does ALL Incoming internet trafic pass from Port 3030?

Thanks.[/quote] no no no

The Netpanzer service used by the OP listens on port 3030, so all Netpanzer traffic has destination port 3030.

Webservers (normally) listen on port 80. So all web traffic (http) has destination port 80.

You must not change these port numbers, or you'll block legitimate traffic. What you need to do, is to tell the router which IP address belongs to your webserver. You usually do this by configuring your router's NAT (network address translator).

---

### Post by dvarsam on 2006-03-23
So, ALL I say to my Router is:

1. Forward all incoming traffic from Port 80 -> Port # (I am missing the number here)?
    What is the destination Port?

OR:

2. Just tell the Router to "Baptize" & Open up Port 80 (pointing where exactly – to a "/var/www/my_web_page" path)?

Sorry man, I am a total fruitcake on this...

Any ideas?

---

### Post by wsanders on 2006-03-23
You won't actually have a destination port; you have a port that you forward to a certain computer, i.e. the one you want to run the server. 

You need to find your computer's IP on your intranet. You can do this by going into your terminal on the computer and typing ifconfig. Whatever interface you're using to get on to the Internet will say something like inet addr:192.168.0.101 
or something like that. Depending on your router, you'll need to set the port number 3030 to forward to the section of digits (101 in the example above). I hope this helps; sorry if I'm not explaining this well.

---

### Post by Azrael on 2006-03-23
[quote=dvarsam]So, ALL I say to my Router is:

1. Forward all incoming traffic from Port 80 -> Port # (I am missing the number here)?
    What is the destination Port?
[/quote] The destination port is 80 as it always is. As I said, you don't change the port number.

You need to tell the router to forward all incoming packets (i.e. packets coming from the internet) with destination port 80 to the IP address of your computer within your LAN that is running Apache. This is called port forwarding or NAT. (In case your router has a firewall enabled which doesn't have port 80 open by default, you also need to add a rule to the firewall to explicitly open port 80)

---

### Post by Coelocanth on 2006-03-23
Think of the port as a highway called Route 80 and the IP of your server as the destination (call it Tropical Paradise). You want to reroute (forward) all the traffic from Route 80 to the Tropical Paradise (IP address).  Whenever something comes into your router from Route 80, you detour it to your Tropical Paradise. ;)

---

### Post by dvarsam on 2006-03-23
Thank you for your Reply.

According to the Internet site: [http://portforward.com](http://portforward.com), a PC MUST have a Static IP to function a a Web Server.

So, I performed the following steps (on my US Robotics 9107 ADSL Router):

_Part A – Setting Up a Static IP_:
To setup a Static IP on your PC, perform the following steps:

1. Launch a Browser's window & type "192.168.1.1".

2. Type in your Router's Username & Password to log into your Router.

3. Under the "LAN" Menu, select "DHCP Server".

    Note:
    You should see that:

    a. Your ADSL Router is assigned:

	1. IP address: 192.168.1.1
	2. Subnet Mask: 255.255.255.0

    b. ALL your PC's connected to the Router are (DHCP) assigned: 

	1. Start IP address: 192.168.1.2
	2. End IP address: 192.168.1.254
	3. Lease Time: 24 hours

4. Select "Disable DHCP Server" & click on the button named "Apply".
    Then click on the button named "Restart" (to Restart the Router).

5. Under the "LAN" Menu, select "Routing – ARP Table".

    Note:
    You can now see your PC's IP address: 192.168.1.2
    You will need to "type-in" this IP address later on...

_Part B – Opening your Ports to the Internet_:
To open your Port 80 to accept Internet Connections:

1. Under the "Security" Menu, select "Virtual Servers".

2. Under the "Select a service" list, select "Web Server (HTTP)"

    Note:
    The following settings will automatically be set:

	a. External Port Start: 80
	b. External Port End: 80
	c. Protocol: TCP
	d. Internal Port Start: 80
	e. Internal Port End: 80

3. Under the "Internal Server IP address:", type: 192.168.1.2
    (this is where I "typed-in" my PC's IP address)

4. Click on the button named "Apply".

    Note:
    When I did the above, I got the following message:
    "Since Port 80 is used, the router WEB server port will be moved to 8080".

5. Under the "Device" Menu, select "Restart" (to Restart the Router).


_PLEASE HELP_:
I do NOT know if I did everything right or wrong, but why did my Router said:

"Since Port 80 is used, the router WEB server port will be moved to 8080".

_Questions_:
1. Did I open the Ports (for my Apache) right? 
1. Who is using my Port# 80?
2. So now I have 2 Ports open (number 80 & number 8080)?
3. My IP address is "62.1.29.17". Can somebody visit me & tell me if you can See & Edit my Web Page (please tell me exactly what you see...)?
4. Is my computer vulnerable now?

Thank you for your help...

P.S.> Please do NOT hack in my computer...

---

### Post by dvarsam on 2006-03-23
[QUOTE=coelocanth]
...You want to reroute (forward) all traffic from Route 80 to the Tropical Paradise (IP address).
Whenever something comes into your router from Route 80, you detour it to your Tropical Paradise.
[/QUOTE]

I understand that my Router's traffic is Route 80.
I just did NOT understand what was the Tropical Paradise's Route #...

But I guess that:

My Router's traffic from Route/Port 80 is detoured to my Tropical Paradise's Port #80...

So it is: Router's Port 80 -> Internal LAN PC's Port 80...

Am I right on this?

Sorry, I was TOO fruitcake on this man.

Now, I am really worried about my questions on my previous post...

Thanks.

---

### Post by Azrael on 2006-03-23
> **dvarsam]
_PLEASE HELP_:
I do NOT know if I did everything right or wrong, but why did my Router said:

"Since Port 80 is used, the router WEB server port will be moved to 8080".
[/quote] Well, I am guessing WEB is your router's web-based interface tool which uses port 80 by default (because you configure it from your browser). So because your Apache computer is now claiming port 80, the router's WEB interface is relocated to port 8080 to prevent ambiguity (sp?) when dealing with packets coming from the internet. I'm not sure though, just guessing. Anyway, it's most likely normal behaviour of your router I think.
> 1. Did I open the Ports (for my Apache) right?
 Yes.
> 1. Who is using my Port# 80? Apache
>  2. So now I have 2 Ports open (number 80 & number 8080)? At least those two, yes. Though 8080 should only be reachable from your LAN and not from the internet.
>  3. My IP address is "62.1.29.17". Can somebody visit me & tell me if you can See & Edit my Web Page (please tell me exactly what you see...)? Yes. :cool:

This is what I see:

[IMG]http://img.photobucket.com/albums/v325/GODGOD/screendump.png[/IMG]
>  4. Is my computer vulnerable now? I'm doing a portscan on your IP. So far so good said:**
> P.S.> Please do NOT hack in my computer... No worries. You are not vulnerable as far as I can see. ;)
> So it is: Router's Port 80 -> Internal LAN PC's Port 80...

Am I right on this? Yes.

Oh, btw, isn't it like 05:08 AM in Greece right now? :-P

---

### Post by dvarsam on 2006-03-24
Dear "Azrael",

Thank you for your reply!!!

Yes, these are the contents of my "www/var" folder.

However, I want to tell "Apache" to show the contents of the file "test.php" & NOT to show its icon...

_Question 1_:
How can I do that?
Do I have to rename it to e.g. "test.index"?
Does the ".index" part tell apache to open it & show the contents?
Cause this is what I want to do...

My IP address has now been changed to "194.219.255.213".
You see, I have a NON Static IP account...

I had to Reset my Router & let me explain why...

When I posted my IP, I was kind of scared about how the security works with Apache...
I had not applied any settings or restrictions & I thought that maybe I was giving access to ALL my Ubuntu PC out there...& NOT just the "/var/www" folder.
Imagine how scary that was for me...

At the same time, I thought of launching a Page from Mozilla Firefox & typing my own IP (i.e. visiting my IP as if I were some stranger surfing in the Internet)...
As I typed it, I was redirected to my Router's page, asking me for my Router's Username & Password...
I typed them in & instead of looking into the stuff you posted with your PIC, I got into my Router's settings...
So, I thought that ALL of you people visitting my IP would probably see the SAME page, asking you for a username & password...
And you would NOT know what to type in...
At the same time even if you typed in a random username & password, you would not be able see the stuff you posted in your PIC, but you would get redirected to try out another username & password combination...
And if you got it correctly you could enter my Router's configuration...
I was scared with this thought in my mind...

So, I decided to close that Mozilla Firefox window, reload a new Browser window & type again my IP (the one I gave you).
Things got worse this time...
I was NOT asked for a username & password to log into my Router's configuration, and was redirected there straightforward...
Then I thought that if I can get inside my Router's configuration, without any passwork, right from my Mozilla Firefox & by only using the IP I provided to ALL of you, you could ALL, ALSO enter my Router's configuration freely...

....IF EVERYBODY has access to my Router's configuration FREELY & with NO username or password asked, my Ubuntu could turn out a "COME IN EVERYBODY & LETS PARTY HERE".
My heart-pulses started increasing exponentially...
IF everybody can access my Router, that is it...
...my Ubuntu will get haunted in NO time...

...and then I thought of my valuable files inside my Hard Drives...
What if some guy starts PARTYING by DELETING my Files...
I have spent 15 years of my life, creating those files...
Before end up getting a heart attack, I decided to reset my Router.
Since I do not have a STATIC IP, at least my IP would be different...
... and hopefully it will be less vulnerable, definately less vulnerable compared to having PUBLICLY announced my IP address...

That is why I changed my IP address!

_Question 2_:
Why was I seeing different stuff than what YOU guys were seing?

What is different when I am visiting my IP & when an outsider visits my IP.
How can I see what YOU see & access my Port 80 the way you do?

Please help...

Thanks.

---

### Post by nickle on 2006-03-25
Thanks for the initial comments, they help me set up my router (Ithink) now I would like to know how to check it.

However I feel much of the discussion (about a apache server) is way above my head and way above the level for this section of the forum.

I still have a some simple questions?
[LIST]
[*]How do I check which ports I "think" I have forwarded in my router?
[*]How do I forward ports in my firewall?[/LIST]I would be grateful for some beginner level advice

---

### Post by Alpha_toxic on 2006-03-25
I think this site can do it for you.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Here you can test everything.
If a port comes up as:
"stealth" - it's not forwarded
"closed" - probably it's forwarded through the router, but there is no app listening to that port on your comp
"open" - forwarded and your comp is listening to that port

The best result is if all ports come up as "stealth", except port 80 and the ones you have manualy forwarded through the router. They should be "open".

---

### Post by r0nin on 2006-03-25
[QUOTE=Alpha_toxic]I think this site can do it for you.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Here you can test everything.
If a port comes up as:
"stealth" - it's not forwarded
"closed" - probably it's forwarded through the router, but there is no app listening to that port on your comp
"open" - forwarded and your comp is listening to that port

The best result is if all ports come up as "stealth", except port 80 and the ones you have manualy forwarded through the router. They should be "open".[/QUOTE]

Isn't having open ports a security risk though? In my case I have 4 ports being forwarded for Bittorrent downloads. If I don't forward them I cannot connect. Is there no way round that?

---

### Post by dvarsam on 2006-03-25
Hello ALL !!!

I got NO answer to my question....

_Question 2_:
...Why was I seeing different stuff than what YOU guys were seing?

What is different when I am visiting my IP & when an outsider visits my IP.

HOW CAN I SEE WHAT YOU SEE & access my Port 80 the way you do?

Please help...

Thanks.

---

### Post by Alpha_toxic on 2006-03-25
[QUOTE=r0nin]Isn't having open ports a security risk though? In my case I have 4 ports being forwarded for Bittorrent downloads. If I don't forward them I cannot connect. Is there no way round that?[/QUOTE]
As long as only the p2p program is listening to the port and it works properly (doesn't have severe security flaws) there is nothing to worry about. It's better to use ports with numbers higher than 1100, even better if the number is 5 digit. AFAIK there is no way to go without forwarded ports.

@dvarsam: I don't know. I'm saying this so you don't think I'm intentionaly not answering or sth.

---

### Post by r0nin on 2006-03-25
[QUOTE=Alpha_toxic]As long as only the p2p program is listening to the port and it works properly (doesn't have severe security flaws) there is nothing to worry about. It's better to use ports with numbers higher than 1100, even better if the number is 5 digit. AFAIK there is no way to go without forwarded ports.
[/QUOTE]

Thanks mate, I've changed the ports to 5 digit ones. :)

---

### Post by dvarsam on 2006-03-25
>  @dvarsam: I do NOT know. I am saying this so you do NOT think I am intentionally NOT answering or something. 

No problem my friend, thanks for your help, anyway...

I really wonder though....

NOBODY in this Forum has Setup an "Apache" Web Server?

I read all these posts about setting up an "apache" & "php" & "mysql", but when it comes to simple questions.... simply... silence...

As if it some kind of "cryptic", "mystic", "voodoo" knowledge I am looking for... and I am a member of a "Mason's" community, asking for the BIG secret to reveal...?

It is impossible to think that NOBODY here has worked on Setting up Web Servers man!!!

come on, help me do a "little rowing" - hopefully we will win the big cup...

I am left doing the "rowing" alone man... it is quite lonely in this ocean...

My boat is sinking & it is pretty deep down there...

---

### Post by guysmiley on 2006-03-25
At one point, someone around here asked, "How do I see what you see" in reference to viewing your external IP address.  Aside from visiting your neighbor, goto [proxify.com]("http://www.proxify.com") or some similar free online proxy server and just type in your IP.

gs

---

### Post by dvarsam on 2006-03-27
[QUOTE=guysmiley]At one point, someone around here asked, "How do I see what you see" in reference to viewing your external IP address.  Aside from visiting your neighbor, goto [proxify.com]("http://www.proxify.com") or some similar free online proxy server and just type in your IP.
[/QUOTE]

Awesome suggestion man!!!

It really worked!!!

Because I also tried the:

[http://www.anonymizer.com/default.html](http://www.anonymizer.com/default.html)

And I got this:
Sorry! Anonymizer's Free Private Surfing limits access to the Web site you selected.
To gain protected access to ALL Web sites on the Internet, download our FREE 7 day trial.

So, do NOT assume that ALL Proxies out there can do it...

At least, with [proxify.com]("http://www.proxify.com"), you do NOT have to install anything in your PC!!!

Thanks again!!!

---

### Post by ritterrav on 2007-08-24
but if you said a cable modem, thats not a router, thus you need not forward anyports. Because i have a cable modem, for optimum online which directly connects me to the net, but with a router then i need a port forward not just with the cable modem.

---

