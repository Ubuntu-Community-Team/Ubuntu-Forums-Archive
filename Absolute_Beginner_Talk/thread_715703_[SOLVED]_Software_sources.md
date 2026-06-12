---
title: "[SOLVED] Software sources"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-05
I need some Third party to be added in Softwares sources. Can any one tell me some sources to be added in that?

---

### Post by Joeb454 on 2008-03-05
Hey, what exactly do you mean you need some Third Party sources added?

What are you trying to install?

---

### Post by jan quark on 2008-03-05
see also:
[LIST]
[*][https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[*][http://ubuntuforums.org/showthread.php?t=485841](http://ubuntuforums.org/showthread.php?t=485841)
[/LIST]

---

### Post by kellemes on 2008-03-05
Some reading about repositories, including adding 3rd-party..
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Like joeb454 I wonder.. is there anything in particular you want to install?

---

### Post by adi_das on 2008-03-05
I have pidgin 2.2.1 installed. I saw that version 2.4.0 is released on march 1.I didnt receive the update so far. is there any software sources to be added?

---

### Post by kellemes on 2008-03-05
> **adi_das said:**
> I have pidgin 2.2.1 installed. I saw that version 2.4.0 is released on march 1.I didnt receive the update so far. is there any software sources to be added?


You can wait (preferred) or use the source to compile/install.
Instructions are inside the tarball.
[http://www.pidgin.im/download/source/]("http://www.pidgin.im/download/source/")

---

### Post by adi_das on 2008-03-05
I have waited for so many days and now i found that GIMP new version is also released a few days ago and yet not received the update.Update manager Shows Other updates.

---

### Post by kellemes on 2008-03-05
> **adi_das said:**
> I have waited for so many days and now i found that GIMP new version is also released a few days ago and yet not received the update.Update manager Shows Other updates.

You have to understand Ubuntu isn't all about being bleeding-edge, the focus also is on stability, the fact there is a new release of some package doesn't mean it's stable enough to be included in Ubuntu.
Also new releases needs to be packaged, this needs to be done considering a hole lot of issues, and at least it takes time..
If you want to go bleeding-edge you can consider ArchLinux or Gentoo but I warn you.. living on the edge makes you bleed ones in a while.. ;-)
You can always compile the source yourself if you're inpatient.

---

### Post by adi_das on 2008-03-05
There is also pidgin version 2.3.1 is released but that also not received.

---

### Post by Joeb454 on 2008-03-05
It takes time for them to be added into the Ubuntu Repositories.

Software isn't added as soon as it is released. Like the above said, you can either download the source and compile yourself, or you could check [getdeb.net]("http://getdeb.net") and see if they have the newest version available to download

---

### Post by AndyCooll on 2008-03-05
> **adi_das said:**
> There is also pidgin version 2.3.1 is released but that also not received.

You will NEVER receive the updates, at least not for Gutsy, Ubuntu doesn't work like that. When a version of Ubuntu is released (e.g. Gutsy) all packages are effectively frozen at the version number they're at. This is for stability reasons. Only occcasionally are updates released, and these are generally for security purposes. Sometimes the most significant apps get updates through the backports project, but again this is the exception rather than the rule.

Newer versions of apps appear in new releases. So the updates to Pidgin and GIMP will appear in Hardy.

If you really must have the latest version of these apps you'll need to install them yourself. The easiest way to get them is to download a pre-compiled binary from [http://www.getdeb.net/]("http://www.getdeb.net/"). In the case of Pidgin you'll probably have to un-install the old version first, but then it's simply a matter of double-clicking the downloaded package.

:cool:

---

### Post by Joeb454 on 2008-03-05
As I suggested (also the person above) try searching **getdeb.net** :) You could also enable the backports in your software sources, I have them enabled (but there's still not much difference in the amount of updates)

---

