---
title: "Pommed and backlight in intrepid"
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by lv1001 on 2008-11-01
Hi,
I am a bit confused about pommed and display backlight on my macbook pro 3,1 using intrepid.

The hotkeys do nothing, which I had read about in various other threads (dim backlight is mapped to "XF86Stop" according to xev).
Other threads also discussed this giving the solution not to use pommed but gnome-power-manager, wich I obviouslly can not do with kubuntu.
Kde power manager does not manage to change the backlight in any way.
So I came back to try pommed.
I CAN CHANGE the backlight by unplugging power and even by changing the "init" value in /etc/pommed.conf and restart pommed ("/etc/init.d/pommed restart") but this seems to me a bit fiddly.
I tried xbacklight but always get "No outputs have backlight property".
How does pommed manage to change backlight? Can I do the same manually? Is there a way to repair pommed's broken hotkey mapping? Does kde offer a way I did not realize yet?

Thanks
  LV

---

### Post by kosumi68 on 2008-11-01
lv1001,

From what I gather, the community is moving towards the use of Xorg XRandR, which has support for a broad range of graphics cards, backed up by kernel support. Both the gnome-power-manager and xbacklight use XRandR.

As for pommed, much of its code seems to have been incorporated into this effort.

Your model has nvidia graphics, has it not? Then there is a kernel module mbp_nvidia_bl to add to /etc/modules. This just might make xbacklight work.

---

### Post by hanzomon4 on 2008-11-01
and uninstall pommed no longer needed

---

### Post by lv1001 on 2008-11-02
Thanks for your hints.
As I had put it before, I had gone back to pommed because kde power manager did not work and after that already did the things stated in other posts (modify 10-macbookpro-utils.fdi, modprobe for mbp_nvidia_bl).
Apparently I missed to check that kde power manager works after these steps just like gnome power manager does.
I still can not set backlight via xbacklight but don't bother anymore.
Nevertheless the hotkeys do not work wich is not that big a problem for me up to now.

Again, thanks for your effort,
  LV

---

### Post by MichaelSwengel on 2008-11-02
Hey, lv1001

I know you're frustrated...It can be annoying. I've been there....

Try this...

open up a Terminal and type:

```
sudo gedit /etc/modules
```

Type your password, and GEdit will open the Modules text file.

At the very END of this file add the following:

```
mbp_nvidia_bl
```

SAVE the file and reboot your computer. Let us know if this works for you so we can help you further if needed.

Regards,
MS

---

### Post by MichaelSwengel on 2008-11-02
Sorry - should have read that you did this already. xD

If you haven't already, use Synaptic Package Manager to make sure that you have xbacklight installed...

Either way, the following post from kosumi68 was helpful to me:

> 
1. pommed is not needed, deinstall it to avoid confusion.

2. you need the mbp_nvidia_bl kernel module installed in /etc/modules.

3. hal might interfere: remove your macbook model from /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi.

4. LCD backlight should work automatically via gnome-power-manager which uses xrandr (same as xbacklight). Use the mactel version of g-p-m.

5. Keyboard backlight works through the hal-applesmc package.

Hopefully these things does it for you
Last edited by kosumi68; 5 Days Ago at 01:58 PM.

---

### Post by cyberdork33 on 2008-11-02
> **MichaelSwengel said:**
> open up a Terminal and type:

```
sudo gedit /etc/modules
```Type your password, and GEdit will open the Modules text file.

Just a nit-pick here. you should use gksudo to launch non-commandline apps with elevated privileges instead of sudo. Using sudo can break the function of some apps (firefox was one of those... at least in hardy).

---

### Post by MichaelSwengel on 2008-11-02
> **cyberdork33 said:**
> Just a nit-pick here. you should use gksudo to launch non-commandline apps with elevated privileges instead of sudo. Using sudo can break the function of some apps (firefox was one of those... at least in hardy).

I've never had a problem with gedit in 3 years....

But if you say so...

---

### Post by cyberdork33 on 2008-11-02
> **MichaelSwengel said:**
> I've never had a problem with gedit in 3 years....

But if you say so...Not saying that you will, but it is better practice to use the tools that you are supposed to use (i.e. do it the "right way"), especially when you are teaching someone else to do something (who might not be as careful with it as you).

See here for more info:
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by kjano on 2008-11-06
lcd backlight and keyboard backlight works with gnome but not with kde for me. any idea?

---

### Post by sjatkins on 2008-11-09
> **kosumi68 said:**
> lv1001,

From what I gather, the community is moving towards the use of Xorg XRandR, which has support for a broad range of graphics cards, backed up by kernel support. Both the gnome-power-manager and xbacklight use XRandR.

As for pommed, much of its code seems to have been incorporated into this effort.

Your model has nvidia graphics, has it not? Then there is a kernel module mbp_nvidia_bl to add to /etc/modules. This just might make xbacklight work.

On my gen 3 MBP this does not work.  Adding the module changes nothing.  xbacklight claims "No outputs have the backlight property".

Does someone have fully up-to-date info on this gen of MBP running kubuntu?  Why do I have to go foraging forums on every single update anyway?  There has to be a better way.

---

### Post by kosumi68 on 2008-11-09
> **sjatkins said:**
> On my gen 3 MBP this does not work.  Adding the module changes nothing.  xbacklight claims "No outputs have the backlight property".


The mbp_nvidia_nl driver adds a sysfs backlight interface under /sys/class/backlight; it does not affect randr in anyway (my bad - old info).

> 
Does someone have fully up-to-date info on this gen of MBP running kubuntu?  Why do I have to go foraging forums on every single update anyway?  There has to be a better way.


The ubuntu community forums and help pages are based on voluntary work. If you feel something is lacking, you are welcome to contribute: [http://ubuntuforums.org/showthread.php?t=969360](http://ubuntuforums.org/showthread.php?t=969360)

---

### Post by cyberdork33 on 2008-11-09
The MacBookPro3,1 seems to have gathered quite a few issues especially on this release. I would be very helpful if someone could point out the various issues and make sure that bugs are reported for them.

---

### Post by kjano on 2008-11-10
kosumi68, does this mean that the macbook function keys do not work with kde4 at all?

---

### Post by kosumi68 on 2008-11-10
> **kjano said:**
> kosumi68, does this mean that the macbook function keys do not work with kde4 at all?

I run gnome, and unfortunately have no deeper knowledge of kde4. If pommed does not work for you, things probably changed a lot in kde4 (and hal) as well. Someone with kde4 knowledge might be able to help you.

---

### Post by nossifer on 2008-11-17
I agree that on a MBPro, the light keys, wifi, sound keys, etc do not work in KDE4.1 / Ibex.  I too have followed the suggested actions and have had no results so far.

If there is anything you need from me to help this problem (logs, etc) then please let me know what you need and I will get it to you asap.

---

### Post by lv1001 on 2008-11-21
Sound function keys work for me, but none of the others.

xev shows that they are mapped to other things (dim lcd -> XF86Stop, toggle keyboard backlight -> XF86Mail, etc.).
I can change the lcd backlight via kde-power-manager so the problem might be solved by just remapping the keys...

my macbook pro 3,1 has a lot of problems with intrepid.
keyboard backlight did not work at all until I tried to use gnome-power-manager instead of kde-power-manager, but I am not happy with this solution at all.
Similarly I changed from knetworkmanager to the gnome "Network manager applet" since the beforementioned would not connect to any wireless lan.
The gnome programs are much better supported by the mactel ppa.

Also I am affected by the slowing down of some kde functions which seem to be related to nvidia cards as I gathered from other posts.

One last thing: My battery has suffered a lot during the last few weeks, leaving around 30% of the original capacity.
Could this be related to any problems with the "power-manager"s or is it just bad luck with my hardware?

Thanks a lot,
  LV

---

### Post by david_edmundson on 2008-11-23
KDE 4 does not have any support for the backlight control hotkeys. guidance-power-manager was ported as a last ditch effort, we should be seeing the brand new PowerDevil daemon in KDE4.2 which is where all the focus and attention is.

---

### Post by hellmitre on 2008-11-23
Yes! That worked! Thanks! I even get the little popup window showing the brightness level. Woot. Just added the mbp_nvidia_bl line to the end of /etc/modules and rebooted. Wondrous. I can take the pommed.conf file off my desktop (I was manually editing its init value and restarting pommed to change the brightness levels). Beeeeautiful.

---

### Post by nossifer on 2009-01-28
mbp_nvidia_bl is only working in gnome.  I tried KDE 4.1 on MBP3.1 and the brightness did not work.  Also just tried in KDE 4.2 and it is not working as well.

<quote> There has to be a better way.  </quote>
Agreed with the previous response.  The better way is to contribute to the community.

---

### Post by nossifer on 2009-01-28
Scratch that last comment.  got it working in KDE 4.2 on MacBookPro3.1
I already have Gnome installed, and already had that _bl line.  the problem is that KDE shortcutted the brightness commands already to something else.  So, just go into preferences > keyboard & mouse > Global Keyboard Shortcuts > Guidance Power Manager (in the dropdown for KDE component) and then change the shortcuts to something you are happy with.

I switched mine to F1 and F2 because I havent used those keys since the WinX days.  

Viva KDE4.2 !! it looks really pretty so far.  Hope it is stable.

---

### Post by hanzomon4 on 2009-04-21
Ah... I tried to set it to f1 and f2 (the default in gnome and OSX) but it said "the key you pressed is not supported by QT" So I had to set it to Fn+Meta+f1(f2) I think the problem lies with QT not understanding the brightness keys

---

