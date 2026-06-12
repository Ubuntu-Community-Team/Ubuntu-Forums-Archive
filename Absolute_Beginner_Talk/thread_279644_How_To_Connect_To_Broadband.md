---
title: "How To Connect To Broadband ?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by darshshinde on 2006-10-18
hello guys ,
i am a ubuntu newbie and m slowly learning to learn things n ubuntu .. but the gr8test hindrance is that i am not able to connect to internet on ubuntu ..the day i do that, i m gonna dump xp for gud ..;) 

i am using a pentium 4 1.6 ghz pc, with 80 gb hard disk, 384 mb ram, 845 chipset motherboard, tnt2 riva 16 mb graphics card. I have dlink ethernet network card installed.

I have dual boot system, running windows xp sp2 & ubuntu 6.06 LTS version. I connect to internet via a boardband provider, who provides connectivity via a dhcp server (that's what he said he me when i tried to get his help on starting net on ubuntu - he could not though !) well in xp all i need is to make a connection for the first time was via a wizard which prompts me to make a choice of type of connection. i made a choice of a connection in which i have to enter a username and password (which my isp gave me)after which i get connected to net via the network. ubuntu shows windows netwrk in network place,(that means it detects my ethernet card) but i dont know the step by step method by which i can connect to net. the isp has provided 2 ip addresses, which are of the server which gives me the connectivity. now what should i do which the settings in netwrk tools menu in ubuntu or somewhere else to get connected.. ? also a thing i forgot to mention .. i use a static ip adress for my pc everytime i log on .

plz help , or i'll will have to](*,) 
darshu:-D 

PS_ is there small patch which would load my ntfs partitions into ubuntu just by click - without typing those commands which i fear might ruin my installation ?:-k

---

### Post by ReaderRat on 2006-10-18
(PS)
[**Mount Windoze Partition**](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by caravel on 2006-10-18
> **darshshinde said:**
> I have dual boot system, running windows xp sp2 & ubuntu 6.06 LTS version. I connect to internet via a boardband provider, who provides connectivity via a dhcp server (that's what he said he me when i tried to get his help on starting net on ubuntu - he could not though !) well in xp all i need is to make a connection for the first time was via a wizard which prompts me to make a choice of type of connection. i made a choice of a connection in which i have to enter a username and password (which my isp gave me)after which i get connected to net via the network. ubuntu shows windows netwrk in network place,(that means it detects my ethernet card) but i dont know the step by step method by which i can connect to net. the isp has provided 2 ip addresses, which are of the server which gives me the connectivity. now what should i do which the settings in netwrk tools menu in ubuntu or somewhere else to get connected.. ? also a thing i forgot to mention .. i use a static ip adress for my pc everytime i log on .

I'm slightly confused.  You mention a DHCP server, yet you use a static IP address?  Have you not tried going into the network configuration and configuring ppp to connect with your username, password[COLOR="Silver"], the static IP[/COLOR] and your primary and secondary DNS servers?  What type of modem are you using, and have you noted down all of the network settings from XP to assist you in configuring this?  Are you using a broadband/adsl router, USB modem or other?

-Edit: **HereInOz** (see below) is right, the static IP is *still* assigned by your ISP.

---

### Post by pradeepadapa on 2006-10-18
hii,

       caravel is right u said that u use DHCP to connect to the net, that means u hav an random ip generation but not static, but u also told that u use some static ip address, plse explain clearly so that we can sort out ur problm.

bye.

---

### Post by electroconvulsive on 2006-10-18
OK first to answer your question about mopunting your NTFS partitions. Check out this thread. 

[http://ubuntuforums.org/showthread.php?t=255896&highlight=ntfs+-3g](http://ubuntuforums.org/showthread.php?t=255896&highlight=ntfs+-3g)

It is a lot simpler than the methiod i have employed and if you have any trouble with it you can post on the thread and the guys there will help out.
Its pretty hard to ruin ether installation (XP or Ubuntu using the NTFS-3G driver to access the NTFS partitions so don't worry about that.

Now to your connection problems. You are using a network cable to connect your computer to your modem arent you? . First you will have to look at your modem setup through your browser (the same as you do through XP and internet explorer). Pretty much it would be wise to get to your modem in XP and check the settings. Please tell us the brand of the modem and the settings you were instructed to use by the ISP, connection type (network or USB) so we can give you specific instructions on how to do this. Oh yeah your ISP will be helpful too.

---

### Post by darshshinde on 2006-10-19
yes i was wrong  .. i called up the isp and he said i use a changing ip adress (thats non permamnant ) but i use dhcp server and that true .. 

so now how should i enter the primary and secondary addresses of the server so that i get connected to net via ubuntu >?

plz help me ...

---

### Post by darshshinde on 2006-10-19
well i dont use a dial up modem stuff, but i connect to internet via a dlink network card .. so modem problem does not arise at all ... plz tell me where and how should i enter my details in ubuntu, for my isp tells me that DHCP server requires just the primary secondary ip adress of server and a username and p/w which he has provided to log in .. 

where to put all this stuff ?

---

### Post by caravel on 2006-10-19
You can't connect to the net with nothing more than a network card, there must be some kind of modem, cable modem, or router between you and your ISP.

If you use DHCP your DNS servers may be irrelevant as DHCP will provinde the DNS server addresses automatically.  If you're connecting to the net via a network card and rj45 patch cable then you are connecting to a router/cable modem.

---

### Post by HereInOz on 2006-10-19
I think this is what you need.

Click on System > Administration > Networking.
Enter your password
Click on the General tab.
Select your Ethernet connection, and click on properties.
Set the configuration to Static IP address
Set the IP address to an address in the same subnet as the local (LAN) address of your broadband router/modem - if the router is 192.168.1.1, set your IP address to, say, 192.168.1.25, if it is 10.1.1.1, set your computer to, say, 10.1.1.25.
The subnet mask should set automatically.
Set the Gateway address to the local (LAN) address of your router/modem.
Click OK

Click on the DNS tab and add the DNS server addresses which you can get from your ISP.
Click OK

From your question, it appears that your broadband router is not assigning your Ubuntu machine an address via DHCP.  I have had this myself on several occasions.  Setting the LAN IP address static and entering the DNS server addresses usually fixes this problem.

Please note that you do not enter the WAN IP address in anywhere.  this is the address that your router is assigned by the ISP, and is on the outside of the router.  

Hope this helps.

---

### Post by pradeepadapa on 2006-10-19
hi man,

      as u hav told that ur connection is DHCP connection there is no need to follow the steps of HereInOz above, bec just go to system->administration->network settings nd then select ur ethernet connection, leave the setting above to DHCP ,DONOT go for static address bec ur's is not an static IP address, nd then save the settings nd close, this is the default procedure to setup the internet connection through UBUNTU if u r using DHCP..

what i wanna know is do u use a client like 24Online client to login to ur net by entering ur username nd password or do u login through webpage .

hope this helps or giv me an reply i shall sort ur problem.

---

### Post by caravel on 2006-10-19
There seems to be some confusion here between WAN and LAN.  **HereInOz** has got it right.  Follow that advice and it should work.  Sometimes a workstation cannot assign an address via DHCP so you have to configure manually in this way.  Strangely I've found this annoying problem to be more common with Windows XP than Linux.

---

### Post by darshshinde on 2006-10-21
well i log on directly by a programme windows, and not through a webpage logon (like in yahoo or hotmail )

so what to do next .. i thnk i better try out the thing u told me and tell u guys if it doesnot wrk out ..

---

