---
title: "Using Boot Camp: Boot to Ubuntu by default"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by dmber on 2007-10-20
I need to change some file or something, but I don't know which one.  What I want is to be able to power my Macbook on from a shutdown and have it boot up into Ubuntu without having to hold option and choose "Windows."  In other words, I want to have to choose to use OS X.

Possible?

Thanks.

---

### Post by cyberdork33 on 2007-10-20
> **dmber said:**
> I need to change some file or something, but I don't know which one.  What I want is to be able to power my Macbook on from a shutdown and have it boot up into Ubuntu without having to hold option and choose "Windows."  In other words, I want to have to choose to use OS X.

Possible?

Thanks.

Have you installed rEFIt? check the config file.

---

### Post by dmber on 2007-10-21
i have not installed rEFIt...

i will get on that.

---

### Post by dmber on 2007-10-21
ok.  I installed rEFIt.  when i power up from a shutdown the rEFIt menu comes up.  it shows my two OS's: OS X  and "Linux."  I try to start linux and nothing happens.  the screen goes black and the backlight is on but it's not doing anything.  i let it sit for a few minutes and nothing.  hitting the power button shuts the computer down instantly.  i then power back up and tried it again.  same thing.  so i shut down and start up and boot into OS X, no problem.

what am i doing wrong?

thanks.

---

### Post by dmber on 2007-10-21
here is my info from the partition inspector:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     84295719  Mac OS X HFS+
 3       84295720     89178532  Linux Swap
 4       89178533    117209783  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     84295719  af  Mac OS X HFS+
 3       84295720     89178532  82  Linux swap / Solaris
 4       89178533    117209783  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 84295720:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 89178533:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

---

### Post by dmber on 2007-10-21
Ok, I apologize, seriously.  I don't know what I did -- I can't think of anything -- but after I posted last, I figured I'd give it another shot while I waited for a reply and now I'm posting from Ubuntu.  I don't know what happened but it worked.

Now I'm wondering how exactly I change the configuration file to get Ubuntu to boot without any "boot choices" screen.  What I'd like is to be able hit the power button from a shutdown, leave, and have Ubuntu up and running when I get back.  Or, if I want to get into OS X, hit the power button, hold some button (option/alt?) and choose OS X.

What do I do exactly to the configuration file to get this to happen?  Remove the # from the "Legacy" line at the bottom?  Will I be able to call up the rEFIt menu with a button then?

Thanks a lot.

---

### Post by cyberdork33 on 2007-10-21
> **dmber said:**
> Ok, I apologize, seriously.  I don't know what I did -- I can't think of anything -- but after I posted last, I figured I'd give it another shot while I waited for a reply and now I'm posting from Ubuntu.  I don't know what happened but it worked.

Now I'm wondering how exactly I change the configuration file to get Ubuntu to boot without any "boot choices" screen.  What I'd like is to be able hit the power button from a shutdown, leave, and have Ubuntu up and running when I get back.  Or, if I want to get into OS X, hit the power button, hold some button (option/alt?) and choose OS X.

What do I do exactly to the configuration file to get this to happen?  Remove the # from the "Legacy" line at the bottom?  Will I be able to call up the rEFIt menu with a button then?

Thanks a lot.
The Legacy first option will make legacy OS the default. i.e. linux.

I think you can adjust the delay, but you can't make it skip rEFIt completely, that is the point of having it.

Also there is no way to have a hotkey when rebooting. That sounds like a good suggestion though. You should make it to the devs:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by dmber on 2007-10-21
ok.  so i should uncomment (is that the right term?) the Legacy option at the bottom and see if i can find something about a delay in that conf file...

sounds like a plan.  i'll report back.

as always, thanks for the help.

---

### Post by dmber on 2007-10-21
Got it!

I set it up so that it auto-launches the selected OS (Legacyfirst) in 10 seconds.  This is great!

Thanks.

---

### Post by cyberdork33 on 2007-10-22
Great

P.S. Uncomment is the correct term, yes.

---

### Post by dmber on 2007-10-22
i thought i changed the thread title of this to [Solved] but it must be my imagination.  here's trying again...

edit: nevermind, i think i figured it out.

---

