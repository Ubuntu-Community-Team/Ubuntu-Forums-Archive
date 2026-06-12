---
title: "xfs mounting problems"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by anson on 2006-03-06
I just installed Ubuntu 5.10 and followed [this link]("http://howtoforge.com/perfect_setup_ubuntu_5.10") for system setup except for the partition setup on [page 2]("http://howtoforge.com/perfect_setup_ubuntu_5.10_p2").

I've my partitions setup as follows:
[INDENT][FONT="Courier New"][COLOR="DarkSlateBlue"]/boot[/COLOR] [COLOR="Sienna"]ext3[/COLOR] 100.0MB
[COLOR="DarkSlateBlue"]/swap[/COLOR] [COLOR="Sienna"]swap[/COLOR] 1.0GB
[COLOR="DarkSlateBlue"]/[/COLOR] [COLOR="Sienna"]xfs[/COLOR] 12.0GB
[COLOR="DarkSlateBlue"]/var[/COLOR] [COLOR="Sienna"]xfs[/COLOR] 12.0GB
[COLOR="DarkSlateBlue"]/home[/COLOR] [COLOR="Sienna"]xfs[/COLOR] 15.0GB[/INDENT][/FONT]

Everything worked fine until I edit [COLOR="DarkSlateBlue"]/etc/fstab[/COLOR] as per the [instructions on page 3]("http://howtoforge.com/perfect_setup_ubuntu_5.10_p3") on setting the quota.  I added [FONT="Courier New"][COLOR="SeaGreen"]errors=remount-ro[/COLOR][/FONT] on the [COLOR="DarkSlateBlue"]/[/COLOR] mount and [FONT="Courier New"][COLOR="SeaGreen"]usrquota,grpquota[/COLOR][/FONT] on the /home and /var mounts.  When I did the [COLOR="DarkOliveGreen"][FONT="Courier New"]mount -o remount /[/FONT][/COLOR] command, it gave me [FONT="Courier New"][COLOR="DarkRed"]/ already mounted or bad options[/COLOR][/FONT].

I thought that would be due to problems with mount for xfs so I rebooted the system and then I got [COLOR="DarkSlateBlue"]/[/COLOR] mounted as readonly every since.  I tried copying mount and umount to [COLOR="DarkSlateBlue"]/boot[/COLOR] (so I've them after unmounting [COLOR="DarkSlateBlue"]/[/COLOR]) and umount the [COLOR="DarkSlateBlue"]/[/COLOR], the command went without error or problem but in fact the [COLOR="DarkSlateBlue"]/[/COLOR] mount is still there...  Are there really problems for mount/unmount or Ubuntu 5.10 dealing with xfs??  How can I get rid of the readonly [COLOR="DarkSlateBlue"]/[/COLOR] mount from the boot time??

Any help will be appreciated, thanks in advance.

Anson

---

