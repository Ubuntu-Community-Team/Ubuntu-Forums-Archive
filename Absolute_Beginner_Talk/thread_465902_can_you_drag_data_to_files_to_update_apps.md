---
title: "can you drag data to files to update apps?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by stewartclandot on 2007-06-06
Hi everyone, Ubuntu Noob here.  I accidentally managed to screw up my dual boot attempt with my Windows 2000 machine, and now only have Ubuntu Feisty Fawn on my hard drive.  All of my Windows files are visible as "HD1" though so I'm not too bothered.  Is it possible however to move my "Inbox" firefox file from my Windows 2000 Firefox location to the Ubuntu Firefox in order to get my Ubuntu email up to speed?.  On my Mac laptop I was able to drag the file to the Firefox file and it updated automatically.  Unfortunately I can't even find my "inbox" file that goes with my new Ubuntu install.
Thanks much for any help.

---

### Post by AndyCooll on 2007-06-06
Your Firefox files are hidden by default in your home folder. CTRL+H should make them visible. The folder you are looking for is .mozilla. And yes you should be able to drop them in (though I'd make a backup of the folder first, just in case).

:cool:

---

### Post by Carlos Santiago on 2007-06-06
Yes you can!
You can do even better, you can make a symbolic link (see 'man ln' on a terminal).

if you make 
```
ln -s real_file alias_for_the_real_file
```
You can access that file from 'real_file' or  from 'alias_for_the_real_file'

```
Try this:
mv ~/.mozilla ~/my_old_mozilla_folder
ln -s /media/hda1/Documents\ and\ Settings\<your user>\Application Data\Mozilla ~/.mozilla
```

If it work. OK ;-)
If not, move back with
```
rm ~/.mozilla
mv  ~/my_old_mozilla_folder ~/.mozilla

```

---

