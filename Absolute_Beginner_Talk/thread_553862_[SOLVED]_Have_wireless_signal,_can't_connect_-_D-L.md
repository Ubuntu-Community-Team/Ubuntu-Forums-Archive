---
title: "[SOLVED] Have wireless signal, can't connect - D-Link DWL-520+ PCI card"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by bobafifi on 2007-09-18
I've got a PC that I just put Feisty Fawn 7.0.4 on. I'm trying to have it be a wireless machine and have a D-Link DWL-520+ PCI card installed.  The card seems to be picking up the signal OK (typically showing 40% -> 50% strength from both my router as well as a neighbor) and my laptop has no problem, but Firefox on the PC won't connect. Any ideas?

Many thanks in advance,

-Bob

---

### Post by SpiritIsReality on 2007-09-18
howdy
it seems you're well along the network trail,
sounds like some ping tries, and check ifconfig -a

here's some links that help me

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=wireless&titlesearch=Titles)
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29)
[http://aboutdebian.com/](http://aboutdebian.com/)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://www.firewall.cx/](http://www.firewall.cx/)

[http://www.google.ca/search?hl=en&q=linux+networking+troubleshooting&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking+troubleshooting&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+networking&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking&btnG=Search&meta=)
[http://en.wikipedia.org/wiki/Computer_networking](http://en.wikipedia.org/wiki/Computer_networking)
[http://www.dmoz.org/Computers/Software/Networking/](http://www.dmoz.org/Computers/Software/Networking/)

trails

---

### Post by bobafifi on 2007-09-18
Thanks fmat,
I've talked with a couple of computer techs and they seem to think I don't have the driver for the 520+
I know I haven't installed any, are they right?  If so, where do I go to get the driver??

Thanks again,

-Bob

---

### Post by ricardoarguello on 2007-09-19
Those are Windows computer techs, because Linux has no "drivers".

---

### Post by bobafifi on 2007-09-19
Hi Ricardo,
> Those are Windows computer techs, because Linux has no "drivers".

Apparently there's acx111, which I'm not sure how to activate/install since I don't have Windows (for ndiswrapper) on the machine at all anymore:
[http://ubuntuforums.org/showthread.php?t=3484](http://ubuntuforums.org/showthread.php?t=3484)

Do you know anything about that?

Thanks,

-Bob

---

### Post by SpiritIsReality on 2007-09-19
howdy
20 hours ago!! sorry about that.
ya right. it seems ndiswrapper uses the windows driver and back engineers it into a module

I used the ubuntu ndiswrapper guide and the driver from ndiswrapper
to get the linksys wpc54g card working on a toshiba satellite 2140 xcds.
that's the full extent of my knowledge of ndiswrapper. 
edit : (When the kernel
get's updated, I have to run the install scenario again to connect.)
edit : the ndiswrapper now stays intact with a kernel update.
edit : now, when the kernel gets updated, I just have to re add the 
acpi=force pci=biosirq
to the root lines in /boot/grub/menu.lst. It's my fault,
I have to learn to manage that file...the options.
I personally like to remove the 
quiet splash 
from the root line. 
at terminal command prompt, type
zless /usr/share/doc/upstart/README.Debian.gz
press enter, use up down arrows to view,
press q to quit.

here's a search for your driver
[http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+DWL-520%2B&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Andiswrapper.sourceforge.net+DWL-520%2B&btnG=Search&meta=)
on this next page, I click on edit, at the top left of firefox window,click on, find in this page,
and at the bottom of the window, in the find box, I typed, dwl-520+.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)
you can hold the Ctrl key down and press the plus or minus keys to change the size of the words (font)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ndiswrapper&titlesearch=Titles)
this next page, along with the driver from ndiswrapper will hopefully get you back in the saddle.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)
on the address for the above page, you can delete the ?highlight and everything after that, click on the shortened address and click arrow,(or press enter key) = to get rid of the ndiswrapper highlight
[http://en.wikipedia.org/wiki/Ndiswrapper](http://en.wikipedia.org/wiki/Ndiswrapper)

sometimes it seems wicd works better than network manager
[http://ubuntuforums.org/showthread.php?t=507939&highlight=dwl-520](http://ubuntuforums.org/showthread.php?t=507939&highlight=dwl-520)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

that acx111 chip
[http://www.google.ca/search?hl=en&q=acx111&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=acx111&btnG=Google+Search&meta=)
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

once you get this card workin', you could write up a howto. try the advanced search,
keyword, dwl-520, titles only.

[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

trails

---

### Post by penguinv on 2007-09-19
(from the penguin with the simple minmd)
I may be on the wrong path but I had this thought.

You don't say the modem won't connect. 
You say Firefox won't connect.

Is this the situation in which the modem is connected but firefox can't get any pages?

That can have many forms and is a common problem.
One is if the DNS is wrong. 
Also if the base has WEP and the password is wrong, then you will connect but not get any pages.

Just a thought.
All the best.

---

### Post by bobafifi on 2007-09-19
Thanks for the replies fmat and penguinv!

Here's a screenshot:
[[IMG]http://img215.imageshack.us/img215/1602/wifiscreenshotuq2.png[/IMG]](http://imageshack.us)

If you look up at the top right (by the date), you can see the four wifi signal bars - two of which are blue.  When I hover over them, it shows connections ranging from 40%-50% (this is about what my Mac laptop is showing too, so I think that's about right for what signal strength my wifi router is putting out). 

anyhow...

From the screenshot, all those zeros can't be a good sign - can they?? How do I change that info?

Thanks again for the help! :-)

-Bob

---

### Post by SpiritIsReality on 2007-09-19
howdy
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

trails

---

### Post by bobafifi on 2007-09-19
Thanks for the links fmat :-)

I've been going through the troubleshooting page and have just run the iwconf command.  This is a screenshot of the return:
[[IMG]http://img292.imageshack.us/img292/1517/iwconfkd2.png[/IMG]](http://imageshack.us)

What does this mean??

Thanks again,

-Bob

---

### Post by SpiritIsReality on 2007-09-19
howdy

wow! screenshots. I'm gonna have to try that sometime.
well pard. you've got a tenderfoot greenhorn dude here.
if somebody could jump in here and put me out of my misery
I'd appreciate it, but until then...

OK, so we're on this page here?
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
and you ran the iwconfig
just curious if you 
"To begin with you'll need to set your Wireless Router up as an 'open' network. This means you'll need to turn off all security such as WAP, WEP and Mac Address restrictions. You'll be able to turn these back on later, we just want to make sure that they aren't causing any problems in the beginning.

You'll also need to give your network an ESSID. Most wireless routers have one set by default. Often it is "default", "linksys" "netgear" or some other generic name."

come on back

---

### Post by SpiritIsReality on 2007-09-19
well bob,
the next thing it says is
"Based on the iwconfig output from above, we know that "wlan0" is our WiFi card's linux device name. Knowing this you'll be able to use the Networking GUI tool to connect to your wireless router. (You may also see ath0 or even eth1 come up as your device name. Don't worry, that's totally fine, it just depends on the type of card you have and the drivers that are accessing it.)

Click on (System)->(Administration)->(Networking) and see if your wireless network card is listed. If it isn't you've got a problem. (Somebody needs to describe what to do next) <!-- Is it possible for wireless interface to be in kernel and not be recognized by the GUI tool? If the tool is reliable we can reference user to troubleshooting a driver. --> "

that'd be about where we're at now
wlan0 is our wifi card's linux device name.

come on back pard, are you there?

---

### Post by SpiritIsReality on 2007-09-19
> **bobafifi said:**
> Thanks for the links fmat :-)

I've been going through the troubleshooting page and have just run the iwconf command.  This is a screenshot of the return:
[[IMG]http://img292.imageshack.us/img292/1517/iwconfkd2.png[/IMG]](http://imageshack.us)

What does this mean??

Thanks again,

-Bob

it looks like fancy talk to me for "a 44%signal 2out of4 bars are green"
and we're not hooked up with the router yet

that about right?

OK back to the cactus...I mean the books...I mean this page here, haha!
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

are we still travelin' pard?
this is kinda like a horse wranglin' job in the yukon...exciting as long as nobody
get's hurt....and try not to mess your pants on the close calls...haha!

---

### Post by lentomies on 2007-09-19
Did you try RIGHT clicking on the SIGNAL BAR and then connecting? YOu may need to enter router P/W etc...

Also, did you go to SYSTEM --> Administration -->  Restricted Devices Manager and confirm everything?

I went through just this process and then everything was working for me... Hopefully it well for you toooo........

---

### Post by SpiritIsReality on 2007-09-19
lentomies ...howdy pard

It's sure good to see you

I'll just tag along for a while if'n you don't mind.
I'm interested in how this things gonna turn out

trails

---

### Post by lentomies on 2007-09-19
Cool.... See it it works and let us know....

---

### Post by bobafifi on 2007-09-19
Just found this - apparently I need to disable NetworkManager (I've run the first two commands). Getting stuck now on the commands that need to be executed as root (get permission denied replies).  How do I do that??
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

Feisty Fawn (7.04)

The driver and firmware work out on Feisty after having disabled NetworkManager [1] as well, with firmware revision 1.2.0.34 (for acx111 PCI) and an upgraded driver, v0.3.36.

To disable NetworkManager permanently:

 sudo /etc/dbus-1/event.d/25NetworkManager stop
 sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

The following two commands need to be executed as root:

 echo "exit" > /etc/default/NetworkManager
 echo "exit" > /etc/default/NetworkManagerDispatcher

Then configure your card as usual. Afterwards you might need to do:

 sudo ifdown wlan0
 sudo ifup wlan0


//
Thanks fmat,

-Bob

---

### Post by SpiritIsReality on 2007-09-19
to run those 2 commands as root, you type
sudo echo "exit" > /etc/default/NetworkManager
sudo echo "exit" > /etc/default/NetworkManagerDispatcher
if you want to give that a try, I'm with you

---

### Post by SpiritIsReality on 2007-09-19
if'n I was me...
I'd be goin after this page too
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

back to the acx driver. it says it's available in those two packages.
or do you figure that's what's given you your 44%.,the acx driver.
can you give us an ifconfig -a for the hell of it

---

### Post by bobafifi on 2007-09-19
> to run those 2 commands as root, you type
> sudo echo "exit" > /etc/default/NetworkManager
> sudo echo "exit" > /etc/default/NetworkManagerDispatcher

I've tried several times with that exact syntax - keep getting denied.  Is there another way?

Thanks fmat,

-Bob

---

### Post by SpiritIsReality on 2007-09-19
I cd'd to /etc/default and there's no NetworkManager there to add an exit to

try on yours, 
```
cd /etc/default
```
then
```
ls
```
and see if a Networkwhatever is there

so, what they want is to create those two files with the word exit in them

---

### Post by bobafifi on 2007-09-19
Not sure what's going on, but the NetworkManager seems to have disappeared from the menu - even though I get 'Permission denied' replies! 

So now that I don't have NetworkManager showing, how does one "Then configure your card as usual" ??

Thanks fmat,

-Bob

---

### Post by SpiritIsReality on 2007-09-19
OK
to run those two commands as root,
you type ```
sudo -i
```
then press enter and enter your passwd.. you get a # prompt, which means you're root
then you can enter the two commands.
you're in the saddle
after you've got the two commands to work, you
```
exit
```
and that get's you back to a $ prompt. the regular
user with sudo privileges.

from
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> Special notes on sudo and shells

    *

      None of the methods below are suggested or supported by the designers of Ubuntu.
    *

      Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.
    *

      To start a root shell (i.e. a command window where you can run root commands), starting root's environment and login scripts, use:

sudo -i     (equivalent to sudo su - , gives you roots environment configuration)

    *

      To start a root shell, but keep the current shell's environment, use:

sudo -s     (equivalent to sudo su)

oops...haha
and there's```
man sudo
```
and
[https://help.ubuntu.com/7.04/advanced-topics/C/index.html](https://help.ubuntu.com/7.04/advanced-topics/C/index.html)

---

### Post by SpiritIsReality on 2007-09-19
that's a good question
I'll get back to you on that
it's back to the cactus for me
I mean books...

---

### Post by bobafifi on 2007-09-19
> sudo -i
Yup - got root with that and ran commands without PD replies - yay! :-)

> I'll get back to you on that

OK, thanks - I don't have a clue what "Then configure your card as usual" means...

-Bob

---

### Post by SpiritIsReality on 2007-09-19
have you tried this
Click on (System)->(Administration)->(Networking) and see if your wireless network card is listed. If it isn't you've got a problem. (Somebody needs to describe what to do next) <!-- Is it possible for wireless interface to be in kernel and not be recognized by the GUI tool? If the tool is reliable we can reference user to troubleshooting a driver. -->
from here
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
does your card show up, wlan0
edit: it's system>admin>network and your card should show up there. left click it, click properties
...or K>system settings >network settings
I'm gonna grab a plate of beans or whatever
and get back to you in 1/2 hour or so
trails

---

### Post by bobafifi on 2007-09-19
> have you tried this
> Click on (System)->(Administration)->(Networking) and see if your wireless network card is listed.

I don't show a 'Networking' link in the menu - just 'Network' and 'Network Tools' . Card isn't listed in either (or I'm not looking in the right place). Do you have a 'Networking' link in your menu??

Thanks fmat,

-Bob

---

### Post by SpiritIsReality on 2007-09-20
howdy
no networking here

edit: it's system>admin>network. 
or K>system settings > network settings.

ya we disabled the NetworkManager with the commands you ran:
> To disable NetworkManager permanently:

 sudo /etc/dbus-1/event.d/25NetworkManager stop
 sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

The following two commands need to be executed as root:

 echo "exit" > /etc/default/NetworkManager
 echo "exit" > /etc/default/NetworkManagerDispatcherfrom here
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

then we're here
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
at the heading "Using the command Line" and the aim is
to follow along and "cofigure the card as usual." haha!

(sorry about the "system>admin>networking", was havin' a bit of trouble keepin' tabs on the string)
but I'm OK now...now...n

---

### Post by bobafifi on 2007-09-20
Thanks fmat - still no go on this end I'm sorry to say :-(
BTW, I just checked on your wpc54g card and it's  for a laptop, right? 
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1115416827032&pagename=Linksys%2FCommon%2FVisitorWrapper)

I'm trying to get a PCI card to work (my Mac laptop connects no problem to the same wireless signal as does a friends' PC laptop, so I know it's not the signal). If you've got a PC desktop, I'll be happy to send you the card - just send me a note.

Thanks again,

-Bob

---

### Post by SpiritIsReality on 2007-09-20
howdy
how far did you get on the configuring at the command line.
bring me up to speed

---

### Post by SpiritIsReality on 2007-09-20
could you post your ```
ifconfig
```

---

### Post by SpiritIsReality on 2007-09-20
> just checked on your wpc54g card and it's for a laptop

yup

> I'm trying to get a PCI card to work (my Mac laptop connects no problem to the same wireless signal as does a friends' PC laptop, so I know it's not the signal). If you've got a PC desktop, I'll be happy to send you the card - just send me a note.

it's good to know you can connect with your Mac
I've got the wireless laptop, and a desktop wired to a linksys wrt54g.
the wrt54g is runnin' openwrt from openwrt.org and is client/bridged
wireless to a dlink DI-524 router.
I'm thinkin' we could try to get your card workin', but probably not a good
idea to be sending it to me.On this internet riggin', if a blacksmith can't
get it workin' at your place, he's not going to get it workin' at his place
either. IMHO..but what do I know..ha and there's far better smith's around
if we could just flush one out of the bush.



holler when you get back
trails

---

### Post by SpiritIsReality on 2007-09-20
> **lentomies said:**
> Did you try RIGHT clicking on the SIGNAL BAR and then connecting? YOu may need to enter router P/W etc...

Also, did you go to SYSTEM --> Administration -->  Restricted Devices Manager and confirm everything?

I went through just this process and then everything was working for me... Hopefully it well for you toooo........

I sure would have liked to try that.
maybe yet
trails

---

### Post by SpiritIsReality on 2007-09-20
back to the cactus
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)
free linux books online

---

### Post by bobafifi on 2007-09-20
Bingo! I'm in and posting from the machine - yay! :-)

Here's what I did:
I redid the kill commands for NetworkManager, this time using sudo -s 
Then I did a ping test which much to my surprise and delight - worked!
Here's a screen shot of the terminal:
[[IMG]http://img218.imageshack.us/img218/2682/terminal1cx8.png[/IMG]](http://imageshack.us)



Thanks so much fmat for the help! 

-Bob

---

### Post by SpiritIsReality on 2007-09-20
good news

now the forum thing to do is to click on thread tools at the top of the page
and mark it solved.
I'm sure glad you got it workin'.
maybe you could write a howto and post it to the tips and tutorials forum.
check the sticky threads at that forum.

trails

---

### Post by bobafifi on 2007-10-01
Hi fmat,

Well after a week of wifi bliss, I'm sorry to say I'm back to no-wifi after I reinstalled the system to pick up a new monitor. Fortunately, the monitor resolution is killer but I've somehow missed a step in setting up the wifi.  I've disabled NetworkManager as before, but can't connect. Here's what I show for iwconfig:

bobafifi@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"STABF6CA2"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=0/100  Signal level=63/100  Noise level=45/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Do you know the commands to set up a card and connect without using NetworkManager?

Thanks,

-Bob

---

### Post by SpiritIsReality on 2007-10-01
howdy
Vadi recommends wicd here [http://ubuntuforums.org/showthread.php?t=562479](http://ubuntuforums.org/showthread.php?t=562479)
Just about everything you would need to know about wireless is here
 [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
You've already got the main command figured as far as I know, iwconfig, if you want to go command line. There's better help in the WifiDocs than I can give.
IMO I'd give the wicd a try first, then can look at man iwconfig for a backup plan
all the best
buds

---

### Post by bobafifi on 2007-10-02
Got it!
Folks - please don't waste your time with 7.04 (like I have!) trying to find a workaround for the wifi problem and the D-Link 520+ card - it's simply not worth it.  After many long hours of searching and reading, I found out that there is a bug with 7.04 for all the cards that use the same chip set as the 520+ ----- yikes! :-|
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118539](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/118539)
 
Fortunately, there's a happy ending to all this - it's the beta release of 7.10 which you can download here:
[http://cdimage.ubuntu.com/releases/gutsy/beta/](http://cdimage.ubuntu.com/releases/gutsy/beta/)

Many thanks to all those responsible for fixing this bug - I've got wifi once again! :-)

-Bob

---

