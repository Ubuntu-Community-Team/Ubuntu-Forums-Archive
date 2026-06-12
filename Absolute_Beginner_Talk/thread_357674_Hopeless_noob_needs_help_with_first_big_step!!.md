---
title: "Hopeless noob needs help with first big step!!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by nooblar on 2007-02-09
Hello all, I stand here before you as a fresh convert straight from the dark side.  I just swaped out my old hard drive for a blank 120 gig one.  I had no problems with partitioning and installing on the blank hdd, it was fast and easy like a dream.

**The Problem:**However, now that I have my computer up and running with a fresh clean install of Ubuntu v6.10 I have hit my first snag, and need help with the next step.  I need to be able to get my internet connection working on my linux box so that I will be able to reach these forums from home instead of a friends computer ( :( ).  When my computer was running M$ OS, I did not have much of a problem setting up a connection, as it was pretty much plug and play.  

**The Facts:**   
[LIST]
[*]I am going straight from modem to computer, no router.
[*]I am using the onboard integrated 10/100 of my motherboard.
[*]I am using a Westell DSL modem, model number: B90-200010-04.
[*]I have a static ip adress, I went to System>Administration>Networking, enabled my wired connection, and entered all of my connection information, nothing happens.
[*]When I plug the ethernet cord in, the port does not light up as it did with M$ OS.
[*]When all is properly connected, the "Link" light on my DSL modem does not light up.
[/LIST]

I have big hopes and dreams for my first ever linux computer, but it looks like it will be babysteps on the way there :) .  Also, sorry for the long post, but I wanted to make sure I had all the bases covered. Thank you.

---

### Post by riven0 on 2007-02-09
Alright, first thing is to find out about your ethernet controller. So go to Applications >> Accessories >> Terminal and copy and paste:

> lspci

Post the results here.

Also, try this command. It may get your connection up and running:

> ifconfig

---

### Post by Happy_Man on 2007-02-09
Correct me if I'm wrong, but if you're using a Westell modem, is it safe to assume Verizon is your ISP? 

Also, I'm not sure what controls the light for the ethernet port, the motherboard or the OS. All I know is that on my setup the light is on and blinking, so I can't be much help there. 

Just some other general information, are you behing DHCP, or something else? You're gonna have to give us every last bit of technical info about your connection, to make it easier to diagnose your problem.

EDIT: ifconfig may work, try it!

---

### Post by nooblar on 2007-02-09
> Alright, first thing is to find out about your ethernet controller. So go to Applications >> Accessories >> Terminal and copy and paste: lspci
Post the results here.

This is what I got: 

```
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary
```
and then

> Also, try this command. It may get your connection up and running:  ifconfig

This command put some text in the terminal, which did not make a whole lot of sense to me, and did not start my connection.

> Correct me if I'm wrong, but if you're using a Westell modem, is it safe to assume Verizon is your ISP? 

My ISP is Illinois Consolidated. [http://www.consolidated.com/]("http://www.consolidated.com/")

> Just some other general information, are you behing DHCP, or something else? You're gonna have to give us every last bit of technical info about your connection, to make it easier to diagnose your problem.

Forgive my ignorance, but I am not exactly sure what DHCP is.  I'll post any information that you might need, but please do not forget that I am not extremely computer savvy.

Thank your for the lightning fast replies!  :)

---

### Post by Maestro23 on 2007-02-09
> Forgive my ignorance, but I am not exactly sure what DHCP is. I'll post any information that you might need, but please do not forget that I am not extremely computer savvy.


DHCP = Dynamic Host Configuration Protocol.  A set of rules used by a communications device such as a computer, router or networking adapter to allow the device to request and obtain an IP address from a server which has a list of addresses available for assignment.

---

### Post by mekkah on 2007-02-09
forget it

---

### Post by nooblar on 2007-02-10
> **mekkah said:**
> forget it

I'm glad that post didn't pertain to this thread because it had me EXTREMLY confused! LOL
I was starting to feel WAY over my head. Haha

---

### Post by tonyr1988 on 2007-02-10
This is probably a really retarded question, but bear with me:

Under your System -> Administration -> Networking, you said you enabled the connection. I'm assuming this means that the box "Enable this connection" is checked under properties. Under Edgy, that's not enough to get a connection. You see the box to the left of the connection name? You have to put a checkmark in *there*. Once you check the box, a box will pop up with a progress bar saying something like "Activing this connection."

I ask because that's something I didn't do. :D I was so used to using Dapper (I'm almost positive Dapper doesn't have the check box) that I didn't even think about it, and checking the box solved all my problems.

P.S. Make sure that your modem is turned on and you're plugging into it before you check the box.

---

### Post by fenian on 2007-02-10
In the network settings where you enabled wired connection were you sure                                          to select static ip from the configuration pull down menu?Did you set your DNS servers?

---

### Post by nooblar on 2007-02-10
> **tonyr1988 said:**
> This is probably a really retarded question, but bear with me:

Under your System -> Administration -> Networking, you said you enabled the connection. I'm assuming this means that the box "Enable this connection" is checked under properties. Under Edgy, that's not enough to get a connection. You see the box to the left of the connection name? You have to put a checkmark in *there*. Once you check the box, a box will pop up with a progress bar saying something like "Activing this connection."

I ask because that's something I didn't do. :D I was so used to using Dapper (I'm almost positive Dapper doesn't have the check box) that I didn't even think about it, and checking the box solved all my problems.

P.S. Make sure that your modem is turned on and you're plugging into it before you check the box.

Thanks to you, good sir, I am happy to report that I am posting this reply with a working internet connection on my brand new Linux box.  I must definitely tip my hat to the Ubuntu community, your responses were sincere and lightning fast.  Thank you guys!!

---

### Post by tonyr1988 on 2007-02-10
I'm glad it worked for you! If you have any other problems, make sure to ask, and help others when possible. (and if you get a chance, let a few of your friends know about Ubuntu :P)

---

