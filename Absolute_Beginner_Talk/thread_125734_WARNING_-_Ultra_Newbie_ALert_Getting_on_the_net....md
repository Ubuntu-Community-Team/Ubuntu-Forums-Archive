---
title: "WARNING - Ultra Newbie ALert: Getting on the net.......How?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by zizzle on 2006-02-04
Hello everyone,
Before I go any further, please let me say that I have never used any Linux operating systems before and I have to say that I'm very impressed!             My querys are :
How do I set up my USB DSL modem so that I can get on the net? 
Do I need special drivers? 
Is there a possibilty of some type of generic driver or something? 
Is there some sort of program that can run Win progams under Ubuntu?

I don't have a clue where to look even. As you will have guessed, I've switched to Windows to post this. Many years of Windows abuse has atrophied my old brain and I still can't get a hook into Ubuntus command line thing (I have no idea about commands, syntax or anything).  Could you guys point me to where I can get some docs on Ubuntu that I can understand. There, I've bared my pitiful soul to you guys - go easy on me please.:) 
Regards to all,
Mike

---

### Post by moephan on 2006-02-04
Zizzle,

Was the modem plugged in when you installed Ubuntu? Try plugging in the modem, then go System->Administration->Networking and see if it looks like Ubuntu is detecting your modem. If so, you can select it and try clicking "Activate".

If the networking administration program doesn't work for you, you might want to check this thread and see if it could be helpful:
[http://ubuntuforums.org/showthread.php?t=35197](http://ubuntuforums.org/showthread.php?t=35197)

Cheers, Rick

---

### Post by Freddie.Ruddick on 2006-02-04
Greetings from a fellow newbie!

DSL modem: No idea, sorry. :(

>Is there some sort of program that can run Win progams under Ubuntu?
Yep, "wine" can run some Windows programs

The "Ubuntu Starter Guide" is a good place to start. Click System, then help (Or the liferaft thing on the bar at the top of the screen) , then select the starter guide.

To learn about the command line, [the LinuxCommand.org "Learning the shell pages"](http://www.linuxcommand.org/learning_the_shell.php) are quite good (they taught me)

Hope this helps. Enjoy Ubuntu!

---

### Post by cjm5229 on 2006-02-04
Here is a pretty useful guide. [http://makuchaku.info/amnesty/#downloadguide]("http://makuchaku.info/amnesty/#downloadguide")
 I hope this helps. Once you get online check out the thread for Automatix. it will help you get setup easily.

---

### Post by Michael Steinberg on 2006-02-04
If your modem and your computer have ethernet ports, there's no problem at all--Ubuntu will try DHCP (getting an internet address from the connection itself) and that should do the trick, unless your ISP uses pppoe ("ppp over ethernet"). The problem you're likely to be having doesn't come from DSL but from the USB connection; it's not the expected course for network connections. Try searching the forum & Wiki for usb networking.

---

### Post by zizzle on 2006-02-06
:) Hey Guys,
Thanks for all the replies - You have all been very helpful. But I think that Michael has hit the nail on the head there when he said about USB ports not being the one of ubuntu's choice. Could this be resolved by just shoving a network card in and trying that? Or is a little more involved than that?
Thanks again to all,
Mike (zizzle)

---

### Post by daibak on 2006-02-06
Hi zizzle,

Please type the following command in a Breezy terminal
```
ifconfig
```, hit Enter, and then copy-and-paste what is output in your terminal so we can try to help you.

---

### Post by Sbarton on 2006-02-06
As someone else who is old but new to linux I can say that my usb modem Voyager 105 just was not good enough.Though I did see that at least one person had made a connection with it after a lot of help. I had to change to a router and network card to geta connection. Even so I still have problems.But that is another matter.All the best. This is a very helpful community so you will get helped.

---

### Post by Sokraates on 2006-02-06
[quote=zizzle]:) Hey Guys,
Thanks for all the replies - You have all been very helpful. But I think that Michael has hit the nail on the head there when he said about USB ports not being the one of ubuntu's choice. Could this be resolved by just shoving a network card in and trying that? Or is a little more involved than that?
Thanks again to all,
Mike (zizzle)[/quote]

Ethernet should do just fine. Usually all you need to do is plug it in. I couldn't get my USB cable-modem to work with ubuntu (or any other linux-distribution, for that matter). Luckily the modem hat an ethernet-port, too. So I just used that one to plug it to my computer an *PRESTO* ubuntu did the rest.

---

