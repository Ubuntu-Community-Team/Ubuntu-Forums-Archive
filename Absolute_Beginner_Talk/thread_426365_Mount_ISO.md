---
title: "Mount ISO ?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-04-28
Is there any gui app to mount iso's like Daemon tools ?

---

### Post by Nythain on 2007-04-28
ya dont really need one, but yeah, there's a few apps... i run acetone iso though its a we bit buggy (sometimes it locks up while i try to unmount an iso)

---

### Post by taurus on 2007-04-28
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```

---

### Post by Oki on 2007-04-28
> **mech7 said:**
> Is there any gui app to mount iso's like Daemon tools ?

Yes, there are many programs witch gives you a GUI. One of them are Kiso, you will find it in synaptic:)

---

### Post by Endolith on 2008-04-24
This has a .deb file for installing a script into Nautilus.  I haven't tried it.

[http://mundogeek.net/nautilus-scripts/#nautilus-mount-image](http://mundogeek.net/nautilus-scripts/#nautilus-mount-image)

And this page:

[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

Lists a utility called gISOmount, which is in Synaptic already.  I'm going to try that with my Ubuntu upgrade CD first.

---

### Post by rcatman on 2008-04-24
I've downloaded the alternative ubuntu cd and i want to mount to iso and use it to upgrade from (just like a cdrom). I can mount the iso but I can't get synaptic to see it as a cdrom.

Ive tried the command > sudo synaptic --add-cdrom /media/iso/ and synaptic opens up and seems to scan it but it's never added to the cdrom list. 

Is there anything else I can try?

---

### Post by Tigershell on 2008-04-24
You could use a nautilus script;
You can mount from the right-click menu. 

[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

---

### Post by Endolith on 2008-04-24
> **rcatman said:**
> I've downloaded the alternative ubuntu cd and i want to mount to iso and use it to upgrade from (just like a cdrom). I can mount the iso but I can't get synaptic to see it as a cdrom.

Is there anything else I can try?

Try this:

[http://ubuntuforums.org/showthread.php?p=4784633#post4784633](http://ubuntuforums.org/showthread.php?p=4784633#post4784633)

---

### Post by marcusfurius on 2008-05-14
You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

---

### Post by Hellweek on 2008-05-14
gmountiso is the package I use.

Very easy.

I created to mount points in my media directory
isoa
isob

I then use gmountiso to mount the iso file.

---

