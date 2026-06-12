---
title: "can someone help please"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by gmcm1979 on 2006-09-15
i had some trouble with xserver after an automatic update yesterday, i then used the live cd to access the internet, when i log on now it goes to the logon screen, i enter my username and password but keep getting returned to the logon screen

---

### Post by Brunellus on 2006-09-15
is it showing any errors?

---

### Post by gmcm1979 on 2006-09-15
at first it showed the error about xserver failing to start, i then used the live cd to get some help on here (as i am doing now) and now i get the problem as stated in my previous post

---

### Post by Brunellus on 2006-09-15
hit CTRL+ALT+F1, login there, and then

sudo chown YOURUSERNAME /home/YOURUSERNAME/.ICEAuthority

then CTRL+ALT+F7 and logging in again.

---

### Post by gmcm1979 on 2006-09-15
tried the advice from your post error states cannot acces file or no such file as .../ICEAuthority

---

### Post by Najand on 2006-09-15
Could you login in Text-base environment? (The black screen after pushing Alt+Ctrl+F1)

---

### Post by gmcm1979 on 2006-09-15
yes i can i enter username and password and then enter the sudo chown etc...

but i get an error which says cannot access:.......... no such file or directory

---

### Post by Najand on 2006-09-15
You have to change YOURUSERNAME with your own user name at:
"sudo chown YOURUSERNAME /home/YOURUSERNAME/.ICEAuthority"

---

### Post by gmcm1979 on 2006-09-15
i know

---

### Post by Najand on 2006-09-15
Can you do:
```

cd
ls -al .*

```
and copy/paste the output here?

---

### Post by gmcm1979 on 2006-09-15
i can't screen print but will transcribe as much as possible

sudo chown graham /home/graham/.ICEAuthority
cannot access: 'home/graham/.ICEAuthority': no such file or directory

---

### Post by Najand on 2006-09-15
Ok.. No need to paste everything here... Just the output to:
```

[COLOR="Blue"]cd
ls -al .I*[/COLOR]

```
is enough.

---

### Post by gmcm1979 on 2006-09-15
nah can't get this to work i just want to get my mp3's off the hard disk onto dvd's and then i am going use suse or maybe back to windows

---

### Post by Brunellus on 2006-09-15
try

chown USERNAME /home/USERNAME/.Xauthority

---

### Post by gmcm1979 on 2006-09-15
same error message as before 

can anyone suggest a way of getting the mp3's from my hard drive onto dvd's or maybe an external hard drive

---

### Post by Najand on 2006-09-15
First you need to login to your system to be able to continue... Anyway, youcan use Live CD to copyyour mp3's to your external hardware....

---

### Post by Brunellus on 2006-09-15
simple solution woudl be to boot the live CD, mount hard drive, and copy the files onto an external hard drive.

I'm struggling to understand what's gone wrong with your system.  there's no ~/.ICEAuthority file?  Nor a ~/.Xauthority file either?  Shouldn't be so.

---

### Post by Thenotsowyzewun on 2006-09-15
I agree, booting up a live cd and a DVD burner or External hard drive (or network to another computer) to copy all your files onto.

Or you could repost over at linuxquestions.org forums, they´ve got alot more people so maybe someone would be able to help.

---

