---
title: "HELP! Partition ownership prob &amp; nw-applet prob!"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-25
I have two problems now and I try to combine them in a thread so that I won't occupy too much resources. The problems are as following:

**[COLOR="Red"]1.[/COLOR]** I have one partition, called /winlin, which is a Fat32 format and can be read by Windows and Xubuntu. However, everytime I copy files from Linux partitions to /winlin, these messages will show up:
```
mv: preserving times for `/winlin/Pictures/blah': Operation not permitted
mv: setting permissions for `/winlin/Pictures/blah': Operation not permitted
```
I searched the forum and change the partition ownership in fstab as
```
UUID=D156-6BD8  /winlin         vfat    defaults,utf8,umask=007,gid=1000 0       1
```
where gid=1000 is my user.
Then, if I check ls -l again, the ownership of /winlin is now like
```
drwxrwx---  10 root cissi  4096 1969-12-31 19:00 winlin
```
Instead of cissi, it was 'plugdev' before.
However, although I modified fstab and restarted my computer, the error message still popped out! In the same way!!! Well... although the message shows, every time the files were still successfully moved even before I modified fstab. It's kinda annoying to see the error message every time, especially when I move a lot of files, it will just print out all the messages for each single file!

[COLOR="Red"]**2.**[/COLOR] It seems there's no way to make the key to wireless router saved in Xubuntu with nm-applet if the key is not the same as the key to login Xubuntu. However, how to turn the error window off? Every time when I boot into Xubuntu, the window will pop out and say:
```
Enter password for default keyring to unlock
```
I have to hit Deny. Then, the wireless window asks me to enter key to wireless, so I do. Then, that keyring window shows again and I have to hit Deny again. It comes again and again. So annoying too.......

Please help me. Any helps will be appreciated. Thanks! :)

---

### Post by incen on 2008-02-25
Did I mess up something? Now, I keep checking with ls -l. However, it seems I just changed the group ownership but not user ownership of /winlin. Should I check it back to gid=46? :confused:

PS. The error message shows up even I used 'sudo' to move files.

---

### Post by incen on 2008-02-26
Please help me!!!  [-o<

I really couldn't make it right. I tried to do chown as this:
```
sudo chown -R cissi winlin/
```

However, it just keeps printing out the error messages:
```
chown: changing ownership of `winlin/Music': Operation not permitted
chown: changing ownership of `winlin/Pictures': Operation not permitted
chown: changing ownership of `winlin/': Operation not permitted

```

What should I do? I just cannot get any idea. I did chown and also modified fstab, but none of them worked. Please~~  [-o<

---

### Post by incen on 2008-02-27
I'm crying out for HELP!!! Could anyone help me with these? At least for the first one? I don't know how to make my user as the owner for /winlin. Did I do something wrong? Thanks in advance!

---

