---
title: "How do I rename the computer"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by jmurrayil on 2008-04-06
Newbie question:  How do I rename the computer's name?  Computer's name is "Admin-Desktop" and I want to change it to something else (Ubuntu 7.10).  

(Only been using Ubuntu for about 2 weeks; now install on 3 notebooks, 1 desktop, and an eeePC).

---

### Post by Rocket2DMn on 2008-04-06
Go to System->Administration->Network and hit the General tab.  There you can change the Host name.

---

### Post by Gordy on 2008-04-06
Try this...

System, Administration, Network, Click on the General and change the Host name:

That should do it!

---

### Post by jmurrayil on 2008-04-06
I did that already, but the other computers on the wireless network still report it as the old name.

---

### Post by Rocket2DMn on 2008-04-06
You may need to restart the computer for other computers to pick up on the change.  If you are using samba, you may just need to restart that.  Try
```
sudo /etc/init.d/networking restart
sudo /etc/init.d/samba restart
```
Then give the other computers awhile to pick up on the change.

---

### Post by brian_p on 2008-04-06
> **jmurrayil said:**
> Newbie question:  How do I rename the computer's name?  Computer's name is "Admin-Desktop" and I want to change it to something else (Ubuntu 7.10).  



Edit /etc/hostname and then

```
sudo /etc/init.d/hostname.sh
```

---

