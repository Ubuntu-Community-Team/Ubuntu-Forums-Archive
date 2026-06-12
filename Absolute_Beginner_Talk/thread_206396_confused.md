---
title: "confused"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by totallyconfused! on 2006-06-30
I am finding that this forum is very confusing as to where exactly I need to post m,y comment....so Ill give it a shot here...
   My boyfriend installed ubuntu/gnome on my puter which was great....while we were in luv...lol....Now he wont give me the admin password so i cant do anything on here....no printer/scanner.....cant play yahoo games......cant get voice for yahoo messenger......i cant even correct the time on here!!! I am very frustrated....I have been on here for almost a week trying to find some way to bypass the damn password so I can download the plugins i need to no avail....Of course, I cant uninstall and reinstall because he has the cd and what not.....Not to mention that im completely computer illiterate and this ubuntu is extremely confusing to me....so If there is anything I can do....Please reply.....
Ty!:confused:

---

### Post by IYY on 2006-06-30
This could work:

> A:
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.


But as for him having the CD: don't forget that Ubuntu can be downloaded for free and easily burnt on a CD. If you don't want to do that, you can even get a free CD shipped to you. And installation, provided that your hardware is supported, is very easy.

---

### Post by woedend on 2006-06-30
IYY has it.  But it depends on how he has it set up.  Did he disable sudo access for said account?  By default, ubuntu's admin password IS the user password.
follow the steps above.
to set the root password, simply type 'passwd' and push enter
let us know if this doesnt work, or what error messages you are getting.

---

### Post by IYY on 2006-06-30
There was also a security hole in Breezy that allowed you to see the password in the file

/var/log/installer/cdebconf/questions.dat

Of course, if you're running something other than an unpatched Breezy you won't have this, but it might be worth a shot.

---

