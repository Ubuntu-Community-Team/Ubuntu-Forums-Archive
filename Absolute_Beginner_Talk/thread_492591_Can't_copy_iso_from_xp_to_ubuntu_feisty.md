---
title: "Can't copy iso from xp to ubuntu feisty"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by kpictjl on 2007-07-04
While sitting on my Ubuntu machine using Nautilus I am unable to copy/paste linux distro iso files from my Windows XP laptop to my Ubuntu Feisty desktop across my network.  I am able to copy other files just fine including other iso's (specifically Windows Home Server Beta iso's).   Ubuntu gives me a dialog box error that says "smb://minnie...netinst.iso" cannot be copied because you do not have permissions to read it."  To make it worse, when I am sitting on my XP machine I am able to copy the same file to my Ubuntu box using Windows Explorer.

So I'm able to get the job done...I just shouldn't have to leave my ubuntu machine to do it.

Thank you.

---

### Post by scragar on 2007-07-05
you properly don't have perditions to copy the file, as far as linux is concerned, the only way to do this asides from changing the perms would be to use the terminal.

Applications > Accessories > Terminal

then type:

sudo mv _File to move including path_ _where to move the file, including name if you wish to rename it_

alternativly you could use the terminal to give everyone permition to read it solving the access problem:

sudo chmod ogu+r _file name including path_

both of these should prompt for a password unless you have entered it recently.

---

### Post by kpictjl on 2007-07-05
Thanks, I tried your suggestions but still no joy.

I mounted the smb share in accordance with [ubuntuguide.org]("http://http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read")
sudo mount //windowspcname/MyDocuments /media/tmp -o username=windowslogon,password=mypassword,dmask=777,fmask=777

Then I was able to use the touch command to create new files in that directory so I know have write permissions.

> **scragar said:**
> sudo mv _File to move including path_ _where to move the file, including name if you wish to rename it_
Then I tried a cp and a mv but I still get "mv: cannot open `debian-40r0-i386-netinst.iso' for reading: Permission denied"

> **scragar said:**
> 
alternativly you could use the terminal to give everyone permition to read it solving the access problem:
Tried that even though 'ls -l' showed that all files were 777 already.  The chmod command seemed to work find but it didn't help.

---

### Post by Axed on 2007-07-05
In that case It appears that the permissions problem is actually on the XP machine rather than the Ubuntu machine. The methods for altering permissions in XP depend on whether you are using simple or advanced file sharing (Home forces you to use simple file sharing). 

If you're using simple file sharing, un-sharing and re-sharing the folder that contains the ISOs should fix it. If you're using advanced or if re-sharing the folder doesn't fix it - edit the permissions of the parent folder, click advanced, and then replace the permissions on child objects.

---

### Post by kpictjl on 2007-07-06
> **Axed said:**
> In that case It appears that the permissions problem is actually on the XP machine rather than the Ubuntu machine. The methods for altering permissions in XP depend on whether you are using simple or advanced file sharing (Home forces you to use simple file sharing). 

If you're using simple file sharing, un-sharing and re-sharing the folder that contains the ISOs should fix it. If you're using advanced or if re-sharing the folder doesn't fix it - edit the permissions of the parent folder, click advanced, and then replace the permissions on child objects.

No joy.  My XP machine is XP Pro.  I un-shared the entire and then re-shared the entire folder via the XP Pro sharing gui.  Then, from Ubuntu I can still only copy some of the files to my Ubuntu machine.

---

### Post by kpictjl on 2007-07-06
After making a copy of the files on my XP Pro machine, I was then able to copy the files to my Ubuntu box using Nautilus.

---

