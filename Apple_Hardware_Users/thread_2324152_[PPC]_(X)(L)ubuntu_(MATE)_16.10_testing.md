---
title: "[PPC] (X)(L)ubuntu (MATE) 16.10 testing"
date: 2016-05-11
forum: Apple Hardware Users
---

### Post by xeno74 on 2016-05-11
Hi All,

I successfully updated my ubuntu MATE **16.04 LTS** PowerPC to **16.10 Yakkety Yak** on my AmigaONE X1000 today. I want to start some testing.

Update instructions for (X)(L)ubuntu (MATE): [forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3439#p37876")

**Issues**

I haven't found any issues. It works very well!

**Tests**

[LIST]
[*]Xorg 1.18.3 works
[*]Hardware 3D acceleration works without any problems with the official Mesa 11.2.1 (Gallium 0.4 on AMD BARTS DRM 2.43.0)
[*]Compiz works
[*]YouTube HD videos work with ViewTube in fullscreen!!!!!! (High Definition MP4 VLC HD MP4)
[*]Sound works
[*]Network works
[/LIST]

[[IMG]https://lh3.googleusercontent.com/-ZSof81buv0g/VzLf77VvBPI/AAAAAAAAC6Q/ekUSHC6VhJsxydC02dhva0xL2mC70j2vQ/w506-h380/ubuntu_MATE_16.10_PowerPC_Kernel_4.6-rc7.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/B9ysb4Kfyn7")

Have a nice day!

Cheers,

Christian

---

### Post by xeno74 on 2016-05-12
ubuntu MATE 16.10 Yakkety Yak PowerPC (development branch) with the stable longterm kernel 4.1.24 :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-jaXl9ofw9sk/VzReWrW9zPI/AAAAAAAAC7Q/pWzs0rJbaY88We6K8eKQDpEdFhBQgqaTw/w506-h380/ubuntu_MATE_16.10_PowerPC_with_kernel_4.1.24.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/LnmzLqbn4Kw")

---

### Post by luigiburdo on 2016-05-16
christian with radeonsi im facing a strange issue here , probably because the new drm... i wil check better today.
pratically mesa dont work in swrast too , i have build last dev and the 11.2.2 and is the same no glx visuals with and without llvm.
if i force fbdev mode in xorg.conf i have only black screen. 
Xorg logs gave me all ok

---

### Post by xeno74 on 2016-05-16
> **luigiburdo said:**
> christian with radeonsi im facing a strange issue here , probably because the new drm... i wil check better today.
pratically mesa dont work in swrast too , i have build last dev and the 11.2.2 and is the same no glx visuals with and without llvm.
if i force fbdev mode in xorg.conf i have only black screen. 
Xorg logs gave me all ok

Thank you for the hint.

---

### Post by luigiburdo on 2016-05-19
Hi Christian,
yesterday update gave me many ppc64 libs upgrade... probably we are near to a transiction? ;-)

---

### Post by luigiburdo on 2016-05-19
Just updated Firefox 46.01 ... and is crashing , there did you have issue too?

---

### Post by xeno74 on 2016-05-20
> **luigiburdo said:**
> Just updated Firefox 46.01 ... and is crashing , there did you have issue too?

I haven't updated my ubuntu MATE  for a few days. Jdupuis and este.el.paz have the same problems with Firefox 46.01. 

Links:

[Ubuntu Mate Updates-Kills Firefox -- forum.hyperion-entertainment]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3448")

[(X)(L)ubuntu (MATE) 16.04 LTS testing]("http://ubuntuforums.org/showthread.php?t=2301608&page=22&p=13491939#post13491939")

LP bug report: [https://bugs.launchpad.net/ubuntu/+bug/1583849]("https://bugs.launchpad.net/ubuntu/+bug/1583849")

On Debian Sid PowerPC Firefox 47 works and on openSUSE Tumbleweed PPC64, Firefox 46 works as well.

**Firefox 47** on **Debian Sid PPC32**:

[[IMG]https://lh3.googleusercontent.com/-bcv-DdOFT5g/VzANPx4s57I/AAAAAAAAC5Y/6DAKEYeOW9gJMnrFA8oEYwwPUoZfEfTFA/w506-h380/Kernel_4.6-rc7_PowerPC_with_the_new_Firefox_47.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/4WYLwXWAMHh")

**Firefox 46** on **openSUSE Tumbleweed PPC64**:

[[IMG]https://lh3.googleusercontent.com/-byHai5ffhpo/VztkiKNVIZI/AAAAAAAAC-c/m9wMgUMWP08w9QE5KX6kl9hqnmxIiJpaQ/w506-h380/openSUSE_Tumbleweed_PPC64_AmigaONE_X1000.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/MmLq52gd4Ud")

---

### Post by xeno74 on 2016-06-09
Firefox **47.0** is available for ubuntu MATE 16.10 PowerPC :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-4lohCcDCvMI/V1HXeRwpXvI/AAAAAAAADGo/gcRw5u4goT0SDHxSsG_KWgjiMBADrMI-g/w506-h380/Firefox_47.0_ubuntu_MATE_16.10_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/jU4Li5yyBeE")

The new MATE 1.14.1 for ubuntu MATE 16.10 Yakkety Yak PowerPC and the kernel 4.6.1:

[[IMG]https://lh3.googleusercontent.com/-ijGyKuTCFQY/V1ARQ72HntI/AAAAAAAADF8/aO8n-_VdpnUV24mSdD131fXhHw-rg-S9A/w506-h380/ubuntu_MATE_16.10_PowerPC_with_kernel_4.6.1_and_MATE_1.14.1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/LfzXqEaakBX")&#65279;

Please test ubuntu MATE 16.10 Yakkety Yak.

---

### Post by rican-linux on 2016-06-10
Where are you getting your OpenSUSE images?

---

### Post by eastone on 2016-06-11
> **rican-linux said:**
> Where are you getting your OpenSUSE images?

[http://download.opensuse.org/ports/ppc/tumbleweed/iso/](http://download.opensuse.org/ports/ppc/tumbleweed/iso/)

---

### Post by luigiburdo on 2016-07-01
yesterday cdimage on quad g5 after splash loading image gave me only a blinking cursor on radeon hd 4650 on 16x slot.
note on 15.10 with this configuration i had 3d and 2d working .
i been try all my knowledge with kernel appends but without different result. 
I will check on 8x slot if something will change... but i have the fear of not

---

### Post by xeno74 on 2016-07-06
"Welcome" doesn't work on my ubuntu MATE 16.10 PowerPC. Any hints?&#65279;

[[img]https://lh3.googleusercontent.com/-CYIb2BT_O0w/V30ls2iiCgI/AAAAAAAADLU/iPRROKnd5KcjgcRxbSYAiwyn-G2MxuqKg/w506-h380/ubuntu_MATE_16.10_PPC_Welcome.png[/img]](https://plus.google.com/115515624056477014971/posts/9ij8A3UpS1N)

---

### Post by ernsteiswuerfel on 2016-07-10
Yes. It's [https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-welcome/+bug/1597764](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-welcome/+bug/1597764) ^^


PPC problems with WebKit2.

---

### Post by xeno74 on 2016-07-11
> **ernsteiswuerfel said:**
> Yes. It's [https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-welcome/+bug/1597764](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-welcome/+bug/1597764) ^^


PPC problems with WebKit2.

Thank you for your reply. :-)

---

### Post by ernsteiswuerfel on 2016-07-12
Would be nice if Firefox 47 finds it's way to yakkety-daily! FF 46 crashes on PPC big endian machines: [https://bugs.launchpad.net/firefox/+bug/1583849](https://bugs.launchpad.net/firefox/+bug/1583849)

---

### Post by ernsteiswuerfel on 2016-07-24
Due to an update mesa-11.2.1 -> **mesa-12.0.1** in Yakkety's daily iso the nasty [bug #1432949]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949") is gone!  KMS works now on my PowerBook 5,6, 3D with r300 works on bit depths > 16 bit , GPU compositors work, even compiz can be enabled and works so far.

---

### Post by ernsteiswuerfel on 2016-07-24
Hmpf, doing an entire disk install I unfortunately hit [Bug #1606089]("https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/1606089") on my PowerBook 5,6, so yaboot-problems again...
Anyone more lucky on an Apple machine?

---

### Post by Casey_C on 2016-08-11
luigi, I've been experiencing the same problem with my 11,2 G5. I've tried my Radeon HD 4650 in 8x with stock card in 16x. Will run nouveau on the 16x but when I try to use the Radeon I get the blinking white cursor. I've tried removing nouveau driver and fbdev, and it logs me into console but no desktop. Have you come up with any ideas about the issue?

---

### Post by rican-linux on 2016-08-11
I ran into the same issue. I also experienced this with Debian Testing and Gentoo.

---

### Post by ernsteiswuerfel on 2016-08-15
> **rican-linux said:**
> I ran into the same issue. I also experienced this with Debian Testing and Gentoo.Ubuntu is using yaboot 1.3.16 whereas Gentoo and Debian use 1.3.17. Can you confirm that this bug is still an issue with 1.3.17? If so this bug report should be taken upstream. I had a look on the yaboot mailing list, some Gentoo Devs did it like that before. Though I found no corresponding Gentoo or Debian bugs.

---

### Post by rican-linux on 2016-08-15
I can confirm it is in both. The fix works in Debian stretch. I am posting a bug report today. I will test in Gentoo soon after if this fix works, but I think it will since I have similar reports in the PPC forums. However I think this project is dead upstream. There has not been a commit the source code in almost 10 years. See [here]("https://github.com/pnasrat/yaboot").

---

### Post by chdrsto on 2016-08-15
Can someone confirm whether this will work on a G5 Quad with a Radeon HD6770 on the 8x PCIe slot?

---

### Post by rican-linux on 2016-08-15
If you are referring to the yaboot issue? It is not hardware dependent. This fix should work on G5 as well.

---

### Post by xeno74 on 2016-08-16
Hi All,

We are also still testing ubuntu MATE 16.10 PowerPC. We had some error messages after an update:

```

systemd[5544] : systemd-logind.service: Failed at step SECCOMP spawning /lib/systemd/systemd-logind: Invalid argument
systemd[1] : Failed to start Login Service
systemd[5544] : systemd-logind.service: Failed at step SECCOMP spawning /lib/systemd/systemd-logind: Invalid argument
systemd[1] : Failed to start Login Service
systemd[5544] : systemd-logind.service: Failed at step SECCOMP spawning /lib/systemd/systemd-logind: Invalid argument
systemd[1] : Failed to start Login Service
systemd[5544] : systemd-logind.service: Failed at step SECCOMP spawning /lib/systemd/systemd-logind: Invalid argument
systemd[1] : Failed to start Login Service


```

The MATE desktop didn't work anymore.

After activating of SECCOMP support in our kernel, the MATE desktop works again.

Some screenshots:

[[IMG]https://lh3.googleusercontent.com/-mJtemqrBWww/V6iDDPe3CxI/AAAAAAAADQQ/7cP_x5x7Hi0HG9ALC4IRLdlauF4bM-4ag/w506-h380/ubuntu_MATE_16.10_PowerPC_SECCOMP.png[/IMG]](https://plus.google.com/115515624056477014971/posts/15oXe5mmBQ7)

[[IMG]https://lh3.googleusercontent.com/-8lK9rN05aVE/V5smuuxi5FI/AAAAAAAADPk/smsW5aU26EArNSuq2ffkHWU9PqeRtISow/w506-h380/ubuntu_MATE_16.10_PPC_Mesa_12.0.1_DRM_2.45.0_kernel_4.8-alpha1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/9mLVGgejdwb")

Cheers,

Christian

---

### Post by xeno74 on 2016-08-16
Hi All,

Great news! The developers fixed the problem with systemd. It is no longer necessary to compile a kernel with SECCOMP support. I was able to boot ubuntu MATE 16.10 PowerPC with the stable longterm kernel [**4.1.30**](http://www.xenosoft.de/vmlinux-4.1.30-AmigaONE_X1000.tar.gz) today. :-)&#65279;

[[img]https://lh3.googleusercontent.com/-5KXh_2aeRIQ/V7MrOYMUlnI/AAAAAAAADSM/uHrWlAZty_UmTO4AT4IZ_syRHWEGQlmVg/w506-h380/ubuntu_MATE_16.10_PowerPC_systemd_231-3.png[/img]](https://plus.google.com/115515624056477014971/posts/SwHMhXzKLVK)

Cheers,

Christian

---

### Post by chdrsto on 2016-08-16
Hi, no I'm more interested on the graphic (3D acc.) issue on G5 PowerPCs. The yaboot is fixable with a boot partition on ext2.

---

### Post by ernsteiswuerfel on 2016-08-16
@chdrsto:

Since mesa-12.0.1 has landed in 16.10 the 3D acceleration works on my PowerMac G5 7,3 (AGP). Don't know what's the status on PCIe-PowerMacs, but it's just one daily iso away to try it out!

---

### Post by chdrsto on 2016-08-16
@ernsteiswuerfel
Thanks, I've just burned two DVDs without success. Is there a special boot option to consider? I mean, there is a page >> [click me]("https://ubuntuforums.org/showthread.php?t=2274612") << where luigiburdo  advise to use following boot option to load the live CD for radeon devices.> live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0

---

### Post by xeno74 on 2016-08-17
Hi All,

I successfully updated my **Lubuntu 16.04.1 LTS PowerPC** to **_16.10 Yakkety Yak PowerPC_** on my USB flash drive today. The reason is, that the Lubuntu developers are looking for testers for the PowerPC platform. I'd like to help them.&#65279;

Update instructions for Lubuntu: [http://forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3439&p=38605#p38605")

[[IMG]https://lh3.googleusercontent.com/-DqGZOBcpqjg/V7RiWpQ14wI/AAAAAAAADSg/K4JX20HvwP8mYmZTamjYXswJLkOGCfWFwCL0B/w506-h380/Lubuntu_16.10_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/7eCQ9EpGdYB")

PLEASE test the new Lubuntu 16.10.

Thanks,

Christian

---

### Post by luigiburdo on 2016-08-17
Chdrsto only 14.04 work with radeonhd and 3d for now , 15.10 working only in fbdev mode but the pcie radeonhd board have to stay in first 16x pcie .
16.04 was not working in my lastest test but i need to made better testing ... sorry guys dont have many free time this period

---

### Post by chdrsto on 2016-08-18
> **luigiburdo said:**
> Chdrsto only 14.04 work with radeonhd and 3d for now , 15.10 working only in fbdev mode but the pcie radeonhd board have to stay in first 16x pcie .
16.04 was not working in my lastest test but i need to made better testing ... sorry guys dont have many free time this period

Hi luigi
Just tell me how to support you or how to do the debugging by my own.
The system boots and tries to start X without success. I'm even not able to change into terminal ... whenever I try to call a terminal, it switches right back into the X11 mode, which is not able to start.

---

### Post by ernsteiswuerfel on 2016-08-22
Done some more testing on my PPC machines. Look out for bugs #[1571416]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416"), #[1583849]("https://bugs.launchpad.net/firefox/+bug/1583849"), #[1597764]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-welcome/+bug/1597764"), #[1615443]("https://bugs.launchpad.net/ubuntu/+source/mate-terminal/+bug/1615443"), #[1615844]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1615844"), #[1615846]("https://bugs.launchpad.net/ubuntu/+source/mate-system-monitor/+bug/1615846"), #[1615848]("https://bugs.launchpad.net/ubuntu/+source/mate-utils/+bug/1615848")
;)

---

### Post by ernsteiswuerfel on 2016-08-22
> **chdrsto said:**
> @ernsteiswuerfel
Thanks, I've just burned two DVDs without success. Is there a special boot option to consider? I mean, there is a page >> [click me]("https://ubuntuforums.org/showthread.php?t=2274612") << where luigiburdo  advise to use following boot option to load the live CD for radeon devices.
Sorry, but I am unable to give you any advice here since my PowerMac G5 7,3 only has AGP-graphics, not PCIe. luigiburdo's kernel boot parameters look fine, however IMHO you don't need the "nouveau"-stuff as this is only for NVIDIA cards.

If your specific graphics card is not working at all you should open a bug about this issue. It won't be a bad idea either to let the upstream devs know about it. Have a look at the current PPC issues: [https://bugs.freedesktop.org/buglist.cgi?quicksearch=radeon%20ppc](https://bugs.freedesktop.org/buglist.cgi?quicksearch=radeon%20ppc)
Maybe you find some good input if you read through the bugs listed there.

In my case the Ubuntu-Bug got [fixed]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949") by upstream devs and 3D-acceleration is working since then, albeit it still has issues.

---

### Post by luigiburdo on 2016-08-23
Hi Chdrsto,
this issue come because Xorg on ppc need xorg.conf in /etc/X11/ 
run "sudo Xorg -configure" and after "sudo cp xorg.conf.new /etc/X11/xorg.conf"

---

### Post by xeno74 on 2016-08-27
The [Beta 1 ]("https://ubuntu-mate.org/blog/ubuntu-mate-yakkety-beta1/")is available.

[[IMG]https://lh3.googleusercontent.com/-ZYXoWKDxxQ4/V8F2pfm8pXI/AAAAAAAADWI/nntzt59YXHk9H1GSlGsLhEWjyltV65O2ACJoC/w506-h380/ubuntu_MATE_16.10_Beta_1_PowerPC_kernel_4.8-rc3-2.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/i27q5EbuC9w")

---

### Post by eastone on 2016-09-03
Finally I found time to install 16.10 update over 16.04 on my G5 2x2.3 6GB NVIDIA 6600 Pci-e :)
WIFI works.
Sound works.
VLC can play smoothly 1080p mov. files.
Glxgears works only with "vblank_mode=0", without parameter not working at all.
[http://i63.tinypic.com/2q9e6iv.png](http://i63.tinypic.com/2q9e6iv.png)
Unfortunately monitor  has distortion in native resolution :(
[https://youtu.be/9iigrQ-1etY](https://youtu.be/9iigrQ-1etY)

---

### Post by eastone on 2016-09-05
[https://www.youtube.com/watch?v=66xCgLkudQE](https://www.youtube.com/watch?v=66xCgLkudQE)
This time more dynamic less static ;)

---

### Post by chdrsto on 2016-09-05
Hi eastone
Do you have or run it on more than one Display? If so, what boot options do you have?

---

### Post by ernsteiswuerfel on 2016-09-05
I finally succeeded in doing a full mainline build of 4.8.0-rc4 for my PowerMac G5 7,3. The good thing is that bug [#1571416]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416") seems gone now with this kerne! Which means the additional "radeon.agpmode=-1" boot parameter is no longer necessary on my machine to avoid the freeze shorty after reaching the desktop. Finally the live iso can boot just with default config and yaboot does not need additional tinkering. At least on my machine, yay! \\:D/ Hope others issues will get resolved too.

Hope kernel 4.8.x will make it into final 16.10 Yakkety.  :)

---

### Post by eastone on 2016-09-06
Hi chdrsto,
No any additional parameters during the boot. 
I have to try dual display.

PS
Dual display. Sorry for poor quality :/
[https://www.youtube.com/watch?v=04YWgFi4zbY](https://www.youtube.com/watch?v=04YWgFi4zbY)

---

### Post by chdrsto on 2016-09-06
Hi eastone

Wow, Im deeply impressed. Can you share your xorg.conf for the dual screen? (If you have one)

---

### Post by eastone on 2016-09-07
Hi Chdrsto,
It works without xorg.conf, I can't even create it.

---

### Post by luigiburdo on 2016-09-07
> **eastone said:**
> Hi Chdrsto,
It works without xorg.conf, I can't even create it.

yes Xorg was fixed for dont use the xorg.config any more... but many issue still there.
es:libglamour crashes
gles, gles2: wrong colors.
Radeon rv730 freeze

and probably ... no radeonhd 5xxx,6xxx,7xxx with 3d working

---

### Post by rican-linux on 2016-09-09
FYI in Lubuntu 16.10 if you try to install the LXQT desktop it will break your system. There are some serious bugs that need fixing there.

---

### Post by luigiburdo on 2016-09-12
I installed xubuntu desktop and made it running with "startx" on the console... but many bugs there , i have many upstart and lightdm tasks active "top" 

[IMG]https://lh3.googleusercontent.com/h1EYOMQFYbnW0G3U25zKT4qh1D3aYpOSaDdqH4BgGUZVQqwwFXTY2MpaHPF83hoe5hPm_u6pTA=w1920-h1080-rw-no[/IMG]


qt software crash (midori and qupzilla), kodi crash and many others... 
there is a unhandled signal on lightdm-gtk-greater who made the screen flashing and pacman crash


```
[   12.861951] systemd[1]: snapd.refresh.timer: Adding 2h 10min 36.599206s random time.[   12.861978] systemd[1]: snapd.refresh.timer: Adding 4h 55min 48.965736s random time.
[   13.405797] systemd[1]: snapd.refresh.timer: Adding 1h 55min 49.064213s random time.
[   13.405824] systemd[1]: snapd.refresh.timer: Adding 1h 14min 17.103596s random time.
[   16.044305] lightdm-gtk-gre[4727]: unhandled signal 4 at 182116a8 nip 182116a8 lr 18211680 code 30001
[   18.192054] lightdm-gtk-gre[4831]: unhandled signal 4 at 1816e6a8 nip 1816e6a8 lr 1816e680 code 30001
[   20.388574] lightdm-gtk-gre[4940]: unhandled signal 4 at 182ad6a8 nip 182ad6a8 lr 182ad680 code 30001
[   22.577413] lightdm-gtk-gre[5081]: unhandled signal 4 at 186256a8 nip 186256a8 lr 18625680 code 30001
[   24.977054] lightdm-gtk-gre[5193]: unhandled signal 4 at 1843c6a8 nip 1843c6a8 lr 1843c680 code 30001
[   27.357445] lightdm-gtk-gre[5302]: unhandled signal 4 at 188d56a8 nip 188d56a8 lr 188d5680 code 30001
[   29.564002] lightdm-gtk-gre[5407]: unhandled signal 4 at 188a16a8 nip 188a16a8 lr 188a1680 code 30001
[   31.777422] lightdm-gtk-gre[5520]: unhandled signal 4 at 181c26a8 nip 181c26a8 lr 181c2680 code 30001
[   33.958786] lightdm-gtk-gre[5624]: unhandled signal 4 at 182936a8 nip 182936a8 lr 18293680 code 30001
[   36.134803] lightdm-gtk-gre[5718]: unhandled signal 4 at 183bb6a8 nip 183bb6a8 lr 183bb680 code 30001
[   38.345727] lightdm-gtk-gre[5813]: unhandled signal 4 at 184af6a8 nip 184af6a8 lr 184af680 code 30001
[   40.531214] lightdm-gtk-gre[5908]: unhandled signal 4 at 1849b6a8 nip 1849b6a8 lr 1849b680 code 30001
[   42.724347] lightdm-gtk-gre[6011]: unhandled signal 4 at 188556a8 nip 188556a8 lr 18855680 code 30001
[   45.009155] lightdm-gtk-gre[6169]: unhandled signal 4 at 181a16a8 nip 181a16a8 lr 181a1680 code 30001
[   47.225088] lightdm-gtk-gre[6260]: unhandled signal 4 at 1837d6a8 nip 1837d6a8 lr 1837d680 code 30001
[   49.419178] lightdm-gtk-gre[6352]: unhandled signal 4 at 1847f6a8 nip 1847f6a8 lr 1847f680 code 30001
[   51.613207] lightdm-gtk-gre[6443]: unhandled signal 4 at 183246a8 nip 183246a8 lr 18324680 code 30001
[   53.788275] lightdm-gtk-gre[6534]: unhandled signal 4 at 1853f6a8 nip 1853f6a8 lr 1853f680 code 30001
[   55.958143] lightdm-gtk-gre[6626]: unhandled signal 4 at 1818e6a8 nip 1818e6a8 lr 1818e680 code 30001
[   58.082939] lightdm-gtk-gre[6717]: unhandled signal 4 at 181846a8 nip 181846a8 lr 18184680 code 30001
[   60.067472] lightdm-gtk-gre[6809]: unhandled signal 4 at 1840e6a8 nip 1840e6a8 lr 1840e680 code 30001
[   62.054863] lightdm-gtk-gre[6901]: unhandled signal 4 at 184fc6a8 nip 184fc6a8 lr 184fc680 code 30001
[   64.054080] lightdm-gtk-gre[6992]: unhandled signal 4 at 183656a8 nip 183656a8 lr 18365680 code 30001
[   66.058101] lightdm-gtk-gre[7084]: unhandled signal 4 at 185e06a8 nip 185e06a8 lr 185e0680 code 30001
[   68.074323] lightdm-gtk-gre[7176]: unhandled signal 4 at 188fb6a8 nip 188fb6a8 lr 188fb680 code 30001
[   70.071975] lightdm-gtk-gre[7267]: unhandled signal 4 at 188226a8 nip 188226a8 lr 18822680 code 30001
[   72.076146] lightdm-gtk-gre[7359]: unhandled signal 4 at 182a76a8 nip 182a76a8 lr 182a7680 code 30001
[   74.127277] lightdm-gtk-gre[7452]: unhandled signal 4 at 186c66a8 nip 186c66a8 lr 186c6680 code 30001
[   76.090711] lightdm-gtk-gre[7544]: unhandled signal 4 at 188806a8 nip 188806a8 lr 18880680 code 30001
[   78.075367] lightdm-gtk-gre[7635]: unhandled signal 4 at 186d76a8 nip 186d76a8 lr 186d7680 code 30001
[  273.713058] pcmanfm[8788]: unhandled signal 4 at 1e3616a8 nip 1e3616a8 lr 1e361680 code 30001
[  275.507507] pcmanfm[8936]: unhandled signal 4 at 1ddc26a8 nip 1ddc26a8 lr 1ddc2680 code 30001
[  276.497133] pcmanfm[8991]: unhandled signal 4 at 1de9d6a8 nip 1de9d6a8 lr 1de9d680 code 30001
[  277.393952] pcmanfm[9010]: unhandled signal 4 at 1e2ee6a8 nip 1e2ee6a8 lr 1e2ee680 code 30001
[  278.105455] pcmanfm[9021]: unhandled signal 4 at 1e1fa6a8 nip 1e1fa6a8 lr 1e1fa680 code 30001
[  278.818089] pcmanfm[9031]: unhandled signal 4 at 1e4c66a8 nip 1e4c66a8 lr 1e4c6680 code 30001
[  606.164491] plugin-containe[9751]: unhandled signal 4 at 18d03014 nip 18d03014 lr 18d02f38 code 30001
[ 1498.413347] caja[10235]: unhandled signal 11 at 0000030f nip 1f0f300c lr 1f0f2fdc code 30001
```

from august lastest updates ... ppc is really broken

---

### Post by xeno74 on 2016-09-14
Hi All,

I updated my ubuntu MATE 16.10 PowerPC on my X1000 today and I saw a lot of ubuntu MATE packages for update. The update worked without any problems.
Unfortunately "Welcome" still doesn't work. There was also an update of systemd. ;-) After a reboot, the stable longterm kernel 4.1.32 works again with systemd on ubuntu MATE 16.10. There was a problem with the stable longterm kernel 4.1.32 and systemd.

I know there are some problems with LightDM on ubuntu MATE 16.10 if you use it on the X5000.  I recommend to use Slim instead of LightDM. Please install SLIM and add the following line to .xinitrc file in the user’s home directory: **exec mate-session**. After that reboot the X5000. Now the X5000 will boot into Slim login where you can login to Mate session. If the MATE desktop doesn't work please install systemd again. I am not sure if Upstart works with the MATE desktop.

[[IMG]https://lh3.googleusercontent.com/-suzAqDAiMLU/V9Zz6lPMFtI/AAAAAAAADfY/yxUI7cz5Njc0-ORJdTVwnIi6-4DBkPoywCJoC/w530-h398-p/ubuntu_MATE_16.10_PowerPC_Mesa_12.0.2_DRM_2.46.0_kernel_4.8-rc6.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/RnLNjQ2cGT9") [[IMG]https://lh3.googleusercontent.com/-Hz6R-fGcnFo/V9kKHgW1AuI/AAAAAAAADiA/oM7cqBm-zlIjIX_IERaw-Z0m9SBf436gwCJoC/w530-h398-p/ubuntu_MATE_16.10_PowerPC_14092016.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/ghked6qkcEm")

[IMG]https://lh3.googleusercontent.com/GS-z2pGUGLupHOmCUeL-PSTEAvSo8iuNdkg_fye7jVhghiWVuiwyhCJMxZAzxLQp1WzTeRjqPg=w1920-h1200-no[/IMG]

Cheers,

Christian

---

### Post by luigiburdo on 2016-09-14
Hi Christian,
after today update: 
i continue have issue with lightdm but i installed gdm3 and it is working really good  . SLIM was gave me issue with Caja .

---

### Post by Casey_C on 2016-09-15
I think systemd-shim is broken on PPC for 16.10 and 16.04.  
I've been trying to get 16.04 and/or 16.10 working on G5/quad with Radeon HD 4650 but keep running into issues.  I suspect it may have something to do with systemd, as I've always been able to at least startx with sysvinit and/or upstart, so I tried using sysvinit with systemd-shim and also tried upstart with systemd-shim but both give a logind error message:

[  174.808740] systemd-logind[2521]: Failed to start unit [email]user@1000.servic[/email]e: Unknown unit: [email]user@1000.servic[/email]e
[  174.808763] systemd-logind[2521]: Failed to start user service: Unknown unit: [email]user@1000.servic[/email]e

I found similar problems for x86 but it appears it has been resolved for them if I'm reading the report right; see [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756076](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756076) and [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756247)
Can anyone confirm?

---

### Post by luigiburdo on 2016-09-15
Hi Casey.X1000,x5000 and sam have one big difference 1 pcie slot with one gpu.
On G5 we have to fight wiht 2 gpus. first gpu is with Open Firmware gpu, other x86 gpu. On 14.0x for sure the first gpu who become up is the nvidia but nouvau.modeset=0 and offb: off made right it works and pull down the nvidia and up the radeon.
from 14.10: 
if you put radeon.modeset=1 and nouveau.modeset=0 you have exactly the opposite in xorg ... nvidia go up and radeon down and this made desktop unusable if radeon is selected in xorg .conf... only way to have x running with radeonhd gpu is with fbdev .
another thing on 14 radeon have to stay on 8x pcie  on 14.10 and up have to stay on first pcie 16x

this why im sure is xorg the problem. If you find another way mate you will made me happy :-)

---

### Post by Casey_C on 2016-09-15
Hey Luigi, Yep I agree with all you said!  What I was thinking is I can make the kernel and xorg *think* there is only one PCIe GPU if I could use sysvinit instead of systemd.  With sysvinit I can make a boot script to "echo 1 > /sys/devices/pci0000:00/0000:00:0b.0/0000:0a:00.0/remove" and the system will think the 16x slot is not there anymore.  This is how I had Wheezy working with radeon.  But I cannot get systemd to "remove" the slot.  I wanted to try using sysvinit, but I think there is a problem with systemd-shim, which is required to use sysvinit.

---

### Post by chdrsto on 2016-09-15
Hi Casey

Im pretty much interested to get a fix for this issue. ... How can I support you?
Im not a developer, but willing and able to test

---

### Post by Casey_C on 2016-09-15
Right now you could see if you can confirm my bug on another system and if so enter a bug report... 
If you can get a G5 (preferably an 11,2 - the ones with PCIe but it probably doesn't matter much for this step) running either 16.04 or 16.10 (without Radeon is fine), try installing/using upstart with systemd-shim. 
"sudo apt install upstart upstart-sysv systemd-shim systemd-sysv-"
As well as the dependencies... 
(Reboot)
See if you also get an error or cannot startx. Make a bug report if you do; mine is at [https://bugs.launchpad.net/ubuntu-mate/+bug/1624171](https://bugs.launchpad.net/ubuntu-mate/+bug/1624171). Hopefully the solution from the x86 side can be easily replicated to fix PPC. 
To restore to a running state: 
"sudo apt install systemd-sysv systemd-shim- upstart- upstart-sysv-"

---

### Post by luigiburdo on 2016-09-16
> **Casey_C said:**
> Right now you could see if you can confirm my bug on another system and if so enter a bug report... 
If you can get a G5 (preferably an 11,2 - the ones with PCIe but it probably doesn't matter much for this step) running either 16.04 or 16.10 (without Radeon is fine), try installing/using upstart with systemd-shim. 
"sudo apt install upstart upstart-sysv systemd-shim systemd-sysv-"
As well as the dependencies... 
(Reboot)
See if you also get an error or cannot startx. Make a bug report if you do; mine is at [https://bugs.launchpad.net/ubuntu-mate/+bug/1624171](https://bugs.launchpad.net/ubuntu-mate/+bug/1624171). Hopefully the solution from the x86 side can be easily replicated to fix PPC. 
To restore to a running state: 
"sudo apt install systemd-sysv systemd-shim- upstart- upstart-sysv-"

Casey the problem is : the radeon 4450 is working with 3d too on 16x on all distros (15.0,16 etc) but 5xxx 6xxxx and 7xxxx have the same issue only fbdev...
i think this because if i remeber good the 4xxx series have a pci-to-pcie chip inside the others not.

---

### Post by Casey_C on 2016-09-16
Luigi, that is interesting.  I have a Radeon 4450 but I have not tried in the 16x slot.  Are there stability issues if the OpenFirmware/nvidia card is moved to 8x?  I know there are stability issues if it is removed...

---

### Post by luigiburdo on 2016-09-18
> **Casey_C said:**
> Luigi, that is interesting.  I have a Radeon 4450 but I have not tried in the 16x slot.  Are there stability issues if the OpenFirmware/nvidia card is moved to 8x?  I know there are stability issues if it is removed...

No no stability issue on Nvidia on 8x ... but:
4650 work but become really unstable, i read this issue was present on x86 too.
the other 5xxx,6xxx,7xxxx work only in fbmode 

The 4650 is the only gpu who have the 3d working.
7xxxx RadeonSI have the libglemor crashing.

---

### Post by xeno74 on 2016-09-19
Hi All,

I updated ubuntu MATE 16.10 PowerPC yesterday and I got the new Mesa version 12.0.3. :-)&#65279;

Screenshot of ubuntu MATE 16.10 PowerPC with the new Mesa:

[[img]https://lh3.googleusercontent.com/-1Fr9cVBaZEg/V9_Xn00_W2I/AAAAAAAADlU/sGFmg8_hzAwPzALxxjr9g2EyfPPm9680wCJoC/w530-h398-p/ubuntu_MATE_16.10_PowerPC_Mesa_12.0.3_DRM_2.46.0.png[/img]](https://plus.google.com/115515624056477014971/posts/9EY9ek9rWB3)

Cheers,

Christian

---

### Post by eastone on 2016-09-19
@xeno74

On G5 Nvidia 6600:
- still needs vblank_mode=0 for glxgears
- Chromium still has wrong colors and random freezes
- every OpenGL game (Neverball, Neverputt) freezes system

---

### Post by luigiburdo on 2016-09-19
> **eastone said:**
> @xeno74

On G5 Nvidia 6600:
- still needs vblank_mode=0 for glxgears
- Chromium still has wrong colors and random freezes
- every OpenGL game (Neverball, Neverputt) freezes system

strange!? ... it meas the novueau have endianess issue?!?!!

---

### Post by eastone on 2016-09-20
G4 1.5GHz R300 (9650)
-glxgears no issue (50% faster than G5 with nouveau)
-Chromium works with correct colors
-OpenGL games freeze system totally (same as G5)
-splash screen has wrong colors but correct on G5 :)

---

### Post by luigiburdo on 2016-09-20
Old card have better support because at that time powerpc was better supported by ATI ... AMD is doing only worst on powerpc

---

### Post by luigiburdo on 2016-09-21
Hi guys need to notice the radeon hd 5xxx and 6xxx are not working on 14.0.4.5 fonts are not show 14.04.3 all is right

---

### Post by eastone on 2016-09-21
I forgot to mention that Blender (2.77a) does not work on nouveau G5 (requires OpenGL 2.1 -has 2.0) but works on G4 with R300 (has OpenGL 2.1 :)

---

### Post by handaxe on 2016-09-28
Hi all, no one else seen a KMS related freeze with linux-image-4-8-0?  This is iMac G5.

The kernel now is generic and no longer powerpc64.  Boot gets to the point where a corrupted cursor shows, then a freeze.

"nomodeset" makes no difference in yaboot.

Kernel 4.40-9136-powerpc64-smp works just fine.

---

### Post by xeno74 on 2016-09-28
Hi All,

Ubuntu MATE 16.10 **Beta 2** PPC is released.

[IMG]https://lh3.googleusercontent.com/proxy/w8XBlohOL-ZpUFNOhhKICIEOBxOubDt1UWlOhZwBbD6vjA_hRCQwMGH3369EKRQ1c1SIO8XxdaMfKWsL3i0s2XTB3gnJ02SoG-Ydus03w1Au2w=w530-h331-p[/IMG]

Link to the announcement: [https://ubuntu-mate.org/blog/ubuntu-mate-yakkety-beta2/]("https://ubuntu-mate.org/blog/ubuntu-mate-yakkety-beta2/")

I was able to update ubuntu MATE 16.10 PPC to Beta 2 on my AmigaOne X1000 today. All things work except the "Welcome" screen. Additionally I was able to boot the Beta 2 ISO with a virtual PowerMac G4 machine with QEMU/KVM PR. Unfortunately it doesn't boot with a virtual G3 machine anymore. The default kernel from the live DVD needs a CPU with AltiVec support. It doesn't boot with a virtual pSeries either.&#65279;

[[IMG]https://lh3.googleusercontent.com/-hrm1ZbQmqzY/V-vUfyCRZMI/AAAAAAAADuc/eSKtze9hR0QGnYJoNVf6b3qdkCbzHNevQCJoC/w530-h398-p/ubuntu_MATE_16.10_Beta2_on_QEMU_PPC_KVM-PR.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/aT4KZ94tXaG")

Please test the Beta 2.

Cheers,

Christian

---

### Post by luigiburdo on 2016-09-29
Christian,
> [COLOR=#000000]G3 machine [/COLOR] does not boot or dont made the Xorg exit?
if dont boot pretty sure something is not working on kernel, if xorg dont work is because libjpeg-turbo ... it was build with simd(altivec) just is need to rebuild again without simd support.

Ciao
Luigi

---

### Post by xeno74 on 2016-09-29
> **luigiburdo said:**
> Christian,
 does not boot or dont made the Xorg exit?
if dont boot pretty sure something is not working on kernel, if xorg dont work is because libjpeg-turbo ... it was build with simd(altivec) just is need to rebuild again without simd support.

Ciao
Luigi

It doesn't boot but I only tested it with a virtual PowerMac G3.

---

### Post by eastone on 2016-09-29
On my G5 when booting from DVD:
[https://flic.kr/p/MEMsEm](https://flic.kr/p/MEMsEm)

---

### Post by ernsteiswuerfel on 2016-09-29
@handaxe + eastone:

I am facing the same/similar problem on my PowerMac G5 7,3. Already filed [Bug #1626332]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1626332") concerning this issue. You may add yourself to this bugreport.

---

### Post by kate-libby on 2016-10-02
Until 12.04 (12.10) *buntu works very good on PowerMac G4 / PowerBook G4. Since *buntu 13.04 only Bugs, bugs, bugs... WHY???   ](*,) ](*,) ](*,)

---

### Post by luigiburdo on 2016-10-04
Ubuntu Mate 16.10 with kubuntu desktop on X5000 ... the opengles wrong colors big endian bug is here


[IMG]https://scontent-mxp1-1.xx.fbcdn.net/t31.0-8/14195353_10207284962863940_4861632354801652103_o.jpg[/IMG]

---

### Post by ernsteiswuerfel on 2016-10-09
As of todays daily iso with its current 4.8.0-x kernel my G5 boots again into the desktop. Just like my other macs.

---

### Post by rican-linux on 2016-10-11
I tried both the Lubuntu and Ubuntu-MATE 16.10 beta 2 on both a PowerBook G4 and a PowerMac G5. In both cases the kernel will load but crash when at the initramfs portion.

---

### Post by ernsteiswuerfel on 2016-10-12
> **rican-linux said:**
> I tried both the Lubuntu and Ubuntu-MATE 16.10 beta 2 on both a PowerBook G4 and a PowerMac G5. In both cases the kernel will load but crash when at the initramfs portion.
They are both too old. You need a current daily iso.

---

### Post by ernsteiswuerfel on 2016-10-13
After reading through several [ppc-bugreports]("https://bugs.freedesktop.org/buglist.cgi?quicksearch=ppc") and tinkering around with xorg-settings on Gentoo and Ubuntu MATE I finally found a config which is working very well on my G5 machine (and probably other G4/G5 Macs with a Radeon AGP-card). It's not fully hardware accellerated but on my G5 the desktop feels a lot more responsive than with default settings. More information at this [thread]("https://ubuntuforums.org/showthread.php?t=2339861").

I am curious if this proves helpful for NVIDIA-users too if they adjust the boot-parameter and the short xorg.conf accordingly?

---

### Post by luigiburdo on 2017-02-02
Now it is a stable release.
I made a video it running on X5000

[https://www.youtube.com/watch?v=wThz_exzsiQ](https://www.youtube.com/watch?v=wThz_exzsiQ)

---

