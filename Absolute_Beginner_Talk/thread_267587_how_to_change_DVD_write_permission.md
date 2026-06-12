---
title: "how to change DVD write permission"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by sanjito on 2006-09-28
I would like to be able to use my DVD burner as it was intended, but for whatever reason I do not have permission to do so. How can I change this so I can write too DVD? Have included a screenshot so you can see what I am taking about. Thanks for the help.

---

### Post by uk_sphinx on 2006-09-28
type gksudo nautilus
type password

in the nautilus window click computer near top

right click your cdrw drive
go to properties
mark the permissions to write for your user name

---

### Post by uk_sphinx on 2006-09-28
im a noob myself but that should work
someone correct me if im wrong

also if it is right please pass this on to other members requesting the same help if you spot anyone and help the community

---

### Post by sanjito on 2006-09-29
> **uk_sphinx said:**
> type gksudo nautilus
type password

in the nautilus window click computer near top

right click your cdrw drive
go to properties
mark the permissions to write for your user name

I was able to get to the cdrw drive properties, but got the following error

[COLOR="Red"]The permissions could not be changed.
Sorry, couldn't change the permissions of "CD/DVD Creator"[/COLOR]

and when I did the gksudo nautilus I got this error.

[COLOR="Red"]sanjito@sanjito:~$ gksudo nautilus

(nautilus:5893): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

** (nautilus:5893): WARNING **: Hit unhandled case 25 (Is a directory) in fm_rep ort_error_setting_permissions

** (nautilus:5893): WARNING **: Hit unhandled case 25 (Is a directory) in fm_rep ort_error_setting_permissions

** (nautilus:5893): WARNING **: Hit unhandled case 25 (Is a directory) in fm_rep ort_error_setting_permissions
sanjito@sanjito:~$[/COLOR]

Thanks for the info though. Any other solutions??

---

### Post by pseudonym on 2006-09-29
As user, you are temporarily granted write priviliges during the burn process. This is how cdrecord and dvd+rw-tools (the linux burning backend programs) are configured. You don't need to change the permissions on any drives/folders or anything. In fact, it's recommended not to.

Have you tried to burn a CD/DVD, and got errors? Or just not tried yet?

---

### Post by sanjito on 2006-09-29
> **pseudonym said:**
> Or just not tried yet?
I honestly did not try yet. I was looking at the permissions when I first installed ubuntu of the disks and noticed that. Kind of made me concerned that I would not be albe to write when I saw that.

> **pseudonym said:**
> Have you tried to burn a CD/DVD, and got errors? Yes I did try to burn an audio cd and got an the following error.
[COLOR="Red"]Unable to handle the following files due to an unsupported format:[/COLOR]
I know this is a seperate question, but how do I change formats? I am trying to k3b.

---

### Post by pseudonym on 2006-09-29
> **sanjito said:**
> Yes I did try to burn an audio cd and got an the following error.
[COLOR="Red"]Unable to handle the following files due to an unsupported format:[/COLOR]
I know this is a seperate question, but how do I change formats? I am trying to k3b. I don't use k3b but have you set up your system properly for multimedia yet? As you may know, Ubuntu doesn't come with support for non-free formats like mp3 'out of the box'. You need to download plugins and codecs before any of that will work. The 'official' howto on doing that is [here]("https://help.ubuntu.com/community/RestrictedFormats"). For ease of use, the section 'Automated Installation' may be especially beneficial to you.

Also, make sure to change the permissions back on your DVD burner if you haven't already :)

---

### Post by sanjito on 2006-09-29
is easyubuntu the same as running automatix? And in automatix, i thought there was something about not installing the non-free formats if you lived in the US. Anyways, I did install the soundconverter, and that worked great. I can know burn audio. The files play fine in xxms as mp3's. And , i was never able to change permissions. Thanks for all your help pseudonym.

---

### Post by pseudonym on 2006-09-29
> **sanjito said:**
> is easyubuntu the same as running automatix?  Essentially, yes. But Easy Ubuntu is supposed to be a little easier to use for beginners.

> **sanjito said:**
> And in automatix, i thought there was something about not installing the non-free formats if you lived in the US. In theory there are issues with patents, which is why this functionality doesn't ship with Ubuntu. The official Ubuntu position appears to be - 

Legal Notice: Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 

> **sanjito said:**
> Thanks for all your help pseudonym.You are welcome.

---

