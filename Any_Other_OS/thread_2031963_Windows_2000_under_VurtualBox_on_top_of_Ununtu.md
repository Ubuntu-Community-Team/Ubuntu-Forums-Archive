---
title: "Windows 2000 under VurtualBox on top of Ununtu"
date: 2012-07-22
forum: Any Other OS
---

### Post by oldefoxx on 2012-07-22
Ubuntu as host, running Oracle VirtualBox as a VM, and having Win2k
installed as a client, is a great combination of software.  I have
the full use of existing Win2k software, plus the addition of all
that Ubuntu provides.  I even have all the Windows updates through
SP4.

What I don't have is the ability to keep updating or upgrading my
Windows software as the developers take them forward.  For instance,
I cannot install Google Chrome, I can't update to the latest
versions of FireFox, and I can't upgrade to some of the add-ons, and
don't like falling behind.  So what to do about it?

Well, the first part of the answer is to recognize that this only
effects the software running under Windows, that I have no such
limitations on the software installed under Ubuntu.

But the second part of the question, I don't have the answer to.
Is there a way to create a shortcut on my Win2k Desktop that
will launch an application like Crome, Opera, or FireFox that is
installed on Ubuntu, and how would I do that?

That's the question.  I can always change the view arrangement
so that I can access the top toolbar on Ubuntu and launch that
way, but I am interested in doing it with a shortcut on the
Windows' Desktop if I can.

Oh, some might think that sticking to Windows 2000 is falling,
behind, but I don't see rebuying all that Windows' software as
moving ahead, particularly since it forces me to consider the
need to replace existing hardware as well.  Your opinion may
differ than mine, but I like what I have here just fine.

---

### Post by k7faq on 2012-07-22
Hi @oldefoxx

I use the Oracle VirtualBox heavily on a Winbloze 7 host.

I am confused as to why Microsofts Update Server(s) would be refusing you updates unless there is a licensing issue. Is your present installation registered with M$? My Winbloze XP Virtuals update just fine so I am not sure where/what the issue would be. M$ Servers should not be blocking you at all unless there is an authenticity issue.

As to not being able to install other software, i.e. FireFox, Chrome, et al. Is your virtual running low on allocated space? I have installed each of these in XP virtuals with no issue.

As to creating a shortcut to a file/folder that exists on your Linux host. YES you can.
In Virtualbox you want to establish a "Shared Folder" pointing to the location on your linux box that contains the file(s) you want to access from the Windows Client. 

Once you have this defined start your windows client and "Map" a "Network drive" in windows to your "Share".  You should find yourself browsing the files on your host.

>  but I am interested in doing it with a shortcut on the
Windows' Desktop if I can.

Are you looking to have an icon on your linux desktop in which you can double click and load the virtual without having to load virtual box then start the machine etc?

I just finished installing Ubuntu 12 on my dev machine and do not have all the other software installed just yet. I should be able to replicate what you are trying within 24 hours from the time of this post. Once I have that I should be able to offer you more unless someone beats me to it.

Steven

---

### Post by Dr. C on 2012-07-28
I run Windows 2000 in one of my virtual machines (VirtualBox)  on top of Ubuntu. It is much leaner than Windows XP and it last version of the NT family without product activation. Many consider it one of the best versions of Windows ever. 

Unfortunatly it went out of support in 2010, so there is no more updates for it from Microsoft; however you will get updates for something more recent installed on Windows 2000 such as Microsoft Office 2003. Mozilla gives their explanation as to why they had to drop support for Windows 2000 here: [http://weblogs.mozillazine.org/asa/archives/2012/01/end_of_firefox_win2k.html]("http://weblogs.mozillazine.org/asa/archives/2012/01/end_of_firefox_win2k.html") and this rationale is likely to apply to many other developers. 

One sugestion here may be to run Windows 2000 in Seamless Mode under VirtualBox (HOST+L) where in the default installation of VirtualBox HOST is Right Ctrl. This provides a very close intergration of the Ubuntu and Windows 2000 desktops.

---

### Post by Rebelli0us on 2012-07-29
I use a Win2k guest all the time, it’s the best OS MS ever made, I get to use Explorer because it’s better than Nautilus for a lot of things.

Some things are no longer supported in Win2k, but the only case I know where Windows Update fails is when Win2k thinks it’s on external disk (such as when you install it on a CF flash drive).

If you’re looking for a shortcut into Linux from Win2k, pressing the Host key will send everything that follows to Linux.

---

