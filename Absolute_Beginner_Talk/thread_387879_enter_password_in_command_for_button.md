---
title: "enter password in command for button"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by EtniesBMX on 2007-03-18
I want to create a button on my desktop with the command "kdesu dolphin" to run my dolphiin file manager with root access, but I also want to enter the password in the command so that I don't have to enter it in the dialog box each time. Does anyone know how to do this?

---

### Post by Madpilot on 2007-03-19
I doubt it can be done easily.

It shouldn't be done, either - having your password stored in plaintext in a script like this is a pretty major security hole.

---

### Post by EtniesBMX on 2007-03-19
I stumbled across it once doing a search in google and it was actually very easy.... I just can't find the page again. :redface:

---

### Post by v8YKxgHe on 2007-03-19
to be honest, for the extra seconds it'll take you to enter in the password, is far better than leaving you're password exposed.

---

### Post by LanDan on 2007-03-19
it can be done very easily,

and you can find out how to do this on google, you might want to start there since you will spend a lot of time searching there when you screw up your system in no time,

have fun, it will be a great learning experience ;)

---

### Post by EtniesBMX on 2007-03-19
So you are all saying that it is easy for anyone to access and read files on my desktop? If they can read files on my computer as it is, then isn't the security already compromised? Could someone clarify just how much is accessible to anyone on the web as it is?

---

### Post by v8YKxgHe on 2007-03-19
I understand what you're getting at, though it's not like that. It's just genearly not good pratice to be able to double click on an icon and have a root-filebrowser at you're finger tips. Not only because of security issuses, but also to protect you from you're self. 

If you forget that the icon on the desktop is for a root-filebrowser and not a regular file browser, you could very easily remove something you shouldn't by accident, for example.

---

### Post by MkfIbK7a on 2007-03-19
but the thing is...
if someone knows anything about grub and linux they can just open a recovery terminal which is root...

---

### Post by compmodder26 on 2007-03-19
> **wert613 said:**
> but the thing is...
if someone knows anything about grub and linux they can just open a recovery terminal which is root...

Not if you A) Remove the recorvery mode option, or B) Lock the recovery mode option with a password.  You would also have to password protect your BIOS and boot menu, if applicable.  After that, the only way to physically gain root access would be to remove the hard drive and place it in another computer.

---

### Post by LanDan on 2007-03-19
mmmmm

its not for others ;)


believe me after some years and several **** ups by myself, you will find out that it is a good thing to protect you from you

---

### Post by mcduck on 2007-03-19
> **compmodder26 said:**
> Not if you A) Remove the recorvery mode option, or B) Lock the recovery mode option with a password.  You would also have to password protect your BIOS and boot menu, if applicable.  After that, the only way to physically gain root access would be to remove the hard drive and place it in another computer.

..Or clear BIOS password by removing the CMOS battery for a while or by using jumpers on your motherboard. Or by booting from any live-cd.. If somebody gets physical access to your machine you are already compromised :D BIOS or GRUB passwords are not a solution.. :D

---

### Post by compmodder26 on 2007-03-19
> **mcduck said:**
> ..Or clear BIOS password by removing the CMOS battery for a while or by using jumpers on your motherboard. Or by booting from any live-cd.. If somebody gets physical access to your machine you are already compromised :D BIOS or GRUB passwords are not a solution.. :D

Yeah sure, that too, but if they can do that, your computer is most likely stolen and that means all bets are off.  As for the live cd, I already covered the boot menu.  Again, it's a moot point if they can get inside your computer.

---

### Post by compmodder26 on 2007-03-19
I should note that if you are afraid of your computer being stolen, you should encrypt all your sensitive data with something like encfs.

---

### Post by EtniesBMX on 2007-03-20
> **AlexC_ said:**
> I understand what you're getting at, though it's not like that. It's just genearly not good pratice to be able to double click on an icon and have a root-filebrowser at you're finger tips. Not only because of security issuses, but also to protect you from you're self. 

If you forget that the icon on the desktop is for a root-filebrowser and not a regular file browser, you could very easily remove something you shouldn't by accident, for example.

Could you please explain the situation for me? How much access do people have to my computer? 

 I understand that it is not good practice to do this, but I would still like to know how to do it. I want my machine to run how I want, and I am willing to accept that I might mess my computer up.  I have the installation CD in case anything goes wrong.

---

### Post by v8YKxgHe on 2007-03-20
> How much access do people have to my computer? 
You and you only (I guess, unless you have other accounts on there?). 

For you're problem, I can't help sorry - I have no idea how to do it.

---

