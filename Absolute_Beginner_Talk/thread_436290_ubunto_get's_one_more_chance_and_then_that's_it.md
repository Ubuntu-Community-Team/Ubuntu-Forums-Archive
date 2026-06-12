---
title: "ubunto get's one more chance and then that's it"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-07
I am one extreemly frustraited little lemming with my experiences of this allegidly hastle free operating system.

At around 9 20 pm (which was the time on the monitor clock) I pottered off into another room for an hour and a hald to mess around on my laptop and when I returned to my PC I found that it had froze, AGAIN!

I have waisted 48 hours of my life trying to get this operating system to work.  Tomorrow I will try and install an earlier version and if that does not work then that is it.

I have to admit that I have been exceptionally tollerent at trying something new and believed all the hype on this site along with comments from various IT professionals that Linux was the way to go.  All I have experienced is failed install after failed install as well as frozen set-up after frozen set up.

Please excuse my frustration but if anybody can point me in the direction of a company or professional body who can help me resolve this issue then I would appreciate it.  I don't even mind paying as long as I get positive results.

However, if I can't get the previous version of ubuntu to work then I'm going back to Microsoft and live with all its faults, which I have to say are minor compared to my last 48 hours.

:(

---

### Post by Bachstelze on 2007-05-07
Maybe Ubuntu just doesn't like your hardware. If you don't want to go back to Microsoft, there are many othert Linux distros out there :)

---

### Post by fakie_flip on 2007-05-07
> **the lemming said:**
> 
Please excuse my frustration but if anybody can point me in the direction of a company or professional body who can help me resolve this issue then I would appreciate it.  I don't even mind paying as long as I get positive results.
:(

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by fakie_flip on 2007-05-07
But if you want free help, you may look for a LUG in the area you live, and bring your computer to one of their meetings.

---

### Post by rygar on 2007-05-07
whoops

---

### Post by wormser on 2007-05-07
> **the lemming said:**
> I am one extreemly frustraited little lemming with my experiences of this allegidly hastle free operating system.

At around 9 20 pm (which was the time on the monitor clock) I pottered off into another room for an hour and a hald to mess around on my laptop and when I returned to my PC I found that it had froze, AGAIN!

I have waisted 48 hours of my life trying to get this operating system to work.  Tomorrow I will try and install an earlier version and if that does not work then that is it.

I have to admit that I have been exceptionally tollerent at trying something new and believed all the hype on this site along with comments from various IT professionals that Linux was the way to go.  All I have experienced is failed install after failed install as well as frozen set-up after frozen set up.

Please excuse my frustration but if anybody can point me in the direction of a company or professional body who can help me resolve this issue then I would appreciate it.  I don't even mind paying as long as I get positive results.

However, if I can't get the previous version of ubuntu to work then I'm going back to Microsoft and live with all its faults, which I have to say are minor compared to my last 48 hours.

:(

IMHO Ubuntu is not for every one yet.  It is getting more user friendly each day.  If you do drop Ubuntu go to Mac OS X.  It is unix based also which makes it more secure than windows.  Then come back to Ubuntu in a year and give it another try.

---

### Post by Mitlik on 2007-05-07
What have you tried to trouble shoot the problem? The LiveCD offers a self checking feature that you can use to see if your ISO was corrupted. Or tried hanging out in the LiveCD environment for a prolonged period of time, maybe surf the web or try an Openoffice document to see how it handles it. Have you checked to see if there are other people with your hardware experiencing problems? What other things are you trying that might have caused it to freeze up when it actually does install? Ubuntu does have some faults, like my computer won't load the grub or tty properly if I have any memory media hooked into that isn't a hard drive (like cds or usb flash memory) or is the freeze caused by your computer going into standby/hibernate? Are you installing third party video drivers? All of these are things that could cause problems. Most are post installation. 
You haven't outlined what is going on, I (nor anyone else) knows how you are set up and why that might cause problems.

---

### Post by PhatStreet on 2007-05-07
I get the feeling you might want to try disabling APIC. When the GRUB boot menu comes up, edit the Ubuntu entry and add "noapic" without quotes to the end of the longest line. I've had APIC issues with two computers now, and Ubuntu works great on both of them now.

---

### Post by use a name on 2007-05-07
There are some boot options that can stop freezes: noapic, acpi=off. Even nosmp can save your day.

You can test them by editing the /boot/grub/menu.lst file and adding them to the line with the kernel, or you can insert them at boot-time by editing the grub menu entry (will not be saved, so is more safe to test).

Here's a more complete list: [http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html) (There may be newer versions around...)

---

### Post by TDogg310 on 2007-05-07
I am having the very same problem.  My computer is a dual boot, and I have been using Windows Vista more often than I would prefer.  If I use Ubuntu for too long, then it will freeze and I have no choice but to press the power button.  My guess is that this is a keyboard/mouse bug, because all of the sudden I will be unable to move the cursor.   I am using the 32-bit version of Feisty Fawn on an HP DV6000t with a 2 GHz Core 2 Duo.  My assumption has been that this problem will be fixed with an update in the near future.

---

### Post by ghostofcain on 2007-05-07
same problem occurring for me, but only since Friday night! (possibly an issue with a recent update?). This is a real issue as I am unable to use Ubuntu at present. Up until Friday I had been using Feisty since the beta version with no issues, will try disabling ACPI but if not I will reluctantly begin the search for a different Distro:(

for more details see my posting to [Bugtracker]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91192")

---

