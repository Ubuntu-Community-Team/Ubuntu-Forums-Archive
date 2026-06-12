---
title: "Opera Bookmarks"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-05-27
Is there a way I can copy my Opera bookmarks from my Windows version of Opera to my Linux version?
If so, how?  (Keep explanations simple, please, as i'm a noob)
Thanks!

---

### Post by aysiu on 2006-05-27
Doesn't Opera have an export bookmarks function?

---

### Post by papangul on 2006-05-27
When you try to either save or export the bookmarks from manage bookmarks option in the menubar, you will be prompted to save a 'opera6.adr' file anywhere in your computer. Save the 'opera6.adr' file in the '.opera' folder in your home directory in linux. 
Since '.opera' is a hidden folder you have to enable 'view hidden files' options in nautilus.

---

### Post by rodrigo666 on 2006-05-27
Altough I am a noob in Ubuntu and Linux as you, I think I can help since I am an Opera entusiast.

First thing you have to do is go to your Opera in Windows, select File> Import and Export> Export Opera Bookmarks.

The a save box will appear, save the bookmarks file in a directory you can open latter in Ubuntu. It will be a opera6.adr file If I'm not mistaken.

Switch to Ubuntu, open your Opera and go File> Import and Export> Import Opera Bookmarks.

A open box will appear, find your opera6.adr (the file you saved when exported with Windows) and voilá! Yours Windows Opera bookmarks will appear in your Ubuntu Opera.

It's normal to need a few bookmarks managements, but it's not a big deal. (The imported bookmarks can appear in a "Opera Bookmarks" directory inside your Bookmarks, all you will have to do is Manage Bookmarks (Ctrl+Alt+B), find that directory, select all files inside it and move outside it).

I hope you gotta it.

---

### Post by JGKC9AYC on 2006-05-27
I'm dual-booting w/XP & Ubuntu.
When I boot back into XP, any suggestions where I can save that file so that I can find it when I boot back into Ubuntu?
I've looked through the file system in Ubuntu, but couldn't find any Windows files/folders.
Thanks for the quick replies...I think that's one of the things I like about Ubuntu is the great support!  :)

---

### Post by rodrigo666 on 2006-05-27
Well, I see that you don't know yet how to mount and unmout the Windows Hard Disks. That would be subject for another threat. It's very easy to find and I recommend you to read it.

Sorry for not posting it's link right now, but it's 3:00 o'clock am here at Brazil and I really got to go to bed.

But I do have a easy solution for you. Since you seem to have your internet conection working well in Ubuntu, all you have to do is eMail the bookmark file to yourself and then download it in Ubuntu.

That's not the pro way, but it's a easy way :cool: .

---

### Post by JGKC9AYC on 2006-05-27
I guess since we're talking about accessing XP files, if I wish to listen to MP3's, i'll need to "mount" also, yes?
Since my MP3's are stored on a separate hard drive, would that be "HDB" (since my dual-boot hard drive is HDA?)?
Thanks again.

---

### Post by rodrigo666 on 2006-05-27
Yes, you will have do mount your Windows HD's to be able to listen to your mp3 in Ubuntu.

There's two ways to do that:

1) You do mount your Hard Disks in Ubuntu for just that session;
2) You do mount your Hard Disks to be always mounted up in every boot.

I preffer the second way and I presume you agree with me.

I must warn you that if the Windows partitions you have are formated in a NTFS mode, you will not be able to write on it by Ubuntu (as a matter of fact, there's some ways to do that, but since I'm a newby, I could not configure that right and can't teach you how do to that).

So, first thing you have to do is find out what Hard Disks you have and it's names on Ubuntu. To do that you must go System> Administration> Disks

It will open the DIsks Manager program, go to the partigions abe and select the partions you want to mount in Ubuntu and note down it's correlative "name" in Ubuntu system.

Like, my Windows C:/ is /dev/hda1/ and my Windows D:/ (where I keep my mp3) are /dev/hda3/

Note down all the Windows partitions and proceed to next step.

2° step: Now you will have to create a directory where each of your Windows partitions will be mounted, so open your terminal and type something like that:

mkdir /media/partitionname

Where partitionname is like windowsc for the Hard Disk C:/ of your Windows. Create a directory to each one of your Hard Disks withe the command above.

Now, I assume that your partitions are formated in NTFS mode and you understood that you will not be able to write on it when using Ubuntu (unless you try some of the "hacks" I mentioned early).

In your terminal type:

sudo cp /etc/fstab /etc/fstab_backup

This will make a backup of your file, so you can recover it if something goes wrong. Then type:

sudo gedit /etc/fstab

It will open a file that controls your mounted units, there you will add a line like this:

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Add a line like that for each one of the Hard Disks you want to mount every time you start up your Ubuntu. Notice to change the "hda1" in "/dev/hda1" and the "windows" in "/media/windows" to it's corresponding created in step one.

Mine is like this:

/dev/hda1       /media/windowsC  ntfs         nls=utf8,umask=0222         0       0
/dev/hda5       /media/windowsD  ntfs         nls=utf8,umask=0222         0       0
/dev/hda6       /media/windowsE  ntfs         nls=utf8,umask=0222         0       0
/dev/hda7       /media/windowsF  ntfs         nls=utf8,umask=0222         0       0

Now, save the file and here goes a little trick, type "sudo mount -a" in terminal to avoid rebooting the system and voilá, your Windows Hard Disks will appear in your Nautilus.

I hope you got that right, cheers.

---

### Post by JGKC9AYC on 2006-05-27
When I opened "Disks Manager" & looked at the Windows partition on my C & D drives, I noticed in the "Partitions" tab there was a button labeled "Enable" next to "Status".
If I clicked "Enabled", would that do the same thing or am I going to have to do it the hard way?  ;)
Thanks!

---

### Post by rodrigo666 on 2006-05-27
As a matter of fact, the way I told you to find out the partitinons using the "Disk Manager" is not the "pro" way, but I believe it will work.

The rest of the tutorial is right, don't worry.

So, answering your question, I don't believe that click on enable will do the work, you will have do the hard way. But don't worry, soon you will start to like that.

---

### Post by JGKC9AYC on 2006-05-28
I heard that Dapper would automatically mount that for me...is that true?

---

### Post by rodrigo666 on 2006-05-28
I can't tell you that because I upgrade a few hours ago to Dapper but it detected my previous settings. So I don't know if the Windows Partitions are mounted because Dapper or because my previous settings.

But I strongly advice you to mount yourself as I said because if you want to migrate to a Linux system like Ubuntu, it's a good thing to yourself getting used to some simple terminal commands.

I never used any Linux System before this week!

---

### Post by virtuelvis on 2006-05-29
Regarding moving your Opera data from XP to Dapper. Since the format of the files is the same on any OS, it is pretty much a matter of just copying the relevant files from your Opera profile folder to ~/.opera (usually from C:\Documents and Settings\Username\Application Data\Opera)

The braver ones can just try copying the entire folder, and then edit any paths in the various ini files so they match your actual installation directory.

---

### Post by JGKC9AYC on 2006-06-04
[QUOTE=rodrigo666]
Add a line like that for each one of the Hard Disks you want to mount every time you start up your Ubuntu. Notice to change the "hda1" in "/dev/hda1" and the "windows" in "/media/windows" to it's corresponding created in step one.

Mine is like this:

/dev/hda1       /media/windowsC  ntfs         nls=utf8,umask=0222         0       0
/dev/hda5       /media/windowsD  ntfs         nls=utf8,umask=0222         0       0
/dev/hda6       /media/windowsE  ntfs         nls=utf8,umask=0222         0       0
/dev/hda7       /media/windowsF  ntfs         nls=utf8,umask=0222         0       0

Now, save the file and here goes a little trick, type "sudo mount -a" in terminal to avoid rebooting the system and voilá, your Windows Hard Disks will appear in your Nautilus.

I hope you got that right, cheers.[/QUOTE]

Here's what happened after I typed "sudo mount -a" in terminal:

[I]mount: /dev/hda1 already mounted or /media/windowsc busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1
mount: /dev/hdb1 already mounted or /media/windowsd busy
mount: according to mtab, /dev/hdb1 is mounted on /tmp/disks-conf-hdb1
[/I]

---

