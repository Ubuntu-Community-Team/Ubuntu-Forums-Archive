---
title: "iBook G3 - Getting correct video modes"
date: 2009-01-19
forum: Apple Hardware Users
---

### Post by DurocShark on 2009-01-19
8.04, iBook G3, 640mb

I can't get higher than 800x600x60hz, and with this laptop it just uses the upper left corner, with the rest of the display repeating parts of the main display.

I've added "Modes "1024x768" " to the xorg.conf and it just breaks the gui altogether... "Screen init failed".

I'm betting it's needing a specific driver (Rage Mobility 128 I think). I tried "ati" and "r128" but I may be putting them under the wrong section.

Help?

---

### Post by DurocShark on 2009-01-20
I know there are at least two people out there who have had this problem with Ubuntu or Debian. So here's how I finally got mine working:

I added the following to my xorg.conf
```
	HorizSync 30-65
	VertRefresh 50-75

```

Those numbers may not be accurate for our iBooks, but they work. 

So no more ](*,) . At least, not for this problem...

---

### Post by wolfdragon on 2009-02-18
> **DurocShark said:**
> I know there are at least two people out there who have had this problem with Ubuntu or Debian. So here's how I finally got mine working:

I added the following to my xorg.conf
```
	HorizSync 30-65
	VertRefresh 50-75

```

Those numbers may not be accurate for our iBooks, but they work. 

So no more ](*,) . At least, not for this problem...

ok... so first off hello. ok now i'm a windows convert who decided to take on a challenge. i've got an ibook g3 with ubuntu 8.10 and i'm having this problem. so i found the xorg.conf file, however where in there is the above modification to be added???

---

### Post by captomner on 2009-02-27
> **wolfdragon said:**
> ok... so first off hello. ok now i'm a windows convert who decided to take on a challenge. i've got an ibook g3 with ubuntu 8.10 and i'm having this problem. so i found the xorg.conf file, however where in there is the above modification to be added???

I've been reading ubuntuforums.org for about 2 years now, and for the first time I have something to contribute!

This code should go in the Monitor section. It's imperative that you spell it right, or you won't be able to start your x server.

I can't vouch for this working under 8.10, I personally am sporting 8.04 on a 600 Mhz G3 ibook. Hopefully this still works for you.

Related question: Is there a way to specify the video resolution and refresh rate on the login screen? Xfce and Gnome both work fine with this setting, but the login screen is set to an incorrect resolution with lots of flickering.

---

### Post by anandrajny on 2009-03-08
I've got mine to work with the following quote in xorg.conf

Section "Device"
       Identifier      "Configured Video Device"
       Driver          "r128"
       BusID           "PCI:0:16:0"
       Option          "UseFBDev"              "false"
EndSection

Section "Monitor"
       Identifier      "Configured Monitor"
       HorizSync       58-62
       VertRefresh     75-117
       Option "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Monitor         "Configured Monitor"
       Device          "Configured Video Device"
       DefaultDepth 24
       SubSection "Display"
       Depth 24
       Modes "1024x768"
       EndSubSection
EndSection

---

### Post by Monk22 on 2009-04-19
> **anandrajny said:**
> I've got mine to work with the following quote in xorg.conf

Section "Device"
       Identifier      "Configured Video Device"
       Driver          "r128"
       BusID           "PCI:0:16:0"
       Option          "UseFBDev"              "false"
EndSection

Section "Monitor"
       Identifier      "Configured Monitor"
       HorizSync       58-62
       VertRefresh     75-117
       Option "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Monitor         "Configured Monitor"
       Device          "Configured Video Device"
       DefaultDepth 24
       SubSection "Display"
       Depth 24
       Modes "1024x768"
       EndSubSection
EndSection

this got mine working perfectly thank you.

---

### Post by jtbrookreson on 2009-05-16
I have the same problems with my ibook g3 500 256 RAM. But after looking around, I am finding differnt values and different drivers. So....

1) how do I find out exactly what I need? I bought this iBook used, and am not a Mac guy at all. So I guess I am a bit of a Noob.

2) Do exactly, step by step, do I reconfig everything to be what it should be? Again, I am a noob.

3) Since I was having this problem with Xubuntu 9.04, someone suggested I switch to Debian 5.0 Lenny, and that everything should work "out of the box." They were wrong. Still the same issues, but Lenny is faster and smoother than Xubuntu 9.04, and I would like to keep using it. Am I correct in thinking that since Xubuntu is Debian based, this solution will work with Lenny?

Thankyou for all your help....

-jtb

---

