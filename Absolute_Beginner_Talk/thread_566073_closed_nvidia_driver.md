---
title: "closed nvidia driver"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-10-03
Am I right in thinking that if I use closed nvidia drivers and the system upgrades the kernel that ubuntu will no longer be bootable?

---

### Post by bodhi.zazen on 2007-10-03
No.

Ubuntu will boot after a kernel upgrade, but X will fail.

You will need to re-install the Nvidia driver with every kernel upgrade.

After a while it is automatic (on your part) ...

sudo sh NVIDIA-xxxx

---

### Post by skotadi on 2007-10-03
I'm almost sure the system will at least still be bootable.  If you use the nvidia driver provided by the restricted drivers manager in ubuntu (feisty only i believe), everything should work swimmingly.  Currently, that's what I'm using, and the nvidia driver survived kernel updates just fine.  

If something should happen to your nvidia driver, Ubuntu *should* fall back to the VESA driver, allowing you to use your computer pretty much normally -- albeit with lower screen resolution and no graphics acceleration.

Hope that helps :)

edit: I'm using Ubuntu 7.04 feisty -- for older versions without the restricted drivers manager, things are a little more dicey.

---

### Post by ofb on 2007-10-03
I don't think I understand. I started with 6.10 and kernel 2.6.17.1-10 in February. I've had four kernel upgrades to 2.6.20-16, and am now on 7.04, and I've had no trouble with the Nvidia driver. All that ever changed is after the upgrade to 7.04 I had an extra step of turning on the Nvidia driver in the Restricted Driver Manager. Performance wise, the only difference was Refresh was too low until I got the driver enabled.

So, what's this talk about X failing? Sounds scary.

While we're at it, I did a custom install of 7.04 on another machine via the Alternative CD, and it has no Restricted Driver Manager. Is the RDM meant to do anthing other than underline that this is not open software? (and thus /could/ be incompatible with a future kernel, but is not certain to.)

I'm really not expecting any problems that won't be noticed by beta testers. Have I missed a memo?

---

### Post by coolen on 2007-10-03
If you never installed the proprietary driver, you wouldn't have had trouble.
Prior to Fiesty, you had to get the driver from a third party, which meant a kernel upgrade from Ubuntu would break the driver (and thus, X). You'd have to get a new version of the driver compiled for the new kernel.
With Feisty's Restricted Driver Manager, the driver is under Canonical's control, so they'll give you a new driver at the same time as the kernel. The setup goes along seamlessly, and X works just fine.
If there was no hardware that required restricted modules, you wouldn't have gotten the message (I'd think the manage would still be there, but I could be wrong).

If you use the RDM, you'll have no trouble. You can also get Envy for a newer driver, but you will break your X server after an upgrade, and you'll have to run Envy from the console.

Stick with RDM unless you're having troubles with your card. I have a 7600 GS, and it runs just fine with Canonical's offering.

---

### Post by bodhi.zazen on 2007-10-03
> **ofb said:**
> I don't think I understand. I started with 6.10 and kernel 2.6.17.1-10 in February. I've had four kernel upgrades to 2.6.20-16, and am now on 7.04, and I've had no trouble with the Nvidia driver. All that ever changed is after the upgrade to 7.04 I had an extra step of turning on the Nvidia driver in the Restricted Driver Manager. Performance wise, the only difference was Refresh was too low until I got the driver enabled.

So, what's this talk about X failing? Sounds scary.

While we're at it, I did a custom install of 7.04 on another machine via the Alternative CD, and it has no Restricted Driver Manager. Is the RDM meant to do anthing other than underline that this is not open software? (and thus /could/ be incompatible with a future kernel, but is not certain to.)

I'm really not expecting any problems that won't be noticed by beta testers. Have I missed a memo?

There are essentially two nvidia drivers. The "open source" driver, which you have been using (AKA the "nv" driver), and the proprietary driver, maintained by Nvidia (aka "nvidia" driver).

osc1882 is asking about the proprietary driver. coolen explained it very well.

So why would own run the proprietary driver ? Some nvidia cards (like mine) are not supported by the open source drivers.

So if your card works with the open source driver, "nv" driver , stay with it.

If not, with the "nvidia" driver, X fails with each new kernel and you need to re-install it. You get good at it after the 10th time around :)

---

### Post by ofb on 2007-10-03
> **bodhi.zazen said:**
> You get good at it after the 10th time around :)

I'll bet! There's a few things like that already.

Now, which driver do I have? I use the nvidia-glx, "NVIDIA binary XFree86 4.x/X.Org driver"

The Maintainer is 'Ubuntu Kernel Team', but I see one of the dependencies is 'linux-restricted-modules-common'. Also, after the upgrade to 7.04 I had to use the Restricted Driver Manager to enable it.

To configure it under 6.10 and 7.04, I have to use the nvidia-settings panel, which looks distinctly proprietory. Also I have Nvidia logo splash screens on start-up.

Sound like I'm using the proprietary, and I had three kernel upgrades under 6.10 without trouble. Hence I'm a little confused by what I'm reading here, and want to ask about it.

If (big 'if') I've got that right, perhaps the kernel upgrades only break X with some Nvidia cards and not all of them? Both of mine are rather old, though not old enough to use nvidia-glx-legacy. And/or, perhaps the trouble has only been for nvidia-glx-new driver users.

FWIW, a friend has a similar setup (installed in Feb with 6.10, has had the same kernel upgrades, and upgraded to 7.04 at the same time) and a newer Nvidia card. He's had the same experience as me. All that's ever changed is he had to enable the card via the new RDM in 7.04.  I'll have to ask if he uses the '-new' driver, and just which card he has.

So... what do I not get yet? Why are we having different experiences?

---

### Post by coolen on 2007-10-03
You're using the proprietary driver, but you'll not get a kernel upgrade until you can also get a new driver for that kernel.
These upgrades won't break your system, or your X.

Before upgrading to Feisty, did you ever go through a lot of steps to get your card set up? There was no simple GUI configuration prior to Feisty (well, none that would work seamlessly with an upgrade).
When you booted into Feisty for the first time, you'd have experienced the benefit of the RDM, which would inform you of the proprietary driver, and give you the option to install.

---

### Post by bodhi.zazen on 2007-10-03
> **ofb said:**
> I'll bet! There's a few things like that already.

Now, which driver do I have? I use the nvidia-glx, "NVIDIA binary XFree86 4.x/X.Org driver"

The Maintainer is 'Ubuntu Kernel Team', but I see one of the dependencies is 'linux-restricted-modules-common'. Also, after the upgrade to 7.04 I had to use the Restricted Driver Manager to enable it.

That is the open source driver. The propriatry nvidia driver is installed either with the envy script or by downloading the driver directly from nvidia and installing it.

You can confir this by looking in /etc/X11/xorg.conf, under the "Device" section, the open source dirver is "nv"

> <clip>
Section "Device"

    Identifier  "Nvidia card xxx"
    Driver      **"nvidia"**

    BusID       "PCI:01:00:0"
<clip>

> To configure it under 6.10 and 7.04, I have to use the nvidia-settings panel, which looks distinctly proprietary. Also I have Nvidia logo splash screens on start-up.

Sound like I'm using the proprietary, and I had three kernel upgrades under 6.10 without trouble. Hence I'm a little confused by what I'm reading here, and want to ask about it.

If (big 'if') I've got that right, perhaps the kernel upgrades only break X with some Nvidia cards and not all of them? Both of mine are rather old, though not old enough to use nvidia-glx-legacy. And/or, perhaps the trouble has only been for nvidia-glx-new driver users.

FWIW, a friend has a similar setup (installed in Feb with 6.10, has had the same kernel upgrades, and upgraded to 7.04 at the same time) and a newer Nvidia card. He's had the same experience as me. All that's ever changed is he had to enable the card via the new RDM in 7.04.  I'll have to ask if he uses the '-new' driver, and just which card he has.

So... what do I not get yet? Why are we having different experiences?

See this page :

[https://wiki.ubuntu.com/AcceleratedX](https://wiki.ubuntu.com/AcceleratedX)

> The opensource 'nv' driver does not support 3D acceleration or Composite

That is the problem, no commpiz/Beryl unless you use the proprietary driver. Now that may be changing, I do not know as the nv drier does not support my card last time I looked at it ...

So if the open source driver works, \0/

[Nvidia driver](http://www.nvidia.com/object/unix.html)

[Envy](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ofb on 2007-10-03
> **bodhi.zazen said:**
> That is the open source driver. The propriatry nvidia driver is installed either with the envy script or by downloading the driver directly from nvidia and installing it.

You can confir this by looking in /etc/X11/xorg.conf, under the "Device" section, the open source dirver is "nv"

Well..

Box1
	Identifier	"NVIDIA GeForce4 MX-440 SE"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

Box2
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

I have not used the Envy script or downloaded from Nvidia. 

The nvidia-glx driver is installed through Synaptic, and its entry for nvidia-glx has the little Ubuntu logo. Stated in the Synaptic info for this driver: 'To enable the driver, run "sudo nvidia-glx-config enable".'

That's all I've done, except after upgrading to 7.04 I had to enable it in the Restricted Driver Manager.

Compiz/Beryl works, though I didn't care for it.

Package information
[http://packages.ubuntu.com/feisty/x11/nvidia-glx](http://packages.ubuntu.com/feisty/x11/nvidia-glx)
[http://packages.ubuntu.com/edgy/x11/nvidia-glx](http://packages.ubuntu.com/edgy/x11/nvidia-glx)

---

### Post by ofb on 2007-10-03
> **coolen said:**
> Before upgrading to Feisty, did you ever go through a lot of steps to get your card set up? There was no simple GUI configuration prior to Feisty (well, none that would work seamlessly with an upgrade).
When you booted into Feisty for the first time, you'd have experienced the benefit of the RDM, which would inform you of the proprietary driver, and give you the option to install.

Hi, coolen. Sorry I missed you there. -- I don't recall trouble installing the nvida driver under 6.10, and believe it was just as described.

On the second machine, with a custom install of 7.04, I don't have the RDM and I'm kinda curious about that. Does the RDM do anything more than just call attention to the fact that you're using a restricted driver?

---

### Post by osc1882 on 2007-10-04
Ok. So "nvidia-glx" is the name of the open drivers. Does nvidia-glx get auto used as soon as you install or do you have to install it yourself? The only reason why I personally use closed drivers is because nvidia-glx doesn't do crap for me. Nothing 3d works for me using that. While I don't mind reinstalling the closed drivers every time I get a new kernel, I am building xp/ubuntu box for someone in a day or two, so I clearly can't use the closed drivers and having X crash on them. 

Should nvidia-glx work on all newer nvidia cards? Because I want ubuntu to look darn sexy for them so they want to use it. 

And for those about to be upset that it also has xp... I'm just lucky they are willing to have ubuntu installed at all and have a some what open mind about it.

---

### Post by ofb on 2007-10-04
> **osc1882 said:**
> Ok. So "nvidia-glx" is the name of the open drivers.

Well, no. I /don't/ have "nv" in xorg.conf, and I /do/ get the Restricted Driver Manager.

I've got a proprietary driver, and it has not caused trouble through 4 kernel upgrades, three of them in 6.10.

So the situation is a more complicated than first stated, and I'm counting on these smarter gentlemen to sort that for us. 

BTW, 3D works fine for me. Also there's three versions depending on the vintage of the card. You'll have to look into that.

nvidia-glx-legacy
nvidia-glx
nvidia-glx-new

---

### Post by steve.horsley on 2007-10-04
Just to list the driver options again...

1)
The default open-source nvidia driver is known as "nv" and mentioned as such in the /etc/X11/xorg.conf configuration file. This has no 3d acceleration.

2)
The latest proprietary driver has to be downloaded from the nvidia website and then compiled for the kernel it's running on. This driver is konwn as "nvidia" in xorg.conf. The benefit is that it has the latest bug fixes, card support and enhancements. The disadvantage is that every kernel upgrade will cause X to fail to start, and you will have to re-compile the driver using the B&W console that you are left with.

3)
Package nvidia-glx is in the repositories, and is a pre-compiled (but not necessarily most recent) version of 2) the proprietary nvidia driver. This is managed by the Restricted Driver Manager. Because it's in the repository, it gets updated when there's a kernel update so you don't have to fear updates any more.

4)
Package nvidia-glx-new is like 3) but (I guess) with a later version of the nvidia driver, support for more recent cards but less tried-and-tested (maybe less trustworthy?) than nvidia-glx. This one is also updated whenever there's a kernel update.

Hope this helps. 
Personally, I use nvidia-glx-new on my 6600GT and spend far to much time playing UT.
I also love the compiz cube and scale effects.

---

### Post by ofb on 2007-10-04
Thank you!

(try the Serenissima map in Chaos melee mode)

---

### Post by osc1882 on 2007-10-04
steve.horsley  ... I love you. lol
Thank you very much for spelling it out for us. We(I) needed the help.

---

### Post by babacan on 2007-10-04
> **bodhi.zazen said:**
> No.

Ubuntu will boot after a kernel upgrade, but X will fail.

You will need to re-install the Nvidia driver with every kernel upgrade.

After a while it is automatic (on your part) ...

sudo sh NVIDIA-xxxx

is this changing with the new 7.10 ? The only thing I hated was getting X error and had to format ubuntu each time kernel updates :P (I was using Envy to install Nvidia drivers for my 6600

---

### Post by bodhi.zazen on 2007-10-04
> **babacan said:**
> is this changing with the new 7.10 ? The only thing I hated was getting X error and had to format ubuntu each time kernel updates :P (I was using Envy to install Nvidia drivers for my 6600

I hope so.

/bodhi wishes either the open source driver starts working with my card or nvidia goes open source

---

### Post by coolen on 2007-10-04
Nvidia going open source would be awesome, not just for our own user experience, but for the community as a whole. Imagine a major vendor like that open sourcing...
Perhaps gaming vendors will start looking at other open source software, such as, oh, I don't know, a growing little platform by the name of Linux...

---

### Post by coolen on 2007-10-05
As of Feisty, a kernel upgrade will not break your X server.
Also, Envy has a text-based mode (-t option) for such situations. It's not pretty, but it works.

---

### Post by FuturePilot on 2007-10-05
> **coolen said:**
> As of Feisty, a kernel upgrade will not break your X server.
Also, Envy has a text-based mode (-t option) for such situations. It's not pretty, but it works.

The only time a kernel update will break X is if you manually installed the driver or used Envy. If you used the Ubuntu repos X will not break with kernel updates.
But it's easily fixable. Just run Envy from a tty or rerun the Nvidia installer.

---

