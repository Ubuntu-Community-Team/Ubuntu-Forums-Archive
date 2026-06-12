---
title: "no-ip.org help please..."
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by SpawnSC on 2006-07-30
I got the sh file to generate a file and I thought I placed the file in the correct folder but its still not updating my domain with the correct ip... anyone help with this please?

---

### Post by nalmeth on 2006-07-30
Huh? What sh script did you run? What for? Wired or Wireless? Ubuntu or Kubuntu?

---

### Post by az on 2006-07-30
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by T700 on 2006-07-30
> **SpawnSC said:**
> I got the sh file to generate a file and I thought I placed the file in the correct folder but its still not updating my domain with the correct ip... anyone help with this please?

Did you follow the extremely detailed directions on the No-IP site for installing their Linux agent?

Paul

---

### Post by SpawnSC on 2006-07-30
ok I think I may have gotten it to work.

I have to move the debian.noip2.sh file from the noip-2.1.3 folder to the /etc/init.d folder

so I went to the console and typed

being in the folder directory

sudo mv debian.noip2.sh /etc/init.d

so it placed the script in the directory and it seems to be working.  I will post if anything changes.

Thanks for the awesome help this boards provides, and thanks for the fast respones.

:D :KS

---

