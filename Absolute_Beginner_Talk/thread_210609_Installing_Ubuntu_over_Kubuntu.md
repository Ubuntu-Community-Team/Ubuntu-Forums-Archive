---
title: "Installing Ubuntu over Kubuntu?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2006-07-07
Hey all :) 

I had what may sound like kind of an odd question. I was wondering if there was a way to install Ubuntu over my current Kubuntu install, here's the short story:

I'm asking this because at the moment I have Kubuntu "Dapper", AMD64-bit installed at the moment and am dual-booting it with WinXP -- however, two things have come up.

1)Much to my dismay almost all Ubuntu guides are writting for the GNOME enviorment leaving me to try to fill in the blank spots (This is my first dip-in-the-water as far as linux goes, so filling in spots is tricky and a little stressful)

2) Secondly I found through the Wiki that apperantly the 64-bit install isn't as well supported by programs as well as the 32-bit. Case in point, aMSN has an auto-installer for the 32-bit distro, where as I have to deal with binary files for the 64-bit distro.. ack :(

So I've decided to just use GNOME and let my processor emulate 32-bit. Now the only problem is I don't know how to go about telling Ubuntu to just install over the Kubuntu partitions without deleting all the partions and starting over from scratch.

If there's a way, I'd much rather just keep the partitions there and save myself oh so much time lol, instead of deleting the partitions, remaking them, formating, you know the drill =/

---

### Post by crystal on 2006-07-07
You could read [Installing Gnome on Kubuntu](http://psychocats.net/ubuntu/gnome.html). I do not know if it really applies to your case though, but that's what it seems to me.

---

### Post by jordanmthomas on 2006-07-07
If you're not wanting to keep anything from your Ubuntu install, why not just format that partition from the installer and put Ubuntu on it?

Of course, I could be missing just what you're getting at.

You could go through the trouble of installing a 32-bit kernel.  I am not sure what kind of trouble this would cause though as I don't have a 64-bit processor.;)

---

### Post by Nexusx6 on 2006-07-07
> You could read Installing Gnome on Kubuntu. I do not know if it really applies to your case though, but that's what it seems to me.

I'd still have a 64-bit distro under it though, that and I some how messed up my nVida install ](*,) so I figure it's better to just start with a clean slate since I don't have any important files.

> If you're not wanting to keep anything from your Ubuntu install, why not just format that partition from the installer and put Ubuntu on it?

I wish I remembered how my install went more clearly, but doesn't *ubuntu make 2 to 3 partions? 1 for Root, 1 for Swap, and 1 for User(s)? If I just formated and installed on the root, would the new install automatically know about the Swap partion and not try to make another one?

Thanks for your quick reply's :D

---

### Post by crystal on 2006-07-07
> If I just formated and installed on the root, would the new install automatically know about the Swap partion and not try to make another one?
At the partitioning stage it will give you the option of creating new partitions, deleting or formatting existing partitions or leaving them untouched.

---

### Post by jordanmthomas on 2006-07-07
It makes three, but it puts the swap partition on an extended partition so it's really more like two.

The users / home is installed in the /root partition by default.

And yes, it will notice the swap partition there and use it.

---

### Post by Nexusx6 on 2006-07-07
Alright! That's exactly what I was looking for, many thanks! \\:D/

---

### Post by picallo on 2006-07-07
I have a question: If i have also the Ubuntu CD, is it possible to install some gnome application using kubuntu equivalent to "Synaptic"??

---

### Post by jordanmthomas on 2006-07-07
You shouldn't need the Ubuntu CD.  In Adept (I'm assuming this is the package manager you're using) there should be a Gnome apps section.  If not, you just need to enable them in your sources.list

---

### Post by picallo on 2006-07-07
yes, but i have 56k internet, and not yet configure in Kubuntu (HSF  modem). Thats why i asked to install using the ubuntu cd

---

### Post by proahang on 2006-07-07
Simply Use Synaptic Package Manager to install "ubuntu-desktop",after that you will have a complete ubuntu(gnome) desktop.
Or you can run this command :sudo apt-get install ubuntu-desktop.

Good luck!!

---

### Post by jordanmthomas on 2006-07-07
You can add a CD as a repository.  I'm just having a hard time figuring out how.  I found this (for Breezy) and you should be able to add something similar to your sources.list (changing numbers and versions to match your cd of course)
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

---

### Post by picallo on 2006-07-07
Thanks i will wait till somobody post for dapper.

---

