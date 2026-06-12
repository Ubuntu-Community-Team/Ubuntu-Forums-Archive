---
title: "Does anyone knows on which port does Ubuntu update manager works."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by wasim2050 on 2007-07-22
Yesterday I installed Firestarter and I am not able to update my system while firestarter is running so I have to disable the firewall for a while so that I can update. If I would know which ports does update manager uses then I don't have to disable firewall every time I do updates.

---

### Post by por100pre1 on 2007-07-22
Did you set Firestarter to be restrictive by default?

---

### Post by xpod on 2007-07-22
You should`nt have firestarter running at any time....other than when(if) you need to change firewall settings
Once you`ve changed whatever settings you would then close firestarter again.

Iptables is your actual firewall which is already installed,firestarter is only a gui frontend to make changing iptables settings a bit easier for some of us.

I`ve used it for nigh on a year now for sharing internet and allowing certain services on ceratin machines within the house but it`s never blocked my update manager.

Just close firestarter and try.

EDIT> Did you set Firestarter to be restrictive by default?
Thats what it sounds like....

---

### Post by wasim2050 on 2007-07-22
Yes I have set the outbound traffic as "Restrictive by default" because I like to know what is exactly going out or coming in my PC. I use to do the same thing in windows too.

Here are the ports which I have put them in white list
80 : HTTP
443 : HTTPS
1863 : MSN protocol
5222 : Gtalk protocol
5050 : Yahoo protocol

But I don't know which port does update manager use therefore I cannot put that port in the whitelist.

So please help.

---

### Post by mckryptyk on 2007-07-22
Your problem depends on the repositories you are using and the way you have configured firestarter.

If your repository is using ftp ( [ftp://foo.debian.org/foo-distro](ftp://foo.debian.org/foo-distro) main )
you will need port 21 enabled.

If your repository is using http ( [http://foo.debian.org/foo-distro](http://foo.debian.org/foo-distro) main )
you will need port 80 enabled.

You should start by going through your settings for firestarter, 
I suggest enabling the "apply changes immediately " and configuring firestarter again.

Cheers

---

### Post by wasim2050 on 2007-07-22
Ok I have also added ftp port : 21 in the whitelist and I have recheck the firefall. The firewall is working as per my desire but there is no updates for me now so I don't know if it will fork or not.

---

### Post by tomcheng76 on 2007-07-22
Correct me if i am wrong
for Ubuntu update manager to work properly, i doesnt need open port
as we are just downloading, not hosting server

I think your firestarter have selected "Block broadcast from internal network" in Advance Options, if you are, please untick

---

### Post by tomcheng76 on 2007-07-22
Also may be because of Policy
go Policy,Editing, choose Outbound traffic policy
then choose permissive default, blacklist traffic

---

### Post by wasim2050 on 2007-07-22
@tomcheng

If you are using internet thru http then u are using port 80 and if using u r using ftp port 21. In short no matter what u are doing but if you are communicating to other computers or servers then u are using one port or another.

And I can use Evolution, Gaim(yahoo, msn, gmail) Internet(http, https, ftp) properly even when firestarter is running because I know which port should be left open for them to work. But I just get confused in the update manager and I think it uses ftp and http ports.

---

### Post by tomcheng76 on 2007-07-22
here is what i think
if you are hosting http or ftp server
the port you are opened and listening is 80 or 21
they will hear for incoming connection
while if u are downloading or browsing website
you are just use a port , may be 13xxx, to a http server. that is 80, and this one is outgoing connection....

---

### Post by tomcheng76 on 2007-07-22
usually open port means allow inbound connection for that port
that is client A x.x.x.x:12345 to server B x.x.x.x:80 (firestarter is installed in PC B)
and PC B is that pc hosting the apt mirror site...

---

### Post by mckryptyk on 2007-07-22
My understanding of his situation is that he wants to whitelist individual outbound traffic, 
not blacklist incoming traffic.

He isn't serving any outward facing services such as httpd, ssh, ftp
he wants to choose how his computer allows outbound connections.

Cheers

---

