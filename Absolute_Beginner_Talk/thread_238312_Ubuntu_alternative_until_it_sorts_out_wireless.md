---
title: "Ubuntu alternative until it sorts out wireless"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by infocom on 2006-08-17
HI

I really want to use Ubuntu but can't get wireless to work for both wireless cards I have (Belkin and Level One) so would like to know what Linux can people recomend I use that is as user friendly as I heard Ubuntu is, until it sorts out its wireless installation?

Thanks

---

### Post by waldschm on 2006-08-17
Hey, sorry to hear you're having wireless problems. Have you tried installing network manager? I installed ndiswrapper and network manager using automatix [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Using network manager which has a system tray icon in the upper right hand corner I was able to connect pretty easily. If you're still looking for another linux distribution, I'm afraid I'm not that knowledgeable especially in terms of wireless auto-detection. Maybe someone else could comment on that?

---

### Post by msak007 on 2006-08-17
I agree that you should give Network Manager a shot. Wireless was hell in Breezy (especially using WPA), but it's very easy using Network Manager. Also, some cards have native drivers (depending on the chipset being used), and others need to use ndiswrapper (using Windows drivers) to be able to work. If you need help, I'm sure people can offer their advice and suggestions if you post the specific model of the cards. The only other distro that I know of that makes it easy to use wireless is SuSE. I used it for a while before Dapper was released, and YaST (their configure everything GUI program) makes it easy to configure and use your card, with native support for WPA (if you use that encryption). It's the only other distro I've used extensively that I know has an easy to use GUI configuration for wireless. Also, Network Manager is a Novell-developed app so SuSE is the only other distro I know of that uses it (Novell owns and develops SuSE). Of course I haven't tried their latest release of OpenSuSE 10.1 (last one I used was 10.0), so I'm not sure how much has changed.

---

### Post by weekend warrior on 2006-08-17
I believe you've been misled infocom. There are a number of wireless cards that will "just work" on Ubuntu, including by the way, the Belkin F5D7050 v2000 built on the Ralink rt2500 chipset. It doesn't need ndiswrapper. It doesn't need anything at all. The drivers are in Ubuntu by default.

Click my signature for wireless cards that **do** work, and what's more - without any installation configuration nonsense. It probably means investment in a new card yes, but it's well worth the money for the frustration you will avoid.

Here's an example of someone who went through what you're probably going through now, and the happy ending. [>> click me]("http://ubuntuforums.org/showthread.php?t=234143")

---

### Post by infocom on 2006-08-17
What wireless card do you have? I have been reading that the Belkin ones are problematic. Theres loads of problems people have instaling it. 

I think if linux is ever to break onto the desktop market it really needs to be user friendly. I thouhgt thats what Ubuntu was but yet there are still loads of "How Tos" that you need to enter command prompts. Normal desktop users at home and workplace are just not that capable so issues like this mean it will never break away from techies. Its a shame as I dont want to use Windows any more but over the years Linux just hasnt been able to compete on the installation and setup stages.

Althogh it may not be the fault so much of the developers as I also ready BElking drivers are closed source and they only develop for Windows. And the major retailers stock Belkin more than any other I find. So I suppose until major manufacturers sort themselves out and retailers support Linux we're stuck wint Windows.

---

### Post by infocom on 2006-08-17
jeez my typing is useless :)

---

### Post by weekend warrior on 2006-08-17
Personally I have a Belkin F5D7010 that's on the Free Software Foundation's list of cards that work well in Linux. It works straight out of the box, just plug it in and boot up. 

If you do need to buy a new device, do your homework first. The list in my sig is a very good resource. Be very careful with version numbers on cards or adapters if they are specified since some card makers change chips even in the same model or series. What you want is a device with a Ralink chipset, that's the key.

---

### Post by infocom on 2006-08-17
I wont give up then!! I am reading forums and it looks like there are a choice of drivers that this could use (different chips or something?). And each one has a different process to follow by looks of it. So how do I found out which one is my card? i.e. theres talk of rt73, rt2500 etc. It doesnt say on box. My driver file is BLKWGU.inf.

Thanks

---

### Post by infocom on 2006-08-17
Sorry but replies have been coming in fast so my replies are out of place. To msak007, I did try using Network Manager. Althouhg, can I just ask, is that System -> Administration -> Networking? 

Because after installing ndisgtk to install the driver, after driver installing Networking would not work. It wa sgreyed out, hung and just the spinning circle. I have installed ndiswrapper-utils.

Laurie

---

### Post by weekend warrior on 2006-08-17
There *should* be a version number somewhere - either on the device itself or in the documentation. You have a 50/50 chance here. If it's the v2000 it's probably Ralink and you're home free. You won't need any driver files from Windows. If not..., well it's probably a Broadcom < that's the one the gives people difficulty.

Then you need to make a decision. Soldier on and deal with the more-than-likely frustration, or simply take a look on eBay and grab one on the cheap that will work automagically.

---

### Post by infocom on 2006-08-17
Nah cant find it anywhere. Just says F5D7050Uk everywhere.

---

### Post by bensexson on 2006-08-17
What is the model number of the card including rev number if any?

---

### Post by infocom on 2006-08-17
ok, i had to take this thing apart. On the board is:
P/N: 141450120011J REV: 01

There's a barcode sticker that says:
001150B0DF24  WN4501H-LF-AK
(think the 00.. is a MAC address it also has it on casing)

The what I think is the chip says:
ZyDAS ZD1211B-QF

Then my eyes start to hurt.

There are other numbers thatg dont seem ot meanmuch, really small, no title.

---

### Post by waldschm on 2006-08-17
Networking under System->Administration is not the same as network manager, network manager has to be installed using either Synaptic or sudo apt-get. I think it is being included by default with dapper though? Anyway, I agree ndiswrapper is not necessary depending on your card and network manager isn't either. Network manager did help me get my wireless working however when I couldn't figure get the tools included with dapper to work.

---

### Post by infocom on 2006-08-17
I cant find Network Manager. Do you know how to install it?

---

### Post by infocom on 2006-08-17
Is zd1211b a relevant version/driver/chipset? Thats what some other sites say and thats what it says in my driver file BLKWGU.inf.

---

### Post by weekend warrior on 2006-08-17
Open Synaptic and use the search to find network-manager or network-manager-gnome and then install with a right click on it.

I'm also getting conflicting info on the "uk" version. It isn't listed specifically on the Ralink list but I did find [this]("http://ubuntuforums.org/showthread.php?t=201754"). Not too promising though I'm afraid. :( 

[Here]("http://www.ubuntuforums.org/showthread.php?t=144151"), the user has the same model and got it working with ndiswrapper apparently.

---

### Post by weekend warrior on 2006-08-17
[This thread]("http://ubuntuforums.org/showthread.php?t=197363") makes reference to your driver file - BLKWGU.inf, and they're also using ndiswrapper.

---

### Post by infocom on 2006-08-17
I did but nothing shows up in Synaptic for network manager. I have the Ubuntu live cd in and it is checking that too.

---

### Post by waldschm on 2006-08-17
It really should be in synaptic under network-manager if you do a search but try this in the terminal (Applications Menu->Accessories->Terminal):

sudo apt-get install network-manager-gnome

If this doesn't work there is an issue with your repositories

---

### Post by infocom on 2006-08-17
It says Couldn't find package network-manager-gnome

I can only use the Live CD as a repository as I cannot connect to internet without fixing the wireless.

---

### Post by waldschm on 2006-08-17
Oh I understand I apologize, I assumed you had landline access to update your computer until you got wireless working. Yea, I don't think you will be able to get network manager without internet access. But you may be able to download the .deb on another computer if you were still interested.

---

### Post by infocom on 2006-08-17
YES! Thats what I have been doing! So can you let me know where I can download it? I did a quick search and cant seem to find anything.

---

### Post by infocom on 2006-08-17
I may give up and buy one. There is very few to choose from that will work from this list:-
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

Anyone recomend any? Looks like the LinkSys ones are the best to go for. Lots of them on eBay. Couldn't find any of the others on eBay Ugly things though.
[http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&flt=9&catref=C6&from=R10&satitle=WUSB11&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=Postcode&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=3&fsoo=1](http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&flt=9&catref=C6&from=R10&satitle=WUSB11&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=Postcode&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=3&fsoo=1)

---

### Post by waldschm on 2006-08-17
Hmm, I don't really know myself but a quick google search turned up these links

[http://www.ubuntuforums.org/archive/index.php/t-186175.html](http://www.ubuntuforums.org/archive/index.php/t-186175.html)
[http://packages.ubuntu.com/dapper/net/network-manager-gnome](http://packages.ubuntu.com/dapper/net/network-manager-gnome)

---

### Post by weekend warrior on 2006-08-17
As I said before, click on my signature below, there are quite a few to choose from.

I think giving up on this one is a wise choice. You need to know which fights are worth fighting and which simply aren't. There's a reason the 7050 isn't on the FSF list.

---

### Post by Metacarpal on 2006-08-17
> **infocom said:**
> I may give up and buy one. There is very few to choose from that will work from this list:-
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

Anyone recomend any? Looks like the LinkSys ones are the best to go for. Lots of them on eBay. Couldn't find any of the others on eBay Ugly things though.
[http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&flt=9&catref=C6&from=R10&satitle=WUSB11&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=Postcode&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=3&fsoo=1](http://search.ebay.co.uk/search/search.dll?sofocus=bs&sbrftog=1&flt=9&catref=C6&from=R10&satitle=WUSB11&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=Postcode&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=3&fsoo=1)

Hmm.  I didn't see mention in the thread on whether you're using a desktop or a notebook computer.  If you're on a notebook with PCMCIA (PC-card) slots, I highly recommend [this card]("http://www.compusa.com/products/product_info.asp?product_code=333622&cm_mmc=bazaarvoice-_-RLP-_-928611-_-description_link").  It's what I have in my computer, works great out of the box, and it's nicely inexpensive.  (They're available in-store only right now, though...)

---

### Post by infocom on 2006-08-17
Do you think the LinkSys WUSB11B will be OK? It says its OK here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

But its not on your page. I think its a good price on eBay.

I also have a LevelOne WNC-0300USB but I there were even more problems trying to install that. 

So I am giving up and will buy one.

---

### Post by infocom on 2006-08-17
Hi Metacarpel

Thanks but its a Desktop and is other side of the house from router so need a wireless and would prefer USB. I can use the USB for my laptop too then on which I will also try to install Ubuntu if this works out.

---

### Post by Fitzcarraldo on 2006-10-07
> **weekend warrior said:**
> Personally I have a Belkin F5D7010 that's on the Free Software Foundation's list of cards that work well in Linux. It works straight out of the box, just plug it in and boot up. 

If you do need to buy a new device, do your homework first. The list in my sig is a very good resource. Be very careful with version numbers on cards or adapters if they are specified since some card makers change chips even in the same model or series. What you want is a device with a Ralink chipset, that's the key.

*weekend warrior*,

You were lucky with the Belkin F5D7010 card. My brother had a terrible time getting it to work (as documented in the following thread):

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

