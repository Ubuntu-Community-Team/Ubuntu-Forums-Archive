---
title: "VMware Server FRUSTRATIONS!!"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-06-11
Hi, I am trying to install winxp in a Vmware server so I can sync my Zune without having to reboot everytime. However, i did something in the install that caused it to close when asking for a serial key. And now when I try to install it, it says a previous installation has been found, please remove. I tried to sudo apt-get remove -- purge it, i even tried with aptitude. But it stills gives me the error. BTW I installed it first through AutomatiX 2, and then I tried uninstalling it, but it still comes back.

---

### Post by zvacet on 2007-06-11
```
whereis vmware server
```

After that go to the every directory with vmware file and remove it manualy

```
sudo rm -r file_name
```


file_name =exact name of vmware file in directory

---

### Post by luchardi on 2007-06-11
Try to run

*sudo apt-get remove vmware**

If this comand does't work, try to do:

*sudo apt-cache vmware**

and then 

*sudo apt-get remove (the output of previous command) ...*

---

### Post by Nekiruhs on 2007-06-11
I tried those, and it didn't help. But I googled this and it told me to run sudo dpkg --configure -a. I am trying that now to see if it installs

---

### Post by Nekiruhs on 2007-06-11
All right, it worked! But now I must get internet working, and sound working. So far on the internet thing, I have tried Bridged and NAT. I am behind a router w/ Comcast. Also, If anyone can point me to a tutorial to sharing a folder (~/My Music) between Ubuntu and my VM, I'd give them much thanks. Maybe even a cookie!
EDIT: Internet worked on vmnet0 but stilll no sound. And can anyone explain to me how to make a Zune show up in VMware?

---

### Post by Nekiruhs on 2007-06-11
sudo bump

---

### Post by veloce on 2007-06-14
> **Nekiruhs said:**
> All right, it worked! But now I must get internet working, and sound working. So far on the internet thing, I have tried Bridged and NAT. I am behind a router w/ Comcast. Also, If anyone can point me to a tutorial to sharing a folder (~/My Music) between Ubuntu and my VM, I'd give them much thanks. Maybe even a cookie!
EDIT: Internet worked on vmnet0 but stilll no sound. And can anyone explain to me how to make a Zune show up in VMware?

How far have you got?  Have you set up a virtual sound card on the vm?  How is that configured?

---

### Post by BHelts on 2007-06-14
first off let me say that i'm not trying to hijack this thread.  i saw a minute ago there was a reply to a post a day ago, so i figure i can try.....
i just set up vmware-server and am running server2003 enterprise.  everythings working except sound.  i'm interested in the "Virtual Sound Card" the previous poster wrote about.  Any idea how to get that working.

again, i'm sorry if this isn't my thread.

---

### Post by veloce on 2007-06-14
> **BHelts said:**
> first off let me say that i'm not trying to hijack this thread.  i saw a minute ago there was a reply to a post a day ago, so i figure i can try.....
i just set up vmware-server and am running server2003 enterprise.  everythings working except sound.  i'm interested in the "Virtual Sound Card" the previous poster wrote about.  Any idea how to get that working.

again, i'm sorry if this isn't my thread.

Have you added it to the "hardware" of the virtual machine?

---

### Post by BHelts on 2007-06-14
no i have not..... obviously there is a way to do that, but i'd be ecstatic if you let me in on the secret.

---

