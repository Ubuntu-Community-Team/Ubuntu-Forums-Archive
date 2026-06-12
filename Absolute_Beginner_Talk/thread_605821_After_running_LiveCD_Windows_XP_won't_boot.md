---
title: "After running LiveCD Windows XP won't boot"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by funparks on 2007-11-07
Hello. 

Last night I downloaded Ubuntu 7.10, burned it to a cd, then opened the cd.
The CD title says Ubuntu 7.10 (Disk Tree)
Under the logo is the statement "Boot from this CD to try Ubuntu without affecting your system."
So I did. I restarted my machine and booted from the LiveCD.
I selected Start or Install Ubuntu.
Ubuntu loaded, it ran great, I spent a couple of hours playing around and loved it.
I then shut down my machine for the night and the CD was ejected.

This morning my machine won't start up. I was running Windows XP. I tried booting from the Windows CD and that failed.

What do I try next?

Thank You.

---

### Post by ohzopants on 2007-11-07
What do you mean it won't start up?  Is it maybe looking for a bootable CD (this will only happen if you had to change the boot priority in the bios)?

The LiveCD doesn't (or shouldn't) make any changes to your system unless you go out of your way to do it.  It's very unlikely that running the livecd broke your pc, did anything unusual happen?

---

### Post by funparks on 2007-11-07
> **ohzopants said:**
> What do you mean it won't start up?  Is it maybe looking for a bootable CD (this will only happen if you had to change the boot priority in the bios)?

The LiveCD doesn't (or shouldn't) make any changes to your system unless you go out of your way to do it.  It's very unlikely that running the livecd broke your pc, did anything unusual happen?
Thank you ohzopants. I'm not blaming LiveCD or Ubuntu for this. It is just the only thing out of the ordinary, or rather, the last thing I did before the problem presented itself.
What I mean by "won't start" is that when powering up the machine nothing loads. The lights on the various drives flicker for a moment, the hard drive spins for a couple of seconds then nothing but a black screen.
Noticing that the CD drive lights came on I thought I'd try to boot from the Windows CD, but that failed. That is, absolutely nothing happened. The system did not even try to read the CD.
Nothing unusual happened at all. All I did while in Ubuntu was open a couple of webpages and some of the Example files to try the applications.
When I was done I simply exited and turned off my machine.
Thanks for the help.

---

### Post by oilchangeguy on 2007-11-07
could be a power supply problem. or cpu fan problem.

---

### Post by Ferri on 2007-11-07
Looks like a problem in your machine, not in the operating system.
Check, if you haven't, that everything is plugged.

---

### Post by amingv on 2007-11-07
Hello,

I guess you didn't open your machine... did you? Whenever that's happened to me it was due to a HD/CD drive not plugged correctly, or the jumpers were not properly set up, or (God forbid) in the worst of the cases, a RAM failure.
Try resetting your BIOS in case there's something wrong over there. (Some PCs have a jumper for that, in others you just remove the battery for some 20 seconds and put it back. Just remember to touch some metal object that has contact with the ground before touching the insides of your PC, as to avoid static.)

Whatever it is, I would discard a software problem. By the way, what is your machine? Brand, specs etc...? Does your CPU beep at all? How many times and for how long?

---

### Post by Duck2006 on 2007-11-07
Can you still boot up from the live CD?

---

### Post by oilchangeguy on 2007-11-07
> **Duck2006 said:**
> Can you still boot up from the live CD?

read post #3.

---

### Post by P4man on 2007-11-07
So you are not even able to get into the BIOS ? Then you have a hardware problem. try disconnecting all disks (harddisk and opticals) and see if at least you get into the BIOS that way. If so, reconnect one by one until you find the culprit. Another likely cause is your powersupply. 

If you are afraid of opening your computer, its time to bring it to the shop Im afraid.

---

### Post by funparks on 2007-11-07
Thanks folks.

I've tried each of the ideas suggested to no avail. 
I think the key is...
No, I cannot even get BIOS to post.
No, I cannot boot from either the windows xp cd or the liveCD.

As for system specs...I am unsure of all the details.
AMD 2600+
ASUS A7N8X-X Motherboard
2 WD 80G HD
Sony CD R/W
Liteon DVD R/W
Nspire NSP300P4B
Running Windows XP SP2

I will check posts for a bit longer then I'm off to the shop.

Good day.

---

### Post by P4man on 2007-11-07
perhaps one last thought: is your monitor still working (and properly connected) ? If that is not the problem, either open the case and get your hands dirty or let someone do it for you.

---

### Post by amingv on 2007-11-07
If your BIOS won't POST, then there's definitely something wrong with whether your motherboard or your power supply. Asus uses the Award BIOS, I think.

Regardless, maybe you want to try removing all of your hardware (PCI cards, HDs CD drives, etc) and tempt the BIOS to fall into a fatal error, in which case, it would POST. I tell you this because one time (it wasn't on an Award BIOS though) I had this pc that wouldn't POST, turns out there was a PCI card that was burnt and would hold the PC somehow. (Yes, I still wonder at it, but I have the PCI card to prove it:lolflag:)

Anyway if you don't want to just take it to a shop, and go in the right frame of mind for paying for some hardware.

PS: Ah, If it's not too much getting into your business. Please post what was the problem when you get it solved. I like to collect solutions :razz:

---

### Post by kurotsuno on 2007-11-07
Sounds to me like a power supply problem/motherboard 

the pc next door did the exact same thing I've kind of figured out the problem is due to over heating its a pretty old one 5 years old solved the problem for now by leaving the case door open but will give it a good clean when I get the chance. 

Originally I thought it was my hdd or ram thats why I made a ubuntu live cd if that didn't boot then I would of been right but it booted fine reformated the hdd with ubuntu and everything works fine now. But still doesn't load up sometimes because of overheating the power supply I think.

---

### Post by funparks on 2007-11-10
Thanks to everyone that tried to help.
I got my hands dirty for a bit and did as much as I was comfortable.
Ultimately went to a repair shop. They couldn't get it to post. Suggested motherboard as the culprit. They were no more specific than that.

As time was of the essence I picked up a refurbished machine for $225, swopped out a bunch of stuff (HD's, RAM, DVD-RW, and USB and DVI cards). I got back up and running like nothing happened in just a couple of hours.

Now I have an extra box I can spiff up and make my new Ubuntu machine.

Thanks again for all your comments. I look forward to spending more time here soaking up information and eventually making a positive contribution as well.

All the best,
Funparks

---

