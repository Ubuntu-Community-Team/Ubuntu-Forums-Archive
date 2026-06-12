---
title: "Can I run Reason3.0?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by IngSoc on 2006-09-20
I was wondering if there was any way to run programs such as reason or flash or even adobe for that matter or if i would have to dual boot?

---

### Post by 23meg on 2006-09-20
You can use WINE to run some (very few) Windows apps. I don't think something as complex as Reason will run properly. Your best bet is to dual boot or use Windows inside a virtual machine (which will result in loss of performance).

(Edit: see [this thread]("http://ubuntuforums.org/showthread.php?t=203845").)

---

### Post by Marsolin on 2006-09-20
If you aren't sure how to get a virtual machine setup in VMware Player you can read the how-to I wrote [here]("http://linuxappfinder.com/blog/switching_from_windows_to_linux_using_vmware_player").

---

### Post by mjpatey on 2006-09-20
Flash currently works just fine up to version 7... we're all hoping Adobe expedites the release of 8 and 9 for Linux!  Thankfully, most sites still use 7.

Regarding Reason, you may have some luck using a program called "Wine", which allows you to install and run Windows software in Linux.  To get a better idea of what to expect in Reason's case, do a Google search for Reason and Wine (maybe use Reason's developer's name-- Propellerhead still? to specify in your search).. and it never hurts to include the word Linux in the search, too :-)

When you say "adobe" do you mean Acrobat?  If so, yes, PDF files open just fine in Ubuntu.  There are also third-party solutions (Foxit Reader) that work really well in Linux.  You should search for PDF writing software if you need that... but I'm almost certain it can be had for no charge.

If you mean Photoshop, then some people have been able to run some versions of it under Wine.  Otherwise, you could try the GIMP (Gnu Image Manipulating Program).  It does almost all of what Photoshop does, except for Layer Effects and maybe a few other things I don't need.  It structure is a little different from PS, so it is an adjustment.  When running it I highly recommend using the following command:

Xnest :1 -ac -name GIMP -geometry 1280x976 & metacity --display :1 & gimp --display :1

This will keep GIMP all in one window... otherwise, you get lots of little windows on the taskbar.

Ubuntu is a wonderful OS, and if you don't mind learning new ways to do things, it'll be well worth the extra time you put into it.

---

### Post by orb9220 on 2006-09-20
I keep a dual boot with 12gb partition with xp for programs and if you want to play Games.

---

### Post by djnapster on 2007-10-28
Reason 4 would run on ubuntu with WINE. But the only problem i have is that when i want to start reason it asks for the DVD.

It isn't fixed by mounting the dvd. It has a copy protection. So i need a program like Daemon Tools, or alcohol 120% to fix it.

---

### Post by ampted on 2008-03-27
djnapster  

do u just run deamon in wine? I had a a wersion that workted fine (4.0 in vista) I can poste the link. But that is a UIF file can I mount Maciq iso in wine? and/or simmular makebelive drives in wine? If u have a simple how to it will help me! I running vista home basic on a VM

---

### Post by ampted on 2008-03-27
the torrent I have contains serial maker patch ad a dvd of reason 4 (all in UIF)

---

### Post by ampted on 2008-03-27
I think a WM will help u. u run a windows of ur liking (or any OS) in it and any appz! but it uses mutch of ur computer!

---

