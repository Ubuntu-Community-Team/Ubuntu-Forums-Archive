---
title: "Hi, how do I...."
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by n00b on 2005-07-04
Hi there,
First I'd like to introduce myself to thies forums. My name is Jason and Im a linux N00b, just as my nick states. I have a strong interest in computers and after 10 years of using Micrsoft Windows, I think its time to learn something new. 

I have very little knowledge about Linux, what I have done is:
Installed it a couple times
Played with the GUI 
Edited pictures with GIMP.


Well now for my questions:
How do I enable auto completion in terminal when using the tab key?
- I start typing text and press tab to complete the syntax but nothing happens. 

How do I establish an internet connection with my ADSL?

How do I configure TCP under linux. 

Thats all for now.
Thanks in advance and I look forward to learning something new.

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=n00b]Hi there,
First I'd like to introduce myself to thies forums. My name is Jason and Im a linux N00b, just as my nick states. I have a strong interest in computers and after 10 years of using Micrsoft Windows, I think its time to learn something new. [/QUOTE]

Thats the attitude we like to see around here. Welcome.
 


> 
How do I establish an internet connection with my ADSL?



I think I can hep with this. Can I have more details (what modem is it? do you connect to it using a network cable or a usb cable -network cable way is much easier).

---

### Post by n00b on 2005-07-04
[QUOTE=poofyhairguy]Thats the attitude we like to see around here. Welcome.
 





I think I can hep with this. Can I have more details (what modem is it? do you connect to it using a network cable or a usb cable -network cable way is much easier).[/QUOTE]
 Its an ethernet router/modem. I have been able to access the setup pages on the device, So I know my little network is working.

---

### Post by ltmon on 2005-07-04
RE: autocompletion

Bash (the default shell for Ubuntu) will autocomplete filenames and executables found in your PATH environment variable.  You don't need to turn it on like in windows... it's there all the time.

The autocomplete works differently from windows though.  If you 'tab' in the command shell in windows a full filename will be completed and subsequent tabs will bring up other filenames that match the autocompletion you started.

In bash the autocomplete will only work as far as it can.  For example, if you have the following files in your home directory:

> ls
test1.txt
test2.txt

> cat te

now hit tab, the autocomplete will only give you

> cat test

if you then hit tab again (twice quickly) a list will be shown of all the possible options.  Play around to get the hang of it.

also try this:

> l <tab><tab>

will show all possible commands beginning with 'l'.

> <tab><tab>

will show all possible commands.

OK that took longer to explain than I thought it would.  Play with it and it will become a little clearer :)

L.

---

### Post by topcop on 2005-07-04
[QUOTE=n00b]Hi there,
First I'd like to introduce myself to thies forums. My name is Jason and Im a linux N00b, just as my nick states. I have a strong interest in computers and after 10 years of using Micrsoft Windows, I think its time to learn something new. 

I have very little knowledge about Linux, what I have done is:
Installed it a couple times
Played with the GUI 
Edited pictures with GIMP.


Well now for my questions:
How do I enable auto completion in terminal when using the tab key?
- I start typing text and press tab to complete the syntax but nothing happens. 

How do I establish an internet connection with my ADSL?

How do I configure TCP under linux. 

Thats all for now.
Thanks in advance and I look forward to learning something new.[/QUOTE]

enable DHCP on your ethernet  router and you will be online without any configuration.

---

### Post by n00b on 2005-07-05
> enable DHCP on your ethernet router and you will be online without any configuration.

Alright, Ive enabled DHCP (I left the host name blank because I dont think I need one) on my router and setup my username and password. What do I do now to establish a connection to the internet?

---

### Post by knewbix on 2005-07-05
Hi Jason, welcome aboard! I wish I could help you but I'd like to add to your question about auto complete in terminal windows. I cannot get this working either. I have used several other distros and the tab/auto-complete thing helps out a lot, but all I get in Kubuntu is a beep, and, well, nothing. Any clues, people?  :-?

---

### Post by Seti on 2005-07-05
[QUOTE=n00b]Alright, Ive enabled DHCP (I left the host name blank because I dont think I need one) on my router and setup my username and password. What do I do now to establish a connection to the internet?[/QUOTE]

What kind of router is it? D-Link? Linksys? Do you have cable or DSL?

---

### Post by n00b on 2005-07-05
[QUOTE=Seti]What kind of router is it? D-Link? Linksys? Do you have cable or DSL?[/QUOTE]

Erm... :-?, Its a Marconi router I got from my ISP. Its is DSL router that connects to my NIC via ethernet cable.

---

### Post by poofyhairguy on 2005-07-05
[QUOTE=n00b]Erm... :-?, Its a Marconi router I got from my ISP. Its is DSL router that connects to my NIC via ethernet cable.[/QUOTE]


Is there any way that you can plug the system straight into the dsl modem for a sec and enable the connection (networking tool)...so we can see if the problem is the router or the modem?

---

### Post by n00b on 2005-07-05
Im not with you  poofyhairguy, 
> Is there any way that you can plug the system straight into the dsl modem 
My computer *is* connected to the dsl router and it works in windows. 

>  and enable the connection 
My this do you mean manually connecting to the internet? Thats what Ive been trying to do the whole time.

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=n00b]Im not with you  poofyhairguy, 
 
My computer *is* connected to the dsl router and it works in windows. 

 
My this do you mean manually connecting to the internet? Thats what Ive been trying to do the whole time.[/QUOTE]

Can you find a website for this router please? I need more details and I'm having trouble finding it myself.

---

### Post by nocturn on 2005-07-06
[QUOTE=n00b]Im not with you  poofyhairguy, 
 
My computer *is* connected to the dsl router and it works in windows. 

 
My this do you mean manually connecting to the internet? Thats what Ive been trying to do the whole time.[/QUOTE]

Can you try opening a terminal and do

```
ifconfig
```

```
host www.google.com
```
 
```
 ping www.google.com
```

```
route
```

What output do you get?

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

have you enabled your ethernet connection in your ethernet settings?

click System/Administration/Networking

then select your ethernet connection and click properties

make sure there is a tick in this device is configured and where it says configuration change it to DHCP and click OK.

Then Click Activate and ensure your default gateway device is eth0 (or whatever it is for your ethernet card)

reboot and it should work!

Hope this helps!

Bl0wn2b1ts

---

### Post by n00b on 2005-07-06
Ok I've been gathering data for the post. Im still without internet access :(
How is setting up internet in ubantu suppost to work?


> Can you find a website for this router please? I need more details and I'm having trouble finding it myself.
Here it is. 
[http://www.marconisa.co.za/4portsadsl.htm](http://www.marconisa.co.za/4portsadsl.htm)

> Can you try opening a terminal and do

ifconfig
host [www.google.com](www.google.com)
ping [www.google.com](www.google.com)
route


**ifconfig** 
eth0     Link encap:Ethernet  HWaddr 00:09:1D:00:B0:32  
            inet addr:10.0.0.6  Bcast:255.255.255.255  Mask:255.0.0.0
            inet6 addr: fe80::209:1dff:fe00:b032/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:45 errors:0 dropped:0 overruns:0 frame:0
            TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:5978 (5.8 KiB)  TX bytes:7970 (7.7 KiB)
            Interrupt:11 Base address:0xec00

lo   
            Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:26356 errors:0 dropped:0 overruns:0 frame:0
            TX packets:26356 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:1942855 (1.8 MiB)  TX bytes:1942855 (1.8 MiB)

**host** 
jason@ubuntu:~ $ host [www.google.com](www.google.com)
Host [www.google.com](www.google.com) not found: 2(SERVFAIL)

**ping** 
jason@ubuntu:~ $ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

**route** 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        
    *               255.0.0.0       U     0      0        0 eth0


> Then Click Activate and ensure your default gateway device is eth0 (or whatever it is for your ethernet card) 

How do I check what the default gateway is ?

---

### Post by Bl0wn2b1ts on 2005-07-06
[QUOTE=n00b]
How do I check what the default gateway is ?[/QUOTE]

the pic you attached at that part click ok and its on the window which appears "Default Gateway Device"

hope this helps

Bl0wn2b1ts

---

### Post by n00b on 2005-07-06
*Bump*
Sorry but I got to bump this up  :razz: 
> How is setting up internet in ubuntu suppost to work? 

Is there a FAQ or walkthrough I could try?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=n00b]
Is there a FAQ or walkthrough I could try?[/QUOTE]

Here is a howto....I searched for a while and its the best I can find. Ask questions about it if you need to:

[http://www.siliconvalleyccie.com/linux-hn/network-linux.htm](http://www.siliconvalleyccie.com/linux-hn/network-linux.htm)

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

Did you check what the default gateway was??

Bl0wn2b1ts

---

