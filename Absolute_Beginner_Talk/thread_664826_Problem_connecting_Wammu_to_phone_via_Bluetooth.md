---
title: "Problem connecting Wammu to phone via Bluetooth?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Prodromoi on 2008-01-11
I feel like I've opened a can of worms here... and I thought it would be so easy!

I would like to get my mobile phone (a Nokia 6822) talking to my PC (running 7.10) via a USB bluetooth adapter.  I *think * I'm nearly there, but not quite.

The USB adapter I have (which I know isn't faulty, since it worked on my WinXP box) is an ES-388 (relatively cheap Bluetooth Class 1 dongle).  It appears that at least one other user has been successful in getting it to work under Linux (albeit under the Archlinux distro).  
[(Link to that post here)]("http://www.linuxquestions.org/hcl/showproduct.php?product=3312&cat=all")

I've installed bluez-utils and python-bluez.  My first attempt was to use Wammu as the front end GUI (and it was this that stated the two aforementioned packages were required).  If I can't get Wammu to work, or don't like it, I'll try gnocky or xgnokii.  (I've got gnome-bluetooth installed too.)

I can get as far as trying to detect the phone but this is where I get stuck - at a rather embarrassing obstacle.  The configuration wizard in Wammu states that I must have the phone and the PC paired first.  And *I don't know how to pair them up!*

I've paired other BT devices before (my phone, headset, PDA) so know my phone's BT does work.  Yes, the phone has Bluetooth activated and is discoverable.  I've set the PC to be discoverable as well.

But I've tried to detect the PC with my phone and PDA but can't find it.

Can someone please point out what I'm doing wrong?

---

### Post by dmitriyp13 on 2008-01-11
Try restarting the bluetooth daemon
```
sudo /etc/init.d/bluetooth restart 
```
This should force the daemon to inherit your specific environment variables and the pairing dialog should come up on its own when you start the pairing process from your phone.  Good luck.

---

### Post by Prodromoi on 2008-01-11
OK, done that.  Thanks.  That's got me a bit further and they can see each other now...

If it helps anyone (to help me!) this is the output when I try to run the Wammu configuration wizard:
(I've emphasised the line where it seems to be failing.)

```
Wammu is now searching for phone:
Starting /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Starting /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Starting /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Scanning for bluetooth devices using PyBluez
**Could not access Bluetooth subsystem (error communicating with local bluetooth adapter)**
Finished /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Finished /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Finished /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
All finished, found 0 phones
No phone has been found!
```

---

### Post by Prodromoi on 2008-01-11
This is getting more puzzling and frustrating by the minute.  I've got the things paired now and set as trusted devices of each other.  But I still can't get the Wammu wizard to correctly link to the phone.
```

Wammu is now searching for phone:
Starting /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Starting /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Starting /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Scanning for bluetooth devices using PyBluez
Checking nn:nn:nn:nn:nn:nn (Naberius) - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'bluerfphonet', 'bluerffbus', 'bluerfat']
Bluetooth device scan completed
Finished /dev/ttyS2 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Finished /dev/ttyS0 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Finished /dev/ttyS1 - ['at19200', 'at115200', 'fbusdlr3', 'fbus', 'mbus', 'fbuspl2303', 'phonetblue', 'fbusblue']
Finished 00:11:9F:02:48:A6 (Naberius) - ['bluephonet', 'bluefbus', 'bluerfgnapbus', 'blueat', 'bluerfphonet', 'bluerffbus', 'bluerfat']
All finished, found 1 phones
Following phone will be used:
Model 6822 (Nokia) on nn:nn:nn:nn:nn:nn port using connection blueat
```

(Where nn... is obviously my phone's MAC address.)  I thought I'd cracked it!  But a click of the "next" button and...

```
Wammu is now testing phone connection. Please wait.

Phone not found!
```

What's going on here?  Could it be a bug in Wammu, or can anyone suggest some alternative directions I can try?

---

### Post by Prodromoi on 2008-01-12
(Bump since the thread has now got a new title.)

---

### Post by finer recliner on 2008-01-12
im not sure what you're using wammu for, but may i suggest trying bitpim? its very poplular for managing files on a cell phone. use this guide for using bluetooth with bitpim: 

[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)

---

### Post by Prodromoi on 2008-01-12
> **finer recliner said:**
> im not sure what you're using wammu for, but may i suggest trying bitpim? its very poplular for managing files on a cell phone.

I've read through that article, thanks  (very comprehensive and well-written) and bitpim looks like it has potential (although the warning about its instability causes a bit of concern).  However looking further, reading through the bitpim.org site it seems that it offers *extremely* limited support for Nokia phones - only one being in the list of supported phones at the moment.

I'll add bitpim to my list of programs to try to sort this out, but given that it doesn't really seem designed to support Nokias, I'll probably try gnocky and xgnokii first.

---

### Post by Prodromoi on 2008-01-12
Alas, so far still a bust...

Could not get gnocky to compile
xgnokii would halt at the "connecting" screen, then just vanish
bitpim seems to not support my phone

I'm still trying to sort out the gnocky issue

---

### Post by jonathanku on 2008-02-02
Prodromoi, I feel your pain.

I started using KMobileTools after reading an article on [Linux.com]("http://www.linux.com/articles/122877"). I got so far with that, but couldn't export my address book to the KDE address book.

Next, I'm trying to use Wammu, but also not getting the phone discovered (I'm using a SonyEricsson).

Let us know how you get on!

---

### Post by jonathanku on 2008-02-02
OK - now getting Wammu to work in conjunction with kbluetooth.

Managed to back up my phone. Now to see if I can load my phonebook into the new phone!

---

### Post by SneakyWho_am_i on 2008-04-08
I tried kmobiletools a few minutes ago and it blew me away, doing all kinds of crazy things. It did fail to send or display SMS messages though.
I don't need to be able to do that but when I was a kid (heck I still am) I saw a movie where they typed a message into someone's computer and it ended up on someone's pager and I thought it was super cool.... So I want that.... heh.

@ how to pair two devices..... that little bluetooth icon in the gnome system tray let me do it. Here is some information from the gammu website on doing it by hand or something:
[http://www.gammu.org/wiki/index.php?title=Gammu:Connecting_to_phone#Bluetooth](http://www.gammu.org/wiki/index.php?title=Gammu:Connecting_to_phone#Bluetooth)

To get kmobiletools working I had to assign a device to my bluetooth device. I didn't know what the existing device if any) was called so I set one up as described here:
[http://ubuntuforums.org/showpost.php?p=3923279&postcount=4](http://ubuntuforums.org/showpost.php?p=3923279&postcount=4)

I didn't discover yet how to have it reinstate itself on startup though.

After my success with KMobileTools, I found a little system tray thing which could send sms messages (yay! more on that in a sec) and decided I still wanted an all-round solution that could do what kmobiletools did and still sent sms.

Still, wammu wouldn't connect to the phone......
So I installed gammu (hey, wait a minute, doesn't wammu need gammu?? Well, yes, yes it does... Apparently... So I don't know why it wasn't a dependancy)


Although I had bluez-utils installed, wammu didn't care, so I also installed python-bluez. Now it is able to detect my devices!
But after a while in "guided" setup in the wizard, it would ask for a "port" and say "enter an address"
Well, what do you want, man, a port or a @#% address!?!?

If I entered an address it would tell me that the address didn't exist. Fat lot of use that is then.
ut if I entered a port it would tell me that gammu wasn't configured.
I don't know how to configure gammu. I have no clue. So I created this configuration file by hand and dumped it in
```
~/.gammurc
```
Wait THIS file:
```
[gammu]
port = 00:18:0F:DE:24:8E
model = 6234
connection = bluephonet
synchronizetime = yes
logfile = gammulog
logformat = textall
use_locking = no
gammuloc = locfile
startinfo = yes
gammucoding = utf8
rsslevel = teststable
usephonedb = yes
name=
```

You could say "no" to the bit where I put "usephonedb = yes"
...
That will create some kind of tcp connection every time gammu does something to your phone and you will probably notice a huge performance increase if you turn it off. Suit yourself.
If you're wondering what values to put, check my first link. Also note that I basically selected the options recommended by the wammu phone wizard (odd that it can recommend them but then makes a near-blank config file...)

NOW......
DO NOT DO THE PHONE WIZARD
If you complete the phone wizard on any of the three modes (manual, guided or automatic), it will fail and destroy your .gammurc!!!!
In other words, only run the phone wizard if you never want to use wammu or gammu ever again and wish to hide information from authorities. 

Just cancel the phone wizard thing and spit in its general direction. It will break your configuration every time for no reason.

MAKE SURE WAMMU IS CLOSED

Into your terminal try this:
```
gammu identify
```

I don't know about your phone but for my phone all kinds of goodies came back and confirmed that my .gammurc is very nice to look at:
```
sneaky@ubuntu:~$ gammu identify
INFO: there is later stable Gammu (1.19.0 instead of 1.18.90) available!
Manufacturer         : Nokia
Model                : 6234 (RM-123)
Firmware             : 04.91 F (25-09-06)
Hardware             : 1004
IMEI                 : 3[censored by sneaky]6
Product code         : 0533334
```

So it works, and we know therefore that if wammu complains, it is just being stupid. You'd best make a backup of this file if you're going to let wammu anywhere near it lest wammu ruin it.

Now start wammu.
Click "Phone" (a menu at the top!) and then click "Connect"
It SHOULD connect OK.
For me it didn't and I had to open the settings dialog and then click OK to exit said dialog, THEN it worked.

I clicked "receive"->"messages" and waited for my messages to arrive.....
Well..... My messages show up .... Sadly I can't preview them in the messages list, but when I preview them they are ALMOST readable:
> Number: +64[aj's number was here]
Date: 2008-03-27 18:42:18
Location: 0
Folder: 4
Memory: ME
SMSC: o
State: Read
Name: thing seems missing....
í·ë*&#140;ä&#158;§íµ§í&#130;¼å±®ì½î·´ç²&#158;ç&#154;&#159;å´®é&#156;&#139;Ä&#128;è&#131;&#147;î¸³à¯&#148;àº»å´*âªºé°&#135;í&#135;&#131;î¬²æ£¾ç&#154;&#159;î&#156;*ë¼í´&#134; 
The message actually originally said "Something seems missing...." - something is for some reason munting the messages in the computer. Still, this is pretty good progress - I've proved to myself that it's possible for me to read my SMS from my computer, and that's a great deal more than I'd ever managed with Nokia PC Suite in Windows (and that tells you something)

So I'm very impressed with wammu altogether - I'm hoping that I can get my messages to display properly by adjusting the character set or some kind of weird protocol thing.
It should be noted that my problem retrieving the messages is not related to wammu itself, and is more a problem with either my phone (which seems to have dodgy firmware) or my gammu configuration. I'll conclude with evidence of this. One day I might try reflashing my phone as the vendor's authorized repairer consistently sends back phones in worse condition than what I send to be fixed :(

```
sneaky@ubuntu:~$ gammu getallsms
INFO: there is later stable Gammu (1.19.0 instead of 1.18.90) available!
Location 0, folder "Drafts", phone memory
SMS message
SMSC number          : ""
Sent                 : Fri 04 Apr 2008 22:51:16 NZST +0000
Name                 : "hat does that mean?"
Coding               : 8 bit
Remote number        : "+642[missing]7"
Status               : Read

8 bit SMS, cannot be displayed here

Location 0, folder "Drafts", phone memory
SMS message
SMSC number          : "n"
Sent                 : Tue 18 Mar 2008 07:02:06 NZST +0000
Name                 : "ne. Testing RAM. Every address will incorrectly return fffffff if written ffffffef. I've just watched forty million errors stack up in memtest86."
Coding               : 8 bit
Remote number        : "+642[censored]4"
Status               : Read

8 bit SMS, cannot be displayed here
```

I hope this helps someone. I know I covered a lot of stuff you didn't ask but imho it's better to have too much than too little?

---

### Post by VeVhLoS on 2008-04-29
Yes it helped me a lot.
wammu [auto]configuration is trash.
i edited ~/.gammurc and it connected right away.
i own a k800i erricsson, here is my ~/.gammurc :
```

[gammu]
port = 00:19:63:12:09:33
model = k800i
connection = blueat
synchronizetime = yes
logfile = gammulog
logformat = textall
use_locking = no
gammuloc = locfile
startinfo = yes
gammucoding = utf8
rsslevel = teststable
usephonedb = no
name=k800i

```
thanks a lot mate!

---

### Post by guillermolisi on 2008-05-16
It works for me too !

Very good job, man !

Thanks a lot !!

---

