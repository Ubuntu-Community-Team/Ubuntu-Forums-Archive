---
title: "Equivalent to Sync with WinSCP"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-05-24
Hi,

Are there any easy to use GUI-based FTP tools that also offer Synchronization between local and remote folders (the remote folder also runs LINUX)? In my recently defunct Windows life, I used WinSCP that I liked because it gave me a preview of which files would be overwritten and in which direction, is there a good alternative?

I just tried Unison for a while but I did not succeed, however, it seems that it will force me to select the remote directory before hand (instead of being able to navigate to it once connected), and I could not find the synch option in gFTP.

Thanks,
Daniel

---

### Post by steve.horsley on 2007-05-24
I believe rsync is the standard tool for this. It's command line, and there are probably GUI wrappers (grsync is one) if the command line scares you.  I don't think you can get confirmation prompts for each file though.

---

### Post by jdrodrig on 2007-05-24
Hi,

Thanks for the quick response. Just for the record, I tried WinSCP under wine, but it has crashed on me when I attempt to transfer files. I guess I will keep looking...

If anyone is interested the crash message I got is:
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 9 lpiArray 0x183fa88
fixme:win:UpdateLayeredWindow (0x4015e,0x940,0x183ea1c,0x183ea14,0x6818,0x183ea24,0x00000000,0x183ea10,2): stub!
wineserver crashed, please report this.

---

