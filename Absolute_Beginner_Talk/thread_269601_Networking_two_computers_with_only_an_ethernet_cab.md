---
title: "Networking two computers with only an ethernet cable"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by daageep on 2006-10-02
Hi. My friend and I met with our laptops to share some music. he connected an ethernet cable to my laptop and his, and through some ifconfigs and routes he managed to copy files from me (i can send files to him too). i vaguely recall seeing 10.0.0.1 and such.

does anyone know what he did? also, would it work if i was connected to someone with windows?

---

### Post by think13 on 2006-10-02
Can't you just ask him?

---

### Post by tagra123 on 2006-10-02
I doubt it was a plain either net cable. With a ethernet "crosover cable" you can connect two computer without a router.

---

### Post by Iowan on 2006-10-02
Agreed - a PC-PC ethernet cable would need to be a crossover cable.
  10.X.X.X is another "private" range [(Reference)]("http://articles.techrepublic.com.com/5100-1035-6089187.html")
 Ubuntu <-> Windows will most likely still need Samba. 
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer-to-peer]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer-to-peer")

---

### Post by 3rr0r on 2006-10-02
Ya, it has to be crossover cable.  You use a "straght" (not crossover) to hardwire pc to routers.  

Also, I'm with the first guy... couldn't you just ask him?

---

### Post by daageep on 2006-10-02
hey all,

what's the difference between a crossover cable and regular cable? also, i could ask him but would have to wait two weeks.

even with a crossover cable, how would one establish the linux-linux connection (syntax-wise).

---

### Post by Iowan on 2006-10-02
A crossover cable has transmit and receive lines reversed on one end.
[http://en.wikipedia.org/wiki/Crossover_cable]("http://en.wikipedia.org/wiki/Crossover_cable")
Getting two Linux boxes to see each other is less of an issue than sharing files between them. a couple of options are either NFS or SSH - both will require some configuration.

---

### Post by cunawarit on 2006-10-02
I have a Windows machine and a Linux machine connected via a crossover cable. To share files you can simply run an FTP server on either machine...

---

### Post by Cruz on 2006-10-02
> **Iowan said:**
> Getting two Linux boxes to see each other is less of an issue than sharing files between them. a couple of options are either NFS or SSH - both will require some configuration.


SSH doesn't. On one machine find sshd in synaptic and install it. It will automaticly be enabled and functional. On the other machine you can use the scp or the rsync commands to exchange files (see man pages for syntax). I don't think it gets any easier than that.

Between a linux and windows machine I would install vsftpd (an FTP server) on the Linux box and use FTP to transfer files. The f***ing IE on win has an ftp client embedded, you just need to call [ftp://ip_of_machine](ftp://ip_of_machine) and the rest should be clear.

---

### Post by cunawarit on 2006-10-02
> **Cruz said:**
> Between a linux and windows machine I would install vsftpd (an FTP server) on the Linux box and use FTP to transfer files.

Or alternatively if you have XP Pro then use the default FTP server.

---

### Post by daageep on 2006-10-02
i'm familar with setting up ftp servers and ssh servers in linux (pure-ftpd), but i'm having troubles deciphering the IP addresses to use.

so say there are laptops A and B. laptop A I can set the IP to be 192.168.1.1 with ifconfig; laptop B, 192.168.1.2.

once the cable is connected and laptop A has an ftp server, would i just aim my ftp client on Laptop B to 192.168.1.1 and the username/password from laptop A? is that it?

suppose that works for linux to linux. what would be the IP for the windows machine in a linux to windows set up? where would i aim my ftp client (in linux)?

thanks for the help everyone

---

### Post by Cruz on 2006-10-02
Yes that would be it. You have to make sure yet that the user logging in with FTP has access to the files you want but I'm sure you can figure that out.

It's the same with windows. Just figure out what the IP address of the windows machien is (ipconfig) or set it in Control Panel -> Network Connections

---

