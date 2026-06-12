---
title: "Windows Problem: NTLDR Not Found"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2006-07-20
Hi,

Apologies for posting this here, but this forums so active and I want to get back into my computer!
I've been dual-booting XP and Server 2003 for ages now (actually I haven't used XP for ages).
Once I get into Server 2003, I load up my VMWare Player with Ubuntu and forget about Windows until I shutdown.
The big advantage of this is that Server 2003 recognizes all my hardware correctly, and as Ubuntu is only having to recognize virtualized/generic versions of these bits of hardware it runs really well!

Anyway, today someone gave me a copy of Vista Beta 2 to try out and I thought why not so I popped it into this machine (which is my main machine for business and leisure, oops!!) and now I can't get into Windows Server 2003.
Vista has detected even less of my hardware than Ubuntu would if it was installed directly, so I couldn't get the machine online.

Fortunately I had a spare one to use so I downloaded something called [VistaBootPro]("http://www.pro-networks.org/vistabootpro/").
I tried reconfiguring Vista's bootloader (which is a new one) and I couldn't, so I used this tool to have a go.
Having failed, I told it to revert back to the legacy (NTLDR) bootloader, it said OK done and I restarted.

Well now all I get is NTLDR Not Found. Press Ctrl + Alt + Del to restart.

BTW: I have one harddrive with multiple partitions (and therefore just one MBR).

So I popped in the Windows Server 2003 installation disk and went Recovery Console, selected the right installation, tapped in my PWD and ran fixboot followed by fixmbr. It didn't work, so I'm abit stuck now :(.

I've got a few Linux Live-CDs lying around, although I don't have a Linux installation directly on the disk (Ubuntu's on a Virtual Hard Drive within one of the Windows partitions) so I'm not sure if I could load up GRUB solely to handle Windows OS's?

Apologies for the long post, and I understand this is completely off-topic, but I won't get a reply for days if I post this on a Windows forum!

Thanks so much for your help, Vista was crap btw - no added functionality, just a load of gizmo's and fancy looking buttons that did the same stuff as before.

EDIT: BTW, I've tried Startup Recovery on the Vista Disc too, it works (it'll get me back to Vista but it won't get me back to Windows 2003 so I can't do much with it (as I say, Vista's didn't recognize much, so there's no proper drivers for graphics sound (realtec) network (onboard ethernet!) or wifi card, really crap!

---

### Post by falcon15500 on 2006-07-20
Hey there... Try the info from this link - might help.
[http://www.computerhope.com/issues/ch000465.htm]("http://www.computerhope.com/issues/ch000465.htm")

falc

---

### Post by Thenotsowyzewun on 2006-07-21
Thanks :) I found a Windows Support site to post this, but as usual the answer here was better! (spot on, as usual!).

---

