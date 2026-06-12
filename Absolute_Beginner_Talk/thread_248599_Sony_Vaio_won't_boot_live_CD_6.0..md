---
title: "Sony Vaio won't boot live CD 6.0."
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by cianclarke on 2006-09-01
I've been having trouble booting ubuntu 6 live on my Sony Vaio FX301, and I'm wondering if anybody can help.

Specs:
128mb RAM
800mhz AMD
10gb HD

And after that I'm not too sure. 

I put in the boot CD, and up comes the ubuntu menu. From searching this forum, I try to boot the following way:
Push F6 to, up comes the boot options (boot=casper etc etc etc). 
After this I add the following:
acpi=off noapic nolapic
I also add pnpbios=off, as one of the error messages I have been recieving instructs me to do so. 

All in all:
acpi=off noapic nolapic pnpbios=off


Is this the right place to add these extra tidbits? I know nothing about linux, just presuming this is where I add them. 
I then push enter, and wait for boot. 
Once the linux kernel bit has loaded I push alt+F1 so I can see the text, and any errors that come up. 

The next error is:
[ 540.353265] Buffer I/O Error on device hdc, logical block 178768

This can repeat a few times, the numbers change... 


So, I give up on the advice on the forums. I try to boot with just the following entered in the F6 options menu:
pnpbios=off

After a fair while (about five minutes) I get to the ubuntu brown background with the mouse, and it says it's loading "window manager". Here it seems to stall, the CD just keeps reading. 
I can get into the console piece by pushing ALT +F1, but it takes  10 seconds or so to appear. It doesn't mention any errors, gets to the line "see "man sudo_root" for details." and just sticks. 


Any ideas? I know *nothing* about linux I'm afraid, hoping to learn! Loving the look of ubuntu, boots fine on my newer laptop but I just want to install it on the old one. I've had a whole host of various error messages appear in my attempts to install, and I'm wondering if anybody has any ideas.

Thanks

---

### Post by benfindlay on 2006-09-01
If you're trying to install it on the laptop I suggest you download the alternate installation disc. Your specs (very much like my old laptop) would be more suited to a text based install. However, do not panic, as "text based" doesn't mean that you're just dumped at a command line and expected to fend for yourself. It guides yo through the entire installation with minimal graphical flair. And when it comes to settings, you're just required to type in what you want, and confirm various settings with the Enter key.  Also I'd recommend installing xubuntu perhaps, since your machine is a little low on RAM. Other than that it should work fine!

Hope this helps!

---

### Post by dsimon on 2006-12-13
I'm new to Ubuntu, but I've been a computer tech for over a decade.  My brother recently gave me a Sony Vaio (P2, 128MB RAM, it's a tower not a laptop) and I tried to run Casper.  I got the same results as you did, until I unplugged the DVD/CD-RW and Zip drive and used a plain old CD-drive.  This got me all the way to the desktop.  I haven't gone much farther than that because of a lack of time so I can't tell you if it is a driver or hardware problem with the Sony equipment.  Even if I knew I don't know how to solve the problem.  Maybe someone with more experience with Ubuntu can take it from here. I hope this helps.

---

