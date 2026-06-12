---
title: "X Server"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by M.Mizery on 2007-05-28
Hello all,


           I am new to Ubuntu and have used the live cd for quite sometime, Ubuntu grew on me and so I installed after doing some research. I was wondering if anyone could possibily help me with adjusting my screen resolution? Right now it my screen is 640 x 480 and I can not make it the way I used to have it in Windows which was 1024 x 768. I went to system from my taskbar and to help...I looked at the Ubuntu book expert. It says in it, if your screen resolution
is not correct and not other choice is available, refer to recipe showing to reconfigure your x server.

I am wondering if x server is already in the system or do I have to download it or something to fix my problem?

If anyone can help me out I would really appreciate it a lot.

And thank you so much for reading my post.

MM

---

### Post by nonimus on 2007-05-28
> **M.Mizery said:**
> Hello all,


           I am new to Ubuntu and have used the live cd for quite sometime, Ubuntu grew on me and so I installed after doing some research. I was wondering if anyone could possibily help me with adjusting my screen resolution? Right now it my screen is 640 x 480 and I can not make it the way I used to have it in Windows which was 1024 x 768. I went to system from my taskbar and to help...I looked at the Ubuntu book expert. It says in it, if your screen resolution
is not correct and not other choice is available, refer to recipe showing to reconfigure your x server.

I am wondering if x server is already in the system or do I have to download it or something to fix my problem?

If anyone can help me out I would really appreciate it a lot.

And thank you so much for reading my post.

MM

What happens when you go to System>Preferences>Screen Resolution?

---

### Post by Ek0nomik on 2007-05-28
```
dpkg-reconfigure -phigh xserver-xorg
```

Try running that, then using the spacebar to select your desired screen resolutions.

If that doesn't work, we can edit the xorg manually.  Let me know how it goes.  :)

---

### Post by M.Mizery on 2007-05-28
ok, will try

---

### Post by M.Mizery on 2007-05-28
dpkg-reconfigure -phigh xserver-xorg

How do I do this? Do I go to the terminal window and type this in or something?


Thank you

---

### Post by Ek0nomik on 2007-05-28
Yep, you do it in the terminal.

---

### Post by M.Mizery on 2007-05-28
Ek0nomik  	
Code:

dpkg-reconfigure -phigh xserver-xorg

Try running that, then using the spacebar to select your desired screen resolutions.

If that doesn't work, we can edit the xorg manually. Let me know how it goes?



MM saids:


Thank you for trying, but this does not give me clear instructions. 

I did put the code in the terminal and hit enter put it did not work.

---

### Post by Ek0nomik on 2007-05-28
What do you mean it doesn't work?

Copy and pasting your terminal output will be good practice on the forums so people can see exactly what's wrong.  :)

I forgot one part of the command by the way, sudo.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That command will do the trick.

If you have problems, post your terminal output and I will help the best I can.

---

### Post by justwannasearch on 2007-05-28
This one should work:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by M.Mizery on 2007-05-28
sudo dpkg-reconfigure -phigh xserver-xorg
Password:

**********************************************************


Well tried that and this is what I got above for me to type in my password. 

Sorry if I upset any body or had improper chat manners, but you also asked me tell you what happened and did not say exactly what you meant????

---

### Post by M.Mizery on 2007-05-28
sudo dpkg-reconfigure -phigh xserver-xorg
Password:

**********************************************************
Ek0nomik,

Well tried that and this is what I got above for me to type in my password. 

Sorry if I upset any body or had improper chat manners, but you also asked me tell you what happened and did not say exactly what you meant????

---

### Post by justwannasearch on 2007-05-28
> **M.Mizery said:**
> sudo dpkg-reconfigure -phigh xserver-xorg
Password:

**********************************************************


Well tried that and this is what I got above for me to type in my password. 

Sorry if I upset any body or had improper chat manners, but you also asked me tell you what happened and did not say exactly what you meant????

This is OK, just type your password and press enter.

---

### Post by M.Mizery on 2007-05-28
justwantoseach:

the system would not let me type my password in. 

I tried to type my password and nothing appears on the screen. I am still starring at the screen I have copied and pasted onto this forum.

Do you have any suggestions?

---

### Post by justwannasearch on 2007-05-28
> **M.Mizery said:**
> justwantoseach:

the system would not let me type my password in. 

I tried to type my password and nothing appears on the screen. I am still starring at the screen I have copied and pasted onto this forum.

Do you have any suggestions?

Type it and press enter.
The password is not displayed on the screen. This way nobody can steal your password by looking over your shoulder.

---

### Post by Ek0nomik on 2007-05-28
**M.Mizery**

You don't have any improper manners bud, you're doin' just fine.  :p

Just do as *justwannasearch* mentioned.  Type in your password and don't look for it on the screen.  It's a security feature.

Also, using the code box on the forum works best for posting terminal output.  (It's the # sign).  Just a suggestion.  :)  I look forward to seeing how it turns out.

---

### Post by M.Mizery on 2007-05-28
justwannasearch:


typed in my password and then pressed enter:

This is what I got:


Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts


I do not understand why the system won't event let me type in my own password???
This is bizarre?

I can log onto my computer, update it and change the time with my password, but it will not take it in the terminal.

MM

---

### Post by Ek0nomik on 2007-05-28
> **M.Mizery said:**
> justwannasearch:


typed in my password and then pressed enter:

This is what I got:


Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts


I do not understand why the system won't event let me type in my own password???
This is bizarre?

I can log onto my computer, update it and change the time with my password, but it will not take it in the terminal.

MM

Are you sure your CAPS LOCK is off?  When running the sudo command, it will be exactly the same one that you use to login to your computer.

---

### Post by M.Mizery on 2007-05-28
Are you sure your CAPS LOCK is off? When running the sudo command, it will be exactly the same one that you use to login to your computer.


No, it was off, LOL @ my self. Dummy me forgot to leave my num lock on.

It's late you know how that goes??

anyways got my password in and this is what is on my screen:


xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070528033546

and then you know after that yourcomputer name@computername - desktop $


What you would I have to do from here?

---

### Post by Ek0nomik on 2007-05-28
So you run the command, you get the backup file message in the terminal, correct?  Then nothing happens?

You don't get taken to a blue screen to load up some options?

---

