---
title: "Going to give Ubuntu a try.  Need some help, tho."
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Babazoz on 2005-11-26
Hi there!

Today, I got pretty much fed up with Windows as my primary OS after seeing that a lot of the software I use can either be emulated through Wine or is represented by a reasonable facsimile.  I installed PCLinuxOS after breaking off 30GB of my 250GB HD which was previously dedicated to Windows.  Then I started reading a lot about Ubuntu and how easy it was to install software, and have heard mostly good things about it, so I am willing to wipe the entire HD clean and give it a go.  I have all my stuff backed up, of course.

The questions I had were:

What would I use to "fix" my HD, since it's split between PCLOS and WinXP prior to reformatting?  I would assume Ubuntu has tools for this?

Would I have to some how fix the LILO that's currently been installed by PCLOS?


I think I can manage the rest, but those were my two main concerns.

Thanks in advance for any comments!

---

### Post by skirkpatrick on 2005-11-26
I believe one of the partitioning options during the install is to wipe and use the whole drive.  And you won't have to worry about your old LILO.

---

### Post by gord on 2005-11-26
the ubuntu installer has its own partition manager so you can edit your partition table to suit your needs. it should also detect your other opperating system and add it to grub (ubuntu uses grub instead of lilo but im pritty sure you can use lilo if your that determined to)

---

### Post by davmac on 2005-11-26
The ubuntu install disk should do everything you need. At the relevant point you can choose to clear and format the whole drive.

The install disc will also install grub, and effectively overwrite LILO.

Hope this helps,

Dave Mac

---

