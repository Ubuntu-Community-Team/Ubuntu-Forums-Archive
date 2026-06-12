---
title: "Changing the permissions"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-25
Hey folks . . .I recently converted my NTFS partition into ext3, but I still can't store anything on it . . .how can I change the permissions for that?

---

### Post by taurus on 2006-11-25
```
sudo chmod -R 777 <mount point>
```

---

### Post by CheshireMac on 2006-11-25
Syntax error . . .should I remove the bracket?

---

### Post by taurus on 2006-11-25
> **CheshireMac said:**
> Syntax error . . .should I remove the bracket?

<mount point> stands for your actual mount point!!!  If you mount it to /media/share, then your mount point is /media/share...

```
sudo chmod -R 777 /media/share
```

---

### Post by CheshireMac on 2006-11-25
Wow . . .don't I feel like a tool . . .mine isn't called media . . .that's my CD drives . . .how again do I find out what it is?

---

### Post by nixclusive on 2006-11-25
mount with gid 'plugdev' and umask 0222 for allowing normal users write access.

---

### Post by taurus on 2006-11-25
Paste them here...

```
cat /etc/fstab
df -h
```

---

### Post by CheshireMac on 2006-11-25
Excellent . . .sudo chmod -R 777 /dev/hdb5 sound right to you?
Also, how would I add umask and plugdev to that line? Sorry for sounding dumb, but I'm not used to this Linux language yet. ~LOL~

---

### Post by taurus on 2006-11-25
Actually, "sudo chmod -R 777 /dev/hdb5" is not a good idea since /dev/hdb5 is a device, not your mount point.  You need to know where /dev/hdb5 is mounted to and that where you change the permissions.  Again, if you paste to output of those two commands from above, then I would be able to tell you your mount point for /dev/hdb5.  Otherwise, we are going around in a circle here...

---

### Post by CheshireMac on 2006-11-25
I've been figuring out the problem with a friend as well, and we found that I'm actually looking for hda1, my master drive . . .also, he says that we need to find out how to mount it and make it stay . . .any thoughts on why it wouldn't stay, and how to make it?

---

### Post by taurus on 2006-11-25
If / is on /dev/hda1, then you _[COLOR="Red"]definitely[/COLOR]_ don't want to use "chmod -R 777" to it because you will trash your system that way...  Paste the output of these commands then!!!

```
sudo fdisk -l
cat /etc/fstab
```

---

