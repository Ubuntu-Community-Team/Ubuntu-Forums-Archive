---
title: "My router sucks, could anyone gimme a hand?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by ThatWeirdGuy on 2005-08-29
I finally got my craptacular broadcom card to work, thanks to many splendid people here. But now I still can't get onto the internet under Ubuntu. This is cut 'n paste from a blog I'm keeping:

Update: I'm pretty sure that my router is working against me here.

After installing the card okay with it all set up, I [start manually inputting all the addresses](http://img39.imageshack.us/img39/5403/networkstuff3kc.png)  and whatnot. I'm thinking positive. I want this to work so I can finally uninstall windows (again) and give linux a second try. I keep changing and inputting [more](http://img39.imageshack.us/img39/9559/dnstab3ky.png) and [more](http://img257.imageshack.us/img257/6164/hoststab1nx.png), and I even have to put in a username somewhere so I just [ throw it in a random place](http://img211.imageshack.us/img211/6074/networksettings5an.png) and the result I get?

[Mozilla Firefox - Nothing's happening.](http://img39.imageshack.us/img39/2324/screenshot0hb.png)

-- Basically, every link is to a screenshot of all the configuration I've done to the network settings in Ubuntu. If anyone's wondering where I got the data I used in the configuration, I got it all from [the connection properties in Windows.](http://img172.imageshack.us/img172/4445/windowsproperties9og.png) But the thing is, I'm desperate to know what I've done wrong, so if anyone could quickly check over those screenshots and point out what's wrong in the pictures </lame pun> then I'd be incredibly greatfull.

If anyone could gimme a hand with this, it would be rather splendid indeed. :)

---

### Post by wvslkr on 2005-08-29
Not sure if this will help, but it appears you have set a static ip for ubunto and are using  
dhcp with windows.  Try changing to dhcp for ubuntu.  Hope it is that simple :)

---

### Post by ThatWeirdGuy on 2005-08-29
[QUOTE=wvslkr]Not sure if this will help, but it appears you have set a static ip for ubunto and are using  
dhcp with windows.  Try changing to dhcp for ubuntu.  Hope it is that simple :)[/QUOTE]
 Ah, but unfortunately, [it's not](http://img279.imageshack.us/img279/2983/notfound7zl.png). (Yup, another screenshot. :P)

---

### Post by wvslkr on 2005-08-29
I hate to ask the obvious.  Did you restart the computer?

---

### Post by ThatWeirdGuy on 2005-08-29
[QUOTE=wvslkr]I hate to ask the obvious.  Did you restart the computer?[/QUOTE]

I did indeed.

---

### Post by wvslkr on 2005-08-29
Open the ping tab under the network tools and type in the address of your router.  If it answers then try to ping somewhere like this forum or yahoo.

---

### Post by manicka on 2005-08-29
You need to add in the dns address and search domain details of your provider and not the address of your router or gateway.

---

### Post by az on 2005-08-29
[QUOTE=manicka]You need to add in the dns address and search domain details of your provider and not the address of your router or gateway.[/QUOTE]
Actually, that would depend on your router.


Are you sure that your network card is working proplerly.


Do me a favor and open a terminal and type this:

ifconfig

Then do

ping 216.239.39.99 

and then ping your router

ping 192.168.0.254 (is this the correct address?)

and then 

ping [www.google.com](www.google.com)

Also, delete your wlan0 connection because you probably really screwed it up.  You should start over and only tell it to use DHCP.  The point of DHCP is that all those other addresses are configured for you.

Cut and paste everything to a text file and show the results here.

---

### Post by ThatWeirdGuy on 2005-08-29
[QUOTE=azz]Actually, that would depend on your router.


Are you sure that your network card is working proplerly.


Do me a favor and open a terminal and type this:

ifconfig

Then do

ping 216.239.39.99 

and then ping your router

ping 192.168.0.254 (is this the correct address?)

and then 

ping [www.google.com](www.google.com)

Also, delete your wlan0 connection because you probably really screwed it up.  You should start over and only tell it to use DHCP.  The point of DHCP is that all those other addresses are configured for you.

Cut and paste everything to a text file and show the results here.[/QUOTE]
 Thanks for the advice, unfortunately I'll only be able to try such things tomorow. For now though, I'll mention that I have pinged the router before and it had a response. Also, I followed the guide that is somewhere on these forums; searching with the criteria "Broadcom" brings it up. In the guide it says that as you close the network properties it should take a second, if not, something's wrong. When I set it to use DHCP, it takes ages before closing. Therfore I assumed that there is something wrong with using that setting.

As I said though, I shall try it all again tomorow. Thank you for your time, advice, and patience. :P

---

### Post by az on 2005-08-29
[QUOTE=ThatWeirdGuy]Thanks for the advice, unfortunately I'll only be able to try such things tomorow. For now though, I'll mention that I have pinged the router before and it had a response. Also, I followed the guide that is somewhere on these forums; searching with the criteria "Broadcom" brings it up. In the guide it says that as you close the network properties it should take a second, if not, something's wrong. When I set it to use DHCP, it takes ages before closing. Therfore I assumed that there is something wrong with using that setting.

As I said though, I shall try it all again tomorow. Thank you for your time, advice, and patience. :P[/QUOTE]
What is ages?

It can take about thirty seconds, if
1- the router is slow to respond to the dhcp request
2- The network app has to rewrite your networking configuration and quit.

---

### Post by ThatWeirdGuy on 2005-08-30
Once again, thanks.

Alrighty, I followed your instructions. Before it's mentioned, yes I did make sure I removed the bcmwl5 installation before hand. Heck I even formatted and redid the partition tables, but that's completely irrelivant. :P

I've followed your instructions, and this is the log:

> root@syren:/home/syren # ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:118262 (115.4 KiB)  TX bytes:118262 (115.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:F5:0B:A1:60
          inet6 addr: fe80::211:f5ff:fe0b:a160/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:cfffa000-cfffbfff

root@syren:/home/syren # ping 216.239.39.99
connect: Network is unreachable
root@syren:/home/syren # 

How you can make sense of that, I've no idea. :P

EDIT: Just thought I'd mention that this time I selected "DHCP" in the Network Properties.

---

### Post by inkysplat on 2005-08-30
Hey, I'm a little confused by your network setup (with DHCP/Static IPs etc), but that shouldn't be the problem.

If it were me, i'd first check the device is working, assuming your using ndiswrapper to use your windows drivers with your device. 

```
sudo ndiswrapper -l
```

It should say device present, and installed. If not you've got a driver problem, but as your Networking Manager is showing wlan0 i'd assume it is. but its worth a shot.

The other thing i'd do is to make sure your puting a - between every four digits in your WEP key. I also had a similar problem with this.

so your WEP key would look like: XXXX-XXXX-XXXX-XXXX-XXXX-XX

The other thing is to ping your router, my router's IP is: 192.168.1.1 its a linksys one. I don't know your Router brand, so i can't comment on what IP it has.

```
ping 192.168.1.1
```

If you get "timeouts" then your not even connected to the router! If its sucessful try pinging google.com.

```
 ping google.com
```

If this comes back as "Destination Unreachable" like you said before, i'd say theres probabily something wrong with your DNS settings, i found this out the hard way. I'd strongly recommend checking the DNS information supplied by your ISP, and enter that into the Network Configurer.

After the above changes in the Network Configurer, you might want to deactivate and reactivate the card, to refresh and write the settings.

Then retry pinging Google again:
```
ping google.com
```

The other thing you can do is check your Dmesg for errors, try:
```
dmesg|grep wlan0
```

And of course there is also manually editting the config file for your network:
```
sudo gedit /etc/network/interfaces
```
The Network Configurer should have some code there for wlan0 already, you just might want to double check its correct there.

If the DNS information you entered into the Network Configurer does nothing, try putting it in:
```
sudo gedit /etc/resolv.conf
```
It should go in the format of "nameserver XXX.XX.XX.XX" add a line for each DNS address.

For now that is all i can suggest. Good luck.

---

