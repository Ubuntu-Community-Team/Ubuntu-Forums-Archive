---
title: "Port control"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Learn!ng on 2007-08-09
Hello i like kubuntu ,,, but is there an application to properly control port access for it?

---

### Post by Learn!ng on 2007-08-09
i didn't read the rules... am i allowed to bump or is it best to wait for 24 hours?

---

### Post by splintercellguy on 2007-08-09
Port access? Like networking? If so, Linux comes with an integrated iptables firewall. If you want a GUI way to configure it, use Firestarter. sudo apt-get install firestarter.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Port access? Like networking? If so, Linux comes with an integrated iptables firewall. If you want a GUI way to configure it, use Firestarter. sudo apt-get install firestarter.

you mean it comes with a built in firewall out of the box?  and firestarter is used to configure it (thx for the sudo cmd btw)?  

are the defaults considered secure... or are there recommended changes to lock down a system?
is it considered a secure fw?  does it pass leaktests... does it lock down the ports porperly?

---

### Post by splintercellguy on 2007-08-09
A lot more secure than Windows. See [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) for a discussion and possible tips. A note on sudo. If you are planning to try to run GUI apps with sudo, use gksudo instead, else you may screw up permissions for some files. Yes, iptables is very much secure. If there was a way to breach the firewall in lieu of the set iptable rules, then I'm sure the Linux devs would quickly create a patch.

---

### Post by Learn!ng on 2007-08-09
ok thx for the info... :)

just wondering before i installed firestarter was the fw operational?
how do i check to make sure i have disabled remote connections and blocked the ports properly?

is there a more secure firewall or an alternative to iptables?

also do you use any of these applications: [http://doc.gwos.org/index.php/SecurityAnalysis](http://doc.gwos.org/index.php/SecurityAnalysis)
and how do i download with gksudo (only started kubuntu a few days ago)

---

### Post by splintercellguy on 2007-08-09
You can try visiting a number of websites that let you port probe, such as ShieldsUp!: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) (I wouldn't buy the crappy rhetoric, but the probing works for me). AFAIK iptables is THE firewall for Linux, and I see no reason to go elsewhere.

---

### Post by Learn!ng on 2007-08-09
ok i am suspicious after building my own port analysis app for windows ;)
pls...how can i install Knocker or pnscan with gksudo?

---

### Post by R_U_Q_R_U on 2007-08-09
> **Learn!ng said:**
> ok thx for the info... :)

just wondering before i installed firestarter was the fw operational?
how do i check to make sure i have disabled remote connections and blocked the ports properly?

is there a more secure firewall or an alternative to iptables?

From psychocats: "By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited."

I think that answers what you are asking...

---

### Post by Learn!ng on 2007-08-09
> **R_U_Q_R_U said:**
> From psychocats: "By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited."

I think that answers what you are asking...

are you sure abt that? even having open ports doesn't compromise security btw... only if there is a app waiting to receive cmds from outside

---

### Post by splintercellguy on 2007-08-09
Why don't you see for yourself by scanning your Ubuntu machine on another computer? And you can find those two tools in the repositories: System -> Administration -> Synaptic Package Manager. Keep in mind that you have to do the scan from a different machine.

---

### Post by R_U_Q_R_U on 2007-08-09
> **Learn!ng said:**
> are you sure abt that? even having open ports doesn't compromise security btw... only if there is a app waiting to receive cmds from outside

I am not a security expert; however, please read this description of security to see if it  more fully addresses your concerns:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Why don't you see for yourself by scanning your Ubuntu machine on another computer? And you can find those two tools in the repositories: System -> Administration -> Synaptic Package Manager. Keep in mind that you have to do the scan from a different machine.

well you see the problem what if there is a single port that can be connected to and accepts cmds then security is over,,, so being able to monitor every port and see what it is doing is best... i was hoping to be able to continously monitor every port,,, and if it shows which app is using it then even better.. then if it includes trace utility for outgoing traffic then well you are on the offensive not the defensive :D

btw i couldn't find the System -> Administration  menu?

---

### Post by HereInOz on 2007-08-09
The iptables firewall is enabled by default, as an inbound firewall.  Once you install Firestarter you will be able to see that the outbound protection is turned off.  With a properly secured Linux system, it is highly unlikely that you will acquire something that will "phone home" so to speak.

So, it is my understanding that, no, the firewall as it is installed would not pass a Steve Gibson leak test, and given that it is a port blocking firewall, rather than an application blocking firewall like Zone Alarm, it is relatively difficult to close it down for outbound applications.  There are many Windows firewalls in this position as well.

I must confess that I like the ability of Zone Alarm to grant specific outbound access to an application, rather than by port number, but the iptables firewall is a port blocker, not an application blocker.  So if you closed down the firewall to outbound traffic, and just opened port 80 for your web traffic, your browser would be able to access the internet, but so would any other application using port 80.

You would then need to open ports for all the other apps which need access to the internet.

You can, however, blacklist ports which are being used by applications which you do not want to have access, but you must first find what ports are being used by which applications.

Hope this is helpful.

---

### Post by Learn!ng on 2007-08-09
> **R_U_Q_R_U said:**
> I am not a security expert; however, please read this description of security to see if it  more fully addresses your concerns:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
thx again.. i read it... but he doesn't seem too sure abt everything????

---

### Post by splintercellguy on 2007-08-09
Ah, you're Kubuntu. I dunno what the equivalent menus are for you, but let's go command line (one command per line):

sudo -s
synaptic

And IMHO, I don't see ANY reason to have to monitor each and every single app and all their traffic. If you're interested in sniffing traffic, there's always Wireshark.

---

### Post by HereInOz on 2007-08-09
Trust me, (I'm from the government - I'm here to help you :-))  

The firewall in (K)Ubuntu has all inbound ports closed by default.  It will respond to a ping request unless you enable ICMP filtering (using Firestarter is the easiest).  Once you enable ICMP filtering, and block response to a ping, the machine will be fully stealthed, unless you deliberately open a port.

---

### Post by Learn!ng on 2007-08-09
> **HereInOz said:**
> The iptables firewall is enabled by default, as an inbound firewall.  Once you install Firestarter you will be able to see that the outbound protection is turned off.  With a properly secured Linux system, it is highly unlikely that you will acquire something that will "phone home" so to speak.

So, it is my understanding that, no, the firewall as it is installed would not pass a Steve Gibson leak test, and given that it is a port blocking firewall, rather than an application blocking firewall like Zone Alarm, it is relatively difficult to close it down for outbound applications.  There are many Windows firewalls in this position as well.

I must confess that I like the ability of Zone Alarm to grant specific outbound access to an application, rather than by port number, but the iptables firewall is a port blocker, not an application blocker.  So if you closed down the firewall to outbound traffic, and just opened port 80 for your web traffic, your browser would be able to access the internet, but so would any other application using port 80.

You would then need to open ports for all the other apps which need access to the internet.

You can, however, blacklist ports which are being used by applications which you do not want to have access, but you must first find what ports are being used by which applications.

Hope this is helpful.

yes that is info and ideas... becos the browser is listening on 80 unless the browser was also designed as a trojan they couldn't gain access to your pc... the webbrowser would effectively plug port 80... well then closed source browsers could be an issue :)

yes montior ports and trace tools ideal for blacklisting ports and applications.

---

### Post by splintercellguy on 2007-08-09
Your knowledge of security seems misguided and well-informed. Browsers, which are clients, do not LISTEN on any port. There's no reason to; they're not servers. They connect to a web server that listens on port 80, but the browsers themselves do not listen on such ports. When a client makes a connection, the connection socket first binds to a port > 1024, then sends a connection request to the server on whatever port.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Your knowledge of security seems misguided and well-informed. Browsers, which are clients, do not LISTEN on any port. There's no reason to; they're not servers. They connect to a web server that listens on port 80, but the browsers themselves do not listen on such ports. When a client makes a connection, the connection socket first binds to a port > 1024, then sends a connection request to the server on whatever port.

yes... but where is the security risk with a browser?

---

### Post by Learn!ng on 2007-08-09
> **HereInOz said:**
> Trust me, (I'm from the government - I'm here to help you :-))  

The firewall in (K)Ubuntu has all inbound ports closed by default.  It will respond to a ping request unless you enable ICMP filtering (using Firestarter is the easiest).  Once you enable ICMP filtering, and block response to a ping, the machine will be fully stealthed, unless you deliberately open a port.

i hope you jking with me abt the govt... :D

---

### Post by splintercellguy on 2007-08-09
A browser may access a page containing an XSS exploit, there may be a bug in plugins, countless ways I can think of. Security isn't just about the network. And my response was a reply to what you said here:

> yes that is info and ideas... becos the browser is listening on 80 unless the browser was also designed as a trojan they couldn't gain access to your pc... the webbrowser would effectively plug port 80... well then closed source browsers could be an issue 

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Ah, you're Kubuntu. I dunno what the equivalent menus are for you, but let's go command line (one command per line):

sudo -s
synaptic

And IMHO, I don't see ANY reason to have to monitor each and every single app and all their traffic. If you're interested in sniffing traffic, there's always Wireshark.

why not monitor what your pc is giving to others ;)

i need to get this sudo and package download thingy sorted... can you pls explain how to get a list of app on the server and the protocol to download them?

---

### Post by splintercellguy on 2007-08-09
What is sudo? Basically it lets you run a command with root privileges. If you want to run a GUI app that way, you have to use gksudo/kdesu. As for Synaptic, press Refresh and search for whatever package you want?

---

### Post by HereInOz on 2007-08-09
Correction: A browser does not listen on port 80.  It uses port 80 to access the internet, but it does not listen on port 80.  It is only server applications which listen on a port.

If you have no firewall, all ports will show, from an internet scan perspective, as Closed, unless there is a server application listening on that port, then the port will scan as Open.

When you activate the firewall, the applications which are listening on the ports are still there, listening furiously, but there is nothing to hear, because the firewall is stopping it.  All ports will then scan as non-existent, unless you direct the firewall to open them.  They will then show as Closed or Open, depending on whether something is listening on that port or not.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> A browser may access a page containing an XSS exploit, there may be a bug in plugins, countless ways I can think of. Security isn't just about the network. And my response was a reply to what you said here:
rly? if the browser has no anger, where is the risk with the port it uses?

---

### Post by splintercellguy on 2007-08-09
> **Learn!ng said:**
> rly? if the browser has no anger, where is the risk with the port it uses?

I am totally not comprendering your response. Anger, where did that come from? You asked about security risks, and I mentioned a few. Ports don't have anything to do with it.

---

### Post by Learn!ng on 2007-08-09
> **HereInOz said:**
> Correction: A browser does not listen on port 80.  It uses port 80 to access the internet, but it does not listen on port 80.  It is only server applications which listen on a port.

If you have no firewall, all ports will show, from an internet scan perspective, as Closed, unless there is a server application listening on that port, then the port will scan as Open.

When you activate the firewall, the applications which are listening on the ports are still there, listening furiously, but there is nothing to hear, because the firewall is stopping it.  All ports will then scan as non-existent, unless you direct the firewall to open them.  They will then show as Closed or Open, depending on whether something is listening on that port or not.

so a browser gets data on 80 and sends requests on another...got it.. still i don't see the risk unless closed source plugin or browser has an opening on purpose.

yes i like your explain abt the apps and the ports...so the fw sits between the apps and the ports and can allow or stop communications... a great one would be an asset if it completely covers all comms on all ports and links to apps as well.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> I am totally not comprendering your response. Anger, where did that come from? You asked about security risks, and I mentioned a few. Ports don't have anything to do with it.
sry... not meant to confuse... i mean the browser just sends and gets data.. unless there is a nasty hook (anger) in the code somewhere any comms on the browser ports will be safe :D

---

### Post by splintercellguy on 2007-08-09
Networking is only one part of security. Problems can happen if programs do not handle invalid/unexpected data properly, aka the billion buffer-overrun exploits out there. See [http://en.wikipedia.org/wiki/Cross-site%20scripting](http://en.wikipedia.org/wiki/Cross-site%20scripting), [http://en.wikipedia.org/wiki/Buffer%20overrun](http://en.wikipedia.org/wiki/Buffer%20overrun), and [http://larholm.com/2007/07/10/internet-explorer-0day-exploit/](http://larholm.com/2007/07/10/internet-explorer-0day-exploit/) for an example of bugs that don't necessarily involve ports. As for links to apps, did you look in the repos?

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Networking is only one part of security. Problems can happen if programs do not handle invalid/unexpected data properly, aka the billion buffer-overrun exploits out there. See [http://en.wikipedia.org/wiki/Cross-site%20scripting](http://en.wikipedia.org/wiki/Cross-site%20scripting), [http://en.wikipedia.org/wiki/Buffer%20overrun](http://en.wikipedia.org/wiki/Buffer%20overrun), and [http://larholm.com/2007/07/10/internet-explorer-0day-exploit/](http://larholm.com/2007/07/10/internet-explorer-0day-exploit/) for an example of bugs that don't necessarily involve ports. As for links to apps, did you look in the repos?

thx... will read in a sec... but if you have complete control of the ports then you win

ah yes i see what you are talking abt... 

Type-0, 1, 2 that could be a problem if code from downloaded pages are able to access the machine...  and yes i am suspicious of sites that require a cookie ever.

---

### Post by splintercellguy on 2007-08-09
Not necessarily. If you download something and run it, whether you have a firewall or not won't make much of a difference if that app is infected.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Not necessarily. If you download something and run it, whether you have a firewall or not won't make much of a difference if that app is infected.

yes i thought web languages were crippled and used for display purposes and stopped access to the rest of pc...  leaving to one side closed source plugin and addins?

---

### Post by splintercellguy on 2007-08-09
> **Learn!ng said:**
> yes i thought web languages were crippled and used for display purposes and stopped access to the rest of pc...  leaving to one side closed source plugin and addins?

Huh? Totally confused. I'm not necessarily talking about web browsers, and my discussion shouldn't totally apply to them. Let's say you download a program that wipes out your hard drive. No firewall will stop you from running such an app. These days, with JavaScript/Flash/AJAX, you can definitely get bitten by visiting a web page with an unsafe browser. Read the aforementioned links I mentioned.

---

### Post by steve.horsley on 2007-08-09
A few points:

The default Ubuntu install has no open ports that a remote machine could connect to and exploit (it has a few ports that are open to connections fom the same box, listening on 127.0.0.1). MyYou can see the listening ports and applications with a command like:
**sudo netstat -laput**
Correction - My DHCP client seems to be listening on port 68 for DHCP responses.

If your machine has already been rooted, you cannot trust netstat or any other utilities to tell you the truth - they will probably have been modified to hide the evidence.

This is **NOT** because iptables has closed the ports, it is because no applications are listening. The default setting for iptables is to allow everything, both incoming and outgoing. If you install an app that listens for incoming connections, then you also need to think whether you should configure iptables to limit who can connect to that app. Youcan see what iptables filters are currently active with the command:
**sudo iptables -L**
and iptables with no filtering looks like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Using the firewall to prevent incoming connections to applications that you don't know are listening is perhaps not overly useful. If there are applications that you didn't know about running on the machine, then you are already walking on thin ice. You may feel you want to protect your other users from beingn compromised when they (perhaps unwittingly) run apps with inbuilt servers though. If you do block access to your users apps, be prepared to deal with complaints that p-p apps, games etc. don't work.

I speak only for Ubuntu Desktop - other variants like Kubintu or Server may have different defaults.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Huh? Totally confused. I'm not necessarily talking about web browsers, and my discussion shouldn't totally apply to them. Let's say you download a program that wipes out your hard drive. No firewall will stop you from running such an app. These days, with JavaScript/Flash/AJAX, you can definitely get bitten by visiting a web page with an unsafe browser. Read the aforementioned links I mentioned.

i am reading... thx for link!

i agree... there is no way to completely protect against bomb/virus attacks but main thing for me anyway is to stop pc being accessed controlled and sending info back to external ip so that i can do banking for example with no worries.

---

### Post by Learn!ng on 2007-08-09
> **steve.horsley said:**
> A few points:

The default Ubuntu install has no open ports that a remote machine could connect to and exploit (it has a few ports that are open to connections fom the same box, listening on 127.0.0.1). MyYou can see the listening ports and applications with a command like:
**sudo netstat -laput**
Correction - My DHCP client seems to be listening on port 68 for DHCP responses.

If your machine has already been rooted, you cannot trust netstat or any other utilities to tell you the truth - they will probably have been modified to hide the evidence.

This is **NOT** because iptables has closed the ports, it is because no applications are listening. The default setting for iptables is to allow everything, both incoming and outgoing. If you install an app that listens for incoming connections, then you also need to think whether you should configure iptables to limit who can connect to that app. Youcan see what iptables filters are currently active with the command:
**sudo iptables -L**
and iptables with no filtering looks like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Using the firewall to prevent incoming connections to applications that you don't know are listening is perhaps not overly useful. If there are applications that you didn't know about running on the machine, then you are already walking on thin ice. You may feel you want to protect your other users from beingn compromised when they (perhaps unwittingly) run apps with inbuilt servers though. If you do block access to your users apps, be prepared to deal with complaints that p-p apps, games etc. don't work.

I speak only for Ubuntu Desktop - other variants like Kubintu or Server may have different defaults.

when you say  The default setting for iptables is to allow everything, both incoming and outgoing... are there any server or networking services vpn etc that could be accessed from an external source?

---

### Post by splintercellguy on 2007-08-09
Um...no. As the link mentioned earlier, Ubuntu does not expose any services by default.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Um...no. As the link mentioned earlier, Ubuntu does not expose any services by default.
 

yes but steve makes an interesting point about default install... if it isn't locked down at the start.. then everything else is a waste of time ;) unless you can install the apps to secure offline before going online.

---

### Post by splintercellguy on 2007-08-09
But it is locked down, unless you mean unplugged from the Internet. Nothing is listening, so what can an attacker connect to?

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> But it is locked down, unless you mean unplugged from the Internet. Nothing is listening, so what can an attacker connect to?

not sure.... discussing to find out if there is something that could be accessed by clever ppls....

what if i downloaded whole cd with firestarter or guarddog and turned it on before going online? (i only downloaded base 2 days ago and got the rest from the net) but some ppl have realised that firewall may not be leakproof either...

thats why i asked about other options with firewalls too :D

---

### Post by splintercellguy on 2007-08-09
You're overthinking this. You are perfectly safe.

---

### Post by Learn!ng on 2007-08-09
what did you do at the start splintercellguy.... did you base it or do the whole cd and did you firestart before webbing at all?

---

### Post by splintercellguy on 2007-08-09
Not sure what you mean by CD, but I just installed Ubuntu and used the web. No firewall tweaking. Firestarter is just a GUI for iptables.

---

### Post by Learn!ng on 2007-08-09
> **splintercellguy said:**
> Not sure what you mean by CD, but I just installed Ubuntu and used the web. No firewall tweaking. Firestarter is just a GUI for iptables.

and you feel safe?

oh sry.... the cd = largest iso image <> base iso image

---

### Post by splintercellguy on 2007-08-09
Absolutely. Don't go to porn sites or give away personal info.

---

### Post by Learn!ng on 2007-08-09
thx to everyone for comments... will read and think abt it... :)

---

### Post by steve.horsley on 2007-08-09
You are safe from attack by network connection unless you install something that listens for connections. And you can only install firestarter over the internet - it's not on the CDs. But it's safe to go online unless you install a service first because there is **nobody listening** to all those attacks. I still don't run a firewall (though I have configured my home SSH service to only accept connections from my workplace). I feel safe.

I think you are being overly cautious. The time for that is when you decide to install a listening service. SSH is easy - only allow connections from known safe places (like work). A web server is a lot harder - you need to accept connections from anywhere (so a firewall doesn't really help), and you are only as safe from compromise as your web server is. Are you sure that's impenetrable?

---

