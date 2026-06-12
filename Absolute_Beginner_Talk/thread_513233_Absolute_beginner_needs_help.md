---
title: "Absolute beginner needs help"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by jhumroo on 2007-07-30
I want to install Ubuntu 6.06 on a Gateway SOLO 2500 laptop and am having problems with getting my D-Link DWL-650L1 wireless PCMCIA card work in Ubuntu.

Let me begin by saying, I am an absolute beginner. I have NEVER used Linux. I use Mac OS X for my work and Win XP for testing etc. I am familiar with GUI based applications but not the Terminal.

This laptop currently has Win XP installed and the D-Link card works with it. But when I ran the Ubuntu live CD, I was not able to connect to the Internet. I checked under the Device Manager and saw that it did recognize the card, so I don't know why its not working.

I read mixed messages on some of the forums where folks reported problems as wells as successes; however, the solutions described in the forums are GREEK to me--I don't understand what they are talking about.

Are there any newbie step by step instructions available anywhere to help me resolve this problem?

I need to be able to connect to the Internet if I install Ubuntu on this laptop, else it's useless to me. I'm sure others have had similar issues so any help would be greatly appreciated.

Thanks in advance.

---

### Post by jhumroo on 2007-07-30
**Follow-up:** When I said the Device Manager recognized the card, I meant that it saw the card and knew it was a D-Link network card, but the same card doesn't show when I go into Network Settings. Only option available there is the Modem.

P.S. This laptop does not have a wired/Ethernet port.

---

### Post by n.aggel on 2007-07-30
> **jhumroo said:**
> I want to install Ubuntu 6.06

This laptop currently has Win XP installed and the D-Link card works with it. But when I ran the Ubuntu live CD, I was not able to connect to the Internet. I checked under the Device Manager and saw that it did recognize the card, so I don't know why its not working.



Hi,

first of all, why don't you install {or try the live cd } from the newer ubuntu 7.04, you maybe get lucky and get your equipment recognized...

The fact that device manager recognizes the card doesn't mean that it will work...

Search to see if there are drivers for your card...and try to install them...

hope i helped...

---

### Post by DalekClock on 2007-07-30
Have you configured your network connection under System > Administration > Network? That's how it worked for me.

---

### Post by jhumroo on 2007-07-30
Thanks for the quick responses ;-)

n.aggel: I am a newbie; I've never used Linux and don't even know how to begin installing a driver for the card.

DalekClock: I don't see the card under System > Administration > Network

---

### Post by ZeroPerCento on 2007-07-30
Hi jhumroo,
try to see if your D-Link card is supported. Check [here]("http://support.dlink.com/downloads/") and you will see if there's a driver suitable for Linux.

If yes download it and search the forum to know how install a package.
Bye!!

---

### Post by dreaswar on 2007-07-30
hi.

i m a new bie too.. i have been using linux for past one week. 
i had the same problem with my DWL G630. I tried this and it worked.

first of all...ubuntu has documentation in its site about the various wireless manufactures and thier cards. just see if yours will work. they have workarounds if it dosent work out of the box. 

mine didnt work out of the box and i had to download the latest ndiswrapper and ndiswrapper utils. 

now you have to find a wired internet connection to do this. once you are connected go to the add/remove programs and under the section "All" search for ndiswrapper and ndiswrapper utils. install both. 

ndiswrapper wireless windows driver installer wil then come listed under the Administration tab which is under the system tab on your menu bar.

you will need your Dlink cd at this point. use it to copy the .inf and .sys files which are in the driver folder. 

then you use the windows wireless driver utility to add the .inf file location and click on install. 

even then it didnt work immediately. i removed and then reinserted my card and then had to configure the connection . 

click configure button on the utility to enable the wireless connection. i simply used DHCp to configure and it worked al rght. 

try it.

---

### Post by jhumroo on 2007-07-30
ZeroPerCento: My card DWL-650L1 doesnot have a Linux driver available on the D-Link site.

Thanks anyway :)

---

### Post by jhumroo on 2007-07-30
dreaswar: I think I read your entry last night in one of the forums. But being an absolute newbie, I am totally clueless as to some of the things you talk about.

Questions:
- where is the Add/Remove utility in Ubuntu 6.06 is it under Administrator?

- can I do this while running from the Live CD? or do I need to install and then try this?

- are the "ndiswrapper" and "ndiswrapper utils" already part of Ubuntu OR is it something I have to download and browse to find in Add/Remove?

- you said "use the windows wireless driver utility to add the .inf file location and click on install" do I do this step in the Administration tab?

Sorry for all the questions, and thanks for your help in advance.

---

### Post by dreaswar on 2007-07-30
ok..

1) you are trying to install a 6.06....while the latest version is 7.04.. if at all possible try installing that. 

2) i am not very sure abou the menu in 6.06. but if it is the same as in 7.04 it will be under the "Applications" in menu bar at the top. 

3) actually i also encountered the same problem of wireless card being not recognised in live d mode.. but usually when you are i live cd mode your administrative privilages are not present and it may not allow you to modify the system. I have tried this in another distribution of linux and it didnt work in live cd mode. 

4) In the CD version of 7.04 i have ndiswrapper is not part. Ubuntu also has a DVD version with lots more programs on it .. i dont know which you have may be it may be there.. it will be a package file with an extension of .deb.

if you dont find it in your DVD you wil have to have an active net connection ( you can use your wired connection for this ..) go to add/remove programs search for ndiswrapper and ndiswrapper util and install both. installtion is fairly simple and is only a few clicks.

5) after you have installed the ndiswrapper things through ubuntu , it would have placed an entry for "windows wireless drivers" under the "administration tab" which is under the "system tab" in your menu bar.

6) at this point use your Dlink CD na open it. under the folder named drivers there are few file. choose the .inf file and .sys file copy them both to a folder of your choice. 

7) run the windows wireless utility. Click on the install windows driver button and it willask you to specify the location of teh .inf file .. you do that and then hopefully it will install the driver .  After this click on the configure button and set enable the wireless connecton and set connection to DHCP under properties. 
if nothing happens even after that ..try removing  and reinserting the card. 

These steps worked for me. ofcourse my card is a DWL 630. It may worl for you too.

 Before you install any firm ware make sure you have got the hardware version and firmware version of your card correctly.It is printed on the undersurface f your card. I had a talk with customer support of Dlink when i was struggling with my card. I actually found a driver in Dlink website for my card ( for linux) but they told me they cannot guarantee it will work and they even told me it may damage the card. Actually i was told that this card will not work in Ubuntu. So dont lose heart.  They also were clear you should only download the drivers available from the website of dlink in the country where you purchased the card ..like if you bought it in usa go to us website and download the drivers .. not any other dlink country website even if the card number matches you should not do that. 

in any case just go to these links ... it will take a couple of days to build your knowledge base ansd be comfortable. just try it. 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
[URL="https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"]
https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide[/URL]

[https://help.ubuntu.com/community/WifiDocs]("https://help.ubuntu.com/community/WifiDocs")
[URL="https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink"]
https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink[/URL]

hope it works for you.. bye..
let me know.. being a newbie i will do al help i can..

---

### Post by jhumroo on 2007-07-30
dreaswar: Thanks a bunch for all the tips and links.

I've downloaded the latest 7.04 and will try out your suggestions. I will post an update of my experience soon.

---

### Post by dreaswar on 2007-07-30
hi..
just one more thing 

just wanted to tell you that if you are not experenced with ubuntu and want to give it a test ride... keeping windows on dual boot...try Wubi..

i think its Wubi.org

youcan do a real install of Ubuntu leeping Windows... noo need to partition and all that.. 

infact i am running Wubi. 

absolutely no problem. Only one thing. ,, it needs the alternate .iso file of the ubuntu cd .. no the regular 7.04 cd iso image you might otherwise download. 

try it.

---

### Post by jhumroo on 2007-07-31
What's the "alternate .iso file of the ubuntu cd"? Where do I find it?

I found Wubi here [http://wubi-installer.org/](http://wubi-installer.org/)

Thanks.

---

### Post by dreaswar on 2007-07-31
you ll find it in the download page itself. 

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

there is a check box at the bottom of the page for the alternate cd. 

try it.

---

### Post by jhumroo on 2007-08-05
Update: Still having problems.

Downloaded Wubi to try it with the the alternate ISO of Ubuntu 7.04, but it didn't work because it needs 4GB free space on the hard-drive (I only had 1+ GB free, Windows stuff was already taking up 4+ GB on this laptop). 

Then I tried booting from 7.04 live CD (I burnt from the regular ISO downloaded from Ubuntu).
- With a normal boot from the CD it hung-up when it got to the desktop (no menu at the top), and there was an error message saying it couldn't load some GNOME settings so some themes and sound files etc. wouldn't work.

- Then I booted in Safe Graphics mode; this time there was the same error but it got to the desktop. However, it was extremely slow and un-responsive when I tried moving the cursor to select items from the menu.

After an hour of frustration, I finally shut-down the machine and booted back into Windows (to write this post).

At this point, I don't know what else to try; maybe Ubuntu is not my cup-of-tea after all :(

---

### Post by dreaswar on 2007-08-08
hi..
hm.. so no space on the hard drive it seems.. cant help you there .. 

try free up some space on your hard drive.. either burn some cds or transfer some stuff to external hard drive.. 

i have done excactly that.. 

i have an external hard drive. All the data goes there and only OS is in the internal hard drive.. along with some programs my wife needs. so i have about 10 gb free on which i can install Ubuntu. 

mine is an old laptop .. a compaq evo N 400c. its about 6- 7 years old.. 18 gb hard disk .. and 384 mb ram. the cd rom is i think only 4 X. 

i had the prblem of the live cd booting up really slowly as my cd rom speed is only 4 X. but it ran well except for the wireless driver. 

so even if it as old machine it should worl well. 

the installed version works comfortably. It iis infact quicker and  more responsive than XP though boot process is a  slower ; may be because i instaled it through Wubi.

If at all you can make some space on your hard disk .. try ubuntu.. 

best of luck

---

