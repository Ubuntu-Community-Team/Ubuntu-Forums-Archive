---
title: "Setting up a LAN between two Ubuntu's. And between Ubuntu and XP."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-12-12
I've done some reading but I'm still unsure of what to do? 

If I want to transfer a folder with music from my mothers XP laptop to my Desktop Ubuntu what do I need to download?

Samba? Or just the smbfs plugin?

After I copy all the music from her laptop so it doesn't get lost, she wants me to install Ubuntu! Help me out guys, if not I'll look like an *** in front of her xD

Thanks. =)


EDIT:
Here's a screenshot of my network window. (Places > Network)

[IMG]http://i9.tinypic.com/8bzyq0w.png[/IMG]

I haven't installed anything about ANYTHING regarding windows here. So is it preconfigured that I can access my XP laptop? When I double click it there's nothing there. Why is it such a hastle to connect to a LAN. =( BAD UBUNTU! BAD!

---

### Post by Dr Small on 2007-12-12
Install Samba on your Ubuntu system, make sure she has her music folder shared (on here windows machine), then go to nautilus and type:
```
smb://*ipaddress*
```

Where, *ipaddress* replace that with the windows machine IP Address.
Then you can copy files / folders and paste them somewhere on your system.

Dr Small

---

### Post by papuccino1 on 2007-12-12
That's some good advice Small! 

However, what is nautilus. I am a REAL beginner at Ubuntu. Not slow, not dumb, but a beginner eager to learn ;)

Help me out man. =)

---

### Post by spai on 2007-12-12
nautilus is like "explorer" in windows.
Actually type nautilus in the terminal and see it for yourself
Oh by the way in the screenshot you have shown, the "window" is nautilus :)

---

### Post by maybeway36 on 2007-12-12
My ISP (Charter) causes problems with Samba. I changed the resolve order line in /etc/samba/smb.conf to:
```
name resolve order = bcast lmhosts host wins
```

---

### Post by Dr Small on 2007-12-12
Nautilus is your file manager.
If you go to Places > Home, this will open up Nautilus.

Press CTRL + L, and this will open the location's bar, in Nautilus, and then you can begin typing :)

Dr Small

---

### Post by papuccino1 on 2007-12-12
> **spai said:**
> nautilus is like "explorer" in windows.
Actually type nautilus in the terminal and see it for yourself
Oh by the way in the screenshot you have shown, the "window" is nautilus :)

Ah! Good to know man. Thanks =) Learning something new everyday.

---

### Post by papuccino1 on 2007-12-12
EVERYTHING WORKS!!!

hahahaha I feel so sexy right now ;)

Thanks a bunch guys. See ya!

---

