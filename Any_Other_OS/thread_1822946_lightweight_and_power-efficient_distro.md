---
title: "lightweight and power-efficient distro"
date: 2011-08-11
forum: Any Other OS
---

### Post by umairalipathan on 2011-08-11
I am working on a project where energy consumption is one of the major issues. What is the most lightweight and power-efficient Linux distro which may have more or less the same application-compatibility as Ubuntu?

---

### Post by XubuRoxMySox on 2011-08-11
I dunno if it's still supported, but there was one designed especially with power consumption in mind called [WattOS]("http://distrowatch.com/table.php?distribution=wattos") using the LXDE desktop and stuff. Looks pretty cool!

-Robin

---

### Post by shobon on 2011-08-11
Gentoo is power-efficient if configured correctly.

But for the most part all distros would be about the same, since power-efficiency is a kernel issue.

---

### Post by NightwishFan on 2011-08-11
> **umairalipathan said:**
> I am working on a project where energy consumption is one of the major issues. What is the most lightweight and power-efficient Linux distro which may have more or less the same application-compatibility as Ubuntu?

Pretty much all of them? Just use a lighter desktop environment. :) Also look into the package laptop-mode-tools.

---

### Post by BrokenKingpin on 2011-08-12
CrunchBang... Debian + Openbox.

Or Lubuntu if you want the distro to be Ubuntu based.

---

### Post by snowpine on 2011-08-13
One option is to stick with Ubuntu and tweak for power efficiency.

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)
[http://www.lesswatts.org](http://www.lesswatts.org)

---

### Post by Kromgol on 2011-08-13
Arch Linux. As efficient as you make it.

---

### Post by NightwishFan on 2011-08-13
> **Kromgol said:**
> Arch Linux. As efficient as you make it.

Arch Linux: You'll know when someone uses it. Beautiful.. functional.. magical.. Arch. It just feels faster.

---

### Post by Plumtreed on 2011-08-13
You could try Fuduntu which has Jupiter included. This is a complete OS yet, with Jupiter, it conserves energy depending on how you use it.

......for something more 'lightweight' look to Peppermint ....and add Jupiter.

---

### Post by NightwishFan on 2011-08-13
> **Plumtreed said:**
> You could try Fuduntu which has Jupiter included. This is a complete OS yet, with Jupiter, it conserves energy depending on how you use it.

......for something more 'lightweight' look to Peppermint ....and add Jupiter.

+1 Fudundu. It has a focus on power-saving and saves the user from doing the tweaks themselves.

---

### Post by XubuRoxMySox on 2011-08-13
> **NightwishFan said:**
> Arch Linux: You'll know when someone uses it.

Because they will tell you.

:D

---

### Post by BrokenKingpin on 2011-08-15
Arch is nice, but I bet it wouldn't save you all that much in terms of power usage. Ubuntu with openbox would probably have the same power usage as Arch + openbox (even if Arch does feel lighter).

---

### Post by drawkcab on 2011-08-15
> **dixiedancer said:**
> I dunno if it's still supported, but there was one designed especially with power consumption in mind called [WattOS]("http://distrowatch.com/table.php?distribution=wattos") using the LXDE desktop and stuff. Looks pretty cool!

-Robin

Coincidentally, WATTOSR4 was just released:

[http://www.planetwatt.com/forums/topic/175/-/view/post_id/735](http://www.planetwatt.com/forums/topic/175/-/view/post_id/735)

---

### Post by umairalipathan on 2011-08-16
Does FUBUNTU has the same application compatibility as UBUNTU?

---

### Post by umairalipathan on 2011-08-16
I just checked the power consumption of wattOS at idle mode. It is consuming the same power as UBUNTU 10.04. I am using a power meter to measure the power consumption of the whole system.

---

### Post by NightwishFan on 2011-08-16
That is what I assumed. ;) Fuduntu should be ok they are all based on Linux.

---

### Post by sanderd17 on 2011-08-16
> **dixiedancer said:**
> Because they will tell you.

:D

Yes we do 

But anyway, in Arch you start from a system with nothing and you have to add your deamons yourself. So you only add the ones necessary. 

But apart from getting rid of heavy stuff, you also have to optimize the kernel for power usage. At least try this here: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)

---

### Post by NightwishFan on 2011-08-16
If you do not mind getting technical. Compile a kernel an ensure you enable:

CONFIG_RCU_FAST_NO_HZ=y
CONFIG_CC_OPTIMIZE_FOR_SIZE=y
DEFAULT_DEADLINE=y
CONFIG_NO_HZ=y
CONFIG_PREEMPT_VOLUNTARY=y
CONFIG_HZ_100=y

If you have an intel cpu enable:
CONFIG_INTEL_IDLE=y

For 64-bit prefer this, but it is not required:
CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=n

---

### Post by unknownPoster on 2011-08-16
> **umairalipathan said:**
> Does FUBUNTU has the same application compatibility as UBUNTU?

*Fuduntu.

As a Fuduntu team member, I can tell you that we do not maintain compatibility with Ubuntu. We maintain compatibility with Fedora.

Check the link in my signature for more information.

---

### Post by ilovelinux33467 on 2011-08-16
+1 for Fuduntu.

---

### Post by fuduntu on 2011-08-16
+1 for Fuduntu ;)

---

### Post by NightwishFan on 2011-08-16
> **fuduntu said:**
> +1 for Fuduntu ;)

Blasphemy! :)

---

### Post by drawkcab on 2011-08-16
> **umairalipathan said:**
> I just checked the power consumption of wattOS at idle mode. It is consuming the same power as UBUNTU 10.04. I am using a power meter to measure the power consumption of the whole system.

Intersting...so WattOS is basically Lubuntu?

---

### Post by fuduntu on 2011-08-16
> **drawkcab said:**
> Intersting...so WattOS is basically Lubuntu?

Most of the distributions tout a "light" window manager as if that's all that is needed to reduce power, but it isn't.  It probably does use a little less under load, if the window manager is very well written, but that doesn't mean that it will give any calculable power savings.

---

### Post by umairalipathan on 2011-08-17
So what should I go for? FUBUNTU or ARCH LINUX? Actually I want to run the applications like OpenCV, FFMPEG etc smoothly, which I have been doing in Ubuntu. Do both of these distros have good compatibility with these?

---

### Post by mips on 2011-08-17
> **umairalipathan said:**
> So what should I go for? FUBUNTU or ARCH LINUX? Actually I want to run the applications like OpenCV, FFMPEG etc smoothly, which I have been doing in Ubuntu. Do both of these distros have good compatibility with these?

Any distro will do as power management is mostly a kernel thing. As far as I'm aware there are regressions wrt power management on the latest kernels but I could be wrong.

Try Fubuntu, Crunchbang, Arch (or Archbang) and decide for yourself. Compatibility with those apps should be fine.

---

### Post by fuduntu on 2011-08-17
> **mips said:**
> Any distro will do as power management is mostly a kernel thing. As far as I'm aware there are regressions wrt power management on the latest kernels but I could be wrong.

Try Fubuntu, Crunchbang, Arch (or Archbang) and decide for yourself. Compatibility with those apps should be fine.

Not exactly, while yes it is a kernel thing, it is not automated except by a few user space apps like my Jupiter applet, or tuned.  Fu[COLOR="Red"]**d**[/COLOR]untu has Jupiter built in.

---

### Post by unknownPoster on 2011-08-17
> **umairalipathan said:**
> So what should I go for? FUBUNTU or ARCH LINUX? Actually I want to run the applications like OpenCV, FFMPEG etc smoothly, which I have been doing in Ubuntu. Do both of these distros have good compatibility with these?

It's Fu**_*d*_**untu. Not Fubuntu.

---

### Post by mips on 2011-08-18
> **fuduntu said:**
> Fu[COLOR="Red"]**d**[/COLOR]untu has Jupiter built in.

I fail to follow the logic. Arch for example comes with nothing, just a base system but that does not mean I can't install jupiter or whatever other pm tools/utils. A simple **packer -S jupiter** will install the applet for me. So how is it any different to being installed by default or me installing it myself?

---

### Post by handy on 2011-08-18
I agree, Arch is like that. You get what you install. Which rarely ever brings problems (though I must admit the most recent upgrade to Openbox is giving me some trouble...).

---

### Post by NightwishFan on 2011-08-18
:)

---

### Post by BrokenKingpin on 2011-08-18
> **handy said:**
> I agree, Arch is like that. You get what you install. Which rarely ever brings problems (though I must admit the most recent upgrade to Openbox is giving me some trouble...).
You can do the same thing with the Ubuntu mini install, or the Debian Net install... a lot of distros offer a way to build you system from the ground up.

---

### Post by cbowman57 on 2011-08-18
> **BrokenKingpin said:**
> You can do the same thing with the Ubuntu mini install, or the Debian Net install... a lot of distros offer a way to build you system from the ground up.

+1, I've become a big fan of the net & minimal install versions.

---

### Post by mips on 2011-08-18
> **BrokenKingpin said:**
> You can do the same thing with the Ubuntu mini install, or the Debian Net install... a lot of distros offer a way to build you system from the ground up.

That was not my point, my point was that any distro can be power efficient and allow you to install applets like jupiter etc. I just used Arch as an example as that is what I use but the same would apply to Debian etc.

---

### Post by handy on 2011-08-18
> **BrokenKingpin said:**
> You can do the same thing with the Ubuntu mini install, or the Debian Net install... a lot of distros offer a way to build you system from the ground up.

I know. 

I personally like the way Arch does it; their style of rolling release suits me, as does the simplicity of the design of the configuration method.

Courses for horses; taste & all that. :)

---

