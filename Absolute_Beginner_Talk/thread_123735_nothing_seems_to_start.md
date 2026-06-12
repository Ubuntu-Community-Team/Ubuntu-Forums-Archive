---
title: "nothing seems to start"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by mcopeland@pobox.com on 2006-01-30
update manager says I have 39 updates available but it will not start, I thought it might be the Firestarter but when I try to start that I get a msg that it's starting and then nothing. Browser and email seem to be the only things that are working on demand

---

### Post by souteneur3190 on 2006-01-30
wait... u click on update and nothng happens?

---

### Post by mcopeland@pobox.com on 2006-01-30
when I click on the red update  ball i get the menu  but nothing works on the menu, i cannot start synaptic package manager either

---

### Post by aysiu on 2006-01-30
What about Applications > Accessories > Terminal and ```
sudo apt-get update
sudo apt-get dist-upgrade
``` Does *that* work?

---

### Post by mcopeland@pobox.com on 2006-01-30
no, I get
 unable to lookup r50e via gethostbyname()
r50e is my computer name

---

### Post by ecto on 2006-01-30
I had the same problem when i had to set up a server at my school when i updated. What happened was that because the update packages were http and the gpg key was something else the gpg key was blocked (a port block) and we got this error. Are you using a dhcp client like dhcpcd or static? If its static you could try reconfiguring your ip and various network devices or if dhcp you can try running dhcpcd in terminal and see if another ip is established. Im not sure if any of these would work becuase the way i fixed the problem at the school was simply take it home and update it (because the school would not allow me to open the port).

---

### Post by mcopeland@pobox.com on 2006-01-31
think I figgered it out. I was also getting the nag for a network issue on log in but didn't associate it with this issue. I put the line in my /etc/hosts file 
127.0.0.1                   (computername)  
and all seems to be working now
can anyone tell me why this fixed my problem? Does the host file affect permissions in the local file system?

---

