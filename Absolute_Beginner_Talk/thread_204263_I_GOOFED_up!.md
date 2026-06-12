---
title: "I GOOFED up!"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Geek Sanity on 2006-06-26
Ok, so the network and internet were working fine, and then I downloaded LimeWire and used the instructions I found here to install it, still was getting the same error message as a couple of the other people were, so I rebooted to see if that would help (hey it works in Windows) and then when I tried to log in, I got this message: >  GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator. 

What I have tried?
1) Tried rebooting from the Live CD.  I crashed it.
2) Tried logging in as Root.  It said System Admin cannot log in from this computer.
3) Am afraid to re-install, because even though I have 2 HD's (1 3.2gb that my OS is installed to, and 1 80gb that my pictures, music, and other stuff are saved on.  I would rather not reformat my 80gb drive, since I cannot get that stuff back) I am afraid somehow if I reinstall it is going to delete my pictures and music and stuff.

So what can I do to access my computer?

---

### Post by acht on 2006-06-26
have you tried formating?

---

### Post by shoot2kill on 2006-06-26
[QUOTE=acht]LoL![/QUOTE]
im sure that was helpful....

i am 90% sure that if you re-install ubuntu on ur small HDD, none of the files will be affected on your 80GB HDD... im sure someone else will be able to help you out better than me

---

### Post by nalmeth on 2006-06-26
Log in to failsafe terminal session

try this command, replacing username with *your* username:

chown username /home/username/.ICEauthority

Have you possibly run out of disc space?

---

### Post by Geek Sanity on 2006-06-26
I shouldnt have, because I have never saved anything to the smaller drive. A friend of mine told me that it automatically writes to that drive when you log in, but I wasn't sure how accurate that was.  How do I log into a failsafe terminal? I'm at my bf's house using his windows machine, so when I go home I should be able to try it out.

---

### Post by glotz on 2006-06-26
In the login screen hit sessions

---

### Post by acht on 2006-06-26
[QUOTE=shoot2kill]im sure that was helpful....

i am 90% sure that if you re-install ubuntu on ur small HDD, none of the files will be affected on your 80GB HDD... im sure someone else will be able to help you out better than me[/QUOTE]

wtf? i did't say "LoL!"

---

### Post by muep on 2006-06-26
First, try logging in in text mode. Press ctrl+alt+f1 to get to a text console. Log in and you get a bash shell.

Then:

sudo rm .ICEauthority .Xauthority

After that, try graphical login again. You get back to the login screen with ctrl+alt+f7

---

### Post by Geek Sanity on 2006-06-26
Thank you.  If all goes well, I post a reply to this from my own computer when I get back home.  If not....well....I'll be back with more questions.

---

### Post by muep on 2006-06-26
If you after all find yourself stuck, try to make a new account. It can be made from the text console with:

sudo adduser new_username

where new_username is the new username you want.

After that try logging in with that new account.

---

### Post by jimrz on 2006-06-26
[QUOTE=Geek Sanity]
3) Am afraid to re-install, because even though I have 2 HD's (1 3.2gb that my OS is installed to, and 1 80gb that my pictures, music, and other stuff are saved on.  I would rather not reformat my 80gb drive, since I cannot get that stuff back) I am afraid somehow if I reinstall it is going to delete my pictures and music and stuff.[/QUOTE]

When you say the 3.2 Gb drive is where your OS is do you mean just "/" or do you mean / + /home + swap?

If it is the latter you may well be put of room on that drive. If That is the case, you should probably re-install using the small drive for "/" (although that may still prove to be a bit smallish if you plan on installing o lot of progs) and creating seperate partitions on your large drie for your swap and "/home". Assuming that your 80 Gb drive has enough available space, this would eliminate the prob.

---

### Post by H.E. Pennypacker on 2006-06-29
[QUOTE=acht]wtf? i did't say "LoL!"[/QUOTE]

How did he quote you using it then? ;)

---

### Post by minden on 2006-06-29
> **H.E. Pennypacker]How did he quote you using it then?  said:**
> 

its easy to change someones quotes

[QUOTE=H.E. Pennypacker]I love windows
[QUOTE=H.E. Pennypacker]LoL![/QUOTE]

---

### Post by H.E. Pennypacker on 2006-06-30
Minden, yeah, I know..lol..I was just messing with acht.  But I wonder why someone would intentionally misquote someone.  lol

---

### Post by Geek Sanity on 2006-07-02
Ok, re-install, and all is good, except I lost my w32codecs, so I can't use mp3s I had before.  Other than that, I've got it figured out.  Anyone know where to get w32 codecs?

---

### Post by H.E. Pennypacker on 2006-07-12
> **Geek Sanity said:**
> Ok, re-install, and all is good, except I lost my w32codecs, so I can't use mp3s I had before.  Other than that, I've got it figured out.  Anyone know where to get w32 codecs?

[http://www.ubuntuforums.org/showthread.php?t=210853&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=210853&highlight=w32codecs)

---

### Post by SigmaX on 2006-07-12
Automatix can come in handy for the codecs (and much more):

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

SigmaX

---

