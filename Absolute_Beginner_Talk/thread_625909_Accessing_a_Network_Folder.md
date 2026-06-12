---
title: "Accessing a Network Folder"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-11-28
I have Ubuntu on my Laptop and Windows XP on my desktop.

My laptop has a USB drive connected to it that holds roughly 350gb worth of my data. I need to access the USB drive from my desktop.

Now I shared my USB drive and I installed SAMBA.  However, now when I try to access he USB drive a permission prompt comes up asking for my US/PW.  I type in my username and my password and it just re-asks for it.

I get the Connect to Sethalos-Laptop prompt.

I type in my US (let's say its): Banana and then type in the PW (let's say its): Split 

The prompt just comes back up with: SETHALOS-LAPTOP\BANANA  ,  and the ***** in the pw box, but won't let me connect.

I'm totally lost here, is there something else I need to install or do?

Thanks

---

### Post by Dr Small on 2007-11-28
Did you setup a samba password ?
```
sudo smbpasswd -a *username*
```

Dr Small

---

### Post by Sethalos on 2007-11-28
Err...no I didn't..lol.

Thank you very much, I just assumed it would use the one I had used to login.

---

### Post by jessecollins on 2007-11-28
> **Dr Small said:**
> Did you setup a samba password ?
```
sudo smbpasswd -a *username*
```

Dr Small

Thanks Dr.

I also assumed my login/pass would work automatically.

---

### Post by Dr Small on 2007-11-28
I did too, but remembered I had to do that to get Samba to work properly for my old system, when I was setting it up for my sister. ;)

---

