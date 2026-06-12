---
title: "Network Manager broken"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by susan_1890 on 2007-06-05
I just installed Ubuntu and most things are working well.  However, I'm having trouble with my wireless network.

My wired connection is working fine and according to the package manager, Network Manager is installed. However, it doesn't appear on my applications menu and when I try to reinstall it, I get an error saying that some resources can't be found.

My system is a Dell Latitude D600 with a 1.4GHz processor, 512 MB Ram and a Dell TrueMobile 1350 wireless card. I've tried installing some of the driver fixes for Broadcom cards. It appears that the driver on the card is working because it shows up in my network tab under system > administration> network.

If it matters, I'm dual-booting XP Pro and Ubuntu.

Thanks in advance for your suggestions!

---

### Post by southernman on 2007-06-05
Hi Susan and welcome to Ubutnu. 

Network manager should be installed on your system. Look under:

System > Administration > Network.

I am ofcourse assuming your using Ubuntu Fiesty Fawn (spunky little deAr). You can edit your profile to show which OSes your running so you don't have to keep typing that in the future.

HTH's

---

### Post by southernman on 2007-06-05
Sorry! I see now that your looking for something deeper.  Going to google. bbl

---

### Post by southernman on 2007-06-05
> However, it doesn't appear on my applications menuI was playing around in the terminal when I ran gksudo nm-applet. Out of the corner of my eye I see the applet appear in the upper right corner of the desktop... I then had two of them running.

Right clicking on the little applet is the same as doing the System > Administration > Network thing.

I am sure you've found this already [http://www.gnome.org/projects/NetworkManager/admins/]("http://www.gnome.org/projects/NetworkManager/admins/"), but if not have a look at it. It might be able to help you out. It looks pretty sparse on good detailed docs though.

There is a man page for NetworkManager... same thing. Not an awful lot of detail.

Someone better suited will surely stop in soon. 

Good luck...

---

