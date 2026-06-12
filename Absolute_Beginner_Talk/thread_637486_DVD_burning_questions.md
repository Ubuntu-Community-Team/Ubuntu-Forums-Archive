---
title: "DVD burning questions"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by chee on 2007-12-11
i have been using devede to convert my avi files to iso so i can burn and watch them.  just wondering if there are any better programs or other ways to do it.  plus when i upgraded to gutsy i guess i took devede off because i no longer have it.  it has been a while since i've used it obviously, and i could just go to the repos and get it again but am open to any alternatives.   i am pretty new though so nothing too complicated (not that i don't want to make the effort--i just don't want to mess up:)  ).  any suggestions would be great. thanks.

---

### Post by gupta_sumesh63 on 2007-12-11
code:

> mkisofs -r -J -o cd_image.iso /dir_of_avi_files

here cd_image.iso is the created iso. /dir_of_avi_files is the absolute path to the dir containing your avi files.(ensure gap between iso and /dir..)

---

### Post by chee on 2007-12-11
i tried out that code and it seemed to work until i burnt the iso file that it made.  my dvd player wouldn't read it and my computer won't play it in VLC.  i might have done something wrong but i don't think so.  any ideas?  like i said i am a newbie

---

### Post by gupta_sumesh63 on 2007-12-11
iso s made by all the programmes or commands are same. Please burn the iso at very slow speed, say at 2x. You can rightclick the iso and use write to disc or use the following command from terminal.
to write a CD, code:

> cdrecord dev=/dev/scd1 speed=0 driveroptions=burnfree -v cd_image.iso

here /dev/scd1 is the path to your CD-ROM device. could be scd1 or scd0 or cdrom. Please check in the dev dir.

To write a DVD use the following code:

> growisofs -speed=2 -dvd-compact -Z /dvd/dvdwriter=dvd_image.iso

Hope this helps.

---

