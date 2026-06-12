---
title: "Some extreme newbie questions"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Iniamyen on 2006-07-25
Not about computers, per se, but about servers specifically. I have access to some older boxes, and I was thinking about installing Linux on one of them, hooking it up to my home network, and using it to store music, movies, web pages, etc etc...

My main question concerns using it as a space for storing web pages (this is what the term "webserver" means, right?) I'm not sure what this would even entail. Do I need to buy a domain name in order to create a web page which isn't tied to storage space on some other computer? I'm fairly experienced creating web pages, but I've always done it using files on some remote computer, so the domain name was something else. The inner workings of it all remain a mystery to me.

Basically, I'd just like to be able to access files on this computer from both inside and outside my network. And being able to access webpages from it would be cool too. Is Ubuntu (server version) the right OS to use for this type of application?

I apologize in advance if my question is poorly-worded. I don't have much experience when it comes to networking, so I can't really convey my thoughts that easily. I'm fairly experienced when it comes to other aspects of hardware and software, though, so hopefully I can clarify if need be.

Thanks!

---

### Post by Ben Armston on 2006-07-25
A webserver is slightly more than just a place to store webpages. You also need to have a program on the system that will send those webpages to the webbrowser that has requested them. The most popular such program is called Apache, and documents about installing it can be found on the wiki [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=apache&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=apache&titlesearch=Titles)

To serve the files to the computers on your own network you will want to have either Samba or NFS. NFS  is the best choice if all your other machines are Linux or Unix machines. But if you are using Windows on them then you will need to use Samba.

For NFS read the server and client pages here [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nfs&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nfs&titlesearch=Titles)

For Samba look at [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
you will also need to do some work on the Windows machines. But I can't help you with that.

Ubuntu is a good choice to use for this idea.

If you are going to allow computers outside of your network to access your web / file server you will need to consider security. A strong firewall is the absolute minimum.

---

### Post by richbarna on 2006-07-25
> **Iniamyen said:**
> I have access to some older boxes, and I was thinking about installing Linux on one of them, hooking it up to my home network, and using it to store music, movies, web pages, etc etc...

Thanks!

If you are thinking of having a server on your network, you might want to use one of those old boxes as a stand-alone firewall.

I use [IPCop]("http://ipcop.org/"), it's secure and easy to setup. It's also a great way to learn more about network traffic and security.

---

### Post by Iniamyen on 2006-07-25
Thanks for the replies. To clarify-

All of the other computers on my network (at this point) will be Windows machines.

I already have a router between my internet connection and my other machines - Isn't this a firewall? I'm getting the sense that allowing outside users onto a computer inside of the network is the difference between a router and another computer being the "firewall." But I'm not sure.

Also, I have cable internet (Comcast) and I know very little about my IP address, whether it's static or dynamic. I would assume it's dynamic (most from ISPs seem to be), so is there a way to host a web page with this kind of limitation?

---

### Post by Ben Armston on 2006-07-25
Being precise for a moment:

A router is a machine which sends network messages (packets) to the correct machine. A firewall is a machine which decides if network packets can pass through it. In practice, most (all?) home routers are also firewalls. Logon to your router, presumably  it has a web interface, and check whether it offers firewall options.

If you have no servers on your network, the safest thing for your firewall to do is prevent all packets, that have not been requested by you, from entering the network.  Once you have a server you need to allow certain packets through the firewall, so you need to take extra measures to prevent damage should something bad happen. Search [www.tldp.org](www.tldp.org) for security HOWTOs.

You can still have a network without a static IP address, it just gets more complicated. Check out [www.dyndns.com](www.dyndns.com) or Google for dynamic dns.

---

### Post by richbarna on 2006-07-25
Depending on what you have on your server, using Ipcop can completely isolate your server from the internal network, which means that if it get's compromised, your other machines are safe.

At the moment being behind a router is pretty secure, but it's better to be safe than sorry. I just thought it would be good to use one of those spare boxes.

As for hosting on a dynamic IP, as long as your router/ server is always turned on, you keep the same IP. If you register a domain name, you can just update the IP ([there are free services that do this]("http://www.google.es/search?hl=en&q=Free+domain+name+redirection&btnG=Google+Search")), but obviously static is better.

---

### Post by Iniamyen on 2006-07-25
Thanks for the references, I'm going to look over those after work today. I'm sure I'll post back tomorrow with other questions, but I can think of a couple quick ones off the top of my head:

If I have a server on my network, which is hooked up to my router, and the router is the machine connected to the ISP, what the heck is my actual IP address, i.e., the one that other people would use to connect to that machine? I know it's hidden (by the ISP?) and then I get a generic one, like 192.168.1.1, 192.168.1.2, etc... from within my network, but what is it from outside the network?

If my server is going to be the only Linux machine for awhile (as I get used to it), can you use GUIs with the server version of Ubuntu? From what I've been reading, the server version is command-line oriented, but is it pretty easy to get a GUI implemented and start using GUI applications as with a desktop machine?

Thanks a lot for the help!

---

### Post by ubuntuuser on 2006-07-25
> **Iniamyen said:**
> My main question concerns using it as a space for storing web pages (this is what the term "webserver" means, right?) 
One of the most often used web servers is apache. you can install it with synaptic. I'm sure you will find a lot of material all over the web on how to configure it.
> **Iniamyen said:**
> 
I'm not sure what this would even entail. Do I need to buy a domain name in order to create a web page which isn't tied to storage space on some other computer?
No, you don't need to buy a domain name, but it would make life much more comfortable. Every time you switch on your modem/router at home, your ISP assigns you an IP address. That IP identifies you all over the web. The problem is that it most likely always a different one. Without a domain name, whoever wants to visit your site needs to know the IP in order to connect to your server. Another option, beside buying a domain name, is a service called Dynamic DNS. Have a look [here]("http://directory.google.com/Top/Computers/Software/Internet/Servers/Address_Management/Dynamic_DNS_Services/"). 

> **Iniamyen said:**
> Basically, I'd just like to be able to access files on this computer from both inside and outside my network
Search for Samba to share files inside your local area network. For accessing files on this server from the outside, I would recommend SecureFTP, also called sFTP. I recommend that you do some research on SSH, Secure Shell, as well.
> **Iniamyen said:**
> Is Ubuntu (server version) the right OS to use for this type of application?
Ubuntu Server is in no way different from regular ubuntu, they all access the same repositories, for example. But the server version only installs the packages that are absolutely necessary, you won't get a graphical interface by default, you'd have to install it seperately, but usually you don't need one on a server. I think I read somewhere that the server versions already installs some server specific software, but I'm not sure about that. Maybe somebody else could elaborate on that?
> **Iniamyen said:**
> I apologize in advance if my question is poorly-worded. I don't have much experience when it comes to networking, so I can't really convey my thoughts that easily. I'm fairly experienced when it comes to other aspects of hardware and software, though, so hopefully I can clarify if need be.Just don't feel intimidated by the topic. If you are interested in learning about the nuts and bolts of networking, I can highly recommend the book "TCP/IP Guide" by Charles Kozierok.

One more thought: You said that you had some box_es_ available. You should really think about setting up another PC as a router/firewall if you plan to make your server accessible from outside. You're right, that little box between your net and the www is (probably) a combined router/firewall/NAT device, maybe even more. But if you really want to control what happens inside your net, IPcop is definitely worth a look. There are loads of different firewalls available for free, but I like IPcop.

---

### Post by ubuntuuser on 2006-07-25
I should have been a little faster with my reply, hm? :-D
> **Iniamyen said:**
> 
If I have a server on my network, which is hooked up to my router, and the router is the machine connected to the ISP, what the heck is my actual IP address, i.e., the one that other people would use to connect to that machine? I know it's hidden (by the ISP?) If the IP your ISP provided was hidden, you would be unable to communicate over the internet, because the other side wouldn't know where to send the packets. Have a look [here]("http://whatismyip.com") to find out your IP. But as I said before, it will change every time you switch on your modem.
> **Iniamyen said:**
> 
and then I get a generic one, like 192.168.1.1, 192.168.1.2, etc... from within my network, but what is it from outside the network? See the link that I provided above to find that out. There are several IP ranges, that are reserved for private use. One of these ranges is 192.168.0.0/16. Internet routers simply drop packets from or to those addresses, so they are only valid in LANs.
> **Iniamyen said:**
> If my server is going to be the only Linux machine for awhile (as I get used to it), can you use GUIs with the server version of Ubuntu? From what I've been reading, the server version is command-line oriented, but is it pretty easy to get a GUI implemented and start using GUI applications as with a desktop machine?
To install Gnome, type ```
sudo apt-get install ubuntu-desktop
```If you want XFCE, it should be xubuntu-desktop, and for KDE kubuntu-desktop.

> **Iniamyen said:**
>  Thanks a lot for the help!Welcome  to the wonderful world of networking. I forgot to mention that you should also do some research on Network Address Translation (NAT) and port forwarding.

---

