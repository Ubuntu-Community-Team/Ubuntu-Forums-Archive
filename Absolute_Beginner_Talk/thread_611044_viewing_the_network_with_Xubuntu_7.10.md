---
title: "viewing the network with Xubuntu 7.10?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by NavyRSt on 2007-11-12
I'm sure this is written down tons of times, but I'm not too savvy on the lingo just yet.

When I first installed FF on the desktop I was able to see my laptop on the network with just a few clicks of the mouse and even run files off of the share folder.

Now, I know NOTHING of samba, and I don't think that I had it running (or even installed) when I was running FF.

But, now that I am running GG Xubuntu, I can't find crap.

Please help,
Brett

---

### Post by reckless2k2 on 2007-11-12
yeah this is a random thing that happens to me and i'm not entirely sure why. i've heard it's because of the setup in the host file and such. an "easy" fix is to install smb4k. some people suggest that. it requires a sudo start unless you monkey with the command line to change the permissions. 

you can try it out.

---

### Post by NavyRSt on 2007-11-12
Awesome, thanks!

---

### Post by reckless2k2 on 2007-11-12
yeah after you install smb4k you have to do this from the terminal to ensure that you can run smb4k as a normal user:

```
sudo chmod u+s /usr/bin/smbmount 

```

```
sudo chmod u+s /usr/bin/smbumount

```

now you'll be able to mount and unmount as a normal user in smb4k. it'll do the network discovery as well.

---

