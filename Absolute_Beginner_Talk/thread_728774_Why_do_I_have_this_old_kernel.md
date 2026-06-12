---
title: "Why do I have this old kernel?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-19
The latest kernel available is 2.6.24.3
But here's mine:

```
glade@Muzic-Jukebox:~$ uname -r
2.6.22-14-generic
glade@Muzic-Jukebox:~$ 
```

I am not notified of any kernel updates.. I do have all the repositories checked..
Any comments?

---

### Post by luisromangz on 2008-03-19
You are using Gutsy, so you have the latest estable versions from when Gutsy was feature freezed. In an Ubuntu distro which has been released, you don't usually get new versions of software, but security updates.

---

### Post by sayakb on 2008-03-19
If I download and install the new kernel manually, then will it work. Or should I wait until Hardy is officially out and shows up on my Update manager..

---

### Post by handydan918 on 2008-03-19
> **LinuxIsInnovation said:**
> If I download and install the new kernel manually, then will it work. Or should I wait until Hardy is officially out and shows up on my Update manager..

Better do a little ggogling on "compiling the linux kernel" before you jump off that cliff...

---

### Post by Sef on 2008-03-19
> If I download and install the new kernel manually, then will it work. Or should I wait until Hardy is officially out and shows up on my Update manager..

If you update the kernel, have everything backed up in case you need to reinstall.

Don't do it on production machines unless absolutely necessary, which is rare.

---

### Post by sayakb on 2008-03-19
Any chances of getting broken kernel fixed if I end up with one. I cannot afford to lose my data, and it's a way too much that I could even think of creating a backup for..

---

### Post by sayakb on 2008-03-19
> **Sef said:**
> If you update the kernel, have everything backed up in case you need to reinstall.

Don't do it on production machines unless absolutely necessary, which is rare.

Except for security, what advantage does a new kernel has over the older one. Are there any performance improvements?

---

### Post by luisromangz on 2008-03-19
There are many improvements between kernel versions, but I think that unless you have problems with the version in your current install of Ubuntu you have no real reasons (others than learning or for fun, if you are so inclined) to compile and use a custom made kernel under normal circumstances.

---

### Post by Tews on 2008-03-19
If your data is that important stick with the kernel that you have.  Compiling a different kernel just because its the latest and greatest is inviting trouble!  Hardy Heron will be out in a few weeks so just exercise a little patience :)

---

### Post by Oldsoldier2003 on 2008-03-19
> **LinuxIsInnovation said:**
> Any chances of getting broken kernel fixed if I end up with one. I cannot afford to lose my data, and it's a way too much that I could even think of creating a backup for..
if the new kernel doesn't work out you can just boot to your current stable kernel from grub the remove the new kernel. its very unlikely you will experience data loss, but its always prudent to back up before making any changes to your system.

---

### Post by billgoldberg on 2008-03-19
> **LinuxIsInnovation said:**
> Any chances of getting broken kernel fixed if I end up with one. I cannot afford to lose my data, and it's a way too much that I could even think of creating a backup for..

I just upgrade to hardy heron alpha 6 and am now backing up 270gb of data, because hardy keeps out spitting errors, the gnome panels aren't there, I can't install them, so I have to use the terminal to start all programs.

Backing up sucks.

To answer the question (if it hasn't already) the new kernel will be in hardy heron (is already in the alpha's).

---

### Post by sayakb on 2008-03-19
Yes, I have read that Hardy will have the latest kernel. So I think I would wait for Hardy. Data is my main concern.

---

