---
title: "Wireless internet"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Scree on 2006-03-19
This question may have been asked already, but I searched through the forums and couldn't find a solid answer.
I am connected to the internet through a belkin wireless card. I recieve internet fine and at start up in windows XP. Right now, I'm running linux through a live disc so I can get the feel of it before I load it as a main OS. What do I need to do in order to gain internet access?

---

### Post by Sendervictorius on 2006-03-19
Have a look at this page, and hopefull identify if your belkin model is supported.
[https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards/](https://wiki.ubuntu.com//HardwareSupportComponentsWirelessNetworkCards/)

Then take a look at 
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)
which will provide lots of information to help.

Personally, I wouldn't bother going to the effort of trying to get the wifi connection going with a live CD, (unless it just works - then you wouldne't need efort!). I would install Ubuntu permanently on my PC, then configure my wifi after. Remember you can always blow Ubuntu away, if you don't like it, and return to windows. In my experience most wifi cards can be made to work, so long as you keep the configuration to a basic level. There can be lots of mesing around, and doing it all on a live CD. Live CD is painfully slow too - and you have to set up stuff every time you boot.

---

### Post by Scree on 2006-03-19
Thanks, I'll take a look at those.
Also (a mildly unrelated question), can I terminate Linux and go straight into Windows, or do I have to log out, reboot, etc?

---

### Post by Sendervictorius on 2006-03-20
Yes you do have to reboot. When a computer "boots" Linux it loads the operating system off the disk, into memory and starts running it. To run windows, your PC must start again, and load Windows off disk into memory and then start running that.

EDIT: Sorry I re-read your question, and maybe I misinterpretted.

You must always shutdown Linux when you are finished. That way Linux shuts down all the programs that are running in an orderly fashion, and makes sure all the data is written to disk. It then "unmounts" the disks.

If you have a power failure, or turn off the PC by hitting the big button, you run the risk of loosing data, or causing corruption to the data on disk. Linux stores lots of data in memory to ensure quick response, so bad things can happen when the power stops. Mostly, it doesn't matter too much in practice, because modern journalling file-systems can recover themselves. But better to be safe. In windows, however, hitting the big button can cause corrupt disks bigtime.

---

