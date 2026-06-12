---
title: "network help"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by vmaxchick on 2006-10-31
Please I hope someone can help me, I have just installed Ubuntu on my computer and have a dreaded Dlink G122 usb connection for the net that connects to another router to get access to the net.

I am disabled hence why i need to router at home but at times i also need to use the system that has the usb device on it the Dlink, I have looked all over and i am currently so stuck its scaring me, I cant find a solution to install or get it to work at all, i cant download on that system either as i cant get a connection. Have looked in the network devices and shows "wireless connection - rausbO not active" when i make it active the whole system freezes and  modem connection.

Please someone help as i am at a loss here and even more so searching, as i say i am stuck and do not know how to get it to work or connect and cant download due to that either.
I pray for a reply, thanks in advance

---

### Post by MyAnda on 2006-10-31
i don't know anything about Dlink G122 but am willing to try...came across this...it is for 6.06 but might be relevant...
[http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)

are you seeing any errors anywhere (e.g. /var/log/messages)?

---

### Post by Iowan on 2006-10-31
[http://leenooks.com/DLink+DWL%2dG122]("http://leenooks.com/DLink+DWL%2dG122")
Found this - which doesn't look very encouraging...
What is the hardware revision level?

I don't do wireless (yet) but the term **ndiswrapper** came up.

[http://anirudhs.chaosnet.org/blog/2005.10.23.html]("http://anirudhs.chaosnet.org/blog/2005.10.23.html")
Here's another link... on setting up the Dlink G122.

---

### Post by vmaxchick on 2006-10-31
hi MyAnda went to the site where it had >>>[http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)
damn thing wont allow me to create a file and when i opened the interface there was nothing there at all file had nothing in it.

Iowan In relation to the other links i do not have that folder on the system as i cant download hence no connection

---

### Post by MyAnda on 2006-10-31
are you running 6.06 or 6.10?...don't have a 6.10 sys here to see if things changed...maybe someone can comment

---

### Post by Henry Rayker on 2006-10-31
6.10, it worked almost out of the box. (I just had to add the "auto rausb0" line above the rest in the /etc/network/interfaces file)

I have that dongle, rev B1, I believe. In 6.06 (Dapper) I had to install a new driver and change my /etc/network/interfaces file so it only included: 

auto rausb0
dhcp rausb0   (something to this effect, I'll get those lines when I'm at home. no laptop with me at work).

The driver I got, I found from [this thread]("http://ubuntuforums.org/showthread.php?t=240669&highlight=rt2500+rt2500usb")

I hope this helps somewhat...

---

### Post by vmaxchick on 2006-10-31
hi there thanks for the reply,
I have accessed the root file interfaces for network, when the window opens i am looking at a file called interfaces but there is no wording or anything showing, no text at all, if i try to type anything in there and save it it cant be done it says and warning also shows in terminal window as well as interfaces. I am getting close to tears and hair is falling out for sure, why is life not easier ha ha I am not winning sorry for being a pest and yes its 6.10 I have

---

### Post by Henry Rayker on 2006-10-31
to ensure your file is actually present, I'd suggest trying this.

open a terminal and type:
cd /etc/network

next, type:
ls

This will show you the contents of the network directory. If there is an interfaces file in there, you should open it with:

sudo gedit interfaces

(The sudo allows you super-user status, for just this command). That will allow you to save any changes you make, but be careful as it is a powerful ability.

Let us know if you actually had the interfaces file.

Also, can you check which revision your usb device is? I am assuming you have a B (it has a ralink chipset in it, the A didn't, I don't believe).

One other thing. This is a fresh install, correct?

---

### Post by vmaxchick on 2006-11-01
hi there and many thanks,
done what you said and >open a terminal and type:
cd /etc/network<
it kept saying no such file or directory so before the cd/ect/network i typed in sudo gedit and it showed me another window, in that window the tab at the one that was open was "network" but the page that was there for it was totally blank. As i say the plain cd/ect/network with nothing typed before it would not execute a thing.

Once again popped back into interfaces and the same thing opened window with interfaces tab and once again just a blank white window with nothing there for change or viewing.

Yes its a full fresh install, with regards to the dlink all it states on the device and the book is its DWL-G122 AirPuls G its high speed 802.11g

What it shows on the text tab on the device is model no as above, H/W Ver - B1 F/W Ver - 2.03

hope that helps

---

### Post by vmaxchick on 2006-11-01
hi there, i have been tinkering about with it and managed to get ip address and gateway ect there and the lights on the usb device showed me it was connecting, when i go into network and see the rausbO and then click properties if i try to select the gs wireless device being the usb Dlink the system damn well freezes every time and without trying to get that in place i still cant connect to the damn internet? even more at a loss now ha ha

---

### Post by vmaxchick on 2006-11-01
still trying since this morning and its now afternoon, it freezes up each time i try to active or change anything in network configuration and thats even doing it after a refresh on installation from scratch again :(( how do i get past the damn freezing

---

### Post by MyAnda on 2006-11-01
now that you have a fresh install, try the steps in the article again
[http://www.hotubuntunews.com/blog_2.shtml](http://www.hotubuntunews.com/blog_2.shtml)

he mentions that when he uses the network config tool it freezes...but that with the other steps he has gotten around it...

---

### Post by Henry Rayker on 2006-11-01
I'm going to guess your hardware revision isn't B. Without confirmation, however, I can't really help any further.

Rather than just the name of the device, we really need the chipset of the device.

---

### Post by vmaxchick on 2006-11-01
hi there henry, when you talking about the hardware i gathered you were asking about the dlink usb device and according to the notes its is version B1
What it shows on the text tab on the device is model no as above, H/W Ver - B1 F/W Ver - 2.03

My Anda went back to the web site again and tried the HOW-TO | D-Link DWL-G122 USB Adapter in Dapper the problem is i can open the interfaces file there is nothing in it its empty but even when i try to type in anything it will not save and gives me warning in the terminal.

Thanks Henry. MyAnda also was i right Henry was it the version of the usb you wanted to know. Its a B version and as i say biggest problem is damn system freezes on cofiguration, will try again now ,:-# grrrrrrrrrrr the second i try to activate it in network settings the damn system locks up totally.

I am sobbing here and damn determined but thank you so much for all the help you are giving, your a brain saver ;)

I noticed now after tampering again, that when i go into interface properties and into the rausbO and click configure it shows network name (ESSID) as being G604T_Wireless
Keytype -  Hexidecimal
WEP key - blank (unsure if anything is needed ere and where i might find it?)
configuration - static IP
Ip address - found on Management IP in router admin
Subnet - found on Management IP in router admin
Gateway address -  found on Management IP in router admin

hope this helps, even this is not connecting me, only one light on in relation to the usb device

---

### Post by Henry Rayker on 2006-11-01
This is incredibly odd because I have that same device, on the same version of Ubuntu.

The fact that you have no interfaces file is incredibly perplexing, because that is kind of a necessary file...

Did you ever try (in a terminal) to:
cd /etc/network [press enter]
ls [press enter]

???

This will show you if you actually HAVE an interfaces file. Let us know if you see one. _***This is pretty important***_.

Also, do you know if you set up a password on the router admin page (that's what the WEP is for). If you didn't, just leave it blank.

copy and paste the commands, just to make sure there isn't a mistype or anything like that. Linux is case-sensitive, so network is not the same as Network etc.

Let us know. I'll post the contents of my interfaces file (when I get home) so you can make it, if you don't have one.

---

### Post by vmaxchick on 2006-11-01
hi there henry i opened a terminal and typed in after the $
cd/ect/network and it said
no such file or directory was there supposed to be words before the cd/ect/network?
password on router admin page is just admin uname and admin no changes were made no other passwords were set up when installed ect

cant copy and paste as i am having to use another system to talk to you, hence why i have the dlink i am  often am confined to one area with one system.

As is say when i look at the interfaces file its totally empty, nothing in it, blank page, if i go to type and try and attempt to save anything in it, it blows me out as says no chance :-k 

would need to know how to create the file, you know you are a gem a true gem ;) 

Got an operation tomorrow but i will be sure ti fix this damn thing if it kills me ha ha

---

### Post by Henry Rayker on 2006-11-01
the command is 
cd etc/network

the way you typed it, you had no space, and ect, not etc...

---

### Post by vmaxchick on 2006-11-01
done that exactly as you said, response is ' no such file or directory '
witness here to verify that i did it right, lol !!!!

---

### Post by Henry Rayker on 2006-11-01
now I've made a mistake, I'm so sorry...it should be 
cd /etc/network

you could alternately do
cd /
cd etc
cd network

the "cd /" is to change directories into your root directory...that one better show up.
the etc directory better be there too, because that's a fairly important folder as well.
I can sort of see the network MAYBE not existing, but only if someone/something deleted it.

if one of these doesn't exist, it would be nice to know where it screws up.

---

### Post by frrobert on 2006-11-01
Not to stir the pot but could the issue be with Edggy?  I found Edggy a bit "unperdictable" in terms of network issues, I wound up going back to 6.06.  Drapper Drake seems much more perdictable especially with network manager.


Fr. Robert

---

### Post by Henry Rayker on 2006-11-01
frrobert: for this particular card, I had no issue whatsoever on Edgy. In fact, Dapper treated me worse. With Dapper, I had to uninstall the default driver, recompile my own and blacklist a bunch of other devices (that I wasn't even using/don't even have).

---

### Post by vmaxchick on 2006-11-01
typed everything in now showing in terminal 
desktop:/etc/network$
what now ?

---

### Post by vmaxchick on 2006-11-01
by the way typed in ls after that and it showed 
if-down.d if-post-down.d if-pre-up.d if-up.d interfaces

---

### Post by Henry Rayker on 2006-11-01
excellent. now type:

sudo gedit interfaces

This SHOULDN'T come up blank...post the contents here.

---

### Post by vmaxchick on 2006-11-01
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

hope that helps
window still open

---

### Post by Henry Rayker on 2006-11-01
change that entire file to this

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto rausb0
iface rausb0 inet dhcp

just comment out the lines I did (put the # character at the start of the line) and add the part about rausb0

after that, try a quick reboot and tell me if you get any sort of luck.

---

### Post by vmaxchick on 2006-11-01
right did that now it seems to have wiped all config for the rausbo device in network properties about to go and try it again and re-enter them need to check should i just take the ip and default gateway out from the management ip in my router admin? and use the primary dns in DHCP config in there also? dont want to destroy it again after all the great help you have given me

---

### Post by Henry Rayker on 2006-11-01
One thing is, make sure you leave it with DHCP. You can probably specify an ip using mac filters and still have DHCP on with your router...the reason for advising this is I have never gotten the static address to work out when specified by the card.

---

### Post by vmaxchick on 2006-11-01
well you my darling are and angel a true angel :KS 
Heather jumps about shouting "Go Henry, Go Henry"
Still getting jiggy with it here, jesus how do you do it, well muster the patience more than anything!

I will say though your post will solve this problem for hundreds of other posts i saw on the forums with no solution as such and no answers in the end.

is there any way i can praise you on the forum so you get a badge or a wage rise haha ;) 

Hmmmm feel kinda naked without you know now that it seems to connect, will miss you man, knowing my luck i will put system on when i get back from hospital tomorrow and bang it will be down again.

heather says to herself "think positive woman!"

Thank you and as i say your a true gent and a man to be applauded, and the only one that did not give up hope for me. Thank you so much xx

have i said thank you enough ha ha wee kiss ;)

---

### Post by Henry Rayker on 2006-11-01
I'm really happy I was able to help! Good luck with your operation and hopefully your connection won't be busted when you try to use it next.

---

### Post by vmaxchick on 2006-11-01
Henry sorry but had another issue, it did not last long and i had to activate it time and time again it eventually worked after about 3 freesez and 8 restarts, is this normal and do you have to active each time system is switched on. Also seems it would noe activate when my system where the router was plugged into was off, router was still on all the same just system off.

Also its now showing in my router config the following and it concerns me as i should only have 1-2 no more than 2 clients showing here, why is it showing all this due to ubuntu? raising concern and wondering wither its a good thing keeping ubuntu?

DHCP Clients 
MAC Address       IP Address  Host Name 
00:11:d8:0b:4c:52 192.168.1.2 unknown 
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033 
00:16:ce:5d:b8:0d 192.168.1.4 user-14eb8b9090 
00:13:46:97:ba:42 192.168.1.5 user-14eb8b9090

---

### Post by Henry Rayker on 2006-11-02
This is indeed a reason to worry. If you have no more than 2 machines on the network that belong to you, you may have someone leeching off of your network.

What is your laptop called? I am willing to bet it is the user-14eb8b9090...another thing to look at...on the back of the usb wireless device, you will find a number. This will be a MAC Address. Please give me this number.

Here are my theories. The first line, that's someone leeching onto your network. The second is your main machine (I hope) and the third and fourth are an onboard wireless and this usb wireless device...If it is an onboard wireless, we may be better off trying to establish a connection with that; Edgy, when I have more than one device currently active, doesn't respond very nicely.

> DHCP Clients
MAC Address IP Address Host Name
00:11:d8:0b:4c:52 192.168.1.2 unknown
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033
00:16:ce:5d:b8:0d 192.168.1.4 user-14eb8b9090
00:13:46:97:ba:42 192.168.1.5 user-14eb8b9090

---

### Post by vmaxchick on 2006-11-02
hi there the mac addy on the sub device is 00134697BA42
I only have one other system in use as my laptop is not connected to ubuntu and i dont have that on as i use the spare system as i call it, bascically another desktop pc set up.

The name of that system is Hster, so i now currently have my main system and my spare desktop system both on. Both are currently running in windows as wanted to check details. Now laptop is fully powered off. Here is what is now showing in my DHCp clients listing
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033 
00:11:d8:0b:4c:52 192.168.1.2 h 
00:12:5a:41:1a:71 192.168.1.5 00:13:46:97:ba:42 


never had this before it has normally showed the 2 systems if in use and no more and not those numbers either except the h as that is the main system..

---

### Post by Henry Rayker on 2006-11-02
Okay. I think I have some bad news. Someone is on your network. 
> 00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033
00:11:d8:0b:4c:52 192.168.1.2 h
00:12:5a:41:1a:71 192.168.1.5 
00:13:46:97:ba:42

You said your mac addy was 00134697BA42? See the last thing listed in that quote box? That's the corresponding MAC address. I'm guessing that it isn't currently recieving an IP, so that's why the IP isn't listed.

Now, if h is the main computer, then it is connected to IP address 192.168.1.2. The others, they are leeching off of your wireless connection. I would recommend using a MAC filter. What kind of router do you have? I'll look up some information on it and try to help get that set up for you.

(One more bit of important information. The earlier DHCP listing:
00:11:d8:0b:4c:52 192.168.1.2 unknown
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033
00:16:ce:5d:b8:0d 192.168.1.4 user-14eb8b9090
00:13:46:97:ba:42 192.168.1.5 user-14eb8b9090
This was given with the laptop powered on, correct? The other listing:
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033
00:11:d8:0b:4c:52 192.168.1.2 h
00:12:5a:41:1a:71 192.168.1.5 
00:13:46:97:ba:42
the laptop was not powered on, correct?)

---

### Post by vmaxchick on 2006-11-02
the eariler config shown was without laptop powered on it has not been for days. The spare system where the dlink usb is sitting is currently powered down. I have reset the router and it is now showing 
DHCP Clients 
MAC Address IP Address Host Name 
00:12:5a:41:1a:71 192.168.1.2 unknown 
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033 

Only system on is the main one, the router is D-Link DSL-G604T

would it be a better option to actually format the main system itself would it solve the leeching issue or any hacking?

---

### Post by Henry Rayker on 2006-11-02
OH! there are a total of 3 systems, then? The spare system is the one you're trying to get the dlink usb to work on?

If this is the case, you may need to disable the eth0 as well.
Remember the interfaces file we edited? I'd comment out everything except rausb0 lines and the lo lines.
(it should look like this
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
)

As for formatting the main system to get rid of leechers/hackers, that won't really work. The problem is the fact that your router isn't secure. Someone is connecting to that via wifi, then connecting to the net. 

To turn on MAC filtering, you'll need to go into your router admin page, and click Advanced (on the top) then Filters (on the side, I believe) and then the "MAC Address Filter" You'll need to use [this link]("http://www-dcn.fnal.gov/DCG-Docs/mac/index.html") first to find all the MAC Addresses your systems use. **one hitch here is I don't really understand what the Source MAC and Destination MACs mean.** I believe the Source MAC is the router's MAC (it should have one on a sticker similar to your USB device) and the Destination MACs will come from that the information in that link I included.

---

### Post by vmaxchick on 2006-11-02
hm looked at the router it has think on the side a LAN MAC ID with a barcode and a long number underneath and then under that WLAN MAC ID and another long number, router is asking for enable bridge filters in there. 

I have for the moment taken ubuntu off the spare system and left it with a bare windows xp while we were talking here, purely as its when i installed ubuntu this issue occured, as you can see its damn well changed again grrrrrrrrrr
00:12:5a:41:1a:71 192.168.1.2 unknown 
00:14:a4:5e:1e:05 192.168.1.3 acer-b147e6c033 
00:11:d8:0b:4c:52 192.168.1.4 h 
and again only one system is on, wondering wither it would need to power down the router overnight, hmm already set it back to factory settings and re-installed it mind u and no change,

had a look at the help bit in the router there for the bridge filters and still a bit unsure what numbers i need ? Also just done a full firewall check in grc as i am using firewall on router and also zonealarm pro came back as fully stealth?

---

### Post by Henry Rayker on 2006-11-02
You could turn the router off overnight. Whoever has been leeching off of you may well quit due to the fact that they no longer have a connection, but that's not a permanant solution. ](*,) 

You could set up some passcode protection on the router (the passcodes will work just fine with windows; the devices were made to work with it, lol)

The problem won't be solved by a firewall or reformatting any of your computers. Basically, your router's front door doesn't have a lock on it. A passkey is the same as someone needing a key, a MAC addy filtering is more like the door has a personal gate-keeper.

I'm not very familiar with this particular router (mine is an older d-link deal). I'd try to look in your router's help section for "MAC Address" filtering or something similar. This is what I think would be best for you to configure.

On the system that is currently the only one on, do this:
click Start, then Run, then type cmd in the text box.
Type in ipconfig/all in the Command Prompt Windows.

The Physical Address that it returns is your MAC address on that computer. Give me that number. At least this way we'll figure out which of those are intruders.

---

### Post by vmaxchick on 2006-11-02
the address has been sent in private post, what i can do is switch if off overnight and try and reset the full thing and see info about the bridge filter thing. Dont want to keep filling your head tonight as u must have other things to do, here i am sitting here with my legs bandaged up, god im off my head haha you know what we are all like when it comes to computer issues

---

### Post by Henry Rayker on 2006-11-02
I would recommend allowing this ip, as well as any other ips and disallow all others, if you can get that set up.

I'd recommend using the link I posted above (for finding your other machines' MAC addresses (well, if it's just the ubuntu and windows xp, then you will just need the instructions I just gave as well as the one on the back of your usb device).

I think you need to set it up like this, though:
Source MAC: machine's MAC
Destination MAC: your router's MAC. Choose the WLAN MAC for the wireless ones, and the LAN MAC for the wired machines.

Say your LAN MAC is 00:00:00:00:00:00, your WLAN is 00:00:00:00:00:01. Say you have one machine that is wired to the router with the MAC 00:00:00:00:00:11 and one wirelessly connected with the mac 00:00:00:00:01:00

you would want to set them up like this
Source MAC            Destination MAC
00:00:00:00:00:11     00:00:00:00:00:00
00:00:00:00:01:00     00:00:00:00:00:01

I hope that kind of makes sense. Keep me updated.

---

### Post by vmaxchick on 2006-11-02
cheers henry will email tomorrow x

---

### Post by vmaxchick on 2006-11-03
Hi there i managed to secure the wireless router, really unsure of abuntu now as this did not occur until i had installed that on my spare system, confuses the life out of me here. But all is secure now and the corresponding systems showing are the only ones that should be there 2 when both are on and one when main system is on.

Do you reckon i should try the ubuntu again or take a side step from it? do know why i left me wide open....

thanks for your help, your a star

---

### Post by Henry Rayker on 2006-11-03
I can assure you that Ubuntu had nothing to do with your router being compromised.
 
Think of it this way: You hide a key outside your door under a rock. Every morning, you eat breakfast; every day, you come home and your house hasn't been broken into. One day, you forget to eat breakfast; you come home and someone's used your spare key to get into your home and steal everything you've got. Are you going to try to blame the robbery on the fact that you didn't have breakfast?

The operating system on your machine has no control over the router's settings.

Did you secure your system via the MAC filters, or by either WEP or WPA (or similar) passcodes?

---

### Post by Henry Rayker on 2006-11-06
Not sure that you're still checking back here, but I started to have some trouble with my wireless card after I made my last post...the bugger would just drop connection randomly...well, I recompiled the drivers and bingo! completely functional...

Bad news is, you'll need an internet connection to download them, but I followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=106846"). If you ever get around to trying to set it up, let me know, and I can help you.

---

