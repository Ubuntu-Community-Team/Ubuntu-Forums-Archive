---
title: "bad deb package install. Now synaptic and apt-get won't work"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-01-13
I tried installing the deb packages from brother for my brother mfc6800 printer and got several errors.
Now when I try to remove it it says the package is in a very unstable state and I have to reinstall it before I can remove it. I can't install it because of the following problem. 

Now synaptic , apt-get, and update console won't work
I get an error message and then it closes
same thing when I try "sudo apt-get -f install"

E: The package mfc6800lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Can someone help me at least remove it and then tell me how to install my printer?

The main thing now is removing the partially installed package though.

Thanks

---

### Post by polmir on 2008-01-13
```
sudo dpkg -i /path to/mfc6800lpr.deb
```

---

### Post by iansane on 2008-01-14
> **polmir said:**
> ```
sudo dpkg -i /path to/mfc6800lpr.deb
```

isn't that the same as cd to the directory and do "sudo dpkg -i mfc6800lpr.deb" ? 

I did that and I'm in the directory (Desktop) but I'll try including the whole path.

I really need to figure out how to remove it because there are several error messages during the attempted install. Files and directories don't exist, permissions denied, and things like that.

There has to be a way to remove the partial install without installing it.

If I could install it I wouldn't be removing it.

---

### Post by polmir on 2008-01-14
[HTML]man dpkg[/HTML]

 >  dpkg -r | --remove | -P | --purge package ... | -a | --pending
              Remove an installed package. -r or  --remove  remove  everything
              except configuration files. This may avoid having to reconfigure
              the package if it is reinstalled later. (Configuration files are
              the  files  listed  in the debian/conffiles control file). -P or
              --purge removes everything, including configuration files. If -a
              or  --pending is given instead of a package name, then all pack&#8208;
              ages unpacked, but marked  to  be  removed  or  purged  in  file
              /var/lib/dpkg/status, are removed or purged, respectively.

---

### Post by forestpixie on 2008-01-14
try these first

```
sudo apt-get install -f
```

if that gets nowhere try

```
sudo dpkg --remove --force-remove-reinstreq *mfc6800lpr*
```

check the package name with name of package you have :)

edit - just seen you've tried install -f

try the   --reconfigure -a command below before this one

but I think you'll need to do the resinstreq command - had the same problem with vbox

---

### Post by polmir on 2008-01-14
I am sorry.

---

### Post by polmir on 2008-01-14
This is driver:
[mfc6800lpr-1.1.2-1.i386.deb]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc6800lpr-1.1.2-1.i386.deb&lang=English_lpr")
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")
Are You do it this?
```
 sudo dpkg --reconfigure -a
```

---

### Post by polmir on 2008-01-14
Please, read this
[http://forums.scotsnewsletter.com/lofiversion/index.php/t18027.html]("http://forums.scotsnewsletter.com/lofiversion/index.php/t18027.html")
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-9050]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-9050")

**forestpixie** pardon me.

---

### Post by forestpixie on 2008-01-14
polmir - probably don't need to keep apologising :)

iansane - try

```
sudo dpkg --reconfigure -a

```

before you try the resinstreq command

---

### Post by polmir on 2008-01-14
```
 gedit /var/lib/dpkg/status
```

---

### Post by polmir on 2008-01-14
> sudo dpkg --reconfigure -a
sudo apt-get install -f
This no the same order :)

---

### Post by polmir on 2008-01-14
Try this link

[http://qref.sourceforge.net/Debian/reference/ch-package.en.html#s-info-package]("http://qref.sourceforge.net/Debian/reference/ch-package.en.html#s-info-package")

I hope this helps.

---

### Post by iansane on 2008-01-15
Well thanks you guys for the responses. Now I wish I had waited, but it had been about 12 hours before anyone responded so I backed up and reinstalled. I'll print off these pages cause at some point I'll try to get the print driver installed again and probably have the same problems.

I did try most of those commands but I think I might have not done the reinstreq thing right. It's hard to understand those man pages sometimes but I guess it'll all make sense to me someday.

Thanks a lot! :-)

---

