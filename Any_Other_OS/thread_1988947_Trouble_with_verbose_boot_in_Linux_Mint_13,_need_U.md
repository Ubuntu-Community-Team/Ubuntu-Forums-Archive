---
title: "Trouble with verbose boot in Linux Mint 13, need Ubuntu user's default.plymouth"
date: 2012-05-28
forum: Any Other OS
---

### Post by GoldenKevin on 2012-05-28
Hi guys. Back when I used Ubuntu 10.04 LTS, I found a handy way to enable verbose boot by going into Synaptic and removing all packages that matched plymouth-theme-*. I wish I could do the same with Linux Mint, but it appears as though the developers have installed several themes that aren't even part of a package - they're just there when the distro is installed and there is no way to remove them with apt, which I assume would automatically update default.plymouth whenever a theme is installed or uninstalled. So I need an Ubuntu user who removed all the plymouth-theme-* packages on their computer and has verbose boot working to post their contents of

```
/lib/plymouth/themes/default.plymouth
```

Right now this is what I have:

```
[Plymouth Theme]
Name=No Logo
Description=A theme that features a blank background.
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/no-logo
ScriptFile=/lib/plymouth/themes/no-logo/no-logo.script
```

and I want to get rid of that [Plymouth Theme] thing safely without breaking my Linux Mint install.

---

### Post by Tido on 2012-07-31
I played a litte bit around, but didn't get smart.
What I found: ```
sudo -s
cd /lib/plymouth/themes/
ls -la

you can see that it points to:
default.plymouth -> /etc/alternatives/default.plymouth
text.plymouth -> /etc/alternatives/text.plymouth

cd /etc/alternatives/
ls -la
in this folder you can see that they point to:
default.plymouth -> /lib/plymouth/themes/no-logo/no-logo.plymouth
text.plymouth -> /lib/plymouth/themes/no-text/no-text.plymouth

So the files are in:
/lib/plymouth/themes/no-logo/
```
The folder details contains```
[Plymouth Theme]
Name=Details
Description=Verbose fallback theme
ModuleName=details
``` which sounds to me for what we are looking for. But I have no clue how to activate this file

---

