---
title: "[SOLVED] If I install ubuntu 7.10 and want to try Linux Mint..."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by patrickaupperle on 2007-12-24
Do I have to dual boot :( or can I just apt-get something like I would if I wanted Kubuntu:KS?:confused::confused:

Oh and one more thing, can these downloads, [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php), be used to make live cds?

---

### Post by seshomaru samma on 2007-12-24
You will need to dual boot
Linux mint is based on Ubuntu but is not Ubuntu
I don't know about the second question

---

### Post by patrickaupperle on 2007-12-24
Thank you,

That is too bad:(, I will have to contemplate dual booting

---

### Post by dpar on 2007-12-24
Those downloads are livecds.

Well....they are isos.

---

### Post by patrickaupperle on 2007-12-24
OK thanks,
Are there any negative effects (besides used harddrive space) to dual booting?

---

### Post by dpar on 2007-12-24
I triple boot, sometimes more, when I'm testing distros, and have had no problems whatsoever.

---

### Post by patrickaupperle on 2007-12-24
With a 60 gig hard drive would it be advisable to dual boot?
how should I partition it?
Will installing Linux mint or Ubunutu first be best?

---

### Post by dpar on 2007-12-24
Yes, thats big enough. I'd split it in half. If you find that you mostly use one distro and are running out of space, you can always resize later.

---

### Post by LowSky on 2007-12-24
> **seshomaru samma said:**
> You will need to dual boot
Linux mint is based on Ubuntu but is not Ubuntu
I don't know about the second question

stragely enought mint can be converted back into vanilla ubuntu.. I only know because I did it like 5 days ago. So in theory you could add mints parts if you know the repository... :guitar:

---

### Post by Duck2006 on 2007-12-24
> Edit: Will installing Linux mint or Ubunutu first be best?

It does not matter witch one you install first. grub will pick up the other ver of linux and you will be able to boot it from there.

Partition for about as much as you need, and you may try one home partition for both ver's of linux, but you will have to have two different users name fir each ver.
For ubuntu / i would try 10Gb
For linux mint / 10Gb
For home 10Gb

---

### Post by dpar on 2007-12-24
You might want to remember, though, whichever distro you install last will 'own' grub.
If you have to edit the menu.lst file at any time later, that is the distro that you will have to do it in.
Because I install and remove distros all the time, I got in the habit of having the new distro install grub on it's own partition and then chainloading from my main distro.
That way grub doesn't really get messed with.
If your not planning to change around a lot, you should be ok.

---

### Post by patrickaupperle on 2007-12-24
> **Duck2006 said:**
> It does not matter witch one you install first. grub will pick up the other ver of linux and you will be able to boot it from there.

Partition for about as much as you need, and you may try one home partition for both ver's of linux, but you will have to have two different users name fir each ver.
For ubuntu / i would try 10Gb
For linux mint / 10Gb
For home 10Gb

Make a home partition for both?:confused::confused:
Can someone link me to a how-to or explain this better?

Thank you all for the wonderful replies:)

---

### Post by Duck2006 on 2007-12-24
> **patrickaupperle said:**
> Make a home partition for both?:confused::confused:
Can someone link me to a how-to or explain this better?

Thank you all for the wonderful replies:)

Yes one home for both. Make your partitions befor you install with gparted cd or from the ubuntu live cd. 
Then when you install ubuntu go to manual partition and mark one of the / root partition for the ubuntu install and do the same for the home partition.
When you install the linux mint do the same as for ubuntu that is mark the other / root partition and mark the home partition (don't format the home partition you have your ubuntu files in).
grub will install and you will be able to dual boot your system.

---

### Post by patrickaupperle on 2007-12-24
> **Duck2006 said:**
> Yes one home for both. Make your partitions befor you install with gparted cd or from the ubuntu live cd. 
Then when you install ubuntu go to manual partition and mark one of the / root partition for the ubuntu install and do the same for the home partition.
When you install the linux mint do the same as for ubuntu that is mark the other / root partition and mark the home partition (don't format the home partition you have your ubuntu files in).
grub will install and you will be able to dual boot your system.

let me clarify:
Your telling me to make 3 partitions with gparted
   Ill just call these 1 2 and 3

you telling me to install ubuntu on 1 and mark 2 as home
the to install linux mint on 3 and mark 2 as home?

Is this correct?

---

### Post by jeffus_il on 2007-12-24
I would download a live cd and make sure that it is really worth all the effort before installing. Go to the mint site and type live cd in the search box, they have quite a bit written about it.

---

### Post by Duck2006 on 2007-12-24
> **patrickaupperle said:**
> let me clarify:
Your telling me to make 3 partitions with gparted
   Ill just call these 1 2 and 3

you telling me to install ubuntu on 1 and mark 2 as home
the to install linux mint on 3 and mark 2 as home?

Is this correct?

Yes i would have

1 as ubuntu
2 as mint
3 as home (just incase you need to increase the size of the home partition).

---

### Post by patrickaupperle on 2007-12-24
ok :) thank you all for all of the help
I am downloading the live cd now to make sure that I want to go through all of this.

---

### Post by Duck2006 on 2007-12-24
Good luck hope it all works out for you.

---

### Post by patrickaupperle on 2007-12-24
Thanks :)

What would happen if i decided to delete my ubuntu or linux mint partitions?

---

### Post by LeAstrale on 2007-12-24
> **patrickaupperle said:**
> Thanks :)

What would happen if i decided to delete my ubuntu or linux mint partitions?

Then you just boot the partition(OS) you want to keep (in case its the one installed latest) and delete the other partitions (the ones with Ubuntu, if thats the system to get rid of). 

that is however NO GO if its not the distro you've installed last you want to keep, because GRUB is lying on the disk of the last system you've installed. I don't know what to di in this case, but someone in this forum does :)

---

### Post by Duck2006 on 2007-12-24
You may have to reinstall grub again, that the worst that could happen.

---

### Post by patrickaupperle on 2007-12-24
ok thanks
Now ill have to think about which to install first on my new hard drive:lolflag:
re-installing grub? yikes, that will be a tough one if it ever comes up

---

### Post by Saint Angeles on 2007-12-24
> **astral-1 said:**
> 
that is however NO GO if its not the distro you've installed last you want to keep, because GRUB is lying on the disk of the last system you've installed. I don't know what to di in this case, but someone in this forum does :)

just google "super grub disc"

its amazingly useful

---

### Post by patrickaupperle on 2007-12-24
> **Saint Angeles said:**
> just google "super grub disc"

its amazingly useful

wow that does look helpful if i ever need it

bookmarked:KS

---

### Post by zekica on 2007-12-24
if you need to reinstall grub after you have deleted the 'second' distribution (which has grub configuraton etc), you can boot a live disc of either Ubuntu or Mint and in terminal type:
**sudo grub**
**find /boot/grub/stage1**
and then type
**root (hd0,x)**
where x is from previous output
**setup (hd0)**

More info on this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by patrickaupperle on 2007-12-24
What is the user and pass for the linux mint live cd?

---

### Post by mikecomua on 2007-12-24
Honestly, having used Linux Mint for a bit I have realized there is nothing good in it for someone who already has some elementary Ubuntu knowledge. It has a weird menu, a weird theme, and there really is nothing to try there. Trust me:)

---

### Post by patrickaupperle on 2007-12-24
:) ill try the live cd.
some people disagree with you:
[http://ubuntuforums.org/showthread.php?t=448956](http://ubuntuforums.org/showthread.php?t=448956)
:)

---

### Post by rsambuca on 2007-12-24
> **patrickaupperle said:**
> Do I have to dual boot :( or can I just apt-get something like I would if I wanted Kubuntu:KS?:confused::confused:

Oh and one more thing, can these downloads, [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php), be used to make live cds?

Actually, all you have to do is add the Linux Mint repository to your sources list, and edit one file to prioritize the mint repos.  You are then running Mint.  Just add the packages for the Mint Menu, themes, etc. 

To add the Mint Repo to your sources list, use```
gksudo gedit /etc/apt/sources.list
``` and add the following line:

```
deb http://www.linuxmint.com/repository daryna main upstream import
```

You will also want to create an apt preferences file that looks like this (gksudo gedit /etc/apt/preferences):

```
Package: *
Pin: release o=linuxmint
Pin-Priority: 700

Package: *
Pin: release o=Ubuntu
Pin-Priority: 500
```

---

### Post by dpar on 2007-12-24
> **mikecomua said:**
> Honestly, having used Linux Mint for a bit I have realized there is nothing good in it for someone who already has some elementary Ubuntu knowledge. It has a weird menu, a weird theme, and there really is nothing to try there. Trust me:)

Weird?? Well, I guess that is a matter of opinion.
And Mint is a little more than Ubuntu with a different theme. Things work in Mint that haven't worked properly in Gutsy since I installed it.

---

### Post by rsambuca on 2007-12-24
> **dpar said:**
> Weird?? Well, I guess that is a matter of opinion.
And Mint is a little more than Ubuntu with a different theme. Things work in Mint that haven't worked properly in Gutsy since I installed it.

When you say "things work in Mint that haven't worked properly in Gutsy...", can you be more specific?  I am very curious about that.

---

### Post by patrickaupperle on 2007-12-24
> **rsambuca said:**
> Actually, all you have to do is add the Linux Mint repository to your sources list, and edit one file to prioritize the mint repos.  You are then running Mint.  Just add the packages for the Mint Menu, themes, etc. 

To add the Mint Repo to your sources list, use```
gksudo gedit /etc/apt/sources.list
``` and add the following line:

```
deb http://www.linuxmint.com/repository daryna main upstream import
```

You will also want to create an apt preferences file that looks like this (gksudo gedit /etc/apt/preferences):

```
Package: *
Pin: release o=linuxmint
Pin-Priority: 700

Package: *
Pin: release o=Ubuntu
Pin-Priority: 500
```

Can you tell me how to just get the theme?

---

### Post by rsambuca on 2007-12-25
> **patrickaupperle said:**
> Can you tell me how to just get the theme?

Try here:

[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

---

### Post by rkd on 2007-12-25
> **patrickaupperle said:**
> Oh and one more thing, can these downloads, [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php), be used to make live cds?

The Linux Mint site is, as far as I can tell, not at all clear about whether those downloads all are live cds.  Certainly some of them are live cds, because the directions about burning them mention that it creates live cds.  Since they don't talk about any other kind of cds, I think it is a reasonable guess that all those .iso files are live cds, but I can't be certain that is true.

---

### Post by dpar on 2007-12-25
To rsambuca:- Just a couple of things that really bug me that I haven't been able to get any help on-
1) Screensaver won't work no matter what
2)Resolution decides to change from 1024X768 to 1280X1024 randomly. Have to ctl/alt/backspace to get it back.
3)Random gnome setting daemon error on boot
There are others, but those really bug me. I realize everyone has a different setup, but I was just saying that I don't have any of these problems with Mint (which is set up exactly the same)

Anyway, that is for another post. This is patrick's post and I don't want to rob it.:)

---

### Post by patrickaupperle on 2007-12-25
> **rsambuca said:**
> Try here:

[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

I did not see it in there

---

### Post by rsambuca on 2007-12-25
> **patrickaupperle said:**
> I did not see it in there

Did you try the mintdesktop package?

---

