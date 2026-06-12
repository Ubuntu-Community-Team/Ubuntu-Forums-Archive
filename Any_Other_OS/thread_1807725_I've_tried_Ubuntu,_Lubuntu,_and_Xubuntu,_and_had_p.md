---
title: "I've tried Ubuntu, Lubuntu, and Xubuntu, and had problems with all of them"
date: 2011-07-19
forum: Any Other OS
---

### Post by BKbroila on 2011-07-19
I began using Linux with Ubuntu, and it was pretty good. Very easy to get to know the system as basically everyone says. But it kept overheating my laptop (a Dell) and so I had to switch distro. I decided to go with Lubuntu, as I posted a thread some time ago asking for suggestions.

Lubuntu seemed very minimal, but it was too minimal for me. As a very novice user, I had trouble getting apps and various programs.
So I installed Xubuntu the other day and it was awesome. Seemed just like Ubuntu, but it a bit lighter. However, I thought wrong and it overheated on the second bootup. 

So now, I'm thinking of getting Linux Mint, but I really don't want to try a distro that will give me problems. So is Linux Mint (specifically the XFCE version) known for overheating problems? It seems like a very up-to-date distro with lots of apps, so I'm not worried about that aspect.

If Linux Mint XFCE probably wouldn't be a good choice, any other recommendations? Peppermint? 

I just really don't want to waste my time trying new distros and waste CDs

---

### Post by snowpine on 2011-07-19
Ubuntu, Lubuntu, Mint, etc. are all the same operating system. :)

Give Fedora, PCLinuxOS, OpenSUSE, etc. a try if you'd like to experiment with different distros.

---

### Post by Morbius1 on 2011-07-19
> So is Linux Mint (specifically the XFCE version) known for overheating  problems? It seems like a very up-to-date distro with lots of apps, so  I'm not worried about that aspect.Mint XFCE is Debian based not Ubuntu based so you might have a different outcome. 

>  I just really don't want to waste my time trying new distros and waste CDs     That's why god made VirtualBox. Once installed download the linux disto of choce. Install from the ISO not from a CD into VBox. It's not going to answer the overhearing problem but you can see how it works before committing to a real install.

---

### Post by 23dornot23d on 2011-07-19
> 
But it kept overheating my laptop (a Dell) and so I had to switch distro.
[COLOR=Red]**Really you need to work out why its overheating .....**[/COLOR]

Graphics card usage maybe ..... I noticed you do rendering ..... but what graphics card are you using and what drivers ..... 

is it a Nvidia graphics card ..... check in Nvidia Settings and watch the thermal reading there as you are doing things ..........

Maybe its a kernel issue ..... what kernel are you running ........

**uname -r**

have you checked by updating/upgrading ..... 

I ask these questions as I have had similar problems a while back now ...... but upgrades and a new graphics driver solved my problems .....


( If its overheating on everything - is it a blocked air vent ...... or no air flow ...... a fan not working maybe !!! )

---

### Post by craig10x on 2011-07-19
if he tried Linux Mint 11, Ubuntu 11.04 or any other current distribution that has the .38 kernel, his hardware probably was suffering from the "power regression" in the kernels from .38 and up...

The last one that didn't have the problem was kernel .37 as that was before certain changes were made that now causes laptops to use quite a bit more battery power (thus shortening the time they last on a charge) and also causes your fan to come on all the time and the computer to overheat even when on AC power...

It's also affected desktops as well as laptops...

Though ubuntu as well as the kernel developers are working on it, it could be quite some time before it really gets fixed...

Meanwhile, he should try Mint 10 instead and likely he should NOT have the problem at all...That used an earlier kernel...

It doesn't affect everyone but it affects MANY...which is why the bug is considered HIGH PRIORITY...

---

### Post by BKbroila on 2011-07-19
> **Morbius1 said:**
> Mint XFCE is Debian based not Ubuntu based so you might have a different outcome. 

That's why god made VirtualBox. Once installed download the linux disto of choce. Install from the ISO not from a CD into VBox. It's not going to answer the overhearing problem but you can see how it works before committing to a real install.

So would Mint XFCE most likely not give me overheating problems? Or does it use the same kernel, which would give me pproblems?

---

### Post by christopher.wortman on 2011-07-19
Try cleaning the cat hair out of the heat sync :-P

In all seriousness, what is the make and model of your laptop.

I highly suggest that you try Arch. It is Debian based with a good attitude when it comes to KDE. It has Gnome and XFCE, but KDE is lighter than Gnome, think just a little heavier than XFCE. 4.6.4 is amazing and 4.7 is just around the corner. It requires 384mb of ram, but usable at 512. I suggest having at least a gig or two of ram. Stay away from RPM based distros. Gentoo and Debian based all the way. RPMs tend to take a lot of processing power, and in my experiences, RPM based distros aren't as robust and seem to break a lot.

---

### Post by BKbroila on 2011-07-19
Well, I think craig10x is right in saying that it's a kernel bug. I've posted help on my problems, and nobody's been able to give a solution. There's other laptops and Dell Studios (my model) that have my same problem.

I'll look into your suggestion though

---

### Post by ilovelinux33467 on 2011-07-19
> **christopher.wortman said:**
> Stay away from RPM based distros. Gentoo and Debian based all the way. RPMs tend to take a lot of processing power, and in my experiences, RPM based distros aren't as robust and seem to break a lot.

That's interesting because I have never had a RPM based distro break on me.

---

### Post by craig10x on 2011-07-20
Yes...please do give Mint 10 a try...you can run it live without installing...and run it for a few hours, including having some high cpu intensive stuff going on in the background (a good test would be the streaming radio from a station's website...keep that on in the background for several hours...

If you find that the computer doesn't overheat and the fan isn't coming on and going into "high gear" then that would indicate the you would be good to go if you would actually install it...

Every latest distro with the .38 kernel i tried had the problem on my computer...that is why i ended up re-installing Mint 10 again...no problem on there...

Just trying a lighter distro like XFCE wouldn't necessarily solve the problem if it had the latest .38 kernel...I would try running the live dvd of Mint 10 first...

---

### Post by kazuya on 2011-07-20
The best option I can recommend would be Crunchbang Linux (uses xfce / openbox)
You can install gnome and/or kde later. It is based on Debian Squeeze. It uses the 2.6.32 kernel at first, but once you complete updates after install you get the liquoriz 2.6.36-rc kernel which I find awesome so far.
 
Quite comparable to the 2.6.37 kernel performance-wise.
 
Linux Mint Debian edition or XFCE Mint is nice as well (slightly easier than crunchbang)
 
Another option may be Mepis (Debian and kde-based)
 
 
If you are fairly good and experienced with linux and not afraid of the cli or terminal, Archbang is another way to go. (default is 2.6.37, but upon upgrade it goes to 2.6.39-rc which is better than 2.6.38. Not all regression issues are fixed on this though. So far, it is hard to see any performance hit on archbang. It is my fastest distro yet.

---

### Post by BrokenKingpin on 2011-07-20
Clean out the fans on your laptop... that is the number one cause of overheating problems. I highly doubt it is the OS causing the overheating issues.

If is somehow is Ubuntu that is causing the issues, give OpenSUSE a try.

---

### Post by craig10x on 2011-07-20
> **BrokenKingpin said:**
> Clean out the fans on your laptop... that is the number one cause of overheating problems. I highly doubt it is the OS causing the overheating issues.

If is somehow is Ubuntu that is causing the issues, give OpenSUSE a try.

A friend of mine had suggested that when i started having problems with distros using .38 kernel, but if it was because the fan was dusty then how come as soon as i switch back to any distro with a kernel previous to that one (like Mint 10 for example) then the problem disappears completely...Computer runs cool, doesn't overheat and the fan doesn't come on at all!

Wish it was something as simple as blowing the dust off the fan...but no..it is the regression...which by the way STILL has not been fixed yet...
Also, did you know that over 300 reports were filed about it at launchpad and it has been assigned a high priority....

Do all 300 have dusty fans??? (lol)

---

### Post by Morbius1 on 2011-07-20
From: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)
> **As you probably already know, the Linux Kernel has a pretty significant power issue starting with version 2.6.38** which hasn't been fixed yet (this includes version 3.0.0). **This bug causes power consumption to go up by nearly 30% (and hence a shorter battery life)** as [reported by Phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1") which is pretty bad for netbook / laptop users. Some users are also reporting that this causes their laptops to **overheat**.

[COLOR=Blue]**EDIT**[/COLOR]: OOPS, what craig10x said.

---

### Post by handy on 2011-07-21
I'd give Mint Xfce at go. It may be based on Ubuntu or Debian which of course Ubuntu is based on, but Mint does manage to solve a lot of bugs that Ubuntu don't, so give it a go with your fingers crossed.

---

### Post by BKbroila on 2011-07-21
Alright, so I'm going to pick Linux Mint XFCE, but I don't know which one to select here: [http://www.linuxmint.com/release.php?id=15](http://www.linuxmint.com/release.php?id=15)

I don't see an option for XFCE

And to make sure, Lint Minux 10 XFCE, if it exists, is Debian-based?

EDIT
Nevermind. Found it!

---

### Post by BKbroila on 2011-07-24
Sorry, I'm confused as to what everyone is recommending: Linux Mint 10, Linux Mint Debian, or Linux Mint Debian XFCE???

Is 10 based on Debian?

---

### Post by Morbius1 on 2011-07-25
You know it is confusing.

Linux Mint 10 = Ubuntu based
Linux Mint 11 = Ubuntu based
Linux Mint Debian Edition = Debian based
Linux Mint XFCE: 

32 bit: [http://www.linuxmint.com/edition.php?id=79](http://www.linuxmint.com/edition.php?id=79)
64 bit: [http://www.linuxmint.com/edition.php?id=80](http://www.linuxmint.com/edition.php?id=80)

All current XFCE's are Debian based.

---

