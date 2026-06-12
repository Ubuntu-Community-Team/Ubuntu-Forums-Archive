---
title: "Netgear WG311T wireless card not recognized"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-10-01
I just installed a Netgear WG311T wireless NIC in my ASUS P3B-F computer that used to run XP Pro. The card used to work with XP on the same computer. What should I do to make it work? :confused:  Please, keep in mind that I'm an absolute newbie with Linux, be as detailed as possible in your instructions as I'll follow them to the letter.
Thanks.

---

### Post by Malice007 on 2006-10-01
I use netgear on my laptop not the model you have but this is what got mine going. Download ndiswrapper and install it. 

Next you will want to install the windows drivers for it.

cd /media/cdrom0/drivers/

I used windows2000 drivers for mine.

next type

sudo ndiswrapper -i rt2500.inf <---your inf will have a dif name just look for the .inf file.

Next type sudo ndiswrapper -l you should now see the screen saying rt2500 driver present.hardware present.

To have this load on boot type:

sudo ndiswrapper -m
sudo vi /etc/network/interfaces
arrow the whole way to the bottom and start a new line byu pressing the letter O and add

iface wlan0 inet dhcp
auto wlan0
 press the ESC key then :wq to write and quit

wlan0 may be different on yours you can type iwconfig to find out.

But then type 

sudo ifup wlan0

If all goes well you should see it now on the computer by typing iwconfig

then you will need to go into SYSTEM/admin/networking

in there you should see your card click on it and then click on properties in there set up the name etc of the network that you are trying to connect  to. 

Also on there default gateway device should be selected as your wireless. at the bottom.

You can find all this info also at:

[Http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](Http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Now keep in mind I myself have only been using linux for about a month so I am new also and this worked for me just fine.

---

