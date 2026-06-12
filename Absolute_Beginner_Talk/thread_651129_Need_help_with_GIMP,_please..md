---
title: "Need help with GIMP, please."
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-27
When I try to, " Save As ",  I get this error message:-

 ' .JPEG image plug-in could not save image '

This just started happening a couple of days ago and I would really appreciate it if someone could explain what causes this.

TIA

---

### Post by L Campbell on 2007-12-27
> **L Campbell said:**
> When I try to, " Save As ",  I get this error message:-

 ' .JPEG image plug-in could not save image '

This just started happening a couple of days ago and I would really appreciate it if someone could explain what causes this.

TIA



Anybody got an idea, here?

---

### Post by Cypher on 2007-12-27
Have you by any chance upgraded GIMP lately? Are you trying to save the file to a directory to which you have no permissions? Show us the output of "df -h"..

---

### Post by L Campbell on 2007-12-27
> **Cypher said:**
> Have you by any chance upgraded GIMP lately? Are you trying to save the file to a directory to which you have no permissions? Show us the output of "df -h"..

Hi, thanks for your interest.

I have not upgraded GIMP.  What I have is 2.4.0~rc3-1ubuntu.

As to, "Are you trying to save the file to a directory to which you have no permissions?"  Heck, I don't know.  :-(

I'm not doing anything differently from what I was doing a few days ago, which was to take the Compact flash card from my camera, insert it in a USB Compact flash card reader and plug it into my 'puter.

From there I would edit the photos with GIMP, 'Save As' with a name, as opposed to a number.  I was able to save the photo to the disk, to my Desktop, to my Home folder, all with no problem. No I can't do that.

Here are the results from Terminal:-

qwer@qwer-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  3.4G   31G  10% /
varrun                379M   84K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   68K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             499M   38M  462M   8% /media/disk
qwer@qwer-desktop:~$ 

Kind regards.

---

### Post by astoltz on 2007-12-27
Try saving as something other than jpeg...

---

### Post by L Campbell on 2007-12-27
> **astoltz said:**
> Try saving as something other than jpeg...

It appears that it will allow me to save the photo as .xcf

When I then try to convert this format to .jpg, it also appears to work.

I did notice that, under Permissions, the file on the disk's 'group' is root but, after I drag the file to my Desktop, the group is 'me'.

---

### Post by astoltz on 2007-12-27
So you can save it as *.xcf, then re-open that file and save it as a jpeg, correct?  That seems weird.  Can you just copy the file(s) from the CF card to your desktop, then open them in gimp and save them as a jpeg again?

---

### Post by xc3RnbFO8P on 2007-12-27
I found this:

This behavior can occur if the JPEG graphics filter is missing or damaged, or if the registry entries for the JPEG graphics filter are missing or damaged.

But this was problem in Picture It.

[http://support.microsoft.com/kb/193354]("http://support.microsoft.com/kb/193354")

---

### Post by L Campbell on 2007-12-27
> **astoltz said:**
> So you can save it as *.xcf, then re-open that file and save it as a jpeg, correct?  That seems weird.  Can you just copy the file(s) from the CF card to your desktop, then open them in gimp and save them as a jpeg again?

Thanks for your interest.

Yes, the files on the CF card are .jpg

I dragged a couple of them onto the Desktop, edited them a little, changed their names and saved them in the .jpg format.

---

