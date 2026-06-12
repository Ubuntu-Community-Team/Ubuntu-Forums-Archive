---
title: "Conflicting Information"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-31
I'm trying to set up a wireless Internet connection for Kubuntu 7.04. The network is enabled as the wireless USB adapter lights up suggesting that it recognizes the router. However, I can't make a connection using Konqueror. I've used Kubuntu's GUI to set the various parameters and some may be set incorrectly. For example, iwconfig gives me:


[INDENT][INDENT]tom@emachine:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  Nickname:"unknown"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:0F:8E:F1
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=94/94  Signal level=-38 dBm  Noise level=-154 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:63   Missed beacon:
[/INDENT][/INDENT]

It indicates that I have an invalid nwid. According to Ubuntu's WiFiTroubleshooting guide, this means that I have the wrong EESID. The invalid crypt:0 means that I have mismatching authentification method/key. However, the values I entered are what's in the router's setup. Something's wrong here. 

I noticed that when I entered the settings in the setup screen, waited for the program to reconfigure with these new settings, exited and then reentered the setup screen, the values I had entered for the key and the default Gateway were gone. That doesn't seem right, but I don't know. 

If anyone could shed some light on this, I'd sure appreciate it.

Thank you!

---

### Post by chili555 on 2007-05-31
The key part here is not: invalid nwid, but rather: Rx invalid nwid:0 which means, as far as I know, your wireless adapter has received 0 invalid nwid packets. This information is trivial. Every well-running adapter will have this, including mine.

The best way to validate what the correct settings are is to do:```
sudo iwlist wlan0 scan
```It may take a few tries. Assuming you have WEP encryption, it should easily connect with:```
sudo iwconfig wlan0 essid linksys
sudo iwconfig wlan0 key 01234abcde
sudo dhclient wlan0
```Remember, in essid's, linksys is not Linksys is not LINKSYS.

---

### Post by tlinux on 2007-06-01
Thanks very much for your advice on getting Kubuntu connected wirelessly to the Internet. I executed the four commands you recommended and then logged right on. I updated the deb packages and instilled a mail program, etc. It works perfectly and I'm very gratefully to you for this information.

I have one remaining problem. When I log off and then log on, I can't connect to the Internet. I have to go through the four commands you gave me and then I can log on. I suspect the my key isn't being saved, but I really don't know. Do you have a recommendation for this?

Thanks again!

tlinux

---

### Post by chili555 on 2007-06-02
I suggest you *sudo gedit /etc/network/interfaces* to make the relevant wireless interface look like:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key 0123456789abcdef
```Save and close gedit and it should start and connect automatically.

---

### Post by tlinux on 2007-06-02
The /etc/network/interfaces file already contains:

[INDENT][INDENT]auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key 0123456789abcdef[/INDENT][/INDENT]

except there is a **s:** in front of the key as can be seen in this pastebin:

[http://pastebin.ca/531384](http://pastebin.ca/531384)

Should I remove the **s:** or what?

Also, I don't have gedit so I tried to install it. However, the installation failed with both Adept and Synaptic. Don't know why.

---

### Post by chili555 on 2007-06-02
The **s:** indicates your key is ASCII. Unusual, but not unheard of. You can tell if your key is actually ASCII or hex because:
# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters 

Count the characters and you will know if it is ASCII or hex. If it is hex, you should remove the **s:**.> Also, I don't have geditSorry, I missed that you are using Kubuntu. You should use *kate.*

---

### Post by tlinux on 2007-06-02
The key has 26 characters so it's a hex key. I removed the **s:**,rebooted the computer and it now works like it should. I believe all the problems are solved.

I really appreciate all the help you've given me. I know I couldn't have solved this problem myself. It appears to me that very few people have as much knowledge of the Internet connection process as you do.

Thanks again!

---

### Post by tlinux on 2007-06-03
For some unknown reason, when I previously tried to post this message, it failed to show up. In any event, the system no longer recognizes wlan0. Now it's back to to the drawing board.

---

### Post by chili555 on 2007-06-03
Let's take a look at the output of these commands:```
iwconfig
sudo lshw -C network
```Thanks.

---

### Post by tlinux on 2007-06-03
This morning I logged on to Kubuntu and it recognized **wlan0** and connected to the Internet. This is baffling to me. Yesterday when I ran

[INDENT][INDENT]sudo iwconfig wlan0 essid linksys
[/INDENT][/INDENT]
I got an error message telling me there was no wlan0. Kubuntu has a GUI option in its Start menu. Yesterday I went to:

[INDENT][INDENT]Start->System Settings->Network & Configuration->Nework Settings[/INDENT][/INDENT]

 
Only the ethernet was enabled. No **wlan0** was shown. Today it shows that both **eth0** and **wlan0** are recognized and enabled. Now everything is working correctly.

My ignorance is proving to be very frustrating. I just don't know what's going on.

Thanks again!!

---

