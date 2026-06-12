---
title: "Minor issues"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-02-12
Hiya, folks. 

I am facing a few minor annoyances that were sort of *always there* (The functions, not the annoyances.) in Windows XP but I can not seem to find them in Ubuntu Linux. 

I'll just create a list since there's quite a few of them: 

[list]
[*]How do I create an euro sign? CTRL + ALT + 5 does not work
[*]Why can I not select the maximum fresh rate available for my monitor? The monitor (902D Deawoo) is capable of 100Hz at 1024x786. It's now at 75Hz. Using a 32MB Nvidia MX400. 
[*]Why can I not turn off the PC by pressing the power button? Windows XP shut it self down when I did that.
[*] Is there a way to have the Windows key bring up my Applications menu? 
[*]Why do not all programs I install add themselves to the Applications menu? 
[*]How do you get one of those ' (Accent grave?) above an e? The ' key doesn't seem to *stick*
[*]Where's PAINT? :KS 
[/list]

Well, thanks for any answers you're able to provide me with. These are just some minor issues that are bothering me from time to time.

---

### Post by mdsmedia on 2006-02-12
To power down using the power button...hold it down for 10 seconds. That should power you down.

Paint is a Windows program. There are Linux equivalents...sorry....alternatives. Try "The Gimp" for probably the most comprehensive.

---

### Post by bonzodog on 2006-02-12
*The euro sign is on altgr + 5 (4 on my keyboard).
*Not sure about the refresh rate thing..I have wierd problems with ubuntu selecting wrong refresh rates, but normally it is listed in resolution settings in the menu.
*ah, yeah, linux has a very specific shutdown procedure that means you need to request a proper shutdown. ACPI does not currently handle power button shutdowns.
*it's possible that you are installing programs manually, in which case, run the menu editor and add the menu item. most, not all, stuff installed through synaptic  adds itself to the menu, but occasionally requires to be manually added.
*not sure what you mean about this
*sudo apt-get install gpaint

---

### Post by atoponce on 2006-02-12
[quote=UbuntuRaptor]Hiya, folks. 

I am facing a few minor annoyances that were sort of *always there* (The functions, not the annoyances.) in Windows XP but I can not seem to find them in Ubuntu Linux. 

I'll just create a list since there's quite a few of them: [LIST]
[*]How do I create an euro sign? CTRL + ALT + 5 does not work
[*]Why can I not select the maximum fresh rate available for my monitor? The monitor (902D Deawoo) is capable of 100Hz at 1024x786. It's now at 75Hz. Using a 32MB Nvidia MX400.
[*]Why can I not turn off the PC by pressing the power button? Windows XP shut it self down when I did that.
[*] Is there a way to have the Windows key bring up my Applications menu?
[*]Why do not all programs I install add themselves to the Applications menu?
[*]How do you get one of those ' (Accent grave?) above an e? The ' key doesn't seem to *stick*
[*]Where's PAINT? :KS[/LIST]Well, thanks for any answers you're able to provide me with. These are just some minor issues that are bothering me from time to time.[/quote] [LIST]
[*]Which keyboard are you using?  Are you using the US keyboard?  Then in Gnome only, the shortuct is Press and hold **Ctrl Shift**, then enter the sequence "20ac".  See the [Wikipedia entry]("http://en.wikipedia.org/wiki/Keyboarding_the_euro_sign") for other keyboards.
[*]Windows has the nastly ability to use refresh rates above what your monitor is capable, even if it is displayed in your display settings.  Tell me, honestly, can you see the difference between 100 and 75?
[*]I am not sure of a way to power off the machine by pressing the power button.  You could just as easily put a shortcut on your desktop that will power down the machine.  The command for the shortcut would be "sudo /sbin/shutdown -h 0" (wihtout the quotes)
[*]Under System -> Preferences -> Keyboard Shortcuts, you have the ability to change "Show the Panel Menu".  Select it until it says "New accelerator..." and press your Windows key.
[*]You need to press and hold **Ctrl Shift** while typing in the hexadecimal equivalent.  In this case it would be "xe8"
[*]"Paint" is a Windows program, but there are alternatives.  Gimp is a powerful graphics alternative that is competing with Photoshop.  It is installed by default.  You could also install gpaint through Synaptic or apt-get.[/LIST]Hope that helps.

---

### Post by user_of_gnomes on 2006-02-12
Thanks to all of you and for your quick response! All of my questions are now answered. 

Although I'd like to know some alternatives to the following issues:

> Windows has the nastly ability to use refresh rates above what your monitor is capable, even if it is displayed in your display settings. Tell me, honestly, can you see the difference between 100 and 75?

This monitor, with proper drivers, is capable of going up to 120Hz on 800x600, 100hz on 1024x786. I like to think this is more healthy for my eyes. Perhaps if I believe hard enough it, it just might be. ;) 

> Which keyboard are you using? Are you using the US keyboard? Then in Gnome only, the shortuct is Press and hold Ctrl Shift, then enter the sequence "20ac". See the Wikipedia entry for other keyboards.

Works, but that's a lot of work for one character. I have a Microsoft natural keyboard with US layout. 

> You need to press and hold Ctrl Shift while typing in the hexadecimal equivalent. In this case it would be "xe8"

Is there no way to make keys *stick* like they do in Windows?

> *it's possible that you are installing programs manually, in which case, run the menu editor and add the menu item. most, not all, stuff installed through synaptic adds itself to the menu, but occasionally requires to be manually added.

Where can I find the "menu editor"?

---

