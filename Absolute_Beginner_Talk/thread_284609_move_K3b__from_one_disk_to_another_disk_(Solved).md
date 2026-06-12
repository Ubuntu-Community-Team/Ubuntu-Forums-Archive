---
title: "move K3b  from one disk to another disk (Solved)"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-25
I have installed CD writer K3b on a Breezy 5.10 system disk. and it works great and I love it.

For whatever reason I cant install K3b on a Dapper system disk because I cant down load it to install.

My question is can I move K3b from the Breezy system disk to the Dapper disk?

---

### Post by aysiu on 2006-10-25
So your Dapper installation isn't connected to the internet?

---

### Post by kent41 on 2006-10-25
> **aysiu said:**
> So your Dapper installation isn't connected to the internet?

Thats right. In Breezy it showed up in system networking now I just have wire connection to router.

---

### Post by aysiu on 2006-10-25
Unfortunately, you might get some serious dependency issues (version conflicts) if you install your K3B .debs from Breezy in Dapper.

Can you explain a bit more about your situation... why you have two installations (one Breezy, one Dapper) and why one is without an internet connection?

Is Dapper not recognizing your router?

---

### Post by kent41 on 2006-10-25
> **aysiu said:**
> Unfortunately, you might get some serious dependency issues (version conflicts) if you install your K3B .debs from Breezy in Dapper.

Can you explain a bit more about your situation... why you have two installations (one Breezy, one Dapper) and why one is without an internet connection?

Is Dapper not recognizing your router?

I switch my hard drives in my laptop between a Windows hard drive for personal stuff and use Ubuntu for the internet. Now I have 3 hard drive 
1) Breezy
1) Dapper
1) Windows

It took a long time to get Breezey just the way I wanted it so I got another drive to install Dapper. and it a good thing I did.

It is very easy to slip one drive out and slip another one in my laptop.

The Dapper does not see my wireless card so it never gets to the router.

It's not a router problem it a Dapper problem

---

### Post by kent41 on 2006-10-25
I think I know why there is no wireless.

When I installed Breezy I had both wire and wireless connected at the same time and when I installed Dapper I only had the wire connection and not the wireless card installed. I might try installing Dapper with wireless card installed.

---

### Post by kent41 on 2006-10-26
Problem solved

It was as I thought after reinstall of Dapper with wireless card in computer  it was recognized by Dapper all is ok as far as wireless goes.

Now on to the next step what ever that is.

Thanks for the suggestions and I am glad I did not have to use ndiswrapper.

---

