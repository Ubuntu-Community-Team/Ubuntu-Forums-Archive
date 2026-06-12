---
title: "Trying a triple boot"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Refresh_61 on 2007-07-26
Hello,

Like a lot of folks, I switched to Ubuntu 7.04 from Windows. I used Ubuntu for about a month but a friend told me about Mepis. I did the download and now I got the following situation :( . Two drives: hd1 Windows xp and Ubuntu.  Dual boot, no problem but then came Mepis, so now on hd2 Mepis (haven't used it yet). How I configure grub to add Mepis (and of course a triple boot)-(forgive me if it's been posted, I read some but they were not quite my case, I'm newbie :confused: Any help will be appreciated.

---

### Post by fazavon on 2007-07-26
Okay, well at one point I had XP, Server 2003, Fedora 5 and Ubuntu 6.06 all on one machine. (I was bored and wanted to see if it would work.) Now before you go all out and run the risk of killing your current installs I would run Mepis in VMserver first to see if it is even worth trying to move forward. 

//j

---

### Post by thefoolisme on 2007-07-26
The information in this link is really good:  

[http://users.bigpond.net.au/hermanzo..._Linux_Systems](http://users.bigpond.net.au/hermanzo..._Linux_Systems)

Most likely you would just need to add a configfile entry to grub if the OS didn't do it.

---

### Post by wolfen69 on 2007-07-26
or you could just choose which hard drive to boot to in the bios.

---

### Post by confused57 on 2007-07-26
> **thefoolisme said:**
> The information in this link is really good:  

[http://users.bigpond.net.au/hermanzo..._Linux_Systems](http://users.bigpond.net.au/hermanzo..._Linux_Systems)

Most likely you would just need to add a configfile entry to grub if the OS didn't do it.

A configfile entry should work:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by bodhi.zazen on 2007-07-26
Almost all modern distro's, including Mepis, should configure GRUB and your MBR and for you automatically.

---

### Post by Refresh_61 on 2007-07-27
Thanks Everyone!!!!!


Mepis Is Up And Running!!!!!


Special Thanks To Confused57 That Link Really Was Helpful!!!    :)

---

### Post by MQMike on 2007-07-27
Edit:  Oops!  I somehow missed the previous posting!

Should be easy.  My setup is identical.

You didn’t tell us the state of your machine after installing Mepis – does it boot any of the OSs now?
Did Mepis install GRUB to the MBR of the first drive hd2?

Doesn’t really matter.  What you need to do:

--   If after installing Mepis, your dual boot with Windows and Ubuntu on hd1 still works just as before, then all you need to do is include a boot entry for Mepis in GRUB’s configuration file kept at Ubuntu and called /boot/grub/menu.lst.  The suggestion above by Confused57 to use configfile is excellent.

So, with root privileges, edit /boot/grub/menu.lst in Ubuntu to include the following boot entry for Mepis (you can place it at the very end if you wish):

title Mepis or whatever you wish here
configfile (hdx, y)/boot/grub/menu.lst

where (hdx, y) is the hard drive x and the partition y where you put Mepis operating system root files (that’s also where the /boot/grub files typically will be).  If you put Mepis on the second hard drive, the first partition, that’s (hdx, y) = (hd1, 0)
** Note that GRUB starts counting drives and partitions from zero.
Don’t forget after editing to File – Save, File – Quit.

--   If after installing Mepis, your dual boot doesn’t work and/or Mepis won’t boot, or really in any case (because it won’t hurt), you should re-install GRUB * from Ubuntu * to your MBR on the first hard drive.  After doing that, you may also have to edit menu.lst in Ubuntu to include a good boot entry for Mepis exactly as we did above.

When you re-install GRUB to the MBR using the GRUB from Ubuntu (as you had it before installing Mepis), that simply requires typing at a GRUB prompt, grub>, a few commands:
root (hdx, y)
setup (hd0)
quit
$exit
close out all windows
re-boot to test it

(You get a grub> by typing sudo grub at a regular Terminal in Ubuntu or Mepis.) 

Now, here, root (hdx, y) is where you put Ubuntu.  If it’s on the first hard drive, the second partition, that would be root (hd0, 1) (remember, GRUB counts from zero).  The (hd0) refers to the MBR of the first hard drive (where Windows and Ubuntu are located).
After doing this, as I said, you may have to edit in Ubuntu the boot menu, /boot/grub/menu.lst, to include a good entry for Mepis, and again the configfile method is good there.

*** All this assumes you want Ubuntu’s GRUB to control the boot menu, and I think that’s a good idea at this point.  You can always easily change this later so Mepis controls the boot menu (using the exact same methods).

Exactly how to do all this and the details is included in my How-To (which is based on the same methods as Herman’s bigpond – in fact, he’s one of my main references! – and it’s step-by-step walk in the park):

- - - - -   How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Read the first post and maybe the second post on changing the default OS and timeout.  Be patient, go slow, enjoy, and every single detail you need is there.  Or, maybe you can do it from what I said right here.  I dual boot two HDDs, Windows and several Linux OSs, including Mepis, using exactly these methods, nothing more.  Post back if you get stuck and any of us can keep you on track, but, trust me, this is easy stuff.

--Mike

---

