---
title: "[SOLVED] Help! I need Resoultion Help! Help!!!"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-11
I just upgraded to Hardy beta, and then it said I needed to update, I updated, restarted, and my resoluton is at 720:320 or something dude! I cant change it either!! Help! Linux is messed up so bad I cant even move the windows or click ok on anything! Help!! Why did it do this?!???!

---

### Post by LaRoza on 2008-04-11
Run this command:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and restart X.

---

### Post by R6V2 on 2008-04-11
Dude! The terminal doesn't even come up!! It just's a huge blank white screen!! Help Please!!

---

### Post by LaRoza on 2008-04-11
> **R6V2 said:**
> Dude! The terminal doesn't even come up!! It just's a huge blank white screen!! Help Please!!

Can you log on to the Recovery Console?

(It should be the second option in the Grub menu)

---

### Post by ByteJuggler on 2008-04-11
Press Ctrl-Alt-F1 while on the white screen, which should take you to a text mode console.  Then log in and enter that command.  Alternatively, boot up in recovery mode, which will also give you a text mode based administrative shell.

It sounds like video driver + compiz issues to me, by the way.  Do you use Compiz?  What video driver?  What video card do you have?

---

### Post by R6V2 on 2008-04-11
Well Actually, I typed blankly, and remembered that 'sudo' always requires password, so I typed that in, pressed enter, typed my password, and then pressed enter, and restarted, so why exactly did it do that? Now I have all the resouletions! Thank You!

---

### Post by LaRoza on 2008-04-11
> **R6V2 said:**
> Well Actually, I typed blankly, and remembered that 'sudo' always requires password, so I typed that in, pressed enter, typed my password, and then pressed enter, and restarted, so why exactly did it do that? Now I have all the resouletions! Thank You!

I have done that before, going by memory :-)

It just reconfigures xserver.

It often happens during an upgrade, X be "deconfigured".

That is the first command I memorized when I started Ubuntu.

---

### Post by R6V2 on 2008-04-11
I can see why you have over 500 thanked. Your so helpful, so I gave another! :)

---

