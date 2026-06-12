---
title: "Help on how to do a clean uninstall"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Sable683 on 2007-03-31
I am trying to find help on how to completely remove a program from Wine. I have installed Quicken 2006 Basic and have had nothing but problems. 
Here is what I have done so far:
1) I used the Wine Uninstaller, however, I was unable to completely remove Quicken 
    from my machine, it still shows up on my menu. 
2) I attempted to edit the "registry" in Wine, but it got to be too tedious to remove all 
    of the strings relating to Quicken. 
3) I have attempted to uninstall Wine (this is the only program I installed with it), but 
    when I do, I still have the .wine folder in my home directory.
4) I re-installed Wine and installed a windows registry editor, but that program did not
    work.
5) I removed Wine again with the Add/Remove Applications and I still have the .wine 
    folder in my Home directory.
6) I then deleted the .wine folder from my home directory and rebooted the box, but  
    still have the Wine, Quicken & Registry Mechanic on my menus.
7) Every time I open the Main Menu Preferences editor and click on Wine to uncheck 
    it, it crashes.

Any help would be appreciated. I cannot think of anything else to try at the moment.

Thanks in advance,

John

---

### Post by Jussi Kukkonen on 2007-03-31
Go to synaptic, select Wine-package, select "remove completely", and click Apply.

That removes the Wine and all of its configuration files.

---

### Post by Sable683 on 2007-03-31
Thank you.... I used synaptic to completely remove Wine. Synaptic says process completed successfully.

I checked the menu and I still have Wine there, now the Quicken Icon does not appear on my menu but the Registry Mechanic icon is still there. I rebooted the box, but alas... it remains the same. 
I checked synaptic manager and the add/remove applications and it is showing not installed. Also, the .wine folder is still in my home folder. Any other ideas?

Thanks,

John

---

### Post by joeycbulk on 2007-03-31
If the menu you are referring about is from gnome or kde then you will have to manually remove it. Check ~/.wine/<drive>/Program Files or <windir> for files that have not been removed.

The applications installed in wine may not appear in synaptic since applications found from it are files you have installed and applications available for installation(e.g. updates) that came from your repository for your LINUX or *.deb packages.

If your concern are registry values or libraries that have not been removed from wine then the problem may also exist if your using windows. The only difference is that you have noticed it because they try to make Linux and its applications as transparent as possible, which means that with Linux you are able to see almost everything happening behind it unlike windows. Transparency is one of the things that makes Linux beautiful.

If your really want to make sure if everything is remove then:
1. Uninstall wine from synaptic.
2. Delete ~/.wine folder
3. Check /etc for configurations for files related to wine then delete it.(Make sure to make backup then restart. If everything goes well then its safe to delete your backup files)
4. Same procedure as number 3 but this time you check /bin and /usr for binaries.

---

### Post by Sable683 on 2007-03-31
Joey, 
  
    I'm only running Ubuntu, no windoze dual boot here. My concern was that if Quicken was not removed, some of the orphaned DLL files in the registry could interfere with something that I will install at a later time. It was just aggravating that no matter how many times I used the wine uninstaller, both programs would not uninstall. 
    I followed your advise, but could not find and .conf files in etc, usr or var. I ended up installing Wine again so I can use it for other programs. On a side note, it pays to check the Wine Application Compatibility page, they have the work-arounds for some programs that could come in handy.

Thanks again,

John

---

### Post by joeycbulk on 2007-04-01
uninstallation of wine from synaptic only removes the files used by wine. It does not remove the application you installed in wine. This is to preserve the changes you made(e.g. configurations of programs installed).

Try exploring the /home/<user>/.wine/, you will see *.reg files, dosdevices folder, and drive_c folder. The *.reg files within .wine folder are registry values you find in regedit. The drive_c folder contains the subfolders which contains the *.dll files and *.exe files you installed in wine. The dosdevices contains the link to the folders that acts as your storage devices.

As you said earlier, you have deleted the .wine folder, this does the job of removing everything you installed(e.g. binaries or *.exe, libraries or *.dll, registry values, and configuration files), no need to be concerned about orphaned files. 

The menus you find and the shortcuts you find in your desktop was not removed because it is no related to your wine installation and .wine folder. Its more related to your desktop environment and the application you installed from wine. Seeing these shortcuts after deleting the .wine folder does not mean that you failed in doing a clean uninstall. All you have to do is manually remove these shortcuts.

Some programs you installed from wine may not have worked not because of the orphaned files that you were concerned about but more likely about compatibility issues, its good that you have checked the wine web site. Make sure that you are looking at the same version of program and same Linux distribution and also check for its rating; things that have worked, and things that have not worked.

From your earlier post, you said that the menu crashes. This could be a bug from your desktop environment or a problem from your Linux installation. Check for updates related to you desktop environment and install it.

---

