---
title: "Any idea when there might be a release of Ubuntu with easy to setup WPA support?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by contriver on 2006-08-30
Anyone have any idea?

---

### Post by H.E. Pennypacker on 2006-08-31
It's already here.  I've had absolutely no problems with WPA on my Dapper laptop.  It was as simple as disabling the connection, adding the key, and enabling the connection.  Whenever something goes wrong, all I do is click on "disable", and "enable" right afterwards.  All this is done via GUI.

Pretty simpple, huh?

If you have any problems, let us know so that there may be improvements.  Reporting errors is a fundamental need in the open source world.  It is almost as important as the existence of developers.

---

### Post by contriver on 2006-08-31
Interesting.  I will have to give it another try.  Can you please explain what application you are using to enter the key into?


Thanks!

---

### Post by matthew on 2006-08-31
I think you will find this howto useful. You may be able to get things going in just a couple of steps, I did.

[http://ubuntuforums.org/showthread.php?t=125150](http://ubuntuforums.org/showthread.php?t=125150)

---

### Post by contriver on 2006-08-31
Matthew, I tried what that link suggested.  I installed network-manager-gnome, however I still do not see a place to input the WAP key in the GUI.  Where do I enter the WAP key?

---

### Post by matthew on 2006-08-31
network-manager-gnome installs a little icon in one of your gnome panels (on my computer it is at the bottom right corner of the screen). Just left click on the icon and choose "Create a new wireless network"

---

### Post by contriver on 2006-08-31
What is a gnome panel?

---

### Post by contriver on 2006-08-31
Also, what exactly does the little icon look like?

Thanks!

---

### Post by matthew on 2006-08-31
> **contriver said:**
> What is a gnome panel?That's the name of the bars that run across the top and the bottom of your screen.

> **contriver said:**
> Also, what exactly does the little icon look like?For me it looks like a series of vertical bars, like those on a mobile phone that report the signal strength.

I did some google-searching for you to give you some resources to look at regarding network-manager-gnome. These should help you.

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
[http://www.gnome.org/projects/NetworkManager/users/](http://www.gnome.org/projects/NetworkManager/users/)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by contriver on 2006-08-31
Thanks for the links man.  No, I didn't get an icon that looks like verticle bars.  This is turning out to be alot of work.  I think I might just throw in the towel for now.  Hopefully a future release will have an easier method of doing this.

In any case, thank you very much for your assistance :)

---

### Post by contriver on 2006-08-31
Well, I gave it one more shot.  I really examined the information in the links you posted.  And...it works!  Whhooohooo.  Thanks!  Maybe I can finally begin using Linux exclusively.  This is great!

---

### Post by matthew on 2006-08-31
> **contriver said:**
> Well, I gave it one more shot.  I really examined the information in the links you posted.  And...it works!  Whhooohooo.  Thanks!  Maybe I can finally begin using Linux exclusively.  This is great!Excellent! I am so glad to hear it worked. Congratulations!

---

### Post by H.E. Pennypacker on 2006-09-01
Contriver, I add the key, if need be, to a text document.  I hardly ever have to open it, but if I need it, it is there.  

I hardly ever switch networks, and when I need to switch back to my original network, I open up the file.  

I am not sure what it is you are using, but if you are using Network Manager, it is all a matter of getting used to it.  It should be real easy.  Take a few minutes to understand everything.
If you have any connection problems, first begin by disabling the wireless connection, and re-enabling it.

---

### Post by contriver on 2006-09-09
I just tried this on another computer now and Network Manager gives me options to setup WEP, but not for WAP.  Any ideas why?

---

### Post by jimrz on 2006-09-09
> **contriver said:**
> I just tried this on another computer now and Network Manager gives me options to setup WEP, but not for WAP.  Any ideas why?

may sound silly, but does your other card support WAP? and is it's firmware up to date?

---

