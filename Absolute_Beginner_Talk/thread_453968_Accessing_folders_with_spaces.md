---
title: "Accessing folders with spaces"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Stoodle on 2007-05-25
I'm trying to become more acquainted with the terminal so I can have more control over my computer (and face it, using just the terminal looks positively sexy! ;)).While going around in the terminal, I tried to delete some files from my windows partition (still adjusting). I couldn't do it through the GUI because I don't have permission and I don't know how to do sudo in the GUI. I got to the folder I wanted and tried to cd and ls into it but I can't since it has spaces (Documents and Settings). What do I do?

---

### Post by Ek0nomik on 2007-05-25
Imagine it's Program Files:

```
cd Program\ Files
```

To delete if you need permission:

```
sudo rmdir directory.name
```

If the partition you are trying to delete from is a NTFS drive, you need to install NTFS-3G so you can have write support.

```
sudo aptitude install ntfs-3g
```

I hope it works!

---

### Post by Stoodle on 2007-05-25
Thanks, I think I got it now.

---

### Post by Ek0nomik on 2007-05-25
Excellent.  Good luck.  :)

---

### Post by shen-an-doah on 2007-05-25
For future reference, if you want to delet things via nautilus (your default GUI file manager in gnome), just put this into a terminal:

```
sudo su
```

This logs you in as root, then:

```
nautilus
```

This launches nautilus as root.

---

### Post by Ek0nomik on 2007-05-25
```
gksudo nautilus
```

would be more appropriate.

---

### Post by Stoodle on 2007-05-25
Wait, what if it's a read only? How do I change that?

What's gksudo?

---

### Post by Ek0nomik on 2007-05-25
Are you trying to delete things from your Windows partition?

If so, it's formatted as a NTFS partition, and Linux can only natively Read NTFS partitions.

```
sudo aptitude install ntfs-3g
```

Once you have installed this, you will see you can launch some settings by going to System Tools and you can enable NTFS write support.  (write support will allow you to delete and create files on the drive)

---

### Post by shen-an-doah on 2007-05-25
> **Stoodle said:**
> Wait, what if it's a read only? How do I change that?

What's gksudo?

There's another simple way to enable write support for NTFS, just go to "add/remove programmes" and install the NTFS configuration editor. Then it's just a couple of checkboxes.

gksudo is a graphical frontend for sudo.

If you don't know what a command is, you can use "whatis", e.g:

```
whatis gksudo
```

---

### Post by Ek0nomik on 2007-05-25
> **shen-an-doah said:**
> There's another simple way to enable write support for NTFS, just go to "add/remove programmes" and install the NTFS configuration editor. Then it's just a couple of checkboxes.

gksudo is a graphical frontend for sudo.

If you don't know what a command is, you can use "whatis", e.g:

```
whatis gksudo
```

What's wrong with the terminal?  ;)

---

### Post by shen-an-doah on 2007-05-25
> **Ek0nomik said:**
> What's wrong with the terminal?  ;)

Nowt, just thought I'd give an alternative for anyone who might want the simplicity of a couple of checkboxes ;)

---

### Post by reckless2k2 on 2007-05-25
I thought this was about accessing folders with spaces? 

cd "Documents and Settings"

is what i believe you're looking for.

---

### Post by Stoodle on 2007-05-25
The NTFS file is set to read-write yet it doesn't say that when I try to delete files.

---

### Post by JonnyCMW on 2007-05-27
> **shen-an-doah said:**
> For future reference, if you want to delet things via nautilus (your default GUI file manager in gnome), just put this into a terminal:

```
sudo su
```

This logs you in as root, then:

```
nautilus
```

This launches nautilus as root.

I tried this, and it came up with this:

[I]jonny@jonny-desktop:~$ su
Password: 
root@jonny-desktop:/home/jonny# nautilus

(nautilus:10161): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

Nautilus did come up, in my root folder, so then I navigated to my /media/disk-1/documents and settings , to delete some files, but then I didn't have my awesome root powers anymore, so I couldn't do anything to my files :(

Also, it says that my Disk-1 is read only, is that because I'm not as root, or because its set to read only?

---

### Post by shen-an-doah on 2007-05-27
> **JonnyCMW said:**
> I tried this, and it came up with this:

[I]jonny@jonny-desktop:~$ su
Password: 
root@jonny-desktop:/home/jonny# nautilus

(nautilus:10161): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/I]

Nautilus did come up, in my root folder, so then I navigated to my /media/disk-1/documents and settings , to delete some files, but then I didn't have my awesome root powers anymore, so I couldn't do anything to my files :(

Also, it says that my Disk-1 is read only, is that because I'm not as root, or because its set to read only?

Have you got NTFS writing enabled? You need to either install the NTFS configuration editor from add/remove programmes or do "sudo apt-get install ntfs-3g" like it says earlier in the thread.

---

### Post by JonnyCMW on 2007-05-27
> **shen-an-doah said:**
> Have you got NTFS writing enabled? You need to either install the NTFS configuration editor from add/remove programmes or do "sudo apt-get install ntfs-3g" like it says earlier in the thread.

I've done that, and I followed this guide: [HTML]http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html[/HTML]
but I never got to the window in the 3rd picture on that page :( I typed in my password, then nothing happened.

---

### Post by drs305 on 2007-05-27
Just to recap the original post, Ek)nomik's post answered the question. When typing
```

cd Program\ Files

```
the \ tells linux that there is a space following the last entry and the next one (i.e. between the m and F) and the two are joined (to produce 'Program Files').

Another way is to enclose the entry in quotes (either ' or "):

```

cd "/Program Files"
```

And if it's a long entry, the quotes can enclose the entire string or just the space-separated name:

```
cd drive_c/"Program Files"
```
or
```
cd drive_c/"Program Files"
```

---

### Post by shen-an-doah on 2007-05-27
> **JonnyCMW said:**
> I've done that, and I followed this guide: [HTML]http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html[/HTML]
but I never got to the window in the 3rd picture on that page :( I typed in my password, then nothing happened.

Odd, no idea what's happening there...

---

### Post by JonnyCMW on 2007-05-27
> **shen-an-doah said:**
> Odd, no idea what's happening there...

I've just tried it again, and it worked! :D
Thanks for your help ^-^

---

