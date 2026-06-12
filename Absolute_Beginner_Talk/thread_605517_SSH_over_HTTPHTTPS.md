---
title: "SSH over HTTP/HTTPS ?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by sinobato on 2007-11-07
Hi,

I have just setup my Gutsy server at home with LAMP, SSH, PHP121 and basically, I still have mostly default settings. I have also opened ports 80, 443 and 22 on my firewall so that I can connect from the internet. What I would like to do are two things:

1. Connect to the PHP121 directory using HTTPS. Currently, I am now able to connect to this using HTTP from my office PC. How can I make connections to my /var/www/php121 folder only accessible by HTTPS?

2. Since SSH is blocked on our office network, I would like to still connect to my home server using SSH through HTTPS. Can someone point to me how I can do this?

Thanks in advance for your help!

---

### Post by hyper_ch on 2007-11-07
why not making ssh listening to another port that's not blocked?

---

### Post by sinobato on 2007-11-07
Sorry, what do you mean by this? If I understand you correctly, only HTTP (port 80?) and HTTPS are able to connect to outside from our office network.

> **hyper_ch said:**
> why not making ssh listening to another port that's not blocked?

---

### Post by hyper_ch on 2007-11-07
http is by default port 80
https port 81
ssh port 22

So if https and http works for your (maybe also test port 21 [ftp]) then you could, instead of looking for a difficult solution, also use any of the working ports that and have ssh server listen to it. so you can use ssh just like you normally do only you run it on a different port.

---

### Post by starfry on 2007-11-07
My company blocks these with good reason and they fire people who try to circumvent the company's policy.

That said, you may find "mindterm" interesting. You can try googling for "mindterm over https".

---

### Post by hyper_ch on 2007-11-07
What good reasons do you have for blocking SSH?

---

### Post by starfry on 2007-11-07
I guess it boils down to you're paid to be at work to work, not to log on to your home PC. If there isn't a business reason for allowing outgoing SSH then don't allow it. An outgoing SSH can be used to set up a tunnel over which anything could happen.

---

### Post by hyper_ch on 2007-11-07
> **starfry said:**
> I guess it boils down to you're paid to be at work to work, not to log on to your home PC. If there isn't a business reason for allowing outgoing SSH then don't allow it. An outgoing SSH can be used to set up a tunnel over which anything could happen.
So does normal internet access with MSIE ;)
If there isn't a business reason for not allowing outgoing SSH then they should allow it ;)
And logging into the home pc might actually be useful, even at work ;)

---

