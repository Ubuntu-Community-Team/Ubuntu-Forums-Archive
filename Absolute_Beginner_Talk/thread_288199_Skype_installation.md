---
title: "Skype installation"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by HenningS on 2006-10-29
Good evening, it's your favourite Xubuntu noob again.

This time, I'm having problems with installing Skype in Xubuntu. I did everything they told me on the website in the console (tar xjvf skype-version.tar.gz or whatever), and it put the files in the directory. Now I have an executable file titled skype. Hurray. It doesn't work. I double clicked it, nothing happened. I used "run program..." from the Applications menu, nothing happened. Can anyone help me?

---

### Post by Marsolin on 2006-10-29
[Skype]("http://linuxappfinder.com/package/skype") is available from their deb repository. I suggest installing the deb file instead of the tar.gz file.

---

### Post by HenningS on 2006-10-29
> **Marsolin said:**
> [Skype]("http://linuxappfinder.com/package/skype") is available from their deb repository. I suggest installing the deb file instead of the tar.gz file.Thanks for your quick answer. What is a deb file? And how do I install it? I have no idea :(

---

### Post by AgenT on 2006-10-29
A good idea would be to read the official website.
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Notice the large Download Skype For Linux section with this entry:
>  Debian package (9.6 MB)
    Xandros, MEPIS, ***_Ubuntu_***, other Debian-based distros

---

### Post by HenningS on 2006-10-29
> **AgenT said:**
> A good idea would be to read the official website.
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Notice the large Download Skype For Linux section with this entry:
Aaah thank you. I see I have just embarassed myself again ;)  thanks for helping though.

---

### Post by AgenT on 2006-10-29
> **HenningS said:**
> Aaah thank you. I see I have just embarassed myself again ;)  thanks for helping though.Not really. You did the right thing to ask first. The reason is, even if a program is available on the programs' official website, it is still better to get the official Ubuntu deb if available. However, in the case of Skpe which is [**NOT** free]("http://en.wikipedia.org/wiki/Free_software"), it is not (and probably cannot legally be) included in Ubuntu. Therefore, your best option is to get the debian package from the programs' official website.

---

### Post by flajus on 2006-11-02
> **AgenT said:**
> Not really. You did the right thing to ask first. The reason is, even if a program is available on the programs' official website, it is still better to get the official Ubuntu deb if available. However, in the case of Skpe which is [**NOT** free]("http://en.wikipedia.org/wiki/Free_software"), it is not (and probably cannot legally be) included in Ubuntu. Therefore, your best option is to get the debian package from the programs' official website.

Please can someone help me i dont understand how to install skype (i used fakeroot user ) i downloaded skype from [www.skype.com](www.skype.com) >>  skype_debian-1.3.0.53-1_i386.deb
I tried to install with alien i get following error: Desktop# alien -i skype_debian-1.3.0.53-1_i386.deb
dpkg-deb: failed to create directory: Permission denied
dpkg: error processing skype_debian-1.3.0.53-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype_debian-1.3.0.53-1_i386.deb


I tried with chmod +x but it doesnt help and i tried with rpm -U and it doesnt help!:  rpm -U  skype_debian-1.3.0.53-1_i386.deb
skype_debian-1.3.0.53-1_i386.deb: read manifest failed: Success


HELP!

---

### Post by boban on 2006-11-02
> **flajus said:**
> Please can someone help me i dont understand how to install skype (i used fakeroot user ) i downloaded skype from [www.skype.com](www.skype.com) >>  skype_debian-1.3.0.53-1_i386.deb
I tried to install with alien i get following error: Desktop# alien -i skype_debian-1.3.0.53-1_i386.deb
dpkg-deb: failed to create directory: Permission denied
dpkg: error processing skype_debian-1.3.0.53-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 skype_debian-1.3.0.53-1_i386.deb


I tried with chmod +x but it doesnt help and i tried with rpm -U and it doesnt help!:  rpm -U  skype_debian-1.3.0.53-1_i386.deb
skype_debian-1.3.0.53-1_i386.deb: read manifest failed: Success


HELP!

You should try: ```
 sudo dpkg -i skype_debian-1.3.0.53-1_i386.deb 
```

There is easier way for skype installation - try automatix2 ( [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu) )

If you want to do it manually, check: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Messenger_.28Skype.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Messenger_.28Skype.29)

---

### Post by mips on 2006-11-02
> **HenningS said:**
> Good evening, it's your favourite Xubuntu noob again.

This time, I'm having problems with installing Skype in Xubuntu. I did everything they told me on the website in the console (tar xjvf skype-version.tar.gz or whatever), and it put the files in the directory. Now I have an executable file titled skype. Hurray. It doesn't work. I double clicked it, nothing happened. I used "run program..." from the Applications menu, nothing happened. Can anyone help me?

](*,) ](*,) ](*,) ](*,) 

Why do people always want to do things the hard way and others encourage them ???

All you have to do to install MOST packages, even the non-free ones is to ensure all your repositories are enabled and you have added the PLF repositories.

This will allow you to install stuff like Skype, Java, Codecs, DeCSS etc via Synaptic, aptitude, apt-get.

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
## wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
```
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free
```

---

### Post by flajus on 2006-11-02
> **boban said:**
> You should try: ```
 sudo dpkg -i skype_debian-1.3.0.53-1_i386.deb 
```

There is easier way for skype installation - try automatix2 ( [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu) )

If you want to do it manually, check: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Messenger_.28Skype.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Messenger_.28Skype.29)

THANK YOU VERY MUCH BOBAN!:)

---

### Post by boban on 2006-11-02
> **flajus said:**
> THANK YOU VERY MUCH BOBAN!:)

You are welcome :)

---

