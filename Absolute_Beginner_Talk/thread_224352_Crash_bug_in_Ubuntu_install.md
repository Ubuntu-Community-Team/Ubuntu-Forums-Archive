---
title: "Crash bug in Ubuntu install?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by sojakfa on 2006-07-27
So, on Sunday night I installed Ubuntu for the first time and loved it. It worked great for a couple of days while I manually installed and updated everything. I even started moving over files from my Window's hard drive (like my 12gig music collection :-( ).

So once I've pretty much got all my hardware running (which wasn't hard, just time consuming since I did it manually) I start tweaking my software, trying to get my games (well, just Guild Wars actually) running. During the course of that I find a helpful piece of software named Automatix. I install it and have it update everything that sounds interesting/helpful, and that's where the trouble starts. After I install it I restart it, and since that point Ubuntu will boot up, it'll let me log in, and then a couple of minutes later will hang. And it doesn't seem to matter what I'm doing, whether it be installing software or just surfing the net.

So I boot it up in the safe mode to maybe try and save my music, but find out it's command line only, which is a completely foreign language to me. So I bite the bullet, put in the boot cd, and repartition the drive and do a fresh install. That time and every time since (it's been at least 4 times now) I've formatted the drive and reinstalled it fresh, and it will stay up at the longest two hours and at the shortest 5 minutes, and I'm not sure why. Sometimes Automatix will be installed and I'll have at least some of it updated, sometimes all the alteration I've done is plug my WEP key into my wireless network card.

Here are my system stats, incase that helps:
2.0 gH Celeron
1 gig DDR RAM
1x 40gig hard drive formatted NTFS with Windows XP Pro installed
1x 120gig hard drive formatted to whatever Ubuntu formats to with a broken version of Ubuntu on it.
1 Creative Labs Audigy LS sound card
1 Geforce FX 5600
1 Dynex 4 port USB PCI card.
1 D-Link wireless network card.

I'd really like Ubuntu to work, as I was really enjoying it. If someone has any ideas I'd love to hear them!

---

### Post by T700 on 2006-07-27
"So I bite the bullet, put in the boot cd, and repartition the drive and do a fresh install. That time and every time since (it's been at least 4 times now)"

If you've reformatted and reinstalled four times, there is nothing from earlier installations hanging around to cause trouble.  Perhaps a hardware issue?

Paul

---

### Post by sojakfa on 2006-07-27
Well, it was working fine for like 2 days before this popped up, and all my hardware seems to be compatible. The only piece of hardware that I had to do anything special for at all was my Geforce 3d card, which I was expecting.

---

### Post by molly_001 on 2006-07-27
Were you using the Alternate Install CD for these installation(s) or the Live-CD installer?

---

### Post by sojakfa on 2006-07-27
I was using the one at [this]("http://www.ubuntu.com/download") link, which I assume is the LiveCD.

---

### Post by Sef on 2006-07-27
> I was using the one at this link, which I assume is the LiveCD.

That link lead to both the LiveCD and the alternate cd.

Yes or No Question: Did you install from the LIveCD?

---

### Post by nalmeth on 2006-07-27
I would wager that you selected to install nvidia drivers thru automatix, and when you restarted, X wouldn't load.

Try installing with the alternate install CD, and if anything similar occurs again where X cannot start, at the command prompt, issue this command:

sudo dpkg-reconfigure xserver-xorg

and go back to the nv driver, or failing that, the vesa driver.

---

### Post by sojakfa on 2006-07-27
First, where is the alternate cd? I'll gladly use it if I can find it!

There is one issue though. Like I said, one install literally all I did was enable my wireless card. I didn't do any kind of updates at all, not even the geforce drivers, and it still crashed.

Still though, I'll give anything a shot at this point. I really enjoyed using Ubuntu those couple of days it worked!

---

### Post by sojakfa on 2006-07-27
> **Sef said:**
> That link lead to both the LiveCD and the alternate cd.

Yes or No Question: Did you install from the LIveCD?

How can I tell? I just downloaded from one of the United States links.

---

### Post by nalmeth on 2006-07-27
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

simply scroll down to alternate install section.

It's a less pretty but more stable way to install

Good Luck!

---

