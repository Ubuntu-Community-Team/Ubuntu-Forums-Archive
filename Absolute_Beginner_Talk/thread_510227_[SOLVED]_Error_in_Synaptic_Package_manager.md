---
title: "[SOLVED] Error in Synaptic Package manager"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by MacDuff on 2007-07-26
I tried to install the Linux version of Mailwasher and it seemed to be OK (said it had all dependencies) but failed at the end.  Now I cannot install anything else.

When I try to install a package using the Synaptic Package Manager it gives the following error message:
"E: the package mailwasher needs to be reinstalled, but I can't find an archive for it.
E: internal error opening cache (1). Please report."

Report to who?   What can I do to eliminate this problem please?

---

### Post by Seisen on 2007-07-26
Try reinstalling mailwasher and see if that fixes the problem.

---

### Post by MacDuff on 2007-07-26
I tried to re-install mailwasher.  Here is the full story:  I enquired from mailwasher if they have a version for Ubuntu and they said that the Kabuntu package will work.

So I tried to install the version for Kabuntu 6.10.   It asked if it was OK to open with G Debi Package Installer.  Since there was no other option and I don't know anything about Ubuntu nor Linux I told it to use the G Debi Pkg installer.

When it tries to install, I get the message "could not open maiwasher_2.0.0_kabuntu_6.10_i386.deb.  the package might be corrupted or you are not allowed to open the file. Check the permissions of the file"

---

### Post by cycleger on 2007-07-26
I have the same problem trying to install VirtualBox. I first tried to install from a downloaded file then directly from the web site. I got the identical message as MacDuff. I've since tried to install anything else and get the same message including update manager

---

### Post by OzzyFrank on 2007-08-11
Personally, I've found those messages to be correct, ie that the deb archive is corrupt. It happens... not everything downloads without fault... and sometimes packages just aren't written properly. In another post of yours I suggest using the Windows one, which I am assuming you do have. Obviously, the problem is with Mailwasher not Synaptic or any other package manager... find it and mark it for complete removal. In the future, do the same for any "problem" package.

In Windows, when a program just won't install properly, we give up (or contact support who invariably tell us to reinstall Windows!)... in Ubuntu, sometimes these faulty programs can halt your package manager as they are still trying to install themselves, so we have to stop them manually.

---

### Post by MacDuff on 2007-08-12
> **OzzyFrank said:**
> Personally, I've found those messages to be correct, ie that the deb archive is corrupt. It happens... not everything downloads without fault... and sometimes packages just aren't written properly. In another post of yours I suggest using the Windows one, which I am assuming you do have. Obviously, the problem is with Mailwasher not Synaptic or any other package manager... find it and mark it for complete removal. In the future, do the same for any "problem" package.

In Windows, when a program just won't install properly, we give up (or contact support who invariably tell us to reinstall Windows!)... in Ubuntu, sometimes these faulty programs can halt your package manager as they are still trying to install themselves, so we have to stop them manually.
Hi OzzyFrank:

The pressure is off for the moment.  I just finished writing a Windows application for a client and can now spare a few hours to get back to the matter of getting Ubuntu to play with my other computers.

You make a couple of points, one of which is that I can manually stop the install process of a problem package.  I have tried to run the Synaptic Package manager to delete MailWasher but cannot get into Synaptic without encountering the error message reported earlier.

What are the commands to stop the installation of MailWasher  and delete the corrupted Mailwasher package?

Second: I infer from your last post that you suggested installing the Windows version of Mailwasher.  That puzzles me.  Is it possible to install applications written for Windows directly into Ubuntu?   I must be mis-interpreting what you have written, not?

Mac

---

### Post by MacDuff on 2007-08-12
OssyFrnank: I found your reply to the other thread that I posted and re-tried your code.  It worked perfectly this time.

Thank you very much for your help.
Mac

---

### Post by OzzyFrank on 2007-08-12
EXCELLENT! (Be sure to be copying and pasting all these woes and solutions, not only for your own reference should you need it, but also to maybe help others in the forums later...  most of the things I have helped people with I've referred to my own document full of fixes and commands, etc).

OK... Windows programs in Ubuntu! I gather you haven't heard of Wine then, which is sort of refreshing considering there are many out there who crack it when it won't run all 117 of their Windows apps, hehe.

Yes, it is a Windows "compatibility layer" (they don't like the term "emulator")... unlike doing something drastic like installing Windows into Vmware in Ubuntu, this is quite transparent. Meaning once you've searched for WIne in Synaptic and installed it, you won't see it (besides the new Wine menu you'll get)... but instead of getting a quizzical look from Ubuntu when you try and run an .exe file, Wine will try to run it. Remember not to go madly double-clicking the icon, as Wine will take a few seconds to run the program. So either the app runs or it won't, and you can find plenty of Wine stories of glee and woe if you want an idea of what runs happily and what doesn't.

People have even gotten Adobe Photoshop - yes, that big monster - to run via Wine (I couldn't get CS2 going but I've seen success stories for earlier versions). Personally, I'm happy I got Mailwasher Pro (with custom filters from Windows) going. Also managed to get DVD Shrink and DVD Decrypter working, as well as MD5 Checker (small freeware), Ulead PhotoImpact, and a couple small apps.

Just remember that some will fail during the install, or the install won't even run, but then amazingly will run if you copy the program folder over from Windows. Others will seem to install perfectly, then fail to run. Some will install and run no problems. Just do what I do and look at each one that works as a blessing... not what others do which is damn Wine to hell for not running all their Windows apps.

In case you're wondering, the all-important folders of \Windows and \Program Files are recreated in a fake Drive C: that resides in /home/yourname/.wine (which is where you'd copy your app folders from Windows to, then create a link to them).

Remember that if an app won't run after being copied but will if you install properly, you can always copy settings files over (like I did with Mailwasher Pro).

So now that Synaptic is working again, you can install Wine and look for yourself. I'm going to start a thread soon on Wine Success Stories, so drop by and tell us what works in a few days or so. Cheers Mac!

---

### Post by MacDuff on 2007-08-12
Hi Again:

Yes I have heard of Wine.  One of my professions is that of photographer and I have invested too much in Adobe Photo-Shop to give it up.  After reading posts and evaluations about Wine I decided that I would install VMWare Server to run PhotoShop CS2.  Since I have VMWare Server installed, there is probably no point in trying Wine is there?

Actually other than CS2 and DesignCad, I can pretty much find Linux alternatives for the other Windows applications and change over to Ubuntu completely on one of my four computers.  Of course I have yet to solve the problem of the network not allowing me to write to Linux files on the Ubuntu Box. 

My desire is to use the Ubuntu machine as a communications file server and temporary backup for the other systems, so it will run 24/7.  I don't want to compromise security but I must be able to write to it from any of the windows boxes and the dual boot machine.  Maybe I will be able to get back to that tomorrow. 

I also intend to replace the motherboard on the Ubuntu box with an AMD Athlon 64 with an integrated nVidia graphics card.  That with a GB of memory should speed up FireFox substantially should it not?

As to saving all the problem fixes, yes to that too.  I have been a software architecht for many years and that is one of those  "must do" things.  You never know when the same or a similar problem will arise to bite you again and computers being so damed literal, you can't miss a single keystroke or the entire system can crash down upon you.

Mac

---

