---
title: "JRE v5.0 Update 8 problems"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2006-09-07
I tried to follow the guide on: [http://ubuntuguide.org/wiki/Dapper#How_to_install_JRE_v5.0_Update_8](http://ubuntuguide.org/wiki/Dapper#How_to_install_JRE_v5.0_Update_8)

but It didn't work for me.

I can't copy the downloaded: "jre-1_5_0_06-linux-i586.bin" file to: 
/usr/java/

It says I dont have permission to do that or something. Im new to linux and I realize this is probly a stupid noob question but I would really appreciate some help on this.

---

### Post by jordanmthomas on 2006-09-07
I believe that is what the block of code does:  copy the contents of the bin to /usr/java

**you don't need to, but to copy the bin file to /usr/java you would do this:
```
sudo mkdir /usr/java
sudo mv jre-1_5_0_08-linux-i586.bin /usr/java

```

---

### Post by Zaid on 2006-09-07
Try this 

sudo mkdir /usr/java
sudo mv /home/admin/Desktop/jre-1_5_0_06-linux-i586.bin /usr/java

That will move the file that is on your desktop.

---

