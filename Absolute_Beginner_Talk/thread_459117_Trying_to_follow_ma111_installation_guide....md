---
title: "Trying to follow ma111 installation guide..."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Andrew Garn on 2007-05-30
Trying to follow ma111 guide

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

go to the point where I am editing /etc/network/interfaces

I need to get my adapter to connect to a network using WEP 64 bit encryption with a shared key that is 1234567891. The network name is SOTON.

My current idea of what to write is:

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON
wireless_enc on
wlan_ng_key0 1234567891
wlan_ng_authtype sharedkey

anyone know why this doesnt work? and why it doesnt allow me to save over the interfaces file?
Thanks

---

### Post by Andrew Garn on 2007-05-30
i can take the wireless key off for a while to test it

but i need to know why i cant save the interfaces file once i edit it

---

### Post by Inxsible on 2007-05-30
Are you using gksudo to open up the editor ?
 
You need to be the root in order to edit files.
 
```
gksudo gedit /etc/network/interfaces
```
 
or
 
```
sudo nano /etc/network/interfaces
```
 
Gedit and Nano are just editors. Gedit is GUI based and nano is CLI based. Gksudo is used to login as root in graphical apps and sudo is used for command line.
 
I had read a link somewhere, where it said it was always better to used gksudo for graphical apps and sudo for CLI apps.

---

### Post by Andrew Garn on 2007-05-30
hi thanks

i had just worked out how to save the file when I read this post

i did sudo chmod ugo+xwr interfaces and that worked

my only other question for this was:

can i represent the network key as numbers or does it have to be in xx:xx:xx:xx:xx format?

my settings are in first post.

thanks

---

### Post by Mnew2Linux on 2007-05-30
> **Inxsible said:**
> Are you using gksudo to open up the editor ?
 
You need to be the root in order to edit files.
 
```
gksudo gedit /etc/network/interfaces
```
 
or
 
```
sudo nano /etc/network/interfaces
```
 
Gedit and Nano are just editors. Gedit is GUI based and nano is CLI based. Gksudo is used to login as root in graphical apps and sudo is used for command line.
 
I had read a link somewhere, where it said it was always better to used gksudo for graphical apps and sudo for CLI apps.

Can't the user just enter: ```
sudo gedit /etc/network/interfaces
```  That's what I've tried and I've been able to edit the file...I'm having the same trouble with the MA111, I'm able to **lsmod | grep prism** it and it recognizes it but it doesn't recognize the wireless device in network management (I know windows terms but I can't think of what else its called at this moment :(  )

---

### Post by Inxsible on 2007-05-30
> **Mnew2Linux said:**
> Can't the user just enter: ```
sudo gedit /etc/network/interfaces
```  That's what I've tried and I've been able to edit the file...I'm having the same trouble with the MA111, I'm able to **lsmod | grep prism** it and it recognizes it but it doesn't recognize the wireless device in network management (I know windows terms but I can't think of what else its called at this moment :(  )

yes you can use ```
 sudo gedit /etc/network/interfaces
```

and it almost always works. But here is a little more info on potential pitfalls of doing it

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Andrew Garn on 2007-05-30
> **Mnew2Linux said:**
> Can't the user just enter: ```
sudo gedit /etc/network/interfaces
```  That's what I've tried and I've been able to edit the file...I'm having the same trouble with the MA111, I'm able to **lsmod | grep prism** it and it recognizes it but it doesn't recognize the wireless device in network management (I know windows terms but I can't think of what else its called at this moment :(  )

To make mine work all I did was:

lsmod | grep prism
sudo apt-cdrom add
sudo apt-get install linux-wlan-ng

then edited the interface file.

When I took the network key off my network the internet worked.

However I still need to know how to input the information:

Network key: 1234567891
Shared Key and WEP

in the ubuntu services file

---

### Post by Mnew2Linux on 2007-05-30
> **Inxsible said:**
> yes you can use ```
 sudo gedit /etc/network/interfaces
```

and it almost always works. But here is a little more info on potential pitfalls of doing it

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

editing /etc/network/interfaces is considered graphical?  I consider it command line because you're looking to change how the OS loads up the network configuration...right or wrong?

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> To make mine work all I did was:

lsmod | grep prism
sudo apt-cdrom add
sudo apt-get install linux-wlan-ng

then edited the interface file.

When I took the network key off my network the internet worked.

However I still need to know how to input the information:

Network key: 1234567891
Shared Key and WEP

in the ubuntu services file

Andrew, so right now you don't have WEP on your WIFI?  Why did you 

```
lsmod | grep prism
sudo apt-cdrom add
sudo apt-get install linux-wlan-ng

```

Isn't that if 7.04 didn't have the drivers on the install?  From reading the paperwork, it states only to have to do that for 5.10 and 6.06....I would've thought the MA111 drivers would've been updated for 7.04...

---

### Post by Inxsible on 2007-05-30
> **Mnew2Linux said:**
> editing /etc/network/interfaces is considered graphical?  I consider it command line because you're looking to change how the OS loads up the network configuration...right or wrong?

Editing the interfaces file is NOT graphical, but the application gedit, that you are using to edit the file, is a graphical app. So the gksudo is for gedit and not for the file that you are editing

if you use nano ( a CLI app to edit files) you can use sudo

---

### Post by Andrew Garn on 2007-05-30
For the installation I was just following instructions from here: [https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

I took off the WEP to test the adapter would work and connect with just

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON

in the interfaces file, when network WEP was off. It did

Now I am on my windows pc, trying to get the adapter to work with WEP Shared key back on.

my interface file now says:

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON
wireless_enc on
wlan_ng_keyfile /etc/network/wlan
wlan_ng_authtype shared key

with wlan being a text file with just the network key (1234567891) in it.

The internet does NOT work now.

any advice?

---

### Post by Mnew2Linux on 2007-05-30
> **Inxsible said:**
> Editing the interfaces file is NOT graphical, but the application gedit, that you are using to edit the file, is a graphical app. So the gksudo is for gedit and not for the file that you are editing

if you use nano ( a CLI app to edit files) you can use sudo

uh huh, thanks...I was totally off on the one...

---

### Post by Inxsible on 2007-05-30
> **Mnew2Linux said:**
> uh huh, thanks...I was totally off on the one...

No problem. I am glad to help :)

---

### Post by Andrew Garn on 2007-05-30
> **Inxsible said:**
> No problem. I am glad to help :)

Can you help me? :)

---

### Post by Inxsible on 2007-05-30
> **Andrew Garn said:**
> Can you help me? :)

:)

Would love to. But unfortunately, i don't use your router and I never made the changes that you are making to the interfaces file :(  Sorry.

Can someone else jump in here and help us out ?

---

### Post by Mnew2Linux on 2007-05-30
What about going the ndiswrapper route Andrew?  I really have no clue on that one as well, but I've been advised to take that route...can anyone help in how to install that?  I think we're already talking about this in another thread but the user that was helping us isn't on now...so he had said to see if ndiswrapper was in synaptics package manager...but I haven't been on the ubuntu side since this morning...

---

### Post by Andrew Garn on 2007-05-30
ndiswrapper is used for installing the usb drivers as far as i can understand

my usb adapter is installed it just needs configuring properly.

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> ndiswrapper is used for installing the usb drivers as far as i can understand

my usb adapter is installed it just needs configuring properly.

It is recognized by the OS but not installed...at least that's what I'm conjuring.  However, I was just thinking, you had said when you took WEP off it worked, right?

---

### Post by Andrew Garn on 2007-05-30
yes after I took WEP off on my router it worked, hence the adapter is installed.

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> yes after I took WEP off on my router it worked, hence the adapter is installed.

Yeah, exactly what I was just thinking there...that's freakin' weird...

---

### Post by Andrew Garn on 2007-05-30
well thats why I thought my setting were wrong

but I do not know how they should be, which is what I am asking anyone to help me with.

I opened a new thread asking:
[http://ubuntuforums.org/showthread.php?t=459254](http://ubuntuforums.org/showthread.php?t=459254)

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> well thats why I thought my setting were wrong

but I do not know how they should be, which is what I am asking anyone to help me with.

I opened a new thread asking:
[http://ubuntuforums.org/showthread.php?t=459254](http://ubuntuforums.org/showthread.php?t=459254)

Can you post your entire /etc/network/interfaces file, just so I can get a clue as to how it should look...take out the personal information like the WEP key and what not, but mine looks like this right now

 ```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed

auto eth0

```

I'm currently hardwired to my router and am on the net via that way but I cannot even get the adapter to work with the WEP off...In network settings I just have  Wired Connection (wlan0) and Wired Connection (eth0) and modem connection which isn't configured...

---

### Post by Andrew Garn on 2007-05-30
Here is my interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
ifaceath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless_enc on
wireless-essid SOTON
wireless-key s:1234567891

auto wlan0

```

---

### Post by Mnew2Linux on 2007-05-30
I don't have anything in Network Settings indicating that my wireless adapter is even recognized...though when I **lsmod | grep prism** it shows that it recognizes the adapter.  

```
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid Wireless

auto wlan0
```

This is my interfaces file, the last few lines.  I have turned off wireless enc and the howto for the MA111 said to not even put the wireless_enc and below lines in there...is there something I'm doing wrong or is unit not even on my system?

---

### Post by Mnew2Linux on 2007-05-30
Furthermore, this comes up when I try to alias wlan0 to the prism2_usb device
```

lee@lee-desktop:~$ alias wlan0 prism2_usb
bash: alias: wlan0: not found
bash: alias: prism2_usb: not found
lee@lee-desktop:~$

```

---

### Post by Andrew Garn on 2007-05-30
when i turned wireless encryption off on my adapter I only needed these three lines to make it connect

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid SOTON

auto wlan0

then i resetlaptop and it worked.

---

### Post by Andrew Garn on 2007-05-30
> **Mnew2Linux said:**
> Furthermore, this comes up when I try to alias wlan0 to the prism2_usb device
```

lee@lee-desktop:~$ alias wlan0 prism2_usb
bash: alias: wlan0: not found
bash: alias: prism2_usb: not found
lee@lee-desktop:~$

```

I get those errors too.

did you do these two lines?

sudo apt-cdrom add
sudo apt-get install linux-wlan-ng

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> I get those errors too.

did you do these two lines?

sudo apt-cdrom add
sudo apt-get install linux-wlan-ng

I'm guessing I'll need the 7.04 ROM I made right?

---

### Post by Andrew Garn on 2007-05-30
the ubuntu cd yes.

---

### Post by Mnew2Linux on 2007-05-30
> **Andrew Garn said:**
> the ubuntu cd yes.

Hey, thanks it worked WITHOUT WEP...is there a way that we can WEP it, using a 64 bit encryption...I have a network PW and I wonder if that has anything to do with it...

---

