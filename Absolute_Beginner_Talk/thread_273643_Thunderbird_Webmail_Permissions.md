---
title: "Thunderbird Webmail Permissions"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by bedfojo on 2006-10-08
I am setting up the Webmail extension for Thunderbird on Xubntu 6.06. I need to allow write access to the applcation folder (Thunderbird I assume) but I can't recall were it is.   On which files/folders do I need to change the permissions? Thanks.

---

### Post by William the Conquerer on 2006-10-08
Why exactly do you need to change write permissions on the thunderbird application folder if you're installing an extension...  do you mean the .mozilla-thunderbird folder in your home directory?...  so if you're at a command prompt thats:
```
$ cd ~/.mozilla-thunderbird
```

---

### Post by bedfojo on 2006-10-09
That's the one.

For some reason when Thunderbird is set up, the folder permissions will not allow the Webmail extension to write to the folder.  Therefore the account manager will not include webmail options unless Thunderbird is run by sudo. To get round it you need to allow permissions. I had just forgotten where.

Thanks so much, these forums really are amazing.

---

### Post by bedfojo on 2006-10-10
Actually for anyone else with the same problem, you also need to allow write access to usr/lib/mozilla-thunderbird/defaults/isp/

---

### Post by nrayever on 2006-10-20
> **bedfojo said:**
> Actually for anyone else with the same problem, you also need to allow write access to usr/lib/mozilla-thunderbird/defaults/isp/

bedfojo:

i have tried to set permissions in /usr/lib/mozilla-thunderbird/defaults/isp/ as 755 but still ddoesn't work!! do you have any other idea of which directory has a bad setup on permissions??

my .mozilla-thunderbird has the same permissions 755. i don't get it!! ](*,) ](*,) ](*,) 

please some help!!

nrayever

---

### Post by aysiu on 2006-10-20
I don't think it should have anything to do with /usr/lib/mozilla-thunderbird/defaults/isp

All extensions get installed to your local directory.

Close Thunderbird

Then paste this command in the terminal ```
sudo chown -R nrayever:nrayever /home/nrayever
``` Open Thunderbird again and try to install the extension.

---

### Post by nrayever on 2006-10-20
> **aysiu said:**
> I don't think it should have anything to do with /usr/lib/mozilla-thunderbird/defaults/isp

All extensions get installed to your local directory.

Close Thunderbird

Then paste this command in the terminal ```
sudo chown -R nrayever:nrayever /home/nrayever
``` Open Thunderbird again and try to install the extension.

aysiu:

i have check my home folder and the permissions are set to nrayever:nrayever. i have to tell you that i haven't used the command, because i checked the permissions on my home folder and for .mozilla-thunderbird folder and both folders have permissions are set for nrayever:nrayever.

do you still think that i need to run the command??

nrayever

---

### Post by aysiu on 2006-10-20
The **-R** option makes the ownership *recursive*, meaning that it will apply to not only the folder itself but all the subfolders and files within those folders.

It's just to make sure your extensions folders and files didn't somehow lose ownership.

---

### Post by everettattebury on 2006-11-03
The reason that you need to change the permissions for /usr/lib/mozilla-thunderbird/defaults/isp is that the webmail extension wants to write a file, webmail.rdf, to that directory.  This file is what adds the extra entry for webmail accounts to the new account wizard for Thunderbird.

You only need to change the permissions until that file is written, then you can change them back.

---

