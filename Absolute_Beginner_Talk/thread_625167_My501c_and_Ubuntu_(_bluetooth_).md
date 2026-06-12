---
title: "My501c and Ubuntu ( bluetooth )"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Lderan on 2007-11-27
I have followed any tutorial and walk through i can find but I can't sync my sagem my501c with my ubuntu 7.04.

My phone can see my computer
My computer can see my phone

But when I try and sync with my phone to the computer, it asks for the key code (i give it) and then it goes into pairing mode and then errors.

What can i do to get it to work, I would like to use phone manager with it so i can text and have my phone by it (its my old phone, my new one lacks bluetooth x,x)

---

### Post by Inxsible on 2007-11-27
what are the errors that you get ?

---

### Post by Lderan on 2007-11-27
I get no errors from

sudo hidd --connect 00:17:E3:2A:AF:EE
There seems to be no erroring on the computer from any of the commands i give it. Its just not connecting to the phone.

My phone gives the error "failed" when i try and sync from it.

I remeber getting the phone to sync with dapper drake, but I have no idea how.

---

### Post by Inxsible on 2007-11-27
you may have to change the authentication```
gksudo gedit /etc/bluetooth/hcid.cong
```Look for a line which says ```
security user;
``` and change it to ```
security auto;
```You can also change the passkey if you like. Save the file and restart X.

---

### Post by Lderan on 2007-11-27
It synced!
:KS
Thankyous

Now to get phone manager working x.x;

---

### Post by Inxsible on 2007-11-27
> **Lderan said:**
> It synced!
:KS
Thankyous

Now to get phone manager working x.x;Sweet !! Glad to help !

---

### Post by Lderan on 2007-11-27
phone manager isn't seeing my phone now >.<
pesky bluetooth

---

### Post by Inxsible on 2007-11-27
what phone manager are you using ?

---

### Post by Lderan on 2007-11-27
gnome-phone-manager I think its called

---

### Post by Inxsible on 2007-11-27
> **Lderan said:**
> gnome-phone-manager I think its calledI don't know much about that app. I never used it. Maybe someone else could better help you with it.

Are you trying to connect to the phone manager via bluetooth?
I generally use Wammu, and it serves my purpose. You might want to check it out.

---

### Post by Lderan on 2007-11-27
Wammu loads up, asks if i want to do a search for my phone then crashes o.O
*goes to reinstall it*

It keeps crashing, It only happens while its searching for my phone. Gah

---

### Post by Lderan on 2007-11-27
I don't think my computer see's my phone o.o

---

