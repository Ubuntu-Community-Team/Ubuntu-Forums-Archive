---
title: "[SOLVED] Japanese Input on Gutsy Gibbon"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by TWO on 2007-12-08
Ever since I've updated to Gutsy Gibbon, I've had a hard time trying to suss out how to enable Japanese Input. It worked from the word go in Feisty, but on upgrade I could never get SCIM to display on the panel, nor could I get it to start up in OpenOffice or indeed any other program where typing was necessary.

I tried to un-install and re-install several times but to no avail. I also followed instructions on installing the Im-Ja program and again, that program failed to start up when using particular problems in spite of having set the keyboard shortcuts and the like.

Does anyone else one Gutsy Gibbon and need Japanese support. I have referred to the various tutorials on enabling Japanese support and each have come to nothing.

I don't know if it's just me or whether this is a bug with SCIM on Gutsy.

Any advise would be greatly appreciated.

Thanks

TWO

---

### Post by TWO on 2007-12-11
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

This site solved my problem.

It appeared I didn't have "anthy-bridge" installed. Also, a certain file had to be edited.

---

### Post by DNAspark99 on 2007-12-17
I recently upgraded to gutsy, and couldn't get scim to 'activate' until I came across this post and edited the /etc/X11/xinit/xinput.d/scim file as per instructions, and restarted X...

&#12393;&#12418;&#12354;&#12426;&#12364;&#12392;&#12372;&#12374;&#12356;&#12414;&#12377;&#65281;

---

### Post by Kulgan on 2007-12-31
&#12393;&#12418;&#12354;&#12426;&#12364;&#12392;&#65281;

---

### Post by Pochan on 2008-01-21
This is an area that has been frustrating me (a complete newbie to linux) for a week or two now.  With the help of this post I have got to the stage where SCIM Japanese etc works in gedit BUT I can't get it to activate in Open Office or Yahoo mail etc.  I used the package manager method rather than command line.  Can anyone suggest what else I should do?  Thanks

---

### Post by Pochan on 2008-01-21
Thanks to those who thought about answering but luckily I worked it out and got things going.  I needed to edit the /etc/X11/xinit/xinput.d/scim file as per instructions and hey presto! Phew burned a bit a grey matter getting there I can tell you!

---

### Post by az_s_za on 2008-02-04
Just want to say thank you SO much for this thread.

I administer a shared desktop with my Japanese wife.  She has been having trouble with SCIM for a while now (probably since I enabled the backports repository and updated the SCIM packages).  It had finally become unusable.

The instructions in this post fixed everything for me.  SCIM-Anthy is now working for her, and is more stable than ever before.

I REALLY appreciate being able to have these instructions in English.

Thank you.

---

### Post by Chokkan on 2008-02-18
Same situation as previous poster. Now we are typing in harmony! I used the how-to linked above and had to alter the file specified. Works great now.

---

### Post by ryukent on 2008-02-18
In case any of you have problems entering into non GTK or QT applications, please see this alternative:

[http://ubuntuforums.org/showthread.php?t=684469]("http://ubuntuforums.org/showthread.php?t=684469")

I love SCIM too, but it does have some outstanding issues, so thought I should provide an alternative!

---

