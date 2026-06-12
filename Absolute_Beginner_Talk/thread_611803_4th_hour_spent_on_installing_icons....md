---
title: "4th hour spent on installing icons..."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by BloodRedSandman on 2007-11-13
OMG...

I've downloaded icons in tar.gz file then unpacked it
- I've tried to drag and drop it to /usr/share/icons -> no permission
- the I typed ```
sudo cp ./icon_pac /usr/share/icons/
``` -> ...catalog was skipped

Please tell me how can I copy one catalog into another :confused:

---

### Post by bulldog on 2007-11-13
Just copy them to your .icons folder in your home.

---

### Post by ukripper on 2007-11-13
Try this way - on terminal type following
```
su
```
enter your root password and then try copy over

cp {file} {target}

---

### Post by mcduck on 2007-11-13
> **ukripper said:**
> Try this way - on terminal type following
```
su
```
enter your password and then try copy over

cp {file} {target}

That won't work. 'su' needs root user's password, which doesn't even exist.. For same results in Ubuntu you need to use 'sudo -i' and your own password.

Anyway, if you only want to install the icons for one user, just put them into a hidden directory inside your home dir, called .icons.

For all users, you could just open the file manager as root by running 'gksudo nautilus' and use that to extract the icons into correct place. Anyway, the original command was also wrong (unless the extracted icon directory really is hidden one for some strange reason..). "sudo cp -R icon_pac /usr/share/icons/" should work.

---

### Post by stchman on 2007-11-13
> **BloodRedSandman said:**
> OMG...

I've downloaded icons in tar.gz file then unpacked it
- I've tried to drag and drop it to /usr/share/icons -> no permission
- the I typed ```
sudo cp ./icon_pac /usr/share/icons/
``` -> ...catalog was skipped

Please tell me how can I copy one catalog into another :confused:

To install icons do the following:

System--->Preferences--->Themes

Click on the Install and then navigate to the .tar.gz archive of icons you want.  Highlight and click on the archive and open it.  The Themes manager will unpack and install the Icons.  In the Icons tab under the Customize tab you will see the set of icons you wish to use.

Do not unpack the archive.

---

