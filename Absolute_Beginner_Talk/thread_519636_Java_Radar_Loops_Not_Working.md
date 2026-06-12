---
title: "Java Radar Loops Not Working"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by rbigbie on 2007-08-07
I am trying to get the radar loops from this site to work.
[http://radar.weather.gov/](http://radar.weather.gov/)
Pick a site from the map and click a loop.
For me it wants me to download java. Went to Sun and loaded it still does not work. When I created the link in plugins and click on the loops it will crash Firefox. I rm the link.
Could someone point me in the direction to go. 
It seemed that java was  loaded and working with Firefox on other sites but this site does not work.
I am runing 6.06 LTS with latest  updates.
Thanks!

---

### Post by dca on 2007-08-07
Works fine for me, I have Sun Java 5.0 Web Start and Java Web Start 1.4 installed...

---

### Post by FuturePilot on 2007-08-07
Never mind. It's working for me. Did you try installing Java with Synaptic?

---

### Post by rbigbie on 2007-08-07
Synapatic shows "java-common" and "java-gcj-compat" packages. Is there another I should have?

---

### Post by FuturePilot on 2007-08-07
You need sun-java6-jre installed.

---

### Post by dca on 2007-08-07
In Feisty, use the add/remove under the applications menu.
 
Select Internet and scroll down putting a check-mark in 1.4,5, & 6 Java Web Start run time dealies...  That's how I got mine to work...

---

### Post by rbigbie on 2007-08-07
I don't see sun-java6-jre.
But I am new at this. I look and did a search for sun. Nothing with Sun.
I have just loaded Ubuntu 6.06 and then It did and update last night.
Would it have updated to 6.10?

---

### Post by timcredible on 2007-08-07
check out [www.ubuntuguide.org](www.ubuntuguide.org), there's detailed copy-paste instructions on installing java - very easy.

---

### Post by jamesstansell on 2007-08-07
No, I expect that 6.06 won't update to a new version until the next LTS release comes out (next year.)

The sun-java5-plugin package is in the multiverse repository.  I'm not sure if add/remove utility on your system should know about it.

The page [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) has screenshots at the "Adding the Universe and Multiverse Repositories" section to walk you through activating the multiverse repository.  After that both Synaptic (and probably Add/Remove) should be able to find the sun java plugin package.

Please followup here either with additional questions or (hopefully) with news of your suceess!

For the curious, this page in the help docs is very thorough: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Regards,

-james.

---

### Post by FuturePilot on 2007-08-07
Java 6 has been backported to Dapper I think, because I have Java 6 installed on my Dapper box.

---

### Post by rbigbie on 2007-08-07
OK! Got sun-java5-plugin loaded and it now works.
Thanks for all the help everbody.
THANKS!!

---

### Post by rbigbie on 2007-08-07
Now found the sun-java5-plugin and loaded it and the Radar loop now have all funtions.
This is as good as weather radar gets. Worlds best. Forget all other and use these if you want good up to the minute radar data.
Thanks!
The lastes java plugin and flash should load with the Ubuntu CD.

---

