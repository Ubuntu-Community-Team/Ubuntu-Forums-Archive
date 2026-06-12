---
title: "WINE installed programs has no Icon"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2005-11-14
my programs installed in WINE 0.9 does not show its icon on my desktop, instead it only show Prograname.lnk, I used WINE before at it shows both Programname.lnk and the Icon of the program just like in window$ Desktop

my other question on WINE is that is it really slow when I don't use -opengl??

---

### Post by reedlaw on 2005-11-14
I always create my own launchers (in Gnome, right-click desktop and choose New Launcher).  You can input 'wine /path/to/program.exe' as the command.  Choose an icon and you're ready to go.
As far as the -opengl command, my wine runs very fast without it.  I can run Picasa2 no problem.

---

### Post by jeffreyvergara.NET on 2005-11-14
the weird thing is that I installed programs before (games) and it's original icon shows on desktop, but now it wont...

---

### Post by reedlaw on 2005-11-14
I know KDE adds wine icons to its menus.  I have also seen games in wine install desktop icons.  Maybe it is only with a different version of wine or with winetools.  I am using sidenet-config with wine now.  It gets everything I need working and comes with React Explorer that shows your fake-windows directories and can launch any program with a double-click.

---

### Post by jeffreyvergara.NET on 2005-11-15
maybe the reason I dont get the original icons of the exes is that I compiled WINE.?

---

### Post by jeffreyvergara.NET on 2005-11-16
is there away to get Icons from exe files?

---

### Post by Stormspace on 2005-11-16
My Wine installation doesn't create icons that function either. I usually have to create an entry in the menu as such:

wine "/home/user/c/windows/program files/app directory/app.exe"

note I use quotes around the path since wine doesn't like the spaces in it.

---

### Post by jeffreyvergara.NET on 2005-11-16
it does creates my an Icon but no image and cannot be openned, it has a ProgramaneIcon.lnk with a foot icon.

---

### Post by Rackerz on 2005-11-16
I can't even get Wine working. It wont launch exe's .. could someone help me?

---

### Post by Stormspace on 2005-11-16
[QUOTE=jeffreyvergara.NET]it does creates my an Icon but no image and cannot be openned, it has a ProgramaneIcon.lnk with a foot icon.[/QUOTE]

Same here. This icon is placed there by the windows installation routine and is not a gnome icon. I don't know how to make *.ink files work, but the best solution I've had is to just create a new desktop item and put the wine command in the settings.

---

### Post by Stormspace on 2005-11-16
[QUOTE=Rackerz]I can't even get Wine working. It wont launch exe's .. could someone help me?[/QUOTE]

I had the same trouble. My solution was to uninstall wine, set the file browser to show hidden files and then go to /home/username/./wine and delete all of the c drives I saw there. Reinstall wine and then use sidenet to install IE. From that point on it worked fine.

---

### Post by Rackerz on 2005-11-16
Ok i've uninstalled Wine. But i don't know how to set the file browser to show hidden files and folders. 

Thanks for your help :)

---

### Post by Stormspace on 2005-11-16
I don't have my Ubuntu box in front of me, so look for a folder options menu item in nautilus. Or something similar. Anyone else have the direct menu item and menu for this guy? I'll check when I get home and if you don't have a reply, I'll post it.

---

### Post by Rackerz on 2005-11-16
I forgot to mention I'm using Kubuntu. So i don't think i can use nautilus.

---

### Post by Rackerz on 2005-11-16
Ok i've worked how to view hidden files and folders. I just can't delete the drive_c folder to the waste bin!

---

### Post by Stormspace on 2005-11-16
[QUOTE=Rackerz]Ok i've worked how to view hidden files and folders. I just can't delete the drive_c folder to the waste bin![/QUOTE]

When I did mine, I saw something like c.111520051134. And there were more than one like that, each with a date and timestamp in the folder name. I suspect that the multiple instances of wine were confusing it, thus the reason it started working once I deleted those and reinstalled Wine. Please don't just take my word for it though, get a second opinion.

---

### Post by Rackerz on 2005-11-16
I re-installed Wine but now it's asking for a drive_c. Hmmmm.

---

### Post by Stormspace on 2005-11-16
[QUOTE=Rackerz]I re-installed Wine but now it's asking for a drive_c. Hmmmm.[/QUOTE]

run winecfg.

---

### Post by Rackerz on 2005-11-16
Ok i've added one but now when i try to run a file it says it can't find my temp folder.

---

### Post by Stormspace on 2005-11-16
[QUOTE=Rackerz]Ok i've added one but now when i try to run a file it says it can't find my temp folder.[/QUOTE]

Go ahead and install sidenet and run that with option 3 for IE6.

---

### Post by jeffreyvergara.NET on 2005-11-17
i just installed cedega to to try it, the it asked for xlibs installation. after that I tried to install programs again in WINE and the icons worked fine, I removed Cedega and retained xlibs, and the Icons still work fine, so maybe xlibs is the solution?

---

### Post by Rackerz on 2005-11-17
[QUOTE=Stormspace]Go ahead and install sidenet and run that with option 3 for IE6.[/QUOTE]

Were can i get SideNet? Also i ran a tool called winesteuptk and directed to my install of Windows. It wont run programs like MSN Messenger or Windows Media Player but Winehq says it can :S. 

Thanks for your help

---

### Post by Stormspace on 2005-11-17
Here ya go. 

Once I installed Sidenet many things started working. That's not to say I still don't have issues. :)

[http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.0.tgz]("http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.0.tgz")

---

### Post by Rackerz on 2005-11-17
Thanks :)! Just installing now, i'll let you know if i have any problems.

Cheers!

---

### Post by Rackerz on 2005-11-17
Well i had problems which is why im forced back on Windows. IE worked once then it failed to load up internet pages again and again. Then i tried to install MSN Messenger which is supposed to work with Wine, but it kept saying i needed a XP/2000 system. I tried adding the application to the winecfg screen under 'Windows XP' but it still failed to work. Any ideas?

---

### Post by Stormspace on 2005-11-17
I'm still experienceing some issues with my install. For instance MS office installs and runs, IE runs, but frontpage opens but will not import or export webs. I've hit a dead end on several of my apps but think the answer lies in dcom, which gives me a strange error at the end of the installation.

---

### Post by Rackerz on 2005-11-17
Well thing is i really need some windows apps. Some are quite important but wont seem to run. Thats the problem i rely on alto of Windows progs.

---

### Post by Stormspace on 2005-11-17
[QUOTE=Rackerz]Well thing is i really need some windows apps. Some are quite important but wont seem to run. Thats the problem i rely on alto of Windows progs.[/QUOTE]

If I could get frontpage and Musicmatch to run I'd be happy for a while. :)

---

### Post by pdpmalcolm on 2005-11-17
im having some problems too... when i try to launch photoshop.. it stops and say:

"Could not inititialized Photoshop because teh file is locked. Use the 'Properties" command in Windoes Explorer to unlock the file."

---

