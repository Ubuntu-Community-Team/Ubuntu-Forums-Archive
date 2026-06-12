---
title: "[SOLVED] Video Resolution venting"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Webby_s on 2007-07-01
So I am on my 3 install of ubuntu because of a boot problem and the last two times where video resolution problems. Granted they were caused by the end user (Me) But there has to be an easier way. Seriously I am just trying to hook this up to my HDTV via VGA with 1366 (or 1360)x768. Honestly why has it been this hard. I had modified the xorg.conf file 2 ... the first time I don't know if it was that or me but I did have it backed up ... the third time I didn't have a backup of the xorg file and I am too much of a noOb to have restored the file in terminal.

So here I am [COLOR="Red"]enjoying[/COLOR] having to reload this ubuntu for the third time just because I have a generic intel video out that is from the motherboard and can't *EASILY* change it to widescreen.

I tried intstalling xubuntu the other day on a crap PC with the alternate disc and I specificly remember it asking what resolutions I should check mark to be able to have options. GRRRRR

Ok I am done now unless someone can help me with this specific problem.

Widescreen ... that's all I am wanted. I have searched and searched the boards and all are either regarding video cards or modify this, configure that. 

But I do thank you all and I will continue to try this.

---

### Post by mikewhatever on 2007-07-01
Hope you'll get it right this time. To backup xorg, use the following command
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

To restore xorg use this one
> sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by Webby_s on 2007-07-01
Thanks **mikewhatever**. Now to get the widescreen working.

---

### Post by Webby_s on 2007-07-01
Ok so I have been following these directions: [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")
and so far I have screwed it up again. I ctrl+alt+f1 to get to the terminal to do the restore of the backup and I typed in to restore it. And now nothing. Like I said I typed it in and then it asked me my password. I did that then it just hung there. It did nothing. So I reset the computer **hoping** that it did what I asked, but no. So how do I restore a backup? What am I doing wrong?

---

### Post by Webby_s on 2007-07-01
Ok get this ... this will make you laugh .... I just went ahead and reconfigured the xorg file just because I didn't know really what terminal to put the commands into and I knew that I would definitly get soemwhere with the reconfigureing....

So I reconfigured and now I only have 640x480. Ya I am not kidding. Ubuntu has just gotten down-right fed up with me trying to get it to render video in to 1366x768 that is said 'screw you, your only getting 640x480'

I even restored my new xorg with my origianal back up and I still have only the option of the lowest setting.

Help anyone. Really truely you guy/gal's are the best but this is getting old.

---

