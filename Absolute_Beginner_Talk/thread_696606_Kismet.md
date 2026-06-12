---
title: "Kismet"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-02-14
Finally got it going one problem tho i cant seem to view essid mac address are bssid

&#9484;&#9472;Network List&#9472;&#9472;(Autofit)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;&#9472;Info&#9472;&#9472;&#9472;&#9488;
&#9474;     Name                      T W Ch  Packts Flags IP Range         Size                                        &#9474;&#9474; Ntwrks &#9474;
&#9474;   . WANADOO-DB30              A O 001    515       0.0.0.0            0B                                        &#9474;&#9474;      3 &#9474;
&#9474;   . BTHomeHub-C201            A Y 001    436       0.0.0.0            3k                                        &#9474;&#9474; Pckets &#9474;
&#9474;     StudyWiFi                 A O 011      1       0.0.0.0            0B  

is there anyway of doing this?

---

### Post by wieman01 on 2008-02-14
You probably need to wait until one of the client PCs establishes a connection with the router. Only then is the SSID broadcast.

---

### Post by coubury on 2008-02-14
Got press i on the screen for more info

mate any chance you could help me with this 

i need to start airodump so it can start collecting data
now this is what iv read to put in 
airodump-ng wlan0 -w /home/coubury/Documents/glen123 1 1

wlan0 being my wireless card
-w tells airodump to write the file to
1 is channel my ap is on
1 tells airodump to collect iv's

when i enter that in at a terminal nothing happens :confused:

---

### Post by wieman01 on 2008-02-14
Hey, you can follow my tutorial ("How secure is WEP?") for more information. It contains clear instructions, but please read the disclaimer first.

---

### Post by coubury on 2008-02-14
cheers mate got it going :)

---

### Post by coubury on 2008-02-14
Its running very slow

 CH  1 ][ Elapsed: 8 mins ][ 2008-02-14 13:57 
                                                                                                                            
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                                                                            
 00:18:F6:5F:6D:57   -1   0      466        0    0   1  48  WEP  WEP         BTHomeHub-C201                                
                                                                                                                            
 BSSID              STATION            PWR  Lost  Packets  Probes  

how come its not showing a section for IVS?

---

### Post by wieman01 on 2008-02-14
What wireless adapter have you got and did you patch the driver?

---

### Post by coubury on 2008-02-14
edimax 7128g pci card 

ralink chipset rt2500

nah it dosent need patched

well at least i dont think so

---

### Post by wieman01 on 2008-02-14
> **coubury said:**
> edimax 7128g pci card 

ralink chipset rt2500

nah it dosent need patched

well at least i dont think so
It definitely needs patching. I have a rt2570 and installed the patched version of the driver using the source posted on Aircrack's website. 

No patch = no packet reinjection.

---

### Post by coubury on 2008-02-14
Its actually the rt61

i was on the serial monkeys forum there and they dont have a patch in the rt61 sub forum

---

### Post by wieman01 on 2008-02-14
> **coubury said:**
> Its actually the rt61

i was on the serial monkeys forum there and they dont have a patch in the rt61 sub forum
Mmm... Do you find anything useful on Aircrack's website? Don't have access to it right now, can't help you.

---

### Post by coubury on 2008-02-14
aye its supported for airplay

do you think the might increase? looks like i could be here all night

---

### Post by wieman01 on 2008-02-14
"Data" is the section for IVs. It's there.

You can increase the speed only by replaying packets for instance. Do you do it while capturing packets?

---

### Post by coubury on 2008-02-14
aye kismet is running aswell

its captured 9500 packets

whats the purpose of packets?

---

### Post by wieman01 on 2008-02-14
> **coubury said:**
> aye kismet is running aswell

its captured 9500 packets

whats the purpose of packets?
The packets are data exchange between the client and the AP. It's basically traffic. You could read some stuff on Aircrack's website, they do a fantastic job explaining every little detail.

---

