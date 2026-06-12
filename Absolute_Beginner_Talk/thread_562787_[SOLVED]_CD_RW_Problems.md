---
title: "[SOLVED] CD RW Problems"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by TrevP on 2007-09-29
I'm currently running Ubuntu 7.04 and have been ever since it was released. I have had no problems whatsoever up to now, but now when I put a blank disk into my CD RW drive, the "blank disc" icon appears and I am invited to make either an audio or data disk as normal. However, when I try to write the disc, the program just asks me to insert a blank disk.

Obviously something is wrong - does anyone know if there is any package I can re-install to correct this problem? I can't understand why this has happened as it worked perfectly previously.

---

### Post by por100pre1 on 2007-09-29
It would be good to know which burning programs do you use. I remember a similar issue with Gnomebaker, so if you have it installed try that one first.

---

### Post by TrevP on 2007-09-29
Hi,

I'm just using the standard tools that come with hte Ubuntu installation. I did try installing gtoaster but I have uninstalled it now.

---

### Post by FuturePilot on 2007-09-29
I had this same problem. Apparently it's an issue with the Nautilus CD burner. Try either Gnomebaker or K3B. Both are in the repos. Gnomebaker worked for me.

---

### Post by staticvoid on 2007-09-29
most KDE apps are very good, not good looking in my opinion, but good, with lots of options for power :P k3b is good. Although... it may be a problem with your cd drive? Also try Brasero....

sv

---

### Post by crimesaucer on 2007-09-29
I've had problems with GnomeBaker, and xfburn....

... I found the solution was a burning program called Brasero: [http://www.gnome.org/projects/brasero/](http://www.gnome.org/projects/brasero/)


My favorite thing about Brasero is that it's simple to use for a beginner, and it doesn't turn my CDs and DVDs into unusable coasters... 


... it is in the repos, and you can use synaptic to get it.

---

### Post by TrevP on 2007-09-29
Thanks everyone for the advice. Nice to see I'm not the only one having some difficulties here. I'll try a different package.

---

### Post by TrevP on 2007-09-29
I've just tried installing brasero. It looks to be a good application. Unfortunately, it doesn't solve the problem. An icon still appears on the desktop telling me I have inserted a blank disc, but brasero tells me the drive is empty! The drive is a Samsung 224-B.

---

### Post by tgalati4 on 2007-09-29
I use K3b and I also have the problem on a Dapper system.  The work-around for me is as follows:

Don't touch the dialog box!  Leave it open when it says "Data or Audio CD?"

Then go into K3b and proceed as usual.  The dialog box will go away by itself when you initiate a new burn.

It looks like when you click that dialog box, it permanently locks out the drive for any other use.  Not sure why.  I don't know if it is a Gnome bug, a Nautilus bug, or a kernel issue.

---

### Post by FuturePilot on 2007-09-29
There's a bug report here that might be related to this
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254")

---

### Post by TrevP on 2007-09-30
Thanks again everyone! The bug report was very enlightening. I've now installed K3B which uses the cdrecord suite and I can now burn disks again.

So - I guess the problem is solved for me, but it does indicate an ongoing problem with the Nautilus CD burning tools. It's interesting that the original version on 7.04 worked but there have been some recent software updates which I downloaded which have probably broken the system. I hope this will be resolved on the forthcoming "Gutsy Gibbon" release.

---

