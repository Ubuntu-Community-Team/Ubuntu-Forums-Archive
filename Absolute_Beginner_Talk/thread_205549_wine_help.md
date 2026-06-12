---
title: "wine help"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by shootdamonkey on 2006-06-28
i installed wine but now eveytime i winecfg i get this:

err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.

and i cant seem to figure out how to use it.

Also i downloaded the demo of crossover office which i have on the desktop, but have no idea how to install that (its an sh file if taht helps)

---

### Post by Kilz on 2006-06-28
[QUOTE=shootdamonkey]i installed wine but now eveytime i winecfg i get this:

err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ root\\Desktop"'.

and i cant seem to figure out how to use it.

Also i downloaded the demo of crossover office which i have on the desktop, but have no idea how to install that (its an sh file if taht helps)[/QUOTE]
Im not sure of the problem with winecfg, but to install the crossover office. 
Open a terminal and type in 
```
cd ~/Desktop
```
then
```
sudo sh ./<filename>
```
Changing <filename> for whatever the crossover offices file name is That will start the install.

---

### Post by shootdamonkey on 2006-06-28
i tried the cd desktop thing and got:
bash: cd: /home/gaz/desktop: No such file or directory

---

### Post by shoot2kill on 2006-06-28
use a capital "D" in desktop

---

### Post by shootdamonkey on 2006-06-28
it uncompresseed it and everything but now says:

The '/home/gaz' directory does not belong to you.
Point $HOME to your home directory and try again.

Sorry about this i'm a ubuntu noob lol

---

### Post by shoot2kill on 2006-06-28
maybe a stupid question, but is your username "gaz"

---

### Post by shootdamonkey on 2006-06-28
yip it sure is

---

### Post by shootdamonkey on 2006-06-28
ah it works fine now, i just cant find the programs to run lol

---

