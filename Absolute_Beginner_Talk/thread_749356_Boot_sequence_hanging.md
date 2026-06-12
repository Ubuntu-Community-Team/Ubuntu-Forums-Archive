---
title: "Boot sequence hanging"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by grazed on 2008-04-08
Hi. 

So, this is about my third time over the past year and a half that I have tried to install ubuntu over 3 different machines. First one constantly crashed every 5 minutes, the second would never recognize the laptop monitor, and now this. I think I'm about to throw in the towel with linux. -_-

I spent the past two days setting up my install with drivers, eye candy and the such. Then last night I got a random lockup while browsing screensavers. I rebooted, only to never get past it.

The machine boots, runs the loading bar, does a fcsk disk check, then hangs. It seems to always get stuck after the line that says "Loading ACPI modules"... or something to that effect.

I tried all of the available boot options to no avail, all having the same result. This is the second time this has happened on this machine.. The first being after a crash during updating... accidentally closed my laptop screen. =/ So it seems to only happen after a crash. I can't keep uninstalling every time my system crashes.

Is there anything I can do? any help would be deeply appreciated.

also, I'm running Hardy through wubi. The first time this happened it was on a partition, so I don't think it has anything to do with wubi.

Thanks!

---

### Post by philinux on 2008-04-08
I'm surprised you're running hardy this way. It's not ready for primetime. 

It breaks. But anyway post here.

you'll get better info.

[http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

---

### Post by grazed on 2008-04-08
gutsy crashes my system every 5-10 minutes so i don't have much choice. =/

I found this...[http://ubuntuforums.org/showthread.php?t=116297&highlight=acpi%3Doff](http://ubuntuforums.org/showthread.php?t=116297&highlight=acpi%3Doff)

any way to apply that before booting?

---

### Post by spiderbatdad on 2008-04-08
Read the output of ```
dmesg
```from the terminal. I believe you will see a line to the effect: ACPI disabled by system BIOS...try 'lapic' to fix the problem.

Follow the steps I posted in this thread...beginning around post 7 (i think) and continued on page 2.
[http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)

Hint: you  will add lapic to the kernel line.

---

### Post by grazed on 2008-04-08
well, I would be happy to show you the terminal output but as I said i can't actually get into ubuntu. It hangs in the middle of loading. Is there a way to access the terminal from the boot menu?

I edited my grub menu file through windows and added the change you suggested... but it still hangs on "Loading ACPI modules"

---

### Post by spiderbatdad on 2008-04-08
From the grub menu press 'e' to edit. Then arrow key down to the line that begins with 'kernel.' Delete 'ro --quiet splash' insert 'lapic'. Press 'b' to boot. Wait several minutes. After system starts run ```
sudo update-initramfs -u
``` Reboot.

---

### Post by grazed on 2008-04-08
I tried that, it looks like that line already had that code in it though from when i edited the grub file.

it's still hanging on loading acpi modules.

I'm guessing... I need to enter a command or line into the grub file that disables API?

if not I think I'm about to wipe my hands of this. I can't see so much time and effort just to get an OS to start properly on common hardware.

---

### Post by spiderbatdad on 2008-04-08
try noapic nolapic  be sure to remove 'ro --quiet splash'

lol...there is no common hardware. Ubuntu is available factory installed by Dell now. And several other manufactuers...Asus...

---

### Post by grazed on 2008-04-08
that worked! kinda.

that leaves me with text followed by a whole string of Init errors saying...

username-laptop login:

thank you very much for your help by the way.

---

### Post by spiderbatdad on 2008-04-08
I would try logging in and fixing /boot/grub/menu.lst
Then run sudo update-initramfs -u

If you could then post your computer specs and upload dmesg as an archive maybe we can get everything running smoothly

---

### Post by grazed on 2008-04-08
It doesn't let me login.

when I get that prompt, I try to enter my password, but it just keeps repeating itself.

---

### Post by spiderbatdad on 2008-04-08
What happens if you try to boot into the recovery option?

---

### Post by grazed on 2008-04-08
It displays a huge wall of foreign characters. o_O

---

### Post by spiderbatdad on 2008-04-08
lol.  Try booting off the live cd...make sure cd is set as the first boot device.
If you get Desktop, open the terminal and enter su yourusername. I believe that will work.
Its been a while since I've tried this. If you get your user login, then proceed to fix grub...
It's hard to diagnose the needed parameters with out dmesg, so try to get that posted as an archive please, as it is quite long.

If you know how to irc, I could talk to you on #ubuntu

---

### Post by grazed on 2008-04-09
I'm going to install the 64bit version on a fresh hdd. I'll force myself into a crash and see if the problem persists.

thank you VERY much for your help. I'll report back. =)

---

### Post by grazed on 2008-04-10
well, just as i anticipated I am now again unable to boot into Ubuntu again... for the fourth time, in four days, in four seperate fresh installs. this is unreal.

this time like all others, I randomly crashed in the middle of updating, rebooted, and now getting stuck. 

I run through the normal boot sequence, and this time it starts repeating itself saying "checking battery state"

over..and over..and over.. until I get a super low res version of my logon screen. after logging in I get nothing. just sits there. I tried booting into recovery mode, same deal.

I really just don't understand why this is happening. Mind you I have had issues now over 3 different Ubuntu install types. 32bit through wubi, 64bit through wubi, and two 64bit installs on a fresh partition. All having issues randomly crashing while updating, then refusing to let me into a desktop environment afterwards.

Let's add to that and say the time I tried the 6.x releases I could never get my laptop monitor to be recognized over numerous installs and mind numbing hours, as well as the 7.x releases hard crashing every 5 minutes at will on 2 different dell machines. Now this. 

3 different machines. Almost 2 years and around a dozen Ubuntu installs and I STILL cannot get a working system.

Time for another distro.

sorry for the rant, but this is annoying. If anyone can suggest anything to do I'll give it a go, but this is my last shot.

thanks.

---

