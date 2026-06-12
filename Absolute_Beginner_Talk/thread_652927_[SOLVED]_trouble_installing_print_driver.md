---
title: "[SOLVED] trouble installing print driver"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by trugreg on 2007-12-29
Still a lot to learn --  in first week after escaping Windows 

- after i download hp print driver in Gutsy 7.10 i get this error trying to install -

Could not open the file /home/greg/Desktop/hplip-2.7.12.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by aktiwers on 2007-12-29
You should do like this in Terminal (Applications => Accessories => Terminal):

Go to the Desktop where the file is stored
```
cd Desktop
```
Make it executable 
```
chmod +x hplip-2.7.12.run
```
Run the File
```
sudo ./hplip-2.7.12.run
```

Because you are trying to run a Binary.

I Think that should work

---

### Post by trugreg on 2007-12-29
I think I need it because Ubuntu isn't "seeing" my printer.

---

### Post by trugreg on 2007-12-29
SOMETHNG IS NOT RIGHT -  PROBABLY ME

greg@greg-desktop:~$ chmod +x hplip-2.7.12.run
chmod: cannot access `hplip-2.7.12.run': No such file or directory
greg@greg-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
greg@greg-desktop:~$ sudo ./hplip-2.7.12.run
[sudo] password for greg:
sudo: ./hplip-2.7.12.run: command not found
greg@greg-desktop:~$

---

### Post by RRS on 2007-12-29
> greg@greg-desktop:~$ cd desktop
I believe it should be "cd Desktop"

Linux is case sensitive

Simply copy/paste Aktiwers' code into your terminal, I've found it a good way to avoid typo's.

---

