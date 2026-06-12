---
title: "Ubuntu 10.10 and Mac Mini 4,1"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by GNUinU on 2010-10-31
Hey everyone.
I've got a Mac Mini 4,1 and just a few minutes ago tried to boot from a recently downloaded 10.10 installation disc.

I got to the Language selection screen, selected Spanish and also chose it to try Ubuntu instead of installing it.

Everything looked fine till the screen turned off itself without showing a thing. The Mini's DVD kept reading, but nothing happened. I decided to wait, but after some minutes the disc stopped spinning and couldn't do anything, so had to hard reset the Mini to boot into Mac OSX again.

I've read this is a known issue with 10.04, but it's supposed to be solved with 10.10, isn't it? The only "not regular" thing I've done is using a bluetooth mouse and keyboard. I've got no USB ones, so can't try with them.


Any ideas?


Thanks!

---

### Post by linuxopjemac on 2010-10-31
I don't know for 10.10, but it should work with a patched kernel of 10.04:

[https://help.ubuntu.com/community/Macmini4-1/Lucid](https://help.ubuntu.com/community/Macmini4-1/Lucid)

---

### Post by GNUinU on 2010-10-31
Thanks for your reply.

Yeah, I know about the 10.04 kernel patch, but just take a look:

[/community/Macmini4-1/Maverick]("https://help.ubuntu.com/community/Macmini4-1/Maverick")

They don't even mention any kernel or booting issues.

---

### Post by linuxopjemac on 2010-10-31
I read

**Installation tested only with the alternate i386 cd. **

---

### Post by GNUinU on 2010-10-31
> **linuxopjemac said:**
> I read

**Installation tested only with the alternate i386 cd. **

Uhmm... How could I get that exact version?

Thanks!

---

### Post by linuxopjemac on 2010-10-31
if you are happy with a server in The Netherlands:
[http://nl.releases.ubuntu.com/releases/10.10/ubuntu-10.10-alternate-i386.iso](http://nl.releases.ubuntu.com/releases/10.10/ubuntu-10.10-alternate-i386.iso)

---

### Post by Jeisson on 2010-10-31
GNUinU. In order to download the alternative version, click the [alternative link]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") in the downloads section of Ubuntu web site. The alternative installation will work fine in mac mini 4,1 with wired connection but it is unable to reboot the computer, shut down option works well but it is not explicitly available.

Anytime I tried to run Ubuntu in graphical mode, the screen goes blank and the reboot option freezes the mac mini. It can be solved adding two parameters to the kernel (suggested by [Shii0]("http://art.ubuntuforums.org/showpost.php?p=9976695&postcount=15")):

```
nomodeset reboot=pci
```

If you run the graphical installation you should provide those parameters, I believe the F6 option is the mechanism to input them (I did the alternate installation).

Once your system is installed, you should make those parameters permanent. For the first time Ubuntu will run, keep Ctrl key pressed while your computer is booting in order to see the GRUB menu. Select the first option and press the "e" key to edit the entry. Add the parameters at end of line:

```
linux /boot/vmlinuz-2.6.35-22-generic[...] nomodeset reboot=pci
```

When Ubuntu has started, use your wired connection to get the nVidia drivers and wireless drivers (menu System|Administration|Additional drivers).

Now, make permanent the kernel parameters. Edit the /etc/default/grub file: press Ctrl+F2 and call your favorite editor with administration privileges. Something like:

```
gksudo gedit /etc/default/grub
```

Locate the eight line and append the parameters:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset reboot=pci"
```

Save the file and update the grub running "sudo update-grub" in terminal or "gksudo update-grub" in Ctrl+F2 dialog. Now you can reboot safely.

So far, my wireless connection is not working yet. I do not see my wireless network. Ubuntu does not detect it and the ifconfig command does not show any entry for wireless.

Edit: Sound works doing the trick indicated [here]("https://help.ubuntu.com/community/Macmini4-1/Maverick").

I hope this information helps you.

Best regards
-Jeisson

---

### Post by linuxopjemac on 2010-10-31
This is very helpful. Good work Jeisson.

---

### Post by GNUinU on 2010-10-31
Thank you very much for your reply, very complete.
Will try it out without a doubt. 

Cheers.

---

