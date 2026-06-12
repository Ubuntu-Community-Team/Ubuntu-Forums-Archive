---
title: "Help - W7 won't boot anymore, error 0xc000000f"
date: 2012-06-01
forum: Any Other OS
---

### Post by taptwo on 2012-06-01
Disclaimer: This problem may have nothing to do with my Ubuntu partition, no idea what happened, semi-n00b here, any help would be appreciated.

Yesterday I had my W7/Ubuntu dual-booted netbook running W7 to transfer some files from one external HDD to another. It may have run out of battery while performing the transfer. At some point the receiving HDD was unplugged by a friend, presumably after the transfer was done, but no guarantee. Either way, the battery was dead this morning.

I plugged it in and turned it on, and selected W7 at the GRUB screen, and got the following error:

Status: 0xc000000f
Info: The boot selection failed because a required device is inaccessible.

Ubuntu runs fine, but I also can't seem to mount the W7 partition when running Ubuntu. I think I could before, but I'm not 100% on this.

The only thing that happened was this external HDD transfer that may have involved a power disruption. Any idea for what might have gone wrong? Here's my setup from GParted.

[IMG]http://dl.dropbox.com/u/15351852/Screenshot.png[/IMG]

Thanks!

---

### Post by darkod on 2012-06-01
Have you tried entering the windows advanced menu with F8? It still works if you press F8 immediately after selecting windows from the grub boot menu.

See if you can boot it in safe mode first. Or something like Last Known Good Configuration...

---

### Post by taptwo on 2012-06-01
Tried smashing F8 and (on a separate attempt) holding shift - no difference. It doesn't seem to get to the point where safe mode is offered as an option, so similarly I don't get the last known good configuration message. (I'm used to encountering that screen because it comes up every time the battery dies while on standby)

:(

---

### Post by oldfred on 2012-06-01
Moved to otherOS.

Anytime a write is not completed you have file corruption. With Windows you then have to run chkdsk and LInux fsck to houseclean bits of a file that may be corrupt.

You can use your Windows repairCD or USB to run chkdsk. And with chkdsk you have to rerun until no errors as it does not fix everything on one pass.

Gparted usually shows a error message if it cannot mount a partition that need chkdsk. Can you mount and see your Windows ok in Ubuntu?

XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by taptwo on 2012-06-01
No, I can't seem to mount it in Ubuntu. I don't get an error though, it just doesn't obey. Yeah I kind of thought the battery dying during transfer might be bad. Had hoped my friend would have noticed, but will provide power next time.

I'll try chkdsk from USB later tonight. Thanks for the advice - will post back if it works!

---

### Post by taptwo on 2012-06-01
Brilliant! Disaster averted. Thanks for helping this dual-bootin' n00b!

---

### Post by TheGuyWithTheFace on 2012-06-01
Would you mind marking this thread as solved? I was already frantically googling your problem, and was very disappointed to learn it had already been solved...

;)

---

### Post by phaygarth on 2013-01-16
Been searching for a solution to this for a while. Many thanks.
 
[RIGHT][[COLOR=#f7f6f5]_web-made.net_[/COLOR]]("http://www.web-made.net")[/RIGHT]

---

