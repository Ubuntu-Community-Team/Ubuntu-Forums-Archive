---
title: "Wifi mission impossible?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Bertfiddledither on 2007-05-05
I am absolutely new to Ubuntu.  I have an aging Dell 2600 laptop and a more recent HP Pavillion.  I have installed 6.10 on the Dell and 7.04 on the desktop.  I cannot find out how to get wifi working. With the Dell I have a Hercules PCMCIA card using a ralink rt2500 chipset for which the driver is supposed to be built in.  I have tried also my spare Olitec usb key which has a marvell chip I believe.  On the desktop I have a Thomson 120 usb with an orinoco chipset that runs a hermes driver. I have also tried a Belkin F5D7000 which according to Berlios is supported.  The problem is that not one, not a single one, of these wifi cards is recognised by Ubuntu.  All of them work under windows xp pro. The Hercules sits with a steady power on indicator,  but there are never any status lights at all on any of the others, indicating that the USB ports are not even powered. Frankly, if I cannot find  way of connecting to the internet I might as well uninstall linux now and keep taking the tranquilisers needed to live with MS XPs continual crashes.  But I would really like to give this a try, so any and every practical suggestion would be welcome (except ones requiring the use of any cables - this is simply not an option for me).:)

---

### Post by e_james on 2007-05-05
I am no linux expert (see signature) and I don't recognise your hardware, but from your current position there are 2 strategies I would try.

1. Try as many alternative linux live CDs / DVDs as I could find. Mandriva and Suse come to mind. The hardware detection and configuration routines can have useful suggestions and clues. They might even work.

2. Search these forums and others for references to my hardware in order of preference. If I can find that someone has encountered and solved the same problem, I can probably apply the same solution.

If those options don't work, the next possibility is to buy compatible hardware. See the hardware forum.

The last option I would try is to use a wired connection to a wireless adaptor. Netgear make one they call a games adaptor for connecting equipment like PS2 to the internet. (WG111, also known as a wireless ethernet bridge). No drivers are required apart from ethernet. The adaptor does all the work. I have 2 of these in use. They do the job nicely. A external power supply is required unfortunately. I suspect this is one of the things you want to avoid.

---

### Post by nickpaton on 2007-05-05
Welcome to Ubuntu and the forums Bert.

Ralink RT2500 - there are loads of posts about this so it's worth doing a search.
Also there are some drivers at [this site.]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")

Re the Belkin, again there are loads of posts about it, and according to [this]("http://ubuntuforums.org/showthread.php?t=388363") one, it uses the same Ralink RT2500 driver as above.

Bear in mind you've just embarked on the Ubuntu journey and initially it does take some time to get things going, but I would say that someone here has already had the same problem as you and we are only too willing to help.

It's worth using the search function for this very reason and if you need clarification, to give details of the post and the bits you're having problems with.

As a general rule, when you're initially setting up wireless, do it unencrypted and when you're happy to then apply encryption.

Good luck and get back with your progress.

---

### Post by Bertfiddledither on 2007-05-06
Thanks for these replies. I have been doing a bit of digging (although why for such a fundamental thing there is no help on the system or scripts already available to solve these issues I do not understand).  I have discovered that my Belkin card has passed on. It will not be missed, it was always twitchy.  My Thomson USB wifi runs with the Orinoco driver, which is according to my research, part of the kernel.  I have managed to find it listed in device manager, where it is shown as an unidentified USB wifi card, but I still have not got the first idea about how to get it activated.  On the laptop device manager list the Hercules card, identifies it as using the ralink 2500 driver, but once again I remain completely in the dark as to how to get it to actually do anything.

I have turned off the encryption on my router and told it to accept any connection.  As I live down a little used country lane with my nearest neighbour some 300 metres away this should not be an issue, but again it has made no difference.

I have followed a number of links, but to me, even though I used to use DOS command lines regularly in the early days of PCs, they seem to be written in gobbledeegook; it is assumed that the reader understands not only linux syntax and script conventions but also the function of the commands.  And I don't. And what is more I don't know how or where to find the answers to such basic questions like these.  Despite the fact that I have been reading around the linux forums and info sites for some weeks I still don't even know the first thing about the way in which it works.

Once again, any further contributions welcome.

---

### Post by nickpaton on 2007-05-06
> **Bertfiddledither said:**
>  My Thomson USB wifi runs with the Orinoco driver, which is according to my research, part of the kernel.  I have managed to find it listed in device manager, where it is shown as an unidentified USB wifi card, but I still have not got the first idea about how to get it activated.

First off am I right in thinking that you have a wireless ADSL modem router to which you are trying to connect the two PC's?

Right...!  Starting off with the desktop which has 7.10 installed (a memory prompt for me!).

We need to see what's been installed an what's recognised.

Open a terminal (Applications > Accessories > Terminal)
Plug in your Thompson usb device and type in:

```
lsusb
```  

(first letter is lower case L), and post the results back.

[This post]("http://ubuntuforums.org/showthread.php?t=320270") explains how to find and install the driver.

I've had a look at it and for someone starting out with Ubuntu it's somewhat involved, so I've PM'ed you about it.

Moving onto the laptop....

> **Bertfiddledither said:**
> On the laptop device manager list the Hercules card, identifies it as using the ralink 2500 driver, but once again I remain completely in the dark as to how to get it to actually do anything.

Have you tried following any of the posts to install the driver?  If not that's fine 
Can you type the following commands in a terminal and post the results back to me:

```
iwconfig
```

Gives details of the installed wireless card / chip.

```
lshw -C network
```

This lists all network hardware.

Think it's best to start from here and then I'll post again.

> **Bertfiddledither said:**
> I have turned off the encryption on my router and told it to accept any connection.  As I live down a little used country lane with my nearest neighbour some 300 metres away this should not be an issue, but again it has made no difference.

The reason for turning off encryption is to make sure that you've not made any typo errors when configuring it, rather than any potential security risks with near neighbours.  Once it's all working you can then apply encryption to your hearts content!

> **Bertfiddledither said:**
> I have followed a number of links, but to me, even though I used to use DOS command lines regularly in the early days of PCs, they seem to be written in gobbledeegook; it is assumed that the reader understands not only linux syntax and script conventions but also the function of the commands.  And I don't. And what is more I don't know how or where to find the answers to such basic questions like these.  Despite the fact that I have been reading around the linux forums and info sites for some weeks I still don't even know the first thing about the way in which it works.

Tell me about it - it's a big learning curve, but there are a number of really good articles which will help you on your way:

The Psychocats website[ here]("http://www.psychocats.net/ubuntu/")

And within Psychocats, [this]("http://psychocats.net/ubuntu/terminal") is is spot on.

For the teminal have a look at[ this]("http://linuxcommand.org/learning_the_shell.php")

Can you check you PM as well.

Good luck and await your reply.

---

