---
title: "Samba: cannot write on NTFS share?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by siorai on 2005-12-03
Right now I have XP Pro installed in VMWare Player. I've setup my samba shares and can access them no problem through VMWare. My problem is that I'm not able to write to the disc at all. My shares look like this in my smb.conf:

```
[storage]
path = /media/storage
available = yes
browseable = yes
public = yes
writable = yes
```

I went through the FAQ guide and made the changes for the Public folder and restarted samba. I also restarted XP, but I still get denied access to writing to the NTFS shares. The VFAT share is fine though. Is this actually normal? I would have thought I should be able to write to the NTFS shares through XP.

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=siorai]Right now I have XP Pro installed in VMWare Player. I've setup my samba shares and can access them no problem through VMWare. My problem is that I'm not able to write to the disc at all. My shares look like this in my smb.conf:

```
[storage]
path = /media/storage
available = yes
browseable = yes
public = yes
writable = yes
```

I went through the FAQ guide and made the changes for the Public folder and restarted samba. I also restarted XP, but I still get denied access to writing to the NTFS shares. The VFAT share is fine though. Is this actually normal? I would have thought I should be able to write to the NTFS shares through XP.[/QUOTE]

Not sure I understand you exactly.  If your Ubuntu machine is acting as the server running samba, the file shares are using the SMB protocol, but the underlying filesystem is *not* NTFS.  That would only be the case if your Windows machine is the server.  

So are you saying you have a Windows server and your Ubuntu client has problems writing to it, or do you have an Ubuntu server and your Windows client has problems writing to it?

---

### Post by manicka on 2005-12-03
It is normal to not be able to write to ntfs shares.

---

### Post by siorai on 2005-12-03
[QUOTE=cwaldbieser]Not sure I understand you exactly.  If your Ubuntu machine is acting as the server running samba, the file shares are using the SMB protocol, but the underlying filesystem is *not* NTFS.  That would only be the case if your Windows machine is the server.  

So are you saying you have a Windows server and your Ubuntu client has problems writing to it, or do you have an Ubuntu server and your Windows client has problems writing to it?[/QUOTE]

Sorry, I should have been more specific. I have one box with Ubuntu as the OS. I have VMWare installed on it, with XP Pro running as a virtual machine. In Ubuntu I have a couple NTFS partitions that I am sharing through samba. I'm trying to write to those NTFS shares with XP Pro through samba.



[QUOTE=manicka]It is normal to not be able to write to ntfs shares.[/QUOTE]

Hmm... So even with the XP Pro running in VMWare I can't write to those NTFS shares? That's disappointing, but oh well. Just means I work out my partition scheme differently then.

---

### Post by manicka on 2005-12-03
[QUOTE=siorai]
Hmm... So even with the XP Pro running in VMWare I can't write to those NTFS shares? That's disappointing, but oh well. Just means I work out my partition scheme differently then.[/QUOTE]

I ended up just leaving my main xp partition as ntfs and use fat32 for the other data partitions. Every now and then I erase one and replace it with ext3 and if it weren't for the rest of my family the others would go as well.

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=siorai]Sorry, I should have been more specific. I have one box with Ubuntu as the OS. I have VMWare installed on it, with XP Pro running as a virtual machine. In Ubuntu I have a couple NTFS partitions that I am sharing through samba. I'm trying to write to those NTFS shares with XP Pro through samba.[/QUOTE]
Well, I am not exactly sure I get what is going on since I haven't actually ever used VMWare (though I think I get the concept).  If there are NTFS partitions on your machine, WinXP should be able to read/write to them without having to use file sharing.  It should be able to read and write from the partitions directly.

What really is weird to me is that if the share is set up with Ubuntu as the server, the filesystem should have to be ext3 or fat32 or something that Ubuntu can actually write to.

I may have this totally wrong, but I think about it like this:

When a client wants to read or write to a file share, it contacts the server using the SMB protocol and sends the appropriate commands to it, like "rename this file" or "delete this file" or  "create this file" or "read this file".  The server then has to carry out those commands for the client.  In this case, since Ubuntu is the server, there doesn't seem to be a way for it to write to an NTFS partition.

Now if you flipped things around and made WinXP the server, then Ubuntu as a client could manipulate files on the share, because WinXP would receive the SMB requests and do the actual writing.

---

### Post by manicka on 2005-12-04
[QUOTE=cwaldbieser]
When a client wants to read or write to a file share, it contacts the server using the SMB protocol and sends the appropriate commands to it, like "rename this file" or "delete this file" or  "create this file" or "read this file".  The server then has to carry out those commands for the client.  In this case, since Ubuntu is the server, there doesn't seem to be a way for it to write to an NTFS partition.

Now if you flipped things around and made WinXP the server, then Ubuntu as a client could manipulate files on the share, because WinXP would receive the SMB requests and do the actual writing.[/QUOTE]

A thorough explanation :)

---

### Post by siorai on 2005-12-04
[QUOTE=cwaldbieser]When a client wants to read or write to a file share, it contacts the server using the SMB protocol and sends the appropriate commands to it, like "rename this file" or "delete this file" or  "create this file" or "read this file".  The server then has to carry out those commands for the client.  In this case, since Ubuntu is the server, there doesn't seem to be a way for it to write to an NTFS partition.[/QUOTE]

That's exactly how it was working out, but I figured that XP would be able to write to the NTFS partitions because well.. they're NTFS. That's how my non-server knowledgable brain figured the logic would go at least. As you know, that's completely wrong. So I have now converted the NTFS partitions to ext3 like the rest of my Ubuntu install and it works perfectly. In fact this is 100000% better since I can write to the partition no matter what I'm using. Thanks for the explanation. That makes it very clear.

---

