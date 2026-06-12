---
title: "firewalls"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-07
If I go a few days without a firewall while I learn more about ubuntu, am I likely to have any serious problem?  I have an always on connection with a cable modem, but there is nothing private on my computer.  I just installed a new hard drive, installed ubuntu and have placed no personal data on it.

---

### Post by taurus on 2007-01-07
There is already a build in firewall, iptables, running everytime (as default) you boot Ubuntu so I wouldn't worry too much about it.

---

### Post by Frak on 2007-01-07
There is already a firewall called iptables built in, the GUI frontent to control it is FireStarter, but most users don't need this.

---

### Post by tickmike on 2007-01-07
> **Frak said:**
> There is already a firewall called iptables built in, the GUI frontent to control it is FireStarter, but most users don't need this.

Hi .
My network is back of a smoothwall box  (firewall), do I need to turn off the iptables firewall to stop double NATing ?.
If so how ?. 

Michael

---

### Post by Frak on 2007-01-07
Shouldn't have to, but if you do install firestarter with this

```
sudo aptitude install firestarter
```

and use that to open all ports, if you need it, but it may be another program conflicting with NAT to make it do that.

---

### Post by steve.horsley on 2007-01-07
> **taurus said:**
> There is already a build in firewall, iptables, running everytime (as default) you boot Ubuntu so I wouldn't worry too much about it.

This is true but misleading. The default Ubuntu install leaves iptables in its default state of allowing averything. You need to take positive action in order to have the firewall block anything.

---

### Post by tc101 on 2007-01-07
-> The default Ubuntu install leaves iptables in its default state of allowing averything. 
-> You need to take positive action in order to have the firewall block anything.

OK, so what positive action should I take, and am I in much danger if I do nothing for a few days?  Remember I am a total beginner at this.

---

### Post by steve.horsley on 2007-01-07
> **tickmike said:**
> Hi .
My network is back of a smoothwall box  (firewall), do I need to turn off the iptables firewall to stop double NATing ?.
If so how ?. 

Michael

No you don't. In fact I think you would have to recompile the kernel to turn iptables off. It's part of the kernel. 

A few of points I'd like to make:

1) iptables is **the** linux firewall / packet filtering (and NAT) software. It's built into the kernel, and is always there. Its default state is to permit everything - as though it's not turned on. What it does is configured from the command line with rather tricky syntax commands.

2) A number of "firewall" GUI applications exist, and firestarter and guarddog seem quite popular. These all work by presenting a GUI to the user for simple configuratinon, and using command-line instructions to iptables behind the scenes to achieve the required effect. Many different control panels, but just one engine.

3) A default Ubuntu install (this is not true of all Linux distros) doesn't need an active firewall because it has no listening services that an intruder could try and connect to.

4) As far as I know, Linux doesn't have anything like the ability to restrict which applications are allowed to use the internet, such as I have seen on windows. I don't miss that ability actually - it is probably giving a false sense of security anyway.

---

### Post by steve.horsley on 2007-01-07
> **tc101 said:**
> OK, so what positive action should I take, and am I in much danger if I do nothing for a few days?  Remember I am a total beginner at this.

Sorry - to answer your original question, you need not take any special action. Unless you install a listening service sudh as an SSH server or web server, your machine will not accept incoming connections so cannot be got at. As soon as you install a service that listens for incoming connections, you need to review your firewall needs.

---

### Post by tickmike on 2007-01-07
Hello Steve and tc101
Steve thanks for info.  :) 

tc101, sorry for hijacking your post,
If you want a very secure hardware firewall you can download from   [http://www.smoothwall.org](http://www.smoothwall.org)
the software for free and use an old computer to build a very good (Linux based) firewall.
How do you connect to the internet ? do you have a firewall in your router that will protect you while you are testing for a few days ?.

Regards Michael.

Ps. Steve are you interested in space ..re your avatar

---

### Post by Lord Illidan on 2007-01-07
> 4) As far as I know, Linux doesn't have anything like the ability to restrict which applications are allowed to use the internet, such as I have seen on windows. I don't miss that ability actually - it is probably giving a false sense of security anyway.

Doesn't SELinux take care of that?

From : [http://en.wikipedia.org/wiki/Selinux](http://en.wikipedia.org/wiki/Selinux)
> 
[LIST]
[*]Clean separation of policy from enforcement
[*]Well-defined policy interfaces
[*]**Support for applications querying the policy and enforcing access control (EG crond running jobs in the correct context)**
[*]Independent of specific policies and policy languages
[*]Independent of specific security label formats and contents
[*]Individual labels and controls for kernel objects and services
[*]Caching of access decisions for efficiency
[*]Support for policy changes
[*]Separate measures for protecting system integrity (domain-type) and data confidentiality (MLS aka [Multilevel_security]("http://en.wikipedia.org/wiki/Multilevel_security"))
[*]Very flexible policy
[*]Controls over process initialization and inheritance and program execution
[*]Controls over file systems, directories, files, and open file descriptions
[*]Controls over sockets, messages, and network interfaces
[*]Controls over use of "capabilities"[/LIST]

---

### Post by Frak on 2007-01-07
nUbuntu would be great to run as a firewall, its made to be a server...

[http://www.nubuntu.org/](http://www.nubuntu.org/)

---

### Post by steve.horsley on 2007-01-07
> Ps. Steve are you interested in space ..re your avatar
I have a mild interest. I found the picture on NASA.gov. A real enthusiast would remember the name or the astronaut who's picture he stole though.

> **Lord Illidan said:**
> Doesn't SELinux take care of that?

From : [http://en.wikipedia.org/wiki/Selinux](http://en.wikipedia.org/wiki/Selinux)

Yes, it probably does, and more. I forgot that. I read about it once, and it's way advanced over anything windows could dream of.

---

### Post by tc101 on 2007-01-07
> 
Unless you install a listening service sudh as an SSH server or web server, your machine will not accept incoming connections so cannot be got at. As soon as you install a service that listens for incoming connections, you need to review your firewall needs.


Great news.  Does anyone disagree with this?  

I don't even know what an SSH server is.  I don't plan to install a web server.

I am just running firefox as a browser, evolution for email, using open office for a few things and that is about it.  So do I have to think about security at all with umbutu?  Are there any problems with viruses or spyware?

---

### Post by tc101 on 2007-01-07
> How do you connect to the internet ? do you have a firewall in your router that will protect you while you are testing for a few days ?

I connect with a cable modem through comcast.  We do have a router that is supposed to have a firewall but I have never been sure how or if it worked.  Until yesterday I was running windows and used zone alarm.

---

### Post by steve.horsley on 2007-01-08
> [QUOTE]Unless you install a listening service sudh as an SSH server or web server, your machine will not accept incoming connections so cannot be got at. As soon as you install a service that listens for incoming connections, you need to review your firewall needs.
Great news. Does anyone disagree with this?
[/QUOTE]
You are wise to ask. I would like to know if anyone disagrees, too.
> 
I don't even know what an SSH server is. I don't plan to install a web server.

Secure SHell allows remote logins, file transfers and command execution. All encrypted and authenticated, but there are password-guessing bots out there that do notihing but guess passwords all day long (and fill up your logs).
> 
I am just running firefox as a browser, evolution for email, using open office for a few things and that is about it. So do I have to think about security at all with umbutu? Are there any problems with viruses or spyware?

Viruses are not much of an issue (yet). You may want to install a scanner so you don't forward mails infected with Windows viruses between your windows friends though. Don't run untrusted software (especially unexpected email attachments). Linux is not so easy as Windows, but trojans do exist. If you're paranoid, check for rootkits occasionally, and chack the logs occasionally (although a good intruder will delete their own activity from logs).

---

### Post by tickmike on 2007-01-08
> **tc101 said:**
> I connect with a cable modem through comcast.  We do have a router that is supposed to have a firewall but I have never been sure how or if it worked.  Until yesterday I was running windows and used zone alarm.



Hi, what make and model of router is it ?.
Re ..ZoneAlarm its good used it for years before building my 'smoothwall' firewall.

---

### Post by Efwis on 2007-01-08
to date there are only approximately 40 Linux capable viruses made, adn my understanding is that most, if any, of them are not in the wild at this time. (i.e. built and stayed in the lab)

here is some more info in regards to that
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by tc101 on 2007-01-08
> Hi, what make and model of router is it ?.

Linksys Broadband Firewall Router model number BEFSX41

---

### Post by jkroto on 2007-01-08
> **steve.horsley said:**
>  Unless you install a listening service sudh as an SSH server or web server, your machine will not accept incoming connections so cannot be got at. 

To take it from another direction, what program, if any, can be used to see if anything is 'listening'??  
I use SSH so I know it's installed, but sometimes synaptic or apt-get can install dependencies that could be 'listening' and I don't know it.  Maybe not, but I don't know enough to know better, and I don't want to leave something open that shouldn't be.  Hope I'm making sense.

Anyway, any programs (or commands) that will show what might have open ears?  Suggestions?  Or is smoothwall/firestarter the answer to this as well?

Thanks.

---

### Post by Efwis on 2007-01-08
try Nessus. It's in the repos.

---

### Post by tickmike on 2007-01-08
Just looked your router up and you can access the firewall setting by using a web-browser-based configuration tool, to check if its turn on. It also said you have 24/7 help from linksys if you get stuck.

---

### Post by Frak on 2007-01-08
Then do that, sounds like how most routers work, because of compatability issues with OS's, with drivers and such, instead use a universal tool, and all OS's, in some way, have a web browser of some kind.

---

### Post by ubuntuuser on 2007-01-08
Nessus can be a bit tricky to set up if you're not sure what you're doing. You can also try nmap, which is, beside other things, a port scanner. To install nmap:```
sudo apt-get update
sudo apt-get install nmap

```

Then, to run nmap: ```
sudo nmap -sT -O localhost
```
This should get you an idea of what services are listening on your PC.

---

### Post by steve.horsley on 2007-01-09
This command will show you what's got what ports open:
**sudo netstat -plantu**

Anything listening on 127.0.0.1 is harmless as this address cannot be connected to from outside the machine.

---

### Post by jkroto on 2007-01-09
> **ubuntuuser said:**
> Nessus can be a bit tricky to set up if you're not sure what you're doing. You can also try nmap, which is, beside other things, a port scanner. To install nmap

[QUOTE=steve.horsley]This command will show you what's got what ports open:
sudo netstat -plantu

Anything listening on 127.0.0.1 is harmless as this address cannot be connected to from outside the machine.[/QUOTE]

Thanks to you both and Efwis for the suggestion.  I looked at Nessus and instantly realized it would probably take me years to figure out how to use it.  

This is the greatness of Ubuntu/Linux, a program that robust.. and in the repo's.  If it was for work purposes I might try it, but for home it seems like overkill.  Why use a battleship when a handgun is all I need?  But hey, it's there if I want it, that's the best part.

Thanks again to all.

---

