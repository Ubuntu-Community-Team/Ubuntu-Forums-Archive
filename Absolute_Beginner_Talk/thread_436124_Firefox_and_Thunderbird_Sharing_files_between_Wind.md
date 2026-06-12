---
title: "Firefox and Thunderbird: Sharing files between Windows and Ubuntu"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Howard Kaikow on 2007-05-07
I currently have a  multiboot Windows 2000 system on which the Thunderbird mailboxes, Firefox Profile, and Thinderbird Profile are shared amongst multiple Windows OS.

Now, I am trying to summon the courage to install Ubuntu 7.04.

I created a small FAT 32 partition and moved  the Thunderbird mailboxes, Firefox Profile, and Thinderbird Profile to the FAT 32 drive. I used Partition Magic to create  ext3 and  Linux swap partions. All other partitions are NTFS.

I had ASSuMED that I could directly share the Thunderbird mailboxes and that I could use symlinks to share some of the files within the respective Thunderbird and Firefox profiles, however, I have at least the following concern.

Since Window and *ix use different delimiters for text files, how can this work?

---

### Post by pizzutz on 2007-05-07
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings)

may help

It does not look like your initial concern should be a problem.  The imports should be able to compensate for the different text file tags.

---

### Post by louieb on 2007-05-07
[Howto: Share Thunderbird & Firefox data between Ubuntu & Windows - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=203524")
or use the foxmarks add in to make you bookmarks accessible from any PC.

---

### Post by codedmin on 2007-05-07
Follow this [http://www.brunolinux.com/05-Configuring_Your_System/Sharing_FF_and_TB_config.html](http://www.brunolinux.com/05-Configuring_Your_System/Sharing_FF_and_TB_config.html)

:)

---

### Post by psyopper on 2007-05-07
[http://www.linuxjournal.com/node/8761/print]("http://www.linuxjournal.com/node/8761/print") is the set of instructions I used. I am doing this very thing as we speak. I am sharing my Firefox and Thunderbird profiles between WindowsXP and Ubuntu Fiesty through an auto-mounting Fat32 partition in Ubuntu.

Works like a charm! If you are new to Ubuntu/Linux know this... files and folders preceded by a . will susually be hidden, in this instance your profiles in your /home/<username> directory where Thunderbird and Firefox are located. If you open up your /home/<username> folder can select View -> Hidden Files to see and access them.

Good luck!

---

### Post by Howard Kaikow on 2007-05-07
> **pizzutz said:**
> [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings)

may help

It does not look like your initial concern should be a problem.  The imports should be able to compensate for the different text file tags.

I saw that article, but have not yet read it.
I'm not talking about importing, rather I need to share the files.
The files would liveon theFAT32 drive and be shared by Thunderbird/Firefox in both OS.

---

### Post by Howard Kaikow on 2007-05-07
> **louieb said:**
> [Howto: Share Thunderbird & Firefox data between Ubuntu & Windows - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=203524")
or use the foxmarks add in to make you bookmarks accessible from any PC.

Thanx.
I'll take a look.

---

### Post by Howard Kaikow on 2007-05-07
> **psyopper said:**
> [http://www.linuxjournal.com/node/8761/print]("http://www.linuxjournal.com/node/8761/print") is the set of instructions I used. I am doing this very thing as we speak. I am sharing my Firefox and Thunderbird profiles between WindowsXP and Ubuntu Fiesty through an auto-mounting Fat32 partition in Ubuntu.

Works like a charm! If you are new to Ubuntu/Linux know this... files and folders preceded by a . will susually be hidden, in this instance your profiles in your /home/<username> directory where Thunderbird and Firefox are located. If you open up your /home/<username> folder can select View -> Hidden Files to see and access them.

Good luck!

Thanx, I'll take a look.

---

### Post by Howard Kaikow on 2007-05-08
> **psyopper said:**
> [http://www.linuxjournal.com/node/8761/print]("http://www.linuxjournal.com/node/8761/print") is the set of instructions I used. I am doing this very thing as we speak. I am sharing my Firefox and Thunderbird profiles between WindowsXP and Ubuntu Fiesty through an auto-mounting Fat32 partition in Ubuntu.

Works like a charm! If you are new to Ubuntu/Linux know this... files and folders preceded by a . will susually be hidden, in this instance your profiles in your /home/<username> directory where Thunderbird and Firefox are located. If you open up your /home/<username> folder can select View -> Hidden Files to see and access them.

Good luck!

I do not understand how those instructions can work:

1. It is necessary to have a separate profile for Linux and for Windows, at least because:
      a.  there are paths encoded within the files within each profile;
      b.  different extensions may be used;
      c.  Windows uses CRLF at end of record, Linux does not.

2. Sharing of files such as Thunderbird mailboxes, address book, dictionary, and Firefox cookies, bookmarks, host permissions seem to also face the different end of record used by Linux and Windows.

---

### Post by jiminycricket on 2007-05-08
Why not ntfs-3g / ntfs-config instead of fat32?  For firefox, try [Google Browser Sync]("http://www.google.com/tools/firefox/browsersync/").

[Another ]("http://www.geektimelinux.com/index.php?q=node/view/362")howto for Firefox that can maybe be adapted to Thunderbird

---

### Post by Howard Kaikow on 2007-05-08
> **jiminycricket said:**
> 
[Another ]("http://www.geektimelinux.com/index.php?q=node/view/362")howto for Firefox that can maybe be adapted to Thunderbird

Does not address the issues I raised.

---

### Post by louieb on 2007-05-08
It works,  but I give your questions a shot.
> **Howard Kaikow said:**
> 
      a.  there are paths encoded within the files within each profile;       b.  different extensions may be used;
One profile one path, one extension.
> **Howard Kaikow said:**
> 
      c.  Windows uses CRLF at end of record, Linux does not.

CRLF or just CR is treated as white space. (ie.. tab, space, CR,LF) Easy enough for a program to tell if its dealing with a Linux or windows text file and act accordingly. (Try NoteTab it even tells you which format the file uses. Windows notepad doesn't, go figure).     
> **Howard Kaikow said:**
> 
2. Sharing of files such as Thunderbird mailboxes, address book, dictionary, and Firefox cookies, bookmarks, host permissions ...[LIST]
[*]fat32 does not support file ownership or access permissions,
[*]NTFS and ext3 Windows ignores permissions and ownership in ext3 files.
[*]Linux same for NTFS files.[/LIST]

---

### Post by Howard Kaikow on 2007-05-08
> **louieb said:**
> It works,  but I give your questions a shot.

One profile one path, one extension.

1. D:\whatever is not recognized by linux.
    ~\whatever is not recognized by Windows.

2. an extension may be used in windows, say, FlashGot, that is not used in linux, or vice versa.

> **louieb said:**
> CRLF or just CR is treated as white space. (ie.. tab, space, CR,LF) Easy enough for a program to tell if its dealing with a Linux or windows text file and act accordingly. (Try NoteTab it even tells you which format the file uses. Windows notepad doesn't, go figure).

I agree that this can be handled internally by the program, but it gets messy if some records are terminated by CRLF and others are terminated by LF in the same file.     

> **louieb said:**
> [*]fat32 does not support file ownership or access permissions,
[*]NTFS and ext3 Windows ignores permissions and ownership in ext3 files.
[*]Linux same for NTFS files.[/LIST]

I'm not talking about file permissions, rather the hostperm.1 file.

Also, printers are defined differently in each profile.

---

