---
title: "How do you connect to a windows pc?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-08
I have samba installed, and it works great, and i'm able to open up my ubuntu shared folder on my windows laptop.  How do I see my windows pc's shared folders on my ubuntu desktop?

---

### Post by Ramses de Norre on 2006-05-08
In nautilus browse to smb://ip.adres.windows.box.

---

### Post by user1397 on 2006-05-08
I tried that and all I got was:
"The folder contents could not be displayed."
"Sorry, couldn't display all the contents of Windows Network: <IPaddress>."
What do i need to do?

---

### Post by Daremo on 2006-05-08
Do you have Folder / file sharing configured on your Windows PC?

---

### Post by user1397 on 2006-05-08
[quote=Daremo]Do you have Folder / file sharing configured on your Windows PC?[/quote]
Well i thought that Network Places->SharedDocs was the filesharing folder? I didn't do any configuring. what would i need to do?

---

### Post by user1397 on 2006-05-08
Is the configuring stuff in my network places? (Argh, I hate windows...)

---

### Post by Daremo on 2006-05-08
Run the "Network Setup Wizard". It's usually in the Control Panel. This will start basic file sharing. You will probably need a local account on the Windows machine for authentication.


When you are done you should see a "hand" holding the shared folder icon. This represents a shared folder.

---

### Post by user1397 on 2006-05-08
[quote=Daremo]Run the "Network Setup Wizard". It's usually in the Control Panel. This will start basic file sharing. You will probably need a local account on the Windows machine for authentication.


When you are done you should see a "hand" holding the shared folder icon. This represents a shared folder.[/quote]
After I enable it, will I have to do some extra safe-guarding against evil people on the internet so that they don't connect to my pc thru the shared docs?

---

### Post by user1397 on 2006-05-08
[quote=Daremo]You will probably need a local account on the Windows machine for authentication.[/quote]
How do I create this?

---

### Post by Daremo on 2006-05-08
[QUOTE=erik1397]How do I create this?[/QUOTE]
You most likely already have one from the initial Windows install. Open Control Panel and double-click on User Accounts. This should show you all the local accounts on that machine. I mention this because when you try to connect to the Win XP box from ubuntu t may prompt you for a username and password.

---

### Post by user1397 on 2006-05-08
[quote=Daremo]You most likely already have one from the initial Windows install. Open Control Panel and double-click on User Accounts. This should show you all the local accounts on that machine. I mention this because when you try to connect to the Win XP box from ubuntu t may prompt you for a username and password.[/quote]
I don't see any option to create a "local user", just to create a new user, but that's the same as a computer admin, so...

---

