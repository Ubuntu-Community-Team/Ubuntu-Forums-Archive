---
title: "This is really starting to tick me off!"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by doncasteel8587 on 2007-04-14
WARNING THIS IS A RANT!

I'm not stupid, or incapable or a computer noobie. 
I'm a mechanical engineer and application developer/programmer who would like to transition to a non-Microsoft OS.

I've been reading the forum and FAQ's and docs, before asking for help, as requested.
I'm not the only one having trouble with networking the threads are loaded with struggling beginers

But you people need to help us "Absolute Beginers" a little.

HERE'S THE CRITICAL STEP:
Create a downloadable documentation archive that has ALL OF THE REQUIRED INFORMATION for setting up and connecting to the internet!

		NO HYPERLINKS!
		
Let me say that again

		NO HYPERLINKS!

If I can't connect to the internet, hyperlinks do me no good whatsoever!

Let me say that again

			If I can't connect to the internet, hyperlinks do me no good whatsoever!
			
I am willing and able to contribute to making this happen if I can ever get ubuntu working.


--------------------------------------------------------------------------------------------
Here's what I've done so far this morning......

file:///media/usbdisk/Networking%20guide/WifiDocs-WirelessTroubleShootingGuide%20-%20Community%20Ubuntu%20Documentation.htm

The documentation tells me this:
--------------------------------------------------------------------------------------------
			3.2.4. Check driver
			
			    *
			
			      If you ran lshw and saw a driver bound to the device then let's test to make sure it's communicating to the kernel.
			         1.
			
			            run the command lsmod to see if driver is loaded. (look for the name that was listed under lshw). If you did not see it in the list then use the modprobe command to load it.
--------------------------------------------------------------------------------------------

Running lshw gives me this information (plus a ton of other stuff I've trimmed out)
--------------------------------------------------------------------------------------------
           *-communication UNCLAIMED
                description: Communication controller
                product: PCI6515 SmartCard Controller
                vendor: Texas Instruments
                physical id: 1.5
                bus info: pci@03:01.5
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:dfcfc000-dfcfcfff iomemory:dfcfd000-dfcfdfff irq:5
           *-network DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@03:03.0
                logical name: eth1
                version: 02
                serial: 00:14:a4:2a:79:a5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:dfcfe000-dfcfffff irq:201
--------------------------------------------------------------------------------------------
driver=bcm43xx 


running lsmod gives me this:
--------------------------------------------------------------------------------------------
			pcspkr                  4352  0 
			bcm43xx               127252  0 
			ieee80211softmac       33792  1 bcm43xx
			ieee80211              35272  2 bcm43xx,ieee80211softmac
			ieee80211_crypt         7552  1 ieee80211
--------------------------------------------------------------------------------------------
Docs say:

    *
         3.

            run the command iwlist to scan for a router. If an access point is identified this is a second identifier which shows the driver as communicating and shows that it's probably working as it can complete a wireless interface task. (note not all cards support scanning so this may not work for you) 
--------------------------------------------------------------------------------------------
		ubuntu@ubuntu:~$ iwlist
		Usage: iwlist [interface] scanning
		              [interface] frequency
		              [interface] channel
		              [interface] bitrate
		              [interface] rate
		              [interface] encryption
		              [interface] key
		              [interface] power
		              [interface] txpower
		              [interface] retry
		              [interface] ap
		              [interface] accesspoints
		              [interface] peers
		              [interface] event
		ubuntu@ubuntu:~$ iwlist accesspoints
		lo        Interface doesn't have a list of Peers/Access-Points
		
		eth0      Interface doesn't have a list of Peers/Access-Points
		
		eth1      Interface doesn't have a list of Peers/Access-Points
		
		sit0      Interface doesn't have a list of Peers/Access-Points
		
		ubuntu@ubuntu:~$ iwlist scanning
		lo        Interface doesn't support scanning.
		
		eth0      Interface doesn't support scanning.
		
		eth1      No scan results
		sit0      Interface doesn't support scanning.
		
		
--------------------------------------------------------------------------------------------

Here's where the documentation quits, no more information is given on what to do if access points AREN'T loaded

So what's the next step?

---------------------------------------------------------------------------------------------

		3.2.5. Driver looks ok, device disabled
		
		    *
		
		      Newer laptops come with features to disable the wireless radio to save battery when not in use. Usually this is switched by a FN+Fx key combo or specific button for the purpose. It is possible driver and everything is ok but the wireless device is in the disabled state and can't be used. Using the designated key(s) in linux sometimes does not work.
		
		      Usually this is apparent by running the lshw command you see *-network:1 DISABLED or if you run the iwconfig command you see eth1      NOT READY!.
		
		      So how do you rectify this? It varies so much the exact solution can't be put here in this document for all the different models. So... 
		
		   1.
		
		      Look at the LaptopTestingTeam page here on the wiki to see if your laptop is listed with any information.  [https://help.ubuntu.com/community/LaptopTestingTeam](https://help.ubuntu.com/community/LaptopTestingTeam)
		   2.
		
		      Do a google search using terms such as manufacture, model, linux, wireless, enable, button, radio....etc. When searching and finding similar pages that don't help, use words that are used in those pages to help you search.
		   3.
		
		      Go to the [WWW] ubuntu forums and ask, maybe someone else has the same laptop and knows the work around. 
---------------------------------------------------------------------------------------------
OK....  now I'm really getting ticked off!

First of all, you guys need to get a clue!
I'm trying to use the documentation BECAUSE I CAN'T CONNECT TO THE INTERNET!!! So why do the docs have all the information linked to the internet?
YOU'VE GOT TO BUILD A NETWORKING GUIDE THAT'S SELF CONTAINED!!! If I can't connect to the internet the links do me no good whatsoever!

Ok.... shut down ubuntu.... reboot to Windows..... get on:confused: line and enter the link.....

[https://help.ubuntu.com/community/LaptopTestingTeam](https://help.ubuntu.com/community/LaptopTestingTeam)

Guess what! it gives me this:		
---------------------------------------------------------------------------------------------
			LaptopTestingTeam
			This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists. 
---------------------------------------------------------------------------------------------

COME ON PEOPLE! 
DO YOU WANT PEOPLE TO USE THIS UBUNTU OR NOT?

---

### Post by tchoklat on 2007-04-14
Yo! hand on 'bro!
 
If you can't connect to the internet to use the hyperlinks - how the $%^& do you read the forum?

---

### Post by caffienefree on 2007-04-14
The correct page for what you're looking for is [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

This guide will help you get it set up using ndiswrapper. [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I don't see why there's a need for what you're asking for. If you're posting here, it means that you have a network connection from somewhere. You can therefore either print out the guide, or save a copy of the webpage. The reasons for having linked paged is because there is no grand unified howto for wireless. There is a unified troubleshooting guide, but no surefire solution for everyone.

---

### Post by dptxp on 2007-04-14
> **tchoklat said:**
> Yo! hand on 'bro!
 
If you can't connect to the internet to use the hyperlinks - how the $%^& do you read the forum?

Have a heart. He is obviously using some other PC, or dual boot, triple boot, quad.........

---

### Post by xpod on 2007-04-14
> I'm not stupid, or incapable or a computer noobie.
I'm a mechanical engineer and application developer/programmer who would like to transition to a non-Microsoft OS.

Me thinks this is the problem...

You really need to accept that you ARE in fact a noob when it comes to any new OS:D 
Once you get that out of the way the rest will be a stroll in the park hopefully.

Good luck anyway and welcome to the forums

---

### Post by tchoklat on 2007-04-14
... therefoer he can follow the hyperlinks to see what the issue may be.
 
Ubuntu forums are maintained by a community and hlep is provided as able. I sometimes am unable to get the assistance that I need, though I do perservere and dont go off the handle!

---

### Post by doncasteel8587 on 2007-04-14
I'm probably going to get some *snip* remark like:
         "Then how did you post this thread"

(I saw some *snip* post that in one of the other threads I was reading).

The answer is duh.... I had to reboot my system to MS Windows to get online, and yes that ticks me off because each time I have to swich operating systems it takes 5 minutes, and I loose my train of thought, and everything just becomes more frustrating.

Boot to windows
Remember what I was thinking
Get online and read some stuff
Figure out some things to try
Re-boot to Ubuntu
Remember what I was thinking
Navigate an unfamiliar system and try the stuff
Find out it doesn't work
Think of other things that may help
Re-boot to windows 
Remember what I was thinking

Get online and read some stuff
Figure out some things to try
Re-boot to Ubuntu
Remember what I was thinking
Navigate an unfamiliar system and try the stuff
Find out it doesn't work
Think of other things that may help
Re-boot to windows 
Remember what I was thinking

Get online and read some stuff
Figure out some things to try
Re-boot to Ubuntu
Remember what I was thinking
Navigate an unfamiliar system and try the stuff
Find out it doesn't work
Think of other things that may help
Re-boot to windows 
Remember what I was thinking

Get online and read some stuff
Figure out some things to try
Re-boot to Ubuntu
Remember what I was thinking
Navigate an unfamiliar system and try the stuff
Find out it doesn't work
Think of other things that may help
Re-boot to windows 
Remember what I was thinking

Get online and read some stuff
Figure out some things to try
Re-boot to Ubuntu
Remember what I was thinking
Navigate an unfamiliar system and try the stuff
Find out it doesn't work
Think of other things that may help
Re-boot to windows 
Remember what I was thinking

---

### Post by Maestro23 on 2007-04-14
Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

You can keyword search "ndiswrapper" and "wireless network card".  Will find many HOW-TO's on various wireless cards and installing.

---

### Post by ESPOiG on 2007-04-14
wireless is hard for begineers, i remeber havin to help someone do theres it aint trouble free and instead of entering to pass, you end up downloading an app and setting all sorts of things like channel encryption settings specific ip etc, it is quite alot harder for someone hwo came form windows and is now trying to use linux and do the same thing

---

### Post by doncasteel8587 on 2007-04-14
> **xpod said:**
> You really need to accept that you ARE in fact a noob when it comes to any new OS:D 


No *snip* Sherlock....
This is not helpful

What I need is documentation that doesn't require the internet to use

---

### Post by DaDave on 2007-04-14
Everyone needs to blow off a little steam now and then. Rant is no problem with me. Sorry forum, but I tend to agree a little. At times it's much easier and faster to just figure out the problem yourself than to find the answer on the forum. Sometimes. Not much can be done about that. Fortunately, Ubuntu isn't all that complicated or confusing. On the good side, this forum is way better than "the windows handbook".

---

### Post by caffienefree on 2007-04-14
> **doncasteel8587 said:**
> No *snip* Sherlock....
This is not helpful

What I need is documentation that doesn't require the internet to use

You're not going to get anywhere antagonizing people. If you had read my above post:

> **caffienefree said:**
> The correct page for what you're looking for is [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

This guide will help you get it set up using ndiswrapper. [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I don't see why there's a need for what you're asking for. If you're posting here, it means that you have a network connection from somewhere. You can therefore either print out the guide, or save a copy of the webpage. The reasons for having linked paged is because there is no grand unified howto for wireless. There is a unified troubleshooting guide, but no surefire solution for everyone.

You'd have realized that I already answered your question. You're going to need some way of transferring the drivers to ubuntu, so just save a copy of the webpage for reference when you transfer the drivers. 

Have a nice day.

---

### Post by drbob07 on 2007-04-14
Also may I reccomend printing some stuff out, I had to use internet at my dad's work and print out about 10 pages before I ever got my card working.

First off, I reccomend disabling security on your network for the time being. It was 100x easier getting myself on an unsecured network than it was getting WPA set up.

Secondly, most laptops have Ethernet, I reccomend connecting through that, it should set up seamlessly with no problems, then you will be able to at least browse the internet without having to boot back into Windows to solve your problems
(Since it's a laptop I assume it has an Ethernet Port, and that access to your router isn't very difficult)

Also, this guide looks like it may be of some help: 
[http://ubuntuforums.org/showthread.php?t=285809&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=BCM4318)

---

### Post by Maestro23 on 2007-04-14
> **caffienefree said:**
> You're not going to get anywhere antagonizing people. If you had read my above post:



You'd have realized that I already answered your question. You're going to need some way of transferring the drivers to ubuntu, so just save a copy of the webpage for reference when you transfer the drivers. 

Have a nice day.

Just to add to your post.  If the OP runs into any dependency issues, he might need to get packages from Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by seshomaru samma on 2007-04-14
I think you have a point - there is no point in hyperlinks when the document is about connecting to the internet

however my suggestion is first we try to solve your internet problem
then you can make a suggestion to the developers to change the documentation

what you should understand though that people here in the forum are all users like you , none of the ubuntu developers are active here (as far as i know) 

sadly , i don't use wireless so i cant help you, i know though that if you put the name of your wireless device in the search box if this forum you will probably find a solution 

you can then save it as html in your windows partition. ubuntu can read documents from windows partitions so you can access it when you boot into ubuntu
if you dont know how to mount a windows partition read [here]("http://www.psychocats.net/ubuntu/mountwindows") (save it as html for later

---

### Post by qamelian on 2007-04-14
> **doncasteel8587 said:**
> No *snip* Sherlock....
This is not helpful
Neither is your attitude. If you expect people to help you should at least behave in a rational, civil manner. Frankly, someone that opens a thread with ignorant rant that you did would be the last person I'd be inclined to assist.

Calm down and be reasonable. There are a lot of great people on this forum who are will to help you along the learning curve.

---

### Post by xpod on 2007-04-14
> No *snip* Sherlock....
This is not helpful

It`s elimenatry dear doncasteel8587:D 

>  
What I need is documentation that doesn't require the internet to use

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Anyway,good luck & ......have fun!!

edit: oop`s same link...oh well

---

### Post by doncasteel8587 on 2007-04-14
Apologies to the forum for my ranting

Thanks to those who provided helpful replies

Best of luck to everyone.

---

### Post by K.Mandla on 2007-04-14
Your apology is accepted. ;)

It can be frustrating to venture into unknown territory, and that's why the forum is here. If you run into more problems, please let us know and there are a lot of people who will try to help. :D

---

### Post by bapoumba on 2007-04-14
@ doncasteel8587: [https://help.ubuntu.com/]("https://help.ubuntu.com/") has pdf docs you can download and read from you other OS. Not sure all you need is in there, I have not followed all your story ;)

---

### Post by louieb on 2007-04-14
>  HERE'S THE CRITICAL STEP:
Create a downloadable documentation archive that has ALL OF THE REQUIRED INFORMATION for setting up and connecting to the internet!

        NO HYPERLINKS![COLOR=Blue]warning Cafe stuff...[/COLOR] Its easy as eating cherry pie. You find an active Ethernet wire and plug it in the NIC. Thats **[COLOR=Red]all of the required information[/COLOR]**   you need. 
I've worked in IT since 1979. Set up my first work group  in the mid 80's using Win3.11 on a couple of  IBM PS2 computers.  Man those were the days. 

Oh I see you want **wireless** internet. I finally broke down and got a laptop last week and put Linux on it. Had wireless up and running **in only 2 days**. You've seen the wireless drill first you got to figure out what you've got. Me I'm a software guy and i don't give a damn about chip sets; hardware should just work. :rolleyes: I had a couple of pcmica wireless card around both were the same brand (different models) and  two completely different chips sets requiring different drivers. Bla...bla...bla.  two different solutions . 
But its nice to see you got big dreams.  Me I dreamed small I just wanted to get away from using **Sneaker net** :D. 
One last thing; as a programmer I'm a lousy user manual writer. Don't kick some programmer (we bite).   Find the documentation guy and kick him.

BTW: I found my solution here by doing  a search on the wireless cards chip set.

---

### Post by itzpapalotl on 2007-04-15
A little shameless self-promotion here.....

I have had no end of problems with bcm43xx and fwcutter and NDISWRAPPER and all of it. If have a NX9600 laptop (basically a server in a laptop form) and that internal  Broadcom card was the ONLY thing that didn't stand up and salute after I installed Dapper. 

I did in fact finally give up. (well, finally has yet to happen, but for now...) 
I needed wireless. NOW. with no problems.

The following post is a rough outline of my work-around. It's gaming the system rather than solving the problem, (Which frankly I have no doubt can and will be solved by the stupendous development team at Ubuntu... eventually) but it puts me in a place where I can wait. Plus a Mechanical Engineer like yourself will probably be able to follow the second bit about soldering USB connections to the power leg.

Have look. It's end game for wireless, if you don't mind cheating.. ;)

[http://ubuntuforums.org/showthread.php?t=410440](http://ubuntuforums.org/showthread.php?t=410440)

Ubunutu, Debian and the whole Opensource thing are the true future of computing in the business world. Welcome aboard the sometimes turbulent ride! Folks here are VERY helpful, and we need input from all over. Maybe blunt the edges a bit, but...  I understand your complaint. It was mine as well. Ubuntu will catch up. Wireless is the thorn... But I feel certain that the Ubunutu Developers are looking for the correct set of tweezers to remove it.

Luck!

---

