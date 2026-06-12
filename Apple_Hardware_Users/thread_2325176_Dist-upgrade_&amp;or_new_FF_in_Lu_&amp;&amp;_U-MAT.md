---
title: "Dist-upgrade &amp;/or new FF in Lu &amp;&amp; U-MATE breaks browser??"
date: 2016-05-19
forum: Apple Hardware Users
---

### Post by este.el.paz on 2016-05-19
Folks:

New thread to see if any other PPC folks are having this issue with latest dist-upgrade & FF update?

> OK, the reason I'm posting back here, running Lu 16.04 on an PPC iBook,  and MATE/XFCE 16.04 on a PM ST. . . did a dist-upgrade today, so new  "22" kernel and saw in the list upgrades to FF and T-bird . . . on both  machines after reboot FF window frame loads . . . and then crashes . . .  .  The iBook "doesn't have enough memory to report the problem" . . .  and on the PM . . . apparently the error report was "corrupted" . . . .   Tried to revert to old kernel in the iBook, seemingly failed . . . shut  it down; went to the PM tried there, failed . . . installed Midori to  make this post.  I ran "apt-get -f install" in the iBook . . . nothing  showed up.  No "comment" in the terminal during the upgrade asking any  questions or reporting "problems" . . . FF is kaput!!!!

e...

LP bug report:  [https://bugs.launchpad.net/ubuntu/+bug/1583849](https://bugs.launchpad.net/ubuntu/+bug/1583849)

---

### Post by xeno74 on 2016-05-20
> **este.el.paz said:**
> Folks:

New thread to see if any other PPC folks are having this issue with latest dist-upgrade & FF update?



LP bug report:  [https://bugs.launchpad.net/ubuntu/+bug/1583849](https://bugs.launchpad.net/ubuntu/+bug/1583849)

I haven't updated my ubuntu MATE  for a few days. Jdupuis and Luigi have the same problems with Firefox 46.01. 

Links:

[Ubuntu Mate Updates-Kills Firefox -- forum.hyperion-entertainment]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3448")

[[PPC] (X)(L)ubuntu (MATE) 16.10 testing]("http://ubuntuforums.org/showthread.php?t=2324152&p=13491692#post13491692")

On Debian Sid PowerPC Firefox 47 works and on openSUSE Tumbleweed PPC64, Firefox 46 works as well.

**Firefox 47** on **Debian Sid PPC32**:

[[IMG]https://lh3.googleusercontent.com/-bcv-DdOFT5g/VzANPx4s57I/AAAAAAAAC5Y/6DAKEYeOW9gJMnrFA8oEYwwPUoZfEfTFA/w506-h380/Kernel_4.6-rc7_PowerPC_with_the_new_Firefox_47.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/4WYLwXWAMHh")

**Firefox 46** on **openSUSE Tumbleweed PPC64**:

[[IMG]https://lh3.googleusercontent.com/-byHai5ffhpo/VztkiKNVIZI/AAAAAAAAC-c/m9wMgUMWP08w9QE5KX6kl9hqnmxIiJpaQ/w506-h380/openSUSE_Tumbleweed_PPC64_AmigaONE_X1000.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/MmLq52gd4Ud")

---

### Post by este.el.paz on 2016-05-20
> On Debian Sid PowerPC Firefox 47 works and on openSUSE Tumbleweed PPC64, Firefox 46 works as well.

@xeno74:

Thanks for the info, I like the visual-aids images to graphically illustrate your data . . . very nice.  Unfortunately I don't have Debian or Opensuse loaded anywhere . . . switching to Midori in U-MATE didn't seem to be worth the time it took to do that install, as it also crashed . . . .

In the meanwhile there was actual activity on the LP post . . . seems like this is indeed a known issue . . . suggestion was to "downgrade to FF 44" until the storm blows over . . . .  Might do that, or just forgettaboutit until the next FF package is added to update/upgrade . . . and "test it." : - )

e...

---

### Post by Spectre660 on 2016-05-20
Both Midori and Qupzilla work for me after the update. not Firefox thought. My machine is a Sam460ex

---

### Post by este.el.paz on 2016-05-20
> **Spectre660 said:**
> Both Midori and Qupzilla work for me after the update. not Firefox thought. My machine is a Sam460ex

Cool.  It seemed like Midori was working for me for a few web sites; then when I was trying to post this thread and add a quote . . . whoops . . . down she went.  I didn't see qupzilla listed in synaptic as "available" for my system . . . but looks like for the time being FF is dysfunctional.

e...

[Edit: @spectre660 . . . thanks for the reminder on qupzilla . . . as I mentioned, it didn't show up in the list of "browsers" but searching for it directly on synaptic it was there.  And things were working fine until I tried to log into this forum to reply, and I couldn't get the cursor to show up in the Ubuntu log in window . . . so I ran update/upgrade and in there were three "python" packages of some type . . . when I came back to the login . . . there was a cursor, so . . . perhaps Qupzilla will be the browser . . . ???  Thanks though.]

[Edit2:  Possibly spoke too soon, clicked on a friend's post on FB, tried to type a comment, and back to the no cursor in the field thingie . . . .]

---

### Post by este.el.paz on 2016-05-27
> **este.el.paz said:**
> Folks:

New thread to see if any other PPC folks are having this issue with latest dist-upgrade & FF update?



LP bug report:  [https://bugs.launchpad.net/ubuntu/+bug/1583849](https://bugs.launchpad.net/ubuntu/+bug/1583849)

et al:

As of a couple of days ago this bug was marked as "confirmed--effects multiple users" on LP . . . as of a few minutes ago, nothing "fresh" in "upgrades" for Firefox . . . typing this in Qupzilla . . . which is working despite the "This version of safari is no longer supported" in various web sites, like Gmail . . . .

e...

---

### Post by luigiburdo on 2016-05-29
Here on X5000 Midori and Qupzilla are working but ... all websites who have a video make me a crash (youtube,facebook,photobuket etc etc)
I hope firefox will fixed soon ... is really boring situation. 
The best was have the old 4.5 because firefox is buggy but most compatible and modern browser.

Lastest midori and qupzilla need qt 5 up for run and are not all ported on ppc hw

---

### Post by este.el.paz on 2016-05-29
> **luigiburdo said:**
> Here on X5000 Midori and Qupzilla are working but ... all websites who have a video make me a crash (youtube,facebook,photobuket etc etc)
I hope firefox will fixed soon ... is really boring situation. 
The best was have the old 4.5 because firefox is buggy but most compatible and modern browser.

Lastest midori and qupzilla need qt 5 up for run and are not all ported on ppc hw

@LB:

Thanks for your post . . . did you try to add your name to my LP bug report, or there are some others that I guess you could register your issues with?  Perhaps the more people who add their names, the "faster" something might happen . . . .  : - 0  But, agreed on the "really boring situation" . . . hard to "win" for all the "losing" . . . .  

What is the "old 4.5" that you are referring to?  Kernel? or FF version??

e...

[What's sort of amusing is that the LP devs have marked this bug's "importance" level as "medium" . . . .]

---

### Post by luigiburdo on 2016-05-31
Hi Este,
this bug is now really know by firefox devs ...but after yesterday i understand it effect only  the ppc 32 distros (like is mate,lub). this because on fedora 24 full ppc 64 distro firefox 46.1 is not crashing. I been tested it on my hw and i was browsing without crashes

---

### Post by xeno74 on 2016-06-01
> **luigiburdo said:**
> Hi Este,
this bug is now really know by firefox devs ...but after yesterday i understand it effect only  the ppc 32 distros (like is mate,lub). this because on fedora 24 full ppc 64 distro firefox 46.1 is not crashing. I been tested it on my hw and i was browsing without crashes

Firefox 47 works on Debian Sid PPC32. ;-)

FYI: Firefox **47.0b5** is available for _Debian Sid_ PPC32.

Further information: [packages.debian.org](https://packages.debian.org/de/experimental/powerpc/firefox/download)

[[img]https://lh3.googleusercontent.com/-f1xlId06oRQ/V066sLa5GGI/AAAAAAAADDg/Mbt_ZEkpayEUhfTQRvTlmY-cPZ9BLogaQ/w506-h380/Firefox_47.0b5_Debian_PowerPC.png[/img]](https://plus.google.com/115515624056477014971/posts/7cHF5cziXVA)

---

### Post by luigiburdo on 2016-06-01
i will try to install the deb on ubuntu hope will start browse on ubuntu soon because midori and qupzilla are really unstable if found a website with a video

---

### Post by xeno74 on 2016-06-03
Firefox **47.0** is available for ubuntu MATE 16.10 PowerPC :-)&#65279;

[[img]https://lh3.googleusercontent.com/-4lohCcDCvMI/V1HXeRwpXvI/AAAAAAAADGo/gcRw5u4goT0SDHxSsG_KWgjiMBADrMI-g/w506-h380/Firefox_47.0_ubuntu_MATE_16.10_PowerPC.png[/img]](https://plus.google.com/115515624056477014971/posts/jU4Li5yyBeE)

---

### Post by xeno74 on 2016-06-09
**Firefox 47** is also available for **ubuntu MATE 16.04 LTS** PowerPC. :-)&#65279;

[[img]https://lh3.googleusercontent.com/-eWfMfquhOSs/V1m5zVjxTgI/AAAAAAAADHg/V6_okKkM7R8nO0nkT6t9NgTes3ZS9PJ6w/w506-h380/Firefox_47_ubuntu_MATE_16.04_LTS_PowerPC.png[/img]](https://plus.google.com/115515624056477014971/posts/YT7NgE3whru)

---

### Post by este.el.paz on 2016-06-10
@zeno74:

Thanks for the head's up . . . I had just checked that the day before and it wasn't in the tubes . . . .  Seems to be once again working . . . .

e..

---

### Post by rican-linux on 2016-06-10
FF46 is broken on Gentoo as well. I am unning it on my PM G5 and PB G4. Could somone with the issue launch FF in the terminal and post the results? I wondering if it is the same issue...

---

### Post by este.el.paz on 2016-06-11
@r-l:

Hey bud, so you are playing with Gentoo these days?  This shouldn't be an issue anymore, as of yesterday using apt there was a new kernel and an upgrade for FF . . . 47??  It's working, it still takes a couple minutes to launch, literally . . . and it still takes awhile to load the "restore" pages . . . perhaps such is life in 32 bit . . . but, it's working . . . .  Should be in the repos???

If there is something that needs checking later today perhaps I could do something, but we should be moving on to the next issue in our "testing" of 16.04????  : - )

e

---

