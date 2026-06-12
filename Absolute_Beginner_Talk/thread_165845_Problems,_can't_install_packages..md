---
title: "Problems, can't install packages."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-25
hey

I am a web developer, and I am new to linux.

I am facing some problem with the Synaptic Package Manager.

I need to install a web server on linux, so I need apache, php, and mysql.
I went to the Package Manager to install apache ... it worked. but when I wanted to install php I couldn't find it so went to the repositories and did exactly what is mentioned in the documents, I added php [http://www.php.net](http://www.php.net) php4 in the custom and it gave me an "unable-to-find" error statement ... 

I signed in terminal as root and then I typed:

```
apt-get install php4
```
but it gave me this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

What does that mean? and how can I install php and mysql without getting such errors?

any help will be appriciated.

---

### Post by mjm115 on 2006-04-25
When you did this, was Synaptic still open?  If the synaptic is open, apt-get will not work because the sources.list file is locked by Synaptic.

---

### Post by pbaehr on 2006-04-25
You need to use
```
sudo apt-get install php4
```

This gives you super-user priveleges during the duration of the command.

Also, it may be that you still have synaptic open. Only one apt-get based application can access the files at any given time.

Edit: I missed the part where you said you were root so you can ignore the sudo bit. The other part is still valid.

---

### Post by Isoss on 2006-04-25
Thanks guys, Synaptic was open indeed so I closed it.

I typed ```
apt-get install php4
``` and this is what it gave me:
```

root@ubuntu:/home/isos# apt-get install php4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4

```

what can I do to get that package?

---

### Post by mostwanted on 2006-04-25
[QUOTE=Isoss]Thanks guys, Synaptic was open indeed so I closed it.

I typed ```
apt-get install php4
``` and this is what it gave me:
```

root@ubuntu:/home/isos# apt-get install php4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4

```

what can I do to get that package?[/QUOTE]

[http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories)

php4 is in Universe.

The rest of that page is also worth a read.

---

### Post by Isoss on 2006-04-25
Hey, thanks. I read the documents on how to get packages by adding repositories ...  I tried and tried and each time it hits me with that Upable-to-find package alerts. but the page you gave me seems good so I'll go read it as if reading the bible, and hope this would save me :p 

So anyway thanks for the help guys.

---

### Post by pbaehr on 2006-04-25
Make sure you run
```
sudo apt-get update
```

After you change your repositories!

---

### Post by Sef on 2006-04-25
You can also find the packages on this site.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/") 

once you find them, open the terminal and type:

sudo apt-get update

sudo apt-get install package-name

---

### Post by Isoss on 2006-04-25
Hey, problem ... I read the page which mostwanted syggested ... and when I went to 
[Enabling extra repositories]("http://monkeyblog.org/ubuntu/installing.html#enabling_extra_repositories") I checked all the software sources and clicked ok, and it started to download and then it gave me this error

**[SIZE="3"]Could not download all repository indexes[/SIZE]**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

http://sy.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz: Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]
http://sy.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz: Could not connect to sy.archive.ubuntu.com:80 (85.133.25.8). - connect (111 Connection refused) [IP: 85.133.25.8 80]

```
Sorry it's long but just to give you a idea of what is happening ... 
then it gave me a warning:
**The following problems were found on your system:**
```

W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://sy.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/sy.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

```
what is that? and how bad is that?

---

### Post by Ensnared on 2006-04-25
Connection refused usually means the server is down, but it could also be a firewall issue... You can try connecting to those sites - i.e. [http://sy.archive.ubuntu.com/](http://sy.archive.ubuntu.com/) and [http://security.ubuntu.com/](http://security.ubuntu.com/) - in a web-browser, but chances are you'll get the same problem.

Check your firewall if you're behind one. Do you have any other connection-problems to the internet at all?

The other errors are probably results of apt-get not being able to download the files from the repositories - get that fixed and the they will likely go away as well.

---

### Post by Isoss on 2006-04-25
Actually, I think the problem is with the connection, cuz gaim is not working either.
I am new to linux, and I dunno anything about it's firewall ...

---

### Post by Isoss on 2006-04-25
and by the way, the two links are not working ... they are showing me and index page.

---

### Post by Ensnared on 2006-04-25
[QUOTE=Isoss]and by the way, the two links are not working ... they are showing me and index page.[/QUOTE]
If they both show a while page with the text "Index of /" with a link below labeled "ubuntu" then you're connected and are able to access them. If that's the case then it's very very strange that apt-get is unable to connect.

Are you posting to the forum from the same computer you're having problems with?

Just to make sure you don't have a firewall active on your own box, do this:
```
sudo iptables --list
```...and post the output.

Also, are you connected through an ISP or through a corporate or school network or somesuch? There may be restricted access by a firewall there- ISP's usually don't have anything like that, but a business or school might.

You can also try to ping the sites in question:```
ping sy.archive.ubuntu.com
ping security.ubuntu.com
```
In both cases you should get an output similar to this:```
PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=1 ttl=45 time=55.1 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=2 ttl=45 time=54.9 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=3 ttl=45 time=55.1 ms
```
It will continue until you hold CTRL and press C, and will then show a summary, like this:```
--- security.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 54.986/55.452/56.362/0.578 ms
```

---

### Post by Isoss on 2006-04-25
Ok. I am posting to the forum from the computer which has the linux system. the internet is working fine except for the "GAIM".

My ISP is ADSL and my PC is connected to a hub switch which is connected to a router.

And this is the iptables list:
```
isos@ubuntu:~$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I pingged the sites as you asked : ( please explain, what does this ping do?)
```
root@ubuntu:/home/isos# ping sy.archive.ubuntu.com
PING sy.archive.ubuntu.com (85.133.25.8) 56(84) bytes of data.

--- sy.archive.ubuntu.com ping statistics ---
207 packets transmitted, 0 received, 100% packet loss, time 206099ms

```

```
root@ubuntu:/home/isos# ping security.ubuntu.com
PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```
That's all the 2 pings gave me ...

---

### Post by Ensnared on 2006-04-25
Right.

You have internet access from the computer, so that isn't the problem.

You don't have any firewall rules which would prevent access. The iptables-command shows any firewall rules currently active, the output you have shows the are no rules other than the default "accept everything".

Ping simply sends a network packet with a request for a reply. If the computer you send the ping to receives it, it will send a reply and you'll get the output I showed as an example - unless there's something in between which prevents either your ping, or the reply, from reaching its destination. You're not getting any replies at all, which means something somewhere seems to be preventing either your requests, or the response from the servers you're trying to contact.

How about the index-pages you got on the two URL's? Did they show what I asked, or something else?

So far it sort of seems like you have access from the GUI (except GAIM, but that might be a completely different issue), but not from the command line, which makes no sense to me at all...

Can you post the contents of your /etc/apt/sources.list? Doubt there's something wrong in there, but might as well make sure. Also, post the output of the command "ifconfig -a".

---

### Post by Ensnared on 2006-04-25
Just thought of something - do you use a proxy-server to access the internet? Check the connection-settings in your browser to see if that's configured - it shouldn't be unless you've done it yourself, but just check to make sure.

If you're using Firefox, the settings are under Edit->Preferences->General->Connection Settings

Also check the System->Preferences->Network Proxy in the Gnome-menu.

---

### Post by Isoss on 2006-04-25
Hey
[QUOTE='Ensnared']Ping simply sends a network packet with a request for a reply. If the computer you send the ping to receives it, it will send a reply and you'll get the output I showed as an example - unless there's something in between which prevents either your ping, or the reply, from reaching its destination. You're not getting any replies at all, which means something somewhere seems to be preventing either your requests, or the response from the servers you're trying to contact.[/QUOTE]
First of all, thanks for the explaination.
[QUOTE='Ensnared']How about the index-pages you got on the two URL's? Did they show what I asked, or something else?
[/QUOTE]
[http://sy.archive.ubuntu.com/](http://sy.archive.ubuntu.com/) is showing a normal index, but [http://security.ubuntu.com/](http://security.ubuntu.com/) is telling me: 
**Index of /**

    * ubuntu/ (this one as a link)

Apache/2.1.3 (Ubuntu) Server at archive.ubuntu.com Port 80

[QUOTE='Ensnared']So far it sort of seems like you have access from the GUI (except GAIM, but that might be a completely different issue), but not from the command line, which makes no sense to me at all...[/QUOTE]
What is GUI?
[QUOTE='Ensnared']
Can you post the contents of your /etc/apt/sources.list? Doubt there's something wrong in there, but might as well make sure. Also, post the output of the command "ifconfig -a".[/QUOTE]
Forgive me, but I don't know how to get the contents of /etc/apt/sources.list.
Now this is the output of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:E0:91:02:76:43
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:91ff:fe02:7643/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3031066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4483427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:294648500 (280.9 MiB)  TX bytes:2101151857 (1.9 GiB)
          Interrupt:16 Memory:bc000000-0

eth1      Link encap:Ethernet  HWaddr 00:12:F0:59:A3:07
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xc000 Memory:c4006000-c4006fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6449947 (6.1 MiB)  TX bytes:6449947 (6.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
And yes, my ISP requires a proxy-server, and I have put it manually in the firefox connection settings. but there is nothing in the Network Proxy.

---

### Post by Ensnared on 2006-04-25
[QUOTE=Isoss]And yes, my ISP requires a proxy-server, and I have put it manually in the firefox connection settings. but there is nothing in the Network Proxy.[/QUOTE]

A-ha! That's the culprit right there ;)

Do this:
```
sudo gedit /etc/apt/apt.conf
```
The file is probably empty, but don't worry aboyt that. Put in our proxy-server, like this:
```
Acquire::http::Proxy "http://proxy.server.here:8080/";;
```

Make sure the proxy-host (proxy.server.here in the example) and the portnumber (8080 in the example) are the right ones. Port 8080 is usually what proxy-servers use, but yours might be different.

Save the file and close it. Then do "apt-get update" and watch the magic happen 8)

As for your other questions: To post the contents of sources.list (or any other file), you can do this:
```
sudo gedit /etc/apt/sources.list
```
Select all the text (CTRL+a), copy it (CTRL+c), and paste it in your post (CTRL-v). You've pasted the outputs from various commands so I guess you've got that part narrowed down already :)

And a GUI is short for Graphical User Interface, as opposed to CLI, which means Command Line Interface (which is where you enter the apt-get commands and the like :))

Lastly, if you enter your proxy-server into the System->Preferences->Network Proxy, chances are GAIM will work as well - or maybe it has it's own proxy-configuration, in which case you'll find it within the options of GAIM itself. I use Kopete (an Instant Messaging application for KDE) so I'm not exactly sure how GAIM works in this respect, but you should still enter your proxy-configuration into the Network Proxy, as several other applications are likely to fetch the proxy-information from there.

---

### Post by Isoss on 2006-04-25
MAN ... Thanks a lot for the magic ... it's working now .. and installing php4:D

---

### Post by Ensnared on 2006-04-25
Good to hear - I should've thought of checking for a proxy sooner though, but there you have it. Atleast it's working now :)

---

