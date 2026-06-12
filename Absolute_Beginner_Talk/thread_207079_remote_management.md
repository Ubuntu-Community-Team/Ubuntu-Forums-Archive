---
title: "remote management"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by stone80 on 2006-07-01
is there a program that will allow me to log on remotely from my windows xp work computer to my home linux computer?

---

### Post by Spleenie on 2006-07-01
[QUOTE=stone80]is there a program that will allow me to log on remotely from my windows xp work computer to my home linux computer?[/QUOTE]

An ideal way to communicate between remote computers is SSH. It's like telnet but encrypted, and you can also transfer files (SFTP)

There are a gazillion SSH clients and turning ubuntu into a SSH server is as simple as:

```
sudo apt-get install openssh-server
``` 

Of course, whether your ubuntu machine can been seen from the internet and thus communicated with from the internet is another matter :)

---

### Post by stone80 on 2006-07-01
so all i would have to do is put in the code that you gave me, then install an ssh software on my work computer, and i can remotely access my home computer?

---

### Post by Spleenie on 2006-07-01
[QUOTE=stone80]so all i would have to do is put in the code that you gave me, then install an ssh software on my work computer, and i can remotely access my home computer?[/QUOTE]

it depends on how your home computer connects to the internet. Is it behind any sort of router? What sort of connection do you make to the internet? Static IP or dynamic IP?

Before ANYTHING can be talked to on the internet, it has to be able to be seen from the internet, Ubuntu or anything else. More info is required on your network setup before I can be sure.

---

### Post by stone80 on 2006-07-01
i have cable internet that uses a dynamic IP

---

### Post by Spleenie on 2006-07-01
[QUOTE=stone80]i have cable internet that uses a dynamic IP[/QUOTE]

Maybe someone who knows more about it than me can answer this one, I know not a lot about cable modems, but my assumption would be that you have to set it to forward all requests to port 22 to your computer (port 22 is the ssh protocols port) and that is outside my realm of experience (with cable modems anyway)

Sorry I could not be more help, hopefully someone with more knowledge in this area could help out.

---

### Post by eentonig on 2006-07-01
Then you could use a Dynamic DNS updater to resolve your hostname to the ip address you receive. 

> sudo apt-get install ddns3-client

And then create an account with dyndns.org and configure this applet.

---

### Post by Stormboy on 2006-07-01
[QUOTE=Spleenie]Maybe someone who knows more about it than me can answer this one, I know not a lot about cable modems, but my assumption would be that you have to set it to forward all requests to port 22 to your computer (port 22 is the ssh protocols port) and that is outside my realm of experience (with cable modems anyway)

Sorry I could not be more help, hopefully someone with more knowledge in this area could help out.[/QUOTE]

I was thinking if you know the IP then use Putty to connect to: xxx.xxx.xxx.xxx:22 maybe Dyndns is an option then use the x.dyndns.org:22

that is my 2c worth :)

---

### Post by eentonig on 2006-07-01
Off course, that is if you don't have a FW and you're cable internet is not via some sort of router.

Can you type ifconfig in a terminal and copy and paste the output here? That will give us an idea if you're public ip address is configured on your PC directly, or that you get a private LAN address form your cable modem/router

---

### Post by stone80 on 2006-07-01
i'm at work right now, but i will do that when i get home.

---

