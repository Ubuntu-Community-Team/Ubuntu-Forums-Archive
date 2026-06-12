---
title: "important documents at risk, please help."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by emmet2125 on 2007-01-18
my dell crashed the other day so i booted ubuntu 6.06 from the CD

here i am now running it.

but

i failed to back up my documents.

i would have before, just that this computer is under two months old!

i need to recover these documents.

do i need to install ubuntu to acsess my HDD?

because at the moment i get this error up, "Unable to mount the selected volume." and "error: device /dev/sda2 is not removable

error: could not execute pmount"

this is probs. the dumbest thing ever. i just need help.

thanks.

---

### Post by davebgimp on 2007-01-18
Is this an Ubuntu partition you're trying to get documents off of?

---

### Post by bodhi.zazen on 2007-01-18
What partition are you trying to access ? I assume /dev/hda1

In a terminal:

```
sudo mount /dev/hda1 /mnt
```

Should give you ro access to the partition.

Access with:```
gksudo nautilus
```

navigate to /mnt

Drag and drop the documents you need 8)

---

### Post by emmet2125 on 2007-01-18
sorry guys,

i am a true newbie

these documents were saved in windows

is that what you mean?

---

### Post by davebgimp on 2007-01-18
> **emmet2125 said:**
> sorry guys,

i am a true newbie

these documents were saved in windows

is that what you mean?

Yep, that's what I was asking.

copy the text at this link:
[http://www.smorgasbord.net/files/winmac_fstab](http://www.smorgasbord.net/files/winmac_fstab)

save it to a text file named winmac_fstab in the home directory for your live cd. Open a terminal and type:

**chmod 755 winmac_fstab**

Next type:
**./winmac_fstab**

That should mount the Windows partition as read-only. From there, get your files. Put them on  thumb drive, CD, upload them...whatever you need to do.

---

### Post by emmet2125 on 2007-01-18
uh...

"You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

:S

---

### Post by davebgimp on 2007-01-18
> **emmet2125 said:**
> uh...

"You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

:S

you are trying to save this to the default home?
Try creating a blank text document and pasting the script into it.

---

### Post by emmet2125 on 2007-01-18
i'm so sorry

i have no idea what is going on

i great at WINXP

but

this,

this is a long way from home.

:)

---

### Post by annda on 2007-01-18
emmet, you double posted so it's not easy to follow the solutions.

i made a suggestion in your other thread - i can't guarantee it will work for everyone on every computer but you might try it out. despite the use of terminal it is pretty easy and if something goes wrong you can post the error messages.

good luck again!

---

