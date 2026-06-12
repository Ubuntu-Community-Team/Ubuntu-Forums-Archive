---
title: "Installed TinyXP - Can't boot Ubuntu."
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Jason2gs on 2008-04-02
Due to the plight of The Great Incompatibility War, it would seem my need for an bare-bones, Windows-based operating system is becoming evident.

I didn't want to fork over hard drive space that I didn't have, to get a bunch of crapola that I didn't need, and not wanting to go through the hassle of finding a WinXP install disk, I decided to simply partition away two Gig of hard drive space off my main disk, and install TinyXP.

I bummed a cheap blank CD off my sister, and copied the ISO.

I shut my computer off, popped in the disk, and installed it. Everything was going great.

Until I wanted to boot back up into Ubuntu so I could get online and grab the correct driver for my wireless card.

*Sigh*

Winnowz decided to make itself dominate :(

A friend reminded me about the boot.ini file, and I started editing that.

Here's the current boot.ini file:

```

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\Ubuntu
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\Ubuntu="Ubuntu Gutsy Gibson (7.10)" /fastdetect


```

Is something wrong with that?

When I try to boot up with that, Windows tells me that it's missing a hal.dll.

I don't think I should need hal.dll. Not unless I'm trying to boot up with another Windows.

Another thing: Windows is unable to detect the other partitions on the hard drive.

Really starting to wish I didn't get TinyXP in the first place. Seems anything I try to do ends up backfiring on me ^_^

Well, that about does it. Can someone tell me what I've done wrong? :)

Really hoping to get back into Ubuntu tonight. A little bummed about that.

---

### Post by Jason2gs on 2008-04-02
Oh, another thing.

In Computer Managment window, under Storage, the right pane says, "There are no items to show in this view."

I should be able to set a partition as active, correct?

---

### Post by Jason2gs on 2008-04-02
Bump

---

### Post by ghost_ryder35 on 2008-04-02
google "super grub" download, burn and enjoy :)
*edit* added the link so you dont have to google (damn I'm so nice)
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by Jason2gs on 2008-04-02
That seems like a troubleshooting workaround.

I remember seeing a post somewhere around here about how to restore your GRUB through the Live CD. Would that be better?

I'd also like to not waste another CD...

---

### Post by ghost_ryder35 on 2008-04-02
> **Jason2gs said:**
> That seems like a troubleshooting workaround.

I remember seeing a post somewhere around here about how to restore your GRUB through the Live CD. Would that be better?

I'd also like to not waste another CD...
you can fix your grub with the Live CD, and its not a "Troubleshooting workaround" we already know that Windoze wrote over your MBR
```
sudo gedit /boot/grub/menu.lst
```
The Super Grub CD is a life saver in a lot of cases (yours being one).  Dont be so cheap CD's are like $.10 cents in the United States

---

### Post by Xiong Chiamiov on 2008-04-02
I believe [this]("http://ubuntuforums.org/archive/index.php/t-24113.html") is what you're looking for (or at least one guide that shows what you want to do).

BTW, I always liked that pic of Wikipe-tan.

---

### Post by Jason2gs on 2008-04-02
That was the guide I saw before! Thank you :)

And I know. I'm cheap :(

It's just that I rarely have a chance to get to the store. The times I can get to the store, my only choice is to spend the whole day there when my Mom/sister are working.

I may pick some up. I'm glad to know that it's a known problem.

And isn't she cute? ^_^

I also like your Haibane Renmei angel. Good show.

---

### Post by Xiong Chiamiov on 2008-04-02
> **Jason2gs said:**
> 
And isn't she cute? ^_^
Yes ;)
> **Jason2gs said:**
> 
I also like your Haibane Renmei angel. Good show.
First time someone's recognized it.  I watch a wide variety of stuff, but that's definitely stickin' up in my favs.

---

### Post by LaRoza on 2008-04-02
TinyXP is illegal and getting support for it is not allowed on this forum.

---

