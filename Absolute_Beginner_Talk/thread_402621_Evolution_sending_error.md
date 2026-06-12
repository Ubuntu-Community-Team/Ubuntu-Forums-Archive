---
title: "Evolution sending error"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-04-06
Does anyone know why Evolution give an error everytime I send mail? The error is Evolution error
Error while performing operation

Failed to append to: Could not parse URL 
Appending to local "Send" folder instead

Ratliff

---

### Post by adam.tropics on 2007-04-06
If I remember correctly, I had similar errors when using IMAP. The problem came because it wasn't able to write to the remote send folder. The solution was to edit the account to use a local send folder instead. It was a while ago though!

---

### Post by bratliff on 2007-04-06
Thanks but I do not have a reomte folder. I'M not sure what constitutes a "remote" folder.

Ratliff

---

### Post by Tufty on 2007-04-20
I have exactly the same problem...

It all works OK and the outbox messages eventually get posted to my sent items folder, but not until after the error message.

does anyone know how to solve this?

Dave

---

### Post by bratliff on 2007-04-20
Go into the configuration and set the outbox location and send folder. The default is left blank during installation for some strange reason.

Ratliff



> **Tufty said:**
> I have exactly the same problem...

It all works OK and the outbox messages eventually get posted to my sent items folder, but not until after the error message.

does anyone know how to solve this?

Dave

---

### Post by Tufty on 2007-04-25
Showing my ignorance here, but how do I find the configuration for "outbox location and send folder"
I've looked through all the settings I can see under 'Edit' then 'Preferences'
I can't find settings for "outbox location and send folder"???

Cheers.
Dave.

---

### Post by bratliff on 2007-04-25
Go to Evolution edit, mail preferences, mail accounts, edit, defaults, set the drafts folder to draft and set the send folder to send.

ratliff


> **Tufty said:**
> Showing my ignorance here, but how do I find the configuration for "outbox location and send folder"
I've looked through all the settings I can see under 'Edit' then 'Preferences'
I can't find settings for "outbox location and send folder"???

Cheers.
Dave.

---

