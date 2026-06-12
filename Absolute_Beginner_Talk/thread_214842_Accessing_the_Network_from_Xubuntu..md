---
title: "Accessing the Network from Xubuntu."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by sim085 on 2006-07-13
Hello again,

I have downloaded Xubuntu, and am now using the live version.  I have successfully connected to the internet since it recognized my Ethernet Card authomatically :)

Now I am trying to access another computer that is Windows XP based.  Is this even possible? or I need to install some other sofware first?

Thanks and Regards,
Sim085

---

### Post by Kurt` on 2006-07-13
What do you mean by access? Via network shares?

If you're looking to do any sort of workgroup/domain/shares setup, I recommend installing Samba.

[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)

Samba can be very simple, or very complex. Be sure to read the documentation thoroughly!

---

### Post by sim085 on 2006-07-13
Thanks Kurt :)

I will read the document and see how I can do it ... just another question .. would I still need samba if I wanted to access a shared folder on another computer that also has installed Ubuntu or another Linux?

Best Regards,
Sim085

---

### Post by shoot2kill on 2006-07-13
> **sim085 said:**
> Thanks Kurt :)

I will read the document and see how I can do it ... just another question .. would I still need samba if I wanted to access a shared folder on another computer that also has installed Ubuntu or another Linux?

Best Regards,
Sim085
you wouldnt NEED it, but it can still be used for this purpose

---

### Post by wolfmaniac on 2006-07-13
you have two options to acess linux machins
1. samba
2. NFS
but nfs is bit too complicated (my view)

---

### Post by maniacmusician on 2006-07-13
Also, it has been reported that the cifs method results in quicker transfers than smbfs. I think if you just subtitute every smbfs for cifs, it should work. but then again i havn't read the exact code for a while. there's a [how-to]("http://ubuntuforums.org/showthread.php?t=128873&highlight=cifs") on this.

In addition, be careful that you never try to _write_ any data to your XP computer (assuming that it's NTFS formatted). there are huge problems with writing to ntfs from linux and you will probably end up corrupting your whole drive.  It's fine to copy stuff from XP to linux though.

good luck setting up your network!

---

### Post by sim085 on 2006-07-13
Thanks for all the replies.  I will try to set up samba :)

regarding the corruption if I write files on XP ... by corruption you mean I have to throw away the hard drive and buy another one, or format the computer?

and would I be able to recognize the files on that hard drive from another XP installation?

regards,
sim085

---

### Post by maniacmusician on 2006-07-13
by corruption i mean you would have to format that drive. The data on that computer would probably be lost. by default, Ubuntu doesn't even give you permission to write on a drive thats not in your computer, you have to configure that yourself. But i just spoke it as a warning, just so you'd be aware of it. However, that's only if your partition is NTFS. If you're running XP on a fat32 partition (i'm pretty sure thats possible), it would probably be okay. So just check and make sure which partition you have.

---

### Post by sim085 on 2006-07-13
Thanks :)

I will keep that in mind.

Best Regards and many thanks to all,
Sim085

---

### Post by sim085 on 2006-07-14
I have another question about networks between different operating systems...

Is it possible to connect Ubuntu (or other Linux) to a BSD (like FreeBSD)?

Would I still use Samba? or I would need another tool? or it is impossible?

Regards,
sim085

---

### Post by dmizer on 2006-07-14
> **maniacmusician said:**
> In addition, be careful that you never try to _write_ any data to your XP computer (assuming that it's NTFS formatted). there are huge problems with writing to ntfs from linux and you will probably end up corrupting your whole drive.  It's fine to copy stuff from XP to linux though.
this is not true.

the problem when writing to an ntfs drive is when that ntfs drive is mounted in linux and windows is not booted (as like occurs with a dual boot system).  in the case of a network, the drive is mounted by a running win xp/win2000 os, in which case windows uses it's own drive access to write the files.

in other words: linux cannot safely write directly to an ntfs drive, but there is no problem with writing to an ntfs drive remotely via a network connection.

---

### Post by sim085 on 2006-07-14
thanks dmizer for that extra information on the ntfs topic.  All this is very usefull for me since my aim is to create a network that can hove both Linux, BSD and Windows OS connected to it, without any problems :)

thanks again
sim085

---

### Post by Kurt` on 2006-07-14
The operating system doesn't matter in that case.

When I send a file to a share on another machine, the other machine doesn't care what OS I'm running here. It receives the file and writes it to the disk. When I request a file, the other machine reads it into a buffer and sends it through a socket to me.

The filesystem/operating system in use on the other machine doesn't matter, as long as it is able to join your workgroup/domain correctly.

And yes, Samba will work for your desired network setup. :)

---

### Post by sim085 on 2006-07-15
Thanks Kurt :)

I have still to download a version of BSD, however I got my Ubuntu up and running, and my next step is to install Samba and make it work with Windows :)

Thanks and Regards,
Sim085

---

### Post by dmizer on 2006-07-17
> **sim085 said:**
> my next step is to install Samba and make it work with Windows :)
samba is a linux program used to access windows user shares.

samba is not needed in windows, samba is the linux version of windows file and printer sharing.  so in order to enable windows to view/host shares across your samba network, all you have to do is share a folder and make sure that file and printer sharing is enabled.

i really have no idea how to help you with bsd, you'll probably have more luck at a bsd forum.

---

### Post by sim085 on 2006-07-17
Thanks dmizer, I still did not install samba, but soon going to :)  Thanks for the information :)
 
BSD is not an issue at the moment, will think about that later.  If I do successfully create a network betweem Linux, Windows and BSD I will write a post :)

Thanks and Regards,
sim085

---

