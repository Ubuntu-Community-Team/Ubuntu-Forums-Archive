---
title: "ubuntu server"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by nightfire on 2006-07-05
well, hello to everyone!

I have just installed ubuntu 5.10 from the ubuntu install disc. This edition is the regular, not server or 64 bit edition. During the install, i typed server at the boot prompt. Then i installed the os, which worked perfectly. At the point when it asked for a username, i said server. I pressed enter, and it asked again, to confirm i guess. Then i entered my password twice to confirm it. After that i booted to the command prompt. After successfully logging in, i ran the line:[sudo apt-get install samba]i think that was it. So then samba prompted me for a few answers and i said yes. so now samba is installed, and now i have no idea what to do to configure it. I can see the ubuntu server from other windows computers on my network, but when i click on it, i have no idea what the username or password would be. I tried my username and password from ubuntu, as well as several other password and username combinations.

so, what do i do to configure the server, i have heard that i need to edit the smb.conf file, but i don't know what. I need to set up a few usernames on the server, but security is not an issue right now.


well, thanks for anyones time, i've been working on this for a while

---

### Post by dmizer on 2006-07-05
i think you're going to find this site very usefull: [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

for samba server config (among others) starts around chapter 20.

---

### Post by nightfire on 2006-07-05
well, i am looking at that guide, but it doesn't really say what the lines of code mean. I don't realy know what to do with the code, or what it even does.

my aim is ifil2003, if anyone can help

---

### Post by ed_d on 2006-07-05
Remember, the wiki is your friend:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Try that. You could always edit /etc/samba/smb.conf and change "security = user" to "security = share" too. Also make sure your domain is the same so you can see it.

---

### Post by Iowan on 2006-07-05
[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")
This is another Samba how-to that I especially like.

---

