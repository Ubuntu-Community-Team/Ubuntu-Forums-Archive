---
title: "Installing Brother HL-1440 Printer"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by alex1001 on 2008-02-01
Hello, I'm having quite a bit of trouble installing my Brother HL-1440 Black and White Laser Printer on my 7.10 Gutsy Gibbon.

I have looked all over the forums and across the internet, and none of the ideas worked for me. I tried the howto guide here:[ http://ubuntuforums.org/showthread.php?t=105703]("http://ubuntuforums.org/showthread.php?t=105703") but when I tried to install the LPR Driver for the HL-1440 (under "Debian" on the Brother website) I got installation errors and was unable to continue.

I connect my printer via USB, but the computer doesn't recognize anything, and my printer isn't a choice in System-->Printing.

I would really appreciate any help. I am an absolute beginner, so a lot of this coding is over my head. If anyone has any ideas or steps I should take to solve my problem, I would be very grateful.

Thanks!

---

### Post by alex1001 on 2008-02-01
So I went here and downloaded the recommended driver for my hl-1440 and saved the ppd (no idea what a ppd is, but regardless) into a folder on my desktop I named "hl1440." I got the driver off this site:
[URL="http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440"]
http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440[/URL]

Now I have a ppd in the folder, then I open it (this through the gedit application), and then I save it without any changes. How would I proceed from here? Would I install it from the terminal?

Thanks

---

### Post by alex1001 on 2008-02-01
Alright, I think I messed up :|

Now when I try to open Synaptic Package Manager, I immediately get:

"E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Then it closes.

Any ideas?

---

### Post by plucky on 2008-02-01
alex1001,

This [thread](http://ubuntuforums.org/showthread.php?t=636455) might help.

Good luck

---

### Post by alex1001 on 2008-02-01
Thanks for the help! My printer now prints, which is a big relief, but I'm still having some trouble when I open the Package Manager, I'm still getting that error message.

I've been looking around for answers, still have yet to dig up something that works, I tried the method here: [https://answers.launchpad.net/ubuntu/+question/22818]("https://answers.launchpad.net/ubuntu/+question/22818")

but it doesn't work for me.

I tried the following:

sudo touch /etc/init.d/lpd
sudo apt-get purge hl1440lpr

but got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.

Then I tried installing the HL-1440 Debian Driver from the Brother website : [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

When I try to install, it tells me:

Could not open 'cupswrapperHL1440-1.0.2-1.i386.deb
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

I then tried to make a symbolic link as the Brother website recommends:

ln -s /etc/init.d/cups /etc/init.d/lpd
ln -s /etc/init.d/cupsys /etc/init.d/lpd

However, it got me nowhere.

Any ideas?

Thanks again for your help.

---

### Post by alex1001 on 2008-02-01
Anyone else had a similar problem?

---

### Post by plucky on 2008-02-02
alex1001,

Been looking around to try to solve your problem.Have you tried to install the printer in **System > Administration > Printing**. I believe the driver for the HL-1440 is in there.

Also try this in a terminal screen```
sudo dpkg --reconfigure -a
``` and ```
sudo apt-get install -f
```. These commands are used to fix errors in Synaptic package manager.Problem is I don't know if they will fix your error as you installed the drivers seperately.I don't think there is any harm in trying them .

Good luck

---

