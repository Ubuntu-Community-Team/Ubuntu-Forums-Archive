---
title: "Network/File Sharing Project windows to ubuntu"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2007-11-21
Hi everyone.  I want to be able to send files from my windows desktop to my ubuntu 7.10 laptop but have no clue how to go about doing this.  

Any ideas, I need all the guidance I can get.  Thanks.

---

### Post by MaximusTG on 2007-11-21
Go to Places -> network, you should be able to see the windows pc there, if you have shared folders on the windows pc

---

### Post by 3rr0r on 2007-11-21
I go to network and I see "Windows Network"

I click on it and it goes to location: smb:///

with nothing in it.  I went on my windows desktop and created a folder and made sure it is shared on the network.  Any other ideas?

---

### Post by MaximusTG on 2007-11-21
What if, in nautilus, you type in the address bar:

smb://nameofwindowspc

and if that doesn't work:

smb://ipaddressofwindowspc

---

### Post by 3rr0r on 2007-11-21
no dice

---

### Post by MaximusTG on 2007-11-21
Do you have samba installed?
Try sudo apt-get install samba samba-common

(and then the steps I posted above)

---

### Post by 3rr0r on 2007-11-21
no, it didn't work.

it doesn't even try to connect.  It just immediately tells me that it can't. 

"Nautilus cannot display 10.0.0.2"  Please select another viewer and try again.

---

### Post by jonandrews on 2007-11-21
I've written a guide that shows a simple way to get Ubuntu pc's fully integrated onto a Windows network.

If you find it helpful, let me know.

The guide is at:  [www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

