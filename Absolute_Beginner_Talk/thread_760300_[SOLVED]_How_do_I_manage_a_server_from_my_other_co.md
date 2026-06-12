---
title: "[SOLVED] How do I manage a server from my other computer?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Palu on 2008-04-20
I don't want to buy a monitor for both my computers. If both computers are connected to my router, what do I configure to get them to see each other? What do I do to log into the server from my computer? I don't mind being given terms to Google so I can try to find guides and tutorials. I think I'm looking at these options: VNC or remote login... correct? Is remote login a generic term for what a specific program like SSH does? Will I find those programs under Applications, or are those the generic terms? Is what I'm trying to do considered insecure, or do many people use their server from another computer?

Will running a server mean opening ports? Port 80? A port for remote access? What commands do I need to research in Google to learn how to open ports? I imagine they'll be commands I execute with sudo... correct?

Any tutorials or keywords you can point me to in order to show me how to set up the ability to log into my network by a VPN equivalent method? Given my other questions, do I sound like it's too early for me to dream of such things? :) I'd love a networked partition I could use anywhere with internet, you see... and a live PHP sandbox... and... and...

Sorry to ask so much and sound so clueless in something that's probably over my head, but I'd really like to try. :)

---

### Post by PurposeOfReason on 2008-04-20
Opening ports is done with your router. Then for controling use ssh. Then you could also use firefox as a primitive file browser. Really it depends what you want to do.

---

### Post by Palu on 2008-04-20
I'd want to do everything normally done with a server--just without a monitor... ummm... I guess installing software updates, tweaking config files in mySQL and PHP and Apache... I think I'm asking how to access bash of the server from my other computer and be able to even to sudo stuff. Also, are you sure on the router comment? I know I'll need to forward port 80 to the server (at least I think so), but I thought that was different than allowing Apache and such to use that port. Isn't there a firewall or something like that on Ubuntu server that I'd need to open a port on?

---

### Post by ibutho on 2008-04-20
You can login to the server using SSH and then do all the sysadmin stuff from there. e.g.
```
ssh somehost
```
or
```
ssh IP.ADD.RE.SS
```
After successful login you will be presented with a command prompt, so you can work on the system as if you were sitting right in front of it. 

Another option is to access the server with a web browser using [webmin]("http://www.webmin.com"). It lets you configure various aspects of your server and the system in general using your favourite web browser.

---

### Post by PointyWombat on 2008-04-20
If you simply want access your headless server via CLI, you can just install an ssh server on it:

```
sudo apt-get install openssh-server
```

Then from your other box, you can ssh to that one:

```
ssh <HeadlessServerName>
```

---

### Post by PurposeOfReason on 2008-04-20
Nothing that I ever came across and I have a Debian server running torrentflux. Just go to your router and forward port 80 for http and whatever port you want for ssh. DO NOT keep it as the default 22 as that is not secure.

---

### Post by hyper_ch on 2008-04-20
you will have to install openssh-server on the other computer so that you can login there.

If you are inside the same network, just do:

```

ssh USER@SERVER

```
Where USER is your username on the server and SERVER is the IP of it.

However if the server is behind a router, you will need to forward port 22 from the router to the server. You have to set this on your server.

Then you would use:
```

ssh USER@HOME_IP

```

Where HOME_IP is the public IP address of your server.

---

### Post by hyper_ch on 2008-04-20
> **PurposeOfReason said:**
> DO NOT keep it as the default 22 as that is not secure.

Why?

---

### Post by freduardo on 2008-04-20
You'll get brute force attacks all the time (a.k.a. idiots trying to crack your server through ssh).

You're better off running the daemon on another port (above 1024 I think).
And you could/should tighten security even more in your firewall.

---

### Post by hyper_ch on 2008-04-20
> **freduardo said:**
> You'll get brute force attacks all the time (a.k.a. idiots trying to crack your server through ssh).

You're better off running the daemon on another port (above 1024 I think).
And you could/should tighten security even more in your firewall.

those that bruteforce will nmap first so it does not matter what port sshd runs on... you better off with an auto-ban script like denyhosts or fail2ban

---

### Post by joshrobinson on 2008-04-20
i restrict my fileserver from accessing the internet with my router, it can only accept LAN connections

just throwing that out there

---

### Post by PurposeOfReason on 2008-04-20
> **hyper_ch said:**
> those that bruteforce will nmap first so it does not matter what port sshd runs on... you better off with an auto-ban script like denyhosts or fail2ban
Or all of the above. Windows should have taught everyone one main thing, there is no such thing as being too secure.

---

### Post by Palu on 2008-04-20
Maybe I can find enough info / a tutorial to figure it out, but is fail2ban easy to administer and run?

@joshrobinson's comment: Would a web / game server be better as a seperate box from my internal fileshare as far as security goes?

---

### Post by hyper_ch on 2008-04-20
never tried fail2ban but denyhosts

---

### Post by Oldsoldier2003 on 2008-04-20
> **PurposeOfReason said:**
> Nothing that I ever came across and I have a Debian server running torrentflux. Just go to your router and forward port 80 for http and whatever port you want for ssh. DO NOT keep it as the default 22 as that is not secure.

actually port 22 is just as secure as any other port. Securing SSH is more about actually securing it than obscuring it. Sure changing from port 22 will stop the random script kiddies, but it does nothing to actually secure ssh. Some things that do secure ssh are:
disabling root logins
enabling/forcing public key usage for logins
installing DenyHosts
aggressively firewalling port scanning IPs
disabling SSH1 protocol
restricting SSH login to specified users

---

