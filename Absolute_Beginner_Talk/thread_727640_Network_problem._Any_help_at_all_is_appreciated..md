---
title: "Network problem. Any help at all is appreciated."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by pankirk on 2008-03-18
So it seems that in the last day my internet started freaking out on ubuntu. It would work but then it would stop working randomly. So I followed someones advice and they said to "reset" all of my network stuff, So I went ahead and searched for "NetworkManager" in synaptic and removed everything that seemed relevant to the problem I was having. So now guess what I have no internet. So is there a .deb package that I can download or something? I must have my wireless internet working for my school work and I cant Have it not working. Please help me get the wireless internet drivers back on my ubuntu installation! Thanks...

---

### Post by oedha on 2008-03-18
what is your wireless ?
you can see from terminal by tyoing :==> lspci
or
sudo lshw -short -C network

---

### Post by pankirk on 2008-03-18
it says
 [HTML]H/W path        Device     Class       Description
==================================================
/0/e/8          wmaster0   network     RT2561/RT61 802.11g PCI
[/HTML]

and then in the other code (lspci) it says:
[html]02:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
[/html]

if your wondering what my wireless card is, its a linksys wmp54g pci card...

---

### Post by oedha on 2008-03-18
maybe you can check :
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)
[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28ralink%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28ralink%29)
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28ralink%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28ralink%29)
:)

---

