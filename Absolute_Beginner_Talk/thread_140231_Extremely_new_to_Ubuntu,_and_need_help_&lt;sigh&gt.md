---
title: "Extremely new to Ubuntu, and need help &lt;sigh&gt;"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by the_izman on 2006-03-05
Hey all,
I desparately need some help with Ubuntu and more specifically with Wine.
I managed to get it installed with the Synaptic Package Manager - at least it says that it is installed, but where the heck did it install into?  I can't find it in any of the menus.  No, I haven't tried installing Automatix, mostly because I can't find the download thread anymore.  :-)
I've looked in a lot of posts and stuff like that but I think there is something that I am not quite understanding.
There are a few things that I need to port over from Windows mostly for the kids, as well as some other applications.
Trust me - I'd rather NOT have any Windows stuff on here, but there are others who use this computer and I think it would be thoughtful to have a little familiarity for them.
Anyways, I am more than willing to learn this distro.  It was super easy to install and so far I am not having any major issues with using the open source apps, but like I said....kinda need to have Windows stuff on here.

---

### Post by aysiu on 2006-03-05
This little excerpt from [the Ubuntu User Guide](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf) should help you: > A bit about Wine... I don't know how it works, but it does seem to work with a lot of simple Windows programs. I'll show you how I get Filezilla to work in Linux, as an example.

Assuming I've already [enabled extra repositories](http://www.psychocats.net/linux/sources.php), first, I install Wine:
sudo apt-get update
sudo apt-get install wine

Then, I download the setup.exe file for Filezilla. When I double-click on it, Wine will try to open the file. Then, the installer appears, just as if I were using Windows. Instead of installing Filezilla to C:\Program Files\Filezilla\, I'm going to override the default installation location and install it to z:\home\username\.wine\drive_c\Program Files\Filezilla. For some reason, z:\ is what Wine calls my Ubuntu partition.

Then, I set up a launcher (on the panel or in the menu) for the command wine &#8220;z:\home\username\.wine\drive_c\Program Files\Filezilla\Filezilla.exe&#8221;

That's it. Now when I click on that launcher, Filezilla will load up.

---

### Post by Iandefor on 2006-03-05
Hullo. The download thread for Automatix is here:
[http://ubuntuforums.org/showthread.php?t=138405]("http://ubuntuforums.org/showthread.php?t=138405")

And Aysiu's response is more detailed than I can give, regarding WINE.

---

### Post by the_izman on 2006-03-05
well...I did exactly what aysiu suggested....pretty much step-by-step
THAT wasn't a problem at all.  Everything went smoothly, so smoothly in fact that when I went to install wine via "sudo apt-get install wine" method it pretty much told me that I already had the latest version installed.
I double-clicked on the "setup.exe" for MS Office Suite which is on an NTFS hard drive and it started to load up the "Add Applications" menu, which showed me pretty much all of the open source apps I can install on my system.
Could it be because the install files and setup.exe are on an NTFS partition?

---

### Post by the_izman on 2006-03-05
While I'm here I may as well try going through Automatix.
Thanks for the link :p

---

### Post by aysiu on 2006-03-05
[QUOTE=the_izman]
Could it be because the install files and setup.exe are on an NTFS partition?[/QUOTE] Yes. To use Wine properly, you should install things to the hidden directory in your /home folder, not on an NTFS partition.

I'm not sure how well Microsoft Office works in Wine (I think it depends what version of Office you have). Is there any reason in particular that you can't use OpenOffice, Gnome Office, or KOffice?

---

### Post by the_izman on 2006-03-05
oh sorry about the confusion.
Only the install files are in the NTFS partition.  Should I move all the install files oto my Ubuntu partition first?
And in answer to your other question...the wife and kids are used to Office Suite as well as pretty much everyone else I know of.
I myself have used OpenOffice as well as StarOffice and find them quite handy.  I had Mandrake and Knoppix installed on another machine before this one.  The Mandrake one I only had for about a week so I never really got a chance to play with it that much.

---

### Post by aysiu on 2006-03-05
Well, if it does work (and I don't know that it will), install it to ```
~/.wine/drive_c/Program Files/Office
``` If that doesn't work, just put them on OpenOffice. They'll get used to it.

---

### Post by the_izman on 2006-03-05
I'll try a couple more things and see if anything does work.  If it does (and I have my doubts too) I will definitely post them up here.  If not I guess they will have to get used to OpenOffice....or just reboot the machine back into Windows :evil:

---

### Post by aysiu on 2006-03-06
Frankly, having used two versions of OpenOffice and at least three version of Microsoft Office, I don't see what the big deal is (of course, it's ultimately up to your family members to decide what a "big deal" is).

There are often more differences between versions of Microsoft Office than between Office and its corresponding version of OpenOffice.

The interface is very similar, and OpenOffice does just about everything Microsoft Office does (except grammar check and some Macro stuff).

---

### Post by baysteve on 2006-03-06
i attempted to install LimeWire with wine, everything went smoothly till a part of the installation where it tried to install Java..I am totally confused by this as it seems I already have java installed? maybe if i paste some of my error it would help..here goes (i appreciate you all putting up with my noobness)
```

fixme:win:SetWindowTextA setting text "LimeWire 4.10.9 Setup" of other process window (nil) should not use SendMessage
fixme:shell:BrsFolder_OnCreate flags 40 not implemented
fixme:shell:BrsFolderDlgProc Set selection "c:\\Program Files\\LimeWire"
wine: Unhandled exception (thread 0013), starting debugger...
err:seh:EXC_DefaultHandling Unhandled exception code c0000005 flags 0 addr 0x7fcdb5c3
Can't attach process 11: error 87

```

---

### Post by aysiu on 2006-03-06
Why are you installing Limewire through Wine? There's a native Linux version.

[http://makuchaku.info/amnesty/#limewire](http://makuchaku.info/amnesty/#limewire)

---

### Post by baysteve on 2006-03-06
I noticed that..the install files are no longer there though..and I could not find them anywhere else so I thought I would try wine

---

### Post by mwanafunzi on 2006-03-06
hi, try frostwire instead of limewire. [http://www.frostwire.com/static/index.html](http://www.frostwire.com/static/index.html)

go to downloads and click on the debian/ubuntu link

edit: just as a side note as to why you wouldnt want to rely on open office (and I am not if anyone is having these problems), even though you can save your work in .doc or any other mirosoft office format, I am having some problems with the formatting when I open the file in word. Don't get me wrong though, OO is great and everyone should switch to it, but just make sure that you doule check the work you have done (say in OO writer) in word before handing it in to your boss or teacher or for anything official

---

### Post by steve.horsley on 2006-03-06
[QUOTE=the_izman]oh sorry about the confusion.
Only the install files are in the NTFS partition.  Should I move all the install files oto my Ubuntu partition first?
And in answer to your other question...the wife and kids are used to Office Suite as well as pretty much everyone else I know of.
I myself have used OpenOffice as well as StarOffice and find them quite handy.  I had Mandrake and Knoppix installed on another machine before this one.  The Mandrake one I only had for about a week so I never really got a chance to play with it that much.[/QUOTE]

You should be able to right-click an .exe file in nautilus and choose Properties, Open With. There you can add a custom command. The command is wine.

Now double-clicking an .exe should launch it in wine. You may need to drag your installer to a Linux drive, especially if it tries to extract files into its current directory. You can't write NTFS from Linux, so the extraction would fail.

---

