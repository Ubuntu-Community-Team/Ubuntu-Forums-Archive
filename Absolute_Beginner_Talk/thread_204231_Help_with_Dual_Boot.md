---
title: "Help with Dual Boot"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-06-26
As it is for now, when my computer boots up, it will automaticly choose ubuntu, if I dont respond and choose something else in 10 sekunds. What I would like to do is:
I would like to have Windows Xp as my primary boot, and only have a "choose" time of five sekunds. And if its possible make some kind of hotkey like press f3 or so too start ubuntu instead of selecting it manually. If anyone could help me here it would be very much appriciated.

Thanks.

---

### Post by Jagot on 2006-06-26
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by jincast90 on 2006-06-27
[QUOTE=Jagot][http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)[/QUOTE]

Yes this was interresting reading, but it didint really help me with my problem.

I need to know how to automatic boot windows, and not linux. And if possible I would like to be able to press f3 or so to boot linux, instead of manually selecting it.

---

### Post by Optiker on 2006-06-27
I can't help on the hotkey, but in order to change the default boot OS, edit the grub menu list. This is going to sound complex, but writing it out always looks worse than just doing it.

The way I do it is to find the file **/boot/grub/menu.lst** in Konqueror, right-click on it and choose "edit as root". It will ask for your password, so enter it and the file should open in kate or some other text editor. Any lines in the file starting with one or more "#" characters are comments.

Maybe 2/3 of the way to the bottom, find the line that says...
[COLOR="Indigo"]## ## End Default Options ##[/COLOR]

The sections below that starting with "title" are the boot options. They are numbered from zero, so the first, which may be as follows...

[COLOR="Indigo"]title		Ubuntu, kernel 2.6.15-25-386[/COLOR]

would be zro, and the last, which is probably Windows as in ...

[COLOR="Indigo"]title		Microsoft Windows XP Professional[/COLOR]

would be N where N is the number of boot options, PLUS, the divider after the Linux options and before the Windows option counts as one. So, for my installation, I have three Linux options, the divider and Windows. Therefore, the number of my Windows option is 4 since 0 through 2 are Linux, 3 is the divider, and 4 is Windows.

Now, go back up to near the top of the file. Find the section that starts with the comment...

[COLOR="Indigo"]## default num[/COLOR]

The line following the comment lines in that section will be the line that defines which OS is the boot default. In my case, since Windows is the default...

[COLOR="Indigo"]default		4[/COLOR]

Change that number to whatever number corresponds to your Windows entry in the list.

There are other ways to do this, but I like this manual method. That does it!

Incidentally, the section following the one that defines the default boot OS is the section that defines the timeout before the default boots. I don't recall what the default value is, but that's where you would set the length of time in seconds that you want to delay before automatically booting the default OS.

Now, save the menu.lst file and reboot.

Somebody else will have to help you set up a hotkey to select Linux.

Good luck!
Optiker

---

### Post by Optiker on 2006-06-27
Incidentally, forgot to add this in the previous reply. When I started down the Linux path, I was pretty confused about the step that I just went over to "edit as root" and all that stuff since I didn't have to mess with that in Windows. Also, I was doing most of my forum communication in Windows, and didn't wnat to mess with having to exit Windows, boot Linux, etc. to make a change, then exit Linux and reboot to try it.

I found a file utility called **[COLOR="Indigo"]Ext2IFS_1_10a.exe[/COLOR]** that lets me access my Linux partition from Windows. With it, my Linux partition is mapped as just another drive in Windows, and I can open menu.lst for example, in a Windows text editor - no password or sudo to mess with - save it, then exit Windows and boot into Linux to test the change.

At the time, it was very, very useful. Now I don't use it near as much, but still occasionally. For example, in generating the previous reply to your question, I was working in Windows, so in order to get the syntax correct in the examples from my menu.lst file, I just opened it in TextPad from Windows and did a copy/paste.

Might be worth taking a look. However, the caution is that it makes making changes more trivial, so there's the risk of making errors more likely.

Optiker

---

### Post by drtvasudevan on 2006-06-27
very good detailed reply.
but if you are not able to open by right clicking and selecting edit as root?
that i suppose is for kde.
in gnome one has to open terminal and write sudo gedit /boot/grub/menu.lst
then it opens with root acccess.you can edit and save.
otherwise it is read only.

tv

---

### Post by Optiker on 2006-06-27
[QUOTE=drtvasudevan]very good detailed reply.
but if you are not able to open by right clicking and selecting edit as root?
that i suppose is for kde.
tv[/QUOTE]

Excellent point well taken. True, I am using Kubuntu. Thanks for clarifying it for the original poster, jincast90.

BTW, that's one of the things that's nice about using the EXT3 utility and doing it from Windows...a little less intimidating to a beginner, and less dependent on KDE, GNOME, etc. That's what got me through early on in editing menu.lst, sources.list, xorg.conf, and fstab when I couldn't figure out how to do it from Kubuntu and was getting mixed advice from the forums - like I just did and you corrected!   :)

Optiker

---

