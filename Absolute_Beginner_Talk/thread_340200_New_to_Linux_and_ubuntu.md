---
title: "New to Linux and ubuntu"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by photocatcher on 2007-01-16
First I would like to say that I thought the guide lines for posting at the message board were GREAT.  When someone has a question about something that they don't understand they will be reluctant to post if their questions when they see people have been greeted with put downs.  Now on to my question.

Last night I downloaded and installed Ubuntu 6.10.  It looks like a great OS but I am having a big problem using it to access the Internet.  I am using a Linksys Wireless-G broadband router.  I am using 128 bit encryption.  I did turn the encryption off last night hoping that by doing that I would be able to get online but no luck there.  I have read the post "Ubuntu Wireless Router" but I just can't figure it out.  I have tried to find the command line but it is nowhere to be found.  I have spent about six hours reading much of the information that is posted at the UBUNTU website but I still can't figure out how to get online with UBUNTU.

If anyone can help me out I would really appreciate it.

Lenny

---

### Post by jas0 on 2007-01-16
Here's a quick tip to get you started. The easiest and most natural way by war to connect to a wireless network is by using the network manager. In order to install it you'll have to do the following:

Open -- Applications -> Accesories -> Terminal

```
sudo apt-get install network-manager-gnome
sudo reboot
```

When your computer comes back up, you will notice that you have a net icon in your upper right corner. Click on it and select the network you want to connect to.

If for some reason your wireless network card is not installed by default, come back here and we'll guide you through installing your wireless network card. Just tell us which one you have. 

Welcome to the wonderful world of Ubuntu :)

PS: In future thread titles, be more specific on the kind of problem you're having. This way your thread won't get ignored by most helpful people.

---

### Post by lbrigman on 2007-01-16
First you need to determine if your wireless card is working and recognized by Ubuntu.
From a terminal windows.
ifconfig -a

should show you a list of all networking devices on your system even if they are not
configured.

My xubuntu vmplayer shows
eth1
lo
sit0

If you see one more you should not be concerned.

search the forums for wireless howto and then scroll through the list.
Here is one link that several people that was very good but there a ton of info there.
[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)

---

### Post by riven0 on 2007-01-16
> **photocatcher said:**
>  I have tried to find the command line but it is nowhere to be found.

For the command line: Applications >> Accessories >> Terminal


EDIT: Oh yeah, what is the make and model of the wireless card you're using?

---

### Post by bodhi.zazen on 2007-01-16
Hey, welcome to Ubuntu. Hope you stay a while.

Wireless can sometime be a hassle

See if anything here helps :

[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless)

---

### Post by photocatcher on 2007-01-16
> **jas0 said:**
> Here's a quick tip to get you started. The easiest and most natural way by war to connect to a wireless network is by using the network manager. In order to install it you'll have to do the following:

Open -- Applications -> Accesories -> Terminal

```
sudo apt-get install network-manager-gnome
sudo reboot
```

When your computer comes back up, you will notice that you have a net icon in your upper right corner. Click on it and select the network you want to connect to.

If for some reason your wireless network card is not installed by default, come back here and we'll guide you through installing your wireless network card. Just tell us which one you have. 

Welcome to the wonderful world of Ubuntu :)

PS: In future thread titles, be more specific on the kind of problem you're having. This way your thread won't get ignored by most helpful people.


JasO, Thanks for the heads up about being more specific about my question.  I did what you told me to do and I got this message "E: Couldn't find package network-manager-gnomesudo".

---

### Post by freebeer on 2007-01-16
> **photocatcher said:**
> JasO, Thanks for the heads up about being more specific about my question.  I did what you told me to do and I got this message "E: Couldn't find package network-manager-gnomesudo".

Looks like you didn't break the command into two separate ones.

```

sudo apt-get install network-manager-gnome

```

hit ENTER then type/copy

```

sudo reboot

```

From your error message, it looks like you tried to combine the two commands as one (the "sudo" on the second line is attached to the last of the first line "-gnomesudo")  If you catch what I mean.  :D

---

### Post by photocatcher on 2007-01-16
> **riven0 said:**
> For the command line: Applications >> Accessories >> Terminal


EDIT: Oh yeah, what is the make and model of the wireless card you're using?

RivenO I knew I would forget something when I posted this message.  I am using a Linksys Wireless-G Broadband router 2.4GHz 802.11g and on the other PC I have installed a Linksys Wireless-G PCI Adapter.  The two towers are only three apart so that means that there isn't a long distance for the signal to get interrupted.  I am now on an Acer Aspire using an Athlon 64 3800+processor with 1GBDDR Memory.  The other PC is an HP Pavilion which uses an AMD Athlon XP Processor.

---

### Post by ekka on 2007-01-16
Correct me if I am wrong, but if you need to install any packages by apt-get or any other means you need a working internet connection??

Coming to the problem, this is what I did to online on my Acer Aspire running Ubuntu 6.10

```
sudo lshw –C network
```

Will give all the network devices status including the drivers if any. If you find you wireless device listed and enabled.

Then see if ‘enable this connection’ is checked in system>administration>networking. And also enter your connection details

---

### Post by photocatcher on 2007-01-16
Freebeer I did as you wrote and after I typed in "sudo apt-get install network-manager-gnome" I got a prompt for my password.  So I put in my password and then "Sorry try again" came up so I put my password in again and the same thing happened.  Then on the screen it said "3 incorrect password attempts".  Then "Bash" my password and then  "command not found".

---

### Post by Mba7eth on 2007-01-17
Any how you must have entered the wronge pass :) 
when using sudo you must type password of ur account not the root pass 
one more thing 
try this
$sudo aptitude install wifi-radar   
this is an excellent wireless manger


cheers , 
        Mba7eth

---

### Post by freebeer on 2007-01-17
> **photocatcher said:**
> Freebeer I did as you wrote and after I typed in "sudo apt-get install network-manager-gnome" I got a prompt for my password.  So I put in my password and then "Sorry try again" came up so I put my password in again and the same thing happened.  Then on the screen it said "3 incorrect password attempts".  Then "Bash" my password and then  "command not found".

Looks like that solved your problem, anyway.  The command was accepted without error (the error that follows looks like a password input error as **Mba7eth** has pointed out).  Remember: Linux/Ubuntu is CaSE sensitive (and by extension, so is your password) so this might explain the password error.

---

### Post by stalkingwolf on 2007-01-17
I also am new to the Ubuntu distros.  I tried the "live CDs " on all of my machines (3 desktops, and 1 laptop) in all of them my wireless connections worked (with 3 clicks the last being connect ((for the first time))) "out of the box".  I have the same wireless router, and 3
different cards, one is a netgear pci, one a "noname" pcmcia card, and the last a netgear WG111 v2 USB wifi stick/adapter.  All worked with no problem.

this was a major factor in my choice to install xubuntu on the system that I gave as a gift
to a family member.  They are even more Linux Challenged than I am.:D

---

### Post by vbdanl on 2007-01-17
hi.  sorry to interrupt your thread, but i have a really stupid question.  i am wanting to ask a question, or start a thread, but can't find how to start one.  i have read the guidelines and faq, but don't see it..  at first it said i could not reply or post on the bottom of a page, but now it says i can.  if only i knew how..
thanks for your help..

---

### Post by bodhi.zazen on 2007-01-17
> **vbdanl said:**
> hi.  sorry to interrupt your thread, but i have a really stupid question.  i am wanting to ask a question, or start a thread, but can't find how to start one.  i have read the guidelines and faq, but don't see it..  at first it said i could not reply or post on the bottom of a page, but now it says i can.  if only i knew how..
thanks for your help..

You first log in, then go to the page you want to start a thread, 

[http://ubuntuforums.org/forumdisplay.php?&f=73&daysprune=30&order=asc&sort=postusername](http://ubuntuforums.org/forumdisplay.php?&f=73&daysprune=30&order=asc&sort=postusername)

then click "Make New Post" at the bottom of the page.

There is sometimes a delay once you start a thread ...

---

### Post by vbdanl on 2007-01-17
thanks.  i finally got it.  i think for some reason i had to wait before it would let me post, because now i get a "make new post" button on the top of the page that wasn't anywhere before..

---

### Post by vbdanl on 2007-01-18
Hi.  I am trying to install a D-Link DWL-122 wireless modem to my pc running ubuntu 6.10.  I have the icon in the top right, and ifconfig shows wlan0 with HWaddr all zeros. I am using a 2wire SBC DSL modem.  I know the network name and access point values that are listed on the gateway.2wire.net website, but I am not sure where I need to input these values or what options to update.  I was using a ethernet cable connection, and it worked fine.  I would like to use this wireless connection so I can put the pc in another room.  I am not sure if I need to update something in "Networking", "Network Tools", "Windows Wireless Drivers", or something else ?
Any help is greatly appreciated.

---

