---
title: "Suspend, hibernate not working after upgrade to 11.10"
date: 2011-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tcamdg on 2011-10-16
It worked fine in 11.04, but now the screen goes dark (but is still on), and it requires a power-button reset to start up again.

ASUS K52F, full disk encryption (used the alternate install CD for 11.04)
All updates installed

Any ideas what's going on, or how to figure it out and fix it?

Suspend works with [this fix]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"), but doesn't recover from hibernate properly.

WARNING: Don't use the command *sudo apt-get remove pm-utils --purge* suggested by **bd_grover** below, unless you're prepared to fix all the problems to which that command may give rise. You can use the *apt-get **-s*** option to preview the list of everything that will be removed.

---

### Post by 2F4U on 2011-10-16
What are the hardware specs of this machine? There should be a file /var/log/pm-suspend.log, which can be used to do kind of debugging. You get even more information if you set the variable PM_DEBUG to true and start the suspend from the terminal.

---

### Post by tcamdg on 2011-10-16
64-bit Intel® Core™ i3 CPU M 370 @ 2.40GHz × 4
3.7 GB memory
64-bit Ubuntu 11.10
[Link to ASUS web site with specs]("http://www.asus.com/Notebooks/Versatile_Performance/K52F/#specifications")

Last few lines of of pm-suspend.log after PM_DEBUG=1
> Sun Oct 16 12:08:00 EDT 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem

I have to be honest, that PM_DEBUG log file was 2248 lines of nonsense to me. :(  I've attached it to this post.

---

### Post by Chaconne on 2011-10-16
I'm seeing the same problem after I upgrade from Lubuntu 11.04 to 11.10(32bit official release) on my netbook [ASUS EeePC 1005PXD](http://www.asus.com/Eee/Eee_PC/Eee_PC_1005PXD/#specifications). The function was working fine in 11.04, but now I have to select suspend from the power down dialogue.

---

### Post by dfarrell07 on 2011-10-17
I have a similar issue. On a Lenovo W520, I can suspend fine (via laptop lid or GUI), but I cannot wake up from suspend. I get a black (but powered-on) screen, and sometimes I can see and even move my mouse around. So far, I haven't found any solution, or found a bug report about the issue. pm-suspend is attached in .tar and .zip archives. As a .txt file, it exceeded the max upload file size, sry.

---

### Post by bd_grover on 2011-10-20
Hi,

I had same issue when doing this upgrade ...;

But got it working after all by doing:

sudo apt-get remove pm-utils --purge
(the procedure mentioned an error about some folder not being empty and thus not being able to be removed, which I deleted manually after a reboot)

then redid the sudo apt-get install pm-utils

And everything is working again. The only I can't do (was already the case when running v11.04) is run a pm-suspend when the mythtv-backend service is running, the pm-suspend simply returns immediately from the suspend. If I stop service first then no problem in running the pm-suspend.

Regards.

---

### Post by tcamdg on 2011-10-20
> **bd_grover said:**
> Hi,

I had same issue when doing this upgrade ...;

But got it working after all by doing:

sudo apt-get remove pm-utils --purge
(the procedure mentioned an error about some folder not being empty and thus not being able to be removed, which I deleted manually after a reboot)

then redid the sudo apt-get install pm-utils

And everything is working again. The only I can't do (was already the case when running v11.04) is run a pm-suspend when the mythtv-backend service is running, the pm-suspend simply returns immediately from the suspend. If I stop service first then no problem in running the pm-suspend.

Regards.

:^o

> $ sudo apt-get -s remove pm-utils --purge
Purg acpi-support [0.138]
Purg gdm-guest-session [0.27]
Purg gdm [3.0.4-0ubuntu11]
Purg ubuntu-desktop [1.245]
Purg gnome-power-manager [3.2.0-0ubuntu1]
Purg gnome-session [3.2.0-0ubuntu3]
Purg gnome-session-fallback [3.2.0-0ubuntu3]
Purg nautilus-share [0.7.3-1ubuntu1]
Purg gnome-session-bin [3.2.0-0ubuntu3]
Purg indicator-session [0.3.6-0ubuntu2]
Purg upower [0.9.13-1]
Purg pm-utils [1.4.1-8ubuntu1]
There's no way "apt-get install pm-utils" will restore all of those packages. What is this, the new version of "'# rm -rf /' will fix it?"

No thanks.

---

### Post by bd_grover on 2011-10-21
:oops:

Not aware of those dependencies ... The remove pm-utils did indeed remove more then 1 package ... But I am not using gdm, nor gnome.

Only sure thing: solved MY freeze problem when using pm-suspend .... And my box is still running !

---

### Post by Chaconne on 2011-10-24
Hi, bd_grover

This does not seem to work on my netbook.

I removed pm-utils bu purge. Meanwhile 3 other components were uninstalled as well: xcfe-power-manager, upower, lubuntu-desktop. Then I reinstall all these 4 components immediately and the problem persists.

Have you reinstalled other components after you purged pm-utils?

---

### Post by djpemberton on 2011-10-25
Not sure this will help here, but here it is.

My new Asus u46e with ssd wasn't able to boot ubuntu 11.10. boot option "acpi=off" cured that, but caused other problems. Some of those probs included probs with suspend and sleep (didn't try hibernate). After changing that option to "noapic" those problems were solved, leaving only a problem with my fan running.

---

### Post by alextacy on 2011-11-10
For what it is worth, there seems to be a persistent problem with ASUS models & hibernate suspend.

There is a fix here that most people have had success with:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

If anyone does get success with this could they please please return a favour and give me a bit of a walk through, there are a few steps I don't understand (bit of a newbie), I have a new ASUS U41S (its a SE Asian model) and I couldn't get suspend / hibernate working after installing 11.04 (the machine came with Win7 installed) and now after upgrading to 11.10

Cheers

---

### Post by alextacy on 2011-11-10
There is also a solution here that seems to be working

[http://ubuntuforums.org/showthread.php?t=1444822&highlight=hibernate+suspend+problems&page=8](http://ubuntuforums.org/showthread.php?t=1444822&highlight=hibernate+suspend+problems&page=8)

Can anyone tell me where to save the script that I create... sorry I haven't got up to this stage of learning ubuntu.... my ubuntu basics books that I have bought don't cover it either (grrrrr)....

any walk thru help greatly appreciated!

ta A

---

### Post by tcamdg on 2011-11-10
> **alextacy said:**
> For what it is worth, there seems to be a persistent problem with ASUS models & hibernate suspend.

There is a fix here that most people have had success with:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

If anyone does get success with this could they please please return a favour and give me a bit of a walk through, there are a few steps I don't understand (bit of a newbie), I have a new ASUS U41S (its a SE Asian model) and I couldn't get suspend / hibernate working after installing 11.04 (the machine came with Win7 installed) and now after upgrading to 11.10

Cheers
Thanks! Worked for me with "suspend." I'll try out "hibernate" soon and report back.

---

### Post by TheDespot on 2012-02-09
> **bd_grover said:**
> Hi,

I had same issue when doing this upgrade ...;

But got it working after all by doing:

sudo apt-get remove pm-utils --purge
(the procedure mentioned an error about some folder not being empty and thus not being able to be removed, which I deleted manually after a reboot)

then redid the sudo apt-get install pm-utils

And everything is working again. The only I can't do (was already the case when running v11.04) is run a pm-suspend when the mythtv-backend service is running, the pm-suspend simply returns immediately from the suspend. If I stop service first then no problem in running the pm-suspend.

Regards.

This is horrible. Don't do it. 
I gave it a whirl and it completely screwed my entire system. Nothing worked anymore. I couldn't even get Ubuntu to completely boot after. 

Ironically... I reinstalled and all my hibernate and suspend and lid closing, etc., work perfectly now. 
Nonetheless, you screwed me. ... and thanks for fixing my problem.

---

### Post by tcamdg on 2012-02-10
> **TheDespot said:**
> This is horrible. Don't do it. 
I gave it a whirl and it completely screwed my entire system. Nothing worked anymore. I couldn't even get Ubuntu to completely boot after. 

Ironically... I reinstalled and all my hibernate and suspend and lid closing, etc., work perfectly now. 
Nonetheless, you screwed me. ... and thanks for fixing my problem.
For future reference, the ***-s*** option simulates the apt-get command you want to run, without actually making any changes. In fact, I used it earlier to avoid exactly the problem you may have experienced:

*sudo apt-get **-s** remove pm-utils --purge*

---

