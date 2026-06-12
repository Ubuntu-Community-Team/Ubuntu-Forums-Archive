---
title: "Guides using Ubuntu Server"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by codewriter on 2007-11-26
Hi,

Im really new in Linux and I was trying to setup a server using Ubuntu Server edition. My problem now is that Server edition didnt have any GUI and all need to be type in using command line. Im know nothing about linux command.

Is there any where I can find some guides about setup the server using command line? I read the serverguide file and it still cant make me go anywhere.

I really appreaciate if some one could show me the light.:)

---

### Post by skillet on 2007-11-26
To get a GUI type:

apt-get update && apt-get install ubuntu-desktop

After about 30 mins of downloading and installing you should have gnome installed. 

What are your plans for your new Ubuntu Server? Maybe we can help you or point you in the right direction

---

### Post by codewriter on 2007-11-26
Actually I was planning to run apache, mysql, php using ubuntu server as a server and other client machine(window based) to access the php files. :)

---

### Post by The Cog on 2007-11-26
[http://www.google.com/search?q=linux+command+line+guide](http://www.google.com/search?q=linux+command+line+guide)
has some good links.

---

### Post by louieb on 2007-11-26
New to Linux and the command line. Yes I agree with skillet get a GUI to use  till you  learn your way around.  Even with a GUI, theres a lot to learn  about administration of a LAMP server. 
Might want to take a look at [Webmin]("http://www.webmin.com/") its what I use.
[Webmin on Dapper Server - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=195093")
[Installing Webmin On Ubuntu Feisty Fawn (7.04) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

---

### Post by codewriter on 2007-11-27
> **The Cog said:**
> [http://www.google.com/search?q=linux+command+line+guide](http://www.google.com/search?q=linux+command+line+guide)
has some good links.

Thanks, this really can help me have a good start.

---

### Post by codewriter on 2007-11-27
> **louieb said:**
> New to Linux and the command line. Yes I agree with skillet get a GUI to use  till you  learn your way around.  Even with a GUI, theres a lot to learn  about administration of a LAMP server. 
Might want to take a look at [Webmin]("http://www.webmin.com/") its what I use.
[Webmin on Dapper Server - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=195093")
[Installing Webmin On Ubuntu Feisty Fawn (7.04) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

Thanks a lot. Really much appreciate your help :). If im need to use the GUI, it only available for the ubuntu desktop and not server version. Is ubuntu desktop version can install all the LAMP?

---

### Post by louieb on 2007-11-27
:popcorn:Have your cake and eat it too.
Skillets post showed how to add the desktop to a server install. 
To make a  desktop PC a LAMP server too:
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by codewriter on 2007-11-29
> **louieb said:**
> :popcorn:Have your cake and eat it too.
Skillets post showed how to add the desktop to a server install. 
To make a  desktop PC a LAMP server too:
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Thanks you very much "louieb"

---

### Post by hyper_ch on 2007-11-29
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

