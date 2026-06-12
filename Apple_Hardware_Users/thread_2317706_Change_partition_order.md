---
title: "Change partition order"
date: 2016-03-18
forum: Apple Hardware Users
---

### Post by Marcos_Albernaz_Bi on 2016-03-18
Hi i have this parition map 

[[img]http://www.zimagez.com/miniature/screenshot-18-03-2016-224556.php[/img]](http://www.zimagez.com/zimage/screenshot-18-03-2016-224556.php)

as you can see i have , in the selected region 13,65 gb avalliable, i would like to use that space to expand /dev/sda5 partition... is it possible? how?

---

### Post by papibe on 2016-03-18
Hi Marcos_Albernaz_Bi.

It is possible, although instead of one step, you would need to do several small steps. You would need to boot using a the Ubuntu installation media as a Live media. Instead of choosing install Ubuntu, select 'Try Ubuntu'. Once you get to the desktop, use gparted to do the job.

I'd recommend backing up your data. There is some slightly risk of something going wrong.

This is what I would do:
[LIST]
[*]Get the free space next to the partition:
[LIST]
[*][*]move /dev/sda3 to the end of /dev/sda2
[*][*]move /dev/sda4 to the end of /dev/sda3
[*]
[/LIST]
[*]Then, you can extend* /dev/sda5 to grab the free adjacent space.
[*]
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.: This looks like a Mac. I have no idea how moving the HFS partitions would affect MacOS.

* don't remember if you only can expand only at the end. Is that the case you would need to move /dev/sda5 to the end of /dev/sda4 first.

---

### Post by Bob_Bruce on 2016-03-20
Did this recently (as papibe indicated) with my internal 500GB HD and everything went very well with no issues. 

Tried it again recently with a 2TB USB3 external drive. Was going to move about 450GB of data to make room for expanding another partition. Started it and walked away for awhile as it churned away. When I returned about 10-15 minutes later I saw the estimate of several hours to complete (due to the slow USB2 connection on my 2009 iMac) so I decided to cancel it. It took about as long as it had been going to put everything it had done back in place. Until I get a newer system (with USB3 port) I'll pick a time when I don't need to use the computer (overnight) to move that partition.

---

### Post by papibe on 2016-03-20
> **Bob_Bruce said:**
> ... everything went very well with no issues.
Glad to hear that :D

> **Bob_Bruce said:**
> Tried it again recently with a 2TB USB3 external drive.
Doing this movements on internal SATA drives is pretty safe. Same thing over external USB not really sure.

The only problem that I've had moving partition was while working on a external USB drive. Some how the system lost the connection over USB, remounted the disk on another device, and the disk was left on an messy state. 

I would recommend not getting too confident because of the previous success, and backing up your data by all means.

Just some thoughts.
Regards.

---

