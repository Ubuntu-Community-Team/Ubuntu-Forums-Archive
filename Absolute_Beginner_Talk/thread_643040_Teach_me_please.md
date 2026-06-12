---
title: "Teach me please"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by fr33zypop on 2007-12-17
Ok I am new to the Linux world, I have been an avid winXP user for many years. I am really working hard to learn the ins and outs of Ubuntu. I am currently trying to setup a sharing folder with samba, but that’s not what I am looking help on. I have all the info on what to do with that. It’s just how I have to implement the command in the terminal. This is what i mean. I found this on the wiki page and I can’t understand or know how to read it correctly. 

sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers


system_username = "network username"


When i look at this I am not sure how i would enter the username and password. Say I want the user to be Jason and the password to be Password. 

sudo smbpassword -a system_jason
gksudo gedit /etc/samba/smbusers

or 

Tell me how to do this

If this is correct, i haven’t played around with it. I am at work just doing some research. If I add this or how ever it is correct this user/pass combo would allow me on a XP machine to log into the Samba server. 

I like screen shots I am a visual learner. I would have done a search for this on the forums but I don’t know the wording of what I am trying to do.

---

### Post by jba6511 on 2007-12-17
try: sudo smbpasswd -a jason
gksudo gedit /etc/samba/smbusers

basically you are creating a password for the user jason and then editing the smbusers file.

---

### Post by fr33zypop on 2007-12-17
So the way you put it there, I am just chosing the username and not the password, or is it just cause I said the pasword I wanted to use is how the code is writen.

---

### Post by fr33zypop on 2007-12-17
my bad on this post -  it was repost..

---

