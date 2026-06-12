---
title: "[SOLVED] vnc &amp;amp; ssh secure if ports blocked at router?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-02
Right on a machine I am going to run a ssh and vnc server. If the ports for these two applications are blocked at my router, is the server secure from people outside my network (i have already secured it from other people inside my network[LAN]). Can I safetly run these two servers if the ports are blocked at my router without any problems?


Saj

---

### Post by ruy_lopez on 2008-04-02
> **saj0577 said:**
> Right on a machine I am going to run a ssh and vnc server. If the ports for these two applications are blocked at my router, is the server secure from people outside my network (i have already secured it from other people inside my network[LAN]). Can I safetly run these two servers if the ports are blocked at my router without any problems?


Provided you don't download and run anything suspicious, you should be all right. You can setup public keys for ssh, so it doesn't use password authentication. That way, only someone with a private key can access ssh.

To setup public key authentication:

on the client:
```

ssh-keygen -t dsa

```
Leave the password blank if you don't want to have to type a password every time. (The password is to protect you against people who share the same system.)

Once the key is generated, look inside ~/.ssh/. There should be two files "id_dsa.pub" and "id_dsa". 

Copy "id_dsa.pub" to the server, then login to the server and run this:

on the server:
```

cat id_dsa.pub >> ~/.ssh/authorized_keys

```

Verify that you can login without using a password. Then edit "/etc/sshd_config" and change "PasswordAuthentication" to "No".

---

### Post by lespaul_rentals on 2008-04-02
> **saj0577 said:**
> Right on a machine I am going to run a ssh and vnc server. If the ports for these two applications are blocked at my router, is the server secure from people outside my network (i have already secured it from other people inside my network[LAN]). Can I safetly run these two servers if the ports are blocked at my router without any problems?


Saj

Assuming you haven't opened the ports at the router level, and your server is not a DMZ host, yes, you are secure.

---

### Post by blazercist on 2008-04-02
yes you should be fine just make sure that you have strong passwords just in case but theoretically if the ports are blocked , heck even if theyre not forwarded to the correct internal ip address by the router then you should be safe.  If you are the FBI or the NSA and need super duper uber security i would turn off the remote admin for the router and make sure that you have the latest firmware for it as well.

---

### Post by saj0577 on 2008-04-02
Okay thanks for that guys. :)

Ruy_lopez could you explain more about the private keys please.

Saj

---

### Post by brian_p on 2008-04-02
> **saj0577 said:**
> Right on a machine I am going to run a ssh and vnc server. If the ports for these two applications are blocked at my router, is the server secure from people outside my network (i have already secured it from other people inside my network[LAN]). Can I safetly run these two servers if the ports are blocked at my router without any problems?


Saj

ssh listens on port 22 so if that is not forwarded you're set to go. What port does vnc use? What you are doing will make the servers perfectly secure from remote access.

---

### Post by saj0577 on 2008-04-02
vnc uses 5900 and 5800 for http vnc.

Thanks for the responses guys.

Saj

---

