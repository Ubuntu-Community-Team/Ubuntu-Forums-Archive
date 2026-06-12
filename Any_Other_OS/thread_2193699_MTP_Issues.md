---
title: "MTP Issues"
date: 2013-12-14
forum: Any Other OS
---

### Post by robn30 on 2013-12-14
So I was running Ubuntu 13.10 for a few weeks and MTP for my Samsung Galaxy S4 was working.  I have now switched to my preferred setup with Mint 16 Cinnamon, which is based off of Saucy, and now MTP will not work.  The whole reason I decided to upgrade from Mint 15 to 16 was when using Ubuntu 13.10, MTP worked.  Why would it not work in Mint 16 but work in Ubuntu 13.10?  I find this to be a bit odd?  Is there libraries with Ubuntu that are not installed with Mint 16.  Any assistance would be great.  Thanks.

---

### Post by ajgreeny on 2013-12-14
Have a look to see if you have mtpfs and/or gmtp installed (the latter is a gnome package so may be superfluous).

I point you to [Connect Android to Ubuntu by USB]("http://www.acertabletforum.com/forum/acer-iconia-tab-a500-general-discussions/129-connecting-via-usb-linux-ubuntu.html") which is all about using MTP which seems not to be so well supported in Linux as it is in Windows.  I needed to follow that to be able to connect my Acer Tab to Xubuntu 12.04, as it connects using MTP which I had never needed before.  It now works superbly, so may be all you need as well.

---

### Post by SeijiSensei on 2013-12-15
I think you need to ask this question on the Mint forums.  I've had success with MTP support for my Galaxy S3 since 13.04.

---

### Post by jetercreek on 2013-12-17
I have no solution, but offer commiserations.  Ubuntu, Zubuntu and Kubuntu all 13.10 see my Kindle Fire HD and work
fine.   Mint 16 based on 13.10 does not work.  The .ini file is there just as in the other distros, but I cannot make it work.
Mint sites offer no help so far.   The problem is known and some users report using Windows apps in Wine.  I haven't
tried that.

I've been a long time Ubuntu user, but have found Mint to offer a simpler interface for me.  My Android "fix" is to dual
boot Mint and Ubuntu.  I go into Ubuntu to send files to the Kindle!  Easy for me as I have not used Windows in many
years.

I do not think attempting to do a fix based on 10.04 as that link suggests would not prove profitable, but would love to hear
about it if someone is brave enough to try!

D

---

### Post by philip550c2 on 2013-12-27
I have Mint16 and I plugged my Galaxy s4 in and it kept bringing up the mtp error message but I just let it accumulate about 10 errors and then for some reason it mounted. Make sure the screen is unlocked, it could prevent usb access. Also do you have usb debugging enabled?

---

### Post by H4Marine on 2013-12-28
Maybe I need to start a new thread? having problems with Hudl (archos badged tablet)  running Android 4.2.2 
The Device is a Tescos Hudl.

My machine...
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

what it sees...
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:d250 Suyin Corp. 
Bus 002 Device 006: ID 0e79:500a Archos, Inc. 

It's there but can't connect

Tried the approaches above with no success :( thanks for any ideas or hgelp ( I am a beginner with Ubuntu so go slowly please)

---

### Post by SeijiSensei on 2013-12-28
12.04 has rather poor support for MTP.  You need to use 13.04 or later, or else transfer files by [wifi]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en") or use Windows.  For bulk transfers, I like [Acrosync]("https://play.google.com/store/apps/details?id=com.acrosync.android.plus&hl=en"), an rsync client.

---

