---
title: "My Gimp has NO Help files?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by adrians on 2005-12-23
Hi

Very new to all this Ubuntu lark having just installed system on my home PC; I tried to use GIMP, but found NO help info with the following message:-

"The GIMP help files are not installed.  Please make sure gimp-help-en is installed......

Could not open '/usr/share/gimp/2.0/help/en/gimp-help.xml for reading: No such directory."

I find that '/usr/share/gimp/2.0/help' folder is indeed missing.

What do I need to do to sort this out?

---

### Post by TimL on 2005-12-23
Hi,

You just need to install the 'gimp-help-en' package through synaptic or apt-get.

To install through apt-get, type the following in a shell:

```
sudo apt-get install gimp-help-en
```

Type your password when prompted. You should then be able to view the GIMP's help files.

Cheers,

Tim

---

### Post by Madpilot on 2005-12-23
Check Synaptic for "gime-helpbrowser", "gimp-help-common" and "gimp-help-en". (or your language of choice, for that last package.)

Make sure they're installed, restart the GIMP, and you should be OK.

I wish doc & help files were installed by default - it's irritating that they aren't.

---

### Post by adrians on 2005-12-24
[QUOTE=TimL]Hi,

You just need to install the 'gimp-help-en' package through synaptic or apt-get.

To install through apt-get, type the following in a shell:

```
sudo apt-get install gimp-help-en
```

Type your password when prompted. You should then be able to view the GIMP's help files.

Cheers,

Tim[/QUOTE]

Thanks Tim,  It worked fine.  Adrian

---

