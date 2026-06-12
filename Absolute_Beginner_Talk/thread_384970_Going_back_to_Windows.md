---
title: "Going back to Windows"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-03-15
I hate to say this, I've been really happy with ubuntu to date, but the problems of getting my new PC running are making me think seriously about using Vista

I've got an Asus M2NPV-VM motherboard, 1G of DDR2 memory, an Athlon processor and a 160G SATA drive - a nice piece of kit. Initially I couldn't instal 6.06 - I kept getting an installation bug message. This was eventually tracked down to faulty RAM. With new RAM modules the second installation went very smoothly, but I've now got a rather sick Linux PC.

There are two basic problems. First, I have to deactivate, then activate my wireless connection (System>Adminstartion>Networking) everytime I switch my PC on. This gets me a nice strong wireless signal, but for reasons I can't fathom it doesn't always allow me to connect to the Internet, i.e. Firefox sometimes will report 'server not found'. I've posted a couple of threads about this, but so far nobody has been able to help.

Secondly, just after the kernel is booted, I get the message "MP-BIOS Bug 8254 timer not connected to 10-APIC". I've notice that the time setting of my PC is not working - I set the correct time, but the time is wrong when I switch on again - maybe that's relevant. I've done a Google on this particular error, and it sound pretty fundamental, and a bit dire.

I just love working with Linux - the file system is particularly clean and elegant, but work-wise I'm absolutely dependent on a functioning PC. Vista sounds way over the top, and Microsoft has exercised a baleful influence on personal computing, but, if I'm going to start sleeping at night , I reckon I'm going to have to go back to Windows. At least there are people out there who will take my money and get my machine working when it goes wrong.

As a last-fix attempt I'm going to ask the people who built my machine to try a bios update, but if that doesn't work, I'm afraid that really is it with Linux.

Any other ideas, anybody?

Roger D

---

### Post by MikeSz on 2007-03-15
Hi There, 

sorry im new to Linux so I dont know about your first problem, however the second problem sounds like it could be your CMOS battery.  Does the system keep time in the BIOS whenever you set it?  A good way to check would be to set the time, pause the screen just after the power on self test (just before it starts to boot into linux) by pressing the pause key and then leave it for a few minutes, if you reset your system then go back into BIOS it should have kept the time properly if your BIOS and CMOS batter are working.  If it doesnt, you know you have a problem with either the motherboard or your battery which would be there even if you went into windows.  

Hope that helps.

---

### Post by buuntuu! on 2007-03-15
can't give advice on your problems, but if you can't solve them, why window$ instead of another linux-flavour??

---

### Post by hyper_ch on 2007-03-15
If this is a general problem with your wifi card then there's no real solution except that you might get one which is better supported by linux...

But then, you have already made up your mind on going back to Windows. That is your choice and you should do what you think is best for you.

I however prefer to be in control of my computer... why should I trust M$ if they don't trust me? [Trusted Computing]("http://www.lafkon.net/tc/")

---

### Post by ComplexNumber on 2007-03-15
**RogerD**
iadvise you strongly against vista. most hardware and applications are not yet supported on it. i think you will find that much more works on ubuntu compared with vista.

---

### Post by Kobalt on 2007-03-15
> **RogerD said:**
> 
Secondly, just after the kernel is booted, I get the message "MP-BIOS Bug 8254 timer not connected to 10-APIC". I've notice that the time setting of my PC is not working...
Did you check the clock settings in your BIOS, are they correct ? 
Concerning your wifi problem, can you please post the result of this command line (but don't forget to remove you SSID and WEP/WPA key) : 
```
cat /etc/network/interfaces
```
Finally, just like ComplexNumber, I strongly advise you not to install Vista, it's still very buggy... If you really want to get back to Windows, then why not installing XP SP2 aside of Ubuntu, dual-booting, so that you can still enjoy and hopefully improve your Linux on your free time and eventually work on Windows, if you wish to... 
(even though having fun on Linux and working on Windows is a weird sentence for me to write I must say...)

---

### Post by 23meg on 2007-03-15
> 
Secondly, just after the kernel is booted, I get the message "MP-BIOS Bug 8254 timer not connected to 10-APIC". I've notice that the time setting of my PC is not working - I set the correct time, but the time is wrong when I switch on again - maybe that's relevant. I've done a Google on this particular error, and it sound pretty fundamental, and a bit dire.


Try booting with the "noapic" kernel option. Do a forum search and you'll find instructions on how to do it.

---

### Post by flossgeek on 2007-03-15
bye:)

---

### Post by zeifertstc on 2007-03-15
> **ComplexNumber said:**
> **RogerD**
iadvise you strongly against vista. most hardware and applications are not yet supported on it. i think you will find that much more works on ubuntu compared with vista.

Funniest thing about this is that I agree with the last little bit of this post even though I've recently had some horrific problems with the 2.6.17.11 kernel and certain portions of my hardware. It wasn't at all cool but I'd never go for Vista as it is. Ubuntu does have many more working apps for both 32 and 64 bit than vista does. If you want to do any gaming with your pc ever, you'll be screwed with Vista. It seems as if Microsoft was rushed into putting Vista out on the market that they couldn't decide on one or two versions to market so they put out three in my area alone.

And, if you want all that Vista has to offer, btw, it'll cost you over $600 as even the retail outlet versions of Vista Ultimate are not full-featured editions. Honestly, Vista is prettier than it is functional. It'll eat system resources 50% more than XP and even XP ate resources on my machines by about 150% more than Kubuntu Dapper. And, trust me, Kubuntu's desktop environment/window manager is a bit bloated. (And I think I stated that as a bit of a supreme understatement.) GNOME is better than KDE for lesser system resource eating and Fluxbox is even better if you want the speediest system you could possibly get limited only by your hardware.

Linux does have its frustrations but it is definitely worth it to stick it out and work out your bugs. Trust me, after doing a bit more work with your current situation you will most likely discover what the whole problem is and be happy with Linux once more (without killing your wallet/bank account and you won't have to take a third mortgage on your house to purchase the latest and greatest). <i>Wow, did I say not to go out and get the latest and greatest?</i> Yes, I said it. Though I will tell you that it hasn't cost me a dime more than the cost of ISP services to get the latest and greatest of Linux. Though, with as many distros as I have tried, I'm sure that the ISP is just lovin' me as a customer these days. Anyways, I hope you stick with Linux and try it to the very end. I'd not like to see MicroSucks getting more revenue that they don't really need. Billy Gates has enough money too. So, keep some of your own, if you must have windows for something at least make it XP or so. I have it on another partition of my drive just because I need Windows in order to print to my Lexmark X2350. If it wasn't for that paperweight of a printer (by linux standards) I'd not have Windows anymore.

---

### Post by freebird54 on 2007-03-15
RogerD - did you ever try to blacklist ipv6 to resolve your FireFox problem?  Or putting about:config in Firefox's address bar, filtering network, and enabling the option
network.dns.disableipv6   by double-clicking it?

Here's a quicky for the blacklist too, if you haven't tried it...

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add

```
blacklist ipv6
```

save, exit, reboot...

Just a passing thought before doing anything drastic :D

BTW - run XP Pro if you must go back - it mostly works (with a little help from McAfee et al)

---

### Post by excessiveidling on 2007-03-15
I have the same motherboard and almost overall same system stats that you have stated.  I too did have the bios error you had listed however on a whim I did a bios update.  (I DID have version 303 bios installed on my asus m2npv-vm, now I have 0705) .  While I wouldn't normally recommend a bios update if you're computer is working fine and bios updates always scared me (last computer was fried due to power going out right as I started to flash) it seemed to fix the problem for me....perhaps it will for you?

E|

p.s. DON'T use vista....its such a memory/resource hog...if you really need to go back to windows, use xp, atleast wait till M$ is on its service pack 2 with vista....then it MIGHT work well.

---

### Post by anaconda on 2007-03-15
Have you tried ubuntu 7.04 (feisty) it has better support for wifi.. among other things..

---

### Post by tommcd on 2007-03-15
You mentioned that you couldn't install ubuntu 6.06. Did you try edgy 6.10? With a newer motherboard like that you may have better luck with edgy, or possibly fiesty when it comes out in another month. Also try noapic as was suggested.
As others said, try dual booting winXP and ubuntu. That way you can use XP while you get your linux problems worked out. You might also try zenwalk linux [http://zenwalk.org/](http://zenwalk.org/) It's only a 400mb download, installs in about 30 minutes, and uses 2.6.20 kernel, which may have better support for your motherboard.

---

### Post by elijakill on 2007-03-15
test your linux cabailities using a live CD
see that your hardware get recognized and then go for the full monty

---

### Post by RogerD on 2007-03-15
Hi everybody

Thanks for your encouraging replies. I've had a very helpful talk to the guys who sold me the wireless adaptor - there's a well-known instabliity problem, and it looks as though, between us, we'll get to the bottom of it. They also advise me that the 8254 timer not connected message isn't critical - just a warning from the kernel - and my drifting clock problems are, possibly, just down to a bit of dirt on the battery. So, for the time being, I'm going to 'hung on in there'  with LInux

Regards

Roger D

---

### Post by xyz on 2007-03-15
...sooo close  [to going back to Redmond]...yet soo far...
Glad to have you back!

---

### Post by jrandolph on 2007-03-15
I am new to Linux -- but I definatley agree with everyone when they say dont go with Vista -- All they did was made it look pretty I personally dont find any of all that new GUI useful -- although pretty but relatively useless

---

### Post by lastredoubt on 2007-03-15
I think it was mentioned briefly here already, but if you are having woes with ubuntu at least try another ditro of linux befor moving back to vista -- that is, if you consider going back again :P

openSuSe or Mandriva might help you out.  I personally love ubuntu the best and have had little trouble with it, but it doesn't mean its perfect.  Yet.

---

### Post by tommcd on 2007-03-15
See this article:
[http://www.phoronix.com/scan.php?page=article&item=625&num=1](http://www.phoronix.com/scan.php?page=article&item=625&num=1)
This motherboard uses the same chipset as yours. From the last page:
"The NF-M2 nView had functioned flawlessly with x86_64 Ubuntu 6.10 Feisty Fawn. The MythTV derivative MythDora 3.2 had also operated without fault on the Abit NF-M2 nView motherboard. With the exception of the x86_64 Fedora issue with the nForce 430 Chipset, the Abit NF-M2 nView motherboard had run great under Fedora Core, MythDora, and Ubuntu Linux."
Try edgy. If that don't work wait until fiesty. You may want to ask on the phoronix forums:
[http://www.phoronix.net/forums/](http://www.phoronix.net/forums/)
Forum admin Michael is very knowledgeable about new hardware and linux, and he answers many posts on the forums.

---

### Post by jem7v on 2007-03-15
The only thing I'd point out is that it would be a lot cheaper to buy a new, better supported wireless card and a new CMOS battery than it would be to purchase Vista... and then possibly have to do the same thing anyway.

---

### Post by trippinnik on 2007-03-15
Wow, you've gotten a ton of responses!  That's been one of the best parts of using Ubuntu.  The forums are full of genuinely kind and helpful people (I have seen other places where you get slammed for asking stupid questions etc).  

Anyway what is the model number of your wireless card?  Are you using the kind of clunky network configuration in Ubuntu where you click the 'Acitivate' button?  

I had to go through quite a bit to get my wireless card running well, but it's helped to use the Network Manager Applet.  It'll switch the connection from wired to wireless, deal with WEP, and allow you to switch access points.  

Let us know how it goes.

---

### Post by Zzl1xndd on 2007-03-15
Glad to see your hanging in there. Also I gotta agree Vista is not the way to go at all if you do end up going back get XP.

---

