---
title: "Java Installation problems"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Cre-ve on 2007-03-01
Hey all. I'm trying to install java to run with firefox. However, it does not seem to be working. Java opens up an applet but then nothing else shows up within it and it remains a gray color. I've tired sudo apt-get install sun-java6-jre sun-java6-plugin and it has not worked. I tried to manually install java but when i get to fakeroot make-jpkg jre-6-linux-i586.bin it says:

Creating temporary directory: /tmp/make-jpkg.MgcDvH7575
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

any help would be appreciated. thanks guys :)

---

### Post by oilchangeguy on 2007-03-01
have you tried automatix?

---

### Post by overdrank on 2007-03-01
> **Cre-ve said:**
> Hey all. I'm trying to install java to run with firefox. However, it does not seem to be working. Java opens up an applet but then nothing else shows up within it and it remains a gray color. I've tired sudo apt-get install sun-java6-jre sun-java6-plugin and it has not worked. I tried to manually install java but when i get to fakeroot make-jpkg jre-6-linux-i586.bin it says:

Creating temporary directory: /tmp/make-jpkg.MgcDvH7575
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

any help would be appreciated. thanks guys :)

I would use Automatix. It really worked for me.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by klein de usa on 2007-03-01
hi 
do you get a gray block with an ok at the bottom that you can't seem to check or make say ok?
if so hit tab a red box will come around the ok and hit enter,  if it asks you to run something in terminal put sudo in fromt of it .

---

### Post by Cre-ve on 2007-03-01
ok i have java working but i guess the problem wasn't java. its probably the website. it works in windows but not on linux. it basically shows a gray box and it says java applet window. thats all it shows..and it doesn't show anything else. i tested java by going to a java chatroom and that loaded perfectly fine.

---

### Post by Mets on 2007-03-02
Don't try to do it yourself, just get automatix.  It configure Java perfeclty, including all of the website and browser issues.  You'll be thankful, trust us :)

---

