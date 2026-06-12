---
title: "JRE installed from synaptic not working"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-02-08
Hello.
I wanted to install the java runtime environment for viewing web pages bt even after installing it using the synaptic package manager (i installed JRE 6) the page that said i needed to install the missing plugin which was the JRE,still asks for it.
And yeah, I did close all firefox browser windows to make sure that it gets detected during a rerun :).

Could someone suggest something 

Best Regards,

Aijaz.

---

### Post by meng on 2007-02-08
Try this:
sudo apt-get install sun-java5-plugin

(If you installed it from repositories, it should be Java 5 not Java 6, unless perhaps you have some non-official repositories?)

---

### Post by bruenig on 2007-02-08
Java 6 is in the repos now too but I have heard it isn't too great.

---

### Post by meng on 2007-02-08
Ah, interesting - I guess there was sufficient demand to place it in backports, eh?
So you want this:
sudo apt-get install sun-java6-plugin

---

### Post by old_geekster on 2007-02-08
Sorry to hijack this post, but I am having the same problem.  I have installed JRE 5 every way possible, except automatic, and still the page doesn't recognize it.  Hopefully, he will have success with JRE 6.  Then, I will try it.

Till now, I have stayed away from the backports.  They caused me problems at one point.

---

### Post by shareMenaPeace on 2007-02-08
> **old_geekster said:**
> Sorry to hijack this post, but I am having the same problem.  I have installed JRE 5 every way possible, except automatic, and still the page doesn't recognize it.  Hopefully, he will have success with JRE 6.  Then, I will try it.

Till now, I have stayed away from the backports.  They caused me problems at one point.
Try [http://getautomatix.com](http://getautomatix.com) you can install JDK too.

---

### Post by meng on 2007-02-08
Install the plugin!!!!!!
Or if you have installed the plugin and it didn't work, then say so!

---

### Post by Maestro23 on 2007-02-08
> **meng said:**
> Install the plugin!!!!!!
Or if you have installed the plugin and it didn't work, then say so!

LOL. True.

I installed Java6 and its plugin via command line today from the repositories and both are working fine for me.

Just my 2 cents.

---

### Post by old_geekster on 2007-02-15
> **meng said:**
> Install the plugin!!!!!!
Or if you have installed the plugin and it didn't work, then say so!
Sorry about taking so long to get back to this post.

I have figured out that it is a problem with Swiftfox.  I simply did some tweaking with FF2 and it is running faster and JRE6 is working just fine.

Thanks for your replies.

---

