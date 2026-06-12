---
title: "how can i update Sun Java?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-12-21
hi, i still have - java version "1.5.0_05" installed;
jre-1_5_0_06 is out and i want to update to it. i looked to see if i could find out how to do it but i couldn't find anything. in windows if you install over the top the old version remains, as java is such a big install i can't afford that to happen.

is there an easy way to update with the old version being over-written? or do i have to uninstall then install jre-1_5_0_06? thanks

i have found these pages showing how to install Sun Java.
[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)
[http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142)
[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/)
JDK_installation
[http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package](http://wiki.serios.net/wiki/Ubuntu_Java_JRE/JDK_installation_with_java-package)

here's the download
[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

---

### Post by Danielle on 2005-12-21
this is how i'll uninstall if i have to, it is correct, isn't it?
[http://www.ubuntuforums.org/showpost.php?p=416513&postcount=9](http://www.ubuntuforums.org/showpost.php?p=416513&postcount=9)

sorry all these links are mainly for me, but i hope they can help someone else if they ever need it 8-[ :lol:

---

### Post by Leif on 2005-12-21
you could try installing it from a repo : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by Danielle on 2005-12-21
thanks, Leif. i'm going to uninstall then install the new version.

---

### Post by jeremy on 2005-12-22
[QUOTE=Leif]you could try installing it from a repo : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)[/QUOTE]
This link takes me to "This page does not exist yet".

---

### Post by Leif on 2005-12-22
[QUOTE=jeremy]This link takes me to "This page does not exist yet".[/QUOTE]

hmmpf, someone deleted it. god knows why. ok, see these two : [http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories.html)
[http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html](http://velourfog.blogspot.com/2005/11/how-to-install-java-using-repositories_26.html)

use the one that fits you. and let me know if there are any problems.

---

### Post by Danielle on 2005-12-22
[QUOTE=Leif]hmmpf, someone deleted it.[/QUOTE]
:D i wasn't going to say anthing, but i thought you were talking about the non Sun version black something. if i follow your steps what will i download? Sun or the other version? thanks

if i knew what i was doing i would have done it by now, i'm just not sure i'll be able to install jre-1_5_0_06 without mistakes :rolleyes:

---

### Post by Leif on 2005-12-22
[QUOTE=Danielle]:D i wasn't going to say anthing, but i thought you were talking about the non Sun version black something. if i follow your steps what will i download? Sun or the other version? thanks

if i knew what i was doing i would have done it by now, i'm just not sure i'll be able to install jre-1_5_0_06 without mistakes :rolleyes:[/QUOTE]

you'll install the sun jre if you follow those instructions. let me know if you have any problems

---

### Post by Danielle on 2005-12-22
hi, it didn't work :cry: it says i have the latest version installed already. my source list already had these lines:
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free

i think they have the same package, but i'm not sure. when i look in synaptic it says i have the latest version jre-1_5_0_05 and it still says that with this line added from your link:
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

what should i do? if it says 05 is the latest version does that mean it's still safe? normally updates include security updates too. there have been afew java exploits in the past and Linux is vulnerable too :(  

i want the latest version. i found this link which has it
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
i also found the java ControlPanel which is just like the windows version apart from the update button :(

---

### Post by Leif on 2005-12-22
[QUOTE=Danielle]hi, it didn't work :cry: it says i have the latest version installed already. my source list already had these lines:
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free

i think they have the same package, but i'm not sure. when i look in synaptic it says i have the latest version jre-1_5_0_05 and it still says that with this line added from your link:
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

what should i do? if it says 05 is the latest version does that mean it's still safe? normally updates include security updates too. there have been afew java exploits in the past and Linux is vulnerable too :(  

i want the latest version. i found this link which has it
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
i also found the java ControlPanel which is just like the windows version apart from the update button :([/QUOTE]

well, it sometimes takes a couple of days for things to be added to the repos. it's usually not a big delay, but if you need it right now, that might not be good enough for you.

---

### Post by Danielle on 2005-12-22
[QUOTE=Leif]well, it sometimes takes a couple of days for things to be added to the repos. it's usually not a big delay, but if you need it right now, that might not be good enough for you.[/QUOTE]
i don't mind waiting afew days. it might be quicker then my trying to use terminal :-\"

---

### Post by Danielle on 2005-12-22
when there's an update will it tell me? should i uncomment this line you gave me?:
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

these lines already point to java. thanks
deb [ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf) breezy free non-free

---

### Post by Leif on 2005-12-22
[QUOTE=Danielle]when there's an update will it tell me? should i uncomment this line you gave me?:
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

these lines already point to java. thanks
deb [ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf) breezy free non-free 
deb-src [ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_...plf/ubuntu/plf) breezy free non-free[/QUOTE]

you don't need both. and since plf has java plus a lot of other stuff, yes, it makes sense to comment out the tower-net one. yes, when you do an apt-get update/upgrade cycle it will get upgraded automatically.

---

### Post by Danielle on 2005-12-22
[QUOTE=Leif]you don't need both. and since plf has java plus a lot of other stuff, yes, it makes sense to comment out the tower-net one. yes, when you do an apt-get update/upgrade cycle it will get upgraded automatically.[/QUOTE]
excellent :D thanks for all the help, Leif :cool:

---

