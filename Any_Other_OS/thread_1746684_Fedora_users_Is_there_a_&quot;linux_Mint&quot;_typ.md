---
title: "Fedora users: Is there a &quot;linux Mint&quot; type distro for Fedora vanilla"
date: 2011-05-02
forum: Any Other OS
---

### Post by shuttleworthwannabe on 2011-05-02
Hi there,
I want to give Fedora a try (F15 has Gnome 3 Shell that I am attracted to out of the box), but have had numerous issues with my hardware (nvidia and broadcom)--with Ubuntu everything just works (hardware detected automatically and prompt to install restricted drivers make this experience love Ubuntu!). With Fedora you have to get into the guts of it and make it work; in the end it does work. I want to know if there is a distro that does this job ofr me and makes my Fedora experience more worthwhile--something like Mint variant for Fedora--all restricted drivers included out of the box.

Or if not, then is there a good website (ubuntuguide equivalent) where to get all the simple-step-by-step instruction on how to do this. BTW the guys at Fedora Forums, are not as forthcoming as people on this forum---just been my experience.

Please assist.

Regards
S

---

### Post by wilee-nilee on 2011-05-02
I think Fedora is its own entity. I like archbang which is a bootable live cd and basically arch with the open box desktop. A simple install without all the usual arch file tweaking, but it does need a bit more, depending on what you want.
[http://archbang.org/](http://archbang.org/)

---

### Post by Untitled_No4 on 2011-05-02
Never tried it myself, but Fuduntu ([http://www.fuduntu.org](http://www.fuduntu.org)) is meant to be Fedora done the Ubuntu way.

---

### Post by el_koraco on 2011-05-02
[http://fusionlinux.org/]("http://fusionlinux.org/")

There ya go, it even uses the Mint menu.

---

### Post by YeOK on 2011-05-02
> **shuttleworthwannabe said:**
> Hi there,
I want to give Fedora a try (F15 has Gnome 3 Shell that I am attracted to out of the box), but have had numerous issues with my hardware (nvidia and broadcom)--with Ubuntu everything just works (hardware detected automatically and prompt to install restricted drivers make this experience love Ubuntu!). With Fedora you have to get into the guts of it and make it work; in the end it does work. I want to know if there is a distro that does this job ofr me and makes my Fedora experience more worthwhile--something like Mint variant for Fedora--all restricted drivers included out of the box.

Or if not, then is there a good website (ubuntuguide equivalent) where to get all the simple-step-by-step instruction on how to do this. BTW the guys at Fedora Forums, are not as forthcoming as people on this forum---just been my experience.

Please assist.

Regards
S

I'm on the Fedora forums, the above fusion linux link is a good choice. If you want guides check the Guides section on the Fedora forums. You can also use autogen aka fedoraplus. Made by a Fedora Forums user. 

Autogen:
[http://www.dnmouse.org/autoten/autoten.html](http://www.dnmouse.org/autoten/autoten.html)
Guides Section @ fedora forums.
[http://forums.fedoraforum.org/forumdisplay.php?f=12](http://forums.fedoraforum.org/forumdisplay.php?f=12)

---

### Post by overdrank on 2011-05-02
Moved to Other OS/Distro Talk :)

---

### Post by kaldor on 2011-05-02
> **el_koraco said:**
> [http://fusionlinux.org/]("http://fusionlinux.org/")

There ya go, it even uses the Mint menu.

This. It's pretty much a "Mintified" Fedora. Too bad it's a very inactive project overall.

Fuduntu might be a better fit.

---

### Post by boydrice on 2011-05-02
There is also Kororaa by Christopher Smart which is a respin of Fedora aimed at new users. 

[https://kororaa.org/](https://kororaa.org/)

If you are after GNOME Shell why not also look at installing openSUSE 11.4 then upgrading GNOME 2.32 to GOME-shell?

en.opensuse.org/openSUSE:GNOME_3.0

---

### Post by Simian Man on 2011-05-02
I think the reason that no Fedora Linux "Mint" spin has caught on the same way Mint has is because Fedora users tend to be more savvy in general.  I too have to install the Broadcom and Nvidia drivers, but don't mind adding RPM Fusion and installing the drivers myself.  Many Ubuntu users are like this too, but there are more beginners as well.

It's kind of a shame, because I wouldn't like giving out Fedora to complete beginners without helping them get setup, but would rather give them the (IMHO) better designed and more solid Fedora base.  I hope Fuduntu gets something like the restricted drivers manager :).

---

### Post by snowpine on 2011-05-02
Why do you need a separate Fedora respin with "all" restricted drivers, why not just install Fedora and then the two restricted drivers you actually need?

[http://rpmfusion.org/](http://rpmfusion.org/)

IMHO, once you know your hardware and understand some Linux basics, you can choose any distro you want based on other factors. If you limit yourself to "distros with all restricted drivers installed out of the box" then you are missing out on Fedora, Debian, Red Hat, and dozens of other wonderful options.

---

### Post by fuduntu on 2011-05-02
> **Simian Man said:**
> I think the reason that no Fedora Linux "Mint" spin has caught on the same way Mint has is because Fedora users tend to be more savvy in general.  I too have to install the Broadcom and Nvidia drivers, but don't mind adding RPM Fusion and installing the drivers myself.  Many Ubuntu users are like this too, but there are more beginners as well.

It's kind of a shame, because I wouldn't like giving out Fedora to complete beginners without helping them get setup, but would rather give them the (IMHO) better designed and more solid Fedora base.  I hope Fuduntu gets something like the restricted drivers manager :).

It is on my radar.  We have Broadcom, and NVidia drivers available in our repo now, and the GMA500 (Poulsbo) packages in testing.  The restricted drivers manager is something that I have been wanting to port over to Fuduntu for some time now, I just don't have the bandwidth for it yet.

That said though, we are building support for these drivers as they are being requested so one just has to let us know it's needed and we'll try to have it available within a few days if possible.

We stick pretty close to the latest mainline stable kernel so we can't just pull from RPMFusion for kernel related packages.

---

### Post by fuduntu on 2011-05-02
> **snowpine said:**
> Why do you need a separate Fedora respin with "all" restricted drivers, why not just install Fedora and then the two restricted drivers you actually need?

[http://rpmfusion.org/](http://rpmfusion.org/)

IMHO, once you know your hardware and understand some Linux basics, you can choose any distro you want based on other factors. If you limit yourself to "distros with all restricted drivers installed out of the box" then you are missing out on Fedora, Debian, Red Hat, and dozens of other wonderful options.

Well, in the case of Fuduntu it isn't just a remix.  As it's growing it's turning into more of a fork.  One could install Fedora, and the 3 dozen packages from RPMFusion if they want, but we do a lot more than just blend Fedora and RPMFusion packages at Fuduntu.  For example, we maintain Chromium, Jupiter, VLC, and a bunch of other packages too.  Some of them align with RPMFusion, some of them are ported from other distributions, and some (many) of them are organic.

---

### Post by Simian Man on 2011-05-02
> **fuduntu said:**
> We have Broadcom, and NVidia drivers available in our repo now, and the GMA500 (Poulsbo) packages in testing.  The restricted drivers manager is something that I have been wanting to port over to Fuduntu for some time now, I just don't have the bandwidth for it yet.

Good to hear, you've done a really great job so far!  BTW the main reason I haven't fully installed Fuduntu on my main machine is because I'm a KDE user.  Do you have plans for a KDE version (eventually)?

---

### Post by fuduntu on 2011-05-02
> **Simian Man said:**
> Good to hear, you've done a really great job so far!  BTW the main reason I haven't fully installed Fuduntu on my main machine is because I'm a KDE user.  Do you have plans for a KDE version (eventually)?

Thanks!  I don't have any plans for a KDE specific version, but we have people on the team using KDE now.  If someone came on and helped build a KDE variant we would help them in every way possible to support it. :)

---

