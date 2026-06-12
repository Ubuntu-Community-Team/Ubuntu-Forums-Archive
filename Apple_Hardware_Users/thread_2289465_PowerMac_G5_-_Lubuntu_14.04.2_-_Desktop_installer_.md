---
title: "PowerMac G5 - Lubuntu 14.04.2 - Desktop installer freeze - Black screen with cursor"
date: 2015-08-04
forum: Apple Hardware Users
---

### Post by asmodeus3 on 2015-08-04
Hello Ubuntu Forums.

I'm new here and although I have had some previous experience with Lubuntu, I still consider myself a newbie to the Linux universe.

I am currently trying to install Lubuntu trusty 14.04.2 LTS on an old Powermac G5 ( that pc is all I have for now [COLOR=#000000][CENTER]:roll: ).[/CENTER]
[/COLOR]
The computer boots fine from a live DVD and I can get to the Lubuntu desktop using the parameter *"nouveau.modeset=0" *on the Yaboot boot menu.
The problem is the colors of the display. The colors are "psychedelic", as described under the "Configure graphics" section of this FAQ: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) 
The FAQ suggests setting a different framebuffer with *"fbdev"*, which has to be specified in the x*org.conf*, or specifying the nv driver in the same file.
A little lost and afraid to proceed on my own with this because I will practically not know what I'm doing.
 
On top of all this, when I try to launch the Lubuntu installer from the desktop, the window becomes transparent, it doesn't seem to respond and I have trouble killing the process. As a consequence, I can't even begin the installation process.
Im not sure whether this is a window transparency issue and thus connected with the above or an indication that the DVD was badly burned.
I will try burning a disc again to check if it helps at all.

Specs for the ***Power Mac G5 1.6 (PCI) ***can be found [here]("http://www.everymac.com/systems/apple/powermac_g5/specs/powermac_g5_1.6.html").
The video card is an nvidia*** GeForce FX 5200***.
I am using an LG L1753S monitor.

All input will be greatly appreciated, so thanks in advance.

---

### Post by howefield on 2015-08-04
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by asmodeus3 on 2015-08-05
Just a quick update:I tried installing from another DVD but encountered the same problem, so maybe the badly burned disk possibility can be ruled out.

---

### Post by asmodeus3 on 2015-08-08
I finally installed Lubuntu using the Alternate 14.04.1 PowerPC iso. This allowed me to bypass the issue I had with the graphical/desktop installer but I stumbled upon a new issue. I can again go past the splash screen (which pops up some unrelated(?) errors), but I'm now greeted by a blank screen and a "psychedelic" cursor.
The terminal is accessible with *Ctrl+Alt+F1. *I tried starting the *lxpanel *but got a *"Gtk Warning :cannot open display" *error. Next thing I tried was booting with some parameters: 

*Linux video=ofonly *results in a blank screen and an inaccessible terminal.
*Linux nouveau.modeset=0* doesn't alter anything. (I think it is set permanently)

Any directions?

---

### Post by este.el.paz on 2015-08-08
Asmodeus3:

Sounds like you should look thru the "PowerPCFAQ" and read relevant material on setting up an xorg.conf file . . . you can use TTY terminal and run something like "sudo xorg -configure"  OR "sudo -configure xorg" . . . something like that, you have to "stop lightdm" first, so if you are in the GUI console you would be typing in the dark--TTY remains operational, I believe.

But, there seem to be some "special handling" for the PM G5, I have an olde G4 so I haven't been following the threads on it, but look or search the forum or Google for threads including screen names, "rican-linux," "luigiburdo," and "xeno74" ??? I believe they have been wrestling with getting Ubuntu Mate running on G5's . . . and there might be some help for you there.

Another option is to try first with a 12.04 flavor and do the install of that system, I'm still running 12.04 on my PM 3,1 . . . still got some updates last weekend.  And, then, if all goes well you **could*** do the 14 upgrade through "Software Center" . . . every time I boot 12 I get a window asking me if I'd like to upgrade to 14.04 . . . it just takes longer doing it that way, unless you have a superfast internet connection.  But, 12.04 is very good for PPC, should boot up with no boot params . . . .  Also, you mentioned the "nv" driver, that used to be the best choice for us, but apparently it isn't available any more, so "fbdev" is fine . . . .  Best to read through the FAQ for the details.

e..

---

### Post by asmodeus3 on 2015-08-09
Thanks for replying Este.

> Sounds like you should look thru the "PowerPCFAQ" and read relevant material on setting up an xorg.conf file

I already tried generating a xorg.conf .  Booted into single user mode and tried *"sudo Xorg -configure"*. The funny thing is I got dismayed by the 
*"number of created screens does not match number of detected devices" *error and didn't bother reading further into the FAQ, where it said that the file is generated nevertheless, despite the error message. Very silly of me. I will go FAQ myself and report back as soon as possible.

---

### Post by este.el.paz on 2015-08-09
> **asmodeus3 said:**
> Thanks for replying Este.

I already tried generating a xorg.conf .  Booted into single user mode and tried *"sudo Xorg -configure"*. The funny thing is I got dismayed by the 
*"number of created screens does not match number of detected devices" *error and didn't bother reading further into the FAQ, where it said that the file is generated nevertheless, despite the error message. Very silly of me. I will go FAQ myself and report back as soon as possible.

Asm3:

OK, thanks for posting back, yes, there is a certain "attentive ignorance" that is needed when dealing with linux install--knowing when to pay attention and when not to, is key.  Seems like you are in the ballpark on getting it done; it might be mainly in the "3D acceleration" area that the G5 has some issues.  Also responding to the first post, it did seem that there were some issues with the installer from liveDVD on Lu and U-mate, so using the alternate or mini installers seem to fix that problem--don't know if that has been fixed in 14.04.3 yet or not . . . . .

e..

---

### Post by asmodeus3 on 2015-08-15
Update: I tried specifying the *"fbdev"* driver in the *xorg.conf* file and starting with other framebuffers and managed to get a normal looking white cursor.
However, the desktop environment was still not showing up and any try to invoke it through the terminal failed.
For that reason, I tried to give Pangolin a try. The computer finally booted to a "psychedelic" desktop. From here, I will try the latest *"nouveau"*, compiling *"nv" *and *"fbdev"* as a last resort. Lets see where this goes.

---

### Post by rsavage on 2015-08-16
[https://wiki.ubuntu.com/PowerPCKnownIssues#A12.10_Quantal_Quetzal](https://wiki.ubuntu.com/PowerPCKnownIssues#A12.10_Quantal_Quetzal) specifically the section "Lightdm displays a blank screen when used with 8 bit pseudo colour"

---

### Post by asmodeus3 on 2015-08-16
Thanks for the input rsavage. I believe I did raise the colour depth because the cursor turned normal. I'm not sure whether I restarted the desktop service though.

EDIT :

I decided to look into 14.04 again. Will try raising the colour depth with *nouveaufb* and *fbdev*. Restarting the desktop might do the trick. My only question is : in the FAQ it is stated that *"fbdev"* must be specified in the *xorg,conf* file. Is there anything else I need to do, other than replace *"nouveau"* with the *"fbdev"* driver under the device section? 

Also, as a side-note ( and excuse me if I'm stretching this thread too far ), is there any significant performance difference between *nouveau, nv* and *fbdev*? I know that *nv* doesn't support 3D acceleration but nothing more. I have also read that it is best to avoid fbdev initially and only use it as a last resort. Why is that?

---

### Post by asmodeus3 on 2015-08-16
Hooray !

I am posting this message from inside Lubuntu .

Solution : 

Boot into single user mode and specify "fbdev" in the xorg.conf file as suggested by the FAQ. Just replace the *"nouveau"* driver
with* "fbdev"* under the *"Device"* section. Save and reboot.

On the Yaboot prompt type : ***Linux video=offb:off nouveau.modeset=0 single.***
 After that the screen freezes or turns to black but TTY will remain active.
Wait for a minute or so for the computer to boot.
Type in the dark : ***modprobe nvidiafb mode_option=1280x1024-32*** and the console should appear. ( replace 1280x1024-32 with your resolution ).
After that use : ***start lightdm*** and the login screen should appear.

You can also use rivafb. Im not sure about nouveaufb.

---

