---
title: "Wirerless Router Setup with Ubuntu"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Bouzy on 2007-12-02
I have read through the other topics about this ,but I don't think they are talking about what I am confused about. I have a wireless router and it works great for Windows, but when I go in a Live CD Ubuntu it asks me for my network password to connect to the wireless router. I don't even remeber how I set up my router. It was so long ago. (I don't think I used a password it just ran through with a jump drive). What do I have to do to get internet working in Ubuntu?

P.S. (Its a linksys G router)

---

### Post by jimrz on 2007-12-02
> **Bouzy said:**
> I have read through the other topics about this ,but I don't think they are talking about what I am confused about. I have a wireless router and it works great for Windows, but when I go in a Live CD Ubuntu it asks me for my network password to connect to the wireless router. I don't even remeber how I set up my router. It was so long ago. (I don't think I used a password it just ran through with a jump drive). What do I have to do to get internet working in Ubuntu?

P.S. (Its a linksys G router)

Do you have WEP or WPA encryption setup on your wireless router?

If you are not sure, you should access the router from windows and check the settings. I am not certain, but I beleive that linksys uses 192.168.1.1 as the default IP address for the router. You can check this either by looking up the manual for your model on the linksys site or by simply checking your windows network configuration. 

You will also need a user name and password to login to the router. If you just left the defaults when you set it up, these values will also be available from the linksys site.

If you are using encryption, since you obviously no longer know the key (or password), simply change the encryption key and then use the new one when network manager asks for it.

---

### Post by Bouzy on 2007-12-02
Thanks I will try some of that tomorrow.

---

### Post by Threbus5 on 2007-12-02
While you research the router's default IP address and default password determine if there is a hardware reset procedure. I believe that router has a pin hole reset but check to make sure of the pinhole and exact procedure.

That way, if necessary, you can reset the router and reconfigure.

You did not mention whether the machine is part of a network. If it is, then changing the router configuration affects the network. That requires more thought and planning.

Good luck.

---

### Post by ahoucke on 2007-12-03
Hi, I have a similar issue, but I know that I DO have a WEP key (and I know the key!)  It seems I can connect my laptop to the router (I get the connection bars), but I cannot get past the router to the internet.

Any suggestions?

---

### Post by jimrz on 2007-12-03
> **ahoucke said:**
> Hi, I have a similar issue, but I know that I DO have a WEP key (and I know the key!)  It seems I can connect my laptop to the router (I get the connection bars), but I cannot get past the router to the internet.

Any suggestions?

From your panel check in Systen>Adinistration>Network.the "DNS" tab and make sure that you have the appropriate servers showing there. I ahve, in the past, had some arbitrary addresses show up there upon a new install. If that is your case, delete the bad and add your correct ones and you should be good to go.

---

### Post by Threbus5 on 2007-12-06
re:
Re: Wirerless Router Setup with Ubuntu

--------------------------------------------------------------------------------
Hi, I have a similar issue, but I know that I DO have a WEP key (and I know the key!) It seems I can connect my laptop to the router (I get the connection bars), but I cannot get past the router to the internet.

Any suggestions? 

Yes,
You may encounter an inability to add the proper DNS server. I found during Ubuntu 7.10 install that (at least in my instance) the OS continued to disallow DNS entry as described by the previous post.

If a DNS server proves un-addable then edit the resolv.conf file to include the following (without the quotes) 
"nameserver xxx.xxx.xxx.xxx"   replacing the x's with the IP address of your DNS server.

Best of luck

---

