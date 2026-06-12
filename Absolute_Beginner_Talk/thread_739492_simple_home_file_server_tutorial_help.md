---
title: "simple home file server tutorial help"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Jnetty99 on 2008-03-29
I been following this tutorial [http://howtoforge.com/ubuntu-home-fileserver-p3]("http://howtoforge.com/ubuntu-home-fileserver-p3")

I get to the part to add the user family using this code ```
smbpasswd -a family
```  and i get the following asked I put the same password twice and it gives me an error. ```
 New SMB password:
Retype new SMB password:
Failed to modify password entry for user family
```

I tried this tutorial on a virtual machine using VMware and now on a real computer and the same problem both times. What I'm missing? 

If in smb.conf i make security: shared i can see the share and can access it.

---

### Post by HermanAB on 2008-03-29
sudo smbpasswd -a family

---

### Post by freebeer on 2008-03-29
I believe that happens when you don't have a system user with the same name.  (ie the name that you're adding into samba must also exist as a user for the linux box)

---

### Post by Jnetty99 on 2008-03-29
> **HermanAB said:**
> sudo smbpasswd -a family
i'm already su or root.

---

### Post by Jnetty99 on 2008-03-29
> **freebeer said:**
> I believe that happens when you don't have a system user with the same name.  (ie the name that you're adding into samba must also exist as a user for the linux box)

mmm that make sense because on other tutorials that i have done i have added myself and it worked.

---

