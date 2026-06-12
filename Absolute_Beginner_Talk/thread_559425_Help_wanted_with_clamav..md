---
title: "Help wanted with clamav."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by rock-hopper on 2007-09-25
Hello everyone.

I am getting used to Ubuntu and decided to install clamav to help keep down any Windoze viruses that might come my way from accessing Windoze partitions in Linux.  While I gather that these are unlikely to cause any problems with Ubuntu, I would prefer not to pass them on to others using MS OSes.

I can access the application but when I try to run it, it tells me I have no Virus Definitions; when I try to update these, it tells me that I need to be logged in as 'root'.

I think I understand what this means, but I was under the impression that Ubuntu didn't actually use 'root' and typing 'sudo' seems not to be sufficient.

Is there something I'm missing here and can anyone please point me in the right direction?

It isn't so very important this time as I am about to install a new Hard Disk drive for the exclusive use of Ubuntu, and will be setting everything up anew but it would still be nice to know how to become 'root' if ever it is necessary.

Alternatively, are there any other AV apps suitable for use by a very unskilled beginner?

I do apologise for being such a pest with all these questions but you have all been so helpful before.

With kind regards,

rock-hopper.

---

### Post by por100pre1 on 2007-09-25
> **rock-hopper said:**
> 
Alternatively, are there any other AV apps suitable for use by a very unskilled beginner?

I do apologise for being such a pest with all these questions but you have all been so helpful before.


You are NOT being a pest, no need to apologize! Try using [avast]("http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb"), it is very simple to use. Be sure to [register]("http://www.avast.com/eng/home-registration.php") to get the gratis license. Don't worry, they won't send you spam.

---

### Post by PartisanEntity on 2007-09-25
According to the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_update_virus_definitions"), to update clamav type the following into the terminal:

```
sudo freshclam
```

Also, it is possible to install a GUI frontend for clamav:
```

sudo apt-get install clamtk
```

---

### Post by rock-hopper on 2007-09-25
Hello again.  

     I downloaded and installed avast and it seems to run all right, although when I type in the command avastgui, a message is displayed in the terminal:

(process:7534): Gdk-WARNING **: locale not supported by Xlib 

(process:7534): Gdk-WARNING **: can not set locale modifiers 

     In addition, a small 'pop-up' box tells me:

Avast Information

Deleted stale lock file '/home/bob/.avast/lockfile-bob'.

     Apart from that, it appears to scan properly although I am unable to close the terminal window without losing avast, which seems pretty normal behaviour, even to a MS thrall like me!

     Any light that you could throw on this would be most welcome, and thanks in advance.

rock-hopper.

---

### Post by rock-hopper on 2007-09-28
Hello again everyone.  With regard to my recent post about avast antivirus and my little problem with the terminal, I have discovered that again it was I who was wrong and Linux which was right. :KS

I had tried to run the command: avastgui from the Terminal, rather than the Run box.

When I tried again, this time from the Run box, avast opened, updated its signatures and ran properly and quickly.

I can only plead too many years of doing things the Redmond way - i.e. You do it our way or you don't do it at all; and don't touch anything unless we tell you to.  And by the way, that will be £lots, thank you!

I can, with fingers crossed, say that this one is solved.  Thank you for your help.

Regards,

rock-hopper.

---

### Post by por100pre1 on 2007-09-28
Sorry for the delay. The first warnings are nothing to worry about, just minimal configuration issues, won't hurt the system. The other warning:

Avast Information

Deleted stale lock file '/home/bob/.avast/lockfile-bob'.

appears if you logout without closing avast or otherwise force close avast. Avast deletes the lock file automatically (lock files are placed by running programs to prevent multiple instances of the same program). Nothing to worry about. :)

---

