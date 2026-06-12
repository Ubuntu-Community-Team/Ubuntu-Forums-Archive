---
title: "HEEELLLLPPPP!!!! Ubuntu not connecting to the internet"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by jubeiyagyuX on 2008-04-05
hello im new to ubuntu and just installed beta 8.04 on my laptop which had vista installed already,anyway I can't connect to the internet,im using a usb modem(arris 502b) and when i click on the network icon on the top right it says "unidentified usb device" and cannot connect,can anyone help me out!

---

### Post by talsemgeest on 2008-04-05
Chances are its a win-modem (one that is based on software rather than hardware), if you can't find linux drivers for it there isn't much you can do.

Sorry I can't be of more help :(

---

### Post by jubeiyagyuX on 2008-04-05
where can i find the drivers?:(

---

### Post by talsemgeest on 2008-04-05
I'm checking google now

---

### Post by talsemgeest on 2008-04-05
Ok I couldn't find anything, just don't forget that with problems like this Google is your friend!

---

### Post by jubeiyagyuX on 2008-04-05
NOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!
thanx anyway.guess i won't be able to learn how to use ubuntu till i get a new way to conect or something.damn!

---

### Post by talsemgeest on 2008-04-05
But I'm still no expert on networking, so there may be some way to get it working. Anyone else got any ideas?

---

### Post by Sef on 2008-04-05
Check out [Linmodems]("http://linmodems.org").

---

### Post by jubeiyagyuX on 2008-04-06
I checked out linmodems and can't get an email through! anybody else got any other suggestions PLEASE!really need to get on the net

---

### Post by jubeiyagyuX on 2008-04-06
anybody please help!:(

---

### Post by BaffledMollusc on 2008-04-06
Is it a TM502? That's the only model I could find that sounds even vaguely like what you have. The drivers can be found here:

[http://www.arrisi.com/support/usb/index.asp](http://www.arrisi.com/support/usb/index.asp)

There don't appear to be any linux drivers, only windows ones. What you may be able to do is wrap the windows driver in some way. I know that you can use ndiswrapper for Windows wireless drivers, so maybe there's something like that.

---

### Post by BaffledMollusc on 2008-04-06
Actually, I've found the user manual at

[http://209.85.173.104/search?q=cache:XJ162Kzzu0wJ:www.arrisi.com/support/guides/_docs/TM502_User_Guide.pdf+arris+TM502+linux&hl=en&ct=clnk&cd=1&gl=au](http://209.85.173.104/search?q=cache:XJ162Kzzu0wJ:www.arrisi.com/support/guides/_docs/TM502_User_Guide.pdf+arris+TM502+linux&hl=en&ct=clnk&cd=1&gl=au)

and it says under linux "Ethernet connection only: Hardware drivers, TCP/IP, and DHCP must be enabled in the kernel." 

Beats me what that means. Maybe someone else can help.

Oh, here's another Ubuntu user with a TM502, and apparently it does work with linux. See this thread: [http://ubuntuforums.org/showthread.php?t=697138](http://ubuntuforums.org/showthread.php?t=697138)

---

### Post by scrime on 2008-04-06
Is it not possible to plug an ethernet cable into the modem?  It does make mention in the manual of ethernet.  My modem has USB and ethernet connections, there is a USB driver for it but I could never get it working.  I connected via ethernet was working in a few secs.  If you connect via ethernet you could uses Roaring Penguin RP-PPPOE to connect.  Either that or you could set up a machine or router with internet connection sharing and connect via that.  Sorry can't be of more help, there is a chance there are linux drivers for you card.  In regard to the previous comment by BaffledMollusc, TCP/IP and DHCP should already be enabled.

---

### Post by jubeiyagyuX on 2008-04-13
> **scrime said:**
> Is it not possible to plug an ethernet cable into the modem?  It does make mention in the manual of ethernet.  My modem has USB and ethernet connections, there is a USB driver for it but I could never get it working.  I connected via ethernet was working in a few secs.  If you connect via ethernet you could uses Roaring Penguin RP-PPPOE to connect.  Either that or you could set up a machine or router with internet connection sharing and connect via that.  Sorry can't be of more help, there is a chance there are linux drivers for you card.  In regard to the previous comment by BaffledMollusc, TCP/IP and DHCP should already be enabled.

when i plug the ethernet cable into the modem nothing happens no matter what i do even when i use windows vista maybe cus i dnt really knw hw to configure it but i dnt think it needs dat much configuring does it?dnt knw hw to use anyy thing on ubuntu so can any1 just help me out someway:confused:

---

### Post by jubeiyagyuX on 2008-04-13
can someone please help me out of my misery!!!!!:confused:

---

### Post by bwallum on 2008-04-13
I think you might need to connect to the modem once you have an ethernet cable between it and your pc. You will need to find the default IP address. It will be 10.0.0.1 or 192.168.0.1 or 192.168.1.1 or 192.168.2.1 in most cases. Put the address in a browser. You will probably need the default username and password as well.

You have probably have had to dial up you ISP every time you wanted to connect to the Internet.  Personally I would bin it and get a proper router for about £10 off eBay. You get a lot more control that way and the line is always open making initial connection quicker.

Every time I come up against one of these Windows specific dial up modems I bin them and persuade the client to do the proper thing and buy a router.

Good luck

---

### Post by prshah on 2008-04-13
> **jubeiyagyuX said:**
> anybody please help!:(

The 502B is a technology of Arris, not a modem. The cable "modem" model _implementing_ that technology is probably CMTS C3 or CMTS C4. You will have to check and confirm which one it is. If you _also_ have an ethernet (aka LAN) port, better switch to using that rather than a USB port. If you dont have an ethernet port in your computer, you can use an Usb->Ethernet converter. Note that it will convert _host_ (ie, computer) usb to ethernet and not guest (i.e, your "modem") usb to ethernet (which just means that you can do it only if your modem has an ethernet port).

---

### Post by jubeiyagyuX on 2008-04-13
i do have an ethernet port but whenever i connect it nothing happens both on ubuntu and windows.its driving me crazy!!!! thats where the problem is, i can't get it to work with the ethernet cable

---

### Post by Saint Angeles on 2008-04-13
> **jubeiyagyuX said:**
> i do have an ethernet port but whenever i connect it nothing happens both on ubuntu and windows.its driving me crazy!!!! thats where the problem is, i can't get it to work with the ethernet cable
if its not working with windows either, its a hardware issue rather than an ubuntu problem. (make sure you have the correct type of ethernet cable)

---

### Post by jubeiyagyuX on 2008-04-13
when i connect it on windows do i have to do anything special?or configure anything?

---

### Post by prshah on 2008-04-13
> **jubeiyagyuX said:**
> i do have an ethernet port but whenever i connect it nothing happens both on ubuntu and windows.its driving me crazy!!!! thats where the problem is, i can't get it to work with the ethernet cable

Ahh that's because it's setup in "bridged" mode. This is what you should do to check it:

In Windows: Open Network Connections, then choose to setup a new connection. Choose to set Internet connection, then choose Setup myself (words to that effect) then choose "Broadband connection with Username/password, enter your username and password, then try to connect. When asked, choose your LAN port. Wish I could be more specific, but I have no windows...

If it works, your bridged mode is setup fine, and you can use pppoeconf in linux to setup your internet connection.

---

### Post by jubeiyagyuX on 2008-04-15
I tried doing what you said but to no avail!!!:(  i'm on windows vista and when i get to the setup it ask for my username and passowrd which i dnt have(dnt think i was given one by my isp) and then it tries to connect through dial up,if anyone can give me a step-by-step process ill really appreciate it as im nt too good with stuff like this.i'm thinking if i can get the ethernet connection working on vista then i should have less problems with ubuntu.so PLS HELP!!!!!!!!!!!!

---

### Post by jubeiyagyuX on 2008-04-15
:(:confused:

---

### Post by 3rdalbum on 2008-04-15
Boot up Ubuntu with the ethernet port connected to your modem.

Go into a terminal (Applications > Accessories > Terminal) and type (or paste) this in:

```
ping 74.125.19.147
```

 If it puts "Destination Host Unreachable" into the terminal, then you have no connectivity.

If you get something like this come back into the terminal:

```
64 bytes from 74.125.19.147: icmp_seq=1 ttl=241 time=273 ms
```

then it's telling you that you have internet connectivity, but your modem might not know where your ISP's DNS server is. It's easy to fix this though: Go into System > Administration > Network, click the DNS tab, and put in either your ISP's DNS address, or the OpenDNS address:

208.67.222.222

Then you should find that websites will open.

*NOTE: Don't leave the terminal window open once you've performed the test; that IP address you're pinging is actually Google. You don't want Google to get mad at you :-)*

---

### Post by jubeiyagyuX on 2008-04-15
thankx,i tried what you said and it gave me a "Destination Host Unreachable" from terminallike you said it means there's no conncetion,is there anything i can do to get it working?PLEAAAASEEEEEEEE!!!!!!!!!!!

---

### Post by jubeiyagyuX on 2008-04-15
:confused::confused::(:confused:

---

### Post by jubeiyagyuX on 2008-04-15
anybody!!!:(:confused::confused:

---

### Post by Tomatz on 2008-04-15
How does the modem connect to the internet (e.g adsl, 3g?).

---

### Post by jubeiyagyuX on 2008-04-15
dnt really know but its a USB modem.guess it should be dsl or something not really sure tho

---

### Post by Tomatz on 2008-04-15
> **jubeiyagyuX said:**
> dnt really know but its a USB modem.guess it should be dsl or something not really sure tho


So it connects to the phone line :)

Can you Ethernet from the modem to the laptop?

---

### Post by jubeiyagyuX on 2008-04-15
yes i can connect the ethernet cable directly to the laptop but thats the problem nothing happens even when i ping it both on vista and ubuntu but using the usb works fine:(

---

### Post by jubeiyagyuX on 2008-04-15
:confused::confused:

---

### Post by Tomatz on 2008-04-15
Does the modem have a model number on the back of it?  Not the name of the modem as the same modem is probably used by different company's in different countries.

---

### Post by jubeiyagyuX on 2008-04-15
Tm502b/220

---

### Post by jubeiyagyuX on 2008-04-15
arris touchstone

---

### Post by Tomatz on 2008-04-15
Is it a wireless modem as well as a wired?

---

### Post by jubeiyagyuX on 2008-04-15
its wired through USB

---

### Post by Tomatz on 2008-04-15
You are best off using Ethernet if you can.

I cant seem to find ANY information on the modem let alone about running the modem on linux. 

Try doing this in a terminal:

```
ping 216.239.51.99
```

---

### Post by Tomatz on 2008-04-15
I have a huge hunch its based on a thompson speedtouch.

Plug the usb into your laptop and type this into a terminal:

```
awk '/4061/ { print $5 }' /proc/bus/usb/devices 
```

---

### Post by jubeiyagyuX on 2008-04-15
thats what im tryin to do but it doesn't connect thru ethernet,thats where the problem lies

---

### Post by Tomatz on 2008-04-15
> **jubeiyagyuX said:**
> thats what im tryin to do but it doesn't connect thru ethernet,thats where the problem lies

Do this in a terminal (as said) and post the output:

```
awk '/4061/ { print $5 }' /proc/bus/usb/devices 
```

---

### Post by jubeiyagyuX on 2008-04-15
:confused::(

---

### Post by talsemgeest on 2008-04-15
Are you going to do it or not?

---

### Post by Tomatz on 2008-04-15
Plug the **usb** cable from the modem into your laptop.

Open a **terminal**.

Then copy and paste the following into it (the terminal) and press return:

```
awk '/4061/ { print $5 }' /proc/bus/usb/devices 
```

Then copy the **text that follows** the command you just ran (the output) and post it on this thread.

_If nothing happens do this instead (and post the output)_

```
awk '{ print $5 }' /proc/bus/usb/devices
```

;)

---

### Post by DrCoolSanta on 2008-04-15
It does not make enough sense, is it ethernet or your phone cable? Are you even putting the cables in the right port? What kind of modem? Modems don't have ethernet ports as far as I know, and you don't just connect through a modem, you have to give an username and password, if you don't have it, you don't have a modem, it must be a router. You are always better at connecting routers with ethernet cables, USB is just buggy.

If its you are sure its ethernet (ethernet ports are bigger than the phone ports in size, yet confusing), put that in the right port, then on your Ubuntu, goto System -> Administration -> Network, this should show you all your internet devices. If it says phone modem and you have no such modem, you can ignore. The others are the devices Ubunutu detected, if it does say wired network, this is ethernet. Now we need to configure this, click on properties, since I see DHCP setting being needed here, just tell it to use the DHCP server. You probably also need to tell it the DNS servers in the DNS tabs. Check this configuration from your ISP or the manuels given to you. If your manual or ISP says that you must enter a specific IP address, subnet mask or gateway, then you need to do a manual configuration rather than ISP.

If your modem came with a CD, and contains drivers for USB, you are in luck ^_^. First you need to install nidswrapper, goto [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and check how to install ndiswrapper, do that. Then copy the .inf file that came in the cd for the USB drivers, and copy it to your home folder.
then open up terminal
type the following
sudo su
ndiswrapper -i driver.inf (where driver.inf is the file name)
ndiswrapper -m
modprobe ndiswrapper
exit
exit

Now check your internet, if you need to configure your internet you must do it now.

---

### Post by bwallum on 2008-04-15
You really seem to be suffering here. Could we start again from basics? 

1) Firstly, who is your ISP?
2) What type of service do you have? Is it over a phone line, e.g. adsl broadband; or is it over dedicated cable, e.g. Virgin cable broadband? You will definately know if you are on cable or not, check your bills.
3) DON'T publish it here but make sure you have your username and password to hand. If necessary phone up your provider to check.
4) How do you access your modem with a browser? If necessary phone your ISP and ask them. What you need is a URL, it will be in the format xxx.xxx.xxx.xxx where x is a number. 

Options:-
A) If you are on a cable service with only a usb accessible modem you are stuffed. You need a programme called a driver to make the modem work. You must get this from your ISP and it needs to be Linux if you want to run Ubuntu.
B) If you have an adsl service then bin your modem and buy an adsl router (adsl2+). That will have RJ45 ethernet connection and RJ12 adsl connection. Make sure your computer has an ethernet connection, if not buy an ethernet card to plug into a spare slot. Connect your computer to your router with a Cat5e (or 6) cable. Connect your router to your adsl service with a piece of flat telephone cable and a male RJ12 connector on each end. (both of these cables come with a router so make sure if you buy one the cables come with it). Now set up your router and access it with the appropriate url (the router manual will tell you this). Normally routers have default access usernames and passwords, some have none. Access your router with a browser, put in your ISP username and password gathered in 3) above. Save and exit. 

That should get you going. If not, keep shouting. 

Good luck

---

### Post by chrisdugdale on 2008-04-15
Is it a dialup modem? Ubuntu doesn't install stuff to run a dialup modem. If so, the answer is at [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by dstin1 on 2008-04-15
This may sound simple but I've seen it happen before.  Are you using a Ethernet cable or a phone cable?  You did not receive a ethernet cable with the modem but you did get a phone cable.  You can tell if you are using the right cable because it will only fit in the middle plug and not  the first 2 a phone wire will fit all three but loose in the ethernet plug.

Once you verify you have the right cables get the required info for setting up the connection and follow the steps for windows assuming you still have windows installed.

You will most likely have to call your ISP.

p. 33 of this manual.
[http://www.flowjamaica.com/index2.php?option=com_docman&task=doc_view&gid=9&Itemid=307 ]("http://www.flowjamaica.com/index2.php?option=com_docman&task=doc_view&gid=9&Itemid=307")

If you can get it to work in windows then there is no reason it won't work with Ubuntu.  If you can't get it to work in windows and you are using the proper connection then you have a hardware problem.

BTW I have used several different linux distros with several computers and connections and never had a problem.  The only thing the connections had in common is ethernet.

---

### Post by dark_harmonics on 2008-04-15
The first step is to check if you are getting connection lights from the connection. This ensure that your hardware is functioning. Then you will need to know who your provider is and what type of authentication they use (if any). You will need to use this information in your windows or ubuntu to connect through your modem. Also, your modem should be reset at least once (pull the power and any batteries from the unit then push them back in). This ensures that your modem is not "holding" onto the previous connection. I have seen this many many times before. Another thing to check for is that you do not have a DSL filter on the phone connection you are trying to use to connect through. Sometimes users will put these filters on ALL their phone lines (reduces noise) not realizing that the modem cannot be filtered.

---

### Post by Athrun88 on 2008-04-15
I am not sure if this has been suggested, but here it goes.

Trade in your USB modem with an Ethernet modem. The majority of ISP's will allow this change with little or no charge. In my experience (i am Canadian) my then-ISP (Bell Canada) only asked why I needed to change my modem. I just stated that I needed an Ethernet modem because it was faster than USB, less than a week later, I had an Ethernet modem.

Next would be to connect this to a wireless router. A router runs about $50 and is easy to set up if you follow the instructions. Also, while you're out getting that router, get a wireless adapter for your desktop. Major manufacturers have drivers for linux and most are already supported natively. My home desktop was automatically recognized by Ubuntu Live.

Start up your copy of Ubuntu and install your drivers for your wireless adapter and have Ubuntu connect.

Hope that works..

Regards.

---

