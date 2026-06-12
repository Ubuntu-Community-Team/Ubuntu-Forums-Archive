---
title: "What is the best way to get wireless?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-06
Any thoughts on the best way to get my Acer Aspire 1600 Notebook connecting to wireless networks? I borrowed somebodys D-Link DWL-G122 USB thing but found that it will require setting up. I've got my wireless router coming.

I want it to be easy to setup, and to connect to the network pre login in because I share a /home dir.

---

### Post by mahy on 2007-01-06
Everything has to be set up. Period. Just check it against some hw compatibility list. IMHO, the best option would be to buy something with PRISM chipset.

---

### Post by guysmiley25 on 2007-01-07
Thanks mahy.

Any suggestions on what I should get? I think I need a USB one, but it also looks like there is a slot on the side of my laptop?

Chears.

---

### Post by ardvark71 on 2007-01-07
> **guysmiley25 said:**
> Thanks mahy.

Any suggestions on what I should get? I think I need a USB one, but it also looks like there is a slot on the side of my laptop?

Chears.

PCMCIA slot?

There are some card suggestions here if it will help:

[http://ubuntuforums.org/archive/index.php/t-189940.html](http://ubuntuforums.org/archive/index.php/t-189940.html)

---

### Post by guysmiley25 on 2007-01-10
Ok so I have been messing around with the "D-Link DWL-G122 C1" that I borrowed and I cannot get it to work. So could somebody point me to a really good gudie that can help me out. Or tell me what USB wireless thing I should get and point me to a really good gudie for that.

I really would like to go with USB.

I'm using Dapper at the moment but after I do a hardware upgrade to my machines I'll be going to Edgy.

Anyone?

---

### Post by mespork on 2007-01-10
[http://www.newegg.com/Product/Product.asp?Item=N82E16833130111](http://www.newegg.com/Product/Product.asp?Item=N82E16833130111)

Works great, I have bought a couple of these. Work "out of the box". Great price too.

---

### Post by guysmiley25 on 2007-01-10
How big is it, it looks huge! I was hoping for something like the D-Link DWL-G122 because it looks just like a pen drive thing. Easy to carry around.

But will give up size for easiness of setting up. Are you running Dapper or Edgy?

---

### Post by mjm115 on 2007-01-10
I have a Linksys WUSB54G running flawlessly on Kubuntu Edgy.

I followed the instructions of [this]("http://www.ubuntuforums.org/showpost.php?p=1931882&postcount=6") thread.  I had no problems with it.

---

### Post by guysmiley25 on 2007-01-11
Chears. Just to make sure is it this one [here]("http://www.newegg.com/Product/Product.asp?Item=N82E16833124187")? I did a search on google to find that but this [here]("http://www.ascent.co.nz/productspecification.aspx?ItemID=8011372") is the one avaible to me.

Do you think that is differnet because it's WUSB54GC insted of WUSB54G?

Sounds like that ndiswrapper is used so you can use windows drivers with linux. Is this just in the case of wireless/usb devices?

---

### Post by Badgermc on 2007-01-12
I just got a eMachine eTower 667ir set up with Edgy and the wired network works great. It sees the wireless card but will not connect.

---

### Post by gummibaerchen on 2007-01-12
> **guysmiley25 said:**
>  "D-Link DWL-G122 C1" 

This is how you can do it.
You have to compile ndiswrapper yourself under Edgy.

```
Treiber und ndis.tar.gz auf den Desktop legen:

created the file my-wifi:
nano /etc/modprobe.d/my-wifi
ADD:
blacklist rt73usb
alias net-pf-10 off
alias ipv6 off
alias net-pf-10 ipv6 off
blacklist ipv6

insert ubuntu cd-rom if you have no internet access, otherwise continue with the second command
sudo apt-cdrom -m add
sudo aptitude install build-essential

i restarted at this point anyway

gnome-terminal:
cd Desktop
tar xfvz ndiswrapper-1.28rc2.tar.gz  (which you have downloaded)
cd ndiswrapper-1.28rc2/
sudo make distclean
sudo make uninstall
make
sudo make install

cd ..
sudo ndiswrapper -i Dr71WU.inf
sudo cp Dr71WU.sys /etc/ndiswrapper/dr71wu/
sudo rm /etc/ndiswrapper/dr71wu/07D1\:3C04.F.conf 

sudo nano /etc/modules
add ndiswrapper

sudo modprobe ndiswrapper

set everthing in /etc/network/interfaces
```

---

### Post by guysmiley25 on 2007-02-01
I have read that ndiswrapper cannot do WEP. Is this true? IF so I need a device that will allow me to use WEP.

---

### Post by muguwmp67 on 2007-02-01
It can't do WPA, but it can do WEP.  I think you can use another program  (wpasupplicant?) with ndiswrapper to do WPA, but I haven't tested it myself yet.

---

### Post by guysmiley25 on 2007-02-01
Yes thats what I meant sorry. WPA. So do I just use wpasupplicant, or do I use it with ndiswrapper?

---

### Post by guysmiley25 on 2007-02-02
Bump!

---

### Post by ahaslam on 2007-02-09
> **guysmiley25 said:**
> Yes thats what I meant sorry. WPA. So do I just use wpasupplicant, or do I use it with ndiswrapper?

For WPA you'll need both, but the wpa_supplicant version in both Dapper & Edgy isn't up to much IMO. Have you got your own card yet? If not, I found this link useful: [https://help.ubuntu.com/community/Wi...CardsSupported](https://help.ubuntu.com/community/Wi...CardsSupported)

Tony.

---

### Post by guysmiley25 on 2007-02-20
So  have setup a D-Link DWL-G122 C1 using this guide here:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview")

Its is now visible and appears to be working correctly.  However I still cannot get it to work!

I need to connect to the ap with wpa and I cannot figure out how to.

Thanks.

---

### Post by guysmiley25 on 2007-02-23
Bump

---

