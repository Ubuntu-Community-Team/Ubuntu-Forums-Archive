---
title: "IPOD &amp; Laser Printer"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by koz-man on 2007-05-09
Again I'm a new Ubuntu user.  I have reviewed the online help but still am having issues getting 2 items to work.

**IPOD** - I have tried using Rhythmbox and Amarok but no success getting Ipod to sync over to the computer.  Both programs recognized the Ipod as being there but Amarok had some type of error and Rhythmbox did nothing at all.  I can't replicate the error with Amarok right now, whatever it was it froze my Ipod.  So maybe after my Ipod battery dies I can try again because I did not catch the text of the error.
[B]
Laser Printer[/B] - I have downloaded the linux printer driver to my desktop, it is an .rpm file  I understand that Ubuntu does not support the use of these types of files so it must be converted with some other program.

The laser printer is a KonicaMinolta Magicolor 2530DL.  I visited the drivers site at Konica Minolta and did not see any for Ubuntu specifically but saw only a linux download.

Help with the above issues would be greatly appreciated.

---

### Post by klayn on 2007-05-09
Do you have any more information about either problem? The error that amarok gives you would be a big help. Try to be as descriptive as possible so people can assist you better.

As for the laser printer: the make/model would be good to have, then people might be able to point you in the right direction. 

Side note: .rpm files are package files for linux distributions such as red hat, fedora, and others. Ubuntu is a debian-based distro and uses package files with the .deb extension. Try searching for ubuntu-specific drivers instead of simply "linux drivers." Files with a .deb extension will work (and if they don't, they'll at least tell you why not), and in most cases, archives with the extension .tar.gz will work too.

---

### Post by eldepeche on 2007-05-09
Was your iPod formatted on a Mac? If its filesystem is HFS+, Linux can't write to it.

---

### Post by koz-man on 2007-05-09
My Ipod was used in Windows XP using Itunes 7 something.

---

### Post by drowner on 2007-05-09
The iPod error: was it about not being able to do aac files?

Are you using the Gnome desktop?

I know amaroK should run on it well, but I had a few issues.

I now use songbird or gtkpod to sync my ipod.

---

### Post by koz-man on 2007-05-10
THANKS for the replies - it's cool to see people willing to assist.

**IPOD** - I was able to replicate the initial error.  I first plugged in the ipod via my USB connection and after it was recognized by Ubuntu I opened Amarok.  This is one of the error messages I received:

*Media Device: iPod mounted at /media/JASON KOSCI already locked. If you are sure that this is an error, then remove the file /media/JASON KOSCI/iPod_Control/iTunes/iTunesLock and try again.*

I don't know about the Ipod being locked. I have tried this about 4 times and received this error each time.

---

### Post by drowner on 2007-05-10
Have you tried doing what it says?

---

### Post by koz-man on 2007-05-10
Good question.  Being new to Ubuntu I am not sure as to how to do that.  It gave me option to remove it but had error trying to do that.  So I did manualy locate the file and remove it.  so  I then closed Amarok and recieved the 2nd error about KDE crash

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232501040 (LWP 7418)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb66bca3b in KAudioManagerPlay::KAudioManagerPlay ()
   from /usr/lib/libartskde.so.1
#7  0xb6779d03 in KNotify::restartedArtsd () from /usr/lib/kde3/knotify.so
#8  0xb677a01d in KNotify::KNotify () from /usr/lib/kde3/knotify.so
#9  0xb677a85a in kdemain () from /usr/lib/kde3/knotify.so
#10 0x0804e6bf in ?? ()
#11 0x00000001 in ?? ()
#12 0x0807df38 in ?? ()
#13 0x00000001 in ?? ()
#14 0x00000000 in ?? ()



Another error: During the previous startup, KNotify crashed while instantiating KNotify. Do you want to try again or disable aRts sound output?
If you choose to disable aRts output now, you can re-enable it later or select an alternate sound player in the System Notifications control panel.

---

### Post by koz-man on 2007-05-16
Was able to get the printer driver converted and installed.  The computer recognizes the printer is plugged in.  When I go to print an error on the printer window appears and nothing printing.  

Ipod - got the gtkPod sync program, it sees the Ipod but i am having a problem getting the settings correct. so far cannot sync or transfer audio files from ipod to computer.

i must say i love the things that work in Ubuntu but getting things to work seems much more complicated.  I am spending lots of time reading the forums and also launch pad and other websites trying to find fixes for these issues.  if you read this post and you your self have successfully installed your ipod or konica minolta 2530dl color laser printer on ubuntu 7.04 Fiesty Fawn, with Gnome 2.18.1 and you have the patience for a new linux user - let me know.

thanks

---

