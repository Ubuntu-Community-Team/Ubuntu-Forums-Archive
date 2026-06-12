---
title: "Grub"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by jamesburns on 2008-01-09
Hi
I am trying to change the GRUB menu in Ubuntu. I get into the Terminal window but when asked for my password I cannot enter any letters. The enter button on the key board still works but nothing else. Please advise
Thanks

---

### Post by shareMenaPeace on 2008-01-09
Hi James, 
it is normal that you cannot see the typed letters when asked for your password inside the terminal.

Just type it in and hit enter, and if you think you misstyped it just hit a view times the Backspace key.

Cheers

---

### Post by m0rphex on 2008-01-09
Usually when you write a password in the terminal you don't see the letters or stars. So just type in the password even though you cant see it and then press enter. I don't know if this is what you needed :P

---

### Post by jamesburns on 2008-01-10
Thanks for the replies.
The cursor does not move when typing in the password. Is this normal as well?
I still can't get into the Duelboot-Configure Boot Menu or Duelboot-Boot Options. Any advice will be welcome. 
Thanks
James

---

### Post by zvacet on 2008-01-10
Yes,it is normal.Just type your password and press Enter.

---

### Post by jamesburns on 2008-01-10
Thanks again. 
After typing my password I get back to the command line but I am expecting to get to the Duel-Boot Options menu. I am typing in "sudo gedit/boot/grub/menu.1st".
This takes me to "password". I enter password then go back to command line.

Thanks
James

---

### Post by sailor2001 on 2008-01-10
code is :  gksudo gedit /boot/grub/menu.lst

---

### Post by jamesburns on 2008-01-10
Thanks again
james@jims:~$ gksudo gedit /boot/grub/menu.lst. I copied and pasted your reply but it says I do not have rights to use this command as I am using the sudo command.

James

---

### Post by Sef on 2008-01-10
You may have typed in the wrong password or added an extra space when copying it.  The command does work.  I tried it myself.

---

### Post by jamesburns on 2008-01-11
Thanks once again for the help people.
Am still getting a failure however.

"Failed to run gksudo gedit /boot/grub/menu.lst as user root.
The underlying authorisation mechanism (sudo) does not allow you to run this programme.
Contact the system administrator. 

Any ideas please?

Thanks
James

---

### Post by allforcarrie on 2008-01-11
you could do: 
 
su
password :
 then gedit /boot/grub/menu.lst

---

### Post by jken146 on 2008-01-11
> **allforcarrie said:**
> you could do: 
 
su
password :
 then gedit /boot/grub/menu.lst

su doesn't normally work in Ubuntu.  It should be **sudo su** or **sudo -i**

@jamesburns: Can you use sudo for other commands?  For example, try ```
sudo ls
``` (ls just lists the contents of the directory you're in btw).

---

### Post by jamesburns on 2008-01-12
Thanks again for the help.
I have tried all of the suggestions and end up with not recogonised. I tries "sudo ls" but end up back at the command prompt. Is this a clue. When I type "L" at the command prompt it comes out as in the your forum response, yet in my reply L come out as "l".

Thanks

James

---

