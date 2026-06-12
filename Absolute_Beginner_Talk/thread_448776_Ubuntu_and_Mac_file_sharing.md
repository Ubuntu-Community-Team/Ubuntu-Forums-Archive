---
title: "Ubuntu and Mac file sharing"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-05-19
Im trying to be able to access my external hard drives connected to my mac from my Ubuntu PC. Both computers are connected through a router. On Ubuntu I can see my mac but thats it, I cant see any files or shared folders. On the mac ive selected the option to to share files, personal file sharing and windows sharing just in case. Ive gotten the printer share to work, and i can print from my ubuntu pc to the printer connected to my mac. Anyone have any advice?

---

### Post by n8bounds on 2007-05-19
find out the IP address of your mac

open nautilus (or open a folder in gnome)

in the address bar (sorta, you know click the button so the bread crumbs go away and you can type a location in) put in this:

smb://192.168.1.44

replace that ipaddress with whatever your Mac has and hit enter

if it's actually shared the windows way this should show you some folders, you may have to tell your Mac WHICH folders to share, not just that you want to allow Windows TYPE folder sharing...I dunno

---

### Post by Zaff on 2008-03-20
Hi, I don't know how old this post is but I've done all that and I can connect to my macbook from my ubuntu desktop fine but I can't seem to acces my ubuntu shared folder from mac.
My ubuntu desktop appears as shared in the "SHARED" section of the finder but when I try to connect as a guest it fails and if I type in my login and password from ubuntu it fails too saying I've entered an invalild username and password in both cases.
I only used the Ubuntu Gutsy shared folder thing in System. Did I forget something ? It's set up as a Samba. I didn't find a field to add users or something.
Thanks for any help on the subject.

---

