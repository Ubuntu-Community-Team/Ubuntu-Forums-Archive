---
title: "keyring help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2008-01-27
Hi everybody

I was looking about how to change the keyring and i found some suggestion about installing libpam-keyring enter package with the terminal. But when I have restarted the laptop i cannot go inside linux anymore because there is the window "Authentication failed" continuously. Does someone have the cure?

---

### Post by Hospadar on 2008-01-27
what happens if you boot in recovery mode? (as per the grub menu, you might have to press a key during boot to open it up, look for messages during the boot)
Also, where exactly can you not get in? is it at the login window?
if that's the case, at the login window try doing ctrl-alt-F1 to get a text terminal, log in there and then uninstall libpam-keyring by means of command line "sudo apt-get remove libpan-keyring" and then restart your machine and see what happens.

---

### Post by goliath10 on 2008-02-02
i had the same problem a few months ago. shortly after gutsy came out, i got tired of always having to put in the password for my wireless keyring, I havent gotten it fixed yet (mostly cause ive been busy with a heavy courseload and i've basically given up on my linux box cause its a piece of s*** and im getting a macbookpro soon so i'll need to install to that anyways)  


But ya, what happens is it does something equivalent to pressing enter when you are trying to login

(i.e., before you login at all or do anything it presses enter, u try and get rid of the dialog but it comes back up and you cant log in)

trying a
sudo init 5
wont let me get in at all either, it goes to the same normal login screen. 

i think it might haev something to do with deleting the original keyring, thats what the guide i was using told me to do. i said to myself "...." but because i am foolish and impatient i went ahead with it anyways, instead of trying it out without deleting the keyring.

im still fairly new to linux and im kind of a slow learner :P

if anyone know a solution that would be super awesome.

 i'll post a picture and a vid of itin a few min

---

### Post by goliath10 on 2008-02-02
pic 

[[IMG]http://img142.imageshack.us/img142/5682/dsc02282ip2.jpg[/IMG]](http://imageshack.us)[[IMG]http://img151.imageshack.us/img151/5469/dsc02283iv4.jpg[/IMG]](http://imageshack.us)


vid

[http://www.youtube.com/watch?v=XM3GvHM1yrk]("http://www.youtube.com/watch?v=XM3GvHM1yrk")   <----- i'll fix this shortly (by that i mean give youtube to process it :P

[http://www.youtube.com/v/XM3GvHM1yrk]("http://www.youtube.com/v/XM3GvHM1yrk")

---

### Post by midnightray on 2008-02-04
Well ur post is 2 days old but heres the solution:

Reboot and enter recovery:

type:

pico /etc/pam.d/gdm

remove the line:

@include common-pamkeyring

reboot back into normal ubuntu. Problem fixed.

(if u get a security error stick sudo in front)

---

### Post by stchman on 2008-02-04
> **antonio_ing said:**
> Hi everybody

I was looking about how to change the keyring and i found some suggestion about installing libpam-keyring enter package with the terminal. But when I have restarted the laptop i cannot go inside linux anymore because there is the window "Authentication failed" continuously. Does someone have the cure?

Yes, your keyring password needs to match your login password.

[http://www.stchman.com/keyring_password.html](http://www.stchman.com/keyring_password.html)

---

### Post by goliath10 on 2008-02-05
will that enable the pam keyring to work?

---

