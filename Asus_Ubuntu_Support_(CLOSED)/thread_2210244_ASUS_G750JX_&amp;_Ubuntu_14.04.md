---
title: "ASUS G750JX &amp; Ubuntu 14.04"
date: 2014-03-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by zongosaiba on 2014-03-09
Greetings, 

I am posting for info: 
I have been testing Ubuntu 14.04 on an ASUS G750JX for about two weeks. I have to say, it is a delight. This rig cost me an arm and a leg and came with Win 8.1. I was so unsatisfied with it that I almost sold it back. Then I decided to try Ubuntu Linux 14.04. Am I glad... It is speedy with graphics like I have never seen on Windows 8.1. The sound is crystal clear like I have never heard before when running on Win 8.1. Everything works but the keys to dim the display, keyboard brightness and sound (I guess no suprise there). However, you can dim the brightness and keyboard via the central command in gnome. I even have more battery time than I use to get in Windows. Here is the config: 

Ubuntu: 14.04 
Gnome: 3.10.1 
Kernel: 3.13.0-031300rc1-generic
Graphic: Nvidia Drivers 331.49 (Propriatory) - Unfortunately the nouveau drivers did not cut it. 

If you don't have any obligations to be running Windows, get rid of it and try Linux on this specific rig and you will not be sad you did.  
If I can be of any help, just let me know. 

If you still need Window, you can just virtualize it like I did with Virtual Box :). 

A big thank you to the devs at Ubuntu & Gnome for developping such beautiful and streamline OS and Desktop Manager. 

Kind Regards,

zongo saiba

---

### Post by rifak on 2014-03-09
In order to get the Fn keys working, try putting "acpi_osi=" into /etc/default/grub. This has been enabling support of the Fn keys on a lot of the newer Asus laptops. For reference (in case you're unsure how to do this):

```
gksudo gedit /etc/default/grub
```

Look for this line and make the change:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

```
then save.

Then run:
```
$ sudo update-grub
```
then reboot.

If this doesn't enable the Fn keys, just remove the above acpi_osi addition then update-grub again and reboot.

---

### Post by zongosaiba on 2014-03-10
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=613004")ego-sum-deus, thank you for your reply and help trying to make the Fn key work. You solution enabled the wifi only. The rest, such as brightness for the display, keyboard and volume do not work. I had tried many solutions offered on the internet but to no avail. The funny thing is that all the keys worked under 13.10. When I upgraded to 14.04, nothing worked.  Since the main control in Gnome allows to modify those settings, its most definitely nothing much compare to the upside I am getting using Ubuntu on this rig as opposed to Windows 8.1 :) 

This is the solution that I tried but to no avail to make the Fn key work for display, keyboard brightness and volume key: 

Section &#8220;Device&#8221;
Identifier &#8220;Device0&#8243;
Driver &#8220;nvidia&#8221;
VendorName &#8220;NVIDIA Corporation&#8221;
BoardName &#8220;NVS 3100M&#8221;
**Option &#8220;RegistryDwords&#8221; &#8220;Enable BrightnessControl=1&#8243;**
EndSection

GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux acpi_backlight=vendor"

And your solution:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" --> Allows WiFi to be toggled on or off.

I tried xbacklight but no dice.

Kind Regards, 

zongo saiba

---

### Post by zongosaiba on 2014-03-10
addendum to my last post:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" --> Enable wifi toggle with Fn key but Display Brightness is not working anymore  through the Gnome Control Center. I guess I am going to have to go back to the way it was before.

---

### Post by rifak on 2014-03-10
> **zongosaiba said:**
> addendum to my last post:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" --> Enable wifi toggle with Fn key but Display Brightness is not working anymore  through the Gnome Control Center. I guess I am going to have to go back to the way it was before.

Ah, that sucks. You can string these boot parameters together. For example, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=". Also, you can try all the permutations as well, in addition to another acpi_osi option acpi_osi="!Windows 2012".

---

### Post by zongosaiba on 2014-03-10
I tried as well:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" no dice
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi=Linux". I have again complete control through Gnome Control Center. 

I did try this how to: [http://lajackson2.wordpress.com/2014/01/07/g750jh-backlight-brightness/](http://lajackson2.wordpress.com/2014/01/07/g750jh-backlight-brightness/). No dice there. I do have a different model.

Having a control through gnome control panel is good enough for me. From what I have read on the net, acpi is quit tricky. Everyone has its own opinion on this issue and it seems that the matter being so tricky (may be propriatory), no one really understands the way it works :) Especially me of course.

---

### Post by zongosaiba on 2014-03-12
Ok, so I have modify my setup.
I know have:
3.14.0-031400rc6-generic
Trusty 14.04 - This is a fresh install but still when I go into 'details' tab, it show 13.10. I have no explanations for that. I am attaching a screen shot. If anyone has an explanation for that do let me know. My source file is only filled with trusty and not saucy. After checking on the internet, I am not the only one but no fix yet. The system is perfectly stable.
Gnome: 3.9.90 - I am back using my VPN. Earlier, I was running Gnome 3.10.1 and could not use my VPN (OpenVPN) anymore. Now, its back to normal

As far as the Fn key for brightness on Keyboard + Display and Volume Keys, they all work except the display brightness. I have not yet investigated but will do and post back. 
The bluetooth is not working. I have looked for a solution on the internet but to no avail.

---

### Post by zongosaiba on 2014-03-23
So I am back  to give some feedback:
I now run 3.14.0-031400rc7-generic. I still have gnome 3.9.90. All keys now work but the display brightness. I can lower the display brightness through Gnome main control center. Bluetooth is still not working out the box. I haven't really look into it yet.  Anyways, this rig now turns out to be really sweet the way it is set up with Linux.  I still would encourage any one with this rig (model G750JX) to make the switch from Windows. It is most defenitly worth it. Just keep in mind that there is still a learning curve and you must be willing to put some time into learning new thing.  If you need my help (eventhough complete noob) feel free to contact me. If I can help, I will :) 

Peace and Love to all 

zongo saiba

---

### Post by UpSignal on 2014-05-15
> **zongosaiba said:**
> So I am back  to give some feedback:
I now run 3.14.0-031400rc7-generic. I still have gnome 3.9.90. All keys now work but the display brightness. I can lower the display brightness through Gnome main control center. Bluetooth is still not working out the box. I haven't really look into it yet.  Anyways, this rig now turns out to be really sweet the way it is set up with Linux.  I still would encourage any one with this rig (model G750JX) to make the switch from Windows. It is most defenitly worth it. Just keep in mind that there is still a learning curve and you must be willing to put some time into learning new thing.  If you need my help (eventhough complete noob) feel free to contact me. If I can help, I will :) 

Peace and Love to all 

zongo saiba

Hi, have you already solved the issue with the brightness?
i have an asus s56CM ultrabook, and that's the issue too. Worked well with ubuntu 13.10 though

---

