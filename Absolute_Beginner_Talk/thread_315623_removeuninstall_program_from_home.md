---
title: "remove/uninstall program from /home"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Dainn on 2006-12-09
Hi, I thought I was following the directions on how to download and install this jre1.5.0_09-linux-i586.bin file from the java website.  Well, I must of missed something.:rolleyes: [pretty sure it just starts with the part that tells me to set up the temp/fake dir]  

I have searched, I have read, I think I might even have figured out how to do this the "correct" way.  But in the meantime, I still have this one sitting here on my pc.

I finally found were it was on my computer by using locate jre.  It looks like it put everything in /home/biteme/jre1.5.0_09 etc. I have tried to remove it by using rm, remove, sudo aptitude remove, and I am getting responses that it cant be removed.  Now, obviously, I may be doing something wrong. 
 
Is there a way to get rid of this so that I can start over, or move on from this point to fix it?  If so, would someone please either point me to the post that should help or explain it to me.  

Any help would be greatly appreciated.  Thank you.

---

### Post by taurus on 2006-12-09
Applications -> Accessories -> Terminal
```
rm -rf /home/biteme/jre1.5.0_09 
sudo mv jre1.5.0_09-linux-i586.bin /opt
cd /opt
sudo chmod 755 jre1.5.0_09-linux-i586.bin
sudo ./jre1.5.0_09-linux-i586.bin
sudo update-alternatives --config java
java -version
```

---

### Post by Dainn on 2006-12-09
Thank you.  I used the first line, rm -rf, and now when I locate jre I do not get the jre1.5.0_09.

  When I ran the second line I get
 mv: cannot stat `jre1.5.0_09-linux-i586.bin': No such file or directory

Is this becuase I deleted the download from my desktop already, or am I running into another problem?

---

### Post by igknighted on 2006-12-09
yes.  Redownload the .bin file, put it in /opt, then continue as Taurus laid out

---

### Post by Dainn on 2006-12-09
Thank you, will do:)

---

