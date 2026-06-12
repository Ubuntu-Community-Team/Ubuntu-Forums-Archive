---
title: "Comparison and Review of Xubuntu vs. Manjaro (Arch)(Xfce) on a Netbook"
date: 2013-01-13
forum: Any Other OS
---

### Post by Dlambert on 2013-01-13
**Story:** My mother works at a pawn shop, and therefore she gets a discount. And when my laptop failed (HDD) I needed something to do school work on before buying my college laptop, so I bought a netbook for $30. Yes I realized I could just buy a new HDD, but my laptop was falling apart anyways. This brought up the question, which OS to run on it? I was going to try Lubuntu (for the first time), but seeing as 12.10 wasn't out yet I decided to go with Xubuntu. That's what brought me to this point.



**Test Bench**:
HP Mini 110-3510NR
Dual Core 1.66GHz Intel Atom CPU N455
Intel Graphics Media Accelerator 3150
1GB DDR3 Ram (will upgrade to 2GB)
250GB HDD
Dell/Broadcom BCM4313 Wireless

And I think that's everything relevant.

**_NOTE: Same kernel was in use in Both OSes_**



**Experience:** 

Being a netbook, I didn't expect much at all so I started out with the default Xubuntu 12.10 install. From there I went on to install all the codecs and other proprietary software ubuntu doesn't carry by default so I could watch movies,etc. 

**Problem #1:** Vlc in xubuntu couldn't handle video playback very well, with tearing and lag. I just thought this was the netbook's power limits, so I thought nothing of it. I was able to fix this however by enabling GPU-accelerated play back and changing "Skip H.264 in-loop deblocking filter" to all, which improved playback dramatically. Problem solved. I even disabled Compositing  in the window manager settings.

I couldn't tell if this was a VLC issue or an X-org issue, or just my netbook so since I figured out a solution, I dropped the idea.

**Problem #2:** Flash player playback is terrible. I can't run 1080p (to be expected), but even the lower resolutions struggled to play smoothly on a 10Meg down connection. Again, I just figured this was one of the joys of netbook ownership so I didn't think much about it. I was able to slightly fix this by increasing the amount of memory flash was allowed to store. Problem slightly solved.

From there Xubuntu was a breeze with easy to install software and updates.

The responsiveness of Xubuntu was excellent considering that I was on a netbook, and to improve this further I installed the Readahead package.



**The question:** How well would manjaro perform?

Being perfectly happy with my setup, I decided on a whim to install Manjaro (my desktop distro) on this netbook.


So I downloaded the latest 0.8.3 Xfce edition of manjaro and installed it. Right out of the box I noticed that the boot time was lesser than that of xubuntu, which makes sense due to the decreased amount of packages installed by default. Point Manjaro. 

I installed the same software (VLC) and started to playback the same movies, and to my surprise they played flawlessly out of the box. I didn't have to modify any settings in VLC or the window manager. So now my 720p + videos were running with Gpu-accelerated processing on the highest settings flawlessly under manjaro. Whether it be newer version of VLC, x-org, or GPU drivers the point still goes to manjaro.

After that I tried flash playback, and to my surprise flash was more fluid under manjaro. I still couldn't get 1080/720p, but point manjaro.

**Installation of packages:** Pacman took a little to get used to when I first started working with it, and compared to the ubuntu software center and it's GUI it still can't quite match it. Point Xubuntu.

**Availability of software:** Being built on-top of the most popular linux flavor, xubuntu has more commercial support and in general terms more readily install-able applications. But Arch linux, which is what manjaro is built on, has many more packages. The Arch user repository is filled with a ton of software that is A) not avaliable in the default arch repositories or B) have been ported over to arch. I was able to find Google chrome in the AUR, just like I was able to install it in ubuntu through a PPA. In overall terms, this one ends in a draw.

**Gaming support:** By default Steam was designed for Ubuntu, therefore it works in Xubuntu. But the developers of Manjaro had it up and running on arch in no time. But the ultimate factor in this debate is that Ubuntu has the ubuntu software center and it's GUI that features many commercial games with one-click installs. Point Xubuntu, not that I'll be doing much gaming on my netbook.

**User base and support:** Not surprisingly, Ubuntu has a greater user base then arch and therefore manjaro as well as more users online participating in forums. But since arch is more advanced than ubuntu, the users online are likely more knowledgeable in getting the answer to any problems I may have. Draw.

**Software updates:** Both manjaro and Xubuntu feature automatically scanning update notifier systems, but manjaro has the latest stable version as permitted by their package over-viewers. Which in some cases is a version or two ahead of Xubuntu. Also, manjaro linux is rolling release which means I wont have to worry about updating every 6 months. Point manjaro.

**Boot time:** On a netbook without an SSD, boot-time isn't a huge issue, but by default manjaro beat Xubuntu by several seconds. Point Manjaro.

**Security:** One thing that I was sad not to see in the manjaro installer (by default? I just used the standard stable installer) was the ability to encrypt the home folder as well as locking the drive at boot. Not an issue for a standard user, but I'm a bit of a nutcase. Point Xubuntu. 

**Ease of use:** Both run Xfce, but both were very familiar in that aspect on my netbook. Draw.

**Speed:** By default manjaro felt more responsive and quicker on my netbook compared to Xubuntu. Point Manjaro.

When it comes down to it, it's personal preference. The arguement could be made that arch linux is lighter than manjaro, but I was purely looking at two pre-configured distributions. 

**Score:** 5 to 3 Manjaro


And with my findings, Manjaro was a better fit for me and my netbook. Its media playback slaughtered xubuntu, whether it be because of a software issue, the victory still goes to Manjaro. 

**Conclusions:** I believe Manjaro should be included in the "light" linux category along with Lubuntu and xubuntu and many more.So, whether you want a fast little netbook, or want to bring new life to an old machine, Manjaro will certainly do the job. :KS

[http://www.manjaro.org](http://www.manjaro.org)

Thank you for reading, and feel free to teach me something new! -Dlambert

---

### Post by mamamia88 on 2013-01-13
> **Dlambert said:**
> **Story:** My mother works at a pawn shop, and therefore she gets a discount. And when my laptop failed (HDD) I needed something to do school work on before buying my college laptop, so I bought a netbook for $30. Yes I realized I could just buy a new HDD, but my laptop was falling apart anyways. This brought up the question, which OS to run on it? I was going to try Lubuntu (for the first time), but seeing as 12.10 wasn't out yet I decided to go with Xubuntu. That's what brought me to this point.



**Test Bench**:
HP Mini 110-3510NR
Dual Core 1.66GHz Intel Atom CPU N455
Intel Graphics Media Accelerator 3150
1GB DDR3 Ram (will upgrade to 2GB)
250GB HDD
Dell/Broadcom BCM4313 Wireless

And I think that's everything relevant.

**_NOTE: Same kernel was in use in Both OSes_**



**Experience:** 

Being a netbook, I didn't expect much at all so I started out with the default Xubuntu 12.10 install. From there I went on to install all the codecs and other proprietary software ubuntu doesn't carry by default so I could watch movies,etc. 

**Problem #1:** Vlc in xubuntu couldn't handle video playback very well, with tearing and lag. I just thought this was the netbook's power limits, so I thought nothing of it. I was able to fix this however by enabling GPU-accelerated play back and changing "Skip H.264 in-loop deblocking filter" to all, which improved playback dramatically. Problem solved. I even disabled Compositing  in the window manager settings.

I couldn't tell if this was a VLC issue or an X-org issue, or just my netbook so since I figured out a solution, I dropped the idea.

**Problem #2:** Flash player playback is terrible. I can't run 1080p (to be expected), but even the lower resolutions struggled to play smoothly on a 10Meg down connection. Again, I just figured this was one of the joys of netbook ownership so I didn't think much about it. I was able to slightly fix this by increasing the amount of memory flash was allowed to store. Problem slightly solved.

From there Xubuntu was a breeze with easy to install software and updates.

The responsiveness of Xubuntu was excellent considering that I was on a netbook, and to improve this further I installed the Readahead package.



**The question:** How well would manjaro perform?

Being perfectly happy with my setup, I decided on a whim to install Manjaro (my desktop distro) on this netbook.


So I downloaded the latest 0.8.3 Xfce edition of manjaro and installed it. Right out of the box I noticed that the boot time was lesser than that of xubuntu, which makes sense due to the decreased amount of packages installed by default. Point Manjaro. 

I installed the same software (VLC) and started to playback the same movies, and to my surprise they played flawlessly out of the box. I didn't have to modify any settings in VLC or the window manager. So now my 720p + videos were running with Gpu-accelerated processing on the highest settings flawlessly under manjaro. Whether it be newer version of VLC, x-org, or GPU drivers the point still goes to manjaro.

After that I tried flash playback, and to my surprise flash was more fluid under manjaro. I still couldn't get 1080/720p, but point manjaro.

**Installation of packages:** Pacman took a little to get used to when I first started working with it, and compared to the ubuntu software center and it's GUI it still can't quite match it. Point Xubuntu.

**Availability of software:** Being built on-top of the most popular linux flavor, xubuntu has more commercial support and in general terms more readily install-able applications. But Arch linux, which is what manjaro is built on, has many more packages. The Arch user repository is filled with a ton of software that is A) not avaliable in the default arch repositories or B) have been ported over to arch. I was able to find Google chrome in the AUR, just like I was able to install it in ubuntu through a PPA. In overall terms, this one ends in a draw.

**Gaming support:** By default Steam was designed for Ubuntu, therefore it works in Xubuntu. But the developers of Manjaro had it up and running on arch in no time. But the ultimate factor in this debate is that Ubuntu has the ubuntu software center and it's GUI that features many commercial games with one-click installs. Point Xubuntu, not that I'll be doing much gaming on my netbook.

**User base and support:** Not surprisingly, Ubuntu has a greater user base then arch and therefore manjaro as well as more users online participating in forums. But since arch is more advanced than ubuntu, the users online are likely more knowledgeable in getting the answer to any problems I may have. Draw.

**Software updates:** Both manjaro and Xubuntu feature automatically scanning update notifier systems, but manjaro has the latest stable version as permitted by their package over-viewers. Which in some cases is a version or two ahead of Xubuntu. Also, manjaro linux is rolling release which means I wont have to worry about updating every 6 months. Point manjaro.

**Boot time:** On a netbook without an SSD, boot-time isn't a huge issue, but by default manjaro beat Xubuntu by several seconds. Point Manjaro.

**Security:** One thing that I was sad not to see in the manjaro installer (by default? I just used the standard stable installer) was the ability to encrypt the home folder as well as locking the drive at boot. Not an issue for a standard user, but I'm a bit of a nutcase. Point Xubuntu. 

**Ease of use:** Both run Xfce, but both were very familiar in that aspect on my netbook. Draw.

**Speed:** By default manjaro felt more responsive and quicker on my netbook compared to Xubuntu. Point Manjaro.

When it comes down to it, it's personal preference. The arguement could be made that arch linux is lighter than manjaro, but I was purely looking at two pre-configured distributions. 

**Score:** 5 to 3 Manjaro


And with my findings, Manjaro was a better fit for me and my netbook. Its media playback slaughtered xubuntu, whether it be because of a software issue, the victory still goes to Manjaro. 

**Conclusions:** I believe Manjaro should be included in the "light" linux category along with Lubuntu and xubuntu and many more.So, whether you want a fast little netbook, or want to bring new life to an old machine, Manjaro will certainly do the job. :KS

[http://www.manjaro.org](http://www.manjaro.org)

Thank you for reading, and feel free to teach me something new! -DlambertI have arch with xfce on my netbook and i love it.  I doubled the ram to 2gb and installed an ssd recently.  Everything is snappy.  I don't watch much video on it though since i prefer to do all my video watching on a tv.   For youtube i highly reccomend an app called minitube.   Works for most videos and is much better than flash.  As far as availability of apps they are pretty much equal.   But for a netbook i would probably want to use a ppa instead of the AUR because a ppa provides a preconfigured package which is quicker than the AUR which builds from source. Pacman vs apt is kind of a wash for me. Pacman gets the nod slighly because it doesn't install optional dependencies without me asking.  Personally if i was reccomending a distro to a non control freak i would suggest xubuntu and remove the stuff you don't use.  That being said if you want to learn linux than dive into it.   If you do run into trouble it will probably be easier to fix a problem because A) you built the system from the ground up and learned a lot in the process B) the documention has no rival and C) the community is slighly more techincally minded so you are more likely to get a good response if you ask a good question and provide relevant info.

---

### Post by Dlambert on 2013-01-13
I use MiniTube! ;)

---

### Post by SpaceAviator on 2013-01-13
As someone on the Manjaro team, thanks for the review! :)

---

