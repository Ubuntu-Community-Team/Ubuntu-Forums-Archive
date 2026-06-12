---
title: "wifi is working on macbook pro mid 2010 with ubuntu Ubuntu 14.04.2 LTS"
date: 2015-03-17
forum: Apple Hardware Users
---

### Post by mohamed15 on 2015-03-17
This is to just share my experience with installed ubuntu on macbook pro mid 2010 (13'). After installing, everything works fine except wifi. I have Linksys AE1000 usb. So, I used it to update ubuntu. Second step is (while still attaching the Linksys usb), I search for "Additional drivers" on Ubuntu search icon and select (using Broadcom 802.11 .......), then apply changes and close.

Then, I removed the Linksys AE1000 usb and I am still do not have the wifi recognized, but I discovered that I simply have to put the computer into susbend or close the lid and open it again. Now, what happen is that the icon for wifi will be activated and you have to select the wifi network and enter the password. Future connection (I mean after you reboot ubuntu or coming back from mac osx booting), I used to select susbend and re-login again and then the wifi works.

Regards,
Mohamed

---

### Post by rican-linux on 2015-03-17
What is your lspci output?

---

### Post by mohamed15 on 2015-03-17
Dear rican-linux,

Sorry to disappoint you but I am completely newbee to ubuntu/linux world and I do not even understand the question.

Sorry again for this.

Best regards,
Mohamed

---

### Post by rican-linux on 2015-03-17
alright open your terminal and from the command line type lspci. Send us your results. You should be able to find your terminal clicking on the Ubuntu logo on the top left and type terminal.

---

### Post by mohamed15 on 2015-03-17
Many thanks rican-linux, here is the result:

00:00.0 Host bridge: NVIDIA Corporation MCP89 HOST Bridge (rev a1)
00:00.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: NVIDIA Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: NVIDIA Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: NVIDIA Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: NVIDIA Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: NVIDIA Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: NVIDIA Corporation MCP89 LPC Bridge (rev a2)
00:03.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.2 SMBus: NVIDIA Corporation MCP89 SMBus (rev a1)
00:03.3 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.4 Co-processor: NVIDIA Corporation MCP89 Co-Processor (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:06.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:06.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:08.0 Audio device: NVIDIA Corporation MCP89 High Definition Audio (rev a2)
00:0a.0 SATA controller: NVIDIA Corporation MCP89 SATA Controller (AHCI mode) (rev a2)
00:0b.0 RAM memory: NVIDIA Corporation Device 0d75 (rev a1)
00:0e.0 PCI bridge: NVIDIA Corporation Device 0d9a (rev a1)
00:15.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:16.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: NVIDIA Corporation MCP89 PCI Express Bridge (rev a1)
01:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
04:00.0 VGA compatible controller: NVIDIA Corporation MCP89 [GeForce 320M] (rev a2)

---

### Post by rican-linux on 2015-03-17
> **mohamed15 said:**
> Many thanks rican-linux, here is the result:

00:00.0 Host bridge: NVIDIA Corporation MCP89 HOST Bridge (rev a1)
00:00.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:01.0 RAM memory: NVIDIA Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: NVIDIA Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: NVIDIA Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: NVIDIA Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: NVIDIA Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: NVIDIA Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: NVIDIA Corporation MCP89 LPC Bridge (rev a2)
00:03.1 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.2 SMBus: NVIDIA Corporation MCP89 SMBus (rev a1)
00:03.3 RAM memory: NVIDIA Corporation MCP89 Memory Controller (rev a1)
00:03.4 Co-processor: NVIDIA Corporation MCP89 Co-Processor (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:06.0 USB controller: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:06.1 USB controller: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:08.0 Audio device: NVIDIA Corporation MCP89 High Definition Audio (rev a2)
00:0a.0 SATA controller: NVIDIA Corporation MCP89 SATA Controller (AHCI mode) (rev a2)
00:0b.0 RAM memory: NVIDIA Corporation Device 0d75 (rev a1)
00:0e.0 PCI bridge: NVIDIA Corporation Device 0d9a (rev a1)
00:15.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:16.0 PCI bridge: NVIDIA Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: NVIDIA Corporation MCP89 PCI Express Bridge (rev a1)
01:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
04:00.0 VGA compatible controller: NVIDIA Corporation MCP89 [GeForce 320M] (rev a2)

Let get you going. In the terminal enter these commands. 

```
sudo apt-get install firmware-b43-installer ***wait for the install to finish***
sudo modprobe -r b43
sudo modprobe b43
```

It should work now.

---

### Post by mohamed15 on 2015-03-17
Thanks rican-linux for your kind suggestions and kind support. I tested it but wifi does not start automatically when I reboot. Wifi starts after suspend or closing the lid.
Anyway, many thanks, I am happy that it works whatever the mean.

---

### Post by rican-linux on 2015-03-17
Great! Could you mark this as solved by adding this to the beginning of your thread title? [SOLVED]

---

### Post by mohamed15 on 2015-03-17
well, i will do as you said but kindly to note that this was the actual situation before I enter any code to terminal window. my aim of the thread is to inform people that wifi is already working by the naive tip i found. anyway, many thanks for your suggestion. mohamed

---

### Post by mohamed15 on 2015-03-17
the wifi is working

---

### Post by mohamed15 on 2015-03-17
sorry again rican-linux but how can i modify the orginal thread's title. what i found is only "Go advanced". regards, mohamed

---

### Post by rican-linux on 2015-03-18
Hmm most threads allow to update the title.

---

### Post by rican-linux on 2015-03-20
Ah here is how you mark it solved. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by rican-linux on 2015-03-20
which you figured out :)

---

### Post by mohamed15 on 2015-03-20
thanks rican-linux. Anyway, I was willing to know a method to edit the thread's title because I repeated wrongly the word ubuntu twice.

---

