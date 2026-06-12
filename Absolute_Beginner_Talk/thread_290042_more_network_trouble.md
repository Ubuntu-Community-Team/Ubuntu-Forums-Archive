---
title: "more network trouble"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by ducamie on 2006-10-31
Hey fellas, I installed ubuntu 610 yesterday, it's awesome, but I can't get the internet working on my network. My setup is a pc downstairs with XP that i'm on now, and the pc in my room, which had 98se and now has ubuntu conected to the internet through the XP pc..

I cannot seem to work it out, ive been trying all day, but i'm just treading water. I have done what it says on wikipedia:

```

 How to activate/deactivate network connections

    * Read #General Notes
    * System -> Administration -> Networking
    * Network settings 

Connections Tab -> Select "Ethernet connection" -> Activate/Deactivate

[edit]
How to configure network connections

    * Read #General Notes
    * System -> Administration -> Networking
    * Network settings 

Connections Tab -> Select "Ethernet connection" -> Properties
Connection -> Enable this connection (Checked)
Connection Settings -> Configuration: Select "DHCP/Static IP address"
```

The Xp machine seems to be sending but not reciving and the ubuntu manchine doesnt seem to be doing either?
 
Can anyone tell me what I am doing wrong. ](*,)

Thanks :D

---

### Post by pdub on 2006-10-31
Is there a DHCP server on the network so that your Ubuntu computer can get an IP address?

Check to see if your Ubuntu system has an IP address by opening a terminal and typing:

**ifconfig**

Likely it's eth0

If you have an IP address can you ping your XP machine?

---

### Post by ducamie on 2006-10-31
> **pdub said:**
> Is there a DHCP server on the network so that your Ubuntu computer can get an IP address?

Check to see if your Ubuntu system has an IP address by opening a terminal and typing:

**ifconfig**

Likely it's eth0

If you have an IP address can you ping your XP machine?

THANKYOU for your speedy reply.

I dont think i'm connected, my ip on the ubuntu machine was 127.0.0.1. and nothing happened when I pinged my XP machine.

---

### Post by raqball on 2006-10-31
> **ducamie said:**
> My setup is a pc downstairs with XP that i'm on now, and the pc in my room

Are you running wireless then?

eth1 is probably wireless.

---

### Post by ducamie on 2006-10-31
no its not wireless.

i'm actaully thinking that ubuntu may not have detected the network card.

where do i start if this is the case?

---

### Post by raqball on 2006-10-31
What ethernet card are you using?

---

### Post by pdub on 2006-10-31
So you did not see an additional interface when you did the ifconfig?

What type of network adapter is in the computer? Make Model, etc.

---

### Post by ducamie on 2006-10-31
Gawd sorry. That took way too long, I had to open up the tower and peak in with a mirror.

Its a Realtek RTL8139D. :)

---

### Post by ducamie on 2006-10-31
The card isnt compatible with linux apparenlty. 

After an hours research, i've discovered the program ndiswrapper that might be able to use a windows driver and make it work with ubuntu.

But, I have no idea how to use it. The program ndiswrapper is just a load of txt files and things. Can anyone help? ](*,)

---

### Post by RanDinCarolina on 2006-10-31
I think that card is compatible because I have a Realtek 8110 chip on my MSI 865PE Neo2-P and it uses the 8139 driver module. Check the forums a little more closely and I think you'll find what you need......

---

### Post by David Corrales on 2006-10-31
I found this link to an Ndiswrapper howto. Hope it helps :)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by pdub on 2006-10-31
I believe the 8139 is fully supported by Edgy

Type 

**sudo modprobe 8139too**

It should just return you to the prompt.

Then type 

**lsmod | grep 8139too**

To see if the driver loaded

---

### Post by Aranel on 2006-10-31
For the record, this shows up in lspci for me:

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

It worked perfectly during the Ubuntu installation process (I normally use wireless, but the point is, it worked). So I don't think it's a problem with the hardware or Linux's ability to detect it.

...Just my two cents. I have very little experience in that area, so I don't think I can help you very effectively. :-k

---

### Post by ducamie on 2006-11-01
thankyou very much you guys are awesome.

i'll try and get this sorted today.

thankyou

---

