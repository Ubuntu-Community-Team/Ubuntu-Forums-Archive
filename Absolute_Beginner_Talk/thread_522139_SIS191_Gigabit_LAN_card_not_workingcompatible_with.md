---
title: "SIS191 Gigabit LAN card not working/compatible with ubuntu 7.04?Can't access Internet"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by wmg on 2007-08-10
SIS191 Gigabit LAN card not working/compatible with ubuntu 7.04?

I tried "sudo pppoeconf", "ifconfig eth0", no working ethernet cards found though

Now I have dual-boot with Vista & Ubuntu 7.04, 
and I am using dummy Vista to browse the Internet
but I wanna try Ubuntu. It seems faster and safer

but WTF **** OMG if my SIS191 wouldn't bring my Ubuntu online, I would consider uninstalling it. I wouldn't dare modifying my hardware or buying new cards because it would violate the 1-year warranty.

K, please tell me if

1. SIS191 Gigabit LAN card is working/compatible with ubuntu 7.04 or not?
2. What should I do if the answer is "no"?

---

### Post by wmg on 2007-08-10
ALSO....

Intel pentium D
acer aspire SA90
SIS191 onboard GIGABIT LAN
895 mb ram
SIS671 onboard Soundcard
SIS display something... and more

Ubuntu can recognise the model of my SIS191 LAN CARD
but it just can't bring it working
it just said "no working ethernet cards" damn annoying
I even tried compiling the SIS190.c driver using the method based on Ubuntu 5.x

---

### Post by wmg on 2007-08-10
I can see the model name of the LAN card in Ubuntu's system preference

I wonder if Ubuntu 7.04 just supports the SIS191 LAN card or it is just only able to know the exact name of the LAN device instead of running it.

I hope it is a fixable bug.

---

### Post by overdrank on 2007-08-10
> **wmg said:**
> SIS191 Gigabit LAN card not working/compatible with ubuntu 7.04?

I tried "sudo pppoeconf", "ifconfig eth0", no working ethernet cards found though

Now I have dual-boot with Vista & Ubuntu 7.04, 
and I am using dummy Vista to browse the Internet
but I wanna try Ubuntu. It seems faster and safer

but WTF **** OMG if my SIS191 wouldn't bring my Ubuntu online, I would consider uninstalling it. I wouldn't dare modifying my hardware or buying new cards because it would violate the 1-year warranty.

K, please tell me if

1. SIS191 Gigabit LAN card is working/compatible with ubuntu 7.04 or not?
2. What should I do if the answer is "no"?

HI I cant find alot of info on that nic card but if all else fails you can use a 
[http://www.newegg.com/Product/Product.asp?Item=N82E16833124122&CMP=KNC-overturesmx&ATT=product](http://www.newegg.com/Product/Product.asp?Item=N82E16833124122&CMP=KNC-overturesmx&ATT=product)
So I think you will be ok!:popcorn:

---

### Post by wmg on 2007-08-10
> **overdrank said:**
> HI I cant find alot of info on that nic card but if all else fails you can use a 
[http://www.newegg.com/Product/Product.asp?Item=N82E16833124122&CMP=KNC-overturesmx&ATT=product](http://www.newegg.com/Product/Product.asp?Item=N82E16833124122&CMP=KNC-overturesmx&ATT=product)
So I think you will be ok!:popcorn:

Maybe, but is it a wireless one?

BTW, I also have a router behind the LAN networking system. I just have remembered that. Would that be the cause of the problem?

---

### Post by overdrank on 2007-08-10
> **wmg said:**
> Maybe, but is it a wireless one?

BTW, I also have a router behind the LAN networking system. I just have remembered that. Would that be the cause of the problem?

Hi and I know very little on networking so maybe someone else can help. :confused:

---

### Post by WebSiteGuru on 2007-08-10
Does your LAN have a proxy? If, yes, that is your problem. You will have to configured your NIC to point to that proxy.

Hope this help.

---

### Post by wmg on 2007-08-15
> **WebSiteGuru said:**
> Does your LAN have a proxy? If, yes, that is your problem. You will have to configured your NIC to point to that proxy.

Hope this help.

It can detect my LAN in my "System Hardware" but cannot find it in my "Networking". What I see at all is a modem thing which is not really my LAN. Therefore, I cannot configure my LAN proxy.

---

### Post by WebSiteGuru on 2007-08-15
> **wmg said:**
> It can detect my LAN in my "System Hardware" but cannot find it in my "Networking". What I see at all is a modem thing which is not really my LAN. Therefore, I cannot configure my LAN proxy.

Look for Network under system tab (I dont know exactly where it is ATM), and see if you can configure you proxy there.

---

### Post by andre_dc on 2007-08-30
Hi,

](*,)](*,)](*,)
Seems that I do have same problem , you posted 2 weeks ago , any solution ?

Regards,
Andre

---

### Post by anewguy on 2007-08-31
Have any of you with this problem tried blacklisting the driver in /etc/modprobe.d/blacklist and then using ndiswrapper and the Windows drivers?  I checked at SIS and they have a zip file with the driver.  Let me know and perhaps I can get you working - but be forwarned, I don't have your card, and I'm far from being an expert.:)

---

### Post by anewguy on 2007-08-31
If you are having problems and want to try, here is the info for using ndiswrapper:

First, there are a couple of packages you must have installed, so click on System, then on Administration and then on Synaptic Package Manager.  Click the search button, type ndiswrapper in the search string and click find.  Be sure both ndiswrapper-common and the ndiswrapper-utils-xxxxx (don't know what yours will say there) have green boxes.  If not, click the box and click on "Mark for installation".  Now on the left side of the screen click on "All".  Click the search button, type network-manager and click find.  If network-manager and network-manager-gnome are not green boxed, click on each box and select "Mark for installation".  Now, if you had to mark any of the above for installation, click "apply" and wait for the software to install.   Now close out of sysnaptics package manager.

Next, download the file I have attached here and then extract it to your desktop,  It will create a folder on your desktop called "sislan".

Now, open a terminal window and type:

ndiswrapper -l  <-- lower case "L", for "list"

if anything shows as output:

sudo ndiswrapper -r xxxx      where xxxx is the name of one of the things that shows in the list

repeat the ndiswrapper -l  and the sudo ndiswrapper -r xxxx for each thing that shows in the list until no output is returned.


Type:

sudo ndiswrapper -i ~/Desktop/sislan/SiSGbe.inf      -- be sure to match the case (you can just copy and paster the command from here if you want to.

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Now just restart your PC.  When the PC boots back up, click on the network-manager icon on your top bar and see if the wireless networks are shown.  If so, try clicking on one to see if you can connect.  Remember that if you use WEP or WPA you will need to specify that and the key in the connection box.

Let me know if this works or not.:)

---

### Post by andre_dc on 2007-08-31
Ok , I have installed the ndiswrapper succesfully and the SIS191 works fine.

first thing I did with my new pc was uninstall vista , then I got a bit 'scarred' since the network did not come up from start but now I'm convinced more then ever that I did the only right thing!

Thanks to the forum !

A happy Ubuntu user ! :)
Andre

---

### Post by erdalronahi on 2007-09-04
I don't have a solution, but the same problem with the SIS191 Gigabyte Ethernet adapter.

---

### Post by anewguy on 2007-09-05
> **erdalronahi said:**
> I don't have a solution, but the same problem with the SIS191 Gigabyte Ethernet adapter.

Did you try the solution I posted?  it worked for them, maybe it will work for you, too?:)

---

### Post by erdalronahi on 2007-09-06
No, finally it doesn't boot anymore because of the ethernet driver, so I guess we'll have to buy a different network card.

---

### Post by Dr_Snapid on 2007-09-16
I have this problem too, but when I go into Synaptic, NDISWrapper isnt in the list. When I go to settings/repositories i see the message "to install from a cdrom or DVD, insert the medium into the drive" but i already have my ubuntu 7.04 cd in the drive, and it appears as an icon on the desktop and I can browse it. But it isnt available in Synaptic it seems. Plus, when I go to third party/Add cdrom it says it cannot mount the CD!

I need ndiswrapper to get my network going... is there a way i can copy it onto a flash drive and transfer it to the PC that way? Shouldnt my bootable ubuntu CD work as a repository?

---

### Post by splintercellguy on 2007-09-16
Please read [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) to learn how to install ndiswrapper if the machine is not connected to the Internet.

---

### Post by avalentin on 2007-10-11
Hi,
I also have this problem with my Ubuntu Feisty (SiS191 in Acer SA90). I have already run the ndiswrapper solution and succeded listing the driver in the network configuration (Thanks a lot!), but still not have network at all. The parameters are the same as in WXP. 
I really don't know what to do. Ifconfig eth0 still has this message: "error fetching interface information: Device not found"

(I am quite a newbie :(

Thans for any clue!
AV

---

### Post by delmsan on 2007-10-16
I believe following the steps given by anewguy will solve the problem.

Thanks a lot and my sis191 working fine now.

---

### Post by andre_dc on 2007-10-19
after I upgraded to ubuntu 7.10 my sis191driver  no longer works , I tried the same procedure but eth1 is not available so I have no more network access. What has chnged on this level from 7.04 to 7.1 ?
ndiswrapper -l shows the driver is  installed ...:(

Tx for your help.
Andre

---

### Post by gaxy on 2007-12-08
Hi everybody!
I've already tried the steps suggested by anewguy, now if I type "ndiswrapper -l" I can see the driver installed. I've another problem now: it doesn't work!! I cannot find how configure a static ip in the kde network manager (but I guess this is not possible if not via shell; if I try via shell and than I try to ping my router it doesn't work and I "loose" my network card...:confused:). How can I do? Why if I reboot I loose the little icon in the tray that means that my network card is alive?
Cheers. :confused:

---

### Post by teqen on 2007-12-09
Hi I have similar problem. I followed the steps given by Anewguy but something must go wrong cause I still have no net. My situation is:
Ubuntu 7.10
Fujitsu Siemens Esprimo v5515
when I access network manager i can't see anything except for modem connection(there should be wifi and cable connection). I once managed to established cable connection but I could ping only my router. Nothing more. 

I would be grateful for any sugestion.:(

---

### Post by Digger78 on 2007-12-22
> **teqen said:**
> Hi I have similar problem. I followed the steps given by Anewguy but something must go wrong cause I still have no net. My situation is:
Ubuntu 7.10
Fujitsu Siemens Esprimo v5515
when I access network manager i can't see anything except for modem connection(there should be wifi and cable connection). I once managed to established cable connection but I could ping only my router. Nothing more. 

I would be grateful for any sugestion.:(

I have the same laptop and this problem is driving me nuts.

I blacklisted the "alternate driver : sis190"

At one point "ndiswrapper -l" showed that there was no "alternate driver" (at last, but no idea why it finally went away)

I could ping my router and external IP addresses, but I couldn't access my router or websites through my browser.

As surprisingly as it disappeared, the "alternate driver :sis190" reappeared.

To top it all off, my wireless wont associate with my router despite the details being in /etc/network/interfaces and adding them from terminal  "sudo ifconfig wlan0 essid xxxx key xxxxx

sudo ifconfig shows that it has the key but not the essid.

If anybody has any suggestions other than - "Avoid SiS products" - I'm all ears


Kubuntu 7.10

---

### Post by SonicReducer on 2008-01-18
I too have the same problem and followed the above steps to little avail. on another note I cant connect to the internet on vista as it says its connected to an unidentified network. though i can ping my router on vista so i dont think it should be the NIC. Or is it? On Ubuntu on the otherhand i cant ping anything. any ideas?

---

### Post by memala on 2008-01-18
Hi I had a similar problem with the nic "sis191"  (Fujitsu-Siemens Esprimo Mobile V5535) under Ubuntu 7.10 (Gutsy).
You can find my work around under [1] or [2].
I didn't yet reconfigure my wlan.

Emal

1: [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-01/msg01475.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-01/msg01475.html)
2: [https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html)

---

### Post by afrie on 2008-02-06
Hi memala,
your hardy patch instructions does not work for me. The resulting kernel is freezing.

I found a solution to activate the ethernet controller SIS 191 [1039:0191] on a FSC notebook V5515 with Ubuntu 7.10 (Gutsy) by running a customized 2.6.24 kernel from kernel.org. If someone is interrested, please read the instructions from
wget home.teleos-web.de/afriedrich0/afrie_fsc_v5515_sis191_instruct ions.txt

---

