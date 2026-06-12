---
title: "Installing Edgy on a HP DV9000 laptop"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by BCRailrodder on 2007-01-12
Hi folks,

I am running into a bit of a problem with a dual boot install on a new HP DV9000 laptop.  Research on several sites indicated that it should not be a big problem to install other than a couple of items (such as the built-in webcam) that needed work.

Before getting into the install, I did run the live cd and was able to get most things working (had to boot with noapic).

I then went through and installed the alternative disk - everything working fine just like the other installs that I have done.

While I can boot into XP (not what I want) when I try to boot into Ubuntu, it freezes part way through the boot.  Using grub to boot to the recovery version, I can get to root. 

At this point, I am not even sure what info I can provide to you to help me.

Any and all suggestions welcome :-k as this is needed for an upcoming trip.

Thanks in advance,

Kent

---

### Post by Bachstelze on 2007-01-12
Maybe tell us the last thing you see before it freezes ?

---

### Post by BCRailrodder on 2007-01-14
Sorry about dissappearing - I had an unscheduled run out of town.

Btw - I am using the 2.6.17-10-generic kernel installed from the Ubuntu 6.10 - AMD 64 Alternate disk.

Anyhow - booting up normally with the spash screen hangs sortly after it starts.

Booting up with the generic kernel but editing the boot script to remove the "quiet splash"  hangs at : "Starting kernel event manager..." with the prompt flashing on the far right side.

Booting up with the generic kernel but editing the script to remove the "quiet splash"  and replacing it with "noapic" hangs earlier in the boot sequence at:
[   40.806080] PCI: Ignoring BAR0-3 of IDE controller 000:00:0d.0

Booting up with the generic kernel but editing the script to remove the "quiet splash"  and replacing it with "nolapic" hangs at the same place.

I have found a workaround but I do not have a clue as to why it would work.

Booting up with the generic kernel but editing the script to remove the "quiet splash"  and replacing it with "noapic"  and DELETING the 4th line down marked "quiet" will get me to the login screen at which time I seem to be able to login.

Btw - just editing out the 4th line "quiet" also hangs early in the boot sequence.

I would prefer not to have to do a work around :???: 

Kent

Additional - I found out that I did not have to delete the "quiet splash" from the script - just add nopic and delete the 4th line.

---

### Post by BCRailrodder on 2007-01-15
bump

---

### Post by BCRailrodder on 2007-01-16
Don't quite know how or why but after doing a re-install (I messed something up trying to figure this out), I can now boot straight into the login screen.

Now to try to figure out the wireless issues ](*,) ;)

Kent

---

### Post by mikewhatever on 2007-01-16
Glad you solved the boot problem. What's your wireless card? Perhaps it's better to start a new thread and ask.

---

### Post by PSiX on 2007-01-22
Hello,

I'have detected the same problem, but I do have a turnaround to that. 
The fact is that by disable the wi-fi button (in HP DV9000) before the startup boot of
Ubuntu , the OS correctly goes up and running without any problem.

If the wi-fi is already on before the setup boot, the it will freeze in the middle of the boot progression.

Hope that help

Bye

PSiX

---

### Post by BCRailrodder on 2007-01-28
Hi PSiX, 

Don't quite know if that was it or not but I believe I had booted into the Alternate disc using "noapic".  That seem to have solved the boot problem for me but (now that I am back at the computer) I have several others to research.

Thanks for the suggestion, however, mayhaps it will be of help to someone else.

Kent

---

### Post by watson540 on 2007-03-02
Hey, I had to post back when i saw this. I too have problems with freezing like you do. The noapic seems to work mist of the time, although under feisty for some reason that option causes a lot of cpu usage for no reason.

Anyways, that error you see about BAR03 or whatever, when it freezes early in boot...I was looking for the same thing through google. I found out through some other forum , that all that means is you are booting too fast. It has something to do with the bios not setting up the hard drive irq's in time. If you just wait about 5 seconds it boots fine.

I imagine that is why you think that removing the line 'quiet' works for you, because it takes a few seconds to do that :). Hope that helps, note that i still need noapic so it doesnt freeze starting kernel log

---

### Post by watson540 on 2007-03-06
I wanted to bump this because i still have problems with lock ups. Its a catch 22. you can use acpi=off like everyone says will help, but then my nvidia card complains abpout being edge triggered and wont start x. now there is a way to force this that i read in the nvidia docs. it tells me to change a line. but where do i change this so called line in a binary only package?! i think if i could get it to start while on a edge triggered irq i might have the lockup problem solved

Edit: OK This is wierd. Man I have had lock ups over 30 times today while booting alone. After a myriad of options and countless reboots. I for some reason seem to have it narrowed down to the wierdest thing. I used the option vga=791 in my grub boot options to change the reolution of framebuffer. I did not do this in hopes to solve my problem of lock ups but for some strange reason it seems to keep the system from lockng up!! Is this even feasible? I mean could the resolution have any relation to locking up the pc?? I mean any time i had lock ups (other than booting) would be when in console, never in X. How wierd. Would love an expert opinion

---

