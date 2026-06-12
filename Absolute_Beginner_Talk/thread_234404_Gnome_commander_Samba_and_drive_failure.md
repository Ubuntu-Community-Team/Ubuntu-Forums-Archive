---
title: "Gnome commander Samba and drive failure"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2006-08-11
I am facing two problems with the Gnome commander.

I do not see my DVD/CD drive nor my floppy
There is a Samba icon, it directs me correctly to the networks available but both are considered as text files!

"Text Editor does not know how to open remote files. Do you want to download the file to a temporary location and then open it?"

Any idea?

PS Dapper 64

---

### Post by klytu on 2006-08-11
> **IronArjen said:**
> I am facing two problems with the Gnome commander.

I do not see my DVD/CD drive nor my floppy
There is a Samba icon, it directs me correctly to the networks available but both are considered as text files!

"Text Editor does not know how to open remote files. Do you want to download the file to a temporary location and then open it?"

Any idea?

PS Dapper 64

I don't know why your networks seem to appear as text files. By "Gnome commander" do you mean "Nautilus"? Assuming this is what you mean, try accessing the network from a terminal console. For example, if you have network file "BAR" found on network machine named "FOO" you would do:
```
nautilus smb://FOO/BAR
```
Try this with an actual network directory and file and post what happens if you have difficulty.

Normally your CD/DVD drive will not appear on your desktop anywhere unless you have "mount"ed a disc in the drive.  Same thing for a floppy drive. If you have done a default desktop Ubuntu installation, a CD or DVD that has data on it should mount automatically for you when you insert it into your CD or DVD drive and you will then see it appear on your desktop. You can unmount and eject the CD or DVD by right-clicking its icon and then clicking "eject". 

A floppy you can mount from terminal with:
```
mount /media/floppy
```
assuming your floppy drive is listed this way in /etc/fstab. You could unmount the floppy by right-clicking the floppy icon that appeared and clicking "unmount". Or by typing in a terminal:
```
umount /media/floppy
```
The file /etc/fstab has important information about where various storage devices will mount by default and how they will do this. If you are unsure post the contents of your /etc/fstab/ file by using the command:
```
cat /etc/fstab
```
You can paste the output into your post, it shouldn't be too long. For more info on mount and fstab you can type:
```
man mount
```
and 
```
man fstab
```

Hope this helps.

---

### Post by IronArjen on 2006-08-14
Gnome Commander is the Linux version of the old Norton Commander, which has the advantage of having two panes. The Midnight Commander is also similar but meant for Terminal, Gnome Commander is voor Gnome (obvious).

All the things you mention make me understand the basics better but are meant for another software. I do have a CD mounted but the Gnome Commander still does not see it. Nautilus works perfect.

Thanks for you effort!

---

### Post by klytu on 2006-08-15
> **IronArjen said:**
> Gnome Commander is the Linux version of the old Norton Commander, which has the advantage of having two panes. The Midnight Commander is also similar but meant for Terminal, Gnome Commander is voor Gnome (obvious).

All the things you mention make me understand the basics better but are meant for another software. I do have a CD mounted but the Gnome Commander still does not see it. Nautilus works perfect.

Thanks for you effort!

OK. I learned something new from you - thanks! Gnome Commander is a cool app which makes me reminisce about the old days of DOS. 

I installed it and noted the same behaviour you did when going directly to the text folder that appears when "SMB" is first clicked. I think that in order for gnome commander to accesss a networked share properly, it might have to be mounted locally. When I have time, I'll experiment and post back if it works. Meanwhile you might want to take a look at [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite") and also at [this]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read") and try it out on your own.

I noticed some other buggy behaviour. Every now and then gnome-commander crashes as it tries to access the network - sometimes complaining about invalid UTF-8 encoded text. I'll play around with it and see if I can figure out why.

To access a mounted CD/DVD, navigate with gnome commander to it's mount point as it's listed in /etc/fstab (e.g. /media/cdrom0). You should be able navigate the mounted disk normally. (I could when I tried it.)

---

### Post by IronArjen on 2006-08-15
Great! I was looking for the first link before posting  any thread but couldn't find it, the good thing about Ubuntu is that is has all the support you can imagine, the bad thing is that it sometimes is a jungle.

I also did find my cdrom but directly in root as well as in media/. For the ones that find this thread in a search: it is often also located in /mnt/ which stands for mount. Guess it all depends in the intial setup.

Obviously it still does not appear as in the old Norton Commander (drop down menu) but at least one can use this great tool like indeed in the old MSDOS days.

Isn there a similar trick for SMB? Isn't this "mounted" as well? Couldn't locate it.

I had no crashes with Gnome Commander!

---

### Post by IronArjen on 2006-08-15
Gnome Commander does use Nautilus in the background, maybe that helps!

---

### Post by klytu on 2006-08-16
> **IronArjen said:**
> Isn there a similar trick for SMB? Isn't this "mounted" as well? Couldn't locate it.

I don't think that by default SMB is mounted the way local hard drives and removable media are. (but I could be wrong about this) It appears SMB shares are set up in a "virtual" filesystem. This virtual filesystem can be navigated normally by nautilus and apps designed to understand it, but many apps don't recognize it. For example, if you have mp3s stored on a remote network drive you won't be able to play them with XMMS or Rhythmbox because they only play files mounted locally. But Totem understands the SMB virtual filesystem and will play them. A similar problem occurs with mpeg or video (files located on a network share. If you install samba and smbfs, a network share can be mounted like it's a local filesystem which apps can access via it's mount point. 

After reading your explanation of what gnome commander is, I installed and played around with midnight commander (mc). I hadn't heard of that before reading your post either. I found out midnight commander had no difficulty with SMB shares. You can just start it from a terminal console, hit F9 and enter, hit "B" (create SMB link), enter the machine name for the network share, enter the password (if applicable, otherwise just hit enter when it asks for one) and then you can navigate your network share.

You can navigate mounted CD/DVD disks with MC via their mount point, or through the CDROM symlink in your root directory as you noted.

I noticed a setting in gnome commander that you might be interested in if you haven't found it already. First put a data disk into your CD drive and then unmount it, but leave it in the drive. You would unmount it via:

```
umount /dev/hda
```

(substitute the actual device name of you CD drive for /dev/hda as it's listed in /etc/fstab) I was only able to get this to work by opening gnome-commander as root:

```
gksudo gnome-commander
```

Try navigating to Settings>Options then go to the Devices tab. Click "ADD"
for an alias I typed in CD/DVD Drive, for device I used /dev/hda (you would substitute the appropriate information from your /etc/fstab), and for mount point I chose /media/cdrom0. Close the settings dialogue and you will now notice a CD/DVD Drive button in gnome commander. You can click this and gnome commander will mount your CD and you can then navigate it. You can then click "Unmount: CD/DVD Drive" to unmount it.

The steps in the links I posted earlier in the thread should probably work for you in order to navigate your network shares. It worked on my system. 

> **IronArjen said:**
> I had no crashes with Gnome Commander!


Unfortunately, gnome commander crashes often on my system! I didn't use it all before reading your post and, I apologize, but I didn't want to spend anymore time on it because I don't think I'll be using it much - especially now that I learned about midnight commander. MC works for me just as well with no crashes.

---

