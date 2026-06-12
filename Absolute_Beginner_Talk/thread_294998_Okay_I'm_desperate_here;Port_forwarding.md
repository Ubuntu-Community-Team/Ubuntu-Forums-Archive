---
title: "Okay I'm desperate here;Port forwarding"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-11-07
Man I'm having this problem for a long time and I still haven't managed to get it solved.So I have a router at home and that means if I don't port forward I will be getting 2KB/s speeds when using BitTorrent.

Now what I would like you guys to do for me is explaining me what I have to do "exactly".I successfully port forward in Windows but I can't in Ubuntu.


Please help me.I'm sick of having to wait one day or more for something that could take about 2/3 hours...

PS:Please don't assume I know anything about PF.Last time I asked people threw me the "it shouldn't be that much different from Windows".But I have some problems like the standard bit torrent client not having a settings tab.....etc Most importantly I can't even set a Static IP Adress...

---

### Post by taurus on 2006-11-07
You need to get into your router and there would be a section about firewall.  That's where you open some ports for traffic to come thru.  With my router, I can get to it by typing an ip address into firefox so it doesn't matter what machine or OS I connect to it, I can access it with the same IP.  Is that how you access your router in Windows or is there a program in Windows that comes with your router for you to get to your router?  Did you buy it from an electronic store or does it come with your DSL?

---

### Post by dannyboy79 on 2006-11-07
> **Endow said:**
> Man I'm having this problem for a long time and I still haven't managed to get it solved.So I have a router at home and that means if I don't port forward I will be getting 2KB/s speeds when using BitTorrent.

Now what I would like you guys to do for me is explaining me what I have to do "exactly".I successfully port forward in Windows but I can't in Ubuntu.


Please help me.I'm sick of having to wait one day or more for something that could take about 2/3 hours...

PS:Please don't assume I know anything about PF.Last time I asked people threw me the "it shouldn't be that much different from Windows".But I have some problems like the standard bit torrent client not having a settings tab.....etc Most importantly I can't even set a Static IP Adress...

i am trying to understand something here, you don't port forward anything winbloz or ubuntu, you port forward PORTS from your router to the computer you want the ports to show up on. So, when you bittorrent on winbloz, you set your router to foward ports 6881-6889 to the ip address of your winbloz box, well at least that's what you should have done. The reason this has to happen is because your lan ip is different than you wan ip, your wan ip is something like 67.189.54.03 and you lan ip is most likely something like 192.168.0.3. So what is happening is that your telling your router that if it gets traffic on ports 6881-6889, it should forward those packets/traffic to ip 192.168.0.3, your winbloz box. Are you following yet?? If you still have a question please ask it. Also, if you are only getting speeds of 2/3kb, you should close your torrent and get this resolved instead of leaving it openb for a week and trying to still get the torrent files, the reason i say this is because your leeching from everyone and NOT sharing. you need to get this resolved before you click on anymore torrents!

---

### Post by Endow on 2006-11-07
This was the guide is use don Windows

[http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-5100W/BitTorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Billion/Bipac-5100W/BitTorrent.htm)


But it doesn't work for Ubuntu cause I can't even get a Static IP adress in the first place because there aren't enough spaces on System->Administration->Networking to fill up...

---

### Post by dannyboy79 on 2006-11-07
Putting this lightly, you're not making sense. I have a static ip set for my ubuntu box. also, you don't need to set it to be static, can you go into your router config and do what's called address reservation? it's where you tell your router to hand out a certain ip to this certain mac address everytime, that way you can still use dhcp but you'll ensure that your ubuntu box gets the same ip from the router everytime. also, you can't have your router port forward the same ports to 2 different ip addresses. if you have a specific question, ask it.

---

### Post by Endow on 2006-11-07
You're the one not making sense :p  at least I'm not understanding you...

I'm a noob in this sort of drill I only port forwarded once using that tutorial.The tutorial I mentioned has windows in mind.What I'm asking you guys is what do I need to do then (seeing as how the process seems different on Ubuntu;at least that's what I'm understanding from you..) in order to port forward.Can you tell me exactly what to do?My main objective beeing to get normal speeds when using bittorrent.(if for some reason that doens't involve port forwarding im ok with it as well).

Please don't throw in too many technical mumbo jumbo cause I don't get most of it.

Story is repeating itself once again ...I just want someone to tell me things step by step (it can't be that hard)

---

### Post by chocbar31 on 2006-11-07
Same excact process! LOL Only difference is that you may have used internet exploder...I mean internet explorer as opposed to maybe firefox now.

Anyways, don't miss the part where it displays a big picture to open your web browser and type [http://192.168.0.1]("http://192.168.0.1")

However, in my case, my 1st router uses [http://192.168.1.1]("http://192.168.0.1") to gain access.

To make this sound a bit easier...I say "Open up a port".

Oh yea, your router does have a static address, which is what that website is reffering to! **"Do not skip this step!"**

---

### Post by Endow on 2006-11-07
But I don't have info about Default Gateway when i type ifconfig on the terminal!

Oh and the default bit torrent client doens't have any setting tab where I can change those things (which port to start from..etc)

---

### Post by taurus on 2006-11-07
Don't worry about any setting tab in bittorrent!  Open firefox and in the address field, type 

```
192.168.2.1
```
to access your router.  You need to use "admin" as your username and whatever password you created.  In there, look for firewall option, advance setting, etc., like the screenshots!!!

---

### Post by dannyboy79 on 2006-11-07
follow the tutorial and when you get to something you don't understand, ask us the specific quesiton and we'll answer it for ya. the default gateway is gonna be the same as it is in winbloz!
when you setup winbloz to use bittorent did you go into the config settings for your router? If answer is yes then do the same thing but from ubuntu web browser. whatever ip you entered previously for winbloz, well enter the ip that is your ubuntu ip. we can't help you if you don't try to help yourself in the least bit. I personally am not just gonna spoon feed ya, you need to actually understand what you're doing and it sounds like you just want it to work without understanding which you won't learn anything this way. here is a how-to for ya if you don't know how to use the default bittorrent client in gnome, i myself actually use bittornado and love it: [http://www.ubuntuforums.org/showthread.php?t=86064](http://www.ubuntuforums.org/showthread.php?t=86064)

---

### Post by Endow on 2006-11-07
I AM doing it myself but like I said before I'm stuck because I need to have a static ip adress and I dunno the default gateway.

Are you saying I need to reboot in order to go to winbloz to know what my default gateway is?Isn't there some kind of command?

---

### Post by taurus on 2006-11-07
> **Endow said:**
> I AM doing it myself but like I said before I'm stuck because I need to have a static ip adress and I dunno the default gateway.

Are you saying I need to reboot in order to go to winbloz to know what my default gateway is?Isn't there some kind of command?

Have you tried to get into your router with the IP address that I gave you???

---

### Post by dannyboy79 on 2006-11-07
> **Endow said:**
> I AM doing it myself but like I said before I'm stuck because I need to have a static ip adress and I dunno the default gateway.

Are you saying I need to reboot in order to go to winbloz to know what my default gateway is?Isn't there some kind of command?

post the complete results of ifconfig please. your default gateway can be determined from that. also, have you tried to log into your router yet,  you can set the ip of your ubuntu box to be static by using a common feature within routers which is called address reservation, where you tie a mac address to a certain ip, that's what we can do if you can't figure out how to setup ubuntu with a static ip which isn't even that hard. have you tried to gogle for help????? there's gotta be a million guides on how to setup a static ip within ubuntu.

---

### Post by Endow on 2006-11-07
I've found none.Taurus , yes I can enter my router's "contorl panel" using [http://192.168.1.254](http://192.168.1.254)

---

### Post by CatKiller on 2006-11-07
> **Endow said:**
> Most importantly I can't even set a Static IP Adress...

System -> Administration -> Networking.
Click on "Ethernet Connection".
Click on "Properties".
Select "Static IP address" from the dropdown Configuration list. Select 192.168.1.2 unless you know that the static IP address you configured in Windows for this computer was different. If it **was** different, put that one in instead.
Select 255.255.255.0 as your Subnet mask, again unless you know it should be something different.
Select 192.168.1.1 as your Gateway address, unless you know that the address of your router is different.
Click OK.
Click Activate.
Click OK.
Restart your computer.

It **really** isn't hard. And it **really** isn't hard to explicitly say what you've done, what error messages you've received, and to be nice to the people that you'd like to help you.

---

### Post by dannyboy79 on 2006-11-07
> **CatKiller said:**
> System -> Administration -> Networking.
Click on "Ethernet Connection".
Click on "Properties".
Select "Static IP address" from the dropdown Configuration list. Select 192.168.1.2 unless you know that the static IP address you configured in Windows for this computer was different. If it **was** different, put that one in instead.
Select 255.255.255.0 as your Subnet mask, again unless you know it should be something different.
Select 192.168.1.1 as your Gateway address, unless you know that the address of your router is different.
Click OK.
Click Activate.
Click OK.
Restart your computer.

It **really** isn't hard. And it **really** isn't hard to explicitly say what you've done, what error messages you've received, and to be nice to the people that you'd like to help you.

if he logs into his routers config panel using 192.168.1.254, than isn't this what he should put for his default gateway address?

---

### Post by CatKiller on 2006-11-07
> **dannyboy79 said:**
> if he logs into his routers config panel using 192.168.1.254, than isn't this what he should put for his default gateway address?

As far as I know, yes.

---

### Post by Endow on 2006-11-07
CatKiller I resent that comment.I wasn't inconvinient (sp?) with anyone.I was just stating my problem and expected a more straightforward answer(since setting a static ip adress is the first step and since I told you guys I couldn't do it because of ifconfig).


Btw I check on windows and there using ipconfig I get 192.168.1.1 Ip adress.Using ifconfig on ubuntu I get 192.168.1.2.I should be using the first one then?

---

### Post by dannyboy79 on 2006-11-07
> **Endow said:**
> CatKiller I resent that comment.I wasn't inconvinient (sp?) with anyone.I was just stating my problem and expected a more straightforward answer(since setting a static ip adress is the first step and since I told you guys I couldn't do it because of ifconfig).


Btw I check on windows and there using ipconfig I get 192.168.1.1 Ip adress.Using ifconfig on ubuntu I get 192.168.1.254.I should be using the first one then?

use the 192.168.1.1 for what? no you shouldn't use that for anything, that's the ip of your winbloz box. the ip of your ubuntu box is the same but with ending .254? i find that hard to believe, you do have a router correct? i thought you said that you use 192.168.1.254 to log into your router so then it would be impossible for your ubuntu box to have the same ip as your router! why don't you help us help and POST YOUR IFCONFIG like I asked a few threads back. I don't mean to yell but it's really iritating trying to help some1 but they don't don't listen. if you want our help, then post the output of what we ask or do what we are suggesting.

---

### Post by Endow on 2006-11-07
I'm sorry I misspasted the ip.It's 192.168.1.2.Or at least it was.I did what CatKiller said and used the 192.168.1.1 from windows and now the ifconfig says it's 192.168.1.1 and not192.168.1.2 like last time...


Here you go :



wlan1     Link encap:Ethernet  HWaddr 00:0C:F6:1B:03:FC
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe1b:3fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:466 errors:1070 dropped:0 overruns:0 frame:1070
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:546032 (533.2 KiB)  TX bytes:48892 (47.7 KiB)

---

### Post by dannyboy79 on 2006-11-07
> **Endow said:**
> I'm sorry I misspasted the ip.It's 192.168.1.2.Or at least it was.I did what CatKiller said and used the 192.168.1.1 from windows and now the ifconfig says it's 192.168.1.1 and not192.168.1.2 like last time...


Here you go :



wlan1     Link encap:Ethernet  HWaddr 00:0C:F6:1B:03:FC
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe1b:3fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:466 errors:1070 dropped:0 overruns:0 frame:1070
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:546032 (533.2 KiB)  TX bytes:48892 (47.7 KiB)

alright, wait, did you already set your ubuntu box to have static ip 192.168.1.1? if so, and you can still get on the internet and your winbloz box can still get on the internet, then next we need to go into your router config setup and forward the same ports that you used to forward to winbloz to now forward them to ubuntu box, which you're telling me is 192.168.1.1 correct? are you dual booting? you didn't tell us that if so which makes a difference! well I guess this would work to your advantage if you setup both os's with the same ip, that way your router can forward bittorent traffic to 192.168.1.1 and it's gonna work whether you're in winbloz or in ubuntu if your dual booting that is. so if your winxp box used to be 192.168.1.1 and bittorent worked, then it should work on ubuntu now that you have set it to have the same ip! 1 last thing is to make sure you are forwarding the same ports that are configured within your bittorent client. do you remember what ports you're forwarding? if not, then go into your router config and find out. also, while you're in there, make sure that you are forwarding those ports to the ip that you set your ubuntu box to, which is 192.168.1.1 based on what you said.

---

### Post by Endow on 2006-11-07
Thing is I don't even have bit torrent installed on Windows anymore.I'm trying to giving up on windows altogether (and im trying to make my family do it as well).

Also what do you mean by ubuntu box??Yes I'm surfing using a  192.168.1.1 Static IP adress right now(that's out of the way).(seeing as how I don't have bittorrent in windows I can't check which ports I used to use but I'm pretty sure the guide I used back then said they were pretty random provided they were bigger than a certain number or something like that)

---

### Post by dannyboy79 on 2006-11-07
i am going to stop helping you if you don't read my posts thoroughly and respond to all the questions and or suggestions. i'll simply copy and paste my old thread so that you READ IT and provide me with the answers I NEED SO I CAN HELP YOU. then next we need to go into your router config setup and forward the same ports that you used to forward to winbloz to now forward them to ubuntu box, which you're telling me is 192.168.1.1 correct? are you dual booting? you didn't tell us that if so which makes a difference! well I guess this would work to your advantage if you setup both os's with the same ip, that way your router can forward bittorent traffic to 192.168.1.1 and it's gonna work whether you're in winbloz or in ubuntu if your dual booting that is. so if your winxp box used to be 192.168.1.1 and bittorent worked, then it should work on ubuntu now that you have set it to have the same ip! 1 last thing is to make sure you are forwarding the same ports that are configured within your bittorent client. do you remember what ports you're forwarding? if not, then go into your router config and find out. also, while you're in there, make sure that you are forwarding those ports to the ip that you set your ubuntu box to, which is 192.168.1.1 based on what you said.

---

### Post by dannyboy79 on 2006-11-07
i gotta go, all i can tell you from here on out is that I use ports 49193 as the starting port and 50001 and then end port. you'll have to figure it out on your own or wait until I get back, which should be in about 30 minutes from now.

---

### Post by Endow on 2006-11-07
The thing here is I'm not understanding the process...Yes I am dualbooting Ubuntu/Windows.

The thing is you are talking about which ports to forward : right now I have now way to know.I mean I no longer have bittorrent setup in windows.And I don't know how to check it in ubuntu (using the router0s control panel).


Yes, for all intents and puposes Ubuntu's ip' adress is now 192.168.1.1.
But you didn't clear that "ubuntu box" stuff either.For me to answer your questions I need to know what you are tlaking about too :p 


> 1 last thing is to make sure you are forwarding the same ports that are configured within your bittorent client.

Well how do I know which??The standard bittorent doesn't have a settings tab.
And if I need to check that up on the control panel (the router's) where excatly do I get that info?I'm not seeing it 'round here...

---

### Post by podunk on 2006-11-07
The way i did it was:

I used Ktorrent from the repositories. It was a lot easier for *me* to set up, the interface looked familiar and "clicky."

System>Administration>Synaptic Package manager. Click search. Type in Ktorrent. Click OK. When the program comes up in the search field right click and chose Install. Click the Apply button at the top. Close the manager.

I <blush!> went into Windows to get all my network information. 
Start>Settings>Network Settings>Local Area Network

for instance my network config is:
IP Address 192.168.1.96
Subnet   255.255.255.0
Default Gateway 192.168.1.254

I clicked "Details and found
DNS Server 192.168.1.254
{Note - if you have a Windows network that you wish to share with your Linux machine write down the WINS also - you'll need it for Samba)

I closed windows <phew!> and started Ubuntu.

System>Administration>Networking
Click the network card that connects to the Internet. (eth0 for me)
Click Properties (note, many of these things will need to be done before you can run Samba)
Click the Configuration selector and chose "Static IP address"
Enter the info from your Windows install
Click OK
Click the General tab and make sure you have a hostname there. (For Samba later on enter the domain name for your Windows network)
Click DNS. On mine the DNS was already there - but if not click the "Add" button and enter the number from windows.

Click hosts - you won't have to add anything here - just remember where it is when you do Samba networking. :-)

Click Close.

Open Ktorrent Applications>Internet>Ktorrent
Settings>Configure Ktorrent

In "Port" enter 6881
UDP Tracker 444
Max uploads 4
Close Ktorrent

Open Firefox
In the address bar type your DNS (for me 192.168.1.254)

You may have to read your documentation, I have a Westel. I'm sure other brands have a slightly different menu system. Hopefully you'll click on enough stuff to find something similar to mine. Note - the first time I opened my router I had to enter my ISP assigned username and password

Expert Mode>Configure>Connection. DO **not** enter your windows information here - leave it alone. :-)
Configure>Nat (Network Address Translation) > Define Custom service
On the menu that opens click "Port forwarding"
Enter a name I used Ktorrent
My Port range was  6880-6889 
Base host     444
TCP
Click next
Click OK (If it doesn't work at this point you really will have to read the manual for your router)
Click the selector thingie and go down to the service you just enabled. Click it, then click Enable. A little box will pop up with each computer on your network - chose yours and click done.

Open Ktorrent, paste in the URL and go.

Some ISPs try to discourage torrents, the way around that is to use UPnP - which I didn't have to do. My torrent speed jumped up significantly.

---

### Post by RasutoIbuki on 2006-11-07
Okay, if you got the ports forwarded and it worked fine in Windows, the problem probably is you're not opening your firewall up to it. Go to the repositories and get FireStarter. Once you start it the easiest way to get your torrents to work is to press the stop button at the top.

Try that out.

---

### Post by Endow on 2006-11-07
podunk> I did what said but in the end I still get 2KB/s speeds.

Dont you mean ---> UDP Tracker 4444 ?

---

### Post by dannyboy79 on 2006-11-07
ubuntu doesn't have any ports blocked by default. at least not on my box. i haven't edited iptables or firestarter and I get around 125kb/sec download and about 40kb/sec upload. i use the svn version of bittornado and once you click on a bittorrent file, you can then go within settings, then change the ports that you have forwarded within your router.

according to a forum moderator, this is what he says about the default firewall:
Yes there is, IPTABLES, but it doesn't have any rules by default. In other words, it's not enabled.

---

