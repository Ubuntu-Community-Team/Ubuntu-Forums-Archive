---
title: "Installing .DEB files, etc..."
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by anxietyzone on 2005-07-04
Good morning!

I'm kind of new here (just posted my first post last night) and I have a few questions before I switch over from FC4 to Ubuntu. Any help would be greatly appreciated and thank's in advance:).

1) What version of Gnome does Ubuntu v5.04 come with?

2) I have many reasons for wanting to switch to Ubuntu but one of them is the fact that Debian (and Debian-based distros) have thousands of extra pre-compiled programs available for them. I was thinking about downloading the entire 14-CD software set from debian.org. Since they are all in a .DEB format, I'm assuming I should be able to use them with no problem(?).

3) Is there a way to add the entire Debian software library (over at debian.org) to my Synaptic repository list and where are the instructions for doing this?

4) How many programs are now available on the 14-CD set over at debian.org?. When I used Debian about 4-5 years ago, I think it was something like 14,000 programs on 8 CD's. What's it up to now?.

5) As a test, when I was using the LIVE CD, I went to debian.org and clicked on a .DEB file (it was a game) and when the dialogue box appeared and I clicked "ok", it brought the .DEB file up in the archive manager. In Fedora, all of the files were automatically opened using the software installer (not Synaptic, etc). How do I do this in Ubuntu so that when I click on a .DEB file, it is automatically installed?.

Thank's again. Looking forwarding to installing Ubuntu after trying out the LIVE CD.

---

### Post by varunus on 2005-07-04
1.  Ubuntu comes with GNOME 2.10.

2.  Most .DEB files from debian.org will work with ubuntu, but its not recommended to mix debian and ubuntu packages in case of some conflicts...I've had no problems mixing packages, however, but YMMV.  Ubuntu has most of the packages debian does, so you should be ok.  Just enable the "universe and multiverse" repositories ([http://www.ubuntuguide.org](http://www.ubuntuguide.org)  has all the info you'll need).

3.  You can add the debian repositories to Synaptic by going to Settings->Repositories, and choosing add.  Click custom, and then add the "deb" or "deb src" line you want.  However, you should be able to get everything you need in Ubuntu...and packages may not stick to their ubuntu versions, which could cause problems.

I'm not sure about 4 or 5, but I'm sure someone else here will know.  5, I'm willing to bet its just a gnome thing, where you right click and choose "Open With..."

Good luck, and be careful with mixing packages if that's what you do.

---

### Post by anxietyzone on 2005-07-04
Thank's for the quick and detailed response. Is there a place I can go to download all of the packages that don't already come with Ubuntu so I can burn them to CD's?. I found the Ubuntu software directory but I want to be able to download the ISO's (ie; Debian has 14 ISO's with software).

- Thank's again for your help:)

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=anxietyzone]
2) I have many reasons for wanting to switch to Ubuntu but one of them is the fact that Debian (and Debian-based distros) have thousands of extra pre-compiled programs available for them. I was thinking about downloading the entire 14-CD software set from debian.org. Since they are all in a .DEB format, I'm assuming I should be able to use them with no problem(?).
[/QUOTE]

Well...actually...Ubuntu and debian are two different things. And we at Ubuntu don't have the 14 cd thing. I honestly tell people here all the time that if you don't have broadband (aka can't easily download the packages you need one at a time) then its better to use real debian. We are not 100% compatible with real debian.

Even if they are debs...they are not the same. Ubuntu is a fork of debian unstable...teh debs on the cds are debian stable...there might be big problems using one on the other.

Ubuntu has 16000+ packages. Debian stable has 14000+. But if you need the CDs...you gotta use debian. Try prodigy debian- its a great way to install Sarge.

---

