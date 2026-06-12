---
title: "Need help to set up virgin broadband"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by kinglee on 2007-12-26
I last note divorced vista from my laptop and fully installed ubuntu 7.10.
I now need to set up my virgin broadband on linux and i havent a clue what im doing!
Im going to use the eternet cable at first then add the wrless router at a later date.
wired connection-properties do i use static ip adress etc
under the general tab what do i put in as a host name and domain name
DNS- what do i put in the DNS Servers and search domain boxes
and hosts, it asks for an ip address and an alias...whats an alias in computer speak!!!!!
In time ill be advising other people but right now i know nothing!!!
Pls Help!!:confused:

---

### Post by mellowd on 2007-12-26
what connection do you have? Cable or DSL?

---

### Post by LaRoza on 2007-12-26
Does it not work when you plug it in?

---

### Post by asmiller-ke6seh on 2007-12-26
For most systems, all you have to do is plug the network cable from the DSL/CABLE modem into the network card of your system.

Have you tried that? What happened when you did? When you open your internet browser, what happens.

---

### Post by kinglee on 2007-12-26
I have cable broadband.
When i plug the ethernet cable in and click on firefox to browse, it says server cannot be found.
im using the same connection just on my pc instead so i know theres no internet probs.
I guessed as soon as you plugged the cable into the laptop it worked!
Obviously, i is wrong!
At a half educated guess, its where the network settings are not set up, hence need the settings!:)

---

### Post by mellowd on 2007-12-26
> **kinglee said:**
> I have cable broadband.
When i plug the ethernet cable in and click on firefox to browse, it says server cannot be found.
im using the same connection just on my pc instead so i know theres no internet probs.
I guessed as soon as you plugged the cable into the laptop it worked!
Obviously, i is wrong!
At a half educated guess, its where the network settings are not set up, hence need the settings!:)

open up a terminal and type this:

```
ifconfig
```

could you paste your result?

---

### Post by kinglee on 2007-12-26
eth0
Link encap:Ethernet   HWaddr 00:1C:23:A3:89:39
inet addr:192.168.1.1    Bcast:192.168.1.255    Mask:255.255.255.0
UP BROADCAST MULTICAST    MTU:1500    Metric:1
RX packets:324  errors:0 dropped:0 overruns:0 frame:0
Tx packets:154  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes: 119783 (116.9KB) TX bytes: 29372 (28.6KB)
Interrupt: 17

lo
Link encap: Local Loopback
inet addr:127.0.0.1     Mask: 255.0.0.0
inet6 addr:  : :1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436    Metric:1
RX packets:530  errors:0 dropped:0 overruns:0 frame:0
Tx packets:530  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 40900  (39.9KB) TX bytes: 40900 (39.9KB)



This is what comes up when i type ifcofig.
Sorry this took so long, i had to type all this in!!

---

### Post by mellowd on 2007-12-26
I would expect your router to get the 192.168.1.1 address, but its not always like that.

could you do this, open a terminal and type:

```
aptitude install traceroute
traceroute www.google.com
```

Paste your results please.

---

### Post by kinglee on 2007-12-26
should i write this all on one commands or two seperate commands on two seperate lines?

---

### Post by mellowd on 2007-12-26
2 seperate lines, sorry. The first one will install the app, the second one will use it

---

### Post by kinglee on 2007-12-26
aptitude install traceroute
Reading package lists... done
building dependancy tree
reading state information... done
initialising package states... done
building tag database... done
E: could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: unable to unlock the administration directory (/var/lib/dpkg/), are you root?
traceroute www,google.com
The program 'traceroot can be found in the following packages:
 * traceroute-nanog (you will have to enable a component called 'universe')
 * traceroute
try: sudo apt-get install <selected package>
bash :traceroute:  command not found

---

### Post by X40nick on 2007-12-26
For Virgin (ex-NTL) broadband all you need to do is plug the cable and and go! Virgin uses the DHCP IP address, so no need to use static.

I don't know why you are having so much problems, considering it is quite easy to set up. Are you sure you have a driver installed for the network card.

And you can copy and paste things! CTRL+C (copies) CTRL+V (pastes) and for the terminal SHIFT-CTRL-C or V

Hope I can help!

Nick.

P.S

I do have Virgin 2MB Broadband, via the STB.

---

### Post by kinglee on 2007-12-26
Maybe i havent a linux driver installed for the wlan card.
its a dell inspiron 1520, celeron crapcessor with a broadcom wireless card.
the reason i cant copy  and paste is that im typing this on my xp machine and my laptop is on, well my lap!!, thrs no network connection beteen the two at the mo.

---

### Post by kinglee on 2007-12-26
and sorry, a connexant network card built in the laptop...

---

### Post by mellowd on 2007-12-26
oops, you need to add sudo in front when installing:

```
sudo aptitude install traceroute
traceroute www.google.com
```

---

### Post by kinglee on 2007-12-26
sorry, i didnt make myself clear.
where can i find the linux ubuntu drivers for a connexant network card as well as the linux ubuntu drivers for a broadcom 54g wireless card.
I really want to use linux but unless i can get this !simple! thing sorted, then its xp all the way for me.

---

### Post by kinglee on 2007-12-26
it looks like it installs this sudo but it still says it cant find traceroute.
shall i just reinstall linux? im not too bothered if i have to

---

### Post by mellowd on 2007-12-26
Where is the router? are you able to connect via the wired connection? you wireless card defiantely isn't being seen, all I can see ith Eth (wired card) and Lo (loopback)

---

### Post by kinglee on 2007-12-26
no! thats my point! i cant even connect via a wired ethernet connection!
ive a feeling there is no driver installed for my connexant network card.. do u know where i can get the driver required??

---

### Post by kinglee on 2007-12-26
im going for some nicotine, this is jarring me!!

---

### Post by mellowd on 2007-12-26
> **kinglee said:**
> no! thats my point! i cant even connect via a wired ethernet connection!
ive a feeling there is no driver installed for my connexant network card.. do u know where i can get the driver required??

You should be able to via the wired connection as linux is definately seeing the ethernet card. what happens when you put it in?

---

### Post by kinglee on 2007-12-26
nothing. i plug the lead in, theres a little pc icon next to the battery indicator that says its connected but when i try to access the net, server cannot be found, ie, not set up.

---

### Post by benrboone on 2007-12-26
From the post of your ifconfig, it looks as if your eth0 (wired ethernet is actually working at least it's configured right)  if  you run ifconfig with your ethernet connected and then run it without it connected.  then post both of them here. I believe that you will not have an IP address with the disconnected cable.  Also to further test this it would be helpful to try pinging the default loop back address: in your terminal type "ping 127.0.0.1"

---

### Post by kinglee on 2007-12-26
thanx, i have no idea what ping means and when i typed this in a terminal it says 64 bytes from 127.0.0.1 and it just repeats and repeats.
all i need, which i asked originally, is the settings for virgin media broadband for this linux thing, where do i get the settings from? this site or would it be from virgin?

---

### Post by SomethingCronic on 2007-12-26
Dont know if this was mentioned, but I had to activate my line before I could use Virgin Media Broadband - Did this in an XP vmware session as the activation cd did not work in Ubuntu (or Vista).

Bit of a pain, but if you phone Virgin and talk through with their terrible support staff they will show you how to do this over a web browser (i think).

---

### Post by benrboone on 2007-12-26
If you are connected to your router by wire normally you don't need to do anything linux and your router will talk to each other and set all settings by dhcp.

Your reply of  64 bytes from 127.0.0.1 is exactly want we wanted. 
this should mean that your card is working and no drivers are needed.
I assume that your previous experience is related to windows.  In windows most of the time you have acquire a driver.  In Linux most of the driver are already included.  Yours seems to be included.

The next thing to try is pinging your router  and then a computer or server on the internet.  I don't know your gateway ip address, so the two easy methods to get it are typeing "route -n" in your terminal and posting the complete result here.  the second method is getting it from your windows computer in the command promt with ipconfig and looking for the gateway line.

Once we get this information we want to ping the gateway type: "ping gateway" substituiong the real ip address for the gateway.  (just so you know you can stop the pinging by control c)

I would also like you to try this type: "ping 64.233.167.104" and see if you get a reply if you do then try "ping www.google.com" 

please post all this info if possible, also feel free to ask for clarification if needed
goodluck

---

### Post by benrboone on 2007-12-26
well if your broadband is working with windows we probally could collect the information need from it.  

1.   IP address
2.   gateway
3.   subnet mask
4.   DNS server

typing "ipconfig /all" in a command prompt in windows 2000, xp or vista should get us the necessary information

---

### Post by AndyCooll on 2007-12-26
> **kinglee said:**
> thanx, i have no idea what ping means and when i typed this in a terminal it says 64 bytes from 127.0.0.1 and it just repeats and repeats.
all i need, which i asked originally, is the settings for virgin media broadband for this linux thing, where do i get the settings from? this site or would it be from virgin?

Just to clarify things a little clearer in your mind so you know what we are trying to do ...

The fact that it is Virgin Media broadband is in actual fact irrelevent to this problem. You only have to setup Virgin Media Broadband to recognise your router, Virgin Media Broadband _only_ talks directly to your router. Your router then acts as a gateway for all your other pc's, regardless of what operating system they are running. And clearly you have already got your router setup correctly to talk to Virgin Media Broadband since your XP machine connects to the Internet using this method (i.e. Your Machine > Router > Internet),

So what these guys are trying to do is successfully connect you to your router, either via wired cable or a wireless connection. Hence we're trying to figure out whether the fault is at the router end of the wire or the pc end of the wire. If your connection is given an IP address it would indicate that your router is fine, though the fact that it seems to 192.168.1.1 seems a little unsual, more common would be to have an address starting from 2, i.e. 192.168.1.2, 192.168.1.3 etc.

:cool:

---

### Post by kinglee on 2007-12-26
right u are.
ip address192.168.1.2
default gateway 192.168.1.1
subnet mask 255.255.255.0
dns server 192.168.1.1

---

### Post by asmiller-ke6seh on 2007-12-26
Hey, other guys:

Remember that Kinglee tried to manually configure his network setup. That configuration might have to be removed to allow the default configuration to take over.

---

### Post by ubername on 2007-12-26
> **kinglee said:**
> right u are.
ip address192.168.1.2
default gateway 192.168.1.1
subnet mask 255.255.255.0
dns server 192.168.1.1

Hi

I am happily using virgin media broadband, and am also a newbie. I suggest going to system>administration>network, then select 'wired connection'. Click on the properties button to the right and select 'Enable Roaming mode'. This works for me, but as I say, I am no expert.

---

### Post by benrboone on 2007-12-26
Quote:
Originally Posted by kinglee View Post
right u are.
ip address192.168.1.2
default gateway 192.168.1.1
subnet mask 255.255.255.0
dns server 192.168.1.1

I assume that these are your settings from windows right?
if that is the case you should be able to change your address from 192.168.1.2 to 192.168.1.3 and keep all your other settings the same
to change these settings go system> Administration> Network
choose wired then click on properties this should bring up a window where a choice of static automatic or local zero config (you may have to take the check out of enable roaming mode)
after choosing static put 192.168.1.3 for the ip address  then in the subnet put 255.255.255.0 in the last box (the gateway box) put 192.168.1.1 then click ok

finally select the DNS tab and click add then add 192.168.1.1 there you may also want to add a second dns from open dns of 208.67.222.222 (not necessary but helpful if your isp ever has DNS problems)

---

### Post by kinglee on 2007-12-31
[QUOTE=ubername;4019329]Hi

I am happily using virgin media broadband, and am also a newbie. I suggest going to system>administration>network, then select 'wired connection'. Click on the properties button to the right and select 'Enable Roaming mode'. This works for me, but as I say, I am no expert.[/QUOTE


thanx, i done that and i was up and running the same nite!
was gonna rip the hd out of this thing but i have the net now.

---

### Post by kinglee on 2007-12-31
> **benrboone said:**
> Quote:
Originally Posted by kinglee View Post
right u are.
ip address192.168.1.2
default gateway 192.168.1.1
subnet mask 255.255.255.0
dns server 192.168.1.1

I assume that these are your settings from windows right?
if that is the case you should be able to change your address from 192.168.1.2 to 192.168.1.3 and keep all your other settings the same
to change these settings go system> Administration> Network
choose wired then click on properties this should bring up a window where a choice of static automatic or local zero config (you may have to take the check out of enable roaming mode)
after choosing static put 192.168.1.3 for the ip address  then in the subnet put 255.255.255.0 in the last box (the gateway box) put 192.168.1.1 then click ok

finally select the DNS tab and click add then add 192.168.1.1 there you may also want to add a second dns from open dns of 208.67.222.222 (not necessary but helpful if your isp ever has DNS problems)

thanx, i sussed that out!

---

### Post by bluemarble on 2008-02-01
I have a problem with my virgin broadband, however I have a wireless USB virgin modem for my laptop. It has its own sim card and I think works on back of the mobile phone network.

Ubuntu does not ever recognise it when i plug it in, i dont have a clue what to do!! 

I really dont want to use windows every time i need the interent.... can anyone help?

cheers

---

