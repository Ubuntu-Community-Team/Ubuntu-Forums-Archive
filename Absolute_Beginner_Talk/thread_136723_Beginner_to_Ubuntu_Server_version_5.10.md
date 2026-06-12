---
title: "Beginner to Ubuntu Server version 5.10"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by Mike S. on 2006-02-26
I read an article recently in PCWorld about using Ubuntu 5.10 for a home server.

I have a few questions sorry if any of this is reduntant:

  1.  Will server application run ok on a PIII 667 mhz with 128 meg of ram?
      The machine I purchased was a Dell from a resale shop for $ 13.00.
  
  2.  Where I will be using the Dell as the server do not need any drivers
       or is the default drivers that Ubuntu installs sufficient?

  3.  Any recomendations for AntiVirus and Spyware applications for the 
       Ubuntu?  I'm assuming that I can't use win based applications on Linux
       like Norton or others?

Thanks,

Mike

---

### Post by Spinelli on 2006-02-26
I think I can help answer question number 3. As far as I know ClamAV is a popular anti-virus application for ubuntu. I haven't installed it because there really aren't any virus or spyware threats in the world of Linux.

---

### Post by steve.horsley on 2006-02-26
1
I'm sure that spec is OK. It won't be blindingly fast, but it'll go OK. THe GUI will be a bit slow. Be aware that choosing "server" in the installer will leave out any GUI software and you will be running on the command line only.

2
In general, either the drivers are built-in to Ubuntu, or they don't exist. The exception is 3d acceleration video drivers, which you won't need.

3
The only AV I could name is clamav. You only really need it for removing windows viruses from files that are passed in from windows machines. Many people don't bother.

---

### Post by vibes on 2006-02-26
[QUOTE=Mike S.]
 1.  Will server application run ok on a PIII 667 mhz with 128 meg of ram?
      The machine I purchased was a Dell from a resale shop for $ 13.00.
[/QUOTE]
     My server is a P2 333hmz with 64meg so this is fine no GUI is needed for a server and isnt installed by default anyway with the server version

[QUOTE=Mike S.]
  2.  Where I will be using the Dell as the server do not need any drivers
       or is the default drivers that Ubuntu installs sufficient?
[/QUOTE]
       Again you be fine mine is a recon dell and runs ace

[QUOTE=Mike S.]
 3.  Any recomendations for AntiVirus and Spyware applications for the 
      Ubuntu?  I'm assuming that I can't use win based applications on Linux
      like Norton or others?
[/QUOTE]
 not really needed unless you are gonna run a mail server/samba on it

---

### Post by Mike S. on 2006-02-26
Thanks Steve;

I have another question about anti-virus?

This is my first server, I plan to move my data files from (2) win xp clients to the server and use the server with a tape backup drive.  

Eventually after having the server setup, archiving folders to tape, backup the server folders to a web based server in case a fire breaks out one day.

I plan to make a folder for each client on the server, will the client machines scan the perspective folders on the server for any viruses?  I'm assuming I will adjust the client anti-virus to scan the folders on the server.

Thanks,

Mike

---

### Post by VinceDee on 2006-02-26
Mike, if you install Ubuntu server on that Dell and you decide that you do want the Gnome GUI desktop, here's how you can get it:

```
sudo apt-get install ubuntu-desktop
```

---

