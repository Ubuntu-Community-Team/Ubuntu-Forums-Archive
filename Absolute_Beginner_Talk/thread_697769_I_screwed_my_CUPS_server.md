---
title: "I screwed my CUPS server"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Cotopaxi on 2008-02-15
I am using Kubuntu 7.1

In one of my may desperate attempts to install a Brother MFC-5440CN, I ended up screwing the cups server. For this Multifunction printer Brother offers only "..i386.*" drivers and I have been trying arround like mad. 

I cannot acces the localhost://631 anymore and under "System Settings" I cannot add a printer any more.

Is there any way to fix this mess, or shall I just wipe the Hard Disk and make a clean installation?

If the CUPS Server can be fixed, how could delete all the previus installations of CUPS -wrappers and -drivers, in order to clear up the mess a bit?

Thanks for your help!

---

### Post by kellemes on 2008-02-15
Is "ps -auxw | grep cups" showing cupsd is running?

"/etc/init.d/cupsys start" may fix it.

---

### Post by Cotopaxi on 2008-02-15
sorry, what does "ps -auxw | grep cups" mean?

In the terminal I typed: "sudo /etc/init.d/cupsys start"

But even though I cannot acces the printer manager nor can I acces "http://localhost:631"

Thanks anyhow for your fast reply!

---

### Post by kellemes on 2008-02-15
> **Cotopaxi said:**
> sorry, what does "ps -auxw | grep cups" mean?

In the terminal I typed: "sudo /etc/init.d/cupsys start"

But even though I cannot acces the printer manager nor can I acces "http://localhost:631"

Thanks anyhow for your fast reply!

Just type "ps -auxw | grep cups" in the terminal.
Is there a cups process running?

---

### Post by crf on 2008-02-15
Cups saves your old config file and the default config file in /etc/cups
You should be able to either revert to a working old config file, edit it to enable any changes you wanted, or start afresh from the default config file.

Cups recently had a bug that could crop up when working from the http interface.
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/188426](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/188426)

cups stores its logs in /var/log/cups/

---

### Post by Cotopaxi on 2008-02-18
So far, thanks for your help. The interesting challenge (you know, there are no problems, only interesting challenges) I have now is that I the adept package manager ran an uprgrade and restarted the system during the upgrade. After rebooting the adept package manager disappeared completely!

I will now try to follow your advices.

Thanks again!

---

### Post by Cotopaxi on 2008-02-18
Ok, I managed to solve the problem.

It looks like my KDE-core got shot down, so in the Terminal I just typed:

"sudo apt-get install KDE-core"

After this I typed:

"sudo apt-get install adept"

Then from the adept-manager I reinstalled all the CUPS files.

Again, Thank you very much indeed for your help! :KS :D

Now one last question: How do I mark this problem as solved?

---

