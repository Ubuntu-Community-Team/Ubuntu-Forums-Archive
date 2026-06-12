---
title: "Installing bin file"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-03-02
Hi,

I downloaded jre-1_5_0_11-linux-i586.bin - how do you install this? I tried to run this as a script which didn't work...

Thanks,

Rudolf

---

### Post by taurus on 2007-03-02
```
sudo mkdir /opt
sudo cp jre-1_5_0_11-linux-i586.bin /opt
cd /opt
sudo chmod 755 jre-1_5_0_11-linux-i586.bin
sudo ./jre-1_5_0_11-linux-i586.bin
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by chavo on 2007-03-02
Or you could just apt-get install sun-java5-jre, no reason to run that file it's in the repos.

---

### Post by RudolfMDLT on 2007-03-02
Thanks! Why did it need to be in the opt folder in order to work?

---

### Post by Maestro23 on 2007-03-02
> **RudolfMDLT said:**
> Thanks! Why did it need to be in the opt folder in order to work?

Edit: Taurus has it.

---

### Post by taurus on 2007-03-02
Because you move it to /opt.  Therefore, you need to change to /opt first before you can change the permission and execute it or you have type in the full path to run it.

---

### Post by RudolfMDLT on 2007-03-02
If your talking about swthching the working directory that part I get. What i mean is that i had the file in a Downloads folder in my home folder and it would execute there even if  specified the file name specifically ./home/Rudolf/Desktop/Download/jre.......

But thanks - it runs now and so does Eclipse.

---

### Post by lahook on 2007-03-02
you want to download to the folder where itisto be stored (/usr/java)
the cd to the folder, chmod of jre file then ./jre
goto browser plugin folder and create a link to java plugin in /usr/java

---

