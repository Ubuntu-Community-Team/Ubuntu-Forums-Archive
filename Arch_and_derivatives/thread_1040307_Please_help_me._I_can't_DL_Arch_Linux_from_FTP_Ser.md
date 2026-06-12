---
title: "Please help me. I can't D/L Arch Linux from FTP Server- Missing P/W?"
date: 2009-01-15
forum: Arch and derivatives
---

### Post by NewsAndHistory on 2009-01-15
Each time I've tried to download the PPC-version of ArchLinux from [ftp://ftp.archlinuxppc.org/iso/releases](ftp://ftp.archlinuxppc.org/iso/releases) I get a message that asks for a username & password. Would any of you please tell me what the username & password I need to submit to access the Arch Linux FTP server? **OR** Would you tell me where to find a *non*-FTP server, which allows me to download the last 2 PPC versions of Arch Linux?

Screenshot:
[IMG]http://i39.tinypic.com/9u3llz.png[/IMG]

---

### Post by Titan8990 on 2009-01-15
I think you would find better support for this on Arch IRC or forums.

Try using anonymous for both fields.

---

### Post by oldos2er on 2009-01-15
You can try user: anonymous and password: your email address, if this is a public ftp server.

---

### Post by NewsAndHistory on 2009-01-15
I know what you mean. I actually asked for help at the Arch Linux forums before coming, here. It's not as easy to find active members over there, as it is here.

If you or anyone else, who visits this forum-thread isn't very busy helping other noobs like me, would you *please* upload the following file to FileDropper.com or any other free file-hosting website for me? I'm still unable to download it from that FTP server:
```
Archlinux-ppc-2007.08.2-Don't-Panic.ftp.iso
```

Screenshot:
[img]http://i40.tinypic.com/sxmy9x.png[/img]

---

### Post by NewsAndHistory on 2009-01-15
**My 3rd attempt to access & download from that same FTP server (failed):**

[img]http://i43.tinypic.com/osg3sl.png[/img]

Please anyone: download this file for me and upload it to a free file-hosting website? If you do, send the download-link to me, whenever you have enough time to help another noob.

---

### Post by oldos2er on 2009-01-15
Open a terminal and run this command: wget [ftp://ftp.archlinuxppc.org/iso/releases/Archlinux-ppc-2007.08.1-Don%27t-Panic.ftp.iso](ftp://ftp.archlinuxppc.org/iso/releases/Archlinux-ppc-2007.08.1-Don%27t-Panic.ftp.iso)

---

### Post by NewsAndHistory on 2009-01-15
I appreciate your patience & help. That terminal command didn't work on my computer (iMac G5 PPC).

So far, I've tried Apple Safari for Mac, and Firefox to download it. In a moment, I'll download Opera for Mac, so then I can try to download that arch linux .iso-file, again. ](*,)

If you or anyone, who has enough time to deal with this can upload that file to FileDropper.com for me, I would very much appreciate it. Today, my browsers have been working fine on non-FTP servers (especially the ones that don't ask for usernames & passwords).

***I'm leaving this note just to give you or anyone else an idea about how fast FileDropper.com can upload an .iso or any other type of file:***
*I just uploaded 4GB to FileDropper, today. It took less than 10min for it to finish uploading.*

---

### Post by Majorix on 2009-01-15
Try downloading Arch 2008.06 and not 2007.08.2. They might be password-protecting the older releases, even though I wouldn't be able to understand why.

---

### Post by oldos2er on 2009-01-15
"That terminal command didn't work on my computer"

 I assumed you were using Ubuntu; doesn't iMac have something similar to wget? Because that command worked for me.

---

### Post by mips on 2009-01-15
Works fine for me so it must be your computer.

Try using Aria2, [http://sourceforge.net/project/showfiles.php?group_id=159897&package_id=179690&release_id=650120](http://sourceforge.net/project/showfiles.php?group_id=159897&package_id=179690&release_id=650120)

It's a command line tool.

---

### Post by NewsAndHistory on 2009-01-15
> **Majorix said:**
> Try downloading Arch 2008.06 and not 2007.08.2. They might be password-protecting the older releases, even though I wouldn't be able to understand why.
 I see what you mean. I read that the installer in the Arch Linux 2008.06 release doesn't work on old iBook G3 computers. I read about it, here:

[Arch Linux Forums / iBook 300 MHz PPC and archlinux]("http://bbs.archlinux.org/viewtopic.php?id=61519")
 
 > I'm running it my iBook G3, 600 MHz and 640 MB ram, and it's running quite nicely. Although, I had **a lot** of trouble getting X to work, but I finally got a working xorg.conf. There's a couple of ppc bugs in gnome right now, but hopefully that will get worked out here shortly (currently I can't do music or videos). I think gnome & xfce were just added to the ppc port so bugs can be expected. I would probably recommend xfce for your machine as well. You can check out the current bug reports:
 
[http://bugs.archlinuxppc.org/index.php?project=1&do=index](http://bugs.archlinuxppc.org/index.php?project=1&do=index)

*Also, the current ftp installer (2008.08.1) doesn't work. So use the 2007.08.2 ftp installer.*

> **oldos2er said:**
> "That terminal command didn't work on my computer"

 I assumed you were using Ubuntu; doesn't iMac have something similar to wget? Because that command worked for me.
I use an iMac. That command didn't work for me. I'll type it in my terminal again.

**Screenshot of my terminal-window:**
[IMG]http://i39.tinypic.com/dq6gc5.png[/IMG]

> **mips said:**
> Works fine for me so it must be your computer.

Try using Aria2, [http://sourceforge.net/project/showfiles.php?group_id=159897&package_id=179690&release_id=650120](http://sourceforge.net/project/showfiles.php?group_id=159897&package_id=179690&release_id=650120)

It's a command line tool.

Thanks for helping me. I finally successfully downloaded that .iso file I needed from the Arch Linux FTP server by turning off my *Speed Download* (download manager) application, which was intercepting the files I tried to download, until tonight.

---

### Post by NewsAndHistory on 2009-01-15
**[COLOR=Red]Problem solved[/COLOR]** [**-this post may be deleted**-]

---

