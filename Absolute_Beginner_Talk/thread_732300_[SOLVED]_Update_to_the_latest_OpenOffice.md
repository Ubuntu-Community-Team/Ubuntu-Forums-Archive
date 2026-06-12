---
title: "[SOLVED] Update to the latest OpenOffice"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-03-22
Hi, I'm using Ubuntu 7.10 and Open office 2.3.0 which came with it. However, there is an issue with this version that is preventing me from working, and the issue appears to be cleared up in  2.3.1

Is there a way to get Open office to update itself, or, rather, is there a way to get Synaptic to update it for me? I'm not really comfortable with the idea of compiling sources etc, so I'm looking for a deb file or better, for a synaptic source.

Can anyone help?

Cheers

Max

---

### Post by hhhhhx on 2008-03-22
sudo apt-get update ??

---

### Post by epsilon_da on 2008-03-23
MaxVK has you solved it?

I run into the same problem long ago. Formulas slowing down everything.
It was fixed on windows the same day it was released, but then i switched to linux.
I was hoping from ubuntu to have a complete repository just because it is the most popular distro, but it hasnt.

Ubuntu respositories sucks.

OpenOffice is very importante on freesoftware, it should be updated quickly.

I am using Ubuntu 7.10 AMD64 and openoffice is yet on 2.3.0. This sucks.

---

### Post by Oldsoldier2003 on 2008-03-23
> **epsilon_da said:**
> MaxVK has you solved it?

I run into the same problem long ago. Formulas slowing down everything.
It was fixed on windows the same day it was released, but then i switched to linux.
I was hoping from ubuntu to have a complete repository just because it is the most popular distro, but it hasnt.

Ubuntu respositories sucks.

OpenOffice is very importante on freesoftware, it should be updated quickly.

I am using Ubuntu 7.10 AMD64 and openoffice is yet on 2.3.0. This sucks.
The Ubuntu repos are LOCKED at release except for security fixes. Unlike Debian Ubuntu is a short release cycle so we don't do rolling releases.


 If you wish to install the latest open office you can always go to [http://download.openoffice.org/](http://download.openoffice.org/)

interestingly enough the version that comes with Hardy is newer than the download at OOo

---

### Post by epsilon_da on 2008-03-23
I am downloading from here.

[http://download.openoffice.org/other.html#es](http://download.openoffice.org/other.html#es)

Sadly the spanish version is 2.3.0.   :'(
I will have to use english or look around for a patch.

Oldsoldier2003:
To have an up-to-date distro i have to erase my computer 2 times per year? That was the main reason i leaved windows. I just want to install a set of program and update it once a while without having to reinstall all over again. Is it possible or should i move to another distro?

Cheers

---

### Post by Oldsoldier2003 on 2008-03-23
> **epsilon_da said:**
> I am downloading from here.

[http://download.openoffice.org/other.html#es](http://download.openoffice.org/other.html#es)

Sadly the spanish version is 2.3.0.   :'(
I will have to use english or look around for a patch.

Oldsoldier2003:
To have an up-to-date distro i have to erase my computer 2 times per year? That was the main reason i leaved windows. I just want to install a set of program and update it once a while without having to reinstall all over again. Is it possible or should i move to another distro?

Cheers

Its the same thing in windows, I don't see what your argument/complaint is. Update your OOo as often as they release- it not that hard. They lock the repos with the stable version of the app at time of release. Last I checked windows update doesn't go out and update all of your installed software to the latest release, nor does it provide a central repository of applications. 

If you absolutely must have the latest version of OOo available at all times then you might want to switch to a distro that has rolling release repos. Debian comes to mind. of course you will also find that the release cycle of Debian is very slow, so you might find yourself in the same boat you are in now.

---

### Post by MaxVK on 2008-03-23
Well, I understand this entirely:

> The Ubuntu repos are LOCKED at release except for security fixes

and for me this is not an issue. Ubuntu is doing a much better job than Windows for me in any case, so none of this bothers me.

However, if I go to the OOo site and download the latest version it comes as a tar archive, and I don't like to install anything outside of the Synaptic manager unless it is a deb file, allowing for removal etc etc, hence this question.

Id *rather* have a source that can be added to synaptic, allowing the manager to handle the whole thing, but if thats not possible Id like to find a deb file for very similar reasons.

Can anyone point me at a deb file for the latest OOo?

Thanks for your replies

Max

[EDIT]
Just to clarify, I don't want the latest version of OOo all of the time, I need this particular update because there has been a change in the way documents are imported, and it appears that the version I have (That came with Ubuntu) does not properly import drop caps with word documents.

---

### Post by forestpixie on 2008-03-23
Get the file from OO -  the .deb one not the .rpm

then half way down this page - look for update which will give you instructions - you will need to change the file name to suit.

[http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html](http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html)

---

### Post by quinnten83 on 2008-03-23
you can also try your luck at getdeb.net.

---

### Post by MaxVK on 2008-03-23
Unfortunately getdeb doesn't have OOo on there, only an XML plugin.

forestpixie: Iv been to OOo and seen the deb, but somewhere I read that the deb file there is for Debian, and is different from the one needed for Ubuntu.

---

### Post by Irihapeti on 2008-03-23
The OpenOffice deb file is fine for Ubuntu. I use it on my machine. First of all, though, remove the OpenOffice files that came with the Ubuntu disk.

---

### Post by MaxVK on 2008-03-23
Oh well, that didn't work!

I removed OOo that came with Ubuntu (It was version 2.3.0) and then tried to install the deb files that came from OOo in the form of an archive. (This file came from [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and its the English (US) version, the Linux deb)

Unfortunately I hit catch 22. Nothing would install because the dependency of core1 wasn't installed and yet core1 wouldn't install because core2 wasn't installed.

Great. Now I have no OOo, since there is no point in re-installing the Ubuntu version, because it doesn't do what I need.

Any ideas anyone?

Cheers

Max

---

### Post by MaxVK on 2008-03-23
A little update.

Using information from here: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) I have managed to install OOo from the downloaded file.

Everything seems to be working for now, although the promised functionality that was the reason for this little episode appears not to have materialized after all. Oh well....

Thanks to all who helped out.

Regards

Max

---

