---
title: "Another Newbie bites the networking dust with Ubuntu !!!"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by xini on 2007-12-12
It's enough to make a grown man cry, No network or internet.  I have tried every configuration, roaming, dhcp, static. I have tried every piece of advice I have been given and can find on the forums but still no life. Boot off the LiveCD and back into Windows there pops up the little light on the router.... life again.  Throw a Mac at my router.... it lights up and there is also life.  Sadly with Ubuntu the little light just remains off.

Everything else in Ubuntu works fine.  All my hardware is recognised, including the Network Card, but will Ubuntu talk to my router?  NO *cries*

I'm disapointed but want to thank the people in the forums who tried to help me.  If anyone has ever encountered a similar problem then I can maybe learn from your experience.  

In the meantime i'm afraid it's back to plan B ....... XP (screams).

---

### Post by PartisanEntity on 2007-12-12
What kind of a router do you have?

---

### Post by meborc on 2007-12-12
what connection do you have? adsl? does your connection in windows use login and password?

---

### Post by xini on 2007-12-12
Thanks guys, if it is of any use my router is a  DL-504.  It is configured to do all the dialing in for me via PPOE, essentially it is an always on connection.  It can assign addresses no problem to XP and Mac.  I can also assign a manual address if I so wish to any computer, I have the settings required for that and can do that no problem again in xp and mac.   All in all the router appears to do it's work prefectly.

My Lan card is a rtl8139, Ubuntu throws this in no problem and i can see it installed in the system hardware.

Essentially I just cannot get the two to talk to one another.  I'm a total newbie to Ubuntu and since I cannot commit to an install I have to run from the live CD until I can make sure I can configure it to work correctly.  Then the plan was to dump XP for good.

If you have any idea's at all, then throw them at me :)

---

### Post by bumanie on 2007-12-12
The most likely reason for your internet not working is probably an ipv6 conflict. Many using gutsy have had this problem.
In terminal type 
gksudo gedit /etc/modprobe.d/blacklist
At the end of the gedit list type
blacklist ipv6
Reboot and your internet should work.
Alternatively follow old pink's thread regarding how to disable ipv6 in firefox [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
Could also try a firmware upgrade to your modem if you feel confident to tackle this.

---

### Post by zabien1970 on 2007-12-12
bumanie:  Since he's not installing and running the live-cd would this work when he reboots?

---

### Post by swoll1980 on 2007-12-12
after you swithed it to dhcp did you add a check to the ticker that says enable this conection it's on the first screen on the network manager on the left side of the device options "eth0 name of your device there will be a ticker"

---

### Post by swoll1980 on 2007-12-12
that wont work

---

### Post by bumanie on 2007-12-12
> **zabien1970 said:**
> bumanie:  Since he's not installing and running the live-cd would this work when he reboots?

I may have misread the post. I thought ubuntu was already installed and that he was trying the live cd as some sort of fix. Before I installed gutsy, I managed to disable ipv6 prior to the install because I thought it was useless installing if I couldn't get the internet working - can't remember how I did it though.

---

### Post by xini on 2007-12-12
Hi again guys, I have tried to disable IPV6 as per instructions with no success, every time I run the LiveCD then IPV6 is there.  I seem to be unable to disable it.  I agree that maybe you have found my problem, but how to solve it?   The appropriate ticks and settings are no problem within the network settings, I have ensured that they are active and details entered as required while trying different settings.

So far I am no further forward. :(

---

### Post by shadow-of-sin on 2007-12-12
> **xini said:**
> Hi again guys, I have tried to disable IPV6 as per instructions with no success, every time I run the LiveCD then IPV6 is there.  I seem to be unable to disable it.  I agree that maybe you have found my problem, but how to solve it?   The appropriate ticks and settings are no problem within the network settings, I have ensured that they are active and details entered as required while trying different settings.

So far I am no further forward. :(
Did you try and disable IPv6 in Firefox?
Also, what does your "/etc/network/interfaces" file look like?

---

### Post by xini on 2007-12-12
I have tried disabling both ways as described.  I still do not have network connectivity.  I'm afraid i'm a newbie to linux, I do not undestand what you mean in the previous posting.  I would need to be guided.

---

### Post by zabien1970 on 2007-12-12
Since you're running off the live cd any changes you make aren't saved which is why IPV6 is still there, how big is your hard drive, if there's enough room you could try a dual boot, then your changes will stay and you'll still have your windows OS intact. I've read some threads where people couldn't get 'net off the live cd but once they installed it worked.

---

### Post by xini on 2007-12-12
Hi Zabian, I only have the one computer here and i'm afriad the drive is too small to commit to a dual system.  I would commit to a full Ubuntu install if the Internet had worked, but if I do this and it doesn't work then the only way back is a full windows re-install, plus until that time I am without any help or support in the event of any other problems.  

Is this a problem many try before you commit users of Ubuntu are having?  If so, why didn't they make IPV6 something newbies might try to enable rather than try to disable.  Maybe thats one for the think tank at Ubuntu (lol).

It sounds like my circumstances might not be right to try and make the switch at the moment.

---

### Post by zabien1970 on 2007-12-12
Was just rereading this thread and seen where bumanie said others were having this problem in gutsy, maybe if you tried fiesty and see if that works

---

### Post by xini on 2007-12-12
Cool Zabien, I can give that a go.

I wonder how many people have tried the live CD then thrown it in the bin and thought whats the big deal about Ubuntu, it doesnt work!!!!!  LOL I almost have on a few ocassions.

Thanks for the advice guys, it is appreciated.  I will persist with it when I have time.  Hopefully my next thread here will be....OMG, it works and i love it, LOL.

Fingers crossed. :)

---

### Post by The Cog on 2007-12-12
Try posting hte output of these 3 commands, to show us whats going on:
[B]ifconfig
sudo dhclient
netstat -r[/B]

---

### Post by bumanie on 2007-12-12
> **zabien1970 said:**
> Was just rereading this thread and seen where bumanie said others were having this problem in gutsy, maybe if you tried fiesty and see if that works
Yes, I was just going to suggest the same thing. I have not heard of anyone having the same problem with ubuntu 7.04.

---

### Post by leedsdevil on 2007-12-12
just also read this thread and i have also had this problem. i myself have been playing with networking and ubuntu. but as far as internet connection i had to do what was posted in another thread which was to install ubuntu. and bamm its on the net rolling like thunder i hope that helps...:guitar:

---

### Post by stalkingwolf on 2007-12-12
When everything else fails I have had great success with doing this to  get a connection up and running.
It has worked with both wired and wireless connections.

go to:    System> administration> Network> Hosts> select/ highlight the entry that reads,
ffo2::2 ip6 allrouters  > click add.


It works for me  but then it could also be "The Vortex".:lolflag:

---

### Post by gwillgi on 2007-12-12
I myself am a newbie and I happily installed Ubuntu alongside Vista on my laptop, hoping that the internet would work once I had it installed. No deal. Then I tried blacklisting ivr6 and rebooting... cold turkey on my internet connection. Interestingly wireless detection was working. Just that once I looked at the connection information, a load of 0.0.0.0 appeared for addresses. It's as if it could get through to the wireless router but not through the modem. Thing is how do I bleedin' set the addresses for those? The documentation is vague as heck, when it comes to that, sorry guys...

---

