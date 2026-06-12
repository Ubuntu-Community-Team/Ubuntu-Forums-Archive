---
title: "repositories trouble"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by teaker1s on 2005-10-14
breezy badger several people have complained about broken repositories and suggested mirror's that are faster. 

My problem I believe to be related to networking setup as I suffer the same issue when I try to install debian kernal on another pc and also kubuntu on another pc  I have a dlink router and I can successfully get thunderbird and firefox to work.

I can't get apt-get or synaptic to update repository information it claims they are unreachable and stops saying downloaded 5 of 8. changing the mirrors in sources list provides no joy ftp or http it still doesn't work.

one other odd thing Is certain websites claim i'm a us ip address when i'm based in uk

---

### Post by Ampersand on 2005-10-14
Have you made sure that you're using the correct DNS settings for your isp? You can change them in System - Administration - Networking.

---

### Post by teaker1s on 2005-10-15
yes I've manually used my isp's dns ip and I even used another free one off the net on the router and also on ubuntu as you suggested,both will allow me to surf the net but I still get repositories unavaliable.

sorted it the issue is for some reason synaptic can't get dns resolved by router so I've manually entered it in both ubuntu and router

---

