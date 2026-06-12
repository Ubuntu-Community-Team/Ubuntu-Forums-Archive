---
title: "Missing one choice for partitioning"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-17
Good morning from northern California, :D

I have Dapper already installed, and I would like to install Edgy along with Dapper as a dual boot.

I have installed Edgy several times 'after' installing Dapper. I have had them set up successfully as a dual boot. I am having to do a fresh install of both due to some video driver problems and not knowing how to install Dapper without doing damage to the Edgy install. The HDD was formatted. Just a reminder: I have Dapper installed and now want to install Edgy.

Each time, previously, I have been given three (3) choices on how I would like the HDD partitioned. These are the three choices generally stated:
1. Use entire disk...
2. Use the freed space on disk...
3. Manual

However, this time I was only given two (2) choices. See attachment. 
1. Use entire disk...
2. Manual

I would like the partitioning to be automatically done using the second choice in first group above. I do not know what to do with the manual partitioning feature. However, I am willing to learn if someone would take me through it. I do not want to erase Dapper. I still wish to have both Dapper and Edgy installed as a dual boot. 
Thanks for any help here.
kh
Edit: I am using the Live CD at this time.

---

### Post by hyper_ch on 2007-04-17
I guess it's because you don't have any unpartitioned space left on your harddisk?

---

### Post by lamalex on 2007-04-17
Just use the manual, or download the [gparted livecd]("http://gparted.sourceforge.net/") and do all of your partioning there, then go back to the edgy install and finish the deed.

---

### Post by kittyhawk63 on 2007-04-17
> **Iamalex said:**
> Just use the manual, or download the [gparted livecd]("http://gparted.sourceforge.net/") and do all of your partioning there, then go back to the edgy install and finish the deed.

Sorry, you missed the part that I do not know how to use the manual partitioning feature. I never figured out how to get Gparted liveCd to start.

I installed Dapper using erase entire HDD. This is the feature that I have used each time before and still had the three choices.  There is nothing installed except Dapper. Except, I have added Thunderbird. I have a 160 GB hard drive. Only Dapper is installed on it.

---

### Post by hyper_ch on 2007-04-17
Open a terminal and enter
```

sudo fdisk -l

```

And post the output here...

I assume you have 3 partitions right now
1x SWAP
1x Dapper
1x Ex-Edgy

:)

---

### Post by kittyhawk63 on 2007-04-17
I assume you have 3 partitions right now
1x SWAP
1x Dapper
1x Ex-Edgy

No, I have dapper installed and I am presently using the Edgy livecd. I have not partitioned for Edgy.

---

### Post by hyper_ch on 2007-04-17
Do you want to keep your files that you have?

---

### Post by kittyhawk63 on 2007-04-17
sudo fdisk -l will not work since I am using the live cd.

---

### Post by kittyhawk63 on 2007-04-17
> **hyper_ch said:**
> Do you want to keep your files that you have?

I'm sorry, I guess I need to make this a little clearer. This is a fresh install. The HDD has been formatted, There is no saved data except for a fresh install of Dapper and Thunderbird. I am now trying to install Edgy.
Sorry if I have not made this clear.

I can reinstall Dapper if needed.

---

### Post by tstockma on 2007-04-17
Kittyhawk, I have perhaps some bad news...

You're going to have to learn how to work with partitions to get this to work.  I'm no expert yet at GPARTED, but that's actually my next step...you could also buy Partition Magic, or learn to use other command-line tools...personally, I'd recommend GPARTED.

Good luck!

---

### Post by kittyhawk63 on 2007-04-17
[I][quote=tstockma;2468501]Kittyhawk, I have perhaps some bad news...
You're going to have to learn how to work with partitions to get this to work.  I'm no expert yet at GPARTED, but that's actually my next step...you could also buy Partition Magic, or learn to use other command-line tools...personally, I'd recommend GPARTED.[/I]

The Edgy livecd has always allowed me to do a partitioning "automatically". That automatic feature is missing this install and I am trying to understand why.

---

### Post by hyper_ch on 2007-04-17
Just use the first option... Erase all data on the drive

or use the manual partitioner... it's not difficult to setup (and you can't do much wrong as you have no important files on the drive :))

I recommend using the manual one so that you learn how it works :)

With the manual partitioner I recommend 3 partitions:

1) a SWAP partition (Type SWAP) and make it about the double of your ram (somewhat behind 512 MB and 2 GB should be fine)
2) a ROOT partition (Type Ext3) and assign as mounting point "/" - make it about 10 GB
3) a HOME partition (Type Ext3) and assign as mounting point "/home" - use the rest of your diskdrive for that

---

### Post by Outrunner on 2007-04-17
> **kittyhawk63 said:**
> [I][quote=tstockma;2468501]Kittyhawk, I have perhaps some bad news...
You're going to have to learn how to work with partitions to get this to work.  I'm no expert yet at GPARTED, but that's actually my next step...you could also buy Partition Magic, or learn to use other command-line tools...personally, I'd recommend GPARTED.[/I]

The Edgy livecd has always allowed me to do a partitioning "automatically". That automatic feature is missing this install and I am trying to understand why.

Because you formatted the HDD and then used the "automatic partitioning" feature while installing which left no unpartitioned space(hence you can't use the rest of the hard drive because there simply is no more unused space).

Now, first of all I have no idea why you would want to dual boot dapper and edgy; and then second, I'm afraid to say that you will need to learn how to manually partition your hard drive if you want to do this properly(or at all). Might I remind you that if you at least try, you will find that it is an easy thing to do?

---

### Post by kittyhawk63 on 2007-04-17
I found the problem. When the video driver got messed up while installing a new driver, it prevented Dapper from loading on boot. When I booted with Edgy livecd it could not recognize Dapper because the computer did not load any of Dapper's feature that would allow it to start. When those features did not get recognized, Edgy livecd did not give me the choice to use the free space. It makes sense when you think about it.
I have decided to do a fresh install again. This time I will leave the default driver with Dapper alone until I install Edgy. I will be sure to do a xorg.conf.bak file also. That way I can install the default video driver if I need it again.
Thanks of all the help.
kh

---

### Post by kittyhawk63 on 2007-04-17
> **Outrunner said:**
> [quote=kittyhawk63;2468514][i]

Because you formatted the HDD and then used the "automatic partitioning" feature while installing which left no unpartitioned space(hence you can't use the rest of the hard drive because there simply is no more unused space).

Now, first of all I have no idea why you would want to dual boot dapper and edgy; and then second, I'm afraid to say that you will need to learn how to manually partition your hard drive if you want to do this properly(or at all). Might I remind you that if you at least try, you will find that it is an easy thing to do?




I have done this three times using this method and it worked each time. See my explanation concerning the video driver why there was only two choices.
I am still discovering Ubuntu features in both Dapper and Edgy.  I like features in each. I haven't settled on which I prefer. Until much of Feisty's bugs are worked out (several months away) I will stick to either Dapper or Edgy or both.

---

### Post by hyper_ch on 2007-04-17
What Feisty bugs? For me it's rockstable :)

---

### Post by darrenm on 2007-04-17
Echoed. Which Feisty bugs?

---

### Post by kittyhawk63 on 2007-04-17
Type "Feisty bugs" in Google and see the entries for bugs. I even found a Feisty site saying there were bugs. I've tried finding it again. When I do, I will post it.
kh

Try these for a starter:
[http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured/](http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured/)
[https://launchpad.net/ubuntu/feisty/+bugs](https://launchpad.net/ubuntu/feisty/+bugs)
[https://bugs.launchpad.net/ubuntu/feisty](https://bugs.launchpad.net/ubuntu/feisty)

---

### Post by hyper_ch on 2007-04-17
And you think dapper or edgy have no bugs?

---

### Post by darrenm on 2007-04-17
> **kittyhawk63 said:**
> Type "Feisty bugs" in Google and see the entries for bugs. I even found a Feisty site saying there were bugs. I've tried finding it again. When I do, I will post it.
kh

Try these for a starter:
[http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured/](http://www.osnews.com/story.php/17505/Ubuntu-Feisty-Fawn-Desktop-Linux-Matured/)
[https://launchpad.net/ubuntu/feisty/+bugs](https://launchpad.net/ubuntu/feisty/+bugs)
[https://bugs.launchpad.net/ubuntu/feisty](https://bugs.launchpad.net/ubuntu/feisty)

No offence intended but you have to be joking, right?

1. You can also search google for Dapper Bugs and Edgy Bugs and it gives results. Ubuntu will always have open bug reports. But they will never release if there is anything that is going to cause major problems. It has been the same for Dapper and for Edgy. There are still many open bugs for both releases.

2. The osnews review is basically saying that Feisty is very easy to use and the reviewer lists the broadcom wireless drivers as the only problem he had. Theres a whole much bigger story to the Broadcom debacle that runs deeper than I can list here but Feisty is about the best shot you have so far of getting wireless to work if you are burdened with one of those cards. 

3. The 2 links to launchpad are the same site. You can also go to [https://launchpad.net/ubuntu/edgy/+bugs](https://launchpad.net/ubuntu/edgy/+bugs)

The general accepted point of view around the community at the moment is that Feisty is the most stable release so far and its the release that Edgy should have been. Canonical are making a song and dance about this release more than ever before, like a countdown on the Ubuntu home page. Edgy hardly got a mention. 

I don't mean to be rude, I'm just surprised at your point of view :) and certainly from my own experience I would recommend Feisty over any other Ubuntu release or even any other Linux distro. In fact from tomorrow its starting to go on all the new servers my company roll out.

Sorry for pulling your thread off course.

---

### Post by kittyhawk63 on 2007-04-17
No offense taken. You have a right to your view. I just noticed that many people in this forum have had a lot of problems getting Feisty to work properly. I must admit, however, that I installed the beta and it worked fine with no hitches. It even recognized my ATI Radeon 9200SE video card which neither Dapper or Edgy had done. It took me weeks to get that issue resolved.

Again, no offense taken. I appreciate your point of view.
kh

---

