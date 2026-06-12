---
title: "force FSCK?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-24
so how do i force it to FSCK during boot-up more often?i have a paranoia that my hardisk will fail, and i have some sensitive datas on it. i dont want it to FSCK EVERY boot-up, just maby every third or so

---

### Post by autocrosser on 2007-12-24
Look in Synaptic for a app called "Bonager"--it allows you to change the timing of FSCK.  You might also want to do a "deeper" FSCK--in that case:

                                        [SIZE=1]HOWTO - Fix any filesystem errors found on boot automatically:[/SIZE]

[SIZE=1][FONT=Courier New]Edit your /etc/default/rcS---in other words do:
sudo gedit /etc/default/rcS

Find the line: FCSKFIX=false & change it to true

Any errors will be corrected automatically....this will take about 3/4 times as long, but I am paranoid the same way.
[/FONT][/SIZE]

---

### Post by forestpixie on 2007-12-24
also have a look at [this]("http://ubuntuforums.org/showthread.php?t=300477") and of course there is man tune2fs

---

### Post by 99bluefoxx on 2007-12-24
ok, thanks

---

