---
title: "Dapper.Airport Extreme and WPA Sucess!Howto inside"
date: 2006-06-30
forum: Apple PPC Users
---

### Post by ivelasco on 2006-06-30
Hello

This is my first post in this forum,and I am doing it from my powerbook connected to a WPA-PSK based AP.
I have been trying many manuals from the net,with no succes until I follow this steps:

1) To load the dapper driver:

sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
modprobe bcm43xx

2) install wpa_supplicant
3) create a file /etc/wpa_supplicant.conf:

# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="YOUR-SSID"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk="PASSWORD"
}

4) Run this:

sudo wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant.conf -d   

*my iface is eth1,use yours

Check that this file exists(or create):

/etc/default/wpa_supplicant:

OPTIONS="-i eth1 -D wext -c /etc/wpa_supplicant.conf"


Thats all.I ve been working with this laptop at debian and this was one of the "black holes"(plus flash,java....)

I hope that somebody finds this useful

Bye

---

### Post by spy1325 on 2006-06-30
is this usable if i am connecting to an unencrypted wireless network? what do i need to change to disrgard the WPA setup?

---

### Post by ivelasco on 2006-06-30
To connect to an unencrypted wireless network,you only need to load the driver.after you must set up the interface ip address manually or by DHCP.There are many nice apps that help you to do this.(network-admin,nm-applet etc)

---

