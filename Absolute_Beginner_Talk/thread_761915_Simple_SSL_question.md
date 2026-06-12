---
title: "Simple SSL question"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Yamaboy on 2008-04-21
I searched but couldn't find an answer yet. I have SSL enabled on an internal site with apache2. Users can go to [https://internalIP](https://internalIP) and access the site. 

My question is . . . the certificate has expired, so;
a). The site still works, is there any need to renew it on the server?
b). How do I renew it. I don't mind doing this each month I just don't know how.

I tried recreating the cert, but I get the message it already exists. Since the configuration is already in place for virtual host/etc. can I just delete the current cert and create a new one? I'm a little nervous to do this since I have to do a presentation on the site tomorrow and I don't want to blow it up tonight. 

Any simple instructions would be greatly appreciated.

Thanks.
Mr. NooB.

---

### Post by Yamaboy on 2008-04-21
I figured it out on my testbox. It may not be correct, but simply delete the apache.pem from the apache2 ssl directory and the create a new cert. Reload, restart apache. Done.

---

### Post by nxfs on 2008-05-08
hello i am absolutely new to ssl and completely confused

can you show me a link to how to set it up?

i heard ubuntu 8.04 doesnt come with it? i heard theres two different ssl packages? nothing works, or i don't know how to test if its working


please help
thanks

---

