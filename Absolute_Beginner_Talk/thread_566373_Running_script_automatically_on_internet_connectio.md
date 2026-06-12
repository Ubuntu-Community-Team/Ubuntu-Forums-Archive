---
title: "Running script automatically on internet connection"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-10-03
Hi.

On my university campus, in order to use the internet, we have to authenticate with an ssh client. So on my laptop, everytime I want to use the internet, I have to open up Terminal and use ssh and leave that Terminal session open so that ssh can run.

I was wondering if it were possible to run a script when my laptop connected to the campus wireless internet, or my residence wired internet, so that the script will connect to the ssh server, request my password and then run in the background.

---

### Post by Mister.Vash on 2007-10-03
A starting point would be the folder /etc/network/if-up.d 

Scripts placed in this folder will run when you make your network connection

---

