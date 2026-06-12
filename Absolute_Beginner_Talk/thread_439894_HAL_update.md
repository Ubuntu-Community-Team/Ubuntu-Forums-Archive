---
title: "HAL update"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-05-11
So Ubuntu provided me some new updates, but failed to let me update HAL to the newest version. I went into Synaptic to see if I could do it from there and all I get is this message...I'd like to keep my computer updated, so can anyone help me out?

the message:

hal:
 Depends: hal-info (>=20070402) but it is not installable

---

### Post by chek2fire on 2007-05-11
dont worry they will fix it soon.i have the same problem

---

### Post by brazzmonkey on 2007-05-11
could that lead to other troubles ?

---

### Post by PartisanEntity on 2007-05-11
Same issue here, just wondering, will restarting lead to any issues before hal is installed?

---

### Post by brazzmonkey on 2007-05-11
this is exactely my concern...

---

### Post by brazzmonkey on 2007-05-11
now fixed ;)

---

### Post by isaacj87 on 2007-05-11
thanks guys! it's good to know I wasn't the only one with the problem.

---

### Post by isaacj87 on 2007-05-11
fixed? I'm still unable to update...:confused:

---

### Post by carlosqueso on 2007-05-11
> **isaacj87 said:**
> fixed? I'm still unable to update...:confused:

I don't know if this helps, but if you are using apt-get, you need to use:

```
sudo apt-get dist-upgrade
```

---

### Post by isaacj87 on 2007-05-11
hmmm...thanks but that didn't help either...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  hal
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


that's what happened...

---

### Post by PartisanEntity on 2007-05-11
> **isaacj87 said:**
> hmmm...thanks but that didn't help either...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  hal
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


that's what happened...

Open up Synaptic, click on Reload and then you will be able to install the hal update.

---

### Post by isaacj87 on 2007-05-11
It worked! thanks for the tip!

---

### Post by talikarng on 2007-05-11
When I get the option to update HAL using update manager I get warned that the packages are not authenticated. Should I hold off for a while?

---

### Post by netsoul on 2007-05-12
Hi guys,

Yesterday, I installed all updates suggested by the update manager and HAL was among it.  Now, when I try to boot GNOM I got this message: "Failed to initialize HAL"  So my WiFI on the laptop doesn't work as minimum.

I don't know if all this is interrelated but it looks like that.

Do you know how to fix that problem?

Thanks.

---

### Post by bsantos on 2007-05-13
The backlight control doesn't work anymore with g-p-m since this update too. It works with pommed (i wasn't using it but installed to test this) but GNOME can't access it. g-p-m doesn't show brightness control and the brightness applet complaints with 'cannot get laptop panel brightness'.

Can it be related to this also?

---

### Post by Technogenius on 2007-05-14
Yeah, I had the same problem until I did that command. And no, rebooting will not change anything. The update notifier will pop up again when you restart.

---

### Post by monokom on 2007-05-15
apt-get dist-upgrade
This is the solution.

---

### Post by netsoul on 2007-05-15
> **monokom said:**
> apt-get dist-upgrade
This is the solution.

What's the use of this command if my network adapters disappeared and I have no Internet connection now?

---

### Post by introspectif on 2007-05-18
> **PartisanEntity said:**
> Open up Synaptic, click on Reload and then you will be able to install the hal update.

That totally worked for me! Thanks :)

But I am curious, why did this work? What was lacking in doing a ```
sudo apt-get upgrade
```?

---

### Post by PartisanEntity on 2007-05-18
> **introspectif said:**
> That totally worked for me! Thanks :)

But I am curious, why did this work? What was lacking in doing a ```
sudo apt-get upgrade
```?

It should be: sudo apt-get **update**
But explaining to someone how to do it through Synaptic seemed easier at the time.

---

### Post by introspectif on 2007-05-18
Oh, I did that too, of course. It just didn't work when i did a ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mendingo84 on 2007-05-18
same here with "sudo apt-get update && sudo apt-get upgrade".
worked though with "sudo apt-get dist-upgrade"

---

