---
title: "trouble installing java"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Handyman's Special on 2006-07-22
After I got Automatix I had hoped I would have JAVA with my Firefox, but that didn't happen.

I downloaded jre-1_5_0_07-linux-i586.bin and am trying to follow the directions I got from Sun Java.co website, 
"Installation Instructions
Linux download and installation instruction for the Java Runtime Environment (JRE)" 

Had to make some adjustments but did manage to reach this point:

Quote:"Start the installation process.Type:
./jre-1_5_0-linux-i586.bin"

Here is what I get in my terminal after I enter exactly what they show on the website:

[b]hs@hs-ubuntu:~/java$ ./jre-1_5_0_07-linux-i586.bin
./jre-1_5_0_07-linux-i586.bin: line 1: syntax error near unexpected token `<'
./jre-1_5_0_07-linux-i586.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'[/b]

Where am I going wrong? Can someone steer me to the right path?
Thanks,
Handyman's Special

---

### Post by Ziox on 2006-07-22
you can use synaptic to install java, as long as you have extra repos. inabled.

---

### Post by abowman on 2006-07-22
This is how I do it:
[http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/](http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/)

---

### Post by Ziox on 2006-07-22
> **abowman said:**
> This is how I do it:
[http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/](http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/)

that's an out dated version.  Java 5 is now included in ubuntu's repositories after the license change...just search in synaptic for Java, and make sure you have extra repositories enabled. Check my signature if you need help enabling those.

---

### Post by Skia_42 on 2006-07-22
You need to install the plugin for Firefox as well as Java for it to work.

---

### Post by Handyman's Special on 2006-07-23
> **abowman said:**
> This is how I do it:
[http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/](http://abowman.com/2006/05/08/install-java-sdk-on-ubuntu-linux/)

Hello,

Thanks for the link. Can't believe I am having a problem executing the first thing on the list.

"Make sure the following line is in your /etc/apt/sources.list file."

The line is not there but when I add it and try to save the file, it says I do not have permission. Should I edit it from the terminal? 

thanks,
HS

---

### Post by Jagot on 2006-07-23
By default you only have permission to mess around with files in your /home directory.  

From Terminal type:

```
sudo gedit /etc/apt/sources.list
```

This opens the file as root so you can edit it.

Having said that, as someone has already pointed out it is available in the repos.  I'd suggest installing by this method:

[https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956](https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956)

---

