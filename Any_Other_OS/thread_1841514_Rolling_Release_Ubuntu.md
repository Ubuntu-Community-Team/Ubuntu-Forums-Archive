---
title: "Rolling Release Ubuntu"
date: 2011-09-09
forum: Any Other OS
---

### Post by Dlambert on 2011-09-09
I really like the "rolling release" ideal, the install once and done. I am interested in starting a project that turns ubuntu into a rolling release distribution, yes I know you can "upgrade Ubuntu" but I'd prefer an automatically updated Ubuntu. (with updates coming from the alpha/beta of the next release. (with stability a top priority). I Know I would have to set up a server and Repository to Install the updated packages automatically with the update manager. Let me know if there is interest in this Idea. I'd love a rolling Ubuntu. The features of ubuntu, but always up to date. (I think an Ubuntu logo built to resemble the Arch logo would be sweet) ):P

---

### Post by mips on 2011-09-09
Not to rain on your parade but what you are proposing would be extremely difficult if not impossible. Have a look at how the ubuntu releases are developed and think about it again.

You would be better off doing a distro based on debian testing.

---

### Post by BrokenKingpin on 2011-09-09
> **mips said:**
> Not to rain on your parade but what you are proposing would be extremely difficult if not impossible. Have a look at how the ubuntu releases are developed and think about it again.

You would be better off doing a distro based on debian testing.
++

You could look into Linux Mint Debian Edition, which is based on Debian Testing, and they are trying to make it as easy to use as Ubuntu. I don't think they are there yet, but it is coming along pretty good.

---

### Post by Dlambert on 2011-09-09
> **BrokenKingpin said:**
> ++

You could look into Linux Mint Debian Edition, which is based on Debian Testing, and they are trying to make it as easy to use as Ubuntu. I don't think they are there yet, but it is coming along pretty good.

I know! I use LMDE , i just miss some of ubuntus feAtures

---

### Post by handy on 2011-09-10
I saw some video footage of a one of the Ubuntu big wigs speaking at a meeting of Ubuntu big wigs sometime inside of the last couple of years. (Yes I surely do wish I had of bookmarked it!) & he was talking about the possibility of Ubuntu adopting a rolling release upgrade system.

So from what I saw, I can say that the powers that be have/are looking at the pro's & con's of a rolling release Ubuntu. 

Whether it ever materialises or not time will tell.

If it does, I expect that there will be various ways to maintain the different primary clients:- Server systems & those that require LTS would just choose to enable the appropriate repositories, as opposed to those that want to use more recent packages...

---

### Post by Dlambert on 2011-09-10
Ok, so if I can't have a rolling realse Ubuntu (yet) What repos can I add to have the latest kernel, Xorg/wayland(eventually) and Gnome 3 etc. From the 11.10 Alpha

---

### Post by 2F4U on 2011-09-10
Wouldn't it be easier to upgrade to 11.10 rather than just adding some repositories? I guess you could avoid a lot of dependency problems if you completely switch to 11.10.

---

### Post by Dlambert on 2011-09-10
> **2F4U said:**
> Wouldn't it be easier to upgrade to 11.10 rather than just adding some repositories? I guess you could avoid a lot of dependency problems if you completely switch to 11.10.
Anyway to do this from 11.04?

---

### Post by 2F4U on 2011-09-10
Of course. Here are the steps:

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha1)

---

### Post by handy on 2011-09-10
You can also easily upgrade your kernel & other packages beyond Ubuntu "stable", have a look at the Ubuntu stuff: section of the OP in this thread:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by mips on 2011-09-10
> **handy said:**
> I saw some video footage of a one of the Ubuntu big wigs speaking at a meeting of Ubuntu big wigs sometime inside of the last couple of years. (Yes I surely do wish I had of bookmarked it!) & he was talking about the possibility of Ubuntu adopting a rolling release upgrade system.


Recent talk,
[http://ubuntuforums.org/showthread.php?p=11235156](http://ubuntuforums.org/showthread.php?p=11235156)
[http://netsplit.com/2011/09/08/new-ubuntu-release-process/](http://netsplit.com/2011/09/08/new-ubuntu-release-process/)
[http://www.phoronix.com/scan.php?page=news_item&px=OTg5MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTg5MQ)
[http://www.omgubuntu.co.uk/2010/11/ubuntu-to-become-a-rolling-release-distro/](http://www.omgubuntu.co.uk/2010/11/ubuntu-to-become-a-rolling-release-distro/)
[http://www.theregister.co.uk/2010/11/23/darily_ubuntu_updates/](http://www.theregister.co.uk/2010/11/23/darily_ubuntu_updates/)
[http://theravingrick.blogspot.com/2010/11/ubuntu-is-not-moving-to-rolling-release.html](http://theravingrick.blogspot.com/2010/11/ubuntu-is-not-moving-to-rolling-release.html)

That video you saw was probably from the Ubuntu 10.10 conference so maybe have a look and see if you can find it.

---

### Post by handy on 2011-09-11
I had a bit of a search but couldn't find the video on Youtube. 

I'm currently downloading Marks keynote address to the 10.10 UDS. Perhaps that is it? 

Thanks for posting those links.

It looks like nothing is going to change, so Ubuntu will continue to become more unstable with projects/features being added to it before they are ready for public release.

Which is a shame that, as it is costing Ubuntu, users. It seems that the problem will keep snowballing until Canonical decide that they must make changes to their release cycle so as to assure the Ubuntu users of a stable release.

---

### Post by handy on 2011-09-11
I watched Mark Shuttleworth's keynote speech at the Ubuntu Maverick Meerkat 10.10 Developer Summit (UDS) (May 10, 2010):

[http://www.archive.org/details/Mark_Shuttleworth_Keynote_Maverick_Meerkat_10.10_Ubuntu_Developer_Summit](http://www.archive.org/details/Mark_Shuttleworth_Keynote_Maverick_Meerkat_10.10_Ubuntu_Developer_Summit)

There was no mention of rolling release, but plenty on Unity & related. It is something that many who post in the Unity Mega thread would do well to watch I think...

---

### Post by Dlambert on 2011-09-11
Interesting

---

### Post by Dlambert on 2011-09-12
How about, if you modified ubuntu to automatically update to the latest (beta/alpha) version updates?

---

### Post by Dlambert on 2011-09-16
bump

---

### Post by mips on 2011-09-17
You will most likely have dependency issues.

---

### Post by amjjawad on 2011-09-17
I'm not an expert in such projects/stuff but if I were you, I would choose another base for my project which is a Rolling Release Distribution, study it, start some tests and try to build my own distribution based on that OS. Once done successfully, I might try the same with Ubuntu.

I wanted to start a project based on SliTaz but then I realized it's too early for me so I then decided to join LXDE and Lubuntu Team and get involved more and more. I thought it's better to be involved in a current project than start my own. I still need to learn more and LXDE Project is very very interesting and promising at least for me.

Just thought to share this with you :)

Good luck!

---

### Post by PendragonUK on 2011-09-17
My experiences of using a rolling release for an extended time is it's great until the distro needs to make a change that can't be upgraded to. It can trap the distro in to a blind ally. I ran PCLinuxOS for several years and all was well most of the time. However from time to time something would happen that would cause a major break. The disro would want or need to change tack and would want to "roll" in a direction it couldn't this would cause problems.

My suggestion would be for Ubuntu to "Roll" from LTS to LTS. So an LTS would be released every two years. The user would have to choice to stick or Roll. The people needing the stable and predictable LTS would "Stick" but the more adventurous users would "Roll" but only for the two years until the next LTS. Then at LTS time you would go thorough the Distro upgrade. To start Rolling again.

There could be different levels of "Roll" with a 'bleeding edge Roll' or a more 'Stable Roll' But the people that need predictable stability can stick with the LTS.

---

### Post by NightwishFan on 2011-09-17
You mean become Debian? :confused:

---

### Post by Dlambert on 2011-09-17
With the polish of ubuntu, and features. yes. LMDE comes close

---

