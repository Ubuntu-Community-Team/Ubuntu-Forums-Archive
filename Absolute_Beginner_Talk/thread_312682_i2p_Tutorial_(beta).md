---
title: "i2p Tutorial (beta)"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-12-04
Since there's no i2p tutorial and i've been ](*,) for some time, here's a tutorial, but if someone knows a better one, feel free to post

> Scalable anonymity with I2P

Monday September 18, 2006 (02:01 PM GMT)

By: Leslie P. Polzer

The Invisible Internet Project (I2P) is a work in progress whose aim is to provide a secure version of the IP protocol that addresses threats common to the standard TCP/IP networking infrastructure -- most importantly, the effortless identification and tracking of participating peers.

In I2P, each participating peer keeps a secret pool of inbound, or data-receiving, and outbound, or data-transmitting, tunnels it chooses itself. A tunnel consists of a configurable number of routers in sequence, where longer tunnels mean more anonymity, at the expense of performance. When a peer sends data, it is passed through one of its outbound tunnels, at the end of which it enters an inbound tunnel of the recipient. For each router that is part of the chosen tunnel, a layer of encryption based on the router's key is added. This technique, the main feature of "onion routing," prevents compromised routers from eavesdropping. (The most well-known onion routing project, Tor, is more efficient than I2P and more friendly for low-bandwidth peers, but not as flexible an application as I2P and not as good a dynamic threat defense.)

I2P uses what it calls "garlic routing," which enhances onion routing by allowing a message to take multiple paths at once, therefore increasing message integrity. For more information on these routing techniques, refer to this excellent paper.

Addresses, or destinations, in I2P consist of a set of cryptographic keys which are Base64-encoded when used in an ASCII context. In contrast to the TCP/IP and UDP/IP protocols, addresses point to services, not hosts. It is harder to identify which services a certain host is running than to identify a given host, and addresses do not change when services are migrated to another server.

Names in the I2P network are of the form NAME.i2p (comparable to ADDRESS.onion in the Tor anonymous network). Name resolving is currently in its infant stage, and the direction it will take before the project reaches 1.0 release is not clear. At the present time, every peer may offer destination-to-name translation by keeping a text file database of NAME: DESTINATION pairs. Users may then "subscribe" to the databases they would like to use, which instruct their I2P routing software to download updates of those databases regularly.

Running it

As I2P is under heavy development, you have to be lucky to get a package for your favorite distribution. For example, Ubuntu Dapper does not have one, but Arch Linux does. If you cannot get a package, the best way to install is by using the GUI installer from the I2P Web site.

When the download has completed, the command
java -jar i2pinstall.exe

will install the I2P routing software and eventually start it, which will make you a part of the I2P network. Don't worry, this does not expose you to any dangers. You may start and stop I2P with the command i2prouter, which is found in the installation directory. If you are behind a firewall, you must allow incoming UDP traffic on ports 8887 and 123. If, additionally, you are behind a router that does network address translation for you, instruct it to relay traffic on these ports to the machine on which i2prouter is running. After that, you may tweak the configuration of your new I2P router by pointing your favorite Web browser at [http://localhost:7657/](http://localhost:7657/). On that page you will also find a lot of links to help you explore the world of I2P.

Hints:

    * To get started browsing .i2p Web pages, configure your browser to use localhost:4444 as an HTTP proxy.
    * To configure name service subscriptions, point your browser at [http://localhost:7657/susidns/index.jsp](http://localhost:7657/susidns/index.jsp).
    * To find more Web pages and services or to discuss I2P, visit forum.i2p.

Services

I2P offers outbound proxies for, among others, Freenet and HTTP. The gateway to the unencrypted parts of the Web is automatically used when requesting such a page via the aforementioned proxy at port 4444. A Freenet gateway for I2P traffic only is located at [http://tino.i2p/freenet.html](http://tino.i2p/freenet.html).

Peer-to-peer file sharing is made possible by clients such as I2PHex for the Gnutella network and I2PSnark for the BitTorrent network. Another package that offers BitTorrent via I2P is the AnonBT plugin for the popular Azureus client.

Electronic mail is one of the most popular Internet services today, but unfortunately also one of the most insecure. Since most mail clients will leak information about you, for example by querying domain name servers, a webmail interface is available for everyone in the I2P network. SusiMail can help you send your mail encrypted and anonymously via I2P. You can find out more about SusiMail by accessing [http://localhost:7657/susimail/susimail](http://localhost:7657/susimail/susimail) (i2prouter must be running for this page to work).

An intriguing application of I2P is for an anonymous blogging service, and there already is one called Syndie. Citizens of countries that employ censorship and political persecution can use it to express their views freely without risking penalties.

SAM, another I2P feature, is not a service per se, but a simple clear-text protocol that allows services written in any arbitrary language to interface with the I2P network.

For arbitrary tunneling of vanilla TCP applications, you can use the program I2PTunnel. It can be configured from [http://localhost:7657/i2ptunnel/index.jsp](http://localhost:7657/i2ptunnel/index.jsp) (again, i2prouter must be running for this to work). A notable performance penalty comes with this translation, so heavy-duty I2P applications should not rely on it.

I2P already has a road map for future major versions, despite being barely past version 0.6 today. Its code doesn't get as much peer review as Tor yet, which renders it unsuitable for production use at this time. Eventually, though, I2P could become not only the most flexible privacy and security application, but also the safest. 

---

### Post by Thumper322 on 2006-12-04
Here's the [original link]("http://www.linux.com/article.pl?sid=06/09/12/1828258"), if you'd like to click on any of the hyperlinks omitted from raul_'s quote.

And how is this "beta"?

---

### Post by raul_ on 2006-12-04
Beta because it still doesn't cover many aspects of i2p / i2phex setup. If anyone has any doubts, feel free to post so we can improve this tutorial/FAQ

---

### Post by tedrogers on 2007-02-15
How do I uninstall the damn thing!

I'm new to installing anything that's not a .deb or autopackage....I used some java install routine to invoke the installer...but now I don't know how to uninstall i2p at all.

Thanks.

---

### Post by soulbreak on 2007-09-23
I ran java -jar i2pinstall.exe to install i2p in the same directory as the exe but I get this error message:

Failed to load Main-Class manifest attribute from i2pinstall.exe

---

### Post by tedrogers on 2007-09-23
Actually, I guess that my initial question was a bit uninformed, because I suspect the I2P installer is not really a proper installer in that all it does is create a folder called I2P in your home dir.

So to uninstall I expect I just need to delete the folder as it is completely self contained....just like in OS X.

---

