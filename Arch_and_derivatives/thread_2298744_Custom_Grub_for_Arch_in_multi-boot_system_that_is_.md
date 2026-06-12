---
title: "Custom Grub for Arch in multi-boot system that is maintenance free"
date: 2015-10-13
forum: Arch and derivatives
---

### Post by Cavsfan on 2015-10-13
I customized the grub on my Arch Linux install and wanted to share this with any one who's interested. It's for those who multi boot Arch with Ubuntu or another distro and/or Windows.

[[img]http://en.zimagez.com/miniature/20171119182421.jpg[/img]](http://en.zimagez.com/zimage/20171119182421.php)

Here's a post in the Arch Forum:

[https://bbs.archlinux.org/viewtopic.php?id=200995](https://bbs.archlinux.org/viewtopic.php?id=200995)

You have to be logged in to view it.

Since that thread is closed, I had to post updates here and there have been a few to simplify the whole process.

---

### Post by Cavsfan on 2015-10-29
I thinned the partitions out a bit. :p

[[IMG]http://www.zimagez.com/miniature/20151027143535.jpg[/IMG]]("http://www.zimagez.com/zimage/20151027143535.php")

---

### Post by Cavsfan on 2016-07-25
PNG pictures always work for the background picture whereas JPG pictures sometimes display when grub is updated but not on the screen at boot time.

So, instead of wasting time on JPGs, just edit the picture with GIMP, scale the image to the necessary size and then export it as a PNG picture.

The screen size is what the grub picture resolutions is.

---

### Post by Cavsfan on 2016-09-30
I tried to add the Fallback and LTS kernel lines to grub when I first installed Arch but, must have have not gotten it right.
But I have got it down now and am booted up on the LTS kernel and everything is good. 
```
[cavsfan@le-beast ~]$ uname -r
4.4.22-1-lts
```

I noticed that in /boot there was no LTS kernel so I installed that and the nvidia driver for the LTS kernel.
```
sudo pacman -S linux-lts nvidia-340xx-lts
```

That was the driver I use. This is the contents of **/etc/grub.d/06_custom** (Just the Arch part):
```
#!/bin/sh
    echo 1>&2 "Adding Arch Linux"
    exec tail -n +4 $0
    # This file provides an easy way to add custom menu entries.  Simply     type the
    # menu entries you want to add after this comment.  Be careful not     to change
    # the 'exec tail' line above.
    menuentry "Arch Linux" {
        set root=(hd0,2)
            linux /boot/vmlinuz-linux root=/dev/sda2 rw quiet
            initrd /boot/initramfs-linux.img
    }
    menuentry "Arch Linux (Fallback)" {
        set root=(hd0,2)
            linux /boot/vmlinuz-linux root=/dev/sda2 rw quiet
            initrd /boot/initramfs-linux-fallback.img
    }
    menuentry "Arch Linux (LTS Kernel)" {
        set root=(hd0,2)
            linux /boot/vmlinuz-linux-lts root=/dev/sda2 rw quiet
            initrd /boot/initramfs-linux-lts.img
    }
    menuentry "Arch Linux (LTS Kernel Fallback)" {
        set root=(hd0,2)
            linux /boot/vmlinuz-linux-lts root=/dev/sda2 rw quiet
            initrd /boot/initramfs-linux-lts-fallback.img
    }
    menuentry "Arch Linux (Recovery Mode)" {
        set root=(hd0,2)
            linux /boot/vmlinuz-linux root=/dev/sda2 rw single
            initrd /boot/initramfs-linux.img
    }
    
```

---

### Post by Cavsfan on 2016-11-10
My latest Arch Grub screen with all entries:

[[IMG]http://www.zimagez.com/miniature/20161025132409.jpg[/IMG]]("http://www.zimagez.com/zimage/20161025132409.php")[[IMG]http://i.imgur.com/4x43scIm.jpg[/IMG]]("https://imgur.com/4x43scI")

---

### Post by Cavsfan on 2017-03-23
Whenever Arch installs a newer version of Grub2, it does not update grub but, it does make the original files executable.

So, rather than leave it as is, what I have done is make **10_linux** and **30_os-prober** unexecutable and then updated grub.

```
sudo chmod -x /etc/grub.d/10_linux
sudo chmod -x /etc/grub.d/30_os-prober
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by Cavsfan on 2017-08-11
*Update: If you use an HDMI to HDMI cable, there's is no need to create the font, add the **GRUB_FONT=** line or uncommenting out the **GRUB_GFXMODE=** and matching it your monitor's native resolution in **/etc/default/grub**.

Apparently if you have a DVI to HDMI cable, etc. you do need to but, with straight HDMI, the size of the menu fonts are already the desired size.

If your fonts are huge, you have probably figured this out long ago. 

I however had been using the DVI/HDMI cable and making the fonts were needed but, upon cleaning the PC last time I finally noticed that my nVidia card had an HDMI port. 
Between my son and I, we have a few extra HDMI cables laying around.

---

### Post by yoshii on 2017-09-29
Hey thanks for the info.  I'm wondering if this will come in handy for trying to get Manjaro to dual boot with Xubuntu better.  I haven't tried that yet, but I have read on the Manjaro forums that Manjaro needs to be the "boss" GRUB, or otherwise there is incompatibility.

---

### Post by Cavsfan on 2017-09-29
> **yoshii said:**
> Hey thanks for the info.  I'm wondering if this will come in handy for trying to get Manjaro to dual boot with Xubuntu better.  I haven't tried that yet, but I have read on the Manjaro forums that Manjaro needs to be the "boss" GRUB, or otherwise there is incompatibility.

Actually whichever Linux system Manjaro or Xubuntu is installed last would be in control of Grub at that time.
Because Grub is installed on the MBR (Master Boot Record) during installation.

Section [COLOR=blue]_[1.9]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#If_you_multiboot_mutiple_Linux_installs_and_want_one_Grub_to_control_all_of_your_OSs")_[/COLOR] will show you how to change Xubuntu to install it's Grub on the PBR (Partition Boot Record)

You cannot put Manjaro's grub on the PBR, so nothing you can do will prevent grub from being re-installed on Manjaro.

Unless you take the step above on Xubuntu, grub will be on whatever system runs a **grub-install /dev/sdX**.

---

### Post by Cavsfan on 2017-11-04
Just use your native screen resolution and that will work just fine for the grub background image.
I thought the resolution had to be 1597x1198 like in the example picture but, it does not.

PNG pictures always are better and work every time for me so far.

---

### Post by Cavsfan on 2018-03-16
My previous picture hosting site went down, so here is the most current one I have on Arch Linux:

[[img]http://i.imgur.com/ayLlykPl.jpg[/img]](https://imgur.com/ayLlykP)

---

### Post by Cavsfan on 2018-03-16
There is one thing that Arch Linux does when there is an update to grub that requires intervention and that is it makes all the files in **/etc/grub.d/** executable. 
```
[cavsfan@Le-Beast grub.d]$ ls -l -a
total 80
drwxr-xr-x   2 root root  4096 Mar 16 16:12 .
drwxr-xr-x 113 root root 12288 Mar 16 16:12 ..
-rwxr-xr-x   1 root root  8871 Mar 14 16:56 00_header
-rwxr-xr-x   1 root root  2888 Dec 31 18:14 06_custom
-rwxr-xr-x   1 root root 10400 Mar 14 16:56 10_linux
-rwxr-xr-x   1 root root 10455 Mar 14 16:56 20_linux_xen
-rwxr-xr-x   1 root root 11301 Mar 14 16:56 30_os-prober
-rwxr-xr-x   1 root root   214 Mar 14 16:56 40_custom
-rwxr-xr-x   1 root root   216 Mar 14 16:56 41_custom
-rw-r--r--   1 root root   483 Mar 14 16:56 README
```

So, you need to make **10_linux** and **30_os-prober** unexecutable. Also **memtest86+** if you have that installed.
sudo chmod -x <file-name>...

Since no new **/boot/grub/grub.cfg** file was generated as a result of the update, no further action is required.

---

### Post by Cavsfan on 2018-03-16
If you want the ability to restart and shutdown from the Grub menu, add these to the bottom of **/etc/grub.d/06_custom**:
```
menuentry "System restart" {
    echo "System rebooting..."
    reboot
}
menuentry "System shutdown" {
    echo "System shutting down..."
    halt
}
```

Then enter **sudo grub-mkconfig -o /boot/grub/grub.cfg** to update Grub with these changes.

---

### Post by again? on 2018-03-16
Hi Cavsfan,
I use a custom font in grub created with
```
sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono18.pf2 --size=18 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
```
The side borders are dotted lines using this font.
Looking at your pic the borders don't appear to be dotted lines.
What font do you use?

---

### Post by Cavsfan on 2018-03-17
> **guber2 said:**
> Hi Cavsfan,
I use a custom font in grub created with
```
sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono18.pf2 --size=18 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
```
The side borders are dotted lines using this font.
Looking at your pic the borders don't appear to be dotted lines.
What font do you use?

Hi [COLOR=#000000]guber2!
I used to use this on Ubuntu and Arch Linux:
```
sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 --size=24 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf

```
Then added a line in /etc/default/grub:
```
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2
```[/COLOR]
But, that became huge, too big, when I swapped out my DVI to HMDI cable with an HDMI-HDMI cable.
So, I just took building the font and adding the line to [COLOR=#000000]/etc/default/grub[/COLOR] out and used the default font.

I'll try that and see what happens. Maybe font size 18 will work better than 24 did. 
Plus, putting the font in /boot/grub/fonts/ is probably the default font location for grub anyway.

Since I added Restart and Shutdown I have to scroll down to see shutdown.

---

### Post by Cavsfan on 2018-03-17
@guber2, that will definitely not work. I tried font size 18 like you have and everything was huge again. Only about 4 lines displayed.

So, I tried 12 and that was still too big. I got vertical dashes on the sides but, it displayed less than the default.

Then I tried size 8 and everything did display, all 16 lines but, the font was too small.

I'll just leave it at default. That way you do not have to add the **GRUB_FONT=** line to the **/etc/default/grub** file.

Because as you probably already know, if you do not add that line, it will still use the default font - **/boot/grub/fonts/unicode.pf2** - and you can see that in **/boot/grub/grub.cfg**.

We are talking about Arch Linux and not Ubuntu right? I don't think it matters much concerning the font.

---

### Post by #&amp;thj^% on 2018-03-17
> **Cavsfan said:**
> 
We are talking about Arch Linux and not Ubuntu right? _I don't think it matters much concerning the font_.

+1 Just the size as you already noticed. :)

---

### Post by Cavsfan on 2018-03-17
> **Cavsfan said:**
> We are talking about Arch Linux and not Ubuntu right? _I don't think it matters much concerning the font_.

> **1fallen said:**
> +1 Just the size as you already noticed. :)

What you customized your Grub screen too? :)

Edit: Well actually Arch and Ubuntu do handle grub a little differently e.g. the font colors are in /etc/default/grub.

---

### Post by again? on 2018-03-17
> **Cavsfan said:**
> @guber2, that will definitely not work. I tried font size 18 like you have and everything was huge again. Only about 4 lines displayed.

So, I tried 12 and that was still too big. I got vertical dashes on the sides but, it displayed less than the default.

Then I tried size 8 and everything did display, all 16 lines but, the font was too small.

I'll just leave it at default. That way you do not have to add the **GRUB_FONT=** line to the **/etc/default/grub** file.

Because as you probably already know, if you do not add that line, it will still use the default font - **/boot/grub/fonts/unicode.pf2** - and you can see that in **/boot/grub/grub.cfg**.

We are talking about Arch Linux and not Ubuntu right? I don't think it matters much concerning the font.
I am using a normal DVI connection in Ubuntu and the custom font settings work for me.
_Default font_ (too small)
[ATTACH=CONFIG]278976[/ATTACH]

_Custom Font_ (GRUB_FONT=/boot/grub/fonts/DejaVuSansMono-18.pf2)
[ATTACH=CONFIG]278977[/ATTACH]

I just noticed your grubscreen pic where the text looks larger than normal but maybe just a result of HDMI.
As you seem to have a fair amount of knowledge about customizing grub, was wondering if you knew a font that didn't make dotted side borders?

---

### Post by #&amp;thj^% on 2018-03-18
> **Cavsfan said:**
> What you customized your Grub screen too? :)

.

Well of course I did. :D Can't have just plain old grub. now can we! ;)
> **Cavsfan said:**
> 
Edit: Well actually Arch and Ubuntu do handle grub a little differently e.g. the font colors are in /etc/default/grub.
Picky Picky! :p But True.

---

### Post by Cavsfan on 2018-03-18
> **guber2 said:**
> I am using a normal DVI connection in Ubuntu and the custom font settings work for me.

I just noticed your grubscreen pic where the text looks larger than normal but maybe just a result of HDMI.
As you seem to have a fair amount of knowledge about customizing grub, was wondering if you knew a font that didn't make dotted side borders?

Yes, it must be the DVI connector causing the need to use a different font.
I always had to create the font and point to it in /etc/default/grub.

As I mentioned I used to use this to create the font:
```
sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono.pf2 \
--size=24 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
```

It would give some errors but, still created the font.
Then in /etc/defaut/grub at about line 13 I would insert this:
```
GRUB_FONT=/boot/grub/fonts/DejaVuSansMono.pf2
```

The default font is /boot/grub/fonts/unicode.pf2.

This used to provide me with a perfect Grub menu like the one I posted. But, when I went from DVI-HDMI to HDMI-HDMI things drastically changed.
This computer will be 9 years old in April and came with a DVI-HDMI cable. I replaced the video card and got an HDMI port so I use the HDMI-HDMI cable.

Now, there is no need for me to create the font or plug it in /etc/defalt/grub. If I do the font becomes way too big.

Maybe try that and see what happens. It should work for you.

---

### Post by Cavsfan on 2018-03-18
> **Cavsfan said:**
> What you customized your Grub screen too? :)

> **1fallen said:**
> Well of course I did. :D Can't have just plain old grub. now can we! ;)

> **Cavsfan said:**
> Edit: Well actually Arch and Ubuntu do handle grub a little differently e.g. the font colors are in /etc/default/grub.

> **1fallen said:**
> Picky Picky! :p But True.

:guitar: Cool! If it can be done why not do it? :P

---

