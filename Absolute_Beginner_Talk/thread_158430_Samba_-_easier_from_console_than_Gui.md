---
title: "Samba - easier from console than Gui"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Goonie on 2006-04-11
Hey

Can anyone point me to a how-to or a good document on how one should use the built in features in Gnome to access windows machines on the network? I always mount them using:

smbmount //xxx.xxx.xxx.xxx/c$ /mnt/mywindowsbox -o username=myuser,password=mypass

Notice how I cannot use the hostname for the windows box.. My Ubuntu doesn't seem to be able to even ping the name but pings the ip just fine.

This works just fine but I would like to know if there is a way to use Gnome to to this. Whenever I go to "Places - Network servers" I get nowhere because I get promted for a user and a password and a domain name. It makes no difference what I put in there, I get nowhere. Am I doing something painfully stupid? Do I have to install some more support ? 

Thx guys

---

### Post by steve.horsley on 2006-04-11
You are doing it roughly right. When I do this, I generally get prompted first to log into a machine that has a **different** IP address to the address I entered! I assume this is the domain controller, but I'm not sure. I always cancel that, and then get presented with another domain/password prompt where I delete the domain name to leave it blank, and then enter the correct password. This generally works for me. 

If I leave the connection for a while, nect time I use it I gen erally get prompted for the domain-controller login again. I always cancel that and then the connection continues to work using the local user/password.

---

### Post by Goonie on 2006-04-11
This doesn't seem to work with me.. oh well, it doesn't really matter really. Just wanted to show some anti linux ppl that things are really simple and you don't have to use the console all that much..

Goonie

---

