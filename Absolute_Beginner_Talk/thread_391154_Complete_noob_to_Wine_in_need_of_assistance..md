---
title: "Complete noob to Wine in need of assistance."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-22
Ok, the extent of my knowledge of Wine is that it can run Windows programs on Linux.

I would like to run AIM 5.9 on Linux using Wine because I´m not too fond of the other instant messager alternatives.

Can anyone explain to me how to install and run Wine?

Also, just as a general question about Wine, do I have to run Wine first and then run my Windows application, or can I just run the application and Wine will automatically take care of the emulation for me?

---

### Post by cowlip on 2007-03-22
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) I hope this helps on how to install WINE.

Good WINE GUI for installing programs or Internet Explorer easily:  [Winetools]("http://www.von-thadden.de/Joachim/WineTools/") or [Crossover Office]("http://www.codeweavers.com/") (they employ many WINE developers)

How to check if a program will run under WINE is to search the [WINE application database]("http://appdb.winehq.org/"): [http://appdb.winehq.org/appview.php?iAppId=109](http://appdb.winehq.org/appview.php?iAppId=109) It looks like AIM will.

The way WINE works is that you just have to put "wine" in front of whatever Windows exectuable (like .exe or .msi) that you want to run.  eg., "wine ~/.wine/fakeroot/C/program\ files/internet\ explorer/iexplore.exe" would run iexplore.exe.  You can associate .exe files to open up with WINE as you would any other file association, but take into account the security of that since you could be letting Windows viruses run.

---

### Post by tchoklat on 2007-03-22
wine is located in the synaptic package manager if you would like a easier way to install it.  You might have to enable the multiverse and universe repositories though

you then install your package 
"wine package.exe" into a terminal
to install it


tony

---

### Post by Brucey on 2007-03-22
Ok I´ve installed Wine and installed AIM successfully, but when I use winefile to navigate to the /Program Files/AIM folder and double click on aim.exe, nothing seems to happen.

Oh and also, whenever I run Wine I get this error:

winefinelibGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:ole:get_inproc_class_object couldn't load in-process dll L"C:\\ProgramFiles\\AIM\\sb.dll"

Can anybody decipher what this means?

And thanks for all the help, I really appreciate it.

---

### Post by cowlip on 2007-03-22
I would try to find this specific version of AIM: 5.5.3595.  From the Wine Application DB it appears newer versions have problem: > 5.5.3595  	Runs, installs, and works perfectly using Wine 0.9.20 and Internet Explorer 6.0 (installed with ies4linux 2.0.3).  	/  	/  	0


Old versions of AIM: [http://www.oldversion.com/program.php?n=aim](http://www.oldversion.com/program.php?n=aim)

If it still doesn't work, you could try to find  the specific version of WINE that they used, I'm sure there are lots of old .debs of that version on the WINE site.

If it doesn't work after that, you can virtualize Windows under qemu or qemu-launcher or virtualbox or vmware and use a seamless desktop so it looks like it's on your Ubuntu Desktop: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)  [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by DougieFresh4U on 2007-03-22
> **Brucey said:**
> Ok, the extent of my knowledge of Wine is that it can run Windows programs on Linux.

I would like to run AIM 5.9 on Linux using Wine because I´m not too fond of the other instant messager alternatives.

Can anyone explain to me how to install and run Wine?

Also, just as a general question about Wine, do I have to run Wine first and then run my Windows application, or can I just run the application and Wine will automatically take care of the emulation for me?

I  installed AIM through Internet Explorer 6 and it's in my Menu under  "Other"

---

### Post by YokoZar on 2007-03-23
> **cowlip said:**
> Good WINE GUI for installing programs or Internet Explorer easily:  [Winetools]("http://www.von-thadden.de/Joachim/WineTools/") or [Crossover Office]("http://www.codeweavers.com/") (they employ many WINE developers)Avoid Winetools.

---

### Post by Brucey on 2007-03-23
> **DougieFresh4U said:**
> I  installed AIM through Internet Explorer 6 and it's in my Menu under  "Other"

How do you install through Internet Explorer?

And if I did that would I have to open up IE every time I wanted to use AIM?

---

### Post by cowlip on 2007-03-23
> **YokoZar said:**
> Avoid Winetools.

Why's that?

---

### Post by DougieFresh4U on 2007-03-23
> **Brucey said:**
> How do you install through Internet Explorer?

And if I did that would I have to open up IE every time I wanted to use AIM?

When I open AIM, IE opens but after I log onto AIM I close IE and AIM remains active still. I do not understand but as long as it "works" I'm not gonna complain:) :)

---

### Post by AndyCooll on 2007-03-23
> **cowlip said:**
> Why's that?

AFAIK Winetools is no longer being updated (and hasn't been for awhile).

:cool:

---

