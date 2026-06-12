---
title: "Internet connection"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by rakesh343 on 2006-10-14
I have just installed Ubuntus 6.06 LTS Drake Drake. The problem is after installation I am not able to connect to internet in Linux. Though the system is able to identify the ISP address, subnet mask, Default Gateway, etc. Everytime I am trying to connect, it takes a long time after which time out error is displayed. I am having a broadband connection through an ADSL router. I have checked the network settings, it is active. The devise shown is eth0 which is active. Pinging results in successful transfer of all packets. But still I can not open any page.

:confused: :-k

---

### Post by dmizer on 2006-10-14
in firefox, go to: about:config.

in the search bar type: ipv6

change network.dns.disableIPv6 to true by double clicking on the line.

restart firefox and see if that fixes your problem.

---

### Post by Bloch on 2006-10-14
You might need to get the address of your broadband modem.
My one is 
[http://192.168.1.1](http://192.168.1.1)
In other words, enter this in your browser's address bar and it will connect to your modem

(many use the same number; check your modem's documentation)

---

### Post by dmizer on 2006-10-14
> **rakesh343 said:**
> Pinging results in successful transfer of all packets. But still I can not open any page.

this means there is no reason to check your modem or router configuration settings.  the problem could be related to a couple of things:

1) ipv6 is interfering with your ability to browse.
2) possible dns settings.

you shouldn't need to browse to your router or modem to fix this problem.

---

### Post by rakesh343 on 2006-10-15
Then what should I do? Network connection shows "Idle". Otherwise everything seems OK. The deivice activated is Ethernet of eth0 type through an ADSL Router. Pinging is successful. What should I do. Off course my IP Adress is 192.168.1.2, but this it has already detected and thus I guess it is a Dynamic one (DPHC).
What? Please suggest.
:confused: ](*,) ](*,)

---

### Post by Stephen_A on 2006-10-15
I had much the same type of problem and resolved it through this link. I hope it works for you. 

[http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe](http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe)

---

### Post by rakesh343 on 2006-10-15
I do not understand it. Sorry. What is PPPoE? My connection is through an ADSL Router. As I said the system was able to recognise IP Address, Subnet Mask and Default Gateway. So I think connection is OK.
Well, I may be wrong as I know little of all these. Please help me in somewhat easier way. Thanks.

---

### Post by geezerone on 2006-10-15
> **rakesh343 said:**
> I have just installed Ubuntus 6.06 LTS Drake Drake. The problem is after installation I am not able to connect to internet in Linux. Though the system is able to identify the ISP address, subnet mask, Default Gateway, etc. Everytime I am trying to connect, it takes a long time after which time out error is displayed. I am having a broadband connection through an ADSL router. I have checked the network settings, it is active. The devise shown is eth0 which is active. Pinging results in successful transfer of all packets. But still I can not open any page.

:confused: :-k

Sounds like a 99.9% DNS issue BUT just to be sure type [http://66.102.9.104](http://66.102.9.104) ([www.google.com](www.google.com)) in firefox browser which if works IS a DNS issue.

You need to configure the DNS servers (which your ISP will tell you) which you get to through administration > Networking if I remember correctly :-k :-D

---

### Post by rakesh343 on 2006-10-16
For the first time I, with my linited knowledge, have tasted partial success in resolving my problem. Thanks Geezeron. :) :) 

As you said, I typed [http://66.102.9.104](http://66.102.9.104) in the address bar and the google page was displayed. It was not coming when I was typing [www.google.com](www.google.com). In fact, it showed results of a search too that I asked. But then clicking on the displayed links resulted in the same old problem of timed out error. All while, in the address bar it was showing the numerial form address only and not the words ([www.google.com)](www.google.com)). So I am pretty sure that you have grasped my problem. Tell me what to do next.
:-k

---

### Post by mips on 2006-10-16
Your problem is DNS related. Manually configure your ISPs primary & secondary DNS server addresses in your resolv.conf file.

---

### Post by rakesh343 on 2006-10-16
Sorry. But where is this resolv.conf file? How to do it? What are primary and secondary DNS servers? :confused:

---

### Post by geezerone on 2006-10-16
You have made progress but your ISP will have the DNS servers so contact them (The DNS server(s) convert a web address into IP addresses (which is what computers use to find each other) and you bypassed the DNS server when you typed in the IP address of Google you see. 

You can edit the [COLOR="RoyalBlue"]resolv.conf[/COLOR] file (in [COLOR="RoyalBlue"]/etc[/COLOR]) or just go to  [COLOR="RoyalBlue"]System > Administration > Networking[/COLOR] - then click on the [COLOR="RoyalBlue"]DNS[/COLOR] tab which brings up the DNS Servers window and then click [COLOR="RoyalBlue"]ADD[/COLOR] to add these addresses (at least two)

Good luck! :)

---

### Post by rakesh343 on 2006-10-17
Thanks Geezerone. Finally I am able to connect to the internet. In fact I am using it to write to you. This is the first mail that I am writing in Ubuntu. This is the first milestone. I, with this little success, am encouraged enough to appeal to others to shift to Linux and bid a goodbye, a long overdue, to Microsoft's control over our lives. Now I am a happy member of the Linux family. Great. :) :) :D :D

---

### Post by aam-aadmi on 2006-10-17
Rakesh,

The following might work.

Stage 1

1. Boot into Windows XP (I am assuming you have the Windows partition running).
2. Do the following: Start -> Control Panel -> Network Connections -> Right click on the icon  -> Select Properties -> double-click on TCP/IP
3. Note down the following addresses: (a) Preferred DNS server, and (b) Alternate DNS server

Now Restart computer and boot into Linux.

Stage 2

1. Open a terminal and type the following (and hit "enter"): 
```
sudo cp /etc/resolv.conf  /etc/resolv.conf_backup

```
2. Enter password and hit "enter"
3. Now type the following: 
```
sudo gedit /etc/resolv.conf
```  
(A window will open with a file with 3 lines; the first line will start with "search ...". Look at the two lines below the first line. It will have something like "nameserver IP-address " on each line. You need to change the IP-address on each line).
4. Put the address of the preferred DNS server (that you have already noted) in place of the address in the second line; put the address of the Alternate DNS server (that you have already noted) in place of the address in the third line.
5. Save the file and exit.

Restart computer, boot into Linux and you should have proper internet access.

---

### Post by aam-aadmi on 2006-10-17
Oops! ...did not see that Rakesh already had his internet running! Anyway, let us welcome a new member to the Ubuntu family.

---

### Post by rakesh343 on 2006-10-27
Thanks for all the help. But I am still facing some problems. After doing the System>Administration>Networking>DNS tab and adding the preferred and Alternate addresses it starts working. But the problem is soon the connection goes off. If I go back and see the System>Administration>Networking>DNS Tab, I find that it gets rewritten and instead of the two address that I type, I find my IP Address written there. This happen everytime and also between the working sessions. Any help?:confused: :confused:

---

### Post by MaximB on 2006-10-27
you got exacly the problem I had
reconfigure the dns addresses as you need then write or copy/paste at the terminal :
sudo chattr +i /etc/resolv.conf
that will make the resolv.conf file read only.

---

### Post by rakesh343 on 2007-02-27
Again I am having a similar problem of net connectivity. This time the DNS setting show the correct entries, i.e. a preferred and an alternate address and a correct search domain. But still I am not able to connect (a time out error is displayed). This time it started when I tried to connect it through a different server. I changed those settings, but was not able to connect. Afterwards I am not able to connect when I am using the earlier server. This time even using the numeric address (e.g. [http://66.102.9.104](http://66.102.9.104) for google.com) does not help.

---

### Post by gwpritch on 2007-02-27
Try this:

```
sudo gedit /etc/dhcp3/dhclient.conf
```

Look for a line that says something like:

#prepend dns 127.0.0.1 (exact wording I'm not sure)

uncomment this line and change the IP to the IP address of your preferred DNS server.

You can clone this line for any number of server addresses.

Save file and restart network.

This should make your DNS choices permanent.

Also make sure you only have one NIC active or you are going to get interference and will be constantly losing your connection.

---

### Post by rakesh343 on 2007-02-27
It is not helping. when I am typing 

sudo gedit /etc/dhcp3/dhclient.conf

the terminal says "command not found" after asking for the password. What next???

---

### Post by gwpritch on 2007-02-27
Use any text editor...it doesn't have to be gedit.

---

### Post by geezerone on 2007-02-28
> **rakesh343 said:**
>  Afterwards I am not able to connect when I am using the earlier server. This time even using the numeric address (e.g. [http://66.102.9.104](http://66.102.9.104) for google.com) does not help.

Open a terminal and type "ifconfig" and post that here as if you can't get google via IP then tcp/ip has the problem  not dns.

---

### Post by r4ik on 2007-02-28
> **gwpritch said:**
> Try this:

```
sudo gedit /etc/dhcp3/dhclient.conf
```

Look for a line that says something like:

#prepend dns 127.0.0.1 (exact wording I'm not sure)

uncomment this line and change the IP to the IP address of your preferred DNS server.

You can clone this line for any number of server addresses.

Save file and restart network.

This should make your DNS choices permanent.

Also make sure you only have one NIC active or you are going to get interference and will be constantly losing your connection.

I think it has to be done as root and permit me to add,

manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

---

