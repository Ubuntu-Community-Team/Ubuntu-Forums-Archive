---
title: "windows xp network"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by strahil on 2005-12-02
i recently installed ubuntu on this pc.
But my other (xp) computer is not seen in windows network.
So I add it as a server(the ip and all). and when it asks me for authentication, I put the password and it just wont login(password wron or smting:confused: ).
I am a Linux noob, so any help would be appreciated

---

### Post by detyabozhye on 2005-12-02
First you have to set up samba to let yourself login from another computer.
Far as I remember, this is the command: "sudo smbpasswd -a <yourusername>"
I don't remember if there's more after that though.

---

### Post by phen on 2005-12-02
actually, i think there's a misunderstanding?! Do you try to connect to your xp box while using the ubuntu pc?

then: enable your guest account on xp, and try with login "Guest" and password " " or "Guest" (don't remember...)

if you try to connect to your ubuntu box from xp, you have to set up samba. thats a bit more complicated, and i would suggest that you look for howtos/tutorials on the forum/net.

---

### Post by strahil on 2005-12-02
[QUOTE=detyabozhye]First you have to set up samba to let yourself login from another computer.
Far as I remember, this is the command: "sudo smbpasswd -a <yourusername>"
I don't remember if there's more after that though.[/QUOTE]

THANK U...OMG IT WORKED..
Anyways now I can logon from the xp box but when I try to reach it from the ubuntu one it says: sorry couldn't display all the contents of...
anyways..;)

---

### Post by AndyCooll on 2005-12-02
1. Have you set up  both your PC's (XP and Linux) to be on the same domain?
2. Have you set up Samba, including the domain settings?
3. If you have, have you set up your smb password (as mentioned in a post above)?
4. Is your account on XP the same as on your Linux box (i.e. name and password?)
5. Are both Samba (a line in smb.conf) and your XP pc (Administrative Tools-->Local Security Policy-->Security Options-->Enable Microsoft Network Client...SMB) set up work with encrypted passwords.
6. Is your XP pc set up with any folder shares?

Ok. Enough questions for starters.

:cool:

---

### Post by detyabozhye on 2005-12-02
Doitashimashite (You're welcome)! ^_^

---

### Post by strahil on 2005-12-02
another problem( ;) ): I dont mind being able to access the linux box from the xp box only, but I cant modify files from teh xp box or copy my xp files over to teh linux one.
srry 4 the typos and once again any help would be appreciated.

---

### Post by AndyCooll on 2005-12-02
That's due to permission settings.

On your Linux box, did you set your shares (in Samba) to be readable and writeable?

:cool:

---

### Post by strahil on 2005-12-02
I dont know how to change those samba settings!
So I got the graphical tool(swat).
Yet when I install a package in synaptic...theres no icon for me to open it!
one problem after another...:???:

---

### Post by Zimmer on 2005-12-02
Go here, don't worry about SWAT...

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server)
Followed the instructions yesterday and my Ubuntu sees Windows XP and Windows XP sees Ubuntu......
and if you have any problems setting up a share send me  a message....
and if the instructions in the starter guide are  ambiguous I will try and clarify them for you....
Regards
Zimmer

---

### Post by detyabozhye on 2005-12-02
Got to System->Administration->Shared Folders It's in there.

---

### Post by strahil on 2005-12-03
I did and I still dont have write permissions.

---

### Post by detyabozhye on 2005-12-03
Ok, after you open it, click on the folder you want to be writable, click properties, and make sure "Read only" is NOT checked, then click OK. Just kinda thought you'd see it, so I didn't explain in my last post.

---

### Post by strahil on 2005-12-03
I did exactly that and Is till dont have write permission.

---

### Post by detyabozhye on 2005-12-03
Does your user on ubuntu have permission to write to those files or directories?

---

### Post by strahil on 2005-12-04
yes.
this problem is so perstitent!srry if I'm bugging ya!

---

