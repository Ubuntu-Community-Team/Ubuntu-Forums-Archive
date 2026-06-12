---
title: "[SOLVED] desktop effects"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-01-28
i installed ubuntu about two weeks ago and today i have finally got the screen resolution and refresh rate to where they are supposed to be. My next step is to get my desktop effects working, which may prove harder than i had originally thought. I have read many posts that tell me that my graphics card is blacklisted. i have a Mobile Intel GM965. I know this card is capable of 3d graphics so why is it blacklisted? is there a way that i can get around it so i can enable desktop effects? I am hoping to eventually get compiz fusion working, is this possible with my graphics card?

---

### Post by emarkd on 2008-01-28
I can't help you with that card, but I can recommend that since you've got a working x configuration and it took you that long to get it, I'd go right now and make a backup of your xorg.conf in case something breaks as you dig deeper:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.thisworks
```

That simple thing has saved me several times...

---

### Post by PurposeOfReason on 2008-01-28
"
[Update: it is known that Intel 965 graphic chipset is in compiz blacklist. You can force compiz to skip checking and everything goes back to normal.

to do so, in terminal make sure you are in your home directory then type:

sudo gedit .config/compiz/compiz-manager

and add this line:

SKIP_CHECKS=yes

now try compiz again.]"

[http://osnovice.blogspot.com/2007/10/first-experience-with-ubuntu-710-gutsy.html](http://osnovice.blogspot.com/2007/10/first-experience-with-ubuntu-710-gutsy.html)

---

### Post by ronmarley1 on 2008-01-28
If I remember correctly, it is blacklisted due to video playback issues.  I've read work-arounds, so you should be able to do it.  Stability may be an issue.

---

### Post by tjwoosta on 2008-02-01
ok when i type sudo gedit .config/compiz/compiz-manager i get a blank page with no text, i can add the SKIP_CHECKS=yes but i cant save because it doesn't exist or something
what do i do?

---

### Post by PurposeOfReason on 2008-02-01
I'm guessing it says ~/.config/compiz doesn't exist? Run

mkdir ~/.config/compiz

to make it.

---

### Post by tjwoosta on 2008-02-01
i really dont know if im doing this right but this is what happened

tj@tj-laptop:~$ mkdir /.config/compiz
mkdir: cannot create directory `/.config/compiz': No such file or directory
tj@tj-laptop:~$

---

### Post by PurposeOfReason on 2008-02-01
Make sure you have the ~

It is a shortcut for typing /home/YOUR USER NAME/

I'm helping you make the directory /home/whatever/.config/compiz. You just tried to make /.config/compiz. As no /.config exists, you can't make a /.config/compiz.

---

### Post by tjwoosta on 2008-02-01
so no matter where i make the directory it will work all the same?

---

### Post by tjwoosta on 2008-02-01
ok i see it is all starting to make sense to me now

---

### Post by tjwoosta on 2008-02-01
alright i tried to mkdir but i guess it did exist after all because it says already exists,

so i went back to the other step
sudo gedit  /home/tj/.config/compiz/compiz-manager

i got a blank page but this time when i added the SKIP_CHECK=yes it saved
but i still cannot activate desktop effects this is what happens when i try to start compiz

tj@tj-laptop:~$ sudo compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by PurposeOfReason on 2008-02-01
Why are you using sudo? Try using 

compiz --replace

---

### Post by tjwoosta on 2008-02-01
i get the same message
tj@tj-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

i dont know if it means anything but when i go back to 
sudo gedit  /home/tj/.config/compiz/compiz-manager

the SKIP_CHECK=yes is not there even though i just saved it

---

### Post by PurposeOfReason on 2008-02-01
While I can't be too sure as I've never heard of sudo doing this, try editing it without sudo. There is no need to be root to edit your files in your home directory. It's just bad practice.

---

### Post by tjwoosta on 2008-02-01
hmm i restarted my computer and now the SKIP_CHECK=yes is there but it still does the same thing when i try to start compiz  

o well im not really all that comcerned with it right now anyway

thanks for all of your help and patience

---

### Post by juky on 2008-04-01
"SKIP_CHECK=yes" (without quotes) should work, but the path is:

```

/etc/xdg/compiz/compiz-manager

```

Cheers!

---

