---
title: "Dual Monitor/Screen Setup with Fiesty and nVidia 7600GT"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by prcm311 on 2007-09-17
Hi,

I have everything I want working, except my second monitor.  I realize there is a lot of information on this subject, but it is very unorganized.  Hopefully starting a new post will get me to this solution faster than trying different approaches blindly.  

I am familiar with editing 'xorg.conf' and using 'nvida-setttings.'  I know about backing up my files in the case I forget a letter/number/capital, so I don't mind some trial and error.  With that said here's what I've got.

I've been using 'nvidia-settings' to generate an 'xorg.conf' file and then editing the 'xorg.conf' based on suggestions.  The file that gets me closest is attached.  The fastest way to get this file is for me to run' nvidia-settings' and select Display Config. and add my second monitor (old gateway, 1024x768 ).  I want to use TwinView so I select that and click add.  When I do that I save the 'xorg.conf' file.  I have to erase all the extra res. settings in the file to get X to in anyway that's near decent.  The only entry I leave specifies the native resolutions of the displays I have and the absolute coordinates of my second monitor.  When I restart X my windows have no title bars and things look a little odd, "glitchy" if you will.  Also it appears that the resolutions are not correct even with only one option.

Any help would be appreciated.  (A commented, edit to my 'xorg.conf' file would rock.)

---

### Post by MrHippocampus on 2007-09-20
The one thing I would change would be the Subsection "Display" bit to this:

```
SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
```

Otherwise you can look at/post your /var/log/Xorg.0.log, that normally gives information about why things aren't working.

---

