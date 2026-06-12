---
title: "Sluggish VNC connections"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Copps on 2006-09-18
I am using a VNC aoftware client to connect from my Windows PC at work to my Ubuntu machine at home over SSH tunnelling. No probs logging in, but the remote desktop window is so sluggish for even tasks like moving the mouse cursor and opening programs.

When I remote into Windows PCs I have the option to set a connection speed which restricts various features like desktop backgrounds, windows themes etc in exchange for a much faster performance. Any way to do this in Ubuntu?

---

### Post by buffy^ on 2006-09-18
Yes it is possible, as the client side is not allowing you to control it from there, then you shuold ne able to log in and goto system, and drop down to whereis says remote desktop and alter the setting in there.

---

### Post by Copps on 2006-09-18
Thanks. But the only options I see are;

 Sharing
* Allow other users to view your desktop
* Allow other users to control your desktop

Security
When a user tries to view or control your desktop
* Ask for confirmation
* Require the user to enter this password

I don't see how that helps speed up my connection?

---

### Post by buffy^ on 2006-09-18
Ok, you have other options, try could try another VNC server / client and remove the limited on thats there.

---

### Post by Copps on 2006-09-18
I've made some changes in the remote VNC client I'm using, and logged on again, but it's not much quicker. Can I make setting changes on the VNC server I've installed to Ubuntu? I ran

sudo apt-get install vnc4server xinetd

to get a VNC server up and running.

---

### Post by Copps on 2006-09-20
Anyone?

---

