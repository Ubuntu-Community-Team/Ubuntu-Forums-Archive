---
title: "Network Trouble!"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by olieviya on 2005-12-12
I have not yet managed to make my Ubuntu Repositories or anything on Ubuntu except Firefox go properly on-line, I have tried to change my DNS settings (because they are wrong) but they keep changing back, is it because I'm not logged in as Administrator?

If so, does anybody know how to do that?

---

### Post by olieviya on 2005-12-12
I think the problem (as I said above) is that I'm not logged in as an Admin.

Please help

---

### Post by carlosqueso on 2005-12-12
By default, Ubuntu doesn't have an Admin account (called root in linux).  If you want to change something in the GUI, it will ask you for your user password when it's required.  If you use something in the terminal, just preface your commands with "sudo" and enter your password after that.  As far as changing your DNS, I don't know, but someone else may.

---

### Post by olieviya on 2005-12-12
Thing is: I open up System>Administration>Networking and it asks for my pass and I type it in, I make the appropriate changes and my internet/synaptic etc work fine but if I restart it goes back to the previous way it was.

Any ideas anybody?(Also I'm having screen & speakers trouble: [http://www.ubuntuforums.org/showthread.php?t=101639](http://www.ubuntuforums.org/showthread.php?t=101639) )

---

### Post by janrinok on 2005-12-12
One way to begin to track this down is to identify what is changing.  May I suggest the following:

Enter System-Administration-Networking, make your changes, and check using Firefox or Synaptic that you are online.  On a command line type:

'ifconfig' 

and save the output to a file.  Then, next time you reboot and cannot get online, go to the command line and run 'ifconfig' again.  Again save the output to a file.  Then copy the contents of each file to your reply to this thread and we can try to identify what is changing.  Make sure that you label the good and the bad entries clearly. We can perhaps then begin to look at _why_ it is changing and provide some help.  HTH, Jan

---

### Post by janrinok on 2005-12-12
Sorry, I was just assuming that you have a network connection to the internet simply because you are changing the network settings.  Can you also provide more information on the details of your connection?  ie is it through an ADSL modem/router, or a shared connection or whatever?  Jan

---

### Post by olieviya on 2005-12-12
I'm on an ADSL line via a router er.. what else can I tell you?

---

### Post by olieviya on 2005-12-12
Here are the results of an ifconfig with the correct settings just typed in:


eth0      Link encap:Ethernet  HWaddr 00:30:1B:1E:A3:35
          inet addr:192.168.1.70  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe1e:a335/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38663042 (36.8 MiB)  TX bytes:4241097 (4.0 MiB)
          Interrupt:11 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3147316 (3.0 MiB)  TX bytes:3147316 (3.0 MiB)

---

### Post by olieviya on 2005-12-12
Ok and here are the wrong ones with ifconfig:

olivia@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:1E:A3:35
          inet addr:192.168.1.70  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:fe1e:a335/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:396950 (387.6 KiB)  TX bytes:38527 (37.6 KiB)
          Interrupt:11 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:50654 (49.4 KiB)  TX bytes:50654 (49.4 KiB)

olivia@ubuntu:~$

---

### Post by olieviya on 2005-12-12
Looks like the problem isn't there then :O

---

### Post by janrinok on 2005-12-12
Ok, as the previous post has already observed, your network card settings are not changing. Your ADSL router should have an IP setting, your card is set to 192.168.1.70 but you haven't said what your router is set to.  What I would like to be able to do is prove that the hardware between your card and the router is not the problem (although it looks most unlikely to be the cause).  To do this we could use the 'ping' command to send a message to the router which would then echo it back.  Providing we receive that we can go on to test whether we can ping an address on the internet.  If that works we can probably forget about hardware problems, and we will also have proved that your DNS settings are correct.  However, we can probably try to miss the router check and just go straight for an external address.  On a command line, type 'ping www.symantec.com'.  When you have seen several lines of response (a few seconds and no more) press Ctrl-C to stop the ping command.  If that works DNS is working fine, if not then we have identified at least one problem.  Save the results of the ping command and paste them in your next reply.  Jan.

---

### Post by ninotob on 2005-12-12
After you change the DNS entries, do you restart your network card?  In other words, make changes, deactivate eth0, activate eth0, save settings?

EDIT:  when you have this problem, can you ping your router sucessfully?
ping 192.168.1.1
(assuming this is your router address, change as appropriate if it isn't the router's address).

EDIT2:  well, it looks like ping is already discussed! I should read to the end before posting.  ;-)

---

### Post by olieviya on 2005-12-13
I think the problem is it doesn't accept the correct settings even without rebooting! :(

I'm getting so frustrated about this - I'm thinking of just going back to windows.
So many things are not working for me. Please help.

---

### Post by olieviya on 2005-12-13
Here they are:


olivia@ubuntu:~$ ping [www.symantec.com](www.symantec.com)
PING a568.d.akamai.net (80.67.81.32) 56(84) bytes of data.
64 bytes from 80.67.81.32: icmp_seq=1 ttl=53 time=140 ms
64 bytes from 80.67.81.32: icmp_seq=2 ttl=53 time=135 ms
64 bytes from 80.67.81.32: icmp_seq=3 ttl=53 time=136 ms
64 bytes from 80.67.81.32: icmp_seq=4 ttl=53 time=137 ms
64 bytes from 80.67.81.32: icmp_seq=5 ttl=53 time=139 ms
64 bytes from 80.67.81.32: icmp_seq=6 ttl=53 time=137 ms
64 bytes from 80.67.81.32: icmp_seq=7 ttl=53 time=137 ms
64 bytes from 80.67.81.32: icmp_seq=8 ttl=53 time=138 ms
64 bytes from 80.67.81.32: icmp_seq=9 ttl=53 time=136 ms
64 bytes from 80.67.81.32: icmp_seq=10 ttl=53 time=134 ms
64 bytes from 80.67.81.32: icmp_seq=11 ttl=53 time=139 ms
64 bytes from 80.67.81.32: icmp_seq=12 ttl=53 time=138 ms

--- a568.d.akamai.net ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 16705ms
rtt min/avg/max/mdev = 134.174/137.701/140.214/1.733 ms
olivia@ubuntu:~$

---

### Post by olieviya on 2005-12-13
I've tried various ways of editing, activating, deactivating and all those in various orders including the one you suggest --- noting has worked so far!


EDIT: Oh, and how do i find out what the router's address is?

EDIT2: Here are the results of pinging the address you metioned:

olivia@ubuntu:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.28 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.27 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.28 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.28 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 1.273/1.313/1.447/0.080 ms
olivia@ubuntu:~$

---

### Post by janrinok on 2005-12-13
Olieiviya,  Hello again.  The results from the ping command show us several things.  Firstly, they prove that all your hardware is set up correctly and is working.  Secondly, they show that the DNS values that you have input are also correct.  If you had put the incorrect numbers in, then your ping command would not have found the [www.symantec.com](www.symantec.com).  (I could have used any website, but I know that symantec is working correctly so I chose that).  So when your computer fails to access certain sites, as in your original problem, we know that it is not a basic network problem or a matter of DNS.  In fact, these results suggest that it is a problem with the programs that you are using.  This does not mean that you have done anything wrong but rather that the configuration of one or more programs is not quite right.  What we now have to discover is what _is_ the problem.  Can you identify what programs sometimes do find the internet and yet sometimes do not?  Jan

EDIT1:  You mentioned that you haven't managed to get Synaptic or Firefox to work properly.  When you have a working internet connection and you try to use either program, what errors do you see?  What do you expect to happen, and what actually happens?  Jan

---

### Post by olieviya on 2005-12-13
Synaptic doesn't d/l files properly and they don't show up anywhere, also i get error messages assosiated with clam after i click the reboot button but now not anymore since i've removed it.

---

### Post by janrinok on 2005-12-13
When Synaptic downloads files it doesn't always put the new program into the menu for a while, sometimes until after I have logged off and back on again.  And, of course, many programs do not have menu entries.  What kind of error do you have when Synaptic fails to download properly?  And what error messages did you get with clamav?  (Yes I know that you have removed it but it might give us a clue to what is going wrong.)

---

### Post by olieviya on 2005-12-13
Like failed to properly install or something. If you think i'll help i'll reinstall just to see what it was. Oh, how do I start up a program not in the menu?

Also, Gaim doesn't connect and even though you said my DNS setting must be right they aren't the same as my isp's.
This my ISP's DNS and other stuff info page: [http://www.spidernet.net/main/default.aspx?tabid=86](http://www.spidernet.net/main/default.aspx?tabid=86)

---

### Post by janrinok on 2005-12-13
OK. to start a program that is not in the menu, you have to know its name.  For example, the Synaptic Package Manager (menu item) is actually simply called 'synaptic' and it can be located by using the 'which' command e.g.

which synaptic

returns the following

/usr/bin/synaptic

To start this program, which will require root permissions to run, you would use the following:

sudo synaptic  or  sudo /usr/bin/synaptic (but they should be equivalent to each other in this instance)

It would then prompt for your password and start the program.  If you have installed a program and do not know its correct name, try using the 'which' command with a lowercase name.

When it comes to using DNS addresses, it doesn't really matter which you use as long as they work.  Your ISP has given you some but whatever you have set up at the moment appears to be working so that isn't likely to be the cause of your problems.  We can look at changing them later on if you want to.  But, more importantly for you, you want to get your system working online.

What happens exactly when you try to start firefox?  Have you tried any other browser (although if Synaptic is not working you might have a problem installing one!) ?

---

### Post by janrinok on 2005-12-13
Looking more closely at the information provided by your ISP, I note that they have provided you with a HTTP proxy server address.  Try the following in Firefox:

Edit - Preferences - General - Connection Settings

Select Manual Proxy Configuration and put the following address and port number in the appropriate fields for HTTP: www-proxy.spidernet.net Port: 80

Save all the settings and try accessing a web page - if in doubt try www.google.com!

Let me know what happens.  I'm going to be offline for an hour or two, but I will be back later to help if nobody else chips in while I'm away.

---

### Post by olieviya on 2005-12-13
Firefox is working fine, it's gaim that's playing up.

---

### Post by janrinok on 2005-12-13
Olieviya, I do not know very much about GAIM but perhaps I can still ask a few questions.  Do you have a firewall installed?  When you say it 'is playing up', what exactly does it do.  Does it refuse to connect to anyone, does it drop out after a short period, or does it not even start properly?

---

### Post by olieviya on 2005-12-14
It doesn&#180;t connect to msn

---

### Post by janrinok on 2005-12-14
Have you got a firewall installed?

---

### Post by olieviya on 2005-12-14
None that I know of, how can I find out?

---

