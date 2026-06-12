---
title: "Help installing themes in KDE"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-18
Hi,

I downloaded the tar file from this link:
[http://maxilys.ifastnet.com/](http://maxilys.ifastnet.com/)

I got the link from kde-look.org. The theme is Serenity. I tried ./configure but it said X fails and I have to set the path right. Then I download the rpm and converted to a deb using alien. Then I installed that using package manager. I think it got installed. Now where do I get to use the theme? I keep seeing go to the theme manager but there is no theme manager in kubuntu. Is there a place where we can change themes in kubuntu?

I went to appearence through system settings but I dont see "Themes" there, only induviual components of the theme. I am wondering if there is a place where we can change the theme itself.

Thanks.

---

### Post by Happy_Man on 2007-06-19
The thing is, wth Kubuntu, they disable the default version of Kcontrol and use that crippled version instead. [shudders] But, it's easy to get the real Kcontrol. Simply open up Konsole and type: ```
kcontrol
``` Then go to the Appearance and themes --> Theme Manager, click install a new theme, and navigate to the .tar.bz2. Then click OK and it will install for you! Yay!

---

