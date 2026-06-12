---
title: "HP PSC 1317 All-in-One CUPS prob"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-06-13
I have a HP PSC 1317 All-in-One USB scanner / printer.

It is attached to a Windows XP machine, which shares it on the network.

XP and Vista machines can print to it okay.

I tried to set it up in Ubuntu via 'System' > 'Administration' > 'Printing'

Selections as follows:

Step 1: Printer connection
- selected network printer, windows printer SMB
- asked for username / password
- there's no username & password required on this network afaik, so I left both blank.
- it gave me a choice of machines
- chose the XP host that has the printer attached;
- it asked for username & password;
- again none required afaik so left blank;
- it showed me the share name for the printer, so I selected it;
- clicked 'forward';
- selected HP PSC 1310 as the nearest sounding driver;
- had a look at 'install driver', but it asked for a 'ppd' file that HP don't seem to offer
- so I stuck with the PSC 1310
- hit apply, it waited a few secs, then disappeared.
- 'printers' is now showing a PSC 1310, big green tick as default

Tried to print both a test document, and a document out of open office.. 

On the XP machine, in the printer's document list, I get a 'Remote downlevel document' which claims to be in the process of printing. However it never completes, nothing comes out of the printer, and the XP machine goes unstable. The 'Remote downlevel document' cannot be cleared even by rebooting, the only way seems to be to cancel it numerous times, send some test documents from XP, and reboot numerous times whereupon it eventually dies.

The PSC 1310 is very similar to the 1317, in the past I've used the 1310 Windows driver for it with no problems (either that or the same download covers both, memory's a bit dicky on that but I'm pretty sure the 2 models are very close - whether this would apply to a linux driver I don't know)

Any ideas?

---

### Post by phr0ze on 2007-06-13
I have had a hard time with the test page. Use open office and print from there. Make sure you set CUPS to the right paper size too.

---

### Post by ecs_pf5 on 2007-06-13
I set paper size to A4 (it's A4 that's in the printer & it's the right size for it as far as I know..), and tried from OO.. everything in Ubuntu seems fine, the jobs show up in the jobs list, and disappear after a few secs.. (as if the jobs have been sent off okay and Ubuntu thinks everything's hunky dory)

Something arrives at the xp machine for every job sent, but it's always marked as 'Remote downlevel document' & that's when trouble starts, it just locks up.. not totally, just goes real slow & jerky. & nothing from the printer.

In XP the document properties for these 'Remote downlevel documents' show data like the following:

Size: 2399257 bytes
Pages: 0 (weird)
Datatype: RAW
Processor: WinPrint
Owner: Guest

I tried setting the XP machine with an explicit username and password, and re-setting up the printer in Ubuntu accordingly - no improvement.

Perhaps I need a better driver

---

### Post by dstew on 2007-06-13
That printer uses the proprietary hpjis language, not Postscript. If you chose a Postscript driver, you can change it to an hpjis driver. From Synaptic, install HPLIP and HPIJS if these have not yet been installed. In the Printers window, right-click the printer, choose hpijs in the Driver list, then pick your printer. However, it you already have the hpijs driver, then I am not sure what to do.

---

### Post by ecs_pf5 on 2007-06-13
It does say hpjis in the driver screen & it appears to have a green dot beside it - it came up like that when I selected the PSC 1310 in setup.

Those 2 you mention are green already in synaptic - however there are a few hp-related items which aren't installed including 'hpoj' which is the hp driver for office jet. Interestingly this is listed in the notes as covering the 'all-in-ones' including 'psc' types... hmm

Will post back if I get any joy..

---

### Post by southernman on 2007-06-13
I may not be entirely correct here, but lets give it a shot -

SMB = Samba (used for sharing files and printing between Windows and Linux machines)

Samba = "requires" a username and password to work, for authentication purposes. Even though your printer and / or Windows boxes aren't setup to require authentication, Samba isn't going to work without doing so. Someone with a better understanding of Samba will have to direct you how to set it up... or you could google/search the forums while your waiting. :(

If you were to take your printer and plug it directly into your Ubuntu machine, you'd find it to work effortlessly. The problem is stemmed from printing across a multiplatform network eg... Samba. Nothing wrong with Samba, it just has to be configured/setup with user/passwd properly.

HTH's in some way...

PS. HP definately has the advantage for widespread Linux compatability. Never buy a Lexmark for use with Linux... period!

---

### Post by ecs_pf5 on 2007-06-13
A networking problem would fit the evidence, as the Windows XP machine never seems to know who it is that it's talking to.. owner of the document is always just "Guest". I did try setting the XP machine up explicitly with a password on the main user account, but I haven't yet looked at passwording the network, or the printer itself. 

It's a part-wired, part-wireless network over a Belkin 4-port wireless ADSL router. The XP printer host is a wireless laptop, Ubuntu's on the wired side of the network.

---

### Post by southernman on 2007-06-13
When I get through with some domestic duties, I'll dig up some research on setting up smb for you. If you figure it out before I get back, just leave a note as to what you did to get it working so others too may benefit. ;)

bbl

---

### Post by ecs_pf5 on 2007-06-13
Thanks. & will do.

I found this which might be worth a try, 

[http://lists.samba.org/archive/samba/2005-October/112851.html](http://lists.samba.org/archive/samba/2005-October/112851.html)
in short, they suggest disabling bidirectional support on the shared printer. It's one to try, anyway..

Dug up this interesting guide on samba for reference, not done anything yet other than try & familiarise with the lingo
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ecs_pf5 on 2007-06-15
This is all working fine now.

What I did, was to edit smb.conf so that the 'workgroup=' line near the top, read correctly for the Windows workgroup of which the printer host XP machine was a part of.

i.e.

```

workgroup=WORKGROUP

```

not MSHOME or DEBIAN as was the current setting.

There were 2 smb.conf files on my machine - I edited both, no doubt I only really needed to edit one of them though.

Thanks for you guys' attention to my problem :) appreciate your taking a look

---

