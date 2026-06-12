---
title: "Chicken of the VNC (Mac)  to Ubuntu"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by pdpotter on 2008-02-17
I have read several threads referencing problems similar to mine, but none solved my problem.  I want to be able to access my Ubuntu box headlessly from my iMac. I have a KVM that I use to set up the Ubuntu box.

I use an iMac (OS X 10.5.2). On the Ubunu box, I used Remote Desktop Preferences, checked both boxes under "Sharing," and the second box under "Security" and entered a password.

On the Mac, I used Chicken of the VNC, entered the host (Ubuntu) IP, and left display set at 0. I entered the same password mentioned above, but I get "authentication failed."

I know the IP # is correct, because I can use Samba for file sharing, but I really want to "see" and control my Ubuntu box from my Mac.

Any help?

---

### Post by mattismyname on 2008-02-17
One thing that's sort of strange about the default VNC server on Ubuntu is that it requires you to be logged in at the terminal before it will share the desktop.

One thing you might try is sshing in and running an independent vncserver, set the password with vncpasswd, and then connect in from the mac.

---

### Post by pdpotter on 2008-02-17
Thanks, Mattismyname.

How do I run an independent vnc server? Sorry for the newbie question.

---

### Post by mattismyname on 2008-02-18
To install the standalone server: ```
sudo apt-get install vnc4server
```
Then, set your vnc password: ```
vncpasswd
```
Then launch the vncserver: ```
vnc4server
```

After it has started up, you should be able to connect from the mac.

---

