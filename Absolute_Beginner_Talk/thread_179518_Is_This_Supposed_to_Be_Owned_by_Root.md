---
title: "Is This Supposed to Be Owned by Root???"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-20
is the windows network under places->network servers supposed to be owned by root?
maybe this is the reason why i don't see any of my windows computers in there?

---

### Post by juicybananahead on 2006-05-20
[QUOTE=erik1397]is the windows network under places->network servers supposed to be owned by root?
maybe this is the reason why i don't see any of my windows computers in there?[/QUOTE]
You shouldn't need root access to get onto your windows computers' shared drives. Can you ping your Windows computers? If so, let me guess... nothing's showing up when you try to browse around Places->Network Servers? Try connecting to them using Places->Conect to Server, using Windows Share as the Service type and one of your Windows computers' ip addresses in the Server field. This should verify whether you are able to connect to them at all. 

As for them not showing up, I think it might have to do with firewalling on your Windows pc's (UDP ports 137 and 138 might be closed), but I can't be too sure. Any SMB experts out there want to comment? ;)

// dave

---

### Post by user1397 on 2006-05-20
what would i need to type in the terminal to make it owned by me?
would it be something like:
```
sudo chmod+x network:///
```???

---

### Post by user1397 on 2006-05-20
bump! :D

---

### Post by argie on 2006-05-20
Not sure if this'll help, but I perhaps you should try doing:
[b]
gksudo nautilus
Go>Location...
network:///
Properties>Permissions
[/b]

---

### Post by user1397 on 2006-05-20
[quote=argie]Not sure if this'll help, but I perhaps you should try doing:
[B]
gksudo nautilus
Go>Location...
network:///
Properties>Permissions
[/B][/quote]
i've already tried that, but i can't change the permissions from within sudo nautilus

---

### Post by juicybananahead on 2006-05-20
Hi Erik,

I'm a bit confused - why do you want to own the SMB share on another computer? As far as I know, that share is always going to show up as being owned by root and the read/write permissions are set at the serving computer i.e. the Windows PC.

// dave

---

### Post by user1397 on 2006-05-22
this thread has sort of switched to this thread:

	 	  		 		 			 				 				 [IMG]http://ubuntuforums.org/images/lite/misc/paperclip.gif[/IMG]  				 				 			 			 			 			 			 			 			 				[Where is the windows network in terminal?]("http://www.ubuntuforums.org/showthread.php?t=179714")

---

