---
title: "Terminal Stuck"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by oldstumpy on 2007-02-03
my installer gets stuck in terminal can't figure out howto fix please help here is a pic

oldstumpy@oldstumpy-desktop:~$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java5-doc (1.5.0-08-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] sudo apt-get upgrade sun-java5-jre
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

i downloaded those and put them in root like it said here tried to get pic in root but couldn't figure how beleve me they are there.Don't know what to do :confused: :confused:

---

### Post by taurus on 2007-02-03
Maybe this helps.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by oldstumpy on 2007-02-03
Still Looking for help with problem Terminal stuck on java installations,need to know how to clear terminal of this problem PLEASE HELP SOON. Thanks oldstumpy

---

### Post by djrenown on 2007-02-06
I'm gettin the same problem... is there anyone that could help... thank you in advance.

---

### Post by shareMenaPeace on 2007-02-06
What you can try is

get this tool to install automaticly.
[http://getautomatix.com](http://getautomatix.com) 

Downlaod the correct installer for your ubuntu version and just run the file once downloaded.

After this you can access automatix from

Applications -> System Tools -> Automatix

Choose Internet -> Sun Java 1.5 JRE and install.

OR 

Choose Utilities -> Sun Java 1.5 JDK

---

### Post by djrenown on 2007-02-06
ya i cant install that because when i go to install it it gives me the jdk error message.  Thanks for the suggestion though.

---

### Post by djrenown on 2007-02-06
Alright after spending a few hours with the determination that me a linux noob will figure out this stupid error i finally did it... BRILLIANT!!!
What to do is actually very easy once i figured out what it actually wanted.

1) [https://sdlc1a.sun.com:443/ECom/EComActionServlet;jsessionid=08D2981BB074FE35C3FAFCFDFAB67FA2](https://sdlc1a.sun.com:443/ECom/EComActionServlet;jsessionid=08D2981BB074FE35C3FAFCFDFAB67FA2)
go there and download the zip... if the link doesnt work google: jdk-1_5_0-doc.zip and it will take you to the site. **You're going to want to download this str8 into your /tmp folder**

2)If you cant download it str8 into your /tmp folder then just download it and move it using the terminal

3)lastly you have to change the ownership of the zip file.  to do this use this command in the terminal: 
> sudo chown system_username /location_of_files_or_folders

PS. I am a noob so i dont know if have a the correct linux lingo but i hope this helps cuz i have been sooo frustrated over that stupid error message.  But right now you cannot understand the jubilation i am enjoying.

---

