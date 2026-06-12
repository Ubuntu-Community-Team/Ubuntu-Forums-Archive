---
title: "Java not working with Firefox 1.5.0.3"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-12
i installed this latest version of firefox and its plugins using automatix, and whenever i try load something that's java, it doesn't load!!
BTW, this happened also with firefox 1.5.0.2 (which i also installed from automatix)

---

### Post by uzi09 on 2006-05-12
do you mind checking on this site whether it is installed correctly or not:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

sorry, i've never used automatix before, but why don't you uninstall it from there and follow this guide (assuming you are using breezy -- if you're using dapper, there is  a link on the top of the page):
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)


if that doesn't work, just install it manually from their website. the instructions are very clear and they also have screenshots.

heres the link for the downloads page and next to it is the link for instructions:
[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
ps: i'm not sure what your computer specs are, but you're probably going to need the second file "Linux (self-extracting file)".

thanks,
uzi

---

### Post by user1397 on 2006-05-16
[quote=uzi09]do you mind checking on this site whether it is installed correctly or not:
[http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")

sorry, i've never used automatix before, but why don't you uninstall it from there and follow this guide (assuming you are using breezy -- if you're using dapper, there is  a link on the top of the page):
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")


if that doesn't work, just install it manually from their website. the instructions are very clear and they also have screenshots.

heres the link for the downloads page and next to it is the link for instructions:
[http://www.java.com/en/download/linux_manual.jsp]("http://www.java.com/en/download/linux_manual.jsp")
ps: i'm not sure what your computer specs are, but you're probably going to need the second file "Linux (self-extracting file)".

thanks,
uzi[/quote]
the thing is i have java installed, and i know it.
and i installed firefox w/ all its plugins with automatix, so it should immediately work, but it doesn't.  on the java check site, it starts checking for my java installation, and then firefox closes and says that there was some type of error.
also when i tried to play a java game online, there was something about "gcj" or something like that. ???HELP???

---

### Post by user1397 on 2006-05-16
I fixed it! i just uninstalled blackdown java and sun java, and reinstalled sun java using the ubuntu wiki, and now it works!

---

