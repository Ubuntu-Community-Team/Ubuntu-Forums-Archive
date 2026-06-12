---
title: "LTSP on 7.04"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by perryoh on 2007-07-24
According to the feature tour, Ubuntu 7.04 comes with LTSP, which is supposed to be installed by default.  I've installed 7.04, but LTSP doesn't seem to be there.  Can anyone help me figure out how to get it installed from the CD?

---

### Post by Rocket2DMn on 2007-07-24
If you are using a thin client, check this out: [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
More can be found here for LTSP - [https://help.ubuntu.com/community/LTSPHowTo](https://help.ubuntu.com/community/LTSPHowTo)
and more: [https://help.ubuntu.com/community/LTSPClientSetup](https://help.ubuntu.com/community/LTSPClientSetup)
--These are older documents, but the setup in Feisty shouldn't vary too much.

Perhaps you could give us more information on your setup?

---

### Post by Jose Catre-Vandis on 2007-07-24
AFAIK, LTSP comes with the Server Edition and Edubuntu.

Suggest you go for an Edubuntu CD, LTSP installation will take place during the install (this is the easiest way to do LTSP, that I have found). You can always switch to the standard desktop and loose all the Edubuntu stuff if you need to. Works great!

---

### Post by perryoh on 2007-08-02
Sorry, I should have made it clear that I installed the server edition, but LTSP does not seem to be there.  How different is the Edubuntu from the server version?

---

### Post by DaveEaseman on 2007-08-03
I am fairly new to Ubuntu, but I managed to install LTSP on 7.04 Ubuntu and had it working within minutes. It is not installed by default; see this link [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

There was one additional thing I had to do as I was installing on our corporate network behind a proxy server/firewall, and that was do the following before the build-client:-

export http_proxy=http://username:password@proxyserver.net:port/

But if you are not running behind a proxy, you presumably will not need this. Check this article - 
[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html;](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html;) you don't need to specify the username:password@ part if your proxy is not configured with a username and password.

e.g.

export http_proxy=http://sample.com:8080/

sudo ltsp-build-client

---

